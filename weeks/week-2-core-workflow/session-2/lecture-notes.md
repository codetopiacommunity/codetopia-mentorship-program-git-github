# Lecture Notes — `.gitignore` & Undoing Changes Safely

## 1. Why we ignore files

Not everything in your folder belongs in history. Three categories to never commit:

1. **OS junk** — `.DS_Store` (macOS), `Thumbs.db` (Windows)
2. **Editor junk** — `.vscode/`, `.idea/`, `*.swp`
3. **Machine-specific and secrets** — `node_modules/`, `venv/`, `.env`, API keys

Committing these once pollutes history forever. Prevention is cheaper than cleanup.

## 2. The `.gitignore` file

A plain text file at the repo root. Each line is a pattern.

```gitignore
# OS
.DS_Store
Thumbs.db

# Editors
.vscode/
.idea/
*.swp

# Node
node_modules/
npm-debug.log

# Python
__pycache__/
*.pyc
venv/
.env

# Build output
dist/
build/
```

Start from our template: [`../../../templates/.gitignore-template`](../../../templates/.gitignore-template).

### Pattern quick-reference

| Pattern | Matches |
| ------- | ------- |
| `secret.txt` | a file named `secret.txt` anywhere |
| `/secret.txt` | `secret.txt` only in the repo root |
| `*.log` | any file ending in `.log` |
| `build/` | any folder named `build` |
| `!important.log` | re-include `important.log` even if `*.log` is ignored |
| `docs/**/*.pdf` | any `.pdf` at any depth under `docs/` |

### Gotcha: already-tracked files

`.gitignore` **only ignores untracked files**. If you already committed `.env`, adding it to `.gitignore` does nothing. You have to untrack it first:

```bash
git rm --cached .env         # remove from index, keep on disk
echo ".env" >> .gitignore
git add .gitignore
git commit -m "chore: stop tracking .env"
```

> 💡 If a secret was ever committed, *assume it is leaked*. Rotate the secret. History rewrites don't help if someone already cloned.

## 3. Undoing, level by level

Git has three "levels" where changes live. Undoing means picking the right level.

```
   level 3: working dir  ──► git restore <file>
   level 2: staging area ──► git restore --staged <file>
   level 1: last commit  ──► git commit --amend
   level 0: older commits──► git reset / git revert   (careful)
```

Learn them in that order. Reach for the smallest tool that solves your problem.

## 4. `git restore` — the modern undo

Git 2.23+ split the old `git checkout` into two clearer commands: `git switch` (for branches, next week) and `git restore` (for files).

### Throw away working-tree edits

```bash
git restore README.md                # throws away your uncommitted edits to README.md
git restore .                        # throws away every uncommitted edit (DANGER)
```

There is no undo. The edits are gone. Stage or stash first if you're unsure.

### Unstage a file

```bash
git add README.md                    # oops, didn't mean to stage
git restore --staged README.md       # unstaged; edits still in working dir
```

This is the move that replaces the confusing `git reset HEAD <file>` of yore.

### Restore from a specific commit

```bash
git restore --source=HEAD~2 README.md   # replace working README with its state 2 commits ago
```

## 5. `git commit --amend` — fix the last commit

Two flavors:

### Fix just the message

```bash
git commit --amend -m "docs: add github section"
```

### Add a forgotten file to the last commit

```bash
# You committed, then noticed you forgot a file
echo "extra" > notes.md
git add notes.md
git commit --amend --no-edit        # --no-edit keeps the old message
```

`--amend` rewrites the last commit — the hash changes. If you already pushed it, see §8.

## 6. `git reset` — the three modes

`git reset` moves the branch pointer. The *mode* decides what happens to the staging area and working directory.

```
               before:  A ─ B ─ C          HEAD=C
   git reset --soft  A ─ B (─ C)       HEAD=B, C's changes staged
   git reset --mixed A ─ B (─ C)       HEAD=B, C's changes in working dir (DEFAULT)
   git reset --hard  A ─ B             HEAD=B, C's changes GONE
```

| Mode | Moves HEAD | Keeps staged | Keeps working dir |
| ---- | :--------: | :----------: | :---------------: |
| `--soft` | yes | yes | yes |
| `--mixed` (default) | yes | no | yes |
| `--hard` | yes | no | **no** |

### Common uses

```bash
# "I want to redo my last 2 commits as one commit, keeping all the work."
git reset --soft HEAD~2
git commit -m "feat: combined thing"

# "My last commit is wrong, but the changes are fine — let me restage carefully."
git reset HEAD~1                      # --mixed is default
git status                            # files now 'modified, not staged'

# "Burn down the last commit, edits and all." (DANGEROUS)
git reset --hard HEAD~1
```

> ⚠️ `--hard` deletes uncommitted work. Run `git status` first. Always.

## 7. `git reflog` — the safety net

Git rarely throws anything away immediately. Every move of HEAD is logged for ~90 days.

```bash
git reflog
```

```
c9f1aa2 HEAD@{0}: reset: moving to HEAD~1
a83b01f HEAD@{1}: commit: docs: add resources section
72e4d90 HEAD@{2}: commit: docs: add markdown section
```

"Oh no, I `reset --hard`-ed away my work!"

```bash
git reset --hard HEAD@{1}            # go back to before the reset
```

Reflog is **local-only**. It doesn't help if you cloned fresh. Still — it's saved countless people.

## 8. `reset` vs `revert` — when you've already pushed

If a broken commit is already on `main` and others have pulled it:

- `git reset` **rewrites** history. You'd need to force-push and disrupt everyone.
- `git revert <sha>` creates a **new** commit that undoes the old one. History stays linear.

Rule of thumb:

> Rewrite *your own, unpushed* history freely. Once others have it, only add new commits.

## 9. Live demo script (mentor)

```bash
mkdir undo-lab && cd undo-lab
git init
echo "# Undo Lab" > README.md
git add README.md
git commit -m "feat: initial README"

# --- .gitignore ---
echo "secret" > .env                          # pretend this has an API key
echo "temp.log" > temp.log
git status                                    # narrate: both untracked
cat > .gitignore <<EOF
.env
*.log
EOF
git status                                    # .env and temp.log now hidden
git add .gitignore
git commit -m "chore: add gitignore"

# --- restore working tree ---
echo "wrong text" >> README.md
git diff
git restore README.md
cat README.md                                 # narrate: "edits gone"

# --- restore --staged ---
echo "staged by accident" >> README.md
git add README.md
git status                                    # narrate: "staged"
git restore --staged README.md
git status                                    # unstaged, edits kept
git restore README.md                         # clean up

# --- amend ---
echo "## Notes" >> README.md
git add README.md
git commit -m "docs: adds notes"              # past tense, bad
git commit --amend -m "docs: add notes"
git log --oneline

# --- reset --soft ---
echo "## Section A" >> README.md
git add README.md && git commit -m "docs: add section A"
echo "## Section B" >> README.md
git add README.md && git commit -m "docs: add section B"
git log --oneline
git reset --soft HEAD~2
git status                                    # two commits worth staged
git commit -m "docs: add sections A and B"

# --- reflog as safety net ---
git reset --hard HEAD~1                       # "oh no"
git reflog                                    # find the previous HEAD
git reset --hard HEAD@{1}                     # rescue

# --- revert (for pushed commits) ---
git revert HEAD --no-edit
git log --oneline
```

## 10. Recap

- `.gitignore` prevents junk from entering history; it doesn't retroactively clean tracked files.
- Undo at the smallest possible level: working tree → staging → last commit → history.
- `git restore` handles files; `git reset` handles history.
- `--soft` keeps everything staged. `--mixed` unstages. `--hard` deletes. Memorize this.
- `git reflog` is your time machine. Show it to someone before they need it.
- Rewrite your own unpushed history freely. Never rewrite shared history without agreement.

## 11. Further reading

- [`../../../templates/.gitignore-template`](../../../templates/.gitignore-template)
- [`../../../troubleshooting/reset-and-restore.md`](../../../troubleshooting/reset-and-restore.md)
- [Pro Git §2.4 — Undoing Things](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things)
- [github/gitignore — language-specific templates](https://github.com/github/gitignore)

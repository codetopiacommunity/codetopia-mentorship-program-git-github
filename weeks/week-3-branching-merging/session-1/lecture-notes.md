# Lecture Notes — Branches: Movable Pointers

## 1. The one-sentence truth

> **A branch is a lightweight, movable pointer to a commit.**

Re-read it. Say it out loud. Write it on a sticky note.

It is not a folder. It is not a copy of your code. It is a name that points at one commit. When you make a new commit on that branch, the pointer moves forward.

Everything else about branches falls out of this.

## 2. The mental model

After three commits on `main`:

```
   A ── B ── C          (main → C, HEAD → main)
```

`main` is a pointer to commit `C`. `HEAD` is a pointer to `main` (which is a pointer to `C`). `HEAD` is "where am I right now?".

Create a new branch called `feature/login`:

```bash
git branch feature/login
```

Nothing changes about your files. You just made a new sticky note:

```
   A ── B ── C          (main → C, feature/login → C, HEAD → main)
```

Now switch to it:

```bash
git switch feature/login
```

Still no file changes. `HEAD` moved:

```
   A ── B ── C          (main → C, feature/login → C, HEAD → feature/login)
```

Make a commit on `feature/login`:

```
                   D    (feature/login → D, HEAD → feature/login)
                  /
   A ── B ── C          (main → C)
```

`main` didn't move. `feature/login` did. That's it. That's a branch.

## 3. `HEAD`, detached or otherwise

`HEAD` is *usually* "which branch am I on". Normally it points at a branch, which points at a commit.

```
HEAD ──► main ──► C
```

If you check out a commit directly (`git switch --detach <sha>` or `git checkout <sha>`), `HEAD` points straight at the commit, skipping the branch. Git calls this **detached HEAD**:

```
HEAD ──► C          (main still at B, say)
```

You can still commit — but the new commit has no branch name, and as soon as you switch away, it's "orphan" until `git gc` cleans it up (typically ~90 days). Reflog can save you if you act fast.

> 💡 **Mentor framing:** "Detached HEAD isn't broken. It's just un-named. Name it with `git switch -c new-branch` before you make commits worth keeping."

## 4. The working vocabulary

### Create

```bash
git branch feature/login              # create only
git switch -c feature/login           # create AND switch
git switch -c feature/login main      # create from main specifically
```

`git switch -c` is almost always what you want.

### List

```bash
git branch                            # local branches; * marks current
git branch -a                         # include remote-tracking branches
git branch -v                         # with last commit sha/message
git branch --merged                   # branches already merged into current
git branch --no-merged                # branches with unmerged work
```

### Switch

```bash
git switch feature/login              # switch to an existing branch
git switch -                          # switch back to previous branch
git switch main                       # back to main
```

### Rename

```bash
git branch -m old-name new-name       # rename a branch
git branch -m new-name                # rename the current branch
```

### Delete

```bash
git branch -d feature/login           # safe: refuses if unmerged
git branch -D feature/login           # force: deletes anyway (dangerous)
```

Use `-d` unless you're sure. The error message from `-d` is the kind of safety rail Git quietly provides.

## 5. `git switch` vs `git checkout`

Before Git 2.23, `git checkout` did two unrelated things:

1. Switch branches.
2. Restore files.

Which is confusing. Since 2.23 there are two commands:

- `git switch` — switch branches.
- `git restore` — restore files.

You will see `git checkout` everywhere online. It still works. But prefer `switch` + `restore` in new muscle memory.

## 6. Branching strategies — a quick tour

This is just naming conventions; the mechanics are identical.

- **Trunk-based**: everyone commits to `main`, feature branches are short-lived (hours).
- **GitHub Flow**: one long-lived `main`, feature branches per change, merged via PR.
- **Git Flow**: long-lived `main`, `develop`, plus `feature/*`, `release/*`, `hotfix/*` branches. Heavier, older.

For this program we use **GitHub Flow**. Branch names like:

- `feat/login-page`
- `fix/typo-in-readme`
- `docs/update-contributing`
- `chore/bump-deps`

## 7. Reading the graph

```bash
git log --oneline --graph --decorate --all
```

```
* d4c0ffe (HEAD -> feature/login) feat: add login form
* c9f1aa2 (main) docs: add installation steps
* a83b01f feat: initial README
```

- `*` marks a commit.
- `(HEAD -> feature/login)` — `HEAD` points at `feature/login`, which points at this commit.
- `(main)` — another branch pointer, at a different commit.

With more branches you get the famous ASCII graph:

```
*   e7b2c1a (HEAD -> main) Merge branch 'feature/login'
|\
| * d4c0ffe (feature/login) feat: add login form
|/
* c9f1aa2 docs: add installation steps
```

Read top-to-bottom (newest first) or bottom-to-top (chronological) — your preference.

## 8. Live demo script (mentor)

```bash
mkdir branch-lab && cd branch-lab
git init
echo "# Branch Lab" > README.md
git add README.md
git commit -m "feat: initial README"

echo "- main line" >> README.md
git add README.md && git commit -m "docs: add main line note"

# Branch off
git switch -c feature/extra
echo "- extra feature" >> README.md
git add README.md && git commit -m "feat: add extra feature note"

git log --oneline --graph --decorate --all
git branch                                   # * feature/extra, main

# Switch back to main; show the file state changes
git switch main
cat README.md                                # narrate: "no extra line"

# Switch forward; show the file comes back
git switch feature/extra
cat README.md                                # narrate: "extra line is back"

# Rename demo
git branch -m feature/extra feature/note-extra
git branch

# Delete demo (after a merge in session 2 — here we'll use -D for speed)
git switch main
git branch -d feature/note-extra             # will refuse: unmerged
git branch -D feature/note-extra             # force delete; note the warning

# Detached HEAD demo
git switch --detach HEAD~1
git log --oneline -n 2                       # narrate: "HEAD points at a commit, not a branch"
git switch -                                 # back to main
```

## 9. Anti-patterns to call out

- **Working on `main` for everything.** Fine for tiny solo projects, painful as soon as you collaborate.
- **Long-lived feature branches.** The longer a branch lives apart from `main`, the harder it is to merge back.
- **Branch names with spaces or uppercase.** Use `kebab-case` or `feat/slash-separated`. Lowercase.
- **Never deleting old branches.** `git branch` turns into a graveyard. Prune.

## 10. Recap

- A branch is a pointer to a commit. `HEAD` is a pointer to (usually) a branch.
- `git switch -c <name>` is your create-and-move-to command.
- `git switch <name>` is your switch command. `git switch -` goes back.
- `git branch -d <name>` safely deletes a merged branch; `-D` forces it.
- The graph (`git log --oneline --graph --decorate --all`) is the source of truth for where everything is.
- Nothing about branches is expensive. Make lots of them. Delete them when done.

## 11. Further reading

- [Pro Git §3.1 — Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
- [Pro Git §3.2 — Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- [Learn Git Branching (interactive)](https://learngitbranching.js.org/)

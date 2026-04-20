# Solutions — Week 2 · Session 2

> **Mentor only.** Don't peek until you've tried.

## Mistake 1 — Committed a junk file

```bash
# Stop tracking without deleting from disk
git rm --cached .DS_Store

# Prevent recurrence
cat > .gitignore <<EOF
.DS_Store
Thumbs.db
EOF

git add .gitignore
git commit -m "chore: stop tracking .DS_Store and add gitignore"
```

Watch for mentees who `rm .DS_Store` (without `--cached`) — that deletes it from disk and still leaves it staged for deletion, which works but is a different move. Both are valid; explain the distinction.

## Mistake 2 — Staged the wrong file

```bash
git restore --staged later.md
git status                        # later.md is now 'untracked' or 'modified'
git commit -m "docs: add keep.md"
```

Avoid `git reset HEAD later.md` — it still works but `git restore --staged` is the modern idiom.

## Mistake 3 — Typo in the last commit message

```bash
git commit --amend -m "docs: add notes"
```

Verify with `git log -n 1`. Note the hash changed.

## Mistake 4 — Two commits that should have been one

```bash
git reset --soft HEAD~2
git status                        # both sets of changes are staged
git commit -m "feat: add sections A and B"
```

## Bonus — Reflog recovery

```bash
git reflog
# Find the HEAD@{n} just before the reset --hard
git reset --hard HEAD@{1}
```

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| `.gitignore` doesn't hide `.DS_Store` | It was already tracked | `git rm --cached .DS_Store` |
| `git restore --staged` "did nothing" | Nothing was staged | Check `git status` first |
| `git commit --amend` opens an editor with no changes staged | That's expected — it's for message-only amendments | Save & quit, or `-m "msg"` |
| `git reset --hard` took my `.env` | `.env` wasn't committed; it's still on disk unless you `git clean`-ed | Check your editor's local history |

## Grading rubric (if you want a quick score)

- All 4 mistakes demonstrated: 40
- All 4 fixes correct: 40
- `recovery-log.md` clear and committed: 20

Pass: 70.

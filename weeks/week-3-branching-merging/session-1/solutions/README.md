# Solutions — Week 3 · Session 1

> **Mentor only.** Don't peek until you've tried.

## Expected graph shape

After all three branches with two commits each:

```
* 6a2e8f1 (HEAD -> draft/detailed) style: reorder final quote
* 1d9c4b2 feat: add long quotes draft
| * 3f0e77a (draft/themed) fix: typo in "Play" section
| * a83b01f feat: add themed quotes draft
|/
| * b5e9c0d (draft/minimal) chore: tighten spacing
| * c4a2f01 feat: add minimalist quotes draft
|/
* 90deadb (main) feat: scaffold index.md
```

Hashes and exact ordering will vary. Key signals:

- Three branches diverging from the same `main` commit.
- Two commits per branch (minimum).
- Conventional messages throughout.

## Model answer — "What is a branch, really?"

> "A branch is a lightweight, movable pointer to a commit. It's not a copy of my files or a folder — it's a name Git keeps in `.git/refs/heads/` that points at one commit hash. When I commit, the pointer for the current branch moves forward to the new commit. `HEAD` is a pointer to the pointer: it's how Git knows which branch I'm on. This is why branches in Git are cheap — creating one is just writing a sha to a file."

## Model answer — Detached HEAD

> "Detached HEAD happens when `HEAD` points directly at a commit rather than at a branch — for example after `git switch --detach <sha>` or `git checkout <sha>`. It's not an error; it's a warning. I can still look around and even make commits, but those commits don't belong to any branch name, so once I switch away, I might lose them unless I reattach with `git switch -c new-branch` first. It's how Git says 'you're off the map, name a destination before you save.'"

## Branch recovery — expected commands

```bash
git switch main
git branch -D draft/detailed
git reflog                          # find the last commit on draft/detailed
git branch draft/detailed <sha>     # recreate the pointer
```

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| "Your local changes would be overwritten" on switch | Uncommitted edits | Commit or `git stash` first |
| Forgot to switch before branching-off | Branched from the wrong commit | Delete with `-D`, start over, or `git branch -f <name> <sha>` |
| `git branch -d draft/x` refuses | Branch has unmerged work | `-D` to force (know what you lose), or merge first |
| Mentee confuses `-` with a branch name | `git switch -` is "previous branch" idiom | Explain: like `cd -` in a shell |

## Grading rubric (quick)

- 3 branches with 2 commits each: 30
- `git log --graph` screenshot committed in `branching-notes.md`: 20
- "What is a branch?" paragraph accurate: 20
- Detached HEAD paragraph accurate: 15
- Recovery commands correct: 15

Pass: 70.

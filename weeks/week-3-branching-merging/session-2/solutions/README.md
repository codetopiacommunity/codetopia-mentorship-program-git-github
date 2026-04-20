# Solutions — Week 3 · Session 2

> **Mentor only.** Don't peek until you've tried.

## Part 1 — Fast-forward

Expected output:

```
Updating 90deadb..c4a2f01
Fast-forward
 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Graph after:

```
* c4a2f01 (HEAD -> main) fix: clarify placeholder
* 90deadb feat: initial README
```

Model answer: *"No divergence — `feature/typos` was a direct descendant of `main`. Git just moved the `main` pointer forward."*

## Part 2 — Three-way merge

Expected graph after:

```
*   1f3e2a4 (HEAD -> main) Merge branch 'feature/intro'
|\
| * a2c3b01 docs: add intro
* | 5d4e1f2 docs: add license section
|/
* c4a2f01 fix: clarify placeholder
* 90deadb feat: initial README
```

Model answer: *"Both `main` and `feature/intro` moved after their common ancestor, so Git couldn't fast-forward — it created a merge commit with two parents."*

## Part 3 — Conflict resolution

Pre-resolution file (abbreviated):

```
<<<<<<< HEAD
# Merge Lab — A Git Playground
=======
# Merge Lab — Learn By Breaking Things
>>>>>>> feature/tagline

## Features
...
```

Acceptable resolutions:

- Combine intents: `# Merge Lab — A Git Playground for Breaking Things Safely`
- Pick one explicitly (and document *why* in MERGE-LOG.md)

Key thing to check: **no markers remain** (`grep -n '<<<<<<<\|=======\|>>>>>>>' README.md` should return nothing).

Expected graph after:

```
*   e7b2c1a (HEAD -> main) Merge branch 'feature/tagline'
|\
| * d4c0ffe feat: add tagline
* | 9f2a0c1 feat: add alt tagline
|/
*   1f3e2a4 Merge branch 'feature/intro'
...
```

## Part 4 — Abort

After `git merge --abort`:

- `git status` — clean.
- README first line — the one from `main` just before the attempted merge (the "alt tagline" from earlier, say).
- `feature/broken` still exists as a branch; `-D` it.

Model answer: *"Use `--abort` whenever you realize mid-merge that you're resolving wrong, that you merged the wrong branch, or that this merge should be done later. It's cost-free — you're back where you started."*

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| FF merge didn't happen — got a merge commit | Mentee made a commit on `main` in Part 1 | Start over — keep `main` unchanged in Part 1 |
| "Already up to date." in Part 2 | Branch merged earlier, or main has no new commits | Check `git log --graph --all`; redo the diverging commit on main |
| Committed the markers | `git add` without opening the file | `git reset --soft HEAD~1`, fix, recommit |
| README contents scrambled after conflict | Resolved by concatenation, not by editing | Reset to the merge state and try again |
| `git merge --abort` says "no merge in progress" | Already committed the merge | Use `git reset --hard ORIG_HEAD` to undo the merge commit |

## Grading rubric (quick)

- Part 1 (FF) correct + explained: 20
- Part 2 (3-way) correct + explained: 25
- Part 3 (conflict) resolved cleanly, both intents thought about: 35
- Part 4 (abort) correct + explained: 20

Pass: 70.

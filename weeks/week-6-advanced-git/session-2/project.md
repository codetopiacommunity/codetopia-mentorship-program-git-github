# Session 2 Project — "Rescue Mission"

> **XP:** 50

## Brief

You will deliberately break a repo, then fix it using each of the four tools: `reflog`, `cherry-pick`, `stash`, `bisect`. Document every step.

## Setup

```bash
mkdir rescue-mission && cd rescue-mission
git init
for i in 1 2 3 4 5 6 7 8 9 10; do
  echo "line $i" >> log.txt
  git add log.txt
  git commit -m "feat: add line $i"
done
```

You now have 10 commits.

## Steps

### Part A — reflog

1. Hard-reset 5 commits back: `git reset --hard HEAD~5`.
2. Confirm your log now shows only 5 commits.
3. Use `git reflog` to find the old top SHA.
4. Restore using `git reset --hard <sha>`.

### Part B — cherry-pick

1. Create a new branch from 3 commits back: `git switch -c hotfix HEAD~3`.
2. On `main`, find the SHA of a commit from the top half.
3. Cherry-pick it onto `hotfix`.
4. Compare the original SHA with the new one (`git log --oneline` on both branches) and note that they differ.

### Part C — stash

1. Switch back to `main`.
2. Edit `log.txt` without committing.
3. `git stash push -m "mid-edit"` and verify `git status` is clean.
4. Switch to `hotfix`, make a tiny commit, switch back to `main`.
5. `git stash pop` and confirm your edits returned.
6. Commit them conventionally.

### Part D — bisect

1. Create a "bug" by editing line 6 of `log.txt` to say `BUG` in a commit.
2. Add 3 more normal commits on top.
3. Run `git bisect start`, mark `HEAD` bad and the initial commit good.
4. At each step, inspect `log.txt` — if line 6 says `BUG`, mark bad; otherwise good.
5. Let bisect find the culprit. Note its SHA.
6. `git bisect reset`.

## Deliverable

Submit your work as follows:

1. **In your project's `screenshots/` folder** (the submission of record): add at least one screenshot — typically the `git reflog` moment where you found the lost SHA, or the bisect "first bad commit" output. Name them `01-reflog.png`, `02-bisect.png`, etc.
2. **In the WhatsApp group** (informal share): drop a copy of your best screenshot so the cohort can cheer you on.
3. A `rescue-mission/` repo containing:

   - The repo in its final state.
   - The `screenshots/` folder.
   - A `RESCUE-LOG.md` with sections A/B/C/D. For each part, include:
     - The commands you ran.
     - What you observed (terminal output snippets are great).
     - A one-sentence reflection on *when you would use this tool in real life*.

See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

## Stretch (+25 XP)

- Do Part D with `git bisect run` and a shell script that greps for `BUG` in `log.txt`. Include the script in the repo.
- Add a scenario of your own: delete a branch, then use `reflog` to resurrect it.

## Checks before submitting

- [ ] All four tools appear in `RESCUE-LOG.md`.
- [ ] You can explain, for each tool, *one real situation* you'd use it.
- [ ] `git bisect reset` was run at the end (no lingering bisect state).

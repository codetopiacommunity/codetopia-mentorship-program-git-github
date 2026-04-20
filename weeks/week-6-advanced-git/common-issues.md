# Week 6 — Common Issues

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| `fatal: It seems that there is already a rebase-merge directory` | A previous rebase was not finished. | `git rebase --abort` to bail out, or `git rebase --continue` if you resolved the conflicts. |
| Editor opens with `noop` during `rebase -i` | The base you chose is ahead of HEAD. | Use a commit *behind* HEAD, e.g. `git rebase -i HEAD~5`. |
| Commits vanished after a bad rebase | History was rewritten but the old commits still exist. | `git reflog`, find the old `HEAD@{n}`, then `git reset --hard HEAD@{n}`. |
| `error: cannot 'squash' without a previous commit` | First line of the todo list was marked `squash`. | The top commit must be `pick`. Squash into it, not from it. |
| "Your branch and 'origin/main' have diverged" after rebase | You rebased commits you had already pushed. | If you're alone on the branch: `git push --force-with-lease`. If others are on it: *do not force-push* — revert the rebase via reflog. |
| `git stash pop` conflicts | Stashed changes touch the same lines as current work. | Resolve the conflicts manually, then `git stash drop` to clean up the stash entry. |
| `git cherry-pick` says "empty commit" | The change is already present on this branch. | `git cherry-pick --skip` or `--abort`. |
| `git bisect` finishes on the wrong commit | You mislabeled a commit as good/bad. | `git bisect reset`, start over, and be careful with `good`/`bad` tags. |
| `--amend` rewrote a commit others had pulled | You amended a pushed commit. | Coordinate with teammates. They'll need to `git fetch` and `git reset --hard origin/<branch>`. Don't do this again on shared branches. |
| Detached HEAD after checking out a commit | Normal — you're not on a branch. | `git switch -c rescue-branch` to save the state as a new branch. |
| Conflict markers (`<<<<<<<`) still in files after rebase | You forgot to `git add` after fixing conflicts. | Edit the files, remove markers, `git add <file>`, then `git rebase --continue`. |

If none of the above match, check [`../../troubleshooting/`](../../troubleshooting/) or ask in the cohort channel with the exact error text.

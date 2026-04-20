# Week 3 — Common Issues

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| `fatal: A branch named 'x' already exists.` | Branch name collision | `git branch -D x` (if safe) or pick another name |
| `error: Your local changes would be overwritten by checkout` | Uncommitted work conflicts with target branch | `git stash` → switch → `git stash pop`, or commit first |
| Switched branch and my files vanished | They belong to the other branch; you're seeing the right working tree | Switch back with `git switch -` |
| `Already up to date.` on a merge you expected to do something | Target branch has nothing new for you | Check `git log --oneline --graph --all` |
| "Fast-forward" merge but you wanted a merge commit | FF is the default when possible | `git merge --no-ff <branch>` |
| `CONFLICT (content)` | Both branches changed the same region | Open the file, edit between markers, `git add`, `git commit` |
| Merge went wrong, want to start over | Mid-merge panic | `git merge --abort` |
| Deleted a branch but want it back | Local branch deleted | `git reflog`, then `git branch <name> <sha>` |
| `error: The branch 'x' is not fully merged.` | `-d` refuses to delete unmerged | Merge first, or `-D` to force (know what you're losing) |
| `HEAD detached at <sha>` | You `switch`-ed to a commit, not a branch | `git switch -c new-branch` or `git switch -` |
| Conflict markers committed by accident | Didn't finish editing | `git revert HEAD` or fix and `--amend` (if not pushed) |
| `git switch` not recognized | Git < 2.23 | Upgrade, or use `git checkout -b` / `git checkout` |

If your issue isn't here, see [`../../troubleshooting/merge-conflicts.md`](../../troubleshooting/merge-conflicts.md) or post in **Discussions → Q&A** with:
1. `git status`
2. `git log --oneline --graph --all -n 10`
3. The exact error message

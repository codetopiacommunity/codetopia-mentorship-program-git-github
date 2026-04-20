# Week 2 — Common Issues

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| `git diff` shows nothing after editing | You already staged the change | `git diff --staged` (or `--cached`) |
| `git log` opens a pager you can't escape | That's `less` | Press `q` to quit; add `--no-pager` to skip it |
| `git log` is empty | No commits yet | Make your first commit |
| `git log --oneline --graph` is ugly | Terminal doesn't support the glyphs | Install a Nerd Font or omit `--graph` |
| `.gitignore` has no effect on an already-tracked file | Git only ignores *untracked* files | `git rm --cached <file>` then commit |
| `.DS_Store` keeps coming back (macOS) | Not in `.gitignore` yet, or added before | Ignore it *and* `git rm --cached .DS_Store` |
| `git restore` not recognized | Git < 2.23 | Upgrade Git, or use `git checkout -- <file>` |
| Lost uncommitted work after `git restore <file>` | That's what it does | Check editor local history; next time, `git stash` first |
| `git reset --hard` nuked your work | That's also what it does | Try `git reflog` — commits may still exist |
| `git commit --amend` changed a pushed commit's hash | Amending rewrites history | Force-push only to *your own* branches: `git push --force-with-lease` |
| `HEAD detached at <sha>` after `git checkout <sha>` | You're on a commit, not a branch | `git switch -` to go back |
| Want to unstage without losing edits | `git reset` is confusing | `git restore --staged <file>` |

If your issue isn't here, see [`../../troubleshooting/reset-and-restore.md`](../../troubleshooting/reset-and-restore.md) or post in **Discussions → Q&A** with the output of `git status` and `git log --oneline -n 5`.

# Week 1 — Common Issues

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| `git: command not found` (Windows) | Terminal opened before install finished | Close & reopen terminal |
| `xcrun: error: invalid active developer path` (Mac) | Missing Xcode CLI tools | `xcode-select --install` |
| `Author identity unknown` | Skipped `git config user.name/email` | Set them globally |
| Commits all stuck on `master` | Old default branch | `git config --global init.defaultBranch main` then re-init |
| `nothing to commit, working tree clean` after editing | Forgot `git add` | `git add <file>` then commit |
| Committed a typo in the message | Last commit only | `git commit --amend -m "new message"` |
| Wrong file committed | Just made the commit | `git reset HEAD~1 --soft`, fix, recommit |
| Accidentally `git init`-ed inside another repo | Nested `.git/` directories | `rm -rf .git` *only* in the inner folder |
| Confused by "modified" vs "staged" | Mental model | Re-watch the 3-state diagram in lecture notes |

If your issue isn't here, post in **Discussions → Q&A** with:
1. The exact command you ran
2. The full error message
3. The output of `git status`

# Week 4 — Common Issues

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| `Permission denied (publickey)` | SSH key not generated or not added to GitHub | See [`../../../troubleshooting/permission-denied-publickey.md`](../../../troubleshooting/permission-denied-publickey.md) |
| `remote: Support for password authentication was removed` | Used GitHub password over HTTPS | Use a Personal Access Token or switch to SSH |
| `fatal: remote origin already exists` | Ran `git remote add origin` twice | `git remote set-url origin <new-url>` |
| `src refspec main does not match any` | No commits yet, or branch named `master` | Make a commit first; rename with `git branch -M main` |
| `! [rejected] main -> main (fetch first)` | Remote has commits you don't have | `git pull --rebase origin main` then push |
| `Your branch is behind 'origin/main' by N commits` | Someone else pushed | See [`../../../troubleshooting/branch-behind-origin.md`](../../../troubleshooting/branch-behind-origin.md) |
| `fatal: refusing to merge unrelated histories` | Local repo and remote repo were initialized separately | `git pull origin main --allow-unrelated-histories` |
| `Could not resolve host: github.com` | No internet, or DNS issue | Check Wi-Fi; retry |
| Push succeeds but GitHub shows nothing | Pushed to the wrong branch or wrong repo | `git remote -v` and `git branch -vv` to verify |
| Asked for username/password on every push | HTTPS without credential helper | `git config --global credential.helper osxkeychain` (macOS) / `manager` (Win) |
| `ssh: connect to host github.com port 22: Connection refused` | Network blocks port 22 | Use HTTPS, or SSH over port 443 (`ssh.github.com:443`) |

If your issue isn't here, post in **Discussions → Q&A** with:

1. The exact command you ran
2. The full error message
3. The output of `git remote -v` and `git status`

# Solutions — Week 4 Session 1

> **Mentor only.** Don't peek until you've tried.

## Expected `git remote -v` output

```
origin  git@github.com:ada/hello-remote.git (fetch)
origin  git@github.com:ada/hello-remote.git (push)
```

Two lines. One label (`origin`), two flows (`fetch` / `push`). HTTPS URLs are equally valid.

## Expected `ssh -T git@github.com` output

```
Hi ada! You've successfully authenticated, but GitHub does not provide shell access.
```

The "does not provide shell access" phrase is the success signal — mentees routinely read it as an error.

## Expected `git push -u origin main` output

```
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 220 bytes | 220.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:ada/hello-remote.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

Key phrases to verify:

- `[new branch]      main -> main`
- `set up to track 'origin/main'`

## Model answer — "What does `-u` do?"

> "`-u` (short for `--set-upstream`) tells Git to remember that my local `main` branch is paired with `origin/main`. After one `push -u`, I can just run `git push` or `git pull` with no arguments."

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| `fatal: remote origin already exists` | Mentee ran `remote add` twice | `git remote set-url origin <url>` |
| `Permission denied (publickey)` | Key not added to agent or GitHub | See troubleshooting doc |
| `src refspec main does not match any` | No commit yet, or branch is `master` | Commit first; `git branch -M main` |
| `refusing to merge unrelated histories` later | Checked "Initialize with README" on GitHub | `git pull origin main --allow-unrelated-histories` |
| `Support for password authentication was removed` | Typed GitHub password instead of PAT | Create a PAT; paste as password |

## Stretch solution

```bash
git remote add backup git@github.com:ada/hello-remote-backup.git
git push backup main
git remote -v
# origin  git@github.com:ada/hello-remote.git         (fetch)
# origin  git@github.com:ada/hello-remote.git         (push)
# backup  git@github.com:ada/hello-remote-backup.git  (fetch)
# backup  git@github.com:ada/hello-remote-backup.git  (push)
```

Reinforce: **remotes are just named bookmarks**. You can have as many as you want.

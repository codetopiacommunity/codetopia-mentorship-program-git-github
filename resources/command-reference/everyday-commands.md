# Everyday Commands — Reference

The 20 commands you'll use 90% of the time.

## Inspect

| Command | What it does |
| ------- | ------------ |
| `git status` | Show working tree state |
| `git log --oneline -10` | Last 10 commits |
| `git diff` | Unstaged changes |
| `git diff --staged` | Staged changes |
| `git show <commit>` | Inspect a specific commit |

## Stage / Commit

| Command | What it does |
| ------- | ------------ |
| `git add <file>` | Stage a file |
| `git add -p` | Interactively stage hunks |
| `git commit -m "..."` | Commit staged changes |
| `git commit --amend` | Rewrite last commit |

## Branch

| Command | What it does |
| ------- | ------------ |
| `git switch <branch>` | Switch branches |
| `git switch -c <branch>` | Create + switch |
| `git branch -d <branch>` | Delete (safe) |
| `git merge <branch>` | Merge `<branch>` into current |

## Remote

| Command | What it does |
| ------- | ------------ |
| `git clone <url>` | Copy a remote repo |
| `git pull` | Fetch + merge |
| `git push` | Push local commits |
| `git fetch` | Download without merging |

## Undo

| Command | What it does |
| ------- | ------------ |
| `git restore <file>` | Drop unstaged changes |
| `git restore --staged <file>` | Unstage |
| `git revert <commit>` | Safe undo (new commit) |
| `git reset --hard HEAD~1` | Dangerous: nukes last commit |

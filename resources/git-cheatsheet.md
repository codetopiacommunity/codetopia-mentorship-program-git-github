# Git Cheatsheet

Print this. Tape it next to your monitor.

## Setup (once per machine)

```bash
git config --global user.name  "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --global pull.rebase false
```

## Daily Workflow

```bash
git status                   # what's going on?
git add <file>               # stage one file
git add .                    # stage everything in cwd
git commit -m "feat: ..."    # commit staged changes
git log --oneline -10        # last 10 commits, one line each
git diff                     # unstaged changes
git diff --staged            # staged changes
```

## Branches

```bash
git branch                   # list branches
git switch -c feature-x      # create + switch
git switch main              # switch
git merge feature-x          # merge into current branch
git branch -d feature-x      # delete (safe)
```

## Remotes

```bash
git remote -v                # list remotes
git push origin main         # push
git pull                     # fetch + merge
git fetch                    # fetch only
git clone <url>              # copy a remote repo
```

## Undo

```bash
git restore <file>                # discard unstaged changes
git restore --staged <file>       # unstage
git commit --amend                # rewrite last commit
git reset --soft HEAD~1           # undo commit, keep changes staged
git reset --hard HEAD~1           # nuke last commit (careful!)
git revert <commit>               # safe undo via new commit
```

## Inspect

```bash
git log --graph --oneline --all   # pretty history
git show <commit>                 # what changed in a commit
git blame <file>                  # who changed each line
git reflog                        # your safety net
```

## Stash

```bash
git stash                  # shelf current changes
git stash pop              # bring them back
git stash list             # what's on the shelf
```

# Resources — Week 3 · Session 2

## Reading

- [Pro Git §3.2 — Basic Branching & Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- [Pro Git §3.5 — Advanced Merging](https://git-scm.com/book/en/v2/Git-Branching-Advanced-Merging)
- [GitHub Docs: Resolving a merge conflict on the command line](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)
- [Atlassian — Merging vs Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

## Watching

- [Git Merge in 4 minutes (YouTube)](https://www.youtube.com/results?search_query=git+merge+in+4+minutes)
- [Merge conflicts explained (YouTube)](https://www.youtube.com/results?search_query=git+merge+conflicts+explained)

## Interactive practice

- [Learn Git Branching](https://learngitbranching.js.org/) — do the "Ramping Up" and "Mixed Bag" sections for merge practice.

## Inside this repo

- Troubleshooting: [`../../../troubleshooting/merge-conflicts.md`](../../../troubleshooting/merge-conflicts.md)
- Cheatsheet: [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- Glossary: [`../../../resources/glossary.md`](../../../resources/glossary.md)
- Commit message guide: [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md)

## Command reference card

```bash
# Merge another branch into the current branch
git merge feature/x

# Force a merge commit even on FF
git merge --no-ff feature/x

# Abort a merge in progress
git merge --abort

# Resolution workflow
# 1. edit the conflicted file(s)
# 2. git add <files>
# 3. git status (verify "All conflicts fixed")
# 4. git commit
```

## Configure your editor for merge conflicts

### VS Code / Cursor

Conflicts show "Accept Current Change | Accept Incoming Change | Accept Both Changes | Compare Changes" buttons above the markers. Click the one you want, save, `git add`.

### Set Git's default editor (once)

```bash
git config --global core.editor "code --wait"       # VS Code
git config --global core.editor "nano"              # nano
git config --global core.editor "vim"               # vim
```

# Resources — Week 3 · Session 1

## Reading

- [Pro Git §3.1 — Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
- [Pro Git §3.2 — Basic Branching & Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- [GitHub Docs: About branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)
- [Atlassian — git branch](https://www.atlassian.com/git/tutorials/using-branches)
- [GitHub Flow explained](https://docs.github.com/en/get-started/using-github/github-flow)

## Interactive practice

- [Learn Git Branching](https://learngitbranching.js.org/) — drag-and-drop graph visualizer. Do at least levels 1 and 2.
- [Oh My Git!](https://ohmygit.org/) — free game that teaches branch mechanics.

## Watching

- [Git branches in 100 seconds (Fireship)](https://www.youtube.com/results?search_query=git+branches+100+seconds)

## Inside this repo

- Cheatsheet: [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- Glossary: [`../../../resources/glossary.md`](../../../resources/glossary.md)
- Commit message guide: [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md)

## Command reference card

```bash
# Create + switch
git switch -c feat/login

# List
git branch            # local
git branch -a         # include remotes
git branch -v         # with last commit

# Switch
git switch main
git switch -          # previous branch

# Rename
git branch -m old new
git branch -m new     # rename current

# Delete
git branch -d feat/login      # safe
git branch -D feat/login      # force

# Inspect
git log --oneline --graph --decorate --all
```

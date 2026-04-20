# Resources — Week 2 · Session 2

## Reading

- [Pro Git §2.4 — Undoing Things](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things)
- [Pro Git §7.10 — Rewriting History](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)
- [GitHub — Ignoring files](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files)
- [Atlassian — Resetting, Checking Out & Reverting](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting)
- [Julia Evans — Oh Shit, Git!?!](https://ohshitgit.com/)

## Templates

- [github/gitignore](https://github.com/github/gitignore) — language-specific `.gitignore` files maintained by GitHub
- [gitignore.io](https://www.toptal.com/developers/gitignore) — generator; pick your OS, editor, language

## Inside this repo

- [`../../../templates/.gitignore-template`](../../../templates/.gitignore-template)
- [`../../../troubleshooting/reset-and-restore.md`](../../../troubleshooting/reset-and-restore.md)
- [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- [`../../../resources/glossary.md`](../../../resources/glossary.md)

## Command reference card

```bash
# Untrack a tracked file
git rm --cached <file>

# Throw away working edits
git restore <file>

# Unstage
git restore --staged <file>

# Fix last commit
git commit --amend             # edit message and/or add staged files
git commit --amend --no-edit   # keep message

# Reset modes
git reset --soft  HEAD~1       # keep staged
git reset --mixed HEAD~1       # unstage (default)
git reset --hard  HEAD~1       # delete

# Time machine
git reflog
git reset --hard HEAD@{n}

# Safe undo of a pushed commit
git revert <sha>
```

# Resources — Week 2 · Session 1

## Reading

- [Pro Git §2.3 — Viewing the Commit History](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)
- [Pro Git §7.13 — Debugging with Git (blame, pickaxe)](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git)
- [GitHub Docs: About commit history](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/viewing-and-comparing-commits/commit-branch-and-tag-shortcuts)
- [Atlassian — git log tutorial](https://www.atlassian.com/git/tutorials/git-log)

## Watching

- [Git log like a pro (YouTube, 8 min)](https://www.youtube.com/results?search_query=git+log+like+a+pro)
- [Understanding git diff (YouTube, 12 min)](https://www.youtube.com/results?search_query=understanding+git+diff)

## Inside this repo

- Cheatsheet: [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- Glossary: [`../../../resources/glossary.md`](../../../resources/glossary.md)
- Commit message guide: [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md)
- Troubleshooting: [`../../../troubleshooting/reading-diffs.md`](../../../troubleshooting/reading-diffs.md)

## Cheat commands worth aliasing

```bash
git config --global alias.lg  "log --oneline --graph --decorate --all -n 20"
git config --global alias.st  "status -sb"
git config --global alias.df  "diff --word-diff"
```

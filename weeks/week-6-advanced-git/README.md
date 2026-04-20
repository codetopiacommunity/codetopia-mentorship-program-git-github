# Week 6 — Advanced Git

> **XP:** 450 (200 + 200 + 50 stretch on capstone)

By now you can commit, branch, merge, and open a PR. This week we learn the tools that separate "I can use Git" from "I'm comfortable fixing a mess in Git."

## Theme

Your history is a product. A clean, readable log of commits is a gift to every future teammate — including future-you. We'll learn how to reshape history deliberately, and how to recover when something goes wrong.

## Sessions

| # | Title | Focus |
|---|-------|-------|
| 1 | [Rewriting History](./session-1/README.md) | `git rebase -i`, squash, reword, `--amend` |
| 2 | [Recovery & Power Tools](./session-2/README.md) | `reflog`, `cherry-pick`, `stash`, `bisect` |

## Capstone

[**Clean up a messy history.**](./capstone/README.md) You'll clone a repo with 10+ scrappy commits and rebase it into a presentable log, then write up what you did and why.

## Learning objectives

By the end of the week, you should be able to:

- Squash, reword, reorder, and drop commits with interactive rebase.
- Explain *why* rewriting shared history is dangerous.
- Recover a "lost" commit using `git reflog`.
- Move a specific commit between branches with `git cherry-pick`.
- Pause work safely with `git stash` and resume it.
- Find the commit that introduced a bug with `git bisect`.

## The rule that governs this week

> **Never rewrite history that has been pushed and that other people may have based work on.**

Everything else is negotiable. This one is not. We'll come back to this rule several times.

## Common issues

See [`common-issues.md`](./common-issues.md) for a quick lookup when something goes sideways.

## Cross-refs

- [`../../templates/`](../../templates/) — commit-message and PR templates.
- [`../../resources/cheatsheet.md`](../../resources/cheatsheet.md) — the commands you'll reach for.
- [`../../troubleshooting/`](../../troubleshooting/) — when rebase goes wrong.

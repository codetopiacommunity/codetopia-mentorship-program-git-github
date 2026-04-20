# Week 2 · Core Workflow

> **Total XP:** 400 — split as 75 (S1) + 75 (S2) + 200 (capstone) + 50 (stretch).
> **Outcome:** Mentees can inspect, read, and *surgically undo* changes to a repo. They leave the week unafraid of `git log`, `git diff`, `git restore`, and `git reset`.

## Sessions

| # | Title | Folder |
| - | ----- | ------ |
| 1 | Working with Files — Diffing & Reading History | [`session-1/`](session-1/) |
| 2 | `.gitignore` & Undoing Changes Safely | [`session-2/`](session-2/) |

## Capstone

Build a multi-file **recipe collection** repo with a real `.gitignore`, intentional atomic history, and at least one commit fixed with `git commit --amend`. See [`capstone/`](capstone/).

## Big Picture

Week 1 taught you how to *record* history. Week 2 teaches you how to *read it, compare it, and rewrite it safely*.

By the end of this week mentees should be able to:

1. Read a diff — unified-diff format, `---`/`+++`, hunk headers.
2. Navigate history with `git log` (flags: `--oneline`, `--graph`, `--stat`, `-p`, `-n`, `--author`, `--since`).
3. Inspect any past commit with `git show`.
4. Write a `.gitignore` that covers OS, editor, and language junk.
5. Undo changes at three levels: **working tree**, **index**, **history** — and explain *which one* `git restore` vs `git reset --soft/--mixed/--hard` touches.
6. Fix the last commit with `git commit --amend`.

## Common Issues

See [`common-issues.md`](common-issues.md).

## Cross-references

- Cheatsheet: [`../../resources/git-cheatsheet.md`](../../resources/git-cheatsheet.md)
- Commit message guide: [`../../templates/commit-message-guide.md`](../../templates/commit-message-guide.md)
- Gitignore template: [`../../templates/.gitignore-template`](../../templates/.gitignore-template)
- Troubleshooting: [`../../troubleshooting/`](../../troubleshooting/)

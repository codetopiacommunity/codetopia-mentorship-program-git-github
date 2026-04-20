# Week 3 · Branching & Merging

> **Total XP:** 450 — split as 100 (S1) + 100 (S2) + 200 (capstone) + 50 (stretch).
> **Outcome:** Mentees can create, switch, merge, and — most importantly — *reason about* branches. They stop fearing merge conflicts because they've deliberately made and resolved one.

## Sessions

| # | Title | Folder |
| - | ----- | ------ |
| 1 | Branches — Movable Pointers | [`session-1/`](session-1/) |
| 2 | Merging & Conflict Resolution | [`session-2/`](session-2/) |

## Capstone

A **feature playground** repo where you create three feature branches, merge two cleanly, and deliberately engineer + resolve a conflict on the third. See [`capstone/`](capstone/).

## Big Picture

A branch is not a folder. A branch is not a copy of your code. A branch is **a lightweight, movable pointer to a commit**.

Everything else — fast-forward merges, 3-way merges, conflicts — falls out of that one fact.

By the end of this week mentees should be able to:

1. Draw the branch-as-pointer mental model on a whiteboard.
2. Create, list, rename, and delete branches.
3. Use `git switch` (and know what `git checkout` used to do).
4. Predict whether a merge will be fast-forward or three-way *before* running it.
5. Read conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) and resolve by editing.
6. Abort a merge safely with `git merge --abort` when it goes sideways.

## Common Issues

See [`common-issues.md`](common-issues.md).

## Cross-references

- Cheatsheet: [`../../resources/git-cheatsheet.md`](../../resources/git-cheatsheet.md)
- Troubleshooting: [`../../troubleshooting/merge-conflicts.md`](../../troubleshooting/merge-conflicts.md)
- Commit message guide: [`../../templates/commit-message-guide.md`](../../templates/commit-message-guide.md)

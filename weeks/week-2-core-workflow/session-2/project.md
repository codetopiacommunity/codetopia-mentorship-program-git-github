# Project — Week 2 · Session 2

> **XP:** 50

## What you'll do

Build an "undo lab" repo where you deliberately make four classes of mistakes and then fix each one with the right tool.

## Steps

### Setup

```bash
mkdir undo-lab && cd undo-lab
git init
```

### Mistake 1 — Committed a junk file

1. Create `notes.md` with a few lines, and also create a `.DS_Store` file (or `Thumbs.db`).
2. `git add .` and commit *both*.
3. Verify the junk file is in the commit: `git show HEAD --stat`.
4. **Fix it:** write a `.gitignore`, `git rm --cached` the junk file, and commit.

### Mistake 2 — Staged the wrong file

1. Create two files: `keep.md`, `later.md`.
2. `git add keep.md later.md`.
3. Realize `later.md` isn't ready.
4. **Fix it:** `git restore --staged later.md`, then commit only `keep.md`.

### Mistake 3 — Typo in the last commit message

1. Commit something with an intentionally wrong message (e.g., `docs: adds notes` — past tense).
2. **Fix it:** `git commit --amend -m "<better message>"`.

### Mistake 4 — Last two commits should have been one

1. Make two commits that logically belong together.
2. **Fix it:** `git reset --soft HEAD~2`, recommit as one.

### Bonus — Recovery with reflog

1. Make a commit with content you'd hate to lose.
2. Run `git reset --hard HEAD~1`.
3. Panic briefly.
4. `git reflog`, then `git reset --hard HEAD@{1}`.

## Deliverable

A single `recovery-log.md` file committed to the repo with four sections (one per mistake) documenting:

- **What I did wrong** (the exact command)
- **What I ran to fix it** (the exact command)
- **What `git status` looked like before and after**

Commit it:

```bash
git add recovery-log.md
git commit -m "docs: add recovery log"
```

Then submit your work as follows:

1. **In your project's `screenshots/` folder** (the submission of record): add at least one screenshot — typically a clean `git log --oneline` and a glimpse of your `recovery-log.md`. Name them `01-git-log.png`, `02-recovery-log.png`, etc.
2. **In the WhatsApp group** (informal share): drop a copy of your best screenshot so the cohort can cheer you on.
3. **In Discussions → Week 2** (additional channel): post the output of `git log --oneline`.

See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

## Stretch goal (+25 XP)

Do the bonus reflog recovery and include the `git reflog` excerpt in your `recovery-log.md`.

## Stuck?

- [`../common-issues.md`](../common-issues.md)
- [`../../../troubleshooting/reset-and-restore.md`](../../../troubleshooting/reset-and-restore.md)
- Post in **Discussions → Q&A**.

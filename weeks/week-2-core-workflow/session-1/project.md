# Project — Week 2 · Session 1

> **XP:** 50

## What you'll do

Build a small "study-notes" repo, then go on a guided tour of its own history using only *read-only* Git commands.

## Steps

1. Create and enter a new folder:

   ```bash
   mkdir study-notes && cd study-notes
   git init
   ```

2. Make **at least 6 commits** that build up a `README.md` with these sections. One commit per section:

   - Title
   - `## Git` with 3 bullet points
   - `## GitHub` with 3 bullet points
   - `## Markdown` with 3 bullet points
   - A `## Resources` section with 2 links
   - A typo fix in any of the above (`fix:` prefix)

   Use conventional commit messages. See [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md).

3. Run the **history tour**, saving each output to a file called `tour.md`:

   ```bash
   git log --oneline
   git log --oneline --graph --decorate
   git log --stat -n 3
   git show HEAD
   git show HEAD~2 -- README.md
   git blame README.md
   ```

   Paste each command and its output into `tour.md` under a clear heading.

4. Commit `tour.md`:

   ```bash
   git add tour.md
   git commit -m "docs: add history tour"
   ```

## Deliverable

Submit your work as follows:

1. **In your project's `screenshots/` folder** (the submission of record): add at least one screenshot — typically a clean `git log --oneline` and a glimpse of your `tour.md`. Name them `01-git-log.png`, `02-tour.png`, etc.
2. **In the WhatsApp group** (informal share): drop a copy of your best screenshot so the cohort can cheer you on.
3. **In Discussions → Week 2** (additional channel): post the output of `git log --oneline`, a link (or paste) of `tour.md`, and a short paragraph (3–5 sentences) answering: *"If I had to explain `git diff` vs `git diff --staged` to a friend, I'd say..."*

See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

## Stretch goal (+25 XP)

Set up the three aliases from [`resources.md`](resources.md) (`lg`, `st`, `df`) and include the output of `git config --get-regexp alias` in your post.

## Stuck?

- [`../common-issues.md`](../common-issues.md)
- [`../../../troubleshooting/reading-diffs.md`](../../../troubleshooting/reading-diffs.md)
- Post in **Discussions → Q&A** with your `git status` and the exact error.

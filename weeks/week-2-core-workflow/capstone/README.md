# Week 2 Capstone — Recipe Collection

> **XP:** 200 base + up to 50 stretch

## Brief

Build a small **recipe collection** repo. Multiple files, intentional history, proper `.gitignore`, and at least one commit fixed with `git commit --amend`.

The point is not the recipes. The point is to demonstrate you can *shape* a repo's history, not just produce commits by accident.

## Requirements

- A `screenshots/` folder in your project containing at least 2 screenshots showing the work in action (e.g., `git log --oneline`, your `HISTORY.md`, or the `.gitignore` proof). See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).
- Brand-new repo created with `git init`.
- A `README.md` at the root describing the collection.
- A `recipes/` directory with **at least 3** recipe files (markdown, one recipe per file).
- A `.gitignore` — use [`../../../templates/.gitignore-template`](../../../templates/.gitignore-template) as a base and add anything else appropriate.
- **At least one file** that *should* be ignored exists on disk and is correctly ignored (e.g., a `.DS_Store`, a scratch `notes.tmp`, or a `secrets.env`). Mentor checks with `git status` — it must be clean even with those files present.
- **At least 10 commits**, each atomic and conventionally formatted. See [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md).
- **At least one commit amended** with `git commit --amend`. Document *which one* in `HISTORY.md`.
- A `HISTORY.md` file at the root with:
  - A bulleted summary of your commit history (copy `git log --oneline`).
  - A section "Amend I'm proud of" explaining what you amended and why.
  - A section "What `.gitignore` is hiding for me" listing at least 2 patterns and why.

## Deliverable

Submit your work as follows:

1. **Open a PR** (the submission of record) adding your project under `projects-showcase/week-2-projects/<your-handle>/`, with your `screenshots/` folder included. See [`../../../CONTRIBUTING.md`](../../../CONTRIBUTING.md).

   Include in your PR description:

   - The output of `git log --oneline`.
   - A one-paragraph reflection: *"The mistake I made and how I fixed it."*

2. **In the WhatsApp group** (the celebration): once your PR is open, share your best screenshot and the PR link so the cohort can cheer you on.

## Grading

See [`rubric.md`](rubric.md). Pass = 70+. Use [`checklist.md`](checklist.md) before submitting.

## Stretch (+50 XP)

- **+15** — Use `git reset --soft HEAD~N` at least once to squash two logically-related commits into one, and document it in `HISTORY.md`.
- **+15** — Use a `revert` commit to undo a deliberately-broken recipe, rather than amending. Document why.
- **+20** — Push the repo to your own GitHub account and link it from the PR. Include a screenshot of the commit graph on GitHub.

## Cross-references

- [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md)
- [`../../../templates/.gitignore-template`](../../../templates/.gitignore-template)
- [`../../../troubleshooting/reset-and-restore.md`](../../../troubleshooting/reset-and-restore.md)
- [`../common-issues.md`](../common-issues.md)

# Week 4 Capstone — "Pushed to Prove It"

> **XP:** 200 base + up to 50 stretch

## Brief

Create a brand-new, README-only project in a fresh local repo, push it to **your own** GitHub account, and deliver the commits in **two separate pushes**. The content doesn't matter — a book list, a song list, a favorite-meals list, your picks of the year. What's being graded is that you moved a real repo through the full local → GitHub pipeline cleanly.

## Requirements

- Brand-new local repo created with `git init`.
- A meaningful `README.md` (minimum 3 sections of real content — no lorem ipsum).
- A `.gitignore` (use [`../../../templates/.gitignore-template`](../../../templates/.gitignore-template)).
- **At least 5 atomic commits** with conventional messages (`feat:`, `docs:`, `fix:`, ...).
- The 5 commits delivered in **two pushes** (e.g., 3 commits → push → 2 more commits → push).
- A GitHub repo **on your own account** (public or private).
- `git remote -v` shows a single `origin` remote.
- Authentication working (SSH greeting or no-prompt HTTPS push).

## Deliverable

Open a PR against this mentorship repo adding a file at `projects-showcase/week-4-projects/<your-handle>/README.md` containing:

- A one-line description of the project.
- A link to your GitHub repo.
- A paste of your `git log --oneline` output.
- A paste of your `git remote -v` output.
- A "What I learned this week" section (specific — name a stuck moment).

See [`../../../CONTRIBUTING.md`](../../../CONTRIBUTING.md) for PR etiquette.

## Grading

See [`rubric.md`](rubric.md). Pass = 70+. Use [`checklist.md`](checklist.md) before submitting.

## Stretch (+50 XP)

| Item | XP |
| ---- | -: |
| Add a second remote (`backup`) on another provider or another GitHub repo | +15 |
| Enable branch protection on `main` in your GitHub repo settings | +10 |
| Include at least one `fix:` commit that corrects a real typo | +10 |
| Write your README in a language other than English (or bilingual) | +15 |

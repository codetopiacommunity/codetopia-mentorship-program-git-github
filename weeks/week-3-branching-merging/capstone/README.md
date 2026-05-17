# Week 3 Capstone — Feature Playground

> **XP:** 200 base + up to 50 stretch

## Brief

Build a **feature playground** repo: a tiny landing page (HTML or Markdown — your call) where you deliberately develop **three features on three branches**, merge two cleanly, and engineer + resolve a merge conflict on the third.

The point is not the landing page. The point is to *own* the branching-merging-conflict-resolving loop.

## Requirements

- A `screenshots/` folder in your project containing at least 2 screenshots showing the work in action (e.g., the merged branch graph, a captured conflict block). See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).
- Brand-new repo created with `git init`.
- A `README.md` at the root describing the project and how to read the branch history.
- A "landing page" file (`index.html`, `index.md`, or similar) on `main` with:
  - A title
  - A short intro paragraph
  - At least 3 stub sections (e.g., `## About`, `## Features`, `## Contact`) ready to be filled in by the feature branches.
- A sensible `.gitignore` (see [`../../../templates/.gitignore-template`](../../../templates/.gitignore-template)).

### The three feature branches

All three must be created with `git switch -c` from `main` at the same starting commit.

1. `feat/about` — fills in the About section. **Merges cleanly into `main`** (fast-forward OR three-way, your choice — document which).
2. `feat/features-list` — fills in the Features section. **Merges cleanly into `main`**.
3. `feat/contact` — fills in the Contact section **AND modifies a line the other branches also touched** (e.g., the intro paragraph, the title, or a shared footer). This branch **must produce a merge conflict** when merged, which you resolve by editing.

### Commits

- ≥ **2 commits per feature branch** (so each branch shows real work).
- ≥ **12 commits total** across the repo (main + all branches).
- All conventional — see [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md).
- At least one `fix:` and one `docs:` commit somewhere.

### Required file — `MERGE-STORY.md`

Committed to `main` after all three merges are done. Must contain:

1. **Graph snapshot** — the output of `git log --oneline --graph --decorate --all`.
2. **Merge 1** — name of the branch, whether it fast-forwarded or was three-way, a sentence on why.
3. **Merge 2** — same.
4. **The conflict** — paste the *unresolved* conflict block (with markers) and the *resolved* version. Explain your decision in 2–4 sentences.
5. **A lesson** — one paragraph: *"The hardest part of merging and how I'd teach it to next week's cohort."*

## Deliverable

Submit your work as follows:

1. **Open a PR** (the submission of record) adding your project under `projects-showcase/week-3-projects/<your-handle>/`, with your `screenshots/` folder included. See [`../../../CONTRIBUTING.md`](../../../CONTRIBUTING.md).

   Include in your PR description:

   - The output of `git log --oneline --graph --decorate --all`.
   - A screenshot of the repo's graph (from your terminal or, if you pushed, from GitHub).
   - A one-paragraph reflection tying this to Week 2's "undo lab": *"When something went wrong this week, which undo tool did I reach for, and why?"*

2. **In the WhatsApp group** (the celebration): once your PR is open, share your best screenshot and the PR link so the cohort can cheer you on.

## Grading

See [`rubric.md`](rubric.md). Pass = 70+. Use [`checklist.md`](checklist.md) before submitting.

## Stretch (+50 XP)

- **+15** — Use `git merge --no-ff` on one of the clean merges and explain in `MERGE-STORY.md` why a team might prefer this.
- **+15** — Engineer a *second* conflict on a fourth branch `feat/footer`, then use `git merge --abort` to back out, then retry successfully. Document the abort in `MERGE-STORY.md`.
- **+20** — Push to your own GitHub. Open and merge the three feature branches as Pull Requests via the GitHub UI. Link to the merged PRs from your capstone PR.

## Cross-references

- [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md)
- [`../../../templates/.gitignore-template`](../../../templates/.gitignore-template)
- [`../../../troubleshooting/merge-conflicts.md`](../../../troubleshooting/merge-conflicts.md)
- [`../common-issues.md`](../common-issues.md)

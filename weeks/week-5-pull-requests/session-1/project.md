# Project — Week 5 Session 1

> **XP:** 50

## What you'll do

Fork this mentorship repo, clone your fork, add your handle to a contributors file, and open a pull request with a properly filled-out description.

## Steps

1. On github.com, navigate to this mentorship repo and click **Fork** (top right). Wait for the copy to finish.

2. Clone your fork locally (replace `<your-handle>`):

   ```bash
   git clone git@github.com:<your-handle>/git-github-mentorship.git
   cd git-github-mentorship
   ```

3. Add `upstream` pointing at the original:

   ```bash
   git remote add upstream git@github.com:<program-org>/git-github-mentorship.git
   git remote -v
   ```

4. Sync with upstream before you start:

   ```bash
   git switch main
   git fetch upstream
   git merge upstream/main
   git push origin main
   ```

5. Create a feature branch named after your change:

   ```bash
   git switch -c docs/add-<your-handle>-to-contributors
   ```

6. Add yourself to `discussions/good-resources.md` under a "Mentees" section (create the section if it doesn't exist). One line: your handle and one favorite Git/GitHub resource link with a one-sentence note.

7. Commit and push:

   ```bash
   git add discussions/good-resources.md
   git commit -m "docs: add <your-handle> to mentees list"
   git push -u origin docs/add-<your-handle>-to-contributors
   ```

8. Open a PR from your fork's branch into `upstream/main`. Fill out the template at [`../../../templates/pr-template.md`](../../../templates/pr-template.md):

   - Title: `docs: add <your-handle> to mentees list`
   - Summary: one sentence
   - What changed: the one line you added
   - How to test: "open `discussions/good-resources.md`, scroll to Mentees, see my entry"
   - Checklist: tick the ones that apply

9. Request your mentor as a reviewer.

## Deliverable

Submit your work as follows:

1. **In your project's `screenshots/` folder** (the submission of record): add at least one screenshot — typically the open PR page on GitHub and `git remote -v` showing both `origin` and `upstream`. Name them `01-pr-page.png`, `02-git-remote.png`, etc. (If your project is the fork itself, drop the folder under `projects-showcase/week-5-projects/<your-handle>/screenshots/` in the same PR.)
2. **In the WhatsApp group** (informal share): drop a copy of your best screenshot so the cohort can cheer you on.
3. **In the Discussions tab** (additional channel): post the PR URL, the `git remote -v` output, and a one-sentence answer to: *"Why did I need a fork for this instead of just a branch?"*

See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

## Stretch goal (+10 XP)

Open the PR as a **Draft** first, leave a comment on your own PR saying "Ready for a first look — does the section placement make sense?", then convert to Ready when your mentor responds. Screenshot both states in your discussion post.

## Stuck?

- Lecture notes §3 (fork/clone/upstream sequence).
- Contributing guide: [`../../../CONTRIBUTING.md`](../../../CONTRIBUTING.md)
- Common issues: [`../common-issues.md`](../common-issues.md)
- Post in **Discussions → Q&A** with the screenshot of the GitHub screen you're stuck on.

# Session 2 Project — "The Dry Run"

> **XP:** 75

## Brief

Before the capstone, we do a dry run. Using a sandbox repo (either our cohort's practice repo, or a project of your choice where you're willing to open a throwaway PR), you'll run the complete fork-and-PR workflow.

The goal is to feel the full loop once — *before* the capstone where the PR is real.

## Target

Pick one of:

- **Option A (recommended):** Our cohort's sandbox repo at `templates/oss-practice-repo/` (mentor will point you to the URL).
- **Option B:** `firstcontributions/first-contributions` — explicitly built for this.
- **Option C:** A project from your session 1 shortlist, with a *trivial* change (a typo, a missing period). Keep the scope tiny.

## Steps

### 1. Fork and clone

```bash
gh repo fork <owner>/<repo> --clone
cd <repo>
git remote add upstream git@github.com:<owner>/<repo>.git
git remote -v
```

### 2. Sync

```bash
git fetch upstream
git switch main
git merge upstream/main
```

### 3. Branch

```bash
git switch -c <type>/<handle>-<short-desc>
```

### 4. Make a change

- Small and obvious — a typo, a broken link, a missing word.
- Single-file, single-commit.

### 5. Commit conventionally

```bash
git add <files>
git commit -m "docs: fix typo in <file>"
```

### 6. Push and open the PR

```bash
git push -u origin <branch>
gh pr create --web
```

Fill out the PR description using the four-question structure from the lecture:

- **What**
- **Why**
- **How**
- **Testing**

### 7. Simulate a review round

In your PR, reply to one of the (possibly auto-generated) review comments, or leave a self-comment that says "things to address in a second pass:" and imagine the review.

Then push a follow-up commit (even a no-op formatting tweak) to practice the "respond, push, reply" loop.

## Deliverable

A short `dry-run.md` in `projects-showcase/week-7-projects/<your-handle>/session-2/` containing:

- The PR URL.
- The full PR description you wrote (as a code block).
- A reflection section:
  - What surprised you about the workflow?
  - What part felt awkward or unclear?
  - One thing you'd do differently on the real capstone.

## Stretch (+25 XP)

- Use `gh pr checks` to verify CI passed. Screenshot the output.
- Practice the sync-while-PR-open scenario: after your PR is open, rebase it on fresh upstream and force-push with `--force-with-lease`. Note what changed.
- Invite a cohort peer to leave a review comment on your PR, then respond to it.

## Checks before submitting

- [ ] PR actually opened (link works).
- [ ] PR description has all four sections.
- [ ] Commit message is Conventional Commits.
- [ ] Branch naming followed a convention.
- [ ] Reflection is honest, not boilerplate.

# Lecture Notes — Forks and Pull Requests

## 1. Branch vs fork — the real distinction

A **branch** is a pointer inside one repository.
A **fork** is a *copy of an entire repository* on your own GitHub account.

| | Branch | Fork |
| --- | --- | --- |
| Lives inside | one repo | your GitHub account |
| Who can push to it | anyone with write access to that repo | only you (until you add collaborators) |
| Use case | team members on a shared project | contributing to a project you don't own |

If you're on a team with write access, branches are enough. If you want to contribute to someone else's repo and you're not a collaborator, you **fork**.

> Mentor framing: "A fork is a branch you had to copy the whole repo to make, because you didn't have permission to push a branch there."

## 2. A pull request, defined

A pull request (PR) is a **request** to pull commits from one branch into another — usually from a feature branch (or fork) into `main`. It's wrapped in a web UI that adds:

- A title and description.
- A diff view.
- Line-by-line comments.
- Approvals, change requests, and required checks.
- A merge button.

PRs are a GitHub/GitLab/Bitbucket feature, not a Git feature. `git` itself has no concept of "pull request" — only branches and refs.

## 3. The fork-and-PR workflow, step by step

### Step 1 — Fork on github.com

Visit the repo you want to contribute to. Click **Fork** (top right). GitHub copies it to `github.com/<your-handle>/<repo>`.

### Step 2 — Clone *your fork*

```bash
git clone git@github.com:<your-handle>/<repo>.git
cd <repo>
git remote -v
# origin  git@github.com:<your-handle>/<repo>.git (fetch)
# origin  git@github.com:<your-handle>/<repo>.git (push)
```

`origin` points at your fork, not the original. That's correct.

### Step 3 — Add `upstream`

You want a way to sync changes from the original repo when its `main` moves. Add a second remote:

```bash
git remote add upstream git@github.com:<original-owner>/<repo>.git
git remote -v
# origin    git@github.com:<you>/<repo>.git          (fetch)
# origin    git@github.com:<you>/<repo>.git          (push)
# upstream  git@github.com:<original>/<repo>.git     (fetch)
# upstream  git@github.com:<original>/<repo>.git     (push)
```

Convention: `origin` = yours, `upstream` = the source of truth. You push to `origin`, you fetch from `upstream`.

### Step 4 — Sync your fork's `main`

Before you start work, bring your fork's `main` up to date with upstream:

```bash
git switch main
git fetch upstream
git merge upstream/main
git push origin main
```

### Step 5 — Branch for the work

```bash
git switch -c feat/add-about-section
```

One branch = one logical change. Don't mix a bug fix and a new feature in the same branch.

### Step 6 — Commit and push

```bash
# make edits
git add .
git commit -m "feat: add about section to homepage"
git push -u origin feat/add-about-section
```

Git's output includes a URL — click it to jump straight to the PR-creation page.

### Step 7 — Open the PR on GitHub

- **Base** branch (where it's going): usually `main` on the **upstream** repo.
- **Compare** branch (what's coming in): your feature branch on **your fork**.

GitHub labels this "cross-repository pull request." Double-check both dropdowns.

## 4. Anatomy of a good PR description

Fill out the template — don't leave it blank.

```markdown
## Summary
Adds an "About" section to the homepage, linking to the team bios page.

## Why
Issue #42 — users landing on home have no way to learn about the team.

## What changed
- New `<section id="about">` in `index.html`
- Link to `/team` added in the nav

## How to test
1. Pull the branch
2. Open `index.html` in a browser
3. Scroll — "About" should render between Hero and Footer
4. Click "Meet the team" → navigates to `/team`

## Screenshots
(before) → (after)

## Checklist
- [x] Tested in Chrome + Firefox
- [x] No console errors
- [ ] Requires docs update — will follow up in separate PR

Closes #42
```

Why this works:

- **Summary** tells the reviewer what you did in one sentence.
- **Why** answers "is this the right change at all?"
- **What changed** is a diff in English — reviewers scan this before the code.
- **How to test** makes the reviewer's life easy. Easy reviews come back faster.
- **Screenshots** for anything visual. Always.
- **Closes #42** — GitHub auto-closes the issue when the PR merges.

See [`../../../templates/pr-template.md`](../../../templates/pr-template.md) for our house template.

## 5. Requesting a review

On the PR page, right sidebar → **Reviewers** → click the gear → type a handle.

- Pick **one primary reviewer** who knows the area.
- Optionally add a second pair of eyes.
- Don't request the entire team; you'll get diffused responsibility and no review.

A good comment when requesting:

> Hey @mentor — this is ready for first pass. Focus on the nav markup; the CSS is cosmetic and can slide.

## 6. Draft PRs

If your work is in-progress but you want early feedback, open a **Draft PR** (dropdown on the "Create pull request" button). Draft PRs:

- Can't be merged.
- Don't notify reviewers as "ready."
- Are a great way to ask "is this the right direction before I go further?"

Convert to "Ready for review" when you're done.

## 7. Live demo script (mentor)

Use a throwaway scratch repo you've pre-created (e.g., `mentorship-scratch`). Pre-fork it to your demo account.

```bash
# As the contributor
git clone git@github.com:demo-student/mentorship-scratch.git
cd mentorship-scratch
git remote add upstream git@github.com:mentor-org/mentorship-scratch.git
git remote -v

git switch -c docs/add-student-name
echo "- Demo Student" >> contributors.md
git add contributors.md
git commit -m "docs: add Demo Student to contributors"
git push -u origin docs/add-student-name
# click the link in Git's output
```

On GitHub:

- Open the PR page, narrate the base / compare dropdowns.
- Fill out the template in front of them. Show how the empty template *guides* you.
- Request a review from a co-mentor.
- Mark as Draft, then ready. Show the difference.

## 8. Gotchas worth calling out

- **"Compare & pull request" button missing**: you pushed straight to `main` instead of a branch. Start over on a branch.
- **PR against the wrong base**: easy to do with forks — GitHub sometimes auto-selects `upstream/main` as base, sometimes your own fork's `main`. Read both dropdowns.
- **Accidentally cloned the upstream**: `git remote -v` shows only the original, not your fork. Re-clone from your fork's URL.
- **One PR, ten unrelated changes**: reviewers hate this. Split into smaller PRs.

## 9. Recap

- Branch = pointer in a repo. Fork = copy of a repo.
- Fork → clone your fork → add `upstream` → branch → commit → push → PR.
- A good PR description has a summary, a "why", a "what changed", and test instructions.
- Request one specific reviewer, not a crowd.
- Drafts are fine and encouraged for early feedback.

## Cross-references

- PR template: [`../../../templates/pr-template.md`](../../../templates/pr-template.md)
- Contributing guide: [`../../../CONTRIBUTING.md`](../../../CONTRIBUTING.md)
- Commit message guide: [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md)
- Cheatsheet: [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)

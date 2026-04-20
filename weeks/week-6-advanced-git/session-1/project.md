# Session 1 Project — "Clean up my mess"

> **XP:** 50

## Brief

Create a toy repo with a deliberately messy history, then clean it up using `git rebase -i`. The point is not the content — it's the rewriting.

## Steps

1. Create a new folder and initialize a Git repo.

   ```bash
   mkdir rebase-practice && cd rebase-practice
   git init
   ```

2. Make exactly **7 commits**, at least 4 of which should be obviously bad:

   - A `wip` commit.
   - A "fix typo" commit.
   - A commit with an all-lowercase, non-conventional message like `stuff`.
   - A commit that adds a file, followed by another commit that deletes that same file (pure noise).
   - A couple of genuine commits mixed in (e.g., `feat: add greeting function`).

3. View the mess:

   ```bash
   git log --oneline
   ```

4. Use `git rebase -i` to clean it into **3 or fewer** well-named conventional commits.

   You must use at least two of: `reword`, `squash`/`fixup`, `drop`.

5. Run `git log --oneline` and paste the before/after into your project's README.

## Deliverable

A `rebase-practice/` folder (pushed to your GitHub or zipped) containing:

- The cleaned-up repo.
- A `README.md` with:
  - A "Before" section showing the original messy log.
  - An "After" section showing the cleaned log.
  - A short paragraph describing what you did for each commit you reshaped.

## Stretch (+25 XP)

- Push the repo to GitHub *before* the rebase, then use `git push --force-with-lease` after. Note in your README what the first push vs the force-with-lease push looked like.
- Do one `commit --amend --no-edit` to add a forgotten file, and note it in the README.
- Include a screenshot of your terminal during the rebase (the editor with the todo list).

## Checks before submitting

- [ ] No more `wip`, `stuff`, or typo-style messages remain.
- [ ] Every final commit is Conventional Commits format.
- [ ] `git log --oneline` fits on one screen.
- [ ] README explains your reasoning, not just what commands you ran.

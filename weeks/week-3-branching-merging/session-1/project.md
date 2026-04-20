# Project — Week 3 · Session 1

> **XP:** 75

## What you'll do

Build a tiny "quotes page" (HTML or Markdown) and run three parallel drafts on three branches. You won't merge yet — that's Session 2.

## Steps

1. Create a new repo:

   ```bash
   mkdir quotes-page && cd quotes-page
   git init
   ```

2. On `main`, create `index.md` with a title, a short intro paragraph, and a `## Quotes` heading. Commit.

3. Create three branches, each with a different draft:

   ```bash
   git switch -c draft/minimal
   # add 3 minimalist quotes, one blank line between each
   git add index.md && git commit -m "feat: add minimalist quotes draft"

   git switch main
   git switch -c draft/themed
   # add 5 quotes grouped by theme (Work, Rest, Play)
   git add index.md && git commit -m "feat: add themed quotes draft"

   git switch main
   git switch -c draft/long
   # add 7 quotes with author + year for each
   git add index.md && git commit -m "feat: add long quotes draft"
   ```

4. On each branch, add a *second* commit that tweaks something (e.g., fix a typo, reorder a quote). So each branch has **two** commits beyond `main`.

5. Practice the vocabulary:

   - `git branch` — list your branches.
   - `git switch -` — bounce between two branches.
   - `git log --oneline --graph --decorate --all` — screenshot or paste the output.
   - Rename one branch: `git branch -m draft/long draft/detailed`.
   - Delete (use `-D` since they're unmerged) one branch you no longer want, then *recover it* with `git reflog` + `git branch <name> <sha>`.

## Deliverable

A file called `branching-notes.md` committed to the repo with:

- **Output** of `git log --oneline --graph --decorate --all` (final state).
- **One paragraph** (4–6 sentences) in your own words explaining *"What is a branch, really?"*.
- **One paragraph** on detached HEAD: when it happens and why it's not scary.
- The commands you used to recover the deleted branch (from step 5).

Commit it:

```bash
git add branching-notes.md
git commit -m "docs: add branching notes"
```

Post your `git log --oneline --graph --decorate --all` output in **Discussions → Week 3**.

## Stretch goal (+25 XP)

Complete [Learn Git Branching](https://learngitbranching.js.org/) levels 1–3 (Introduction Sequence + Ramping Up) and paste screenshots of each level-complete screen in your discussion post.

## Stuck?

- [`../common-issues.md`](../common-issues.md)
- [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- Post in **Discussions → Q&A** with `git status` and `git branch` output.

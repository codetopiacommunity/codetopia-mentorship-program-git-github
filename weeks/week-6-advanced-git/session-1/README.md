# Session 1 — Rewriting History

> **XP:** 100 (attendance + exercises)

## Overview

Up to now, commits have been immutable little stones you stack on a pile. This session we learn to pick them up, polish them, combine them, and occasionally throw one away.

The tool is `git rebase -i` ("interactive rebase"), plus its little cousin `git commit --amend`.

## Objectives

- Understand what rewriting history actually means (commits are remade with new SHAs).
- Use `git commit --amend` to fix the *most recent* commit.
- Use `git rebase -i <base>` to `pick`, `reword`, `squash`, `fixup`, `drop`, and reorder commits.
- Articulate the Golden Rule of Rebasing and when `--force-with-lease` is acceptable.

## Mastery checks

By the end of the session you can:

- [ ] Fix a typo in your most recent commit message without creating a new commit.
- [ ] Take 5 messy commits and squash them into 2 meaningful ones.
- [ ] Reword the second-to-last commit.
- [ ] Explain in one sentence why force-pushing a rebased `main` is a problem.
- [ ] Recover from a rebase you wish you hadn't done, using `git reflog`.

## Materials

- [`lecture-notes.md`](./lecture-notes.md)
- [`resources.md`](./resources.md)
- [`project.md`](./project.md) — practice project for this session
- [`solutions/README.md`](./solutions/README.md) — mentor-only

## Prep

- Bring a sandbox repo you don't care about. We will intentionally break it.
- Make sure your editor is configured: `git config --global core.editor "code --wait"` (or `nano`, `vim`, whatever you're comfortable with).

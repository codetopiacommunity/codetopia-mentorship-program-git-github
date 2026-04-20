# Session 2 — Recovery & Power Tools

> **XP:** 100 (attendance + exercises)

## Overview

Session 1 taught you how to rewrite history. This session teaches you how to survive the consequences — and a few power tools you'll reach for every week for the rest of your career.

Four tools, each a lifesaver in its own domain:

- `git reflog` — every reference change Git has ever made, locally.
- `git cherry-pick` — port one commit from anywhere to anywhere.
- `git stash` — put work aside without committing.
- `git bisect` — binary-search your history for the commit that broke it.

## Objectives

- Use `git reflog` to recover a "lost" commit after a bad rebase or hard reset.
- Cherry-pick a single commit from another branch onto the current branch.
- Stash, list, apply, pop, and drop work-in-progress changes.
- Run a full `git bisect` session (manual or scripted) to find a regression.

## Mastery checks

By the end of the session you can:

- [ ] Recover a branch you accidentally deleted using `reflog` + `git branch <name> <sha>`.
- [ ] Cherry-pick a commit and handle a conflict while doing so.
- [ ] Stash work, switch branches, return, and `stash pop` successfully.
- [ ] Explain what "bisect" is searching through, and why it's O(log n).

## Materials

- [`lecture-notes.md`](./lecture-notes.md)
- [`resources.md`](./resources.md)
- [`project.md`](./project.md)
- [`solutions/README.md`](./solutions/README.md) — mentor-only

## Prep

- A repo from last session (with the rebased history) is ideal.
- Or clone any repo you don't mind experimenting on.

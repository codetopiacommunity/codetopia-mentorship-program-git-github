# Week 4 · Session 2 · Cloning, Pulling, Fetching

> **XP:** 75
> **Time:** 60–90 min
> **Prereqs:** Session 1. You have a working remote on `origin` and can push.

## Learning Objectives

By the end of this session you will:

1. Clone a repository you don't own.
2. Explain the difference between `git fetch` and `git pull`.
3. Read a tracking branch status line (`[ahead 2, behind 1]`) correctly.
4. Handle the case when local and remote histories have diverged.
5. Fix the two most common beginner errors: non-fast-forward pushes and `refusing to merge unrelated histories`.

## Reading

- [`lecture-notes.md`](lecture-notes.md)
- [`resources.md`](resources.md)

## Project

See [`project.md`](project.md). You'll clone a repo, simulate a divergence, and resolve it.

## Mastery Checks

- [ ] You can answer: *"What's the difference between `git fetch` and `git pull`?"*
- [ ] `git clone <url>` produces a working repo with `origin` already configured.
- [ ] You can read `git status` and see whether your branch is ahead, behind, or diverged.
- [ ] You can resolve a "non-fast-forward" rejected push without force-pushing.
- [ ] You know what `origin/main` is (a *remote-tracking branch*) and how it's different from `main`.

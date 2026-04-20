# Week 3 · Session 1 · Branches — Movable Pointers

> **XP:** 100
> **Time:** 75–100 min
> **Prereqs:** Weeks 1 & 2. You can commit confidently and read `git log --oneline --graph`.

## 🎯 Learning Objectives

By the end of this session you will:

1. Explain — in your own words, on a whiteboard — what a branch *actually is*.
2. Create a branch with `git switch -c <name>` and `git branch <name>`.
3. List local branches (`git branch`) and all branches (`git branch -a`).
4. Rename (`git branch -m`) and delete (`git branch -d`, `git branch -D`) branches.
5. Switch between branches with `git switch <name>` and `git switch -`.
6. Read `git log --oneline --graph --all --decorate` and point at each branch pointer.

## 📖 Reading

- [`lecture-notes.md`](lecture-notes.md)
- [`resources.md`](resources.md)

## 🛠 Project

See [`project.md`](project.md). You'll build a tiny site and run three parallel "drafts" on branches.

## ✅ Mastery Checks

- [ ] You can state: *"A branch is a lightweight, movable pointer to a commit."*
- [ ] You can explain what `HEAD` is and what "detached HEAD" means.
- [ ] You can draw a 2-branch graph on paper and say which commit each branch points to.
- [ ] You can list, create, switch to, rename, and delete a branch without checking notes.
- [ ] You know the difference between `git branch -d` (safe) and `git branch -D` (force).

## Next

Session 2: what happens when we *combine* branches — fast-forward and three-way merges, and the conflicts that come with them.

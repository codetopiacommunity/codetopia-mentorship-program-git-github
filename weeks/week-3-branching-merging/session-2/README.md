# Week 3 · Session 2 · Merging & Conflict Resolution

> **XP:** 100
> **Time:** 75–100 min
> **Prereqs:** Week 3 Session 1. You can create, switch, and delete branches.

## 🎯 Learning Objectives

By the end of this session you will:

1. Predict whether a merge will be **fast-forward** or **three-way** by looking at the graph.
2. Perform a fast-forward merge and understand why no merge commit appears.
3. Perform a three-way merge and read its merge commit.
4. Force a merge commit with `--no-ff` and explain why teams sometimes prefer it.
5. Deliberately create a merge conflict.
6. Read `<<<<<<<` / `=======` / `>>>>>>>` conflict markers and resolve them by editing.
7. Abort a broken merge with `git merge --abort` and restart clean.

## 📖 Reading

- [`lecture-notes.md`](lecture-notes.md)
- [`resources.md`](resources.md)

## 🛠 Project

See [`project.md`](project.md). You'll deliberately engineer one fast-forward merge, one three-way merge, and one conflict — then resolve it.

## ✅ Mastery Checks

- [ ] Looking at `git log --graph --all`, you can predict the merge type before running it.
- [ ] You can read a conflict and name which side is "ours" and which is "theirs".
- [ ] You can resolve a conflict and produce a clean `git status`.
- [ ] You can abort mid-merge without leaving garbage behind.
- [ ] You know the shape of a merge commit — two parents, one message.

## Safety creed

> Conflicts are not errors. They're Git *asking you* for help. The computer cannot know which side is right. You decide, you stage, you commit. That's the whole workflow.

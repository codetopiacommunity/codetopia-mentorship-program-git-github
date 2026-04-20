# Week 2 · Session 2 · `.gitignore` & Undoing Changes Safely

> **XP:** 75
> **Time:** 75–100 min
> **Prereqs:** Week 2 Session 1 complete. You can read diffs and logs.

## 🎯 Learning Objectives

By the end of this session you will:

1. Write a `.gitignore` that covers OS junk, editor junk, dependencies, and secrets.
2. Untrack a file you already committed without deleting it from disk.
3. Undo a working-tree change with `git restore <file>`.
4. Unstage a file with `git restore --staged <file>`.
5. Fix the most recent commit (message or content) with `git commit --amend`.
6. Explain — *out loud* — the difference between `git reset --soft`, `--mixed`, and `--hard`.
7. Recover a commit you thought was lost using `git reflog`.

## 📖 Reading

- [`lecture-notes.md`](lecture-notes.md)
- [`resources.md`](resources.md)

## 🛠 Project

See [`project.md`](project.md). You'll deliberately make and *undo* four different kinds of mistakes.

## ✅ Mastery Checks

- [ ] You can write a `.gitignore` for a Node project from memory.
- [ ] You can unstage a file without losing edits.
- [ ] You can amend the last commit's message.
- [ ] You can name which state each `reset` mode leaves your working directory in.
- [ ] You can read `git reflog` output and identify a commit by shorthand (`HEAD@{3}`).

## Safety creed

> **Before any destructive command** (`reset --hard`, `clean -fd`, force-push), stop. Run `git status`. Read it. Then run the command. Git has an undo — it's called `reflog` — but it's easier to just not need it.

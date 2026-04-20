# Week 2 · Session 1 · Working with Files — Diffing & Reading History

> **XP:** 75
> **Time:** 60–90 min
> **Prereqs:** Week 1 complete. You can `git init`, `git add`, and `git commit` without looking.

## 🎯 Learning Objectives

By the end of this session you will:

1. Read a unified diff and name every part (`---`, `+++`, hunk header, `+`/`-` lines).
2. Use `git diff`, `git diff --staged`, and `git diff HEAD` and explain *which comparison each makes*.
3. Use `git log` with the five most useful flags: `--oneline`, `--graph`, `--stat`, `-p`, `--author`.
4. Use `git show <sha>` to inspect a single commit.
5. Find *who last changed a line* with `git blame`.

## 📖 Reading

- [`lecture-notes.md`](lecture-notes.md)
- [`resources.md`](resources.md)

## 🛠 Project

See [`project.md`](project.md). You'll build a small "study notes" repo and run a scripted tour of its history.

## ✅ Mastery Checks

- [ ] You can explain the difference between `git diff` and `git diff --staged` in one sentence.
- [ ] You can read a diff aloud: "this line was removed, these two were added".
- [ ] `git log --oneline --graph --decorate --all` runs without scaring you.
- [ ] You can paste the output of `git show HEAD` and point at the message, author, date, and diff.
- [ ] You know how to `q` out of the pager.

## Next

Session 2 is where we learn to *undo* things safely.

# Week 4 · Session 1 · GitHub Remotes

> **XP:** 75
> **Time:** 60–90 min
> **Prereqs:** You can init, stage, commit, and branch locally (Weeks 1–3). You have a GitHub account.

## Learning Objectives

By the end of this session you will:

1. Explain what a "remote" is in Git terms.
2. Create a new empty repository on github.com.
3. Connect a local repo to it with `git remote add origin <url>`.
4. Push your first commit with `git push -u origin main`.
5. Choose between SSH and HTTPS authentication, and get one of them working end-to-end.
6. Generate an SSH key and register it with GitHub.

## Reading

- [`lecture-notes.md`](lecture-notes.md)
- [`resources.md`](resources.md)

## Project

See [`project.md`](project.md). You'll connect an existing local repo to a fresh GitHub repo and push it.

## Mastery Checks

- [ ] You can answer: *"What is the difference between `git remote add` and `git push`?"*
- [ ] `git remote -v` shows `origin` with a fetch and push URL.
- [ ] `git push -u origin main` succeeds and GitHub shows your commits.
- [ ] `ssh -T git@github.com` returns a friendly greeting **or** HTTPS + PAT works without prompting on every push.
- [ ] You can explain what the `-u` flag in `push -u origin main` actually does.

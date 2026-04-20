# Session 1 — GitHub Actions Basics

> **XP:** 75 (attendance + exercises)

## Overview

Continuous Integration used to mean a Jenkins server, a grumpy sysadmin, and an afternoon of configuration. Now it's a YAML file in a folder. This session we write one.

By the end, any push or PR to your repo will automatically run lint and tests, and block merges if they fail.

## Objectives

- Understand the GitHub Actions model: workflows -> jobs -> steps.
- Write a `hello-world` workflow that runs on push.
- Add a realistic lint + test workflow for a small project.
- Configure branch protection so CI must pass before merge.
- Read a failing workflow log and diagnose the cause.

## Mastery checks

- [ ] I can explain the file path `.github/workflows/ci.yml` and why it matters.
- [ ] I can add a matrix to run the same job across Node 18/20/22 (or Python 3.10/3.11/3.12).
- [ ] I can create a status check that is *required* on the `main` branch.
- [ ] Given a red CI run, I can find the exact failing line in the logs.

## Materials

- [`lecture-notes.md`](./lecture-notes.md)
- [`resources.md`](./resources.md)
- [`project.md`](./project.md)
- [`solutions/README.md`](./solutions/README.md) — mentor-only

## Prep

- A small repo with *some* tests (even one) — Node, Python, Go, whatever you know.
- A GitHub account with a repo pushed up.

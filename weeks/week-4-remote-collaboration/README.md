# Week 4 · Remote Collaboration

> **Total XP:** 400 — split as 75 (S1) + 75 (S2) + 200 (capstone) + 50 (stretch).
> **Outcome:** Mentees can create a GitHub repository, connect a local repo to it, authenticate over SSH or HTTPS, and keep local and remote history in sync with `push`, `pull`, and `fetch`.

## Sessions

| # | Title | Folder |
| - | ----- | ------ |
| 1 | GitHub Remotes — Connecting Local to Cloud | [`session-1/`](session-1/) |
| 2 | Cloning, Pulling, Fetching | [`session-2/`](session-2/) |

## Capstone

Push a brand-new README-only project to **your own** GitHub account with at least 5 commits delivered in two separate pushes.
See [`capstone/`](capstone/).

## Big Picture

A Git repo on your laptop is useful. A Git repo on GitHub is *shared*. This week teaches the 3 things that turn a local repo into a collaborative one:

1. **A remote** — a named URL pointing at a copy of the repo (usually called `origin`).
2. **Authentication** — how GitHub knows it's really you (SSH key or HTTPS + PAT).
3. **Sync commands** — `push`, `fetch`, and `pull`, plus the tracking branches that glue them together.

By end of week, mentees should comfortably say: *"my local `main` tracks `origin/main`, and I sync it with `git pull`."*

## Common Issues

See [`common-issues.md`](common-issues.md).

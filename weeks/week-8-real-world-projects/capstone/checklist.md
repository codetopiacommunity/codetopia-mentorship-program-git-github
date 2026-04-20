# Week 8 Capstone — Pre-Submission Checklist

> This is the last checklist of the program. Take your time with it.

## Repository

- [ ] Public on GitHub.
- [ ] Name is descriptive, kebab-case, no placeholders.
- [ ] `.gitignore` matches the tech stack (no `node_modules/`, no `__pycache__/`, no `.env`).
- [ ] `LICENSE` file present.
- [ ] No leftover `TODO.md`, scratch files, or debug output committed.

## Git history

- [ ] `git log --oneline` reads as a story.
- [ ] All commits follow Conventional Commits.
- [ ] No `wip`, `stuff`, `asdf`, typo-messages.
- [ ] If you used interactive rebase to clean up, great.

## CI

- [ ] `.github/workflows/ci.yml` exists at the correct path.
- [ ] Triggers on `push` to `main` and `pull_request` to `main`.
- [ ] At minimum: checkout + setup + install + lint + test.
- [ ] Currently green on `main`.
- [ ] Branch protection enabled on `main`:
  - [ ] Require a PR before merging.
  - [ ] Require status check `ci` (or your job's name).
  - [ ] Include administrators.
- [ ] Screenshot of the settings page saved.

## README

- [ ] Title and **one-sentence pitch** at the top.
- [ ] At least **3 badges**, all rendering correctly.
- [ ] A **visual** — screenshot, GIF, or demo — showing your actual project.
- [ ] **Quickstart** section with a copy-pasteable code block.
- [ ] **Usage** section with at least 2 realistic examples.
- [ ] **Why I built this** or equivalent humanizing section.
- [ ] **Contributing** sentence (even if "not accepting PRs yet").
- [ ] **License** stated and matches the `LICENSE` file.
- [ ] No broken images, badges, or links.
- [ ] No placeholder text (`Lorem ipsum`, `TODO`, `<project name>`).

## Release

- [ ] Annotated tag: `git tag -a v1.0.0 -m "..."`.
- [ ] Tag pushed: `git push origin v1.0.0`.
- [ ] `git show v1.0.0` shows the annotation.
- [ ] GitHub Release published (not just the tag).
- [ ] Release notes have three sections: **What's new**, **Fixes**, **Breaking changes**.
- [ ] Release notes are human-written, not raw auto-generated.

## Writeup — `GRADUATION.md`

- [ ] **Pitch** — 30-second elevator pitch.
- [ ] **Journey** — 2-3 paragraphs, honest, specific.
- [ ] **What's next** — concrete v1.1 + v2.0 ideas.
- [ ] **Thanks** — one line.

## Cohort submission

- [ ] Folder at `projects-showcase/week-8-projects/<your-handle>/`.
- [ ] Submission README with repo link, release link, live deploy link (if any), pitch.
- [ ] All required screenshots (branch protection, CI green, release page).
- [ ] PR title: `feat(week-8): <handle> graduation project`.
- [ ] PR description follows [`../../../templates/pr-template.md`](../../../templates/pr-template.md).

## Stretch (if attempted)

- [ ] Live deploy URL present and loads.
- [ ] Coverage badge shows a real number.
- [ ] Issue templates in `.github/ISSUE_TEMPLATE/`.
- [ ] PR template in `.github/`.
- [ ] Project-level `CONTRIBUTING.md`.
- [ ] 30-second peer test documented.

## The final sanity check

- [ ] A stranger opening my repo for 30 seconds would understand what it does.
- [ ] A recruiter could screenshot this repo into a job-match slack channel and nobody would laugh.
- [ ] I am proud to put this on my résumé.

If every box is checked, you're ready.

Ship it.

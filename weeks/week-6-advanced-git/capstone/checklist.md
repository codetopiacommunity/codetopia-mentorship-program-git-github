# Week 6 Capstone — Pre-Submission Checklist

Run through this before opening your PR. If any box is unchecked, fix it first.

## History

- [ ] Starting history had **10+ commits** including all required categories.
- [ ] Final history has **3–6 commits**.
- [ ] Every final commit message is **Conventional Commits** format.
- [ ] No `wip`, `stuff`, `asdf`, `...`, or typo-style messages remain.
- [ ] `git log --oneline --graph` fits on one screen.

## Rebase technique

- [ ] I used at least **4 different** rebase verbs.
- [ ] I used `git commit --amend` at least once.
- [ ] I tagged `before-cleanup` or otherwise had a rollback path.
- [ ] `git diff before-cleanup HEAD` shows no file differences (diff preserved).

## Writeup (`WRITEUP.md`)

- [ ] **Before** section with fenced code block of the original log.
- [ ] **After** section with fenced code block of the cleaned log.
- [ ] **Narrative** paragraph per final commit.
- [ ] **Reflection** (3–5 sentences) including the Golden Rule in my own words.

## Repository hygiene

- [ ] Repo is under `projects-showcase/week-6-projects/<your-handle>/`.
- [ ] `.git/` directory is present in the submission (reviewers need the history).
- [ ] `screenshots/` folder present with at least 2 named screenshots (`01-...`, `02-...`)
- [ ] Best screenshot shared in the WhatsApp group
- [ ] No extraneous files (no `node_modules/`, no `.DS_Store`, no personal info).
- [ ] A project `README.md` exists in my submission folder explaining what the repo is.

## PR

- [ ] PR title follows Conventional Commits: `feat(week-6): <handle> capstone submission`.
- [ ] PR description follows [`../../../templates/pr-template.md`](../../../templates/pr-template.md).
- [ ] PR is opened against `main` of the mentorship repo.
- [ ] I checked off this list in the PR description.

## Stretch (if attempted)

- [ ] Screenshot(s) of `--force-with-lease` push saved to `assets/`.
- [ ] `RECOVERY.md` present with reflog output.
- [ ] "When I would NOT do this" section in `WRITEUP.md`.

## Last sanity check

- [ ] I can explain, out loud, what each of my final commits does and why I chose that grouping.
- [ ] I would be comfortable with a senior developer reviewing this log.

If you checked every box, you're ready. Open the PR.

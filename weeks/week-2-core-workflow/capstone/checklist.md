# Week 2 Capstone — Pre-submission Checklist

Run this list before opening your PR. If any box can't be checked, fix it first.

## Repo

- [ ] `git status` returns "nothing to commit, working tree clean"
- [ ] `git log --oneline` shows ≥ 10 commits
- [ ] Every commit message starts with a conventional type (`feat:`, `fix:`, `docs:`, `chore:`, …)
- [ ] No commit message uses past tense ("added", "fixed")
- [ ] No commit message ends with a period

## Files

- [ ] `README.md` present and complete
- [ ] `HISTORY.md` present with all three required sections
- [ ] `recipes/` contains ≥ 3 recipe `.md` files
- [ ] `.gitignore` present at the repo root
- [ ] `screenshots/` folder present with at least 2 named screenshots (`01-...`, `02-...`)
- [ ] Best screenshot shared in the WhatsApp group

## `.gitignore` proof

- [ ] At least one file that *would* be committed without `.gitignore` exists on disk (e.g., `.DS_Store`, `notes.tmp`, `scratch.env`)
- [ ] Running `git status` still shows a clean tree with that file present
- [ ] No `.DS_Store`, `Thumbs.db`, `.env`, or `node_modules/` tracked in the repo

## Amend proof

- [ ] At least one commit was fixed with `git commit --amend`
- [ ] The `HISTORY.md` "Amend I'm proud of" section names the commit and explains the change

## Content

- [ ] Each recipe has a title, ingredients list, and steps
- [ ] README explains how to read the repo
- [ ] Reflection paragraph included in PR description

## Submission

- [ ] You forked the program repo
- [ ] Your folder is under `projects-showcase/week-2-projects/<handle>/`
- [ ] PR title is descriptive (e.g., "Week 2 capstone — @yourhandle — recipe collection")
- [ ] PR description includes `git log --oneline` output and your reflection
- [ ] You tagged your mentor

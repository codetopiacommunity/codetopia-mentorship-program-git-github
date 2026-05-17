# Week 4 Capstone — Pre-submission Checklist

Run this list before opening your PR.

## Local repo

- [ ] `git status` returns "nothing to commit, working tree clean"
- [ ] `git log --oneline` shows at least 5 commits
- [ ] Every commit message starts with a type (`feat:`, `fix:`, `docs:`, ...)
- [ ] No past-tense verbs ("added", "fixed") in commit messages
- [ ] No trailing periods in commit subjects
- [ ] `.gitignore` present — no `.DS_Store`, `node_modules/`, `.env` tracked

## Remote + auth

- [ ] `git remote -v` shows exactly one `origin` with matching fetch/push URLs
- [ ] `ssh -T git@github.com` greets you by name, **or** `git push` doesn't prompt for username/password
- [ ] The GitHub repo exists under your own handle (not a clone, not forked)
- [ ] The GitHub repo's default branch is `main`
- [ ] `git branch -vv` shows `main` tracking `origin/main`

## Delivery

- [ ] Commits were pushed in **two separate batches**, not one (check GitHub's commits view — timestamps should group into two clusters)
- [ ] GitHub's repo homepage shows your README rendered

## Content

- [ ] README has at least 3 real sections (no lorem ipsum)
- [ ] "What I learned this week" section names a specific stuck moment
- [ ] No accidental personal info (real address, phone, secret tokens)

## Submission PR

- [ ] You forked this mentorship repo
- [ ] You added `projects-showcase/week-4-projects/<your-handle>/README.md`
- [ ] `screenshots/` folder present with at least 2 named screenshots (`01-...`, `02-...`)
- [ ] Best screenshot shared in the WhatsApp group
- [ ] That file links to your GitHub repo
- [ ] That file includes `git log --oneline` and `git remote -v` output
- [ ] PR title follows [commit message guide](../../../templates/commit-message-guide.md)
- [ ] You tagged your mentor for review

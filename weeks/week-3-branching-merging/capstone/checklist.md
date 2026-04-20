# Week 3 Capstone — Pre-submission Checklist

Run this list before opening your PR. If any box can't be checked, fix it first.

## Repo hygiene

- [ ] `git status` returns "nothing to commit, working tree clean"
- [ ] `git log --oneline --graph --decorate --all` shows all three feature branches converging on `main`
- [ ] No branch still exists that should have been deleted (`git branch` is tidy)
- [ ] No conflict markers remain anywhere in the repo (run: `grep -rn "<<<<<<<\|=======\|>>>>>>>" .`)

## Commits

- [ ] ≥ 12 commits total
- [ ] ≥ 2 commits per feature branch
- [ ] Every message starts with a conventional type (`feat:`, `fix:`, `docs:`, `chore:`, …)
- [ ] No message uses past tense ("added", "fixed")
- [ ] No message ends with a period
- [ ] At least one `fix:` and one `docs:` commit

## Merges

- [ ] Two clean merges (FF or 3-way, your choice)
- [ ] One merge that *did* conflict, now resolved
- [ ] Every merge commit has a sensible default message (or a better one you wrote)

## Required files

- [ ] `README.md` present, explains the project and how to read the branches
- [ ] Landing page file (`index.html` / `index.md` / etc.) present on `main`
- [ ] `.gitignore` at repo root
- [ ] `MERGE-STORY.md` at repo root with **all five** required sections:
  - [ ] Graph snapshot
  - [ ] Merge 1 summary
  - [ ] Merge 2 summary
  - [ ] Conflict (unresolved + resolved + rationale)
  - [ ] Lesson paragraph

## Submission

- [ ] You forked the program repo
- [ ] Your folder is under `projects-showcase/week-3-projects/<handle>/`
- [ ] PR title is descriptive (e.g., "Week 3 capstone — @yourhandle — feature playground")
- [ ] PR description includes `git log --oneline --graph --decorate --all` output
- [ ] PR description includes your reflection paragraph tying to Week 2
- [ ] Graph screenshot attached
- [ ] You tagged your mentor

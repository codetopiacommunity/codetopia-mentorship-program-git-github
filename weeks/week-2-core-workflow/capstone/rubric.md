# Week 2 Capstone Rubric

Total: 100. Pass: 70+. Stretch adds up to +50 XP.

| Criterion | Points | Great looks like |
| --------- | -----: | ---------------- |
| Repo set up correctly | 5 | `.git/` exists, `main` is default branch, `git status` is clean |
| README clear and inviting | 10 | Title, description of the collection, how the repo is organized |
| ≥ 3 recipe files in `recipes/` | 10 | Real markdown recipes — title, ingredients, steps |
| `.gitignore` correct and effective | 15 | Covers OS + editor + at least one language/tool. A file that *should* be hidden exists on disk and `git status` stays clean. |
| ≥ 10 atomic commits | 15 | One logical change per commit, not a dump of unrelated edits |
| Conventional commit messages | 10 | All start with a valid type, imperative mood, no trailing period |
| At least one `--amend` used and documented | 15 | `HISTORY.md` names the amended commit and why; old+new messages shown |
| `HISTORY.md` complete | 10 | All three required sections, accurate `git log --oneline` dump |
| Content quality | 5 | Real recipes, not placeholder text |
| File organization | 5 | Clear structure, no junk files tracked |
| **Total** | **100** | |

## Stretch (+50)

| Item | XP |
| ---- | -: |
| `reset --soft` squash documented in `HISTORY.md` | +15 |
| `revert` commit used (and amend *not* used for that fix) | +15 |
| Pushed to your own GitHub with a commit-graph screenshot | +20 |

## Pass boundary

**70** is the pass bar. Below 70: request changes on the PR with specific criteria to improve. Above 90: highlight in the weekly roundup.

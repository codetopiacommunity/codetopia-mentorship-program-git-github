# Week 3 Capstone Rubric

Total: 100. Pass: 70+. Stretch adds up to +50 XP.

| Criterion | Points | Great looks like |
| --------- | -----: | ---------------- |
| Repo set up correctly | 5 | `.git/` exists, `main` is default, `git status` clean |
| README + landing page content | 10 | Title, intro, 3 stub sections, real (not lorem) content filled in by the branches |
| `.gitignore` present and correct | 5 | Covers OS junk at minimum; nothing inappropriate tracked |
| 3 feature branches created from same base | 10 | `git log --graph --all` shows three siblings |
| ≥ 2 commits per branch, ≥ 12 commits total | 10 | Real atomic work, not padding |
| Conventional commit messages throughout | 10 | Valid type prefix, imperative mood, no trailing period |
| Merge 1 clean + documented | 10 | Completed, type (FF vs 3-way) correctly named in MERGE-STORY |
| Merge 2 clean + documented | 10 | Same |
| Conflict engineered on `feat/contact` | 10 | Conflict actually occurred (paste shown in MERGE-STORY) |
| Conflict resolved correctly | 15 | No markers remain; resolution is thoughtful, not "pick one blindly" |
| `MERGE-STORY.md` complete | 10 | All five required sections present and accurate |
| Graph screenshot / log included in PR | 5 | Legible, shows all three merges and the conflict merge |
| **Total** | **100** | |

## Stretch (+50)

| Item | XP |
| ---- | -: |
| `--no-ff` used on one merge and rationale documented | +15 |
| Second conflict intentionally aborted with `git merge --abort`, then resolved | +15 |
| Pushed to GitHub; branches merged via PR UI; linked from capstone PR | +20 |

## Pass boundary

**70** passes. Below 70: request changes on the PR naming the specific rows missing points. Above 90: highlight in the weekly roundup and consider as a mentor-lounge example.

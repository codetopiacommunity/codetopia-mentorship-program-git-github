# Week 5 Capstone Rubric

Total: 100. Pass: 70+. Stretch adds up to +50 XP.

## As author (60 points)

| Criterion | Points | Great looks like |
| --------- | -----: | ---------------- |
| Fork + upstream setup | 5 | `git remote -v` on mentee's clone shows both `origin` (fork) and `upstream` |
| Branch name is conventional | 5 | `feat/...`, `docs/...`, etc. — descriptive, kebab-case |
| 3+ atomic commits, conventional messages | 10 | No mega-commits, imperative mood, no trailing periods |
| PR targets correct base | 5 | Base = this repo's `main`, not the fork's `main` |
| PR title follows conventional format | 5 | Reads like a commit subject |
| PR description is complete | 10 | Summary, Why, What changed, How to test — no template comments left |
| Mentor requested as reviewer | 5 | Visible in the Reviewers sidebar |
| Showcase folder structure correct | 10 | `projects-showcase/week-5-projects/<handle>/README.md` exists and renders |
| Responded to review feedback | 5 | Either a new commit or a reasoned reply per thread |

## As reviewer (40 points)

| Criterion | Points | Great looks like |
| --------- | -----: | ---------------- |
| Reviewed at least one peer PR | 10 | Review visible on the Conversation tab of their PR |
| 3+ substantive comments | 10 | Not just "LGTM" — each anchored to a line with a reason |
| At least one suggested-change block | 10 | Triple-backtick `suggestion` that the author can click-accept |
| Explicit verdict (not just comments) | 5 | Comment / Approve / Request changes chosen on purpose |
| Tone follows CoC | 5 | Kind, specific, no blaming language |

## Totals

| Bucket | Points |
| ------ | -----: |
| As author | 60 |
| As reviewer | 40 |
| **Total** | **100** |
| **Pass** | **70** |

## Stretch (+50)

| Item | XP |
| ---- | -: |
| PR merged via squash with a clean conventional squashed message | +15 |
| Reviewed two peer PRs with full quality on both | +15 |
| At least one suggested-change accepted by the other author | +10 |
| No force-push during active review on your own PR | +10 |

## Mentor notes

- **Don't merge instantly.** Leave the PR open for at least one real round of review — the learning is in the round-trip.
- **Check the "Request changes" usage.** If a mentee marks a typo as Request changes, coach them: that's a nit, not a blocker.
- **Confirm suggested-changes worked.** Click into the thread — you should see the "Commit suggestion" action landed as a commit on the PR branch.
- **Showcase folder**: open the `README.md` and confirm it actually renders (no broken image paths, no absolute local file links).

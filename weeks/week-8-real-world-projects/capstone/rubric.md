# Week 8 Capstone Rubric — The Graduation Project

Total: **100 points**. Pass = **70**.

This rubric is stricter than earlier weeks' by design. Graduation should mean something.

| Area | Points | What we look for |
|------|--------|------------------|
| **Repo hygiene** | 10 | Clean name, sensible structure, `.gitignore` appropriate to stack, `LICENSE` present and matches README. |
| **Git history** | 10 | Conventional Commits throughout, no `wip`/`stuff`, logical grouping. `git log --oneline` is a story, not a transcript. |
| **CI workflow exists** | 10 | `.github/workflows/ci.yml` present, triggers on push + PR to main, runs lint + test. |
| **CI is green on `main`** | 10 | Screenshot in writeup; current runs passing. |
| **Branch protection on `main`** | 5 | PRs required, CI required, Include administrators checked. Screenshot required. |
| **README — pitch + visual** | 10 | One-sentence pitch up top. Screenshot/GIF visible. No broken images. |
| **README — badges** | 5 | At least 3, all rendering (no "unknown"). |
| **README — quickstart + usage** | 10 | Copy-pasteable, works for a new user, at least 2 realistic usage examples. |
| **README — about + license** | 5 | Humanized "why I built this"; license stated and matches LICENSE file. |
| **`v1.0.0` annotated tag** | 5 | `git show v1.0.0` shows annotation and message. |
| **Published Release** | 5 | Release page exists on GitHub with the tag selected. |
| **Release notes quality** | 5 | Human-written, What's new / Fixes / Breaking changes structure. Not raw auto-generated. |
| **`GRADUATION.md` — pitch** | 3 | The 30-second recruiter pitch. Specific, not generic. |
| **`GRADUATION.md` — journey** | 4 | 2-3 honest paragraphs, not performative. |
| **`GRADUATION.md` — what's next** | 2 | Concrete v1.1 and v2.0 ideas. |
| **`GRADUATION.md` — thanks** | 1 | A human "thanks". |

Total: **100**.

## Stretch (+50)

| Stretch | Points |
|---------|--------|
| Live deploy with URL in README | 15 |
| Coverage badge from real service | 10 |
| Issue templates (both bug + feature) | 10 |
| PR template | 5 |
| Project-level `CONTRIBUTING.md` | 5 |
| 30-second peer test documented | 5 |

## Scoring tiers

- **95+**: Exceptional. Could go on the cohort's "alumni showcase." Mentor writes a recommendation.
- **85–94**: Strong. Ready to share on LinkedIn. Minor polish only.
- **70–84**: Passing. Graduated. Would benefit from one more polish pass before sharing widely.
- **Below 70**: Sent back for one revision. Graduation delayed by a week. Specific feedback required.

## Automatic fails

- CI red on `main` at time of grading.
- Broken visual in README.
- `v1.0.0` tag missing or not pushed.
- No `GRADUATION.md`.
- Plagiarized project (submitting someone else's repo).

## Notes for graders

- Do the **30-second test** yourself. If you walk away confused, dock the README badly regardless of the rest.
- If you don't know the tech stack well enough to evaluate the code, that's OK — this rubric is mostly about craft and process, not implementation quality.
- Be generous with partial credit on the writeup sections. Graduation should feel like an achievement.
- If the mentee scores 95+, email them a recommendation — this is the kind of student alums would vouch for.

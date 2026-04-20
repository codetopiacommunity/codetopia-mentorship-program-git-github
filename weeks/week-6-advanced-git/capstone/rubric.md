# Week 6 Capstone Rubric

Total: **100 points**. Pass = **70**.

| Area | Points | What we look for |
|------|--------|------------------|
| **Messy starting history** | 10 | At least 10 commits with all required categories (wip, fix-follow-ups, noise, typo, genuine). Evidence in `WRITEUP.md` "Before" section. |
| **Final history is clean** | 15 | 3–6 commits, all Conventional Commits, all meaningful. No `wip`, no typos, no noise commits left. |
| **Verbs used** | 15 | At least 4 different rebase verbs demonstrated (the writeup shows which). |
| **`--amend` used** | 5 | At least one amend, noted in the writeup. |
| **Diff preserved** | 10 | The final working tree matches what it would've been without the cleanup (`git diff before-cleanup HEAD` shows no file differences, only metadata). |
| **Writeup — Before/After** | 10 | Both logs pasted, clearly labeled, in fenced code blocks. |
| **Writeup — Narrative** | 15 | Each final commit has a paragraph explaining which originals merged into it and why. Shows reasoning, not just transcript. |
| **Writeup — Reflection** | 10 | 3–5 sentences. Includes a clear, personal statement of the Golden Rule. |
| **Conventional commit quality** | 5 | Types chosen correctly (`feat`/`fix`/`docs`/etc.), subject line <72 chars, imperative mood. |
| **PR quality** | 5 | Clean PR description, follows [`../../../templates/pr-template.md`](../../../templates/pr-template.md), correct folder path. |

## Stretch (+50)

| Stretch | Points | Notes |
|---------|--------|-------|
| Force-with-lease demo with screenshot | 20 | Must show the push being rejected without it, then succeeding with it. |
| Recovery writeup (`RECOVERY.md`) | 20 | Must show `reflog` output and the `cherry-pick` of the recovered commit. |
| "When I would NOT do this" section | 10 | Must describe a plausible shared-branch scenario. |

## Scoring guidance for mentors

- **90+**: Exemplary. Could be used as a teaching sample for the next cohort.
- **80–89**: Solid. Minor gaps in narrative or a small detail missed.
- **70–79**: Passing. History is clean and writeup is present but reasoning is thin.
- **Below 70**: Does not pass. Send back with specific feedback; re-submission allowed.

## Automatic fails

- Submitting someone else's repo.
- Submitting a history that was clean from the start (no cleanup happened).
- Final diff differs from original — means they changed the code, not just the history.

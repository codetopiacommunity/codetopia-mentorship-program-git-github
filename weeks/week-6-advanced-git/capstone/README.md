# Week 6 Capstone — "The Cleanup"

> **XP:** 200 base + up to 50 stretch

## Brief

You're joining a project. The previous developer left you a branch with 10+ scrappy commits — "wip", "fix", "fix fix", "ugh", "done". Your job is to take that branch and rewrite its history into something you'd be proud to put up for code review.

## Setup

Create a new repo and seed it with a deliberately messy history. Do **all** of the following yourself (do not copy from someone else — part of the exercise is generating the mess):

- At least **10 commits**, of which:
  - At least 3 have non-conventional messages (e.g., `wip`, `stuff`, `...`).
  - At least 2 are one-line "fix" follow-ups to an earlier commit.
  - At least 1 adds a file that a later commit deletes (noise).
  - At least 1 has a typo in the message.
  - At least 2 are genuinely good (feat or fix with a clear message).

Commit as you go — don't fake the timestamps.

## Requirements

Transform that history into a clean one. You must:

1. End with **between 3 and 6** commits, all Conventional Commits format.
2. Use **at least 4** different `rebase -i` verbs across your session (`pick`, `reword`, `squash`, `fixup`, `drop`, `edit`).
3. Use `git commit --amend` at least once.
4. Keep the final diff (working tree) identical to the original — *cleaning history should not change the end state*.
5. Include a `WRITEUP.md` (see below).

## Writeup (`WRITEUP.md`)

Must contain:

- **Before** — the original log (`git log --oneline --graph`) pasted into a fenced code block.
- **After** — the cleaned log.
- **Narrative** — for each final commit, one paragraph on which original commits contributed to it and why you chose that grouping.
- **Reflection** — 3–5 sentences on something that surprised you, and the Golden Rule in your own words.

## Deliverable

Open a PR adding your project under `projects-showcase/week-6-projects/<your-handle>/`. Include:

- The cleaned repo (as a subfolder, with `.git/` intact — so reviewers can see your log).
- `WRITEUP.md`.

See [`../../../CONTRIBUTING.md`](../../../CONTRIBUTING.md).

## Grading

See [`rubric.md`](./rubric.md). **Pass = 70+**. Use [`checklist.md`](./checklist.md) before submitting.

## Stretch (+50 XP)

- After rebasing, push to a GitHub repo and demonstrate `git push --force-with-lease`. Include a screenshot of the push output.
- Deliberately "lose" a commit during the rebase, recover it via `reflog`, and cherry-pick it back. Document this under a `RECOVERY.md`.
- Write a short second section in `WRITEUP.md` titled "When I would NOT do this" — describing a scenario where rewriting the history would be the wrong call.

## Hints

- Before starting the rebase, tag the original HEAD: `git tag before-cleanup`. If you mess up irrecoverably, you can `git reset --hard before-cleanup`.
- `git log --oneline --graph --all` is your friend.
- Don't be afraid of `git rebase --abort`.

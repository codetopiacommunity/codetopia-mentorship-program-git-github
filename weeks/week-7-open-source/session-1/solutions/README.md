# Solutions — Session 1 (Mentor Only)

## What a passing triage notebook looks like

A strong submission should:

1. Cast a wide enough net (10+ candidates) so you can tell they actually looked around, not just picked the first thing.
2. Have a **consistent** format across the 5 deep-triages — same headings, same ordering.
3. Actually **reject** some candidates, not just rate them all Green. The exercise is about discrimination.
4. Draft a comment that is specific and polite, not generic.

## Sample filled-in triage entry

```
### Candidate 3 — `nocodb/nocodb` issue #1234

**Project**
- URL: https://github.com/nocodb/nocodb
- Last commit: 2 days ago
- Open/closed: 700 / 4500
- Last merged PR: yesterday, 3 different contributors
- CONTRIBUTING.md: yes, thorough, includes dev setup in Docker
- CI: yes, green checks on recent PRs
- Verdict: GREEN — clearly alive, welcoming.

**Issue**
- URL: https://github.com/nocodb/nocodb/issues/1234
- Labels: good-first-issue, type:docs
- Assignee: none
- Last comment: 3 weeks ago (maintainer clarifying scope)
- Ask: fix a broken link in docs/setup.md and update the matching screenshot.
- Estimate: 1 hour.
- Concerns: none — well-scoped, unclaimed, doc-only.

**Me**
- Skills: yes — Markdown and a screenshot tool.
- Would enjoy: yes — low-stakes first PR.
```

## Common mentee mistakes

1. **All Greens.** They haven't actually applied the criteria; they've picked easy targets. Push them to examine one stale-looking project too and rate it honestly.
2. **Picking a trending mega-project** (e.g., React, Kubernetes) for a first PR. Technically allowed, but the maintainer response rate on popular projects is slower and the bar is higher. Discuss tradeoffs.
3. **Drafting "Please assign me" as the comment.** Send them back to the lecture's "Good vs Bad template" section.
4. **No concrete estimates.** "Some time" or "a while" doesn't count.

## Feedback rubric for this session

| Area | Points | Notes |
|------|--------|-------|
| 10+ candidates considered | 10 | Evidence in the notebook. |
| 5 deep triages complete | 25 | All three lenses covered for each. |
| Health verdicts assigned | 10 | Mix of ratings, not all green. |
| Drafted comment | 10 | Polite, specific, follows etiquette. |
| Shortlist with reasoning | 10 | Defends picks. |
| Writeup quality | 10 | Organized, readable. |
| **Total** | **75** | Pass = 55+. |

## Stretch bonus

- `gh repo view` snippets: +10
- Built-and-ran confirmation: +10
- Archaeology PR link: +5

## If a mentee is stuck finding candidates

Point them at these safe starters:

- [`EddieHubCommunity/LinkFree`](https://github.com/EddieHubCommunity/LinkFree) — beginner-friendly, active.
- [`firstcontributions/first-contributions`](https://github.com/firstcontributions/first-contributions) — designed as a tutorial PR.
- [`public-apis/public-apis`](https://github.com/public-apis/public-apis) — adding API entries is a gentle doc-style PR.

But discourage submitting to these as the *capstone* — the mentorship should push them to a real project too.

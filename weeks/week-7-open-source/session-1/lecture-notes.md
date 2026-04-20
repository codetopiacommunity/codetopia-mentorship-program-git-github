# Lecture Notes — Finding Good First Issues

## 1. The three-lens triage

When you evaluate an issue, look through three lenses in order:

1. **Project** — is this project alive and welcoming?
2. **Issue** — is this issue actually a good first issue?
3. **Me** — do I have the skills (or am I willing to learn them)?

If any of the three fails, move on. There is no shortage of issues on GitHub.

## 2. Lens 1 — Project health

Open the repo and spend two minutes looking at:

### Signs of health

- Commits to `main` in the last month.
- Issues getting labeled and responded to within a week.
- A `CONTRIBUTING.md` that reads like it was written by a human.
- CI running on PRs (green checkmarks visible).
- Recent merged PRs from *multiple* contributors, not just one person.
- A reasonable ratio of open to closed issues.

### Red flags

- Last commit: 18 months ago.
- 400 open issues, most with no comments and no labels.
- Last merged PR 6 months ago.
- Maintainer's last activity across GitHub: a year ago.
- A CONTRIBUTING.md that says "contributions welcome!" and nothing else.
- All recent PRs closed without merge, with no explanation.

> 💡 **Mentor framing:** "If it feels like nobody's home, nobody's home."

### Tools that help

- [Snyk Open Source Advisor](https://snyk.io/advisor/) — scores npm/PyPI packages.
- [Ecosyste.ms](https://ecosyste.ms/) — activity metrics on a project.
- The "Insights" tab on any GitHub repo.

## 3. Lens 2 — The issue itself

### A good "good first issue" has

- A clear description of the problem or feature.
- An expected outcome or acceptance criteria.
- Labels like `good first issue`, `help wanted`, or `documentation`.
- No active assignee.
- No comments saying "I'm working on this" from the last few weeks.
- A scope you can honestly estimate in 1–3 hours.

### Red flags

- "Refactor the entire caching layer" labeled as `good first issue` (it isn't).
- The issue is 2 years old with 30 comments debating the approach.
- Three people have said "I'll take this" and disappeared.
- The maintainer's last comment is "I'm not sure we want to do this after all."
- The fix requires access you don't have (prod credentials, a specific device).

### The "is this still being worked on?" etiquette

If someone claimed it 3 weeks ago and disappeared:

- Do NOT tag them aggressively.
- Do comment once, politely:

  > "Hi @previous-claimant, are you still working on this? If not I'd love to pick it up."

- Wait **5–7 days** for a response.
- Then comment to the maintainers:

  > "Hi maintainers, I haven't heard back. Is it OK if I take a swing at this?"

- Only start work after a maintainer (or the previous claimant) gives the green light.

## 4. Lens 3 — You

Be honest:

- Can you actually build and run the project locally?
- If the issue touches a subsystem you don't know, are you willing to spend a weekend learning it?
- Does the project's tech stack match your skills (or your learning goals)?

It's fine to pick something slightly stretchy. It's not fine to pick something you have no business touching yet.

## 5. Search queries that actually work

GitHub's search is powerful but awkward. Memorize these patterns:

```text
label:"good first issue" is:open is:issue language:python
```

```text
label:"help wanted" is:open is:issue archived:false updated:>2025-10-01
```

```text
label:"good first issue" is:open no:assignee language:javascript stars:>100
```

Breakdown:

- `label:"..."` — match any issue label (use quotes if it contains spaces).
- `is:open is:issue` — just open issues, not PRs.
- `no:assignee` — rules out claimed issues.
- `language:X` — filter by primary repo language.
- `archived:false` — skip archived (dead) repos.
- `updated:>YYYY-MM-DD` — recent activity only.
- `stars:>100` — vaguely popular.

### Aggregator sites

Don't just use GitHub search. These curate:

- [goodfirstissue.dev](https://goodfirstissue.dev/)
- [goodfirstissues.com](https://goodfirstissues.com/)
- [firstcontributions.github.io](https://firstcontributions.github.io/)
- [up-for-grabs.net](https://up-for-grabs.net/)

## 6. Reading CONTRIBUTING.md

Before you comment, *fully read* CONTRIBUTING.md. Look for:

- Fork-and-PR vs branch-in-main workflow.
- Required issue before PR, or is a PR fine?
- Commit message format (some require Conventional Commits, some DCO sign-off).
- How to run tests (`npm test`, `pytest`, `make test`).
- Linters and formatters (`prettier`, `eslint`, `black`, `ruff`).
- Minimum test coverage.
- PR description template.
- Maintainer expectations on responsiveness (some say "we aim for 7 days").

If there's no CONTRIBUTING.md at all, look at recent merged PRs and imitate their style.

## 7. Live demo script (mentor)

```bash
# 1. Search GitHub
# Open https://github.com/issues?q=label%3A%22good+first+issue%22+is%3Aopen+no%3Aassignee+language%3Apython
# Pick 3 issues, open each in a new tab.

# 2. Triage in real time
# For each one:
#   - Check last commit date on the repo
#   - Open CONTRIBUTING.md
#   - Read the issue description
#   - Score it: Green / Yellow / Red
#   - Narrate why

# 3. Write the "I'd like to work on this" comment together
# Draft it on paper first, critique it, then (maybe) post it.
```

Good template:

```markdown
Hi @maintainers,

I'd like to try this one. Before I start, a quick check:

- My proposed approach is `<X>`. Does that match what you had in mind?
- I see the tests in `tests/foo.py` — should I add a case there, or is there a new spot you'd prefer?

If there's nobody else on it, I'll aim to have a PR up within a week.
```

Bad template:

```markdown
ASSIGN ME
```

## 8. Recap

- Project health before issue quality before your own skills.
- GitHub search is your main tool; aggregators are the assist.
- Etiquette is non-negotiable. You're a guest.
- Read CONTRIBUTING.md before you type a single comment.

## 9. A note on expectations

Your first PR might sit for weeks. That's normal, and not a judgment of you or your work. Open more than one. Don't put all your hope on a single PR.

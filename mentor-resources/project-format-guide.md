# Project Format Guide (for Mentors)

> Read this before Week 1. Re-read before Week 4 and Week 8.

## The one rule

**The lesson is the Git, not the build.**

Every weekly project exists to give the mentee *something to commit, branch, merge, conflict, and PR against*. The artifact's complexity is irrelevant. A 5-file markdown site that demonstrates clean atomic commits is worth more than a 5,000-line app with `wip stuff` in the log.

Carry that idea into every feedback session.

## Why we default to markdown / plain text

| Reason | Why it matters |
| ------ | -------------- |
| **Diffs are legible** | Mentees can *see* what changed. Merge conflicts read like English. |
| **Zero tooling overhead** | Nobody is stuck installing Node / Python / Xcode in Week 1. The friction is Git, on purpose. |
| **Atomic commits feel natural** | "Add a section" maps to one commit. Cleaner habit-building. |
| **It doubles as writing practice** | The about-me page, learning journal, and capstone writeups become real portfolio artifacts. |
| **GitHub renders it for free** | No "deploy" step blocking the dopamine hit. |

When a mentee asks "can I use [framework X]?" — the answer is usually *not yet, here's why*. Let them earn the complexity by Week 5.

## The format arc, week by week

| Weeks | Default format | Notes for mentors |
| ----- | -------------- | ----------------- |
| **1–3** | Pure markdown / text | About-me page, recipe collection, branched personal site. If a mentee insists on HTML, that's fine, but no JS yet. Force their attention onto the commit history, not the rendered output. |
| **4** | Markdown, optional static HTML | They're learning remotes, push, pull. The artifact can stay simple. GitHub Pages is a great optional reward — it lights up the "wait my site is *on the internet*" moment. |
| **5** | Markdown writeup (PR target = this repo) | Capstone is a real PR against our mentorship repo's `projects-showcase/`. Format is determined by us, not them. Keep the bar at "a PR I'd happily merge at work." |
| **6** | Markdown again | The rebase capstone is about *history*, not content. A messy log of fake commits on a tiny markdown project is *exactly* the right scope. Don't let scope creep in. |
| **7** | Whatever the target project uses | They're contributing to an open-source project they didn't pick the format for. Coach them to *match the host project's conventions* — that's the lesson. |
| **8** | Mentee's choice (with constraints) | Graduation: pick one project to polish. Could be markdown site, tiny HTML page, 50-line CLI in any language, a doc site. **Constraint: CI must run something real** (lint, test, link-check). The polish bar is high; the project size is not. |

## When a mentee wants to "level up" early

You'll see this. Someone wants to use React in Week 2.

Try this script:

> *"Cool — and I want you to get there. But this week the *point* is the staging area. If we add a framework, you'll spend the session debugging your tooling instead of building Git muscle memory. Let's hold off until Week 5, when you'll have the chops to debug both. Deal?"*

If they push back: let them, but require markdown commits *in addition* to whatever they want to build. The Git lesson still has to land.

## When a mentee struggles with even markdown

That's not a project problem — that's a signal. Pause. Reduce scope before adding complexity. Coach them to:

1. Write one sentence in `README.md`.
2. Commit it.
3. Look at `git log`.
4. Smile.

Five times in a row.

## How to talk about this in Session 1

Add a 30-second bit to your Week 1 intro:

> *"We're going to keep the *projects* boring on purpose for the first few weeks. The skill we're building is reading a `git status` and choosing the right next move. Once that's automatic, we'll add complexity. Trust the boredom — it's where the fluency lives."*

This sets expectations early and disarms the "this is too easy" complaint.

## Spotting good vs. bad format choices

✅ Good signals:

- The log tells a story without you opening the files.
- Each commit is one logical change.
- The mentee can explain *why* every commit exists.
- No `.DS_Store` or `node_modules/` in the diff.

🚩 Bad signals:

- One giant "initial commit" with the whole project.
- A `wip` or `asdf` commit in the log.
- The mentee can't say what changed in commit #3.
- Secrets, screenshots, or binaries committed.

When you see a 🚩, address it the same week. The compounding cost of bad habits is steep.

## Linking this back to rubrics

Every capstone rubric weights **Git hygiene** (~25 pts), **commit messages** (~15 pts), and **`.gitignore` correctness** (~5–10 pts). That's almost half the score before the project content even gets read. Make sure mentees know this — and that you grade it that way.

See [`rubrics/capstone-rubric.md`](rubrics/capstone-rubric.md) for the generic template and each week's `capstone/rubric.md` for the per-week breakdown.

## TL;DR for mentors

1. Default to markdown.
2. Let the artifact stay small — let the *craft* grow.
3. Resist scope creep, especially in Weeks 1–3.
4. Use Week 8 as the place to let complexity land.
5. Grade the Git, not the build.

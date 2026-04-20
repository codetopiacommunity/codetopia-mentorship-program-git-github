# Session 1 Project — "Triage Notebook"

> **XP:** 75

## Brief

You will evaluate **five** candidate open-source issues from five different projects and produce a written triage notebook. By the end, you will have a prioritized shortlist of 1–2 issues worth actually attempting next session.

## Steps

### 1. Generate candidates

Using GitHub search, curated sites, or both, assemble **at least 10 candidate issues** that look promising at a glance. Technologies that match your skills or learning goals.

### 2. Deep-triage 5 of them

For each of the 5 you chose to examine closely, answer in your notebook:

**Project**

- URL
- Last commit to default branch
- Open issues / closed issues ratio
- Last merged PR date
- Is there a `CONTRIBUTING.md`? Is it useful?
- CI visible on recent PRs? (yes/no)
- Your "health" verdict: Green / Yellow / Red, with one sentence of reasoning.

**Issue**

- Issue URL
- Labels
- Assignee (if any)
- Last comment date
- In your own words: what does the issue ask for?
- Your estimate: 1 hour / half day / full day / "unclear"
- Any concerning signs? (stale, in-debate, out-of-scope, etc.)

**You**

- Do you have the skills?
- If not, what would you need to learn?
- Would you actually enjoy this?

### 3. Shortlist

Pick your top 1–2 candidates and explain *why*. These are the issues you'll consider attempting in session 2.

### 4. Draft a comment (but don't post yet)

For your top pick, draft the exact comment you would post on the issue to ask if you can work on it. Use the etiquette rules from the lecture. Save it in the notebook.

## Deliverable

A single `triage-notebook.md` file (or a folder of 5 markdown files — your choice), submitted as a PR to `projects-showcase/week-7-projects/<your-handle>/session-1/`.

## Stretch (+25 XP)

- Include for each candidate a `gh repo view <owner>/<repo>` output snippet using the [GitHub CLI](https://cli.github.com/).
- For your top pick, clone the repo and verify you can build and run it. Note the exact build commands in the notebook.
- Do one "archaeology" pass: find a similar recently-merged PR on the same project and link to it as a reference for your approach.

## Checks before submitting

- [ ] 5 issues triaged in depth.
- [ ] 10+ candidates considered overall.
- [ ] Each triage includes Project, Issue, and Me sections.
- [ ] Health verdict (Green/Yellow/Red) for each project.
- [ ] Final shortlist of 1–2 with reasoning.
- [ ] Drafted "I'd like to work on this" comment, **not yet posted**.

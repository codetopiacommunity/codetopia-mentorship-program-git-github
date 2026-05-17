# Week 8 Capstone — The Graduation Project

> **XP:** 150 base + up to 50 stretch
>
> **This is the finale.** When it's done, you will have a project on your GitHub that looks like it was built by a professional, because it will have been.

## The moment

Take a breath. Eight weeks ago, some of you had never run `git init`. Today you're going to ship a versioned, tested, documented, hosted project. The craft is real. You built it.

Now let's put a bow on it.

## Brief

Pick **any one project** to graduate. Options:

- An earlier week's capstone, polished up.
- An open-source contribution from Week 7 expanded into a tiny project of your own.
- A brand-new project you've been wanting to build.

The *project content* matters less than the *shipping craft*. A 50-line CLI with perfect polish beats a 5000-line app with a messy README every time.

## Requirements (all must be present)

### 0. Screenshots folder

- A `screenshots/` folder in your project containing at least 2 screenshots showing the work in action — strong picks include: branch protection settings, green CI on `main`, the published v1.0.0 release page, the rendered README, the live deploy (if any). See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

### 1. Repository hygiene

- Public repository on GitHub (under your account, or transferred to yours).
- Descriptive name — kebab-case, no `test` / `untitled-folder` / `my-project-final-FINAL`.
- A clean, linear or clearly-managed Git history. No `wip` / `stuff` / `asdf` commits.
- All commits follow Conventional Commits.
- `.gitignore` appropriate to the stack.
- `LICENSE` file (MIT or Apache-2.0 if unsure).
- `README.md` of portfolio quality (see section 3).

### 2. Continuous Integration

- `.github/workflows/ci.yml` runs on every push and PR to `main`.
- At minimum: checkout, set up language, install, lint, test.
- CI is currently **green** on `main`.
- Branch protection on `main` requires the CI check before merge (screenshot required in writeup).

### 3. README — portfolio quality

The README must contain, in order:

1. **Title + one-sentence pitch.**
2. **At least 3 badges** (CI, version, license — more welcome).
3. **A visual** — screenshot, GIF, or animated demo. Not a stock image. Actual project output.
4. **Quickstart** — copy-pasteable, gets a stranger to "hello world" in under a minute.
5. **Usage** — at least 2 realistic examples.
6. **Why I built this / About** — humanize it. 2-3 sentences minimum.
7. **Contributing** — a sentence and a link, or a note that PRs are not accepted.
8. **License** — stated, matching the LICENSE file.

### 4. Release

- An annotated `v1.0.0` tag, pushed to the remote.
- A published GitHub Release with release notes in **What's new / Fixes / Breaking changes** format.
- Release notes are human-written (auto-generated is a starting point, not the final product).

### 5. Writeup

A `GRADUATION.md` at the root of your repo OR in your cohort submission folder, with:

- **The pitch** — your 30-second elevator pitch, as if to a recruiter.
- **The journey** — 2-3 paragraphs on what you built, what you struggled with, what you're proud of.
- **What's next** — what would `v1.1.0` contain? What would `v2.0.0` change?
- **Thanks** — to your mentor, your cohort, anyone who helped.

## Deliverable

Submit your work as follows:

1. **Open a PR** (the submission of record) to our cohort repo adding your submission under `projects-showcase/week-8-projects/<your-handle>/`. Include:

   - A `README.md` in the submission folder with:
     - Link to your project repo.
     - Link to the v1.0.0 release.
     - Link to any live deploy (Pages, Vercel, etc.).
     - Embedded screenshot.
     - The pitch (same as GRADUATION.md).
   - `GRADUATION.md` (can live here or in the project repo).
   - Your `screenshots/` folder with: branch protection settings, green CI on `main`, the release page (at minimum).

2. **In the WhatsApp group** (the celebration): once your PR is open, share your best screenshot — the release page, the green CI, or the live deploy — alongside the PR link so the cohort can give you a proper graduation send-off.

## Grading

See [`rubric.md`](./rubric.md). **Pass = 70+.** Use [`checklist.md`](./checklist.md) before submitting.

## Stretch (+50 XP)

Pick any combination up to +50:

- **Live deploy** (+15) — GitHub Pages, Vercel, Netlify, Fly, Railway, any. URL in the README.
- **Test coverage badge** (+10) — a real coverage service hooked up (Codecov, Coveralls).
- **Issue templates** (+10) — `.github/ISSUE_TEMPLATE/bug_report.md` and `feature_request.md`.
- **PR template** (+5) — `.github/pull_request_template.md`.
- **`CONTRIBUTING.md` in the project** (+5) — even if you don't expect PRs.
- **30-second test peer feedback** (+5) — documented in GRADUATION.md.

## Graduation day

Your mentor may ask you to do a **5-minute demo** of your project to the cohort. Treat it as practice for demo days, interviews, and Show HN posts. Own it.

## One last thing

You learned something real. Most people who start programs like this don't finish them. You did.

Ship it.

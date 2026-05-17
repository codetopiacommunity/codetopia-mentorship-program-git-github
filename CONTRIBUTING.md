# Contributing

Welcome! This repository is a *learning environment* — contributions from mentees are not only allowed, they are the point.

## For Mentees

### Submitting Your Capstone

1. Fork this repo to your own GitHub account.
2. Clone your fork locally.
3. Create a branch: `git checkout -b week-<n>-<your-username>-capstone`.
4. Add your project files under `projects-showcase/week-<n>-projects/<your-username>/`.
5. Include a `README.md` in your project folder describing what you built.
6. **Include a `screenshots/` folder** in your project with at least one screenshot showing the result (terminal output, rendered page, `git log` graph — whatever proves the work). See [Screenshot conventions](#screenshot-conventions) below.
7. Commit using the [commit message guide](templates/commit-message-guide.md).
8. Push your branch and open a pull request against `main`.
9. Request a review from your mentor.
10. **Share a quick screenshot in the WhatsApp group** so the cohort can cheer you on. The PR is your submission; WhatsApp is the celebration.

### Screenshot conventions

Every project — session work and capstone alike — gets a `screenshots/` folder.

```
projects-showcase/week-<n>-projects/<your-handle>/
├── README.md
├── screenshots/
│   ├── 01-git-log.png
│   ├── 02-branches.png
│   └── 03-final-result.png
└── ...your other project files
```

Rules:

- **The folder in your project is the submission of record.** WhatsApp is informal — files there don't survive.
- Name screenshots `NN-description.png` (`01-`, `02-`, …) so they sort naturally.
- PNG or JPG. Keep each under ~1 MB.
- No secrets in the frame — blur tokens, emails, paths you don't want public.
- Reference key screenshots inline in your project `README.md` so reviewers don't have to dig.

### Asking Questions

- **Quick clarifications:** comment on the relevant session `README.md` line (via Discussions).
- **Stuck for >15 minutes:** open a Discussion in the **Q&A** category — include what you tried.
- **Bug in course content:** open a GitHub Issue with the `content-bug` label.

## For Mentors

### Updating Course Content

1. Branch from `main`: `git checkout -b content/<week>-<short-name>`.
2. Make your changes.
3. Open a PR — even for content changes; this models the workflow for mentees.
4. Tag at least one other mentor for review.

### PR Checklist

- [ ] Links work
- [ ] Code snippets run as-is
- [ ] No mentee PII in examples
- [ ] Capstone rubric (if changed) still sums correctly

## Commit Convention

We follow conventional commits. See [`templates/commit-message-guide.md`](templates/commit-message-guide.md) for the full spec.

```
<type>: <brief description>
```

Types: `feat`, `fix`, `docs`, `refactor`, `chore`.

## License

By contributing, you agree that your contributions will be licensed under the MIT License (see [LICENSE](LICENSE)).

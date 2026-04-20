# Solutions — Week 5 Session 1

> **Mentor only.** Don't peek until you've tried.

## Expected `git remote -v` after step 3

```
origin    git@github.com:ada/git-github-mentorship.git           (fetch)
origin    git@github.com:ada/git-github-mentorship.git           (push)
upstream  git@github.com:program-org/git-github-mentorship.git   (fetch)
upstream  git@github.com:program-org/git-github-mentorship.git   (push)
```

Two remotes, four lines. `origin` = mentee's fork, `upstream` = the program repo.

## Expected PR shape

- **Base repository:** `program-org/git-github-mentorship`, base branch `main`
- **Head repository:** `<mentee-handle>/git-github-mentorship`, compare branch `docs/add-<mentee-handle>-to-contributors`
- **Diff:** exactly one file changed (`discussions/good-resources.md`), ~1–3 lines added.
- **Title:** follows conventional commit format
- **Body:** filled out from the template; no sections left as `<!-- comments -->`
- **Reviewer:** one requested (mentor's handle)

## Model answer — "Why a fork instead of a branch?"

> "I don't have write access to the program org's repo, so I can't push a branch there directly. Forking gave me a copy on my own account where I *do* have push access; then I propose my branch back via a cross-repo pull request."

## Red-flag review comments to leave

If the mentee's PR lands in any of these states, leave the corresponding feedback — these are teaching moments:

| You see | Comment |
| ------- | ------- |
| PR targets the mentee's own fork's `main` | "Check the base dropdown — it's pointing at your fork, but we want to land this in the upstream repo." |
| Title is `Update good-resources.md` | "Please use conventional commit format: `docs: add <handle> to mentees list`." |
| Description is the unfilled template with HTML comments intact | "Fill out the template — especially *What changed* and *How to test*. Pretend I can't read the diff." |
| PR contains unrelated changes (accidental `package-lock.json` etc.) | "Unrelated file `X` slipped in — can you `git restore` it and force-push the cleanup?" |
| One 400-line commit | "Please split into smaller commits; right now the commit message can't describe all of it truthfully." |

## Stretch — Draft demo

Screenshots should show:

1. The PR with the grey "Draft" label and "Ready for review" button.
2. The PR after conversion — green "Open" label and "Close pull request" / "Merge" buttons.

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| "Compare & pull request" button missing | Pushed straight to their fork's `main` | Branch first: `git switch -c <name>` |
| PR diff shows hundreds of unrelated lines | They cloned the *upstream* and set a wrong `origin` | Re-clone from their fork's URL |
| `upstream` missing from `remote -v` | Skipped step 3 | `git remote add upstream <url>` |

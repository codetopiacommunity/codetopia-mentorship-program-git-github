# Solutions — Session 2 (Mentor Only)

## Expected workflow

Step-by-step, the mentee should produce a terminal session roughly like:

```bash
gh repo fork firstcontributions/first-contributions --clone
cd first-contributions
git remote add upstream https://github.com/firstcontributions/first-contributions.git
git fetch upstream
git switch main
git merge upstream/main

git switch -c docs/ada-add-name
echo "- Ada Lovelace" >> Contributors.md
git add Contributors.md
git commit -m "docs: add Ada Lovelace to Contributors list"

git push -u origin docs/ada-add-name
gh pr create --fill --web
```

## Sample strong PR description

```markdown
## What

Adds my name (Ada Lovelace) to the Contributors list, following the
instructions in the README.

## Why

This is the canonical tutorial PR for first-time contributors. Adding
my name exercises the full fork -> PR -> merge loop.

## How

Appended a single line to `Contributors.md`. No logic changes.

## Testing

- Rendered `Contributors.md` in GitHub preview to confirm formatting.
- `git diff` shows only the intended single-line addition.
```

## Common mentee mistakes

1. **Pushing to `upstream` instead of `origin`.** They usually don't have write access anyway, but the intent-error is worth correcting.
2. **Multiple unrelated changes** in one PR. Teach them to split and open two PRs.
3. **Commit message is the default "Update Contributors.md".** Unacceptable. Reject and ask them to amend.
4. **PR description is just "see title".** Reject with a link to the lecture's four-question section.
5. **Force-pushing after every small fix.** If the PR has been reviewed, force-pushing can hide the review context. Teach them to push additional commits.

## Grading rubric (75 pts)

| Area | Points |
|------|--------|
| Fork + upstream set up correctly | 10 |
| Branch named conventionally | 5 |
| Commit message conventional | 10 |
| PR opened successfully | 10 |
| PR description has all four sections | 20 |
| Reflection is substantive | 15 |
| Follow-up commit demonstrates review loop | 5 |
| **Total** | **75** — pass = 55+ |

## Stretch bonus

- `gh pr checks` screenshot with CI green: +10
- Successful sync + `--force-with-lease`: +10
- Peer review round trip: +5

## Things to avoid doing as a mentor

- Don't open the PR *for* them. The awkwardness is the lesson.
- Don't let them use a disposable account; this PR lives on their GitHub profile forever, and that's the point.
- Don't merge too fast if you control the sandbox — let them sit with "my PR is open and nobody is looking at it" for at least a day, so they feel the reality of the next capstone.

# Week 5 — Common Issues

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| "Compare & pull request" button missing | Pushed to `main`, not a feature branch | Create a branch, push it, button appears |
| PR shows commits from other branches | Opened PR against wrong base | Edit PR → change "base" dropdown to `main` |
| Can't push to a repo you don't own | You're not a collaborator | Fork it first, push to your fork, open PR from fork |
| PR diff is enormous (thousands of lines) | Accidentally committed build artifacts or `node_modules/` | `.gitignore` them; reset the branch and start over |
| "This branch has conflicts that must be resolved" | `main` moved since you branched | `git pull origin main` into your branch, resolve, push |
| Reviewer clicked "Request changes" but feedback is vague | Review culture gap | Ask specifically: "Which line? What would 'good' look like?" |
| Merge button disabled | Required checks failing, or review missing | Read the red banner — it names the blocker |
| Merged a PR by mistake | Big red button fatigue | `git revert <merge-sha>` on `main`, open a new PR explaining |
| Pushed a fix to `main` directly | Forgot to branch | Next time: `git switch -c <branch>` *before* editing |
| Suggested change won't apply | PR branch moved since the suggestion | Reviewer re-suggests on the latest commit |
| Force-pushed to a PR and review comments disappeared | Rewrote history the review was anchored to | Communicate first; prefer additional commits over force-push during review |

If your issue isn't here, post in **Discussions → Q&A** with:

1. A link to the PR
2. The exact behavior you expected vs saw
3. Screenshot of the GitHub banner, if any

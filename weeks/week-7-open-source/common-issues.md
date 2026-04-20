# Week 7 — Common Issues

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| No response from maintainer after 2+ weeks | Project is slow, overloaded, or semi-dormant. | Leave *one* polite bump comment. If still nothing after another 1–2 weeks, move on. Don't ping personal accounts. |
| PR CI is failing but worked locally | Different Node/Python/OS version, or missing lint step you didn't run. | Read the CI config (`.github/workflows/`), reproduce locally, push a fix-up commit. |
| "Please sign our CLA" | Project requires a Contributor License Agreement. | Read it. Most are lightweight (MIT/Apache-style). Sign via the bot's link; your PR will re-check automatically. |
| Maintainer requests changes you disagree with | It's their project; their call. | Respond calmly with your reasoning in *one* comment. If they still disagree, implement their version. Don't argue. |
| Fork is out of date, can't update PR | Fork diverged from upstream. | `git remote add upstream <url>`, `git fetch upstream`, `git rebase upstream/main`, `git push --force-with-lease` on your PR branch. |
| Accidentally committed with personal email | `user.email` wasn't set per-repo. | `git commit --amend --author="Name <correct@email>"` then `--force-with-lease`. For older commits, `git rebase -i` with `edit`. |
| Somebody else claimed the issue after I started | You didn't comment first. | Move on graciously. Next time, comment "I'd like to work on this, is it still available?" *before* starting. |
| CONTRIBUTING.md says run `npm run lint` — I didn't | Missed a step; CI will catch it. | Run it locally, fix the output, push a `style:` commit. Don't force-push if the maintainer has already reviewed. |
| PR description is now wrong because scope changed | You added/removed something during review. | Edit the PR description (you can edit your own OP). Add a summary comment of what changed since the last review. |
| "WIP" in title — reviewer reviewed anyway | Some projects ignore WIP tags. | Convert to Draft PR on GitHub. That's the canonical "don't review yet" signal. |
| Conflicts with `main` after my PR sat a while | Upstream moved. | Rebase your branch on the latest upstream, `--force-with-lease` to update the PR. Don't merge main *into* your PR branch unless the project prefers that (check CONTRIBUTING). |
| "Your PR was closed" without explanation | Rare; usually a project-policy reason. | Politely ask "Could you share what I could have done differently?" Don't re-open. |

If in doubt, err on the side of patience and polite persistence.

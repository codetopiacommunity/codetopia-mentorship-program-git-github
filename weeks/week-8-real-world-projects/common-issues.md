# Week 8 — Common Issues

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Workflow doesn't run on push | File isn't in `.github/workflows/` or YAML is invalid. | Check path is exactly `.github/workflows/ci.yml` (dot, hyphen, lowercase). Run `yamllint` locally. |
| `Error: Process completed with exit code 1` | Actual job failure. | Click into the failing step. Read the last 20 lines. Reproduce locally. |
| `No such file or directory: package.json` in job | `working-directory` missing or wrong. | Add `defaults.run.working-directory: ./app` or per-step `working-directory`. |
| `actions/checkout@v4` cloned but no code | Default is a shallow checkout; some tools need full history. | `with: fetch-depth: 0`. |
| Tests pass locally, fail in CI | Node/Python version mismatch, missing env var, different OS. | Pin a version in `setup-node`/`setup-python`. Check `os: ubuntu-latest` vs your mac. |
| CI runs on every branch; I only want main + PRs | Trigger configured too broadly. | Set `on: { push: { branches: [main] }, pull_request: { branches: [main] } }`. |
| `git push` rejects a tag | Tag with that name already exists on remote. | Choose a new name, or delete: `git push origin :refs/tags/v1.0.0` then re-push. Avoid this for published releases. |
| Tag exists but no GitHub Release page | Tag != Release. | On GitHub: Releases -> Draft a new release -> pick the tag -> write notes -> Publish. Or use `gh release create v1.0.0`. |
| README badges show "unknown" | Badge URL wrong, workflow name mismatched, or repo is private. | Match badge YAML name to the workflow `name:` field. Public repos only for free badge services. |
| GitHub Pages shows 404 | Branch/folder wasn't set. | Settings -> Pages -> Source: Deploy from branch -> `main` / `/docs` or `/`. Wait ~60 seconds. |
| GitHub Pages shows raw Markdown | Pages served the `.md` file without rendering. | Link to an `.html`, use a theme in `_config.yml`, or enable the default Jekyll processing. |
| `CI: pending` forever on a PR | Workflow uses a label/branch filter that excludes this PR. | Check `if:` conditions and `branches:` filter. |
| Secrets undefined in workflow | Used `${{ secrets.FOO }}` but never set `FOO` in repo settings. | Settings -> Secrets and variables -> Actions -> New repo secret. |
| Release notes empty | Forgot to write them or didn't click "Generate release notes". | Edit the release, click "Generate release notes" for auto-draft from PRs. |
| Portfolio reader bounced after 10s | README opens with installation steps, not the pitch. | Move the one-line pitch to the top, then a screenshot, then install. |

If you hit something not listed, check [`../../troubleshooting/`](../../troubleshooting/) or post in the graduation-week channel.

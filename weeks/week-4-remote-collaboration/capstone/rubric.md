# Week 4 Capstone Rubric

Total: 100. Pass: 70+. Stretch adds up to +50 XP.

| Criterion | Points | Great looks like |
| --------- | -----: | ---------------- |
| Local repo set up correctly | 10 | `git init` used, `main` is the default branch, `.git/` exists |
| GitHub repo exists on mentee's account | 10 | Public URL shared; owner matches mentee's handle |
| `origin` remote configured | 10 | `git remote -v` shows exactly one `origin` with matching fetch/push URLs |
| Authentication working | 10 | `ssh -T git@github.com` succeeds, OR HTTPS push didn't prompt for creds |
| At least 5 atomic commits | 15 | One logical change per commit, not one mega-commit |
| Conventional commit messages | 15 | All prefixed (`feat:`, `docs:`, `fix:`, ...), imperative, no trailing period |
| Delivered in two separate pushes | 10 | Evident from reflog or GitHub's "Activity" — not one big push |
| README quality | 10 | 3+ real sections, no placeholder text |
| `.gitignore` present and sensible | 5 | No `.DS_Store`, `node_modules/`, `.env` committed |
| "What I learned" section in PR | 5 | Specific, names a stuck moment, not generic |
| **Total** | **100** | |

## Stretch (+50)

| Item | XP |
| ---- | -: |
| Second remote (`backup`) configured and pushed to | +15 |
| Branch protection enabled on `main` | +10 |
| At least one real `fix:` commit | +10 |
| README bilingual or in a non-English language | +15 |

## Mentor notes

- **Verify the two-push requirement** by checking the "Commits" tab on GitHub — commits land in batches; ask the mentee for `git reflog` output if unclear.
- **Authentication check** is pass/fail — if the mentee is still typing passwords, that's 0 on that line, regardless of whether pushes went through.
- **Conventional commits** are not graded on cleverness — a boring `docs: add projects section` is fine. Penalize only for missing type prefix, past-tense verbs, or trailing periods.

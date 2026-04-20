# Commit Message Guide

Good commit messages are a love letter to future-you (and your teammates).

## Format

```
<type>: <brief description>

[optional body explaining WHY]

[optional footer, e.g. "Closes #42"]
```

## Types

| Type | When to use |
| ---- | ----------- |
| `feat` | A new feature for the user |
| `fix` | A bug fix |
| `docs` | Documentation-only changes |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `chore` | Build, dependencies, tooling, maintenance |
| `test` | Adding or correcting tests |
| `style` | Formatting only — no code logic change |

## Rules

1. **Subject line under 72 characters.** Aim for 50.
2. **Imperative mood.** "add login button" — not "added" or "adds".
3. **No period at the end of the subject.**
4. **Capitalization is optional but consistent.** Pick a style and stick with it.
5. **Explain *why*, not *what*.** The diff already shows what.
6. **Separate subject from body with a blank line.**

## Examples

✅ Good:

```
feat: add password reset flow

Users locked out after 3 failed attempts had no recovery path.
This adds a token-based reset email handler.

Closes #128
```

✅ Good (small change):

```
docs: fix broken link in week-3 README
```

❌ Bad:

```
update stuff
fixed bug.
WIP
asdf
```

## Pro tips

- `git commit` (no `-m`) opens your editor for multi-line messages.
- Run `git log --oneline` to scan your last 20 messages and look for patterns to fix.
- Squash WIP commits before opening a PR.

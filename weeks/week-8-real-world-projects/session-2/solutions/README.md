# Solutions — Session 2 (Mentor Only)

## Reference release notes

```markdown
## What's new
- feat(cli): add `--json` flag for machine-readable output (#12)
- feat: support config file at `~/.myapprc` (#15)

## Fixes
- fix: handle zero-byte input files without crashing (#18)
- fix: correct exit code on lint failure (#19)

## Breaking changes
- None.

**Full changelog:** https://github.com/USER/REPO/compare/v0.9.0...v1.0.0
```

## Reference polished README structure

A passing README should look *roughly* like this:

```markdown
# Notely

> A tiny CLI for organizing plain-text notes from the terminal.

![CI](https://github.com/you/notely/actions/workflows/ci.yml/badge.svg)
![Version](https://img.shields.io/github/v/release/you/notely)
![License](https://img.shields.io/github/license/you/notely)

![screenshot](docs/screenshot.png)

## Quickstart

\`\`\`bash
npm install -g notely
notely new "Meeting notes"
\`\`\`

## Usage

\`\`\`bash
notely list
notely search "quarterly review"
notely export --format markdown > notes.md
\`\`\`

See [docs/USAGE.md](docs/USAGE.md) for all commands.

## Why I built this

I take a lot of notes from the terminal and Obsidian felt heavy for that. This is 300 lines of Node and saves me about 10 minutes a day.

## Contributing

PRs welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT (c) 2026 Ada Lovelace
```

## Common mentee mistakes

1. **Lightweight tag instead of annotated.** `git tag v1.0.0` works but is wrong for a release. Teach the `-a` flag.
2. **Forgot to push the tag.** `git push` doesn't push tags by default. Explicit `git push origin v1.0.0`.
3. **README starts with "Installation".** Pitch belongs at the top. This is the single most common polish miss.
4. **Broken screenshot link.** Usually from a local path, e.g. `/Users/foo/...`. Must be a relative path or URL that resolves on GitHub.
5. **Badges in "unknown" state.** Wrong workflow name in badge URL, or repo is private.
6. **Copy-paste boilerplate without editing.** Pitch says "A great project for X" with `X` still a placeholder.

## Grading rubric (75 pts)

| Area | Points |
|------|--------|
| Annotated `v1.0.0` tag pushed | 10 |
| GitHub Release published with populated notes | 15 |
| README: pitch, visual, badges, quickstart, usage, about — all six | 30 |
| No broken images / badges / links | 10 |
| Versioning reasoning (what would bump v1.1 vs v2.0) | 10 |
| **Total** | **75** — pass = 55 |

## Stretch bonus

- 30-second test with peer feedback reflected: +10
- Additional informative badge: +5
- CHANGELOG present and linked: +5
- Working Pages site: +5

## Grading tip: do the 30-second test yourself

Open each mentee's repo for 30 seconds before scoring. What's your gut?

- Did you immediately understand the project?
- Did you see a visual?
- Did you want to try it?

If "yes" to all three, they pass the README portion automatically. If "no" to any, that's the feedback.

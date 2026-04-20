# Lecture Notes — Releases, Tags, and a Portfolio-Ready README

## 1. Semantic versioning (SemVer)

Version numbers look like `MAJOR.MINOR.PATCH`, e.g. `1.4.2`. The rules:

| Bump | When |
|------|------|
| **MAJOR** | You made a change that breaks existing users' code. |
| **MINOR** | You added a feature, backwards-compatible. |
| **PATCH** | You fixed a bug, no API change. |

Examples:

- `1.0.0 -> 1.0.1`: fix a typo in a log message.
- `1.0.1 -> 1.1.0`: add a new `--verbose` flag.
- `1.1.0 -> 2.0.0`: rename `--old-flag` to `--new-flag` with no alias.

Pre-1.0 (`0.x.y`) is "anything goes" territory — you're saying "I'm not committing to stability yet." That's fine for early projects.

> 💡 **Mentor framing:** "SemVer is a promise you make to your users. Break it and they stop trusting you."

## 2. Tags: two kinds

### Lightweight tag

```bash
git tag v1.0.0
```

Just a name pointing at a commit. No author, no message, no metadata. Don't use these for releases.

### Annotated tag

```bash
git tag -a v1.0.0 -m "First stable release"
```

A full Git object — has author, date, message. Can be GPG-signed. **This is the kind you want for releases.**

### Push tags

Tags don't push with `git push` by default.

```bash
git push origin v1.0.0           # push one tag
git push origin --tags           # push all local tags (careful — all of them)
```

### Inspect

```bash
git tag                          # list all
git show v1.0.0                  # see the annotation + the commit
git describe --tags              # describe HEAD relative to nearest tag
```

### Move or delete a tag (don't, mostly)

```bash
git tag -d v1.0.0                # delete locally
git push origin :refs/tags/v1.0.0  # delete on remote
```

Moving a tag after publishing it is the same kind of sin as rewriting shared history. Don't.

## 3. GitHub Releases

A tag marks a commit. A **Release** is a GitHub UI page built on top of a tag, with:

- A title.
- Release notes (usually Markdown).
- Optional binary attachments (compiled artifacts, installers, etc.).
- An RSS feed so people can subscribe.

### Creating a release

**On GitHub (UI):** Releases -> Draft a new release -> pick the tag -> write notes -> Publish.

**With `gh` CLI:**

```bash
gh release create v1.0.0 \
  --title "v1.0.0 — first stable release" \
  --notes-file RELEASE-NOTES.md
```

### Auto-generated notes

GitHub can generate release notes from merged PRs since the last tag. On the release form, click **"Generate release notes"**. Clean it up, don't ship it raw.

### A good release notes template

```markdown
## What's new
- feat: added dark mode support (#42)
- feat: CLI now accepts `--json` flag for scripting (#47)

## Fixes
- fix: correctly handle empty input files (#45)
- fix: retry transient network errors (#48)

## Breaking changes
- None. `v1.x` users can upgrade freely.

## Contributors
- Thanks to @alice, @bob, and @chris.

**Full changelog:** https://github.com/USER/REPO/compare/v0.9.0...v1.0.0
```

## 4. The portfolio-ready README

A recruiter, a hiring manager, or a fellow dev lands on your repo. You have **30 seconds** before they decide. Everything below is the difference between "meh" and "oh, cool."

### The six things every portfolio README needs

1. **One-sentence pitch** — what it does and who it's for. At the very top, under the title.
2. **A visual** — screenshot, GIF, or diagram. The single biggest credibility signal.
3. **Badges** — CI status, latest version, license. Signals life.
4. **Install + quickstart** — one copy-pasteable block that gets someone to "hello world" in under a minute.
5. **Usage** — real examples, not reference dump. Commands they'd actually run.
6. **About the author / license / contributing** — who made this, how to reach you, license.

### Rough template

```markdown
# <Project Name>

> One-sentence pitch. What does it do, for whom?

![CI](https://github.com/you/project/actions/workflows/ci.yml/badge.svg)
![Version](https://img.shields.io/github/v/release/you/project)
![License](https://img.shields.io/github/license/you/project)

<!-- A GIF or screenshot here is worth more than three paragraphs. -->
![screenshot](docs/screenshot.png)

## Quickstart

```bash
npm install -g your-project
your-project --help
```

## Usage

```bash
your-project analyze data.csv --output report.html
```

See [docs/USAGE.md](docs/USAGE.md) for more.

## Why I built this

One or two paragraphs. Humanize it.

## Contributing

PRs welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT (c) 2026 Your Name
```

### Things to avoid

- Starting with "Installation" (pitch comes first).
- Walls of feature lists with no examples.
- Copy-pasted boilerplate with no personality.
- Broken links, broken images, outdated version numbers.
- Emoji carpet-bomb (a few are fine; 40 in one README is not).

## 5. GitHub Pages — free hosting

Any static site (HTML, or a `/docs` folder, or a built SPA) can be served from your repo for free.

### Easiest setup

1. Settings -> Pages.
2. **Source**: Deploy from a branch.
3. **Branch**: `main`, folder `/ (root)` or `/docs`.
4. Save. Wait ~60 seconds.

Your site is live at `https://<you>.github.io/<repo>/`.

### Tips

- A single `index.html` at the root works. No Jekyll, no build step required.
- If you have a `/docs` folder, point Pages at that. Keeps source tidy.
- For a custom domain: add `CNAME` file, configure DNS. Out of scope today but easy.
- For built SPAs: use a Pages action instead (deploy `dist/` on every push to main).

### A minimal deploy action

```yaml
name: pages
on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v5
      - uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist
      - id: deployment
        uses: actions/deploy-pages@v4
```

## 6. Live demo script (mentor)

```bash
# Assume repo with green CI from session 1

# Tag v1.0.0
git tag -a v1.0.0 -m "First stable release"
git push origin v1.0.0

# Create release from the CLI
gh release create v1.0.0 --generate-notes

# Open the release in the browser; edit the auto-notes to show what polish looks like

# Polish the README live:
# - Add one-sentence pitch at top
# - Add badges
# - Add a screenshot (any screenshot)
# - Add a quickstart block
git add README.md
git commit -m "docs: polish README for v1.0.0"
git push

# Enable Pages in the browser if the project is a static site
# Visit the URL, narrate the feeling of "free hosting in 60 seconds"
```

## 7. The "30-second test"

Mentor exercise at end of session:

- Each mentee shares their repo URL in the chat.
- Everyone else opens a random one for 30 seconds.
- Report back: "Did you understand what it does? Did you feel like trying it?"

This is the most useful feedback loop they'll get all program.

## 8. Recap

- SemVer: MAJOR / MINOR / PATCH. Be strict.
- Annotated tags only. `git tag -a`.
- A tag is not a release. Promote it.
- README in 30 seconds: pitch, visual, badges, quickstart, usage, about.
- Pages for free static hosting. Often one-click.

## 9. One final thought

The difference between "a school project" and "a portfolio piece" is this session. Both can have the same code. Only one has the polish that signals professional care.

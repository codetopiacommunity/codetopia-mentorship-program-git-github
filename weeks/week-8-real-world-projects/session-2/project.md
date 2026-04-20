# Session 2 Project — "Ship v1.0.0"

> **XP:** 75

## Brief

Take your project from session 1 (or any project with green CI) and ship a real release. Tag, publish release notes, polish the README. Optionally deploy with GitHub Pages.

## Steps

### 1. Tag

Create an annotated tag:

```bash
git tag -a v1.0.0 -m "First stable release"
git push origin v1.0.0
```

Verify:

```bash
git show v1.0.0
```

### 2. Create a GitHub Release

Either in the UI or with:

```bash
gh release create v1.0.0 \
  --title "v1.0.0 — first stable release" \
  --generate-notes
```

Edit the auto-generated notes to have three sections:

- **What's new**
- **Fixes**
- **Breaking changes** (say "None" if applicable)

Publish.

### 3. Polish the README

Your README must contain **all six** of:

1. One-sentence pitch directly under the title.
2. A visual (screenshot, GIF, or diagram).
3. At least 2 badges (CI + version recommended).
4. A quickstart code block.
5. A usage section with at least one realistic example.
6. About/license/contributing section.

Commit with a `docs:` message.

### 4. (Optional but encouraged) GitHub Pages

If your project has any kind of static front-end or docs:

- Turn on Pages in Settings.
- Verify the site loads at `https://<you>.github.io/<repo>/`.
- Add the Pages URL to your README under the title.

## Deliverable

A PR adding your project under `projects-showcase/week-8-projects/<your-handle>/session-2/` with:

- Link to your repo.
- Link to the published v1.0.0 release.
- Link to your Pages site (if you did that stretch).
- A `notes.md` containing:
  - Your release notes (pasted).
  - A "30-second pitch" you wrote for the top of the README.
  - One or two sentences about what you'd bump `v1.1.0` for.

## Stretch (+25 XP)

- Run the "30-second test" on 3 peers. In `notes.md`, report what they said and what you changed in response.
- Add a second badge you didn't have before (code coverage, npm version, downloads, etc.) and explain what it signals.
- Add a `CHANGELOG.md` that tracks versions going forward; link it from the README.
- Deploy a working Pages site with a real screenshot, not just default text.

## Checks before submitting

- [ ] `v1.0.0` tag pushed and visible under Releases.
- [ ] Release notes have all three sections filled.
- [ ] README has all six required elements.
- [ ] Screenshot/GIF is visible when viewing the README on GitHub.
- [ ] Badges all render (no "unknown" states).
- [ ] If Pages: site loads and links back to repo.

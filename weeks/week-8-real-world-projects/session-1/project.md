# Session 1 Project — "Your First CI"

> **XP:** 75

## Brief

Take a small project (any project) and add a real CI workflow. Prove it works by intentionally breaking something, watching CI go red, fixing it, and watching it go green.

## Steps

### 1. Pick a project

Any repo with *at least one test*. If you don't have one, use a week-3 or week-4 project and add a single test file.

For Node:

```js
// tests/smoke.test.js
test('true is true', () => {
  expect(true).toBe(true);
});
```

For Python:

```python
# tests/test_smoke.py
def test_truth():
    assert True
```

### 2. Add a `hello.yml` workflow

Create `.github/workflows/hello.yml`:

```yaml
name: hello
on: push
jobs:
  hi:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Hello from ${{ github.actor }} on $(date)"
```

Commit, push, screenshot the Actions tab showing the green run.

### 3. Add a real `ci.yml`

Write a workflow that on push and pull_request to `main`:

- Checks out code.
- Sets up your language version.
- Installs dependencies.
- Runs a linter (if your project has one — add one if it doesn't; `eslint`/`ruff`/`flake8`/etc.).
- Runs tests.

### 4. Prove the red-green cycle

1. Open a PR branch.
2. Break the test deliberately (e.g., `expect(true).toBe(false)`).
3. Push. Screenshot the red CI run.
4. Fix the test. Push again. Screenshot the green CI run.

### 5. Branch protection

On GitHub: configure `main` so that:

- PRs are required.
- The `ci` status check is required before merge.

Screenshot the settings page.

## Deliverable

Submit your work as follows:

1. **In your project's `screenshots/` folder** (the submission of record): collect the four CI screenshots — green hello run, red CI run, green CI run after fix, and branch protection settings. Name them `01-hello-green.png`, `02-ci-red.png`, `03-ci-green.png`, `04-branch-protection.png`. Place the folder at `projects-showcase/week-8-projects/<your-handle>/session-1/screenshots/`.
2. **In the WhatsApp group** (informal share): drop a copy of your best screenshot (the green CI badge moment usually wins) so the cohort can cheer you on.
3. **Open a PR** adding your project (or a link to its public repo) under `projects-showcase/week-8-projects/<your-handle>/session-1/` with:

   - The repo URL.
   - The `.github/workflows/ci.yml` pasted into a `workflow.md` for easy review.
   - The `screenshots/` folder (the same four screenshots above).
   - A short `notes.md` with:
     - Which language/framework you chose.
     - One thing you got wrong first and how you fixed it (every first CI has one).
     - One thing you'd add next (matrix, coverage upload, cache tuning, etc.).

See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

## Stretch (+25 XP)

- Add a **matrix** build across 2+ language versions.
- Add a badge to your `README.md` showing CI status:

  ```markdown
  ![CI](https://github.com/<you>/<repo>/actions/workflows/ci.yml/badge.svg)
  ```

- Cache dependencies (`cache: 'npm'` / `'pip'` / etc.) and compare run times before/after.
- Add an `actions/upload-artifact@v4` step that uploads test reports.

## Checks before submitting

- [ ] Hello workflow ran green at least once.
- [ ] CI workflow has checkout + setup + install + lint + test.
- [ ] Branch protection is on for `main` with CI required.
- [ ] All four screenshots included.
- [ ] `notes.md` is honest (include the thing you got wrong).

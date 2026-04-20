# Solutions — Session 1 (Mentor Only)

## Reference workflow (Node)

```yaml
name: ci

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm run lint
      - run: npm test
```

## Reference workflow (Python)

```yaml
name: ci

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.12'
          cache: 'pip'
      - run: pip install -r requirements.txt
      - run: ruff check .
      - run: pytest
```

## Reference stretch (matrix + badge)

```yaml
name: ci
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [18, 20, 22]
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'npm'
      - run: npm ci
      - run: npm test
```

Badge:

```markdown
![CI](https://github.com/USER/REPO/actions/workflows/ci.yml/badge.svg?branch=main)
```

## Common mentee mistakes

1. **`.github` placed under a subfolder** (e.g. `src/.github/workflows/`) — workflow never triggers. Must be repo root.
2. **YAML indentation wrong** — tabs instead of spaces, or mismatched indents. `actionlint` catches these.
3. **Missing `actions/checkout@v4`** — "No such file" errors because the code isn't cloned.
4. **`npm install` instead of `npm ci`** — works but slower; teach the difference (ci uses lockfile strictly, install may mutate it).
5. **Branch protection set but "Include administrators" unchecked** — they can bypass CI, which defeats the point.
6. **Using `on: push` without branch filter** — CI runs on every branch push even before PR, noisy.

## Grading rubric (75 pts)

| Area | Points |
|------|--------|
| Hello workflow runs | 10 |
| CI workflow with all 5 steps (checkout/setup/install/lint/test) | 25 |
| Red-green cycle demonstrated with screenshots | 15 |
| Branch protection set with CI required | 10 |
| `notes.md` is honest + reflective | 10 |
| Workflow YAML readable (no dead code, sensible names) | 5 |
| **Total** | **75** — pass = 55 |

## Stretch bonus

- Matrix: +10
- Badge in README: +5
- Cache + timing comparison: +5
- Upload artifact: +5

## When a mentee is truly stuck

If their CI just won't go green:

1. Have them run the exact lint/test commands locally first.
2. If green locally, check language version in workflow matches local.
3. If still mysterious, `uses: mxschmitt/action-tmate@v3` gives a debug SSH session into the runner. Use sparingly.

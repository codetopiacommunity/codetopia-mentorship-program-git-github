# Lecture Notes — GitHub Actions Basics

## 1. What GitHub Actions is

GitHub Actions runs arbitrary commands in a fresh VM *every time something happens in your repo* — a push, a PR, a tag, a cron schedule. That's it. That's the whole concept.

You configure it by committing YAML files under `.github/workflows/`. One YAML file per workflow.

## 2. The model

```
Workflow (YAML file)
  triggered by Events (push, pull_request, schedule, ...)
  runs Jobs (in parallel by default)
    each Job runs Steps (in order)
      each Step runs either an Action or a shell command
```

> 💡 **Mentor framing:** "Workflow, job, step. That's the whole mental model. Memorize those three words."

## 3. A hello-world workflow

Create `.github/workflows/hello.yml`:

```yaml
name: hello

on:
  push:

jobs:
  say-hi:
    runs-on: ubuntu-latest
    steps:
      - name: Greet
        run: echo "Hello from $GITHUB_ACTOR on commit $GITHUB_SHA"
```

Commit and push. Go to the **Actions** tab on GitHub. Watch it run.

What's happening:

- `name: hello` — what shows in the Actions UI.
- `on: push` — triggers on any push to any branch.
- `jobs.say-hi` — a job with an arbitrary ID.
- `runs-on: ubuntu-latest` — GitHub gives you a fresh Ubuntu VM.
- `steps` — a list of things to do.
- `run:` — raw shell.

### Built-in environment variables

Useful ones:

- `$GITHUB_ACTOR` — the username triggering.
- `$GITHUB_SHA` — the commit.
- `$GITHUB_REF` — the ref being built (e.g., `refs/heads/main`).
- `$GITHUB_REPOSITORY` — `owner/repo`.

## 4. A realistic CI workflow

Let's lint and test a Node project. Create `.github/workflows/ci.yml`:

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
      - name: Check out code
        uses: actions/checkout@v4

      - name: Set up Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install
        run: npm ci

      - name: Lint
        run: npm run lint

      - name: Test
        run: npm test
```

Key things happening:

- **`uses:`** vs **`run:`** — `uses:` invokes a reusable Action (from the [Actions Marketplace](https://github.com/marketplace?type=actions)). `run:` is just shell.
- **`actions/checkout@v4`** clones your repo into the runner. Without it, the runner has no code.
- **`actions/setup-node@v4`** installs Node. There are equivalents for Python, Go, Java, Ruby.
- **`cache: 'npm'`** caches `node_modules` across runs — massive speedup.
- **`npm ci`** is the CI-safe installer (fails if `package-lock.json` is out of sync).

### Python equivalent

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

## 5. Matrix builds

Run the same job against multiple versions in parallel:

```yaml
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

Three parallel jobs, one per Node version. Same idea for OS:

```yaml
strategy:
  matrix:
    os: [ubuntu-latest, macos-latest, windows-latest]
runs-on: ${{ matrix.os }}
```

## 6. Branch protection — making CI matter

A green CI is just a suggestion until you make it a requirement.

On GitHub: **Settings -> Branches -> Add branch protection rule.**

Recommended for `main`:

- Require a pull request before merging.
- Require status checks to pass — select `test` (or whatever your job ID is).
- Require branches to be up to date before merging.
- Include administrators (yes, you too).

Now nobody can land a red PR. Not even you.

## 7. Debugging a red workflow

When CI fails:

1. Go to **Actions** -> click the failing run.
2. Click the failing job.
3. Click the failing step; its log expands.
4. Look at the last 20–30 lines.
5. Copy the actual error into Google *verbatim*. 80% of the time someone has hit it.

### Common causes

- **Missing environment variable.** Reproduce locally with `env -i PATH=$PATH <cmd>`.
- **Lockfile drift.** Run `npm ci` locally — if it fails, commit an updated lockfile.
- **OS-specific behavior.** Paths, line endings, case-sensitivity.
- **Test depending on real network / real files.** Flaky in CI, works locally.

## 8. Secrets

Anything sensitive (API keys, tokens) goes in **Settings -> Secrets and variables -> Actions**.

Use in workflow:

```yaml
- name: Deploy
  run: ./deploy.sh
  env:
    DEPLOY_TOKEN: ${{ secrets.DEPLOY_TOKEN }}
```

Never print a secret. GitHub auto-masks them in logs, but the habit matters anyway.

## 9. Live demo script (mentor)

```bash
# Start from a small Node/Python repo already pushed to GitHub
mkdir -p .github/workflows
cat > .github/workflows/hello.yml <<'EOF'
name: hello
on: push
jobs:
  say-hi:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Hello from $GITHUB_ACTOR"
EOF

git add .github/workflows/hello.yml
git commit -m "ci: add hello-world workflow"
git push

# Open the Actions tab in the browser, narrate the run
```

Then the real CI:

```bash
cat > .github/workflows/ci.yml <<'EOF'
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
      - run: npm test
EOF

git add .github/workflows/ci.yml
git commit -m "ci: add lint+test workflow"
git push

# Intentionally break a test on a feature branch, open PR, watch it go red
# Fix the test, watch it go green
# Then show branch protection setup in the browser
```

## 10. Recap

- Workflows are YAML under `.github/workflows/`.
- Workflow -> Jobs -> Steps; `uses:` for Actions, `run:` for shell.
- `actions/checkout@v4` is the first step of almost every workflow.
- Matrix builds test across versions / OSes in parallel.
- Branch protection turns CI from suggestion into contract.

## 11. The taste test

If your `ci.yml` is over ~50 lines for a small project, you're probably over-engineering. Keep it lean, add complexity as you need it. CI that's hard to understand gets ignored.

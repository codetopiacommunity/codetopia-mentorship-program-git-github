# "fatal: not a git repository"

## Problem

You ran a Git command in a folder that isn't tracked by Git (no `.git/` directory).

## Fix

If the repo exists elsewhere:

```bash
cd /path/to/your/repo
```

If you meant to start a new one:

```bash
git init
```

## Diagnose

Look for a hidden `.git` directory:

```bash
ls -la
```

You should see `.git/`. If not, you're in the wrong folder.

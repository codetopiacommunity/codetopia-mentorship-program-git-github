# "Your branch is behind 'origin/main' by N commits"

## What it means

The remote has commits you don't have locally.

## Fix

```bash
git fetch origin
git pull origin main
```

If you have local changes you want to keep:

```bash
git stash
git pull origin main
git stash pop
```

## If a merge conflict happens during pull

See [`merge-conflicts.md`](merge-conflicts.md).

## Prevention

`git pull` at the start of every session — make it muscle memory.

# "You are in 'detached HEAD' state"

## What it means

You checked out a specific commit (or a tag) instead of a branch. HEAD points at the commit directly. **This is safe** — you're just *looking around*.

## When it happens

- `git checkout <commit-sha>`
- `git checkout v1.0.0` (a tag)
- After certain `git pull` failures

## Fix

If you don't need to keep changes:

```bash
git switch main          # or any branch name
```

If you made commits while detached and want to keep them:

```bash
git switch -c rescue-branch     # save them on a new branch
git switch main                 # then merge or PR rescue-branch
```

## Prevention

Always check out branches by name (`git switch <branch>`), not by SHA, unless you know why.

# "I lost a commit!"

Spoiler: you almost certainly didn't. Git rarely throws anything away within ~30 days.

## First, check `reflog`

```bash
git reflog
```

You'll see every move HEAD has made. Find the SHA you want.

## Recover

If the commit was on a branch you reset:

```bash
git checkout <sha>            # look around
git switch -c rescued         # save it on a new branch
```

If you accidentally `git reset --hard`:

```bash
git reset --hard <reflog-sha>
```

## Prevention

- Before destructive commands (`reset --hard`, `rebase`), make a backup branch:
  ```bash
  git branch backup-$(date +%s)
  ```
- Never `--force-push` to `main`.
- Commit early, commit often.

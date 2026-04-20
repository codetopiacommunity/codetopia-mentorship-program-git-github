# Merge Conflicts

## What it means

Two branches changed the same lines of the same file in incompatible ways. Git refuses to guess.

## Anatomy of a conflict

```
<<<<<<< HEAD
your version
=======
their version
>>>>>>> feature-branch
```

## Fix (the calm version)

1. `git status` — see which files conflict.
2. Open each conflicted file. Decide what stays:
   - Keep yours, theirs, both, or write something new.
   - **Delete the `<<<<<<<`, `=======`, and `>>>>>>>` markers.**
3. `git add <file>` for each resolved file.
4. `git commit` — Git pre-fills a merge message; just save.

## Tools that help

- VS Code: built-in conflict viewer with "Accept Current / Incoming / Both" buttons.
- `git mergetool` if you've configured one (e.g., `meld`, `kdiff3`).
- `git diff --name-only --diff-filter=U` lists just the conflicted files.

## Abort if it gets scary

```bash
git merge --abort
```

You're back to where you started. No harm done.

## Prevention

- Pull / rebase often — small conflicts are easy.
- Communicate before working on the same file.
- Keep branches short-lived.

# Solutions — Week 4 Session 2

> **Mentor only.** Don't peek until you've tried.

## Expected rejection output (step 6)

```
To github.com:ada/diverge-demo.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'github.com:ada/diverge-demo.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
```

Mentees should **not** respond by force-pushing. Reinforce: the fix is `pull`, not `--force`.

## Expected `git status` after rejection

```
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)
```

## Expected `git log --graph --oneline --all` (after merge)

```
*   7ab91f2 (HEAD -> main, origin/main) Merge branch 'main' of github.com:ada/diverge-demo
|\
| * 3c8a4e1 docs: add A section
* | b2f09d7 docs: add B section
|/
* 9e11fa0 feat: seed README
```

The `*   Merge` node with the `|\` splitter is the tell — a proper merge commit with two parents.

## Expected `git branch -vv`

```
* main 7ab91f2 [origin/main] Merge branch 'main' of github.com:ada/diverge-demo
```

Look for `[origin/main]` — that's the tracking link.

## Model answer — "What does `fetch` do that `pull` doesn't let you do?"

> "`git fetch` updates my `origin/*` remote-tracking branches without touching my local branch, so I can inspect the incoming commits with `git log main..origin/main` or `git diff` before I decide to merge them. `git pull` fetches and merges in one step, which is convenient but gives me no chance to look first."

## Stretch answer — rebase vs merge shape

With `git pull --rebase`:

```
* 2f90a31 (HEAD -> main, origin/main) docs: add B section
* 3c8a4e1 docs: add A section
* 9e11fa0 feat: seed README
```

A straight line — no merge commit. B's work was *replayed* on top of A's. Mention that this rewrites the local B commit (new SHA), which is fine here but dangerous on shared branches.

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| Merge conflict markers in file | Normal — Git can't auto-merge | Edit, keep the right lines, remove markers, `git add`, `git commit` |
| `fatal: refusing to merge unrelated histories` | `init` on both sides instead of `clone` | `git pull origin main --allow-unrelated-histories` |
| Mentee force-pushes | Reflex to "make the error go away" | Revert mentally; show `git reflog` to recover if they nuked someone's commit |
| `origin/main` not updating | They ran `git merge` but never `git fetch` | Run `git fetch origin` |

# Lecture Notes — Cloning, Pulling, Fetching

## 1. `git clone` — downloading a repo

```bash
git clone git@github.com:ada/hello-remote.git
```

That one command does five things:

1. Creates a folder named `hello-remote/`.
2. Initializes `.git/` inside it.
3. Adds a remote called `origin` pointing at the URL you cloned from.
4. Downloads the entire history.
5. Checks out the default branch (usually `main`).

You never need to `git init` after a `git clone`. They're mutually exclusive.

```bash
cd hello-remote
git remote -v
# origin  git@github.com:ada/hello-remote.git (fetch)
# origin  git@github.com:ada/hello-remote.git (push)

git log --oneline
# (full history, already here)
```

### Cloning into a different folder name

```bash
git clone git@github.com:ada/hello-remote.git my-folder
```

## 2. The mental model — three branches, not two

When you clone, Git actually tracks **three** pointers related to `main`:

- `main` — your local branch. Moves when *you* commit.
- `origin/main` — a *remote-tracking* branch. A snapshot of where `main` was on the remote **last time we talked to it**.
- `origin`'s real `main` on GitHub — the truth. You can't see it without asking.

```
 (GitHub)   main  →  [C1]──[C2]──[C3]──[C4]
                                          ^
                                          truth

 (local)    origin/main  →  [C1]──[C2]──[C3]       ← last-known snapshot
            main         →  [C1]──[C2]──[C3]       ← your branch
```

`git fetch` updates `origin/main`. It never touches your `main`. `git pull` updates both.

> Mentor framing: "`origin/main` is a cached memory of the remote. It only refreshes when you ask."

## 3. `git fetch` — download without merging

```bash
git fetch origin
```

This contacts the remote, downloads any new commits, and updates `origin/main` (and other `origin/*` branches). Your working files don't change. Your local `main` doesn't move.

Then you can look before you leap:

```bash
git log --oneline main..origin/main        # what's on origin that I don't have
git log --oneline origin/main..main        # what I have that origin doesn't
git diff main origin/main                  # actual content diff
```

If it looks good, merge it in:

```bash
git merge origin/main
```

## 4. `git pull` — fetch + merge, in one step

```bash
git pull origin main
```

Is (roughly):

```bash
git fetch origin
git merge origin/main
```

`pull` is convenient but skips the "look before you leap" step. Both are valid — use `pull` for routine sync, `fetch` when you want to inspect before merging.

### `pull --rebase`

```bash
git pull --rebase origin main
```

Instead of creating a merge commit, Git replays your local commits on top of the remote. Cleaner history, but rewrites your local commits. We'll go deeper on rebase in Week 7. For this week, plain `pull` is fine.

## 5. Tracking branches and `git branch -vv`

Remember `git push -u origin main` from Session 1? That `-u` set up **tracking**. You can see tracking status with:

```bash
git branch -vv
# * main 4a2b1c0 [origin/main] feat: add contact section
```

The `[origin/main]` part means "this branch tracks `origin/main`." With tracking, `git status` gains superpowers:

```
On branch main
Your branch is up to date with 'origin/main'.
# or
Your branch is ahead of 'origin/main' by 2 commits.
# or
Your branch and 'origin/main' have diverged,
and have 1 and 2 different commits each, respectively.
```

Read these like a dashboard. Every sync session starts with `git status`.

## 6. The "ahead / behind / diverged" trichotomy

| State | Meaning | Fix |
| ----- | ------- | --- |
| **Ahead by N** | You've committed locally, haven't pushed | `git push` |
| **Behind by N** | Remote has commits you don't have | `git pull` |
| **Diverged (ahead by X, behind by Y)** | You *and* someone else committed on top of a common ancestor | `git pull` (creates a merge) or `git pull --rebase` |
| **Up to date** | All three pointers agree | Nothing to do |

## 7. Resolving a non-fast-forward rejection

The push failure you'll hit most often:

```bash
git push origin main
# ! [rejected] main -> main (fetch first)
# error: failed to push some refs to 'github.com:ada/hello-remote.git'
# hint: Updates were rejected because the remote contains work that you do not
# hint: have locally.
```

Translation: the remote moved while you were working. Fix:

```bash
git pull origin main      # merges the remote into your local
git push origin main      # now fast-forward
```

If the merge has conflicts, see [`../../../troubleshooting/merge-conflicts.md`](../../../troubleshooting/merge-conflicts.md).

**Do not** `git push --force` to "fix" this. Force-push only when you know exactly what you're overwriting — otherwise you may delete a teammate's work.

## 8. `refusing to merge unrelated histories`

The other nasty one. Happens when your local repo and the remote repo were initialized separately (e.g., you clicked "Initialize with a README" on GitHub *after* running `git init` locally).

```bash
git pull origin main
# fatal: refusing to merge unrelated histories
```

One-time fix:

```bash
git pull origin main --allow-unrelated-histories
# resolve any conflicts, commit
```

Prevention: when creating the GitHub repo, leave the "Initialize with README" box **unchecked** if you already have a local repo.

## 9. Live demo script (mentor)

Run this in two panes: pane A simulates "you", pane B simulates "a coworker".

```bash
# Pane A
git clone git@github.com:ada/hello-remote.git siteA
cd siteA
echo "- About" >> README.md
git commit -am "docs: add about bullet"
git push

# Pane B
git clone git@github.com:ada/hello-remote.git siteB
cd siteB
echo "- Contact" >> README.md
git commit -am "docs: add contact bullet"
git push
# !!  rejected (non-fast-forward)

# Pane B: recover
git status                          # "diverged"
git fetch origin
git log --oneline main..origin/main # show the new commit from Pane A
git pull origin main                # merge
git log --oneline                   # merge commit visible
git push                            # now succeeds
```

Key narration moments:

- Before `git pull` in pane B, say: "origin/main knows more than main. Let's catch main up."
- After the merge commit: "notice the pretty 'Y' shape in `git log --graph --oneline --all`."

## 10. Extras worth mentioning

- `git fetch --all` fetches from every remote you have.
- `git fetch --prune` also deletes your local `origin/*` pointers for branches that were deleted on the remote.
- `git remote show origin` prints a human-readable summary of remote branch states.

## 11. Recap

- `git clone` = `init` + `remote add origin` + `fetch` + `checkout`, one command.
- `git fetch` updates your cached knowledge of the remote (`origin/main`) without touching `main`.
- `git pull` is `fetch` + `merge`. Use it for routine sync.
- `git status` tells you ahead / behind / diverged — read it every time.
- Non-fast-forward? `pull`, resolve, `push`. Never `--force` on shared branches.

## Cross-references

- Troubleshooting: [`../../../troubleshooting/branch-behind-origin.md`](../../../troubleshooting/branch-behind-origin.md)
- Troubleshooting: [`../../../troubleshooting/merge-conflicts.md`](../../../troubleshooting/merge-conflicts.md)
- Cheatsheet: [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- Everyday commands: [`../../../resources/command-reference/everyday-commands.md`](../../../resources/command-reference/everyday-commands.md)

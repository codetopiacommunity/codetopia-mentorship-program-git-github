# Lecture Notes — Recovery & Power Tools

## 1. `git reflog` — the time machine

Every time `HEAD` (or any branch ref) moves, Git writes an entry to the reflog. That log is local to your machine and is kept for 90 days by default.

This means: **almost nothing is truly lost in Git.** Hard-reset the wrong commit? Rebase into oblivion? Delete a branch? Reflog knows where HEAD was before you did the terrible thing.

```bash
git reflog
```

Typical output:

```
a3b4c5d HEAD@{0}: reset: moving to HEAD~3
e6f7a8b HEAD@{1}: commit: feat: add login
c5d6e7f HEAD@{2}: commit: wip
b4c5d6e HEAD@{3}: checkout: moving from main to feature
```

To go back to where `HEAD` was before your mistake:

```bash
git reset --hard HEAD@{1}
```

Or recover a specific commit by SHA:

```bash
git branch rescue a3b4c5d
```

### Reflog for deleted branches

```bash
# Yesterday you deleted `feature/login`
git reflog | grep feature/login
# Find the last SHA, then:
git branch feature/login <sha>
```

> 💡 **Mentor framing:** "If you can get to a terminal within 90 days, you can probably get your work back."

## 2. `git cherry-pick` — surgical commit moves

`cherry-pick` applies the diff of a specific commit onto your current branch as a new commit.

```bash
git switch main
git cherry-pick a3b4c5d
```

Use cases:

- A hotfix lives on `main` and you need it on `release/1.2.x` too.
- A commit ended up on the wrong branch.
- You want one commit from a colleague's branch without merging the whole thing.

### Cherry-pick a range

```bash
git cherry-pick a3b4c5d^..e6f7a8b   # inclusive of both ends
```

### Conflicts during cherry-pick

Same flow as rebase:

```bash
# fix conflicts
git add <files>
git cherry-pick --continue
# or bail
git cherry-pick --abort
```

### `-x` for provenance

```bash
git cherry-pick -x a3b4c5d
```

`-x` appends "`(cherry picked from commit a3b4c5d)`" to the message. Great for release branches and backports.

## 3. `git stash` — shelf work aside

You're halfway through a feature when the boss says "hotfix main, now."

```bash
git stash push -m "halfway through signup form"
git switch main
# ...do the hotfix, commit, push...
git switch feature/signup
git stash pop
```

### The full API

```bash
git stash                     # quick stash, no message
git stash push -m "message"   # stash with message
git stash list                # show all stashes
git stash show -p stash@{0}   # see what's in a stash
git stash apply stash@{0}     # apply but keep stash entry
git stash pop                 # apply and delete stash entry
git stash drop stash@{0}      # delete stash entry
git stash clear               # delete ALL stashes (dangerous)
```

### Gotchas

- Stashes are local-only. They don't travel with `git push`.
- Untracked files are NOT stashed by default. Use `-u`:

  ```bash
  git stash push -u -m "includes new files"
  ```

- `stash pop` can produce conflicts. Resolve like any merge conflict.

> 💡 **Mentor tip:** Discourage stash as a long-term storage. If it's important, commit it to a WIP branch.

## 4. `git bisect` — binary search for bugs

Something works in `v1.0.0`. It's broken in `main`. There are 200 commits between them. Which one broke it?

`bisect` binary-searches: mark a known-good and known-bad commit, and Git checks out the midpoint. You test. If it's good, Git picks the midpoint of the later half; if bad, the earlier half. log₂(200) ≈ 8 tests.

### The manual flow

```bash
git bisect start
git bisect bad                  # current HEAD is bad
git bisect good v1.0.0          # v1.0.0 was good

# Git checks out a commit in the middle
# Test it (run the app, run the test)
git bisect good                 # or: git bisect bad

# Repeat until Git prints "<sha> is the first bad commit"

git bisect reset                # back to where you were
```

### Automate it with a script

If you can write a command that returns exit 0 (good) or nonzero (bad), Git runs the whole thing:

```bash
git bisect start HEAD v1.0.0
git bisect run npm test -- --testPathPattern=login.test.js
```

It'll hand you back the first bad commit in minutes, not hours.

## 5. Live demo script (mentor)

### Reflog rescue

```bash
cd rebase-practice
git log --oneline              # note the top SHA
git reset --hard HEAD~3        # "accidentally" nuke 3 commits
git log --oneline              # they're gone!
git reflog                     # but they're not
git reset --hard HEAD@{1}      # restore
git log --oneline              # back
```

### Cherry-pick

```bash
git switch -c demo-target
git switch main
git log --oneline              # find a commit SHA
git switch demo-target
git cherry-pick <sha>
git log --oneline              # new commit, new SHA, same diff
```

### Stash

```bash
git switch -c wip-stash
echo "unfinished" >> todo.txt
git stash push -m "demo stash"
git status                     # clean!
git stash list
git stash pop
git status                     # it's back
```

### Bisect

```bash
# Set up a repo where commit 5 of 10 has a bug
# (have this pre-made for demo speed)
git bisect start
git bisect bad HEAD
git bisect good HEAD~10
# Git checks out HEAD~5
# test, say "git bisect bad" or "git bisect good"
# Watch it narrow down
git bisect reset
```

## 6. Decision tree

```
"I made a mistake with history" -> git reflog
"I need this one commit elsewhere" -> git cherry-pick
"I need to put this work aside briefly" -> git stash
"Something used to work and doesn't anymore" -> git bisect
```

## 7. Recap

- `reflog` is your seatbelt. Check it *before* you panic.
- `cherry-pick` moves a single commit; be mindful of the new SHA.
- `stash` is a short-lived local shelf, not a filing cabinet.
- `bisect` turns "where did this break?" from hours into minutes.

## 8. What not to do

- Do not rely on `stash` to hold days of work. Commit it.
- Do not cherry-pick a commit, then merge the source branch later — the commit ends up twice (though Git often dedupes).
- Do not close the terminal in the middle of a `bisect` session without running `git bisect reset`. Your branch will be stuck in a weird state.

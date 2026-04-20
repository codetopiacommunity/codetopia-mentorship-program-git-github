# Lecture Notes — Rewriting History

## 1. What "rewriting history" actually means

A commit is identified by its SHA (that long hex string). The SHA is a hash of the commit's content *and* its parent's SHA. Change the message, the author, the diff, or the parent — and you get a new commit with a new SHA.

You don't *edit* a commit. You *replace* it with a new one. The old one still exists (for a while — see `reflog` next session), but nothing points to it anymore.

> 💡 **Mentor framing:** "Rebase doesn't move commits. It re-creates them."

## 2. `git commit --amend` — the smallest rewrite

Amend is rebase's tiny sibling. It rewrites only the most recent commit.

### Fix a typo in the last commit message

```bash
git commit --amend -m "feat: add login form"
```

### Add a forgotten file to the last commit

```bash
git add forgot-this.css
git commit --amend --no-edit
```

`--no-edit` keeps the existing message.

> **Only amend commits that haven't been pushed.** Amending a pushed commit is rewriting shared history, which is the thing we're about to make a big deal of.

## 3. Interactive rebase — the main event

```bash
git rebase -i <base>
```

`<base>` is the commit *before* the first one you want to touch. Usually you'll write it like:

```bash
git rebase -i HEAD~5     # touch the last 5 commits
git rebase -i main       # touch all commits since main
```

Git opens an editor with a "todo list":

```
pick a1b2c3d feat: add navbar
pick d4e5f6a fix typo
pick 7g8h9i0 more navbar stuff
pick j1k2l3m wip
pick n4o5p6q final polish
```

You change the word at the start of each line. The order you leave them in is the order Git will replay them.

### The verbs

| Verb | Short | What it does |
|------|-------|--------------|
| `pick` | `p` | Keep the commit as-is. |
| `reword` | `r` | Keep the diff, change the message. |
| `edit` | `e` | Pause so you can change the diff. |
| `squash` | `s` | Combine with the previous commit; merge messages. |
| `fixup` | `f` | Like squash, but discard this commit's message. |
| `drop` | `d` | Delete the commit entirely. |

You can also reorder lines. Git replays them top-to-bottom.

### Example: squash 3 scrappy commits into 1

Start:

```
pick a1b2c3d feat: add login form
pick d4e5f6a fix typo in login
pick 7g8h9i0 actually finish login
```

Change to:

```
pick a1b2c3d feat: add login form
fixup d4e5f6a fix typo in login
fixup 7g8h9i0 actually finish login
```

Save and close. One clean `feat: add login form` commit remains.

### Example: reword the third commit

```
pick a1b2c3d feat: add login form
pick d4e5f6a add tests
reword 7g8h9i0 docs: update README
```

When you save, Git opens a second editor for you to rewrite that message.

## 4. Conflicts during rebase

Because rebase re-applies commits one at a time onto the base, each one can conflict. The flow is:

```bash
# conflict happens
# ...edit conflicted files...
git add <files>
git rebase --continue
```

Or bail out completely:

```bash
git rebase --abort
```

Your branch is restored to exactly where it was before you started.

> 💡 **Mentor tip:** teach `--abort` *first*. Knowing you can always back out makes students less afraid to try.

## 5. The Golden Rule of Rebasing

> **Never rewrite history that has been pushed and that others may have based work on.**

Safe to rebase:

- Local commits you haven't pushed.
- A feature branch *you* own that nobody else has pulled.

Dangerous:

- `main`, `develop`, or any shared branch.
- A PR branch that a colleague has already reviewed or checked out.

### `--force-with-lease`

After rebasing your own feature branch, `git push` will be rejected. You have two options:

```bash
git push --force                # nuclear, don't use
git push --force-with-lease     # polite, use this
```

`--force-with-lease` refuses the push if someone else pushed to the branch since you last fetched. It's the "I checked, I'm not clobbering anyone" version of force-push.

## 6. When to use what

| Situation | Tool |
|-----------|------|
| Typo in last commit message | `git commit --amend` |
| Forgot a file in last commit | `git add X && git commit --amend --no-edit` |
| 6 "wip" commits on my branch before PR | `git rebase -i main`, squash them |
| Need to reorder two commits | `git rebase -i HEAD~N` |
| Want to drop an accidental debug commit | `git rebase -i`, mark `drop` |
| Working on shared branch | **Don't rebase. Merge.** |

## 7. Live demo script (mentor)

```bash
# Set up a messy history
mkdir rebase-demo && cd rebase-demo
git init
echo "# demo" > README.md
git add . && git commit -m "initial"

echo "line 1" >> notes.txt && git add . && git commit -m "wip"
echo "line 2" >> notes.txt && git add . && git commit -m "more wip"
echo "line 3" >> notes.txt && git add . && git commit -m "fix typo"
echo "line 4" >> notes.txt && git add . && git commit -m "final"

git log --oneline   # show the mess

# Amend the last commit message
git commit --amend -m "feat: finalize notes"

# Interactive rebase the last 4 commits
git rebase -i HEAD~4
# In editor: change last 3 to 'fixup', leave first as 'pick'
# (Or reword the first one to be more meaningful)

git log --oneline   # show the clean history
```

Then deliberately break it:

```bash
# Pretend we pushed, then rebase again
git rebase -i HEAD~1   # reword
git reflog             # show that the old commit still exists
git reset --hard HEAD@{2}   # recover
```

## 8. Recap

- Commits are immutable; rewriting is really replacing.
- `--amend` for the last commit, `rebase -i` for anything further back.
- `pick / reword / squash / fixup / drop` — know them.
- Golden Rule: don't rewrite shared history.
- `--force-with-lease` > `--force`.
- If something goes wrong, don't panic — `reflog` is next session's superpower.

## 9. Conventional commits reminder

After squashing, your final messages still need to be conventional:

```
feat(auth): add login form with validation
fix(nav): correct mobile menu z-index
docs: expand README install steps
chore: bump dependency versions
```

See [`../../../templates/commit-message-template.txt`](../../../templates/commit-message-template.txt) for the full format.

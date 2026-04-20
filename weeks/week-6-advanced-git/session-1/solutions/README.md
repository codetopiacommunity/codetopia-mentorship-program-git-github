# Solutions — Session 1 (Mentor Only)

> Do not share with mentees until after the session.

## Walkthrough of the project

### Expected starting log

```
e6f7a8b final touch
c5d6e7f delete useless.txt
b4c5d6e add useless.txt
a3b4c5d stuff
9a2b3c4 fix typo
7890abc wip
1234567 feat: add greeting function
```

### Solution: `git rebase -i <first-commit>^`

Find the root commit SHA with `git log --reverse --oneline | head -1`, then:

```bash
git rebase -i --root
```

Or if the first commit is the "keeper":

```bash
git rebase -i HEAD~6
```

### Example todo list (cleaned)

```
pick   1234567 feat: add greeting function
fixup  7890abc wip
fixup  9a2b3c4 fix typo
reword a3b4c5d stuff
drop   b4c5d6e add useless.txt
drop   c5d6e7f delete useless.txt
fixup  e6f7a8b final touch
```

When the `reword` editor opens, rewrite `stuff` to something like:

```
feat: add farewell function
```

### Expected final log

```
def4567 feat: add farewell function
abc1234 feat: add greeting function
```

## Common mentee mistakes

1. **Marking the top line `squash` or `fixup`** — produces the "cannot squash without a previous commit" error. First line must be `pick`.
2. **Forgetting `git add` after resolving a conflict** — `rebase --continue` will complain "No changes — did you forget to use `git add`?"
3. **Trying to rebase a branch they already pushed without force-with-lease** — their push is rejected, they panic. Walk them through `--force-with-lease` and re-emphasize this is only safe on *their own* branches.
4. **Rebasing and deleting the wrong commit** — this is the perfect teachable moment for `git reflog` (which is the opener of session 2).

## Grading notes

- Full credit if they show genuine understanding of *why* they chose each verb, not just that the final log is clean.
- Partial credit if the log is clean but README doesn't explain the reasoning.
- No credit if they simply `git reset --hard` and re-committed (that's not a rebase).

## Stretch check

If they did the force-with-lease stretch, verify the `README` explicitly mentions:

- Push was rejected on first normal `git push` after rebase.
- `--force-with-lease` succeeded.
- (Bonus) they understood *why* plain `--force` would be dangerous.

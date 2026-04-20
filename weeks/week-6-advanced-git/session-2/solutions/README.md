# Solutions — Session 2 (Mentor Only)

## Part A — reflog

```bash
git reset --hard HEAD~5
git reflog
# Look for the line that says "reset: moving to HEAD~5"
# The previous HEAD@{1} is what we want.
git reset --hard HEAD@{1}
```

Verify with `git log --oneline | wc -l` returns 10.

## Part B — cherry-pick

```bash
git switch -c hotfix HEAD~3

# On main, find a commit SHA
git switch main
git log --oneline
# copy a SHA from the top half
git switch hotfix
git cherry-pick <sha>
```

Verify the new commit on `hotfix` has a different SHA from the source but the same diff:

```bash
git show <original-sha>
git show HEAD
```

## Part C — stash

```bash
git switch main
echo "uncommitted change" >> log.txt
git stash push -m "mid-edit"
git status                     # clean
git switch hotfix
echo "hotfix change" >> log.txt
git add . && git commit -m "fix: tiny hotfix"
git switch main
git stash pop
git status                     # shows modified log.txt
git add . && git commit -m "feat: finish mid-edit"
```

## Part D — bisect

```bash
# Introduce the bug at HEAD~3 position
sed -i '' 's/line 6/BUG/' log.txt     # mac; use -i '' for BSD sed
git add . && git commit -m "chore: tweak line 6"

for i in 1 2 3; do
  echo "extra $i" >> log.txt
  git add . && git commit -m "chore: extra $i"
done

git bisect start
git bisect bad HEAD
git bisect good <initial-sha>

# Git checks out midpoint; inspect log.txt
grep BUG log.txt && git bisect bad || git bisect good
# Repeat until Git announces the first bad commit
git bisect reset
```

### Stretch: `bisect run`

```bash
cat > test.sh <<'EOF'
#!/bin/bash
grep -q BUG log.txt && exit 1
exit 0
EOF
chmod +x test.sh

git bisect start HEAD <initial-sha>
git bisect run ./test.sh
git bisect reset
```

## Common mentee mistakes

1. **Confusing `HEAD@{1}` with `HEAD~1`.** These are completely different. `HEAD@{1}` is "where HEAD was previously"; `HEAD~1` is "the parent of HEAD."
2. **Running `git bisect` without `reset` afterwards.** Their branch is left in a bisect state; next `git status` shows weird output.
3. **Cherry-picking and being confused that the SHA changed.** Good teaching moment: same *content*, different *parent*, hence different SHA.
4. **Stashing untracked files without `-u`.** File appears "lost." Teach them `git stash list` and `git stash show -p -u`.

## Grading notes

Full credit requires a `RESCUE-LOG.md` that shows *understanding*, not just transcript pasting. If they can't answer "when would you use this?" they haven't mastered it — dock 5 points per tool.

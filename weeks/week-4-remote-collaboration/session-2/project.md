# Project — Week 4 Session 2

> **XP:** 50

## What you'll do

Simulate two people working on the same repo and resolve a real divergence — all on your own machine.

## Steps

1. On GitHub, create a new empty repo called `diverge-demo` (no README checkbox).

2. Clone it into **two** separate folders on your laptop:

   ```bash
   git clone git@github.com:<your-handle>/diverge-demo.git copyA
   git clone git@github.com:<your-handle>/diverge-demo.git copyB
   ```

3. In `copyA`, make a commit and push:

   ```bash
   cd copyA
   echo "# Diverge demo" > README.md
   git add README.md
   git commit -m "feat: seed README"
   git push -u origin main
   cd ..
   ```

4. In `copyB`, pull first, then make a conflicting change:

   ```bash
   cd copyB
   git pull origin main
   echo "## From B" >> README.md
   git commit -am "docs: add B section"
   cd ..
   ```

5. Back in `copyA`, make a different change *without* pulling first:

   ```bash
   cd copyA
   echo "## From A" >> README.md
   git commit -am "docs: add A section"
   git push        # this will succeed (A is ahead)
   cd ..
   ```

6. In `copyB`, try to push. Observe the rejection:

   ```bash
   cd copyB
   git push        # ! [rejected] non-fast-forward
   ```

7. Read `git status`, then use `git fetch` to inspect what `origin/main` now holds:

   ```bash
   git status
   git fetch origin
   git log --oneline main..origin/main
   git log --oneline origin/main..main
   ```

8. Resolve the divergence with `git pull`, handle any merge conflict, then push:

   ```bash
   git pull origin main
   # (resolve conflict, save, stage, commit if Git prompts)
   git push
   ```

9. In a single pane, run `git log --graph --oneline --all` to admire your first remote merge.

## Deliverable

Submit your work as follows:

1. **In your project's `screenshots/` folder** (the submission of record): add at least one screenshot — typically `git log --graph --oneline --all` from `copyB` and `git branch -vv`. Name them `01-graph-copyB.png`, `02-branch-vv.png`, etc.
2. **In the WhatsApp group** (informal share): drop a copy of your best screenshot so the cohort can cheer you on.
3. **In the Discussions tab** (additional channel): paste the `git log --graph --oneline --all` and `git branch -vv` outputs in a code block, plus a two-sentence answer to: *"What does `git fetch` do that `git pull` doesn't let you do?"*

See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

## Stretch goal (+10 XP)

Redo step 8 using `git pull --rebase` instead of a plain `git pull`, in a fresh `copyC`. Paste the resulting `git log --graph --oneline --all` alongside your deliverable and describe the shape difference in one sentence.

## Stuck?

- Lecture notes §7 and §8.
- Troubleshooting: [`../../../troubleshooting/merge-conflicts.md`](../../../troubleshooting/merge-conflicts.md)
- Troubleshooting: [`../../../troubleshooting/branch-behind-origin.md`](../../../troubleshooting/branch-behind-origin.md)
- Common issues: [`../common-issues.md`](../common-issues.md)

# Project — Week 3 · Session 2

> **XP:** 75

## What you'll do

Build a `merge-lab` repo and deliberately produce **one of each kind of merge** — fast-forward, three-way, and a conflict you resolve.

## Steps

### Setup

```bash
mkdir merge-lab && cd merge-lab
git init
echo "# Merge Lab" > README.md
echo "" >> README.md
echo "## Features" >> README.md
echo "- TBD" >> README.md
git add README.md
git commit -m "feat: initial README"
```

### Part 1 — Fast-forward merge

1. Create `feature/typos`, make **one commit** fixing the `- TBD` line.
2. Switch to `main`. Do *not* make any commits there.
3. Merge `feature/typos`. Confirm "Fast-forward" in the output.
4. Delete the branch with `-d`.

### Part 2 — Three-way merge (no conflict)

1. Create `feature/intro`. Add a one-paragraph intro *after the title*.
2. Switch to `main`. Add a `## License` section *at the bottom*. Commit.
3. Merge `feature/intro` into `main`. Confirm a merge commit appears in the log.
4. Delete the branch.

### Part 3 — A real conflict

1. Create `feature/tagline`. Change the first line from `# Merge Lab` to `# Merge Lab — Learn By Breaking Things`. Commit.
2. Switch to `main`. Change the first line to `# Merge Lab — A Git Playground`. Commit.
3. Merge `feature/tagline`. You'll get `CONFLICT (content): Merge conflict in README.md`.
4. Open `README.md`. Observe the `<<<<<<<`, `=======`, `>>>>>>>` markers.
5. **Resolve by editing:** pick a final title that reflects *both* intents, e.g. `# Merge Lab — A Git Playground for Breaking Things Safely`.
6. Delete every marker line.
7. `git add README.md`, `git status` to confirm, then `git commit` (accept the default merge message).
8. Delete the branch.

### Part 4 — Abort a merge

1. Create `feature/broken`. Replace the entire README with one line of nonsense. Commit.
2. Switch to `main`. Also change the README first line (differently than before). Commit.
3. Merge `feature/broken`. You'll get a conflict.
4. Run `git merge --abort`. Confirm the README is back to its pre-merge state and `git status` is clean.
5. Delete `feature/broken` with `-D` (it's unmerged on purpose).

## Deliverable

A file `MERGE-LOG.md` committed to the repo with four sections:

- **Fast-forward** — paste the output of `git merge feature/typos`. One sentence: why did Git fast-forward here?
- **Three-way** — paste `git log --oneline --graph --decorate --all` showing the merge commit. One sentence: why wasn't a fast-forward possible?
- **Conflict** — paste the *pre-resolution* file contents (with markers), then the *post-resolution* content. One paragraph: what did you decide, and why?
- **Abort** — paste the `git merge --abort` behavior. One sentence: when should you use `--abort` in real life?

Commit:

```bash
git add MERGE-LOG.md
git commit -m "docs: add merge log"
```

Then submit your work as follows:

1. **In your project's `screenshots/` folder** (the submission of record): add at least one screenshot — typically the colored `git log --oneline --graph --decorate --all` and the conflict-markers moment. Name them `01-merge-graph.png`, `02-conflict-markers.png`, etc.
2. **In the WhatsApp group** (informal share): drop a copy of your best screenshot so the cohort can cheer you on.
3. **In Discussions → Week 3** (additional channel): paste the `git log --oneline --graph --decorate --all` output.

See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

## Stretch goal (+25 XP)

Do Part 2 *again* with `--no-ff` on a branch called `feature/noff-demo`, then explain in your `MERGE-LOG.md` how the graph differs from the default FF case.

## Stuck?

- [`../common-issues.md`](../common-issues.md)
- [`../../../troubleshooting/merge-conflicts.md`](../../../troubleshooting/merge-conflicts.md)
- Post in **Discussions → Q&A** with `git status` and the exact conflict markers.

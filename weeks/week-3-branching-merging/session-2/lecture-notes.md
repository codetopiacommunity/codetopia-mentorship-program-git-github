# Lecture Notes — Merging & Conflict Resolution

## 1. What merging actually means

Merging combines the work of two branches. In pointer terms: take what one branch has, apply it to another, and decide what the combined history looks like.

There are two shapes this takes:

1. **Fast-forward** — one branch is directly ahead of the other. Git just slides the pointer forward.
2. **Three-way merge** — the branches diverged. Git creates a *merge commit* with two parents.

Conflicts are a third thing — not a merge type, but a *condition* that can occur in either.

## 2. Fast-forward merges

Setup:

```
   A ── B ── C          (main)
              \
               D ── E   (feature)
```

`main` is at `C`. `feature` is at `E`, which descends from `C`. No divergence.

```bash
git switch main
git merge feature
```

Result:

```
   A ── B ── C ── D ── E   (main, feature)
```

Git just moved the `main` pointer from `C` to `E`. No merge commit. This is a **fast-forward**.

When you see:

```
Updating c9f1aa2..1d9c4b2
Fast-forward
 README.md | 3 +++
 1 file changed, 3 insertions(+)
```

That's what happened.

## 3. Three-way merges

Setup — now `main` moved too:

```
   A ── B ── C ── F      (main)
              \
               D ── E    (feature)
```

Both branches have commits the other doesn't. Fast-forward is impossible. Git finds the **common ancestor** (`C`), compares both sides, and creates a merge commit `M` with *two parents*:

```
   A ── B ── C ── F ── M   (main)
              \       /
               D ── E      (feature)
```

```bash
git switch main
git merge feature
# Opens an editor: "Merge branch 'feature'". Save & close.
```

The merge commit has two lines pointing back — one to `F` (main's tip), one to `E` (feature's tip). Your history is now a graph, not a line.

## 4. `--no-ff` — forcing a merge commit even when FF is possible

Some teams prefer every merge to leave a trace, even fast-forwardable ones:

```bash
git merge --no-ff feature
```

Creates a merge commit regardless:

```
   A ── B ── C ─────── M   (main)
              \       /
               D ── E      (feature)
```

Pros: every feature is a visible unit in the graph. Easy to revert (one merge commit = one revert).

Cons: noisier history.

GitHub's "Merge pull request" button is `--no-ff`. Its "Squash and merge" compresses the branch to one commit. Its "Rebase and merge" is a different thing entirely (next week).

## 5. Conflicts — what they are

A conflict happens when Git can't automatically decide how to combine two changes. Specifically: **both branches changed the same lines of the same file in incompatible ways.**

Git will:

1. Stop mid-merge.
2. Mark the file with conflict markers.
3. Leave you at a prompt, with `git status` showing "Unmerged paths".

It will *not* lose your work. It will *not* pick a side for you. It's asking.

## 6. Reading conflict markers

When Git stops, the file on disk looks like:

```
## Features

<<<<<<< HEAD
- Dark mode toggle
- Keyboard shortcuts
=======
- Dark mode
- Export to PDF
>>>>>>> feature/dark-mode
```

Anatomy:

- `<<<<<<< HEAD` — start of **our** side (the branch you're merging *into*).
- `=======` — divider.
- `>>>>>>> feature/dark-mode` — end, labeled with **their** side (the branch being merged *in*).

Resolution = *edit the file* until it says what you actually want. Delete the markers. Save.

Example resolution (keeping both, deduped):

```
## Features

- Dark mode toggle
- Keyboard shortcuts
- Export to PDF
```

Then:

```bash
git add <file>            # mark as resolved
git status                # confirm: all conflicts addressed
git commit                # finishes the merge (default message is fine)
```

## 7. The full conflict workflow

```bash
# You're on main, merging a feature
git switch main
git merge feature/dark-mode
# CONFLICT (content): Merge conflict in README.md
# Automatic merge failed; fix conflicts and then commit the result.

git status                         # shows "Unmerged paths: README.md"

# Open README.md in your editor. Find every <<<<<<<.
# Decide what the final content should be. Edit. Save.

git add README.md
git status                         # "All conflicts fixed but you are still merging."
git commit                         # opens editor with default merge message; save & close
git log --oneline --graph --decorate --all
```

## 8. Aborting a merge

Mid-merge, you realize this is a mess and you want out:

```bash
git merge --abort
```

Back to where you were before `git merge`. No half-state. No stress. Do this whenever you feel lost — you can always try again after a cup of coffee.

## 9. Tools that help

### Use `git status` constantly

During a merge, `git status` is gold. It tells you:

- Which files still have conflicts.
- Which files you've staged (resolved).
- That you're mid-merge.

### Use a good editor

VS Code, Cursor, IntelliJ, etc. all render conflicts with buttons: *Accept Current / Accept Incoming / Accept Both*. These generate the same edits you'd do by hand — they're just faster. Use them once you understand what they're doing.

### `git mergetool`

Launches a configured 3-way diff tool. Overkill for this week, but good to know it exists.

## 10. Live demo script (mentor)

```bash
mkdir merge-lab && cd merge-lab
git init
cat > README.md <<EOF
# Merge Lab

## Features

- TBD
EOF
git add README.md
git commit -m "feat: initial README"

# --- Part 1: Fast-forward merge ---
git switch -c feature/typos
sed -i.bak 's/TBD/To be decided/' README.md && rm README.md.bak
git add README.md && git commit -m "fix: clarify placeholder"
git switch main
git merge feature/typos              # narrate "Fast-forward"
git log --oneline --graph --decorate --all
git branch -d feature/typos

# --- Part 2: Three-way merge (no conflict) ---
git switch -c feature/intro
sed -i.bak '1a\
\
A lab repo for practicing merges.' README.md && rm README.md.bak
git add README.md && git commit -m "docs: add intro"

git switch main
# Make a change on main too, but in a different place
echo "" >> README.md
echo "## License" >> README.md
echo "MIT" >> README.md
git add README.md && git commit -m "docs: add license section"

git merge feature/intro              # narrate "Merge made by 'ort' strategy"
git log --oneline --graph --decorate --all
git branch -d feature/intro

# --- Part 3: Conflict (engineered on purpose) ---
git switch -c feature/tagline
sed -i.bak 's/# Merge Lab/# Merge Lab — Learn By Breaking Things/' README.md && rm README.md.bak
git add README.md && git commit -m "feat: add tagline"

git switch main
sed -i.bak 's/# Merge Lab/# Merge Lab — A Git Playground/' README.md && rm README.md.bak
git add README.md && git commit -m "feat: add alt tagline"

git merge feature/tagline            # CONFLICT
git status
cat README.md                        # show the markers
# Resolve: pick one, or combine
sed -i.bak 's/<<<<<<< HEAD//; s/=======//; s/>>>>>>> feature\/tagline//' README.md && rm README.md.bak
# (In reality, open the file and edit. This sed is demo shorthand.)
# Better demo: open in editor and narrate the edit.

git add README.md
git commit                           # default merge message
git log --oneline --graph --decorate --all

# --- Bonus: abort ---
git switch -c feature/oops
echo "broken" > README.md
git add README.md && git commit -m "feat: break the world"
git switch main
git merge feature/oops               # conflict again
git merge --abort                    # narrate "clean slate"
git status
```

> 💡 In a live class, open the conflicting file in VS Code and *click through* the built-in Accept buttons. Walk through what each button does to the text.

## 11. Anti-patterns

- **Committing the conflict markers.** They compile fine in Markdown. They don't in code. Either way, they're garbage in history.
- **`git add .` mid-conflict without reading the file.** You might mark it resolved with markers still in it.
- **Resolving by always picking one side.** Sometimes correct; often you need *both* changes. Think first.
- **Long-lived branches + infrequent merges.** Conflicts compound. Merge (or rebase) often.

## 12. Recap

- Fast-forward merge: pointer slide, no merge commit.
- Three-way merge: common ancestor + merge commit with two parents.
- `--no-ff` forces a merge commit even when FF is possible.
- Conflicts = Git asking for help. You edit, `git add`, `git commit`.
- `git merge --abort` gets you out of a bad state cleanly.
- Merge often. Keep branches short. Conflicts shrink.

## 13. Further reading

- [Pro Git §3.2 — Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- [Pro Git §3.5 — Advanced Merging](https://git-scm.com/book/en/v2/Git-Branching-Advanced-Merging)
- [`../../../troubleshooting/merge-conflicts.md`](../../../troubleshooting/merge-conflicts.md)
- [GitHub Docs: About merge methods](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges)

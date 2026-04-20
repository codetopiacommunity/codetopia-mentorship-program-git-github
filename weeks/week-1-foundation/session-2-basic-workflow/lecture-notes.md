# Lecture Notes — The Basic Git Workflow

## 1. The 3 Git states

```
   ┌────────────────┐  git add   ┌──────────────┐  git commit   ┌─────────────┐
   │ Working dir    │ ─────────► │ Staging area │ ────────────► │  Repository │
   │ (your edits)   │            │ (proposed    │               │ (history)   │
   │                │            │  next snap.) │               │             │
   └────────────────┘            └──────────────┘               └─────────────┘
```

- **Working directory** — files on disk you can edit.
- **Staging area (index)** — the loading dock; what *will* go in the next commit.
- **Repository** — the saved history of snapshots.

> 💡 The split between staging and committing is the source of Git's power *and* most beginner confusion. Lean into it: you decide *what* makes the cut, not just *when*.

## 2. The 4 most-used commands

```bash
git status                # what state are things in?
git add <file>            # move from working dir → staging
git commit -m "msg"       # move from staging → repo
git log                   # see history
```

`git status` is your friend. Run it between every other command for the first month.

## 3. Initializing a repo

```bash
mkdir my-favorites && cd my-favorites
git init
```

Look inside `.git/` once, just to demystify it:

```bash
ls .git/
```

Don't edit anything in there.

## 4. A first commit

```bash
echo "# My Favorites" > README.md
git status                    # README.md is "untracked"
git add README.md
git status                    # README.md is "to be committed"
git commit -m "feat: add initial README"
git status                    # "nothing to commit, working tree clean"
git log --oneline
```

## 5. Anatomy of a good commit

```
feat: add favorite books section
```

- Type prefix (`feat`, `fix`, `docs`, …)
- Subject under 72 chars
- Imperative mood ("add", not "added")
- No period at the end
- Optional body explaining *why*

See [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md).

## 6. Live demo script (mentor)

```bash
mkdir favorites && cd favorites
git init
echo "# Favorites" > README.md
git add README.md
git commit -m "feat: scaffold favorites README"

echo "## Books" >> README.md
echo "- Pride & Prejudice" >> README.md
git status                  # narrate "modified, not staged"
git diff                    # narrate "the diff lives here"
git add README.md
git commit -m "feat: add favorite books"

# Planned mistake: forget to add
echo "## Movies" >> README.md
git commit -m "feat: add movies"     # nothing to commit
git add README.md
git commit -m "feat: add favorite movies"
git log --oneline
```

## 7. Recap

- Files move through 3 states; commands move them.
- `git add` lets you *curate* the next commit.
- Atomic, well-named commits are a kindness to future-you.

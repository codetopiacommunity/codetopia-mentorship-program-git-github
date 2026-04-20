# Lecture Notes — Working with Files: Diffing & Reading History

## 1. What does "working with files" actually mean?

By now you can record snapshots. But a snapshot is only useful if you can **read it**, **compare it**, and **find things in it**.

Think of your repo as a library. Commits are the books. This session is about learning to:

- Compare two books (`git diff`)
- Scan the card catalog (`git log`)
- Open a single book and read it (`git show`)
- Ask "who wrote this sentence?" (`git blame`)

> 💡 **Mentor framing:** "The git commands in this session don't change anything. They only *look*. You cannot break your repo by running them."

## 2. Three places, three diffs

Remember Week 1's 3-state model? Every diff is a comparison between two of those states.

```
   working dir      staging area          HEAD
        │                │                   │
        │   git diff     │   git diff        │
        ├───────────────►│───staged─────────►│
        │                │                   │
        │           git diff HEAD            │
        ├───────────────────────────────────►│
```

| Command | Compares | Answers |
| ------- | -------- | ------- |
| `git diff` | working dir vs staging | "What have I changed but not staged?" |
| `git diff --staged` | staging vs HEAD | "What will be in my next commit?" |
| `git diff HEAD` | working dir vs HEAD | "What has changed since the last commit — staged or not?" |

Tip: `--cached` is an alias for `--staged`. Same command, two names. Blame history.

## 3. Reading a diff

```diff
diff --git a/notes.md b/notes.md
index 1a2b3c4..5d6e7f8 100644
--- a/notes.md
+++ b/notes.md
@@ -3,6 +3,7 @@
 ## Topics

 - Git
-- GitLab
+- GitHub
+- GitOps

 See also: `./links.md`
```

Line by line:

- `diff --git a/notes.md b/notes.md` — the two "versions" being compared. `a/` = old, `b/` = new.
- `index 1a2b3c4..5d6e7f8 100644` — blob hashes before/after, and file mode.
- `---` and `+++` — old file and new file labels.
- `@@ -3,6 +3,7 @@` — **hunk header**. "Starting at old line 3 for 6 lines; new line 3 for 7 lines."
- Lines starting with ` ` (space) — unchanged context.
- Lines starting with `-` — removed.
- Lines starting with `+` — added.

You will read thousands of these. Learn the shape.

## 4. Comparing across commits

```bash
git diff HEAD~1 HEAD          # what changed in the last commit
git diff HEAD~3 HEAD          # what changed in the last 3 commits
git diff main feature/login   # what's on feature/login that's not on main
git diff abc123 def456 -- README.md   # just one file
```

The `--` separates "revisions" from "paths". Use it when a branch name and a file name might collide.

## 5. `git log` — your history browser

The raw command:

```bash
git log
```

...dumps every commit to a pager. Fine, but noisy. Learn the flags.

### The five flags you will actually use

```bash
git log --oneline                         # compact, one line per commit
git log --oneline --graph --decorate      # ASCII graph with branch names
git log --oneline --all                   # include every branch, not just current
git log --stat                            # show files changed + line counts
git log -p                                # show full diff per commit
git log -n 5                              # last 5 only
```

### Filtering

```bash
git log --author="Ada"                    # commits by Ada
git log --since="2 weeks ago"             # by date
git log --grep="fix"                      # by message
git log -- README.md                      # commits that touched README.md
git log -S"loginUser"                     # commits that added or removed the string
```

The last one (`-S`, the "pickaxe") is magical for debugging: it finds the commit that introduced or deleted a specific piece of code.

### The command to memorize

```bash
git log --oneline --graph --decorate --all -n 20
```

This is the single most useful log invocation. Alias it:

```bash
git config --global alias.lg "log --oneline --graph --decorate --all -n 20"
```

Then just type `git lg`.

## 6. `git show` — open one commit

```bash
git show HEAD                 # the most recent commit
git show HEAD~2               # two commits back
git show abc123               # any commit, by its hash prefix
git show HEAD -- README.md    # just what HEAD did to README.md
```

Output has three parts: metadata (author, date, message), stats, and the diff.

Short hashes (7 chars) are fine — Git expands them as long as they're unique.

## 7. `git blame` — who last touched this line?

```bash
git blame README.md
```

Output:

```
^1a2b3c4 (Ada Lovelace 2026-01-03 10:02:14 +0100  1) # My Recipes
5d6e7f8  (Bob Martin    2026-02-11 14:45:02 +0100  2)
5d6e7f8  (Bob Martin    2026-02-11 14:45:02 +0100  3) A collection of things I cook.
```

Each line: commit hash, author, date, line number, content. Use `-L 10,20 README.md` to blame just a range.

Blame is not for shaming. It's for *asking the right person the right question*.

## 8. Live demo script (mentor)

```bash
# Setup
mkdir study-notes && cd study-notes
git init
echo "# Study Notes" > README.md
git add README.md
git commit -m "feat: initial README"

echo "## Git" >> README.md
echo "- commits are snapshots" >> README.md
git status                              # narrate "modified, not staged"
git diff                                # narrate each part of the diff

git add README.md
git diff                                # narrate "empty — already staged"
git diff --staged                       # narrate "here's the staged diff"

git commit -m "docs: add git section"

echo "## GitHub" >> README.md
echo "- remote hosting" >> README.md
git add README.md
git commit -m "docs: add github section"

# History browsing
git log
# press q to exit pager
git log --oneline
git log --oneline --graph --decorate
git log --stat
git log -p -n 1                         # full diff for the last commit

# Inspecting a specific commit
git show HEAD
git show HEAD~1
git show HEAD~1 -- README.md

# Blame
git blame README.md

# Planned mistake: typo in message
git commit --allow-empty -m "docs: adds placeholder"   # past tense — bad
# We'll fix this in Session 2 with --amend
```

## 9. Recap

- `git diff` compares working dir vs index; `--staged` compares index vs HEAD; `HEAD` compares working dir vs HEAD.
- Unified-diff format has a hunk header (`@@ -a,b +c,d @@`), `-` lines, `+` lines, and ` ` context.
- `git log --oneline --graph --decorate --all` is the "show me my repo" command. Alias it.
- `git show <ref>` opens one commit in full.
- `git blame <file>` tells you *who* and *when*, not *why* — read the commit message for that.

## 10. Further reading

- [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- [Pro Git §2.3 — Viewing Commit History](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

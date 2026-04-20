# Glossary

**Repository (repo)** — a project tracked by Git. Contains all files plus the full history.

**Working directory** — the files you can see and edit on disk.

**Staging area (index)** — the "loading dock" where you queue changes before committing.

**Commit** — a snapshot of the staged changes, with a message and an author.

**Branch** — a movable pointer to a commit. `main` is just a branch.

**HEAD** — a pointer to "where you are" — usually a branch tip.

**Detached HEAD** — HEAD points directly to a commit instead of a branch. Safe; you're "looking around."

**Remote** — a copy of the repo hosted somewhere else (e.g., GitHub). `origin` is the default name.

**Push** — send your local commits to a remote.

**Pull** — fetch + merge from a remote.

**Fetch** — download remote changes without merging.

**Merge** — combine the histories of two branches.

**Conflict** — Git can't auto-merge a region; you decide what stays.

**Rebase** — replay your commits on top of another branch's tip — rewrites history.

**Cherry-pick** — copy a single commit from one branch onto another.

**Fork** — your own server-side copy of someone else's GitHub repo.

**Pull request (PR)** — a GitHub proposal to merge one branch into another, with discussion + review.

**Issue** — a tracked task, bug, or idea on GitHub.

**Tag** — an immutable label on a commit, often used for releases (e.g., `v1.0.0`).

**Reflog** — Git's local log of "where HEAD has been." Often a recovery lifeline.

**Blob / Tree / Commit / Tag** — the four object types in Git's content-addressable database.

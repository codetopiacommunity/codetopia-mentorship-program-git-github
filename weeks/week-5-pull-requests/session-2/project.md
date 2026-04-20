# Project — Week 5 Session 2

> **XP:** 50

## What you'll do

Pair with a peer. Each of you opens a tiny PR; each of you reviews the other's. Practice all three review verdicts and the suggested-changes feature.

## Steps

### Part A — Prepare a PR for your peer to review

1. On your Week 5 Session 1 PR (or a new small PR if that one is already merged), intentionally leave **three reviewable things**:
   - One typo in a word or variable name.
   - One line of commented-out debug code (e.g., `// console.log('TODO remove')`).
   - One short block that could be simpler (e.g., an `if`/`else` returning true/false that could just be `return cond;`).

   Push it.

2. Share the PR URL with your pair partner.

### Part B — Review your peer's PR

On your peer's PR:

1. Open **Files Changed**.
2. Click **Start a review** (not single comments).
3. Leave at least four comments across these categories:
   - One **praise:** — call out something genuinely good.
   - One **suggestion:** using the \`\`\`suggestion code block for a concrete line fix.
   - One **question:** — ask, don't assert.
   - One **nit:** — minor, don't block.
4. Submit the review. Pick the verdict **on purpose**:
   - If everything is minor → **Comment** or **Approve**.
   - If anything is a real blocker → **Request changes**.

### Part C — Address feedback on your own PR

When your reviewer pings you:

1. Open your PR's Files Changed.
2. For each **suggestion** comment, click **Commit suggestion** to accept (or reply with a counter-proposal).
3. For other comments, push a new commit addressing them. Do **not** force-push.
4. Reply to each thread; click **Resolve conversation** on the ones you've addressed.
5. Click the re-request-review icon next to your reviewer's name.

### Part D — Merge

Once re-approved:

1. Pick a merge strategy deliberately. For a tiny PR like this, **Squash and merge** is usually right.
2. Edit the squash commit message to follow conventional format.
3. Merge.
4. Delete the branch using GitHub's button.

## Deliverable

In the **Discussions** tab, post a message containing:

- A link to the PR you **authored**.
- A link to the PR you **reviewed**.
- Screenshots of: (a) a suggested-change comment you wrote, (b) the merge-strategy dropdown open on your own PR.
- A two-sentence answer to: *"When would I pick 'Request changes' over a plain 'Comment'?"*

## Stretch goal (+10 XP)

On your own PR, intentionally get it into a conflict state with `main` (have a partner push a conflicting change to `main` via another PR). Resolve the conflict in the GitHub web UI's conflict editor, then merge. Document the conflict-resolution screen in your discussion post.

## Stuck?

- Lecture notes §3, §4, §6.
- Common issues: [`../common-issues.md`](../common-issues.md)
- Troubleshooting: [`../../../troubleshooting/merge-conflicts.md`](../../../troubleshooting/merge-conflicts.md)
- Post in **Discussions → Q&A** with the screenshot of the GitHub screen you're stuck on.

# Solutions — Week 5 Session 2

> **Mentor only.** Don't peek until you've tried.

## Model review comments

For a typo:

> `nit:` typo — `recieved` → `received`. Pushing this as a suggestion.
>
> ```suggestion
> const received = await fetchOrders();
> ```

For commented-out debug code:

> `suggestion:` looks like leftover debug — can we drop this line before merge? Not a blocker if you want to keep it behind a debug flag.

For the `if/else` returning booleans:

> `nit:` this could collapse to a single `return isActive && !isExpired;`. Totally optional — readability call, happy either way.

For something praiseworthy:

> `praise:` nice extraction of `formatCurrency` into its own helper — makes the call sites much easier to read.

## Model verdict reasoning

| Situation | Verdict | Why |
| --------- | ------- | --- |
| Only nits and a praise, no bugs | **Comment** or **Approve** | No blockers |
| Debug code left in *and* a real bug | **Request changes** | Must fix before merge |
| Structural concerns but you're not the area owner | **Comment** | Flag it; let the owner decide |
| You read every line and would ship it yourself | **Approve** | That's what approval is for |

## Model answer — "Request changes" vs "Comment"

> "I pick **Request changes** when something is a real blocker — a bug, a security issue, a broken contract — something that *must* change before the PR merges. I pick **Comment** when I have opinions or questions but wouldn't block the merge over them, especially for stylistic nits."

## What a good suggested-change screenshot shows

- The diff view with a review comment box anchored to a specific line.
- A triple-backtick `suggestion` block containing the replacement text.
- GitHub's preview rendering a proposed diff with red/green bars.
- A **Commit suggestion** button visible.

## Merge-strategy screenshot expectations

The dropdown shows three options. The mentee should pick deliberately and explain in their deliverable why they picked it — not just "it was default."

For tiny PRs with review-fix commits, squash is almost always right.

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| Review comments sent individually, spamming author | Clicked "Add single comment" instead of "Start a review" | Next time, start a review and batch |
| Suggestion block won't apply | Branch moved since the suggestion was written | Reviewer re-suggests on the latest commit |
| Author force-pushed and reviewer comments vanished | Rewriting history during active review | In-session rule: additional commits only until re-approval |
| Mentee clicks "Request changes" for a nit | Misread the verdict weight | Coach: Request changes = blocker only |
| Both parties "approve" their own PR by mistake | Self-approval doesn't count on most repos | Confirm another human approved |

## Stretch — conflict resolution screen

The GitHub web conflict editor shows:

- A textarea per conflicted file.
- `<<<<<<<`, `=======`, `>>>>>>>` markers.
- A **Mark as resolved** button per file, then **Commit merge**.

Confirm the mentee kept intended lines from both sides, removed the markers, and committed with a conventional merge message.

# Lecture Notes — Code Review

## 1. Why review at all?

Review is not gate-keeping. It's:

- **Shared understanding** — two people now know the code.
- **Quality** — a second pair of eyes catches bugs the author can't see.
- **Mentorship** — juniors learn the codebase, seniors learn each other's domain.
- **Memory** — the PR conversation is a durable "why did we do this?" record.

Treat code review as a conversation with a future teammate, not a test you're grading.

> Mentor framing: "Review the code, not the coder."

## 2. The three review verdicts

On GitHub, when you finish a review you pick one of three:

| | Effect | Use when |
| --- | --- | --- |
| **Comment** | No verdict. Just questions or thoughts. | You have notes but no opinion yet; you're not the decisive reviewer. |
| **Approve** | Green check. Ready to merge (subject to other reviewers). | You read the whole diff and you'd ship it. |
| **Request changes** | Red X. Blocks merge until you re-review. | Something must change before merge. |

**Don't** click "Request changes" for stylistic preferences — use regular comments. Reserve **Request changes** for real blockers: bugs, security issues, broken tests, API contract violations.

## 3. What a good review comment looks like

**Bad:**

> This is wrong.

**Bad:**

> Why did you do it like this?

**Good:**

> This mutates `users` in-place, which will surprise the caller. Could we return a new array with `.map()` instead? Happy to pair if that's more disruptive than it looks.

Good review comments have:

- A **noun** — what line / thing you're talking about.
- A **reason** — why it matters.
- A **suggestion** — what "fixed" looks like.
- A **tone** — not a command; an invitation.

### Conventional review prefixes (optional but useful)

Some teams prefix comments to signal intent:

- `nit:` — stylistic preference, don't block merge
- `question:` — I don't understand this yet
- `suggestion:` — something you should consider
- `blocker:` — must change before merge
- `praise:` — genuinely good, call it out

Example:

> `nit:` could we alphabetize these imports? Optional — approving either way.

## 4. Suggested changes — the superpower

Inside a review comment, you can propose an **exact replacement** for the line(s):

<pre><code>```suggestion
const users = sortBy(rawUsers, 'createdAt');
```</code></pre>

The author then clicks **Commit suggestion** and your change lands as a commit authored by them with you as co-author. No back-and-forth rewrites.

Use suggestions for:

- Typos.
- One- or two-line fixes.
- Concrete rewrites of small blocks.

Don't use them for structural changes — describe those in prose instead.

## 5. Requesting specific line ranges

On the Files Changed tab:

1. Hover the gutter to reveal the **+** button.
2. Click to start a comment.
3. Click and drag across multiple lines to span a range.
4. Pick **Start a review** (batch your comments) rather than **Add single comment** (sends each one individually, spamming the author's inbox).

Submit the whole batch at the end with a review verdict.

## 6. Addressing feedback as the author

When a reviewer leaves comments, **don't force-push immediately**. Force-push during review rewrites history the review anchors to, and GitHub will lose the line-by-line context.

Instead:

```bash
# make the change
git add path/to/file
git commit -m "fix: address review — use .map instead of mutation"
git push
```

New commits show up on the PR, *preserving* all review threads.

Once the reviewer re-approves, **then** you can squash or rebase — or let the merge strategy do it for you (see §8).

### Marking threads resolved

After you address a comment:

- Author clicks **Resolve conversation** on the thread once fixed.
- Reviewer can re-open if not satisfied.

Resolved threads collapse. The PR becomes legible again.

## 7. Re-requesting review

After you push fixes, ask for another pass. On the PR sidebar → Reviewers → click the circular-arrow icon next to the reviewer's name. This sends a fresh notification without being noisy.

## 8. Merge strategies

GitHub offers three merge buttons (a repo's admin controls which are enabled). Pick on purpose.

### Merge commit (default)

```
main:    A───B───────────M
                \       /
feat:            C─D─E
```

- Keeps the full feature branch history.
- Adds a merge commit `M` with two parents.
- Pro: complete, auditable history.
- Con: `main` log is noisy when features have many commits.

Command-line equivalent: `git merge --no-ff feat`.

### Squash and merge

```
main:    A───B───S
```

- Flattens `C`, `D`, `E` into a single commit `S` on `main`.
- Pro: `main` reads as one commit per feature — clean.
- Con: individual work-in-progress commits are lost.

**Recommended default for most teams.** Use when the feature branch had a lot of "fix typo" / "address review" commits you don't need in `main`'s history.

### Rebase and merge

```
main:    A───B───C'───D'───E'
```

- Replays `C`, `D`, `E` onto `main` as `C'`, `D'`, `E'` (new SHAs).
- Pro: linear history, all individual commits preserved.
- Con: new SHAs break links to the original commits; easy to mess up with lots of conflicts.

Use when each commit is meaningful on its own and you want a linear log.

### Which to pick?

| Situation | Strategy |
| --------- | -------- |
| PR is one logical change with messy WIP commits | **Squash** |
| PR is a true feature branch with meaningful commits | **Merge commit** |
| Team insists on linear history | **Rebase** |
| You're not sure | **Squash** |

## 9. The merge button is a trigger, not a reversal

Once you click Merge, the change is in `main`. Reverting is possible (`git revert <merge-sha>`), but that adds a *new* commit — it doesn't erase the original.

Before clicking:

- [ ] At least one approval (team rule).
- [ ] CI is green.
- [ ] You've read the final diff one more time.
- [ ] Base branch is the one you actually want (not a release branch by accident).

## 10. Live demo script (mentor)

Pre-open a throwaway PR in a scratch repo with a small bug (e.g., a hard-coded value that should be a constant, a typo, a loop that mutates).

```
Mentor A (as reviewer):
  - Open Files Changed tab
  - Click +, leave a nit: comment on the typo
  - Drag-select the mutation block, leave a blocker with a ```suggestion``` block
  - Click "Start a review" (not "Add single comment")
  - Submit as "Request changes"

Mentor B (as author):
  - Click "Commit suggestion" on the suggested change — see the new commit
  - Push an additional fix for the nit
  - Click "Re-request review" on the reviewer's avatar

Mentor A (back as reviewer):
  - Re-review, click Approve
  - Show the three merge strategies dropdown
  - Pick "Squash and merge", edit the squash commit message, merge
  - Show main's log — single clean commit
```

Narrate each click. Let them see the noise settle.

## 11. Kindness rules of thumb

- Open with something true and positive. ("Neat approach on the caching layer.")
- Ask questions before asserting ("Does this handle the empty-array case?" beats "This is broken for empty arrays.").
- Flag your confidence level — "Not sure, but..." is okay.
- If you find yourself writing more than 3 blocker comments, consider a call instead of a review.
- End with a clear next step: "Once the mutation is addressed, I'll re-approve."

## 12. Recap

- Three verdicts: Comment, Approve, Request changes. Use them deliberately.
- Suggested changes turn small fixes into one-click merges.
- Address feedback with new commits, not force-push, during active review.
- Pick a merge strategy on purpose — default to squash if unsure.
- Review the code, not the coder.

## Cross-references

- PR template: [`../../../templates/pr-template.md`](../../../templates/pr-template.md)
- Commit message guide: [`../../../templates/commit-message-guide.md`](../../../templates/commit-message-guide.md)
- Contributing guide: [`../../../CONTRIBUTING.md`](../../../CONTRIBUTING.md)
- Code of Conduct: [`../../../CODE_OF_CONDUCT.md`](../../../CODE_OF_CONDUCT.md)

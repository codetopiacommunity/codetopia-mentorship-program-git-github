# Lecture Notes — Making a Great PR

## 1. The full loop, at a glance

```
fork -> clone -> branch -> change -> commit -> push -> open PR -> review -> merge
```

Every step has etiquette and technique. We'll go through each.

## 2. Fork and clone

On GitHub, click **Fork** on the target repo. Then locally:

```bash
git clone git@github.com:<your-handle>/<repo>.git
cd <repo>
git remote add upstream git@github.com:<original-owner>/<repo>.git
git remote -v
```

You should now see:

```
origin    git@github.com:you/<repo>.git (fetch)
origin    git@github.com:you/<repo>.git (push)
upstream  git@github.com:original/<repo>.git (fetch)
upstream  git@github.com:original/<repo>.git (push)
```

> 💡 **Mentor framing:** `origin` is your fork. `upstream` is the real project. You push to `origin`; you pull from `upstream`.

### Keep your fork in sync

Before starting a new branch:

```bash
git fetch upstream
git switch main
git merge upstream/main      # or: git rebase upstream/main
git push origin main         # sync your fork on GitHub too
```

## 3. Branch and change

```bash
git switch -c fix/typo-in-readme
```

Branch naming conventions vary. Common ones:

- `fix/<short-description>`
- `feat/<short-description>`
- `docs/<short-description>`
- `<your-handle>/<short-description>`

Read the target's CONTRIBUTING.md for specifics.

### Scope: keep it tight

**One PR = one logical change.** The smaller the PR, the faster it merges. If you notice a second bug while fixing the first, open a second PR. Don't bundle.

## 4. Commit

Follow the project's commit conventions. Most modern projects accept or require Conventional Commits:

```text
fix(auth): reject empty passwords in login handler

The handler was accepting empty strings as valid passwords,
allowing accidental bypass. Adds a guard and a regression test.

Closes #1234
```

Some projects require a [DCO sign-off](https://developercertificate.org/):

```bash
git commit -s -m "fix(auth): reject empty passwords"
```

The `-s` adds `Signed-off-by: Your Name <your@email>` to the message.

## 5. Push

```bash
git push -u origin fix/typo-in-readme
```

The `-u` sets upstream so future `git push` and `git pull` on this branch work without arguments.

## 6. Open the PR

On GitHub, click **Compare & pull request**. Or use `gh`:

```bash
gh pr create --web
```

### The anatomy of a PR description maintainers love

Answer four questions, in this order:

1. **What** does this change?
2. **Why** does it need to change?
3. **How** did you change it (high level, not a line-by-line)?
4. **How did you test** it?

Plus:

- Link to the issue (`Closes #1234` auto-closes it on merge).
- Screenshots for UI changes (before/after).
- A checklist for any project-mandated items.

### Template worth stealing

```markdown
## What

Fixes the broken link to the setup guide in `docs/getting-started.md`.

## Why

The link `docs/setup.md` was renamed to `docs/setup-guide.md` in #1100,
but `getting-started.md` wasn't updated. Users following the guide 404.

## How

Updated the anchor target and re-ran the docs build to verify.

## Testing

- `pnpm docs:build` succeeds.
- `pnpm docs:linkcheck` passes (previously flagged the broken link).
- Manual click-through on the rendered page.

Closes #1234
```

### What NOT to write

- "Fixes bug" (which bug? what was the root cause?)
- "See title" (the description is where you *expand* on the title.)
- A wall of "I also fixed while I was at it…" — those belong in separate PRs.

## 7. Respond to review

This is where most first-timers fall apart. A few rules:

1. **Respond to every comment**, even with a simple "Done" or emoji.
2. **If you disagree, explain — once — calmly.**

   > "I considered that approach, but I went with X because of Y. Happy to switch if you'd prefer — let me know."

3. **Don't re-force-push after each small change.** Push new commits; the project will usually squash on merge. Force-push only when asked or when rebasing on fresh `main`.
4. **Thank the reviewer.** They're volunteering their time.

### When feedback stings

It will, sometimes. Take a walk, draft a response, save it for an hour, re-read, then send. Never send the first draft of a response you wrote while upset.

> 💡 **Mentor framing:** "Review comments are about the code, not about you. Even when they feel like they're about you — they're not."

## 8. The social contract

Unwritten, but real:

- **Their project, their rules.** You can disagree. They decide.
- **Maintainers are volunteers**, even at big companies. They can be slow. That's OK.
- **A "close without merge" is not a personal attack.** Ask politely what you could do differently. Move on.
- **A "please change X" is not an insult.** It's how code review works everywhere.
- **Say thank you when it merges.** A two-word comment means a lot.
- **If they ignore you for 3 weeks, then ping once. After another 2 weeks, move on.**

## 9. Live demo script (mentor)

Use a sandbox repo you control so you can actually merge at the end.

```bash
# 1. Fork + clone
gh repo fork <mentor-demo-repo> --clone
cd <repo>
git remote add upstream <original-url>

# 2. Sync
git fetch upstream
git switch main
git merge upstream/main

# 3. Branch
git switch -c fix/typo-demo

# 4. Change
sed -i '' 's/teh/the/' README.md
git diff

# 5. Commit
git add README.md
git commit -m "docs: fix typo in README"

# 6. Push
git push -u origin fix/typo-demo

# 7. PR
gh pr create --fill --web
# Paste the 4-section template, narrate each section

# 8. Respond to a "nit" comment (planted by mentor)
# Show the amend, push, reply flow
```

## 10. A syncing gotcha

Your PR has been open for a week; upstream has moved on.

```bash
git fetch upstream
git rebase upstream/main
# fix conflicts if any
git push --force-with-lease
```

Some projects prefer merge over rebase:

```bash
git fetch upstream
git merge upstream/main
git push
```

Default to what CONTRIBUTING.md says.

## 11. Recap

- Fork sets up `origin`; add `upstream` to track the real project.
- Small PRs merge fast. Big PRs rot.
- The four questions: what / why / how / how-tested.
- Respond to every comment. Thank reviewers.
- The project is theirs. You're a guest. Be a good one.

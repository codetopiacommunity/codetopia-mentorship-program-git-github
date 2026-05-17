# Week 5 Capstone — Pre-submission Checklist

Run this list before opening your PR and before submitting your review.

## As author — before opening the PR

### Local state

- [ ] `git status` returns "nothing to commit, working tree clean"
- [ ] On a feature branch, **not** `main` (`git branch --show-current`)
- [ ] `git log --oneline` shows at least 3 conventional commits
- [ ] Every commit message starts with a type, imperative mood, no trailing period

### Remotes

- [ ] `git remote -v` shows `origin` (your fork) **and** `upstream` (this repo)
- [ ] Your feature branch is pushed to `origin`

### Content

- [ ] `projects-showcase/week-5-projects/<your-handle>/README.md` exists
- [ ] That README describes your Week 4 project, links to the GitHub repo, and includes at least one screenshot
- [ ] `screenshots/` folder present with at least 2 named screenshots (`01-...`, `02-...`)
- [ ] Best screenshot shared in the WhatsApp group
- [ ] No absolute local paths or broken image links
- [ ] No accidental unrelated files (package-lock.json, .DS_Store, IDE configs)

### PR form

- [ ] Base is `<upstream-org>/git-github-mentorship : main`
- [ ] Compare is `<your-handle>/git-github-mentorship : <your-branch>`
- [ ] PR title reads like a conventional commit
- [ ] PR description has Summary, Why, What changed, How to test — all filled in
- [ ] No template HTML comments (`<!-- ... -->`) left behind
- [ ] Mentor requested in the Reviewers sidebar

## As reviewer — before submitting your review

### Preparation

- [ ] You opened the PR's **Files Changed** tab
- [ ] You clicked **Start a review** (not "Add single comment")
- [ ] You read the whole diff before commenting

### Comments

- [ ] At least 3 substantive comments, each anchored to a specific line or range
- [ ] At least one uses a \`\`\`suggestion block
- [ ] At least one is a **praise:** or **question:** prefixed comment
- [ ] Tone is kind and specific — no blaming language (per [`../../../CODE_OF_CONDUCT.md`](../../../CODE_OF_CONDUCT.md))

### Verdict

- [ ] You chose an explicit verdict: Comment / Approve / Request changes
- [ ] If Request changes, your top-line review message names the blockers
- [ ] If Approve, you genuinely would ship this

## Before clicking Merge (mentors / mentee with merge rights)

- [ ] At least one approval
- [ ] All conversations resolved
- [ ] Base branch is correct
- [ ] Merge strategy picked on purpose (squash is a safe default here)
- [ ] Squash commit message edited to conventional format

## Final sanity

- [ ] You forked — not cloned — this repo
- [ ] You tagged your mentor
- [ ] You haven't force-pushed during active review

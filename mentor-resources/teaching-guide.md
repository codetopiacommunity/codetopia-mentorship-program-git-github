# Mentor Teaching Guide

> Your operating manual for running the program. Read this once before Week 1.

## The Prime Directive

**Mentees should leave each session feeling more capable than when they arrived.** Everything else — XP, rubrics, pacing — is in service of that.

## Read this before Week 1

[`project-format-guide.md`](project-format-guide.md) — the project-format arc across all 8 weeks. **The lesson is the Git, not the build.** Default to markdown; let complexity grow toward Week 8. Skipping this guide is the #1 way to lose the plot in Weeks 2–3.

## Session Anatomy (90 min)

| Time | Block | What happens |
| ---- | ----- | ------------ |
| 0–10 | Warm-up | "What did you push this week?" — celebrate, recap |
| 10–25 | Concept | Whiteboard / slides — minimal talking head |
| 25–55 | Live demo | You drive, narrate every keystroke |
| 55–80 | Pair work | They try it; you circulate |
| 80–90 | Recap + project handout | What we did, what's due, what's coming |

## Live Demo Rules

1. **Type slowly.** Mentees read, then catch up.
2. **Read the error out loud** before fixing it.
3. **Make a "planned mistake" once per session** — model recovery.
4. **Always run `git status` between commands.** It's the most underused command.

## Common Student Mistakes (and how to head them off)

- **Committing without staging** → demo `git diff --staged` early.
- **Force-pushing to main** → set up branch protection in Week 4.
- **Pasting credentials into commits** → make `.gitignore` a Week 1 ritual.
- **Detached HEAD panic** → defuse it: "you're just looking around."
- **Conflict avoidance** → engineer a merge conflict in Week 3 on purpose.

## Giving Feedback

- ✅ **Specific:** "Your commit message tells me *why* — that's the goal."
- ✅ **Actionable:** "Try splitting this into two commits."
- ✅ **Growth-focused:** "Next, see if you can do this without looking at the cheatsheet."
- ❌ Avoid: "Looks good!" alone — it doesn't teach.

## Red Flags 🚩

- Mentee skips projects, only attends.
- Work consistently incomplete or last-minute.
- Stops asking questions (often = silently lost).
- Visible anxiety about "breaking" Git.

For each flag, schedule a 1:1 the same week.

## Pacing

See [`pacing-guide.md`](pacing-guide.md). Default to **2 sessions/week** unless the cohort tells you otherwise.

## Grading Capstones

Use the rubric in [`rubrics/`](rubrics/). Aim for ≤ 48-hour turnaround on feedback — momentum matters more than perfection.

# Solutions — Week 2 · Session 1

> **Mentor only.** Don't peek until you've tried.

## Expected `git log --oneline` shape

Something like:

```
c9f1aa2 fix: correct typo in Markdown section
a83b01f docs: add resources section
72e4d90 docs: add markdown section
4b0c55e docs: add github section
1f2a8c3 docs: add git section
90deadb feat: initial README
```

Exact hashes and ordering will vary. Look for:

- 6+ commits
- All with conventional prefixes (`feat:`, `docs:`, `fix:`, …)
- At least one `fix:` commit
- Imperative mood ("add", not "added")

## Model answer for the diff prompt

> "`git diff` shows changes I've made but haven't staged yet — the stuff I'm still working on. `git diff --staged` shows changes I've already staged — what will actually go into my next commit. Together they answer 'what am I still deciding?' and 'what have I committed to?'."

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| Pager hijacks the terminal | `less` is open | Press `q` |
| `tour.md` is empty | Redirect appended nothing | Use `git log --oneline > tour.md` explicitly |
| `git show HEAD~2` errors with "unknown revision" | Fewer than 3 commits | Make more commits first |
| `git blame` shows `^xxxxx` for every line | Only one commit touches the file | That's expected |

## Grading rubric (if you want a quick score)

- 6+ commits: 30
- All conventional: 20
- `tour.md` committed and complete: 30
- Diff paragraph clear: 20

Pass: 70.

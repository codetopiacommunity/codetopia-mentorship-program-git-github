# Solutions — Session 1

> **Mentor only.** Don't peek until you've tried.

## Expected `git --version` output

Something like:

```
git version 2.45.2
```

Anything ≥ 2.30 is fine.

## Expected `git config --list` excerpt

```
user.name=Ada Lovelace
user.email=ada@example.com
init.defaultbranch=main
pull.rebase=false
```

## Common gotchas

| Symptom | Likely cause | Fix |
| ------- | ----------- | --- |
| `git: command not found` | Git not installed or terminal not restarted | Restart terminal; reinstall |
| `xcrun: error: invalid active developer path` | Xcode CLI tools missing | `xcode-select --install` |
| `fatal: not a git repository` | Not in the folder you `git init`-ed | `cd` to the right folder |

## "Git vs GitHub" — model answer

> "Git is the version-control program that runs on my computer. GitHub is a website that hosts Git repositories and adds collaboration features like pull requests."

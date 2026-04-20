# Lecture Notes — Introduction & Installation

## 1. What is version control?

Imagine writing an essay where every save kept the previous version, *forever*, and you could compare any two saves side-by-side. That's version control.

Git is the most widely used version control system. It's a *tool that tracks changes to files over time*.

### Why we need it

- **Undo:** revert any change, ever.
- **Memory:** see who changed what and why.
- **Parallel work:** two people edit the same project without overwriting each other.
- **Experimentation:** try a risky change in a branch; throw it away if it doesn't work.

> 💡 **Mentor framing:** "Git is just a tool. It's not magic. It's not even smart. It's a careful filing clerk."

## 2. Git vs GitHub

- **Git** — the tool, runs locally.
- **GitHub** — a website that hosts Git repositories and adds a UI for collaboration.

You can use Git without GitHub. You cannot use GitHub without Git.

## 3. Installing Git

### macOS

Easiest:

```bash
xcode-select --install
```

Then check:

```bash
git --version
```

If you get `xcrun: error`, run `xcode-select --install` again and accept the popup.

### Windows

Download [Git for Windows](https://gitforwindows.org/). Accept defaults. Open **Git Bash** (not CMD).

If Windows says `'git' is not recognized as an internal or external command`, **close and reopen** the terminal.

### Linux (Debian/Ubuntu)

```bash
sudo apt update && sudo apt install -y git
git --version
```

## 4. Configure your identity

Git wants to know who's making changes. Run these once per machine:

```bash
git config --global user.name  "Ada Lovelace"
git config --global user.email "ada@example.com"
git config --global init.defaultBranch main
git config --global pull.rebase false
```

Verify:

```bash
git config --list
```

> 💡 The `--global` flag means "for every repo on this machine." You can override per-repo by dropping `--global`.

## 5. The big picture

Git stores **snapshots** of your project. Each snapshot is called a **commit**. A repository is just a folder with a hidden `.git/` directory holding all the snapshots.

That's the whole model. Everything else — branches, remotes, merges — is built on top of it.

## 6. Live demo script (mentor)

```bash
mkdir hello-git && cd hello-git
git init                  # narrate: "this creates the .git folder"
ls -la                    # show .git/ exists
echo "hello" > hi.txt
git status                # narrate: "untracked"
git add hi.txt
git status                # narrate: "staged"
git commit -m "feat: add hi.txt"
git status                # narrate: "clean"
git log
```

## 7. Recap

- Git tracks changes to files.
- Git ≠ GitHub. Git is local; GitHub is a hosting service.
- You configure your identity once, globally.
- A repo is a folder with a `.git/` subfolder.

# Lecture Notes — GitHub Remotes

## 1. What is a "remote"?

A **remote** is a nickname for a URL that points at another copy of your repository — usually one hosted on GitHub.

By default, the first remote you add is called `origin`. That name is a convention, not a rule. It's just a label:

```
origin  →  git@github.com:ada/hello-remote.git
```

When you `git push origin main`, Git translates that to "send my local `main` branch to that URL."

> Mentor framing: "A remote is a bookmark to another copy of the repo. Git keeps as many bookmarks as you like."

## 2. What GitHub actually is

- A web UI for browsing Git repositories.
- A hosting service for the `.git` data.
- A pile of collaboration features layered on top (issues, PRs, Actions, wikis).

It is **not** Git. You can swap GitHub for GitLab, Bitbucket, Gitea, or a server you control and every command in this lecture still works.

## 3. Creating a repo on GitHub

1. Go to [https://github.com/new](https://github.com/new).
2. Pick a **Repository name** — kebab-case, no spaces (e.g. `hello-remote`).
3. Choose **Public** or **Private**. Either is fine for this course.
4. **Leave** the "Initialize this repository with a README / .gitignore / license" checkboxes **off**. We already have a local repo — checking these would create a conflicting history.
5. Click **Create repository**.

GitHub now shows you a "Quick setup" page with two URLs — an **HTTPS** one and an **SSH** one. Copy one; we'll use it in a minute.

## 4. Connecting local to remote

Inside an existing local repo:

```bash
git remote -v
# (no output — no remotes yet)

git remote add origin git@github.com:ada/hello-remote.git

git remote -v
# origin  git@github.com:ada/hello-remote.git (fetch)
# origin  git@github.com:ada/hello-remote.git (push)
```

Two lines, one remote. Git tracks `fetch` and `push` URLs separately in case you ever want to read from one place and write to another. For now they'll always match.

### Renaming the default branch

If your local default branch is `master` instead of `main`:

```bash
git branch -M main
```

This renames the current branch to `main`. GitHub's default is `main`, so matching it avoids weird "default branch mismatch" banners.

## 5. Your first push

```bash
git push -u origin main
```

Expected output (abbreviated):

```
Enumerating objects: 5, done.
...
To github.com:ada/hello-remote.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

The important bits:

- `[new branch] main -> main` — GitHub didn't have `main`; now it does.
- `set up to track 'origin/main'` — that's what `-u` (short for `--set-upstream`) does.

After this one-time push, you can just run `git push` and `git pull` with no arguments — Git knows where `main` lives.

> Run `git push -u` exactly once per branch. Subsequent pushes are just `git push`.

## 6. SSH vs HTTPS — pick one

GitHub accepts two authentication methods. You only need one.

| | **SSH** | **HTTPS + PAT** |
| --- | --- | --- |
| URL looks like | `git@github.com:user/repo.git` | `https://github.com/user/repo.git` |
| Auth mechanism | Key pair on your machine | Personal Access Token stored in credential helper |
| One-time setup | Generate key, paste public key into GitHub | Create PAT, store with credential helper |
| Works through corporate proxies | Sometimes blocked (port 22) | Almost always works (port 443) |
| Ongoing friction | None once set up | Token expires; re-auth occasionally |

Recommendation for this program: **SSH**. Once it's set up you forget it exists. But HTTPS + PAT is fine — your call.

## 7. Generating an SSH key

```bash
ssh-keygen -t ed25519 -C "ada@example.com"
```

Prompts:

```
Enter file in which to save the key (/Users/ada/.ssh/id_ed25519):  [Enter]
Enter passphrase (empty for no passphrase):                        [Enter or type one]
Enter same passphrase again:                                       [Enter or retype]
```

You now have two files:

- `~/.ssh/id_ed25519`      — **private** key. Never share. Never commit.
- `~/.ssh/id_ed25519.pub`  — **public** key. Safe to paste anywhere.

Start the agent and add the key:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

Copy the public key:

```bash
# macOS
pbcopy < ~/.ssh/id_ed25519.pub

# Linux
xclip -sel clip < ~/.ssh/id_ed25519.pub

# Anywhere
cat ~/.ssh/id_ed25519.pub
```

In GitHub: **Settings → SSH and GPG keys → New SSH key**. Paste. Save.

Test:

```bash
ssh -T git@github.com
# Hi ada! You've successfully authenticated, but GitHub does not provide shell access.
```

That "does not provide shell access" message looks scary but is the success state.

## 8. HTTPS + Personal Access Token (alternative)

1. GitHub → **Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token**.
2. Scope: `repo` (for private repos) or leave minimal for public ones.
3. Copy the token — you see it exactly once.
4. Tell Git to remember it:

   ```bash
   # macOS
   git config --global credential.helper osxkeychain

   # Windows (installed with Git for Windows)
   git config --global credential.helper manager

   # Linux
   git config --global credential.helper "cache --timeout=86400"
   ```

5. Next push prompts for username + password. Paste the token as the password. The helper caches it.

## 9. Switching auth later

You can flip a remote from HTTPS to SSH (or vice versa) without re-cloning:

```bash
git remote set-url origin git@github.com:ada/hello-remote.git
git remote -v     # confirm
```

## 10. Live demo script (mentor)

```bash
# Fresh local repo
mkdir hello-remote && cd hello-remote
git init
echo "# hello-remote" > README.md
git add README.md
git commit -m "feat: add initial README"

# Show no remotes
git remote -v

# (Switch to browser — create repo on github.com, leave all init options OFF)

# Back in the terminal
git remote add origin git@github.com:ada/hello-remote.git
git remote -v

git branch -M main
git push -u origin main

# Show GitHub refreshed — the README is there

# Demonstrate set-url
git remote set-url origin https://github.com/ada/hello-remote.git
git remote -v
git remote set-url origin git@github.com:ada/hello-remote.git
```

If time permits, generate an SSH key live (use a throwaway email/comment) and show the `ssh -T` handshake.

## 11. Gotchas worth calling out

- **Don't check "Add a README" on GitHub** when you already have a local repo — you'll get the dreaded `refusing to merge unrelated histories` later.
- **The `.pub` file is the one you paste** — never the private key.
- **`git push` without `-u` on a new branch** will fail with a helpful message; just run the command it suggests.
- **`origin` is just a name** — you can add more remotes (`upstream`, `deploy`, a co-worker's fork) and push to them independently.

## 12. Recap

- A remote = a named URL for another copy of the repo.
- `git remote add origin <url>` wires them up; `git push -u origin main` syncs and sets tracking.
- SSH (keys) or HTTPS (PAT) — both work; pick one.
- `origin` is convention, not magic. You can rename it, switch its URL, or add siblings.

## Cross-references

- Troubleshooting: [`../../../troubleshooting/permission-denied-publickey.md`](../../../troubleshooting/permission-denied-publickey.md)
- Cheatsheet: [`../../../resources/git-cheatsheet.md`](../../../resources/git-cheatsheet.md)
- Glossary: [`../../../resources/glossary.md`](../../../resources/glossary.md)

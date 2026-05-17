# Project — Week 4 Session 1

> **XP:** 50

## What you'll do

Connect a local repo to a brand-new GitHub repository and push it. Get SSH authentication working end-to-end (or HTTPS + PAT if you prefer).

## Steps

1. Create a new local repo and seed it with one commit:

   ```bash
   mkdir hello-remote && cd hello-remote
   git init
   echo "# hello-remote" > README.md
   git add README.md
   git commit -m "feat: add initial README"
   git branch -M main
   ```

2. On github.com, create an empty repo called `hello-remote`. **Do not** initialize it with a README, `.gitignore`, or license.

3. Copy the SSH URL (starts with `git@github.com:`).

4. Set up authentication (pick one):

   **SSH route** (recommended):
   ```bash
   ssh-keygen -t ed25519 -C "<your email>"
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   cat ~/.ssh/id_ed25519.pub    # copy output
   ```
   Paste the public key into GitHub → **Settings → SSH and GPG keys → New SSH key**, then:
   ```bash
   ssh -T git@github.com
   ```

   **HTTPS route**: create a Personal Access Token and enable a credential helper (see lecture notes §8).

5. Connect and push:

   ```bash
   git remote add origin git@github.com:<your-handle>/hello-remote.git
   git remote -v
   git push -u origin main
   ```

6. Refresh the GitHub page — your README should be there.

## Deliverable

Submit your work as follows:

1. **In your project's `screenshots/` folder** (the submission of record): add at least one screenshot — typically `git remote -v`, the `ssh -T git@github.com` greeting, and the GitHub repo page with your README rendered. Name them `01-git-remote.png`, `02-ssh-greeting.png`, `03-github-repo.png`, etc.
2. **In the WhatsApp group** (informal share): drop a copy of your best screenshot so the cohort can cheer you on.
3. **In the Discussions tab** (additional channel): post the output of `git remote -v`, the URL of your new GitHub repo, and a one-sentence answer to: *"What does the `-u` flag in `git push -u origin main` do?"*

See [CONTRIBUTING.md → Screenshot conventions](../../../CONTRIBUTING.md#screenshot-conventions).

## Stretch goal (+10 XP)

Add a second remote named `backup` that points to a second empty GitHub repo, and push `main` to both:

```bash
git remote add backup git@github.com:<your-handle>/hello-remote-backup.git
git push backup main
git remote -v
```

## Stuck?

- Lecture notes §7 and §8.
- Troubleshooting: [`../../../troubleshooting/permission-denied-publickey.md`](../../../troubleshooting/permission-denied-publickey.md)
- Common issues: [`../common-issues.md`](../common-issues.md)
- Post in **Discussions → Q&A** with your exact command and the exact error message.

# "Permission denied (publickey)"

## Problem

GitHub doesn't recognize your SSH key — either none exists or you haven't added it to your account.

## Diagnose

```bash
ssh -T git@github.com
```

Expected (success):

```
Hi <username>! You've successfully authenticated...
```

## Fix

1. Generate a key if you don't have one:

   ```bash
   ssh-keygen -t ed25519 -C "your.email@example.com"
   ```

   Press Enter through the prompts (or set a passphrase).

2. Start the SSH agent and add the key:

   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   ```

3. Copy the **public** key:

   ```bash
   # macOS
   pbcopy < ~/.ssh/id_ed25519.pub
   # Linux (with xclip)
   xclip -sel clip < ~/.ssh/id_ed25519.pub
   # Or just print and copy by hand:
   cat ~/.ssh/id_ed25519.pub
   ```

4. Paste it in GitHub → **Settings → SSH and GPG keys → New SSH key**.

5. Re-test: `ssh -T git@github.com`.

## Alternative

If SSH still fights you, switch your remote to HTTPS + a Personal Access Token:

```bash
git remote set-url origin https://github.com/<user>/<repo>.git
```

GitHub will prompt for your username and a PAT (use one in place of your password).

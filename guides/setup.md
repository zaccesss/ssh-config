# Setup

## 1. Generate your own keys

```bash
ssh-keygen -t ed25519 -C "your-device-name" -f ~/.ssh/id_ed25519
ssh-keygen -t ed25519 -C "your-device-name-signing" -f ~/.ssh/git_sign_ed25519
```

Use a passphrase on both. `ssh-agent` or Keychain integration means you only enter it once per
session, not on every push.

## 2. Register the public keys

- `id_ed25519.pub` as an **authentication key** on every forge you push to.
- `git_sign_ed25519.pub` as a **signing key** on every forge that supports SSH signature
  verification.

## 3. Clone this repo

```bash
git clone https://github.com/zaccesss/ssh-config.git ~/.ssh-config-src
```

## 4. Create your allowed signers file

Copy the example and replace the placeholders with your own commit email and the contents of
`~/.ssh/git_sign_ed25519.pub`:

```bash
cp ~/.ssh-config-src/allowed_signers.example ~/.ssh/allowed_signers
```

Add one line per signing key, one for each machine you sign commits from, so every machine can
verify commits signed by any other.

## 5. Copy the config into place

```bash
cp ~/.ssh-config-src/<platform>/config ~/.ssh/config
chmod 600 ~/.ssh/config ~/.ssh/allowed_signers
chmod 600 ~/.ssh/id_ed25519 ~/.ssh/git_sign_ed25519
chmod 644 ~/.ssh/id_ed25519.pub ~/.ssh/git_sign_ed25519.pub
```

Replace `<platform>` with `mac`, `linux` or `windows`.

## 6. Verify it worked

```bash
ssh -T git@github.com
git config --get gpg.ssh.allowedSignersFile
```

> [!TIP]
> Make a throwaway signed commit and confirm `git log --show-signature -1` returns "Good git
> signature", not just that the settings are present.

## Updating after a change to this repo

```bash
cd ~/.ssh-config-src
git pull
cp <platform>/config ~/.ssh/config
```

> [!WARNING]
> Pulling the source repo does not update the active `~/.ssh/config` by itself, the copy step has
> to run again.

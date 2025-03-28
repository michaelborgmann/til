# Using SSH for Secure Authentication

[SSH (Secure Shell)]((https://en.wikipedia.org/wiki/Secure_Shell)) enables secure remote connections via SSH keys, eliminating the need for repeated password entry. To set up SSH:

## Generate an SSH Key

```
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```

* Saves key to ~/.ssh/id_ed25519 by default.
* Optionally, set a passphrase for added security.

## Add Key to SSH Agent

```
$ eval "$(ssh-agent -s)"
$ ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

## Configure SSH for GitHub (Optional)

Add to `~/.ssh/config`:

```
Host github.com  
  AddKeysToAgent yes  
  UseKeychain yes  
  IdentityFile ~/.ssh/id_ed25519  
```

## Change Passphrase (if needed)

```
ssh-keygen -p -f ~/.ssh/id_ed25519
```

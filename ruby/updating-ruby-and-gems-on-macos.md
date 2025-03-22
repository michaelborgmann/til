# Updating Ruby & Gems on macOS

If you're using macOS, you might run into issues with Ruby and Gems due to the system's default installation. Here’s how to update both using [rbenv](https://rbenv.org) with [zsh](https://www.zsh.org) (e.g. [Oh My Zsh](https://ohmyz.sh)):

## What is `rbenv`?
A lightweight Ruby version manager that lets you install and switch versions without modifying the system installation.

### Alternative: [RVM](https://rvm.io)
Ruby Version Manager (RVM) also handles Ruby versions but modifies your shell more aggressively. `rbenv` is simpler and preferred by most users.

## 1️⃣ Check Your Current Ruby Version

Run:

```
$ ruby -v
```


## 2️⃣ Install `rbenv`

If not installed, use Homebrew:

```
$ brew install rbenv
```

Then, add `rbenv` to your shell (`~/.zshrc` for `zsh` users):

```
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
```

Apply changes:

```
$ source ~/.zshrc
```

## 3️⃣ Install a New Ruby Version

Check available versions:

```
$ rbenv install -l
```

Install your preferred version (e.g., 3.4.2):

```
$ rbenv install 3.4.2
```

Set the installed version as the global default:

```
$ rbenv global 3.4.2
```

Run this command to apply the changes:

```
$ rbenv rehash
```

## 4️⃣ Update RubyGems

After installing the new Ruby version, update RubyGems:

```
$ gem update --system
$ gem update
```

## 5️⃣ Verify Your Ruby Installation

Check which Ruby version is being used to ensure it's not the system default:

```
$ which ruby
```

If everything is set up correctly, this should point to `~/.rbenv/shims/ruby` instead of `/usr/bin/ruby`.

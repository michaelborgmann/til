# Clean & Update Homebrew (brew)

[Homebrew](https://brew.sh) is a package manager for macOS that simplifies installing and managing software. Without regular maintenance, outdated or duplicate versions can accumulate, wasting disk space.

## Homebrew Terminology

* **[Formulae](https://formulae.brew.sh)**: Homebrew’s package definition files.
* **[Cask](https://formulae.brew.sh/cask/)**: Like formulae, but for macOS GUI apps.
* **Cellar**: Homebrew’s installation directory (`/usr/local/Cellar` or `/opt/homebrew/Cellar` on Apple Silicon), with symlinks in `/usr/local/bin`.
* **Caskroom**: Cask’s installation directory (`/usr/local/Caskroom`)
* **Tap**: A source of formulae (`/usr/local/Homebrew/Library/Taps`). Custom taps can be added via `brew tap <username>/<repo>`.

## Updating & Cleaning

Fetch the latest formulae versions:

```
brew update
```

Upgrade all installed packages:

```
brew upgrade
```

Use `brew cleanup` to remove outdated versions. Add `-s` (*scrub*) to delete all cached downloads, including those for uninstalled packages.

```
brew cleanup
brew cleanup -s
```

It's recommended to run `cleanup` after `update` to remove outdated packages:

```
brew update && brew upgrade && brew cleanup
```

Remove all unnecessary files, including casks:

```
brew cleanup --prune=all
```

Check system health:

```
brew doctor
```

Check for missing dependencies:

```
brew missing
```

## Maintenance Script

```bash
#!/bin/bash
brew update
brew upgrade
brew cleanup -s
brew cleanup --prune=all
brew doctor
brew missing
```

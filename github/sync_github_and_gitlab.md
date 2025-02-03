# Sync GitHub and GitLab

If you want a presence on both [GitHub](https://github.com) and [GitLab](https://gitlab.com) or need redundancy, syncing repositories across both platforms is useful.

## Steps to Sync GitHub and GitLab Repositories

### 1. Create repositories on both platforms

Create a repository on GitHub (`github.com/yourusername/repo`) and GitLab (`gitlab.com/yourusername/repo`).

### 2. Clone one of the repositories locally

```
git clone https://github.com/yourusername/repo.git
cd repo
```

### 3. Add the second remote

```
git remote add gitlab https://gitlab.com/yourusername/repo.git
```

Check your remotes:

```
git remote -v
```

### 4. Push to both remotes

```
git push origin main    # Push to GitHub
git push gitlab main    # Push to GitLab
```

### 5. Add Push URLs

By default, a Git remote has a single URL for fetching and pushing. Using `--add --push`, you can set multiple push URLs.

```
git remote set-url --add --push origin https://gitlab.com/yourusername/repo.git
git remote set-url --add --push origin https://github.com/yourusername/repo.git
```

Now, push to both GitLab and GitHub:

```
git push
```

## Existing Projects

### Pull from both repositories

To avoid conflicts, pull the latest changes from both GitHub and GitLab before pushing.

```
git pull origin main    # Pull from GitHub
git pull gitlab main    # Pull from GitLab
```

### Resolve Conflicts

If differences exist, resolve conflicts manually by merging changes and ensuring consistency.

### Push changes to both platforms

```
git push origin main    # Push to GitHub (master repository)
git push gitlab main    # Push to GitLab (secondary repository)
```

## Additional Tips

* Avoid making changes on both platforms simultaneously to prevent conflicts.
* Rename `origin` if needed: `git remote rename origin github`

# Undo Last Git Commit

You can undo the last commit in Git with [git reset](https://git-scm.com/docs/git-reset), [git revert](https://git-scm.com/docs/git-revert), or [git commit --amend](https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---amend).

## Using git reset

The `git reset` command allows you to undo the last commit.

### Soft Reset (--soft)
Moves the pointer to the previous commit but keeps changes staged for recommitting.

```
git reset --soft HEAD~1
```

### Mixed Reset (--mixed)

Unstages changes but keeps them in the working directory for review.

```
git reset --mixed HEAD~1
```

## Using git revert

Creates a new commit that undoes the last one while preserving history:

```
git revert HEAD
```

## Using git commit --amend

Opens the text editor to modify the last commit message or add staged changes:

```
git commit --amend
```

## Using git reflog

To revert to a previous state, use git reflog to find the commit:

```
git reflog
```

Then reset HEAD to it:

```
git reset --hard <reflog-identifier>
```

⚠️ Warning: This discards all changes.

## Undoing Pushed Commits in Git

Avoid rewriting history in shared repositories unless removing leaked data or large files.

### Delete the Last Commit

Force push specific parent:

```
git push origin +dd21ab16^:master
```

'x^' means "parent of x"; '+' forces a push.

Alternatively, reset Locally and Force Push:

```
git reset HEAD^ --hard
git push origin -f
```

### Remove an Older Commit

Use [git rebase](https://git-scm.com/docs/git-rebase) to rewrite history

```
git rebase -i dd21ab16^
```

In the editor, delete the commit line, then force-push:

```
git push origin -f
```

### Fix Typos in Commit

Same as before, but replace `pick` with `edit`.

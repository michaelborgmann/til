# Amend a Pushed Commit and Update Its Tag

If you forgot to include changes in your most recent commit and have already pushed both the commit and its Git tag, you can amend the commit, move the tag, and force-push the updates.

## Stage the Missing Changes

Add the files you forgot to include:

```bash
git add <files>
```

## Amend the Last Commit

Keep the existing commit message while adding the staged changes:

```bash
git commit --amend --no-edit
```

This creates a new commit with a different SHA.

## Move the Tag

Update the existing tag to point to the amended commit:

```bash
git tag -f v0.1.5
```

## Update the Remote Branch

Since the commit history changed, force-push the branch:

```bash
git push --force-with-lease
```

`--force-with-lease` is safer than `--force` because it refuses to overwrite remote changes you haven't seen.

## Update the Remote Tag

Force-push the updated tag:

```bash
git push --force origin v0.1.5
```

If Git refuses because the tag already exists, delete the remote tag first:

```bash
git push origin :refs/tags/v0.1.5
git push origin v0.1.5
```

## Complete Workflow

```bash
git add <files>
git commit --amend --no-edit
git tag -f v0.1.5
git push --force-with-lease
git push --force origin v0.1.5
```

⚠️ **Warning:** Amending a pushed commit rewrites Git history. Only do this if no one else has based work on the original commit, or coordinate with collaborators before force-pushing.

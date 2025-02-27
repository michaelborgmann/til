# Modifying Git Commit Messages

## Fix the last commit message

```bash
git commit --amend -m "New commit message"
```

This only works for the latest commit.

## Fix an older commit message using interactive rebase

```bash
$ git rebase -i HEAD~2
```

`HEAD~2` lets you edit the last two commits.

1. **In the editor, change** `pick` **to** `reword` **for the commit you want to modify**. Git will then prompt you to edit the commit message.
2. **Be aware**: This changes commit hashes. If the commits haven’t been pushed yet, you're good to go.

If already pushed, you’ll need to force push:

```bash
git push --force
```

⚠️ Use force push with caution, as it rewrites history!
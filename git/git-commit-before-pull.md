# Git Commit Before Pull: Fixing Divergent Branches

If you've committed locally and Git's complaining about divergent branches when pulling, here’s how to fix it:

1. **Merge** (default, creates a merge commit):
   ```bash
   git pull --no-rebase
   ```
2. **Rebase** (cleaner history, rewrites local commits on top of remote):
   ```bash
   git pull --rebase
   ```
3. **Fast-Forward Only** (only pulls if remote is strictly ahead):
   ```bash
   git pull --ff-only
   ```

## Optional: Set Default Behavior

To avoid being asked every time, set your preferred strategy:

* **Merge (default)**:
   ```bash
   git config pull.rebase false
   ```
* **Rebase (cleaner history)**:
   ```bash
   git config pull.rebase true
   ```

Add `--global` to make it your default for all repos.
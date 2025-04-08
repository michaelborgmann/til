# Correct the Author of a Pushed Git Commit

If you commit with the wrong user details (like an incorrect name or email), you can easily fix it even if the commit has already been pushed to GitHub. Here's how to do it:

## Steps:

1. **Amend the Commit Author Information**: Run the following command to change the author of the last commit:

	```
	$ git commit --amend --author="Correct Name <correct.email@example.com>"
	```
	
	Replace "Correct Name <correct.email@example.com>" with your correct details.
	
2. **Force Push the Changes**: Since the commit has already been pushed, you'll need to force-push to update the commit on GitHub:

	```
	$ git push --force
	```
	
3. **Verify the Commit**: You can check the commit on GitHub or use git log to verify that the author details have been updated.

## Important Notes:

* **Force pushing** rewrites the commit history on the remote branch. If others are working on this branch, they will need to run `git pull --rebase` to sync their local copies.
* Always communicate with collaborators before force-pushing to avoid potential issues.

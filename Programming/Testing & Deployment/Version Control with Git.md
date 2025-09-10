---
Created: 2025-06-23T20:22
---
## What Is Git?

- **Git** is a **distributed version control system (VCS)** that tracks changes in your codebase.
- Allows multiple developers to **collaborate**, **revert**, and **branch** without losing code history.

  

## Basic Git Workflow

```Shell
# 1. Clone a repository
git clone <repo_url>

# 2. Make changes in your code

# 3. Check status
git status

# 4. Stage changes
git add <filename>       # or `git add .` for all

# 5. Commit changes
git commit -m "Your message"

# 6. Push to remote
git push origin <branch>

# 7. Pull latest changes
git pull origin <branch>
```

  

## Branching & Merging

|   |   |
|---|---|
|Command|Description|
|`git branch`|List branches|
|`git branch <name>`|Create a new branch|
|`git checkout <name>`|Switch to branch|
|`git checkout -b <name>`|Create and switch to new branch|
|`git merge <branch>`|Merge another branch into current branch|
|`git branch -d <name>`|Delete a branch|

  

## Staging Area

- **Working Directory:** Your local changes
- **Staging Area:** Changes added via `git add`
- **Repository:** Final snapshot after `git commit`

  

## Viewing History

|   |   |
|---|---|
|Command|Description|
|`git log`|Show commit history|
|`git log --oneline`|Compact view|
|`git diff`|View unstaged changes|
|`git diff --staged`|View staged changes|
|`git show <commit_hash>`|See details of a specific commit|

  

## Undoing Changes

|   |   |
|---|---|
|Task|Command|
|Unstage a file|`git reset <file>`|
|Undo last commit (keep changes)|`git reset --soft HEAD~1`|
|Discard local changes|`git checkout -- <file>`|
|Revert a commit|`git revert <commit_hash>`|

  

## Remote Repos

|   |   |
|---|---|
|Command|Description|
|`git remote -v`|View remotes|
|`git remote add origin <url>`|Add a remote|
|`git push -u origin main`|Push and track the remote branch|

  

## GitHub Workflow Summary

```Shell
# Create repo on GitHub
git init
git remote add origin https://github.com/user/repo.git
git add .
git commit -m "first commit"
git push -u origin main
```

  

## Useful Tools & Services

|   |   |
|---|---|
|Tool|Purpose|
|**GitHub**|Code hosting, collaboration|
|**GitLab**|CI/CD integrated VCS|
|**Bitbucket**|Git hosting by Atlassian|
|**Git GUI Clients**|VS Code Git, Sourcetree, GitKraken|

  

## Best Practices

- ✅ Commit often with clear messages
- ✅ Use branches for features and bug fixes
- ✅ Pull before pushing to avoid conflicts
- ✅ Resolve conflicts carefully during merges
- ✅ Never commit sensitive info (use `.gitignore`)
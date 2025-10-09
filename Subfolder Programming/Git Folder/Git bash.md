## Git bash

### ==File & Directory Commands (Bash)==

|   |   |
|---|---|
|Command|Description|
|`pwd`|Show current directory (print working directory)|
|`ls`|List files in directory|
|`ls -a`|List all files including hidden ones|
|`cd folder`|Change directory|
|`cd ..`|Go up one level|
|`mkdir foldername`|Create a new folder|
|`touch filename`|Create a new empty file|
|`rm filename`|Delete a file|
|`rm -r foldername`|Delete folder recursively|
|`clear`|Clear the terminal|
|`exit`|Close Git Bash|

### ==Git Initialization==

|   |   |
|---|---|
|Command|Description|
|`git init`|Initialize a new Git repository|
|`git clone URL`|Clone a repository from GitHub|
|`git config --global user.name "Your Name"`|Set your Git username|
|`git config --global user.email "you@example.com"`|Set your Git email|
|`git config --global core.editor "code --wait"`|Sets vscode as default editor|
|`git config --global -e`|opens git config in default editor|
|`git config --global core.autocrlf true`|`true` for windows input for `mac`|

  

### ==Staging & Committing==

|   |   |
|---|---|
|Command|Description|
|`git status`|Check file status|
|`git add filename`|Stage a file|
|`git add .`|Stage all changed files|
|`git commit -m "message"`|Commit staged changes with a message|

  

### ==Remote Repositories==

|   |   |
|---|---|
|Command|Description|
|`git remote add origin URL`|Add a remote repository|
|`git push -u origin main`|Push to main branch (first time)|
|`git push`|Push changes to remote|
|`git pull`|Pull latest changes from remote|
|`git clone URL`|Clone a repository|

  

### ==Branching==

|   |   |
|---|---|
|Command|Description|
|`git branch`|List all branches|
|`git branch branch-name`|Create new branch|
|`git checkout branch-name`|Switch to a branch|
|`git checkout -b new-branch`|Create and switch to new branch|
|`git merge branch-name`|Merge a branch into current one|
|`git branch -d branch-name`|Delete a branch|
|`git branch -m new-branch-name`|Rename a branch|

### ==History & Logs==

|   |   |
|---|---|
|Command|Description|
|`git log`|View commit history|
|`git log --oneline`|Condensed log view|
|`git show commit-id`|Show changes of specific commit|

  

### ==Undo Commands==

|   |   |
|---|---|
|Command|Description|
|`git reset filename`|Unstage a file|
|`git checkout -- filename`|Revert changes in a file|
|`git reset --hard`|Undo all changes (warning!)|
|`git revert commit-id`|Revert a specific commit safely|

  

### ==Other Handy Commands==

|   |   |
|---|---|
|Command|Description|
|`git stash`|Temporarily save uncommitted changes|
|`git stash apply`|Reapply stashed changes|
|`git diff`|See what's changed|
|`git tag`|Show or create tags (releases)|

## 🛠 ==Git Stash==

|Command|Description|
|---|---|
|`git stash`|Stash tracked changes (default).|
|`git stash -u`|Stash tracked **and untracked** files.|
|`git stash -a`|Stash **all changes** (tracked, untracked, ignored).|
|`git stash save "msg"`|Stash with a custom message (older style, still works).|
|`git stash push -m "msg"`|Preferred way to stash with a message.|
|`git stash list`|Show all stashed entries.|
|`git stash show`|Show summary of latest stash.|
|`git stash show -p`|Show patch (diff) of latest stash.|
|`git stash pop`|Apply latest stash and **remove it** from stash list.|
|`git stash apply`|Apply latest stash but **keep it** in stash list.|
|`git stash apply stash@{n}`|Apply specific stash (by index).|
|`git stash drop stash@{n}`|Delete specific stash.|
|`git stash clear`|Remove **all** stashes.|
|`git stash branch new-branch`|Create a new branch and apply the stash there.|
## More

## ==**Git Configuration**==

|   |   |
|---|---|
|Command|Description|
|`git config --global user.name "Your Name"`|Set global username|
|`git config --global user.email "you@example.com"`|Set global email|
|`git config --list`|List all Git configs|
|`git config --global core.editor "code --wait"`|Set default editor (e.g., VS Code)|

## ==**Repository Setup**==

|   |   |
|---|---|
|Command|Description|
|`git init`|Initialize a new Git repo|
|`git clone <url>`|Clone a repo|
|`git remote -v`|Show remote URLs|
|`git remote add origin <url>`|Add a remote|

## ==**Staging & Committing**==

|   |   |
|---|---|
|Command|Description|
|`git status`|View file changes|
|`git add <file>`|Stage a file|
|`git add .`|Stage all changes|
|`git commit -m "message"`|Commit with message|
|`git commit -am "msg"`|Add and commit tracked files|

## ==**Branching**==

|   |   |
|---|---|
|Command|Description|
|`git branch`|List branches|
|`git branch <name>`|Create a branch|
|`git checkout <name>`|Switch branch|
|`git checkout -b <name>`|Create and switch branch|
|`git merge <branch>`|Merge branch into current|
|`git branch -d <name>`|Delete branch|
|`git branch -m new-branch-name`|Rename a branch|

## ==**History & Undo**==

|   |   |
|---|---|
|Command|Description|
|`git log`|Show commit history|
|`git log --oneline`|Compact log|
|`git diff`|Show changes|
|`git diff --staged`|Staged changes diff|
|`git restore <file>`|Discard changes in file|
|`git reset <file>`|Unstage file|
|`git reset --hard`|Undo all changes (danger!)|

## ==**Sync with Remote**==

|   |   |
|---|---|
|Command|Description|
|`git fetch`|Download from remote|
|`git pull`|Fetch + merge|
|`git push`|Upload changes|
|`git push -u origin <branch>`|Set upstream branch|

## ==**Clean Up**==

|   |   |
|---|---|
|Command|Description|
|`git stash`|Save local changes|
|`git stash pop`|Reapply stashed changes|
|`git clean -fd`|Remove untracked files and dirs|

## ==**Tagging**==

|   |   |
|---|---|
|Command|Description|
|`git tag`|List tags|
|`git tag <name>`|Create tag|
|`git push origin <tag>`|Push tag to remote|

## ==**Git Bash Basics**==

|   |   |
|---|---|
|Bash Command|Description|
|`ls`|List directory contents|
|`cd <folder>`|Change directory|
|`pwd`|Show current directory|
|`mkdir <name>`|Make new folder|
|`touch <file>`|Create new file|
|`rm <file>`|Delete file|
|`clear`|Clear terminal|
|`cat <file>`|Print file content|
|`nano <file>`|Edit file in terminal|

## ==**Tips**==

- Use `TAB` for auto-completion.
- Use `Ctrl + C` to cancel a command.
- Use `!!` to rerun last command.
- Use `git help <command>` for command docs.

## Advance Git Commands

### ==Rewriting History==

|   |   |
|---|---|
|Command|Description|
|`git commit --amend`|Edit last commit|
|`git rebase <branch>`|Replay commits on another base|
|`git rebase -i HEAD~n`|Interactive rebase (edit, squash)|
|`git cherry-pick <commit>`|Apply a specific commit from another branch|
|`git reflog`|Show history of HEAD (useful for recovery)|
|`git reset --soft <commit>`|Reset HEAD but keep changes staged|
|`git reset --mixed <commit>`|Reset HEAD and unstage changes|
|`git reset --hard <commit>`|Reset everything (danger!)|

### ==Remote Management==

|   |   |
|---|---|
|Command|Description|
|`git remote rename <old> <new>`|Rename a remote|
|`git remote remove <name>`|Remove a remote|
|`git push origin --delete <branch>`|Delete remote branch|
|`git fetch --prune`|Remove deleted remote branches locally|

### ==Submodules (Used in Monorepos or Dependencies)==

|   |   |
|---|---|
|Command|Description|
|`git submodule add <repo>`|Add a submodule|
|`git submodule init`|Initialize submodules|
|`git submodule update`|Fetch submodules|

### ==Advanced Log Viewing==

|   |   |
|---|---|
|Command|Description|
|`git log --graph --oneline --all`|Visual branch history|
|`git show <commit>`|Show specific commit|
|`git blame <file>`|Show who changed each line|
|`git shortlog -sn`|Show contributors summary|

## ==Bash Scripting in Git Bash==

If you're using Git Bash for scripting:

|   |   |
|---|---|
|Command|Description|
|`#!/bin/bash`|Start a bash script|
|`for i in *.js; do echo $i; done`|Loop through JS files|
|`if [ -f file ]; then ... fi`|Check if file exists|
|`$(command)`|Command substitution|
|`alias gs="git status"`|Create alias|

## ==Git Internals (for deep dives)==

- `.git/` folder: holds all repo data (HEAD, objects, refs, etc.)
- `git cat-file -p <hash>`: read Git object
- `git hash-object <file>`: hash a file
- `git fsck`: check repo integrity

  

### ==Weird But Useful==

|   |   |
|---|---|
|Command|Description|
|`git bisect`|Binary search to find buggy commit|
|`git archive`|Create a tar/zip of your repo|
|`git worktree`|Manage multiple working directories linked to one repo|

### ==Git Ignore & Attributes==

|   |   |
|---|---|
|File|Purpose|
|`.gitignore`|Ignore files or folders|
|`.gitattributes`|Define file handling behavior (e.g., text, diff)|

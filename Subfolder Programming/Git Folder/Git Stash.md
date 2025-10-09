# 📌 Git Stash Cheat Sheet

### 🔹 What is Git Stash?

`git stash` lets you **temporarily save changes** (modified or staged) without committing them. It cleans your working directory so you can switch branches, pull updates, or work on something else, then restore your changes later.

---
## 🛠 Common Commands

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

---
## ⚠️ Gotchas

- By default, `git stash` only saves **tracked** changes. Use `-u` or `-a` if you want untracked/ignored files.
- `git stash pop` can cause merge conflicts. Use `git status` + `git diff` to resolve.
- If you stash multiple times, each stash gets an index: `stash@{0}` is the most recent.
- Stashing does **not** replace commits — it’s only temporary.
---
## ✅ Real-World Example: Rebasing with Uncommitted Work

Say you’re working on a feature but need to **rebase onto `main`**:
```bash
# Work in progress 
git status 
# shows modified files not ready to commit  

# Save them 
git stash push -m "WIP: login form validation"  

# Update your branch 
git checkout main 
git pull origin main 
git checkout feature-branch 
git rebase main  

# Restore your work 
git stash pop 
# Resolve conflicts if needed
```

👉 This way, you don’t commit half-finished work, but you don’t lose it either.
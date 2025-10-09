# 📌 Git Rebase Cheat Sheet

### 🔹 What is Git Rebase?

`git rebase` **moves or reapplies commits** from one branch onto another.

- It **rewrites history** instead of creating a merge commit.
- Useful for **cleaning commit history** or keeping feature branches up-to-date.
---
## 🛠 Common Commands

| Command                                           | Description                                                                  |
| ------------------------------------------------- | ---------------------------------------------------------------------------- |
| `git rebase <branch>`                             | Rebase current branch onto `<branch>`.                                       |
| `git rebase -i <commit>`                          | Interactive rebase starting from `<commit>` (edit, squash, reorder).         |
| `git rebase --onto <newbase> <upstream> <branch>` | Move `<branch>` onto `<newbase>` starting after `<upstream>`.                |
| `git rebase --abort`                              | Cancel the rebase and return to original branch state.                       |
| `git rebase --continue`                           | Continue after resolving conflicts during a rebase.                          |
| `git rebase --skip`                               | Skip the commit causing conflicts.                                           |
| `git pull --rebase`                               | Pull changes and rebase instead of merge (avoids unnecessary merge commits). |

---
## ⚠️ Gotchas

- Rebasing **rewrites commit history**. Don’t rebase commits that are already pushed to a shared branch.
- Conflicts can happen; resolve them, then `git rebase --continue`.
- Use **interactive rebase** (`-i`) to tidy your commits: squash minor commits, reorder, or edit messages.
---
## ✅ Real-World Example: Updating Feature Branch

You’re working on `feature-branch` and want the latest changes from `main`:

```bash
# Switch to your feature branch 
git checkout feature-branch  

# Rebase onto main 
git fetch origin 
git rebase origin/main  

# Resolve conflicts if they appear 
git status 
git add <resolved-files> 
git rebase --continue  

# If you want to abort 
git rebase --abort
```

---

### 🔹 Interactive Rebase Example (Cleaning History)

`git rebase -i HEAD~4`

- Opens editor with last 4 commits.
- Options:
    - `pick` = keep commit
    - `squash` = combine with previous
    - `edit` = modify commit
- Save & exit → history rewritten.
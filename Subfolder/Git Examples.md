## Examples

## ==**Initialize a Project**==

```Shell
mkdir my-project
cd my-project
git init
```

📝 _Creates a folder, enters it, and initializes it as a Git repo._

  

## ==**Configure User Info (First Time Only)**==

```Shell
git config --global user.name "Juan Dela Cruz"
git config --global user.email "juan@email.com"
```

📝 _Sets your identity for commits across all repositories._

  

## ==**Create and Stage Files**==

```Shell
touch index.html
touch style.css
git add index.html style.css
```

📝 _Creates two files and stages them for commit._

  

## ==**Commit Changes**==

```Shell
git commit -m "Initial commit with HTML and CSS files"
```

📝 _Saves a snapshot of the current project state._

  

## ==**Connect to Remote and Push**==

```Shell
git remote add origin https://github.com/yourusername/my-project.git
git branch -M main
git push -u origin main
```

📝 _Links your local repo to GitHub and pushes your code._

## ==**Clone an Existing Repository**==

```Shell
git clone https://github.com/otheruser/sample-repo.git
cd sample-repo
```

📝 _Downloads and enters a remote project directory._

  

## ==**Branching & Switching**==

```Shell
bash
CopyEdit
git checkout -b new-feature

```

📝 _Creates a new branch and switches to it._

  

## ==**Merge a Branch**==

```Shell
bash
CopyEdit
git checkout main
git merge new-feature

```

📝 _Merges changes from `new-feature` into `main`._

  

## ==**View Commit Log**==

```Shell
bash
CopyEdit
git log --oneline

```

📝 _See a summarized history of commits._

  

## ==**Undo a Change**==

```Shell
bash
CopyEdit
git checkout -- index.html

```

📝 _Reverts `index.html` back to the last committed state._

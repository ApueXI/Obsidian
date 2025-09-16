
### Programming with Mosh

> [!important]
> 
> ### Can also use `git add *.js`
> 
>   
> 
> ### `New-Item -Name .gitignore -ItemType File` You can also change the `.gitignore` into something like `README.md`
> 
>   
> 
> ### `git ls-files`
> 
>   
> 
> ### `git rm —cached FILENAME` or `git rm —cached -r FILENAME` to remove the file from the repository
> 
>   
> 
> ### `git rm -f FILENAME` to remove the file from and directory and the repository
> 
>   
> 
> ### Gitignore Templates ==[https://github.com/github/gitignore](https://github.com/github/gitignore)==
> 
>   
> 
> ### `git status -s` for more easily readable git status
> 
>   
> 
> ### Once you configured git config you can use `git difftool` or `git diftool —staged` to see what difference did the commit did(?)
> 
>   
> 
> ### Can use `git restore —staged FILENAME` to undo change in the stage
> 
> ### Use `git restore FILENAME` to undo change before commitiing
> 
>   
> 
> ### `git log —oneline —reverse` use it to show commit logs. `—oneline` summrizes it `—reverse` reverses the order
> 
>   
> 
> ### `git fetch origin`
> 
> ### `git resset —hard origin/main` fetches the latest from github

  

### Configuring User in git

> [!important]
> 
> ### `git config —global -e`
> 
> ### `git config —global` `[user.name](http://user.name)` `“YOUR NANE”`
> 
> ### `git config —global` `[user.email](http://user.email)` `“YOUR EMAIL”`
> 
> ### `git config —global core.editor “code —wait”`
> 
> ### `git config —global core.autocrlf true`
> 
> ### `git config —global diff.tool vscode`
> 
> ### `git config —global difftool.vscode.cmd “code —wait —diff $LOCAL $REMOTE”`

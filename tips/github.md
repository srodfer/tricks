![grafico_git](http://marklodato.github.io/visual-git-guide/basic-usage.svg)


###git init: 
Create a new directory, open it and perform a git init to create a new git repository
```php
$ git init 
```

###git add: 
Propose changes (add this content to the next commit)
```php
$ git add <filename>
$ git add *
```

###git commit: 
Commit files to the Head
```php
$ git commit -m "Commit message"
```
Stage every file that is already tracked before doing the commit (no need of git add)
```php
$ git commit -a
```
To correct the last commit
```php
$ git commit --amend
```
###git status
Shows status of files in the index versus the working directory. It will list out files that are untracked (only in your working directory), modified (tracked but not yet updated in your index), and staged (added to your index and ready for committing).
```php
$ git status
```

###git log: 
View the commit history
```php
$ git log
```

###git diff:
Compare your working directory to your staging area. The result tells you the changes you’ve made that you haven’t yet staged
```php
$ git diff
```
Compare your staged changes to your last commit
```php
$ git diff --staged
```

###Undo changes:
Unstage a staged file. Copy files from the latest commit to the stage. Use this command to "undo" a git add files
```php
git reset HEAD <filename>
```
Unmodify a modified file. Copy files from the stage to the working directory. Use this to throw away local changes. 
```php
git checkout -- <filename> 
```
Remove a file from your staging area and working directory
```php
git rm
```

###Clone and remotes:

Create a working copy of a local repository
```php
git clone /path/to/repository
```
When cloning a remote repository 
```php
git clone username@host:/path/to/repository
```

Connect your repository with a remote
```php
git remote add origin /path/to/server
```
Send changes to your remote repository (origin is where you want to send your changes, master is the branch you want to push your changes to)
```php
git push origin master
```
Update your local repository to the newest commit
```php
git pull
```
###How to clone a remote repository and link it with another repo**
```php
  1. Create a new repo at github.
  2. $ git clone username@host:/path/to/repository
  3. $ git remote rename origin upstream
  4. $ git remote add origin your_username@host:/path/to/repository
  5. $ git push origin master
```

###Detached HEAD state
Go to commit_id and be in detached HEAD state
```php
git checkout <commit_id>
```
Get out of detached HEAD state and go to last commit
```php
git checkout master
```

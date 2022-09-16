# BRANCH


### Create new branch :
```
git checkout -b <new_branch_name>
```
### Moves to the previous branch where you were before :
``` 
git checkout <branch_name>
```
### In order to rename a current branch :
```
git branch -m <new_branch_name> 
```
### Delete a local branch :
```
git branch --delete <branch_name>
```
### Shorter version :
```
git branch -d <branch_name>  
```
### Force delete un-merged branches :
```
git branch -D <branch_name> 
```


# STASH

### Add changes to stash :
```
git stash 
```
### To see all the changes :
```
git stash list
```
### Get last stash , applies the changes and removes the files from the stash :
```
git stash pop
```
### Applies the changes and leaves a copy in the stash :
```
git stash apply
```

# REVERT

### Undo the commit and creates a new commit :
```
git revert [commit] 
```

# REBASING

### Ultimately main reason to do this to have linear commit history. To make look like we never made of branch history. Keeps our commit any more ordered fashion one solid linear history  :

```
git checkout -b Reabase1
git rebase master
git checkout master
git merge Reabase1
```

# AMEND

### Git amend is useful for changing the commit message or changing your last commit files changes, rewrite history. Don't do this on the master. do it somewhere on your local branch, because it will rewrite the history again can cause conflict.This command will create another commit :
```
git commit --amend
```
### Applies message :
```
git commit --amend -m "message of my commit changed "
```
### Replaces another commit, the last commit is orphaned, applies message, and adds new files :
```
git commit --amend -am "message"
```

# RESET

## There three types of reset. --hard, --soft, --mixed. git reset defaults to --mixed. git reset commands deafults to --mixed.
## Easy explanation : 
## Given : - A - B - C (master)
### You will see B and C's stuff in green (staged and ready to commit) :
```
git reset --soft A
```
### You will see B and C's stuff in red (unstaged and ready to be staged (green) and then committed) :
``` 
git reset --mixed A (or git reset A)
```
### You will no longer see B and C's changes anywhere (will be as if they never existed)
```
git reset --hard A
```

### if you dont want changes, go back but does not cleanup.  unstaging the chnages. This before adding changes (for commits does not apply). How do I get my repo back to the state it was in before I started making changes without losing my changes?

```
git reset HEAD 
```
```
git status -s
```

### Unstage info.txt  removing file  from being staged, untrack the file. 
```
git reset info.txt
```

### Unstaging commited code, back to where it was before. By reseting we can make chnages on local repo, we dont lose here anything. We are going back but we are not deleting or cleaning. 

```
git reset b5cd69e
```
### Undo last commit

```
git reset --soft HEAD^
```

### The “git reset –hard” operation is considered the most effective operation if you wish to entirely get rid of your last commit. It means that when you perform this operation, the head of your file will change, i.e., it will no longer be pointing to your last commit. Not only this, but it will also clear out your last commit from your index and even change your current working directory. What it does head reseted to last commit where it was before, your changes will be lost will start from begining. 

```
git reset --hard 
```
### head will be c9f17d2 at your branch, bracnh will be back to here (c9f17d2)

```
git reset [commit]

git reset c9f17d2 --hard
```

### If you do find yourself in the situation where you’ve accidentally committed some messy code, you can do a “soft” reset. This means that the code appears as if it has not been committed yet. Then you can tidy up your code in your IDE before making a cleaner commit.
```
git reset --soft HEAD~1  
```
### Takes back 2 commits before does not clean your code.
```
git reset --soft HEAD~2
```
### This type of reset essentially erases your last commit. You should be very careful about performing hard resets, especially if you push your branch, as there is no way to restore your commit
```
git reset --hard HEAD~1
```
### Removes file in interactive mode.
```
git clean -x -d -i 
```

# TOOLS

```
git merge master
```
### While merging branch,  if you  face conflict then mergetool will be superman for you
```
git mergetool

git difftoll [commmit] [ commmit]

git difftool HEAD@{1.min.ago} HEAD@{1.day.ago}
```

# CONFIG && ALIAS

```
git config --global -e
```
### Global config for your git.
```
git config --global --list
```
### To get your current config list
```
git config --global alias.onelinegraph 'log --oneline --graph --decorate'
```
### setting config
```
git config --global alias.expireunreachablenow 'reflog expire --expire-unreachable=now --all'
```
### setting config
```
git config --global alias.gcunreachable 'gc --prune=now'
```

# TAG

### Two types of tags: LIGHTWEIGHT and ANNOTATED tags.
### A LIGHTWEIGHT tag is like a bookmark to a specific place that you'd want to use if you want to get back to that spot and an ANNOTATED tag allows you to make a tag that you can put your information about who did it what all the state of the thing was when it was done.
### Gets all tags:
```
git tag
```
### Checkout to the tag_name:
```
git checkout tag_name  
```
### This lightweight tag:
```
git tag mytag 
```
### This one is annotated tag:
```
git tag -a onmasterannotatde -m "say this"
```
### Show commits on a specific tag:
```
git show onmasterannotatde
```
### To delete a tag:
```
git tag -d tag_name
```
### To push all your tags:
```
git push --tags
```
### To delete tag on remote:
```
git push origin :tag_name
```

# LOG

### Shows git history of all commits that is only reachable ones:
```
git log --oneline
```
### Shows entire commit :
```
git log --pretty=oneline
```
### Finds all commits regarding to the given message:
```
git log --all --grep='loca*'
```
### Get all logs from author "username":
```
git log --author="username"
```
### Decorate the logs:
```
git reflog

git log -p

git log --pretty=oneline --abbrev-commit

git log --oneline --graph --decorate
```
### Logs from 100 to end:
```
git reflog HEAD@{100}
```

```
git reflog master

git reflog HEAD@{3.days.ago}

git reflog HEAD@{2.weeks.ago}

git reflog master

git difftool HEAD@{4} HEAD@{5}

git reflog expire --expire-unreachable=now --all
```
### Garbage collector for git history:
```
git gc --prune=now

```









# Stashing

## Prerequisite
Ensure your current directory is the one which we created at the beginning of this practical -- _git-workshop_
```bash
# you should have the following or similar after you 'ls'
$ ls
animal.txt  colour.txt  hello.txt  show.txt
```

## Stash work

```bash
# Lets create a dirty workspace
$ echo 'I am an unwanted change' >> hello.txt

# Git status should show our hello.txt file not staged for commit.
$ git status 

# "stash" those changes
$ git stash save "Experimental work with hello.txt"

# Git status will show we are working tree clean with nothing to commit
git status 

# See what is stashed in this repository
$ git stash list
stash@{0}: On master: experimental work with hello.txt
```
Now make another change to _hello.txt_ before moving on to the next section
```bash
# We want to stash your last change, check the status and our stash list
$ git stash
$ git status
On branch master
nothing to commit, working tree clean
$ git stash list
stash@{0}: WIP on master: 21954be rerge branch 'favourite-show'
stash@{1}: On master: experimental work with hello.txt

# Restore top/first stash (stash@{0}) & remove it from the list
$ git stash pop # == apply && drop

# Back to hello.txt ready to be staged
$ git status -s
 M hello.txt
```

## Reference commands
```bash
# 'save' is the default stash action -- needed if you want to include a message
$ git stash save -u "Stash all including untracked"

# Bring it (or another stash) back
$ git stash apply stash@{0}

# Remove the stash if it's no longer needed
git stash drop stash@{0}

# Or make a new branch & restore your changes there
git stash branch <branchname> [stash@<revision>]
```
# Stashing

Move changes in a dirty workspace away to the side

```bash
# You have a dirty workspace
$ git status -s
 D .eslintrc.json
?? .eslintrc.yaml

# "stash" those changes
$ git stash save "Experimental work with eslint"
Saved working directory and index state On master: Experimental work with eslint
HEAD is now at 645ba47 Merge pull request #884 from...

# See what stashes you have in this repository
$ git stash list
stash@{0}: On master: Experimental work with eslint
stash@{1}: kubernetes client test stuff
stash@{2}: WIP on master: d09a007 Merge pull request #768 from...

# Your workspace is now clean...is it?
$ git status -s
?? .eslintrc.yaml # this file isn't tracked by git yet, so not stashed by default

# Restore top/first stash (stash@{0}) & remove it from the list
$ git stash pop # == apply && drop

# Back to normal
$ git status -s
 D .eslintrc.json
?? .eslintrc.yaml

# 'save' is the default stash action -- needed if you want to include a message
$ git stash save -u "Stash all including untracked"

# Bring it (or another stash) back
$ git stash apply stash@{0}

# Remove the stash if it's no longer needed
git stash drop stash@{0}

# Or make a new branch & restore your changes there
git stash branch <branchname> [stash@<revision>]
```
# (Rundown) Saving Changes and Branching

A recap of some core concepts we have already covered

## Saving

Saving changes is a two-step process in Git:

```bash
# Stages changes to the staging area
git add <files>

# Commits a snapshot of changes to the local repo
git commit
```

## Adding

* Adds changes to the staging area
* Does not really affect the working tree
* Changes are not recorded until committed

```bash
# Add just these file(s)
git add app.js

# Add all changed files in this directory and sub-dirs
git add .

# Glob and stage a pattern of files
git add **/*.js

# Unstage the changes to app.js
git reset app.js
```

## Committing

* Commits the staged snapshot to the local repository
* Include a meaningful commit message
* Logically group your changes into separate commits

```bash
# Commits the staged snapshot - will open editor for a message
git commit

# Commits with a message
git commit -m "Make a meaningful change"
```

Twofer - commit and add in one command:

```bash
# Stage & commit all changed files with a message
git commit -am "FH-12345 - My files on disk are perfect"
```

## Branching

A branch in git is simply a reference to a commit

```bash
# List all local branches
git branch

# Create a new branch locally
git branch mynewbranch [myoptionalbasebranch]

# What commit is a branch pointing at?
git rev-parse mynewbranch

# What commits are on a branch?
git log mynewbranch [--pretty --graph --oneline --decorate]

# What branches point at a particular commit?
git branch --points-at e29b7ee

# Delete a branch
git branch -d mynewbranch

# Really delete a branch, even if it has changes that aren't on any other branches
git branch -D mynewbranch
```

There are also "remote-tracking" branches
These are read-only copies of what is on a "remote", at the time that we last "fetched" (updated the information we store locally about branches on the remote).

```bash
# Get new information from all remotes
git remote update [--prune] # or: git fetch --all [--prune]

# List all remote-tracking branches
git branch -r

# List all branches (local and remote-tracking)
git branch -a

# Track a remote branch
git branch [branchname] -u origin/anybranch

# Now status will show the relationship with
git status [-sb]
stdout: "Your branch is ahead of 'origin/anybranch' by 3 commits"

# Delete a branch from a remote
git push origin --delete mybranchname
```

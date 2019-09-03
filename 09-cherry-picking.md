# Cherry Picking

Apply the changes introduced by some existing commits

Our main use-case for git-cherry-pick is for taking some bugfix commits from one branch, and applying them to another (e.g. a release branch and master)

## Prerequisite
Ensure your current directory is that of the cloned repository in the previous practical.

## Practical

```bash
# Ensure that you're on the branch you want to copy commits to
# and the working directory is clean
$ git status
On branch cp-example
nothing to commit, working tree clean

# Bring a commit from a different branch over
git cherry-pick dea2da

# Notice that the changes, author details, and commit message are the same
# But the commit sha1 is different (and maybe the tree object)
$ git log -1 # or git show
commit b2d900443cb628f8d5c6accc271e7b66aaadb9ca
Author: Jason Madigan <jason@jasonmadigan.com>
Date:   Thu Dec 1 16:42:17 2016 +0000

    name change
```


# Next Section
[Tagging](./10-tagging.md)
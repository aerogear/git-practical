# Merging

In the last section, we learned about creating new branches. Often branches are
created temporarily to work on a specific piece of work. When that work is
ready, then those changes are brought back into the main line again.

Remember the branches from the last section? Originally there was the master
branch, and then we created a branch called 'favourite-animal', where we made
changes. We can now merge those changes back into master branch, and delete the
'my-new-branch' since we won't need it anymore.

## Practical One - Fast-forward merging

The simplest form of merging is *fast-forward* merging. Since branches are just
references to commits, and 'favourite-animal' is a direct descendant of master;
we can just update master to point to the same commit as 'favourite-animal'.

This is the default way that git will merge when the target branch is an
ancestor of the source branch. First, `checkout` the target branch (master in
this case), and then use the `merge` subcommand to bring the changes from the
source branch (favourite-animal) into this branch:

```bash
git checkout master

git merge favourite-animal
```

Master and the 'favourite-animal' branch are now pointing at the same commit.
We can delete the 'favourite-animal' branch.

```bash
git branch -d favourite-animal
```

## Practial Two - Merge commits

In some cases, the target branch will not be a direct ancestor of the source
branch. This is the case for our 'favourite-show' branch. Here, the default
action is to create a new commit which has two (or more) *parent* commits and a
message.

![Before creating a merge commit](./img/basic-merging-before.png)

While on the master branch, we can now merge the changes from the
'favourite-show' branch as follows:

``` bash
git merge favourite-show
```

The default commit message editor will have appeared here, to give you the
opportunity to modify the commit message for the new commit. The default is
usually fine.

![After creating a merge commit](./img/basic-merging-after.png)

Usually a *merge commit* will not contain any changes to files itself. The
changes will be in its ancestors. Sometimes when merging two divergent branches
though, there will be conflicting changes on either side of the merge. In this
case, there may be changes needed in the merge commit to resolve the conflicts.

It is worth checking the log here to see the commit history.
``` bash
git log
```

# Next Section
[Conflicts](./04-conflicts.md)



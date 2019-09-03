# Branches

A branch is just a reference to a commit, it has a human-readable name
and identifier. Instead of using the SHA-1 hash to reference a commit we can
now use the name of a branch.

When creating a repository using `git init` a branch named 'master' is created
for us, it is currently pointed at our latest commit.

![The current state of our repository](./img/basic-branch.png)

Let's designate 'master' as the branch for our main line of development,
anything on that branch should be stable. If we want to test out new features
without breaking the main line then we can create new branches.

## Practical One

We want to add a new file to our current project, but we don't want to mess up
'master'.

#### View the current branches

We can see all of the branches in our repository.

```bash
git branch
# stdout: master
```

#### Create a new branch from master

To add our new feature we want to add a new branch. Our new feature is adding
information about our favourite animal so let's call the branch something
descriptive like 'favourite-animal'.

```bash
git branch favourite-animal
# If we do a 'git branch' now we'll see our new branch is created, but we're
# still on master. Let's 'checkout' our new branch.

git checkout favourite-animal
```

Now that we have our branch created let's take a look at our commit history
using `git log`, this will give us information about what commit each branch is
currently pointing to.

#### Make some changes

Let's make some changes to our new branch and commit them.

```bash
echo 'My favourite animal is a <your-favourite-animal>!' > animal.txt

git add animal.txt
git commit -m "Add favourite animal"
```

We now have a repository that looks like this.

![The new state of our repository](./img/two-branches.png)

## Diving deeper

### Branches under the hood

Branches are stored in the `.git/refs/heads` directory as files. If we view the
contents of any of these files they just contain the SHA-1 hash of the commit
the branch is currently pointing to.

```bash
cat .git/refs/heads/favourite-animal
```

### HEAD

When we were doing `git log` you may have seen 'HEAD' mentioned in the log.
HEAD points to whatever is currently checked out. At the moment we have the
'favourite-animal' branch checked out so it will point to that. HEAD is a file
in the `.git` directory.

``` bash
cat .git/HEAD
# stdout: ref: refs/heads/favourite-animal
```

## Practical Two

We have created a branch that has information about our favourite animal. Now
let's create another branch from master and add information about our favourite
TV show. We are currently on the branch 'favourite-animal'. We need to create
our new branch from master.

```bash
# Create a new branch named favourite-show from the branch master
git branch favourite-show master
git checkout favourite-show
```

We'll leave the rest to you.

# Next Section
[Merging](./03-merging.md)


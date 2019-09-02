# Bisecting

Finding commits within your project.

* git bisect helps you figure out when breaking changes were introduced
* Uses a binary-search between one changeset and another to quickly narrow breakage to a single commit

## Practical

In the `git-tutorial` repo:

```bash
git checkout bisect
# Our bisect branch is a little ahead of of master (500 commits)
# At some point, a commit slipped in that means our app doesn't start
# and our tests fail.
# Lets use git bisect to find the broken commit
git bisect start
# Step 1 - find a commit where things are working
# I have no idea, so lets cast a wide net (across 500 commits)
git bisect good cddd186 # update to 3.0.0
git bisect bad bf0c5b1  # update to 502.0.0
# Run `npm test` to see if our tests fail
# If they fail - run `git bisect bad`
# If they pass - run `git bisect good`
# When done, reset via `git bisect reset` & patch the bug
```
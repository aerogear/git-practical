# Hooks

* Hooks are stored in `.git/hooks/` in your repo
* Hooks can be scripts in any language, and can run any programs available on the system

## View samples
```bash
$ cd .git/hooks/
# To view a list of sample hooks
$ ls
# To view the pre-commit example hook
$ less pre-commit.sample
```
## Build our own hook
```bash
# Create a pre-commit file
$ touch pre-commit
# Open file in vi or editor of choice 
$ vi pre-commit
```
Now we will add a simple bash script to our pre-commit hook, which will return to us the current weather in Waterford. 
Copy the following script into the pre-commit hook
```bash
#!/usr/bin/sh
curl wttr.in/~Waterford
```
Now this hook will be triggered before we make a commit. Return to the _git-workshop_ directory where we will make a change to our _hello.txt_ file
```bash
# Make a change to hello.txt
$ echo 'I am going to trigger a hook' >> hello.txt
# Add hello.txt
$ git add hello.txt
# Commit hello.txt
$ git commit -m 'this should trigger a hook'
```
## More on Hooks
Hooks can be an extremely powerful tool for a developer. For more information refer to https://githooks.com/


# Next Section
[Under the Covers](./14-under-the-covers.md)
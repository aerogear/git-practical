# Config

Config is layered: system, global (user), local (repo)

```bash
# System
cat /etc/gitconfig

# Global (user)
cat ~/.gitconfig # or ~/.git/config

# repo-specific
cat ./.git/config
```

Set defaults for all your projects in ~/.gitconfig, either by editing the file directly, or by using the config subcommand. E.g.:

```bash
# Set a sane editor (otherwise uses value from $EDITOR)
$ git config --global core.editor emacs

# Set a custom commit message template
git config --global commit.template ~/.git-commit-template
```

Gerard's current ~/.git-commit-template file: https://git.io/vQJzx

Most interesting is the user's global config

```ini
[user]
	name = Gerard Ryan
	email = gerard@ryan.lt
	signingkey = 8A617903604095DC

[core]
	excludesfile = ~/.gitignore
	quotepath = false
	autocrlf = input
	safecrlf = warn
	editor = emacsclient -t -a emacs

[hub]
	protocol = ssh

[commit]
	template = /home/grdryn/.git-commit-template
	gpgsign = true

[gpg]
	program = gpg2
```

Aliases are really useful

```ini
[alias]
	br = branch
	co = checkout
	ci = commit -a
	d = diff --color-words
	st = status
	lol = log --graph --decorate --all --abbrev-commit --pretty=oneline
        lg = log --graph --all --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative
	scrub = !git reset --hard && git clean -fd
```

Lots of other useful aliases and config customization examples here:

https://github.com/matthewmccullough/dotfiles/blob/master/gitconfig

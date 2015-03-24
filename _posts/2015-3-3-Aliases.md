---
layout: post
title: Aliasing for easier use
---

First steps in order to provide GitHub your identity and make your commits prettier, is to configure your name and email. You may simply do so by running the following command:

```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

Git config provides a wide range of options, which you may find [here](http://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

Now, let's add a few aliases for convenience

Under your home folder, there is a hidden file called `.gitconfig`. In this file you may set the following options simply by editing the file

```bash
$  vim ~/.gitconfig
[user]
        name = Fotis Alexandrou
        email = fotis@example.com
[alias]
        com = commit
        co = checkout
        br = branch
        st = status
        last = cat-file commit HEAD
        cloner = =
[color]
        ui = true
[core]
        quotepath = false
        excludesfile = /Users/Fotis/.gitignore_global
        editor = vim
        filemode = false
[merge]
        tool = vimdiff
```

Under `[aliases]` you see that we can now use shorter versions of git commands such as

```bash
$ git st # stands for "git status"
$ git co # stands for "git checkout"
```

There also are options for `excludesfile` which is the files that contains the patterns to ignore when commiting, and an option for `[merge]` which is the editor to use when resolving conflicts, but we'll discuss these matters later on
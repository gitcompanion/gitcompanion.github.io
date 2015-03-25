---
layout: post
title: Repositories, Remotes & cloning
---

A source code directory by itself is nothing. It needs to be maintained by several people, iterated, enhanced, cleaned up regularily in order for the software to be presentable to the user.

In order to transform your source code directory into a git repository you may just run

```bash
$ git init
```

This will create the `.git` directory on the top level and it will contain configuration for the repository, the repo history and hooks

After this point, we're ready to add a remote repository, which acts as the storage for our source code. GitHub has made it really easy for us to do so, simply by clicking `+ New Repository`. The repository will then be available and there will be an ssh url available to add as a remote. Remotes are aliases for urls where we can push our code to

```bash
$ git remote add origin git@github.com:falexandrou/thefotisbook.git
```

Of course we can name our remotes however we want, but the converntions are `origin` and `upstream`

We can add our files now, simply by running

```bash
$ git add --all
```

This will add all files under the current directory and this command can also be ran under a certain directory to include all files under that directory. Removing files can be accomplished with `git rm` and we can add or remove separate files by specifying the file's path.

If we wish to start over, we can simply

```bash
$ git reset
```

or if we need to temporarily remove our changes we can run

```bash
$ git stash
```

and then to bring them back we may

```bash
$ git stash pop
```

And there is also a `git rm` command in order to remove a file under a given path

We're now able to commit, to create a point in history where our code exists

```bash
$ git commit -m "This is my first commit"
```

Option `-m` means `message` and you may find many options available for commiting as well

We may now push our code to the remote repository, simply by running

```bash
$ git push origin master
```

This means that we pushed the `master` branch, default branch created to the `origin` remote, so our remote storage now contains our latest changes.

The commit is now represented by a unique `SHA1` hash referenced as commit hash or commit id

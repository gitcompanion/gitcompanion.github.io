---
layout: post
title: Ignoring files
---

There is a need to include certain files when commiting to repositories. For example, if your rails application creates a `development.log` file on your local environment, you certainly don't need to commit that.

There is also the need to provide global exclusions for files, for example MacOS `.DS_Store` files or Windows `Thumbs.db`, hence we need a global exclusion list

In order to define the global exclusion list, we can run

```bash
$ git config --global core.excludesfile ~/.gitignore_global
```

This will create a file `.gitignore_global` under our home directory, where we can start adding patterns that may be excluded

```bash
➜  ~  vim ~/.gitignore_global
.DS_Store
*.orig
```

As you can see we've excluded MacOS `.DS_Store` files and `*.orig` files which are the backup files that git creates after merging

The same functionality works within repositories themselves, only difference is that you need to name the file `.gitignore`

On the other hand, since for example empty directories are omitted, in order to keep a directory (eg. the directory structure for the logs directory, but not the log files themselves), we may add an empty `.gitkeep` file.

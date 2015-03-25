---
layout: post
title: Hooks and usages
---

Git also provides us hooks. These are command that can be run when taking certain actions. The commands are bash scripts which run every time the corresponding action is taken and reside under `.git/hooks`

```bash
$ ls .git/hooks
applypatch-msg.sample     post-update.sample        pre-commit.sample         pre-rebase.sample         update.sample
commit-msg.sample         pre-applypatch.sample     pre-push.sample           prepare-commit-msg.sample
```

You are now able to copy the `pre-commit.sample` file for example into just `pre-commit`, and alter its contents to perform actions before commiting. 

Hint: You can run scripting languages, for example `php` scripts in git hooks. Example

```bash
#!/usr/bin/php
<?php
echo "This is a php script";

```

The hooks are not commited since they are located under the `.git` directory, but they may as well be copied to a directory that is in fact being committed

A great example of hooks usage is the `GitHub` pages functionality (ie. this site) which it uses post-update hooks to locate changes in your Jekyll blog and re-build and publish it. More info on GitHub pages can be found [here](https://pages.github.com/)

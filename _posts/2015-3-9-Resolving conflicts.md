---
layout: post
title: Resolving conflicts
---

Everything comes with a price. You can't collaborate with your colleagues without conflicts, neither in real life nor in the wonderful world of git. Sometimes when the same snippet of code is changed in two different branches for example, git is not able to auto-merge the file and ends up with a conflict.

Resolving a conflict requires a tool. By default git uses a command line editor for example `vim` (`vimdiff`), `emacs` or nano.

```bash
$ git merge origin/master
CONFLICT (add/add): Merge conflict in views/item.rb
Auto-merging src/less/list.less
CONFLICT (content): Merge conflict in src/less/controllers/job/list.less
```

We then need to merge conflicts in our editor by running:

```bash
$ git mergetool
```

And walking through each file separately. There are visual tools that one may achieve conflict resolution such as `meld`, `opendiff` etc but here we'll view conflict resolution via the command line

```bash
$ git mergetool
Normal merge conflict for 'views/item.rb':
  {local}: modified file
  {remote}: modified file
Hit return to start merge resolution tool (vimdiff):
```

We then need to search for `<<<<<<< HEAD` enries and use the tool to resolve conflicts that look something like this:

```
<<<<<<< HEAD
<div>
    <a href="#" class="btn">Test Button</a>
=======
    <a href="#" class="different-class">What a Button!</a>
>>>>>>> origin/master
```

The key here is to remain calm and resolve all conflicts in a way that doesn't break our code base.

Please note, that if the conflict resolution is not successful, `git` will try to ask our confirmation on whether to continue with merging unresolved paths

```
Was the merge successful? [y/n] n
merge of views/item.rb failed
Continue merging other unresolved paths (y/n) ?
```

At this point, git will have created backup files of our merge attempt, which can be removed by running the following command in our repository root

```bash
find ./ -name *.orig | xargs rm
```

Or, if you wish to use more drastic measures, you may configure your git client to automatically remove backup files after each merge as follows:

```bash
git config --global mergetool.keepBackup false
```
---
layout: post
title: Manipulating history, Squashing & Rebasing
---

Merging to `master` can be achieved either by pull requests or by merging locally. This usually encourages developers to also perform local `git merge` of the remote branches, creating a so-called "merge commit", which when pushing and comparing to the base branch is visible and kind of redundant. This is just one of the many cases where manipulating your branch's history might seem handy.

Another case is when we need to "compress" all the commits we were working on for quite a long time, into a single commit. This subject is fairly controversial where some developers think one should never manipulate their history and merge all commits they have ever created on the base branch. Personally, i find `squashing` or `rebasing` (ie. sumarizing a set of commits into one commit by removing intermediate commits) very useful and my main argument around it, is that when one is trying to figure out what a piece of code does, they usually ending up doing `git blame` in order to find out the commit that this change was initially introduced. When working on feature branches and you need to see the entire commit that a feature was introduced (in order to get a clearer image of what is going on), it may be useful if all commits are sumarized as one. It wouldn't be very convenient if for example one should go through a set of 35+ commits where some of them could be typo fixing; they would have to go through the parent commits or the merge commit that the branch was introduced. Another argument pro-squashing would be the ability to revert only 1 commit if something goes wrong (although GitHub now provides an awesome "revert" button).

Squashing might be the simplest for of manipulating history and a typical flow would be i) checking out a branch from the base branch, 2) squash-merging the topic branch 3) commit changes for example:

```bash
$ git checkout upstream/master -b my-squashed-branch
$ git merge --squash --no-commit my-non-squashed-branch-with-a-billion-commits
$ git commit -m "I just added a billion commits as one"
```

Now the branch should be 1 commit ahead of the `upstream/master` branch.

Another form of manipulating the branch's history would be `git rebase` where the developer is able to pick, squash or omit all the commits that are not included when comparing the current with the base branch; For example

```bash
$ git rebase -i upstream/master
```

This would open up an editor, where the developer can perform the specific actions
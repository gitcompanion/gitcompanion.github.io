---
layout: post
title: Branches
---

Branches are the core essence of git. A branch can be a bug fix, a new feature or a separate environment and can be created via a base branch or a base commit. Here's how to create branches

```bash
$ git checkout origin/master -b my-topic-branch # creates a branch

$ git branch # lists the branches
  master
* my-topic-branch
```

We can switch branches by checking them out and we can also manipulate them as follows:

```bash
$ git branch -m my-new-branch-name # renames the branch
$ git branch -D my-old-branch # deletes the "my-old-branch"
```

Branches can be merged to one another simply by running:

```bash
$ git branch # list our branches
  master
* my-topic-branch

$ git checkout master # checkout the master branch
$ git merge my-topic-branch # merge the "my-topic-branch" to master
$ git push origin master # push to remote repository
```

We don't always have to merge locally, we can submit and create pull requests directly on GitHub and merge, create discussions around them and then be merged by repository collaborators.

Pro-tip: IF by any chance you've got a change set which is not included in the main branch, you can use `chery-pick` to add the specific commit. Example:

```bash
$ git branch
 * accidental-branch-i-commited-to
   correct-branch
   master
$ git checkout correct-branch
$ git show accidental-branch-i-commited-to
... abcdef123123435abcdfg # get the commit sha
$ git cherry-pick abcdef123123435abcdfg
```




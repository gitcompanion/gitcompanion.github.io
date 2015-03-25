---
layout: post
title: Tips n tricks
---

Here are a few quick tips n tricks to impress your friends with:

#### Search for a commit, even inside a deleted branch

```bash
$ git log -g --grep=search_for_something
```

#### Create tags / releases

```bash
$ git tag -am <message> <version>
$ git push --tags
```

#### Typo on last commit? No problem

```bash
$ git commit --amend
```

will let you edit your latest commit message

#### Throwing away ALL changes (WARNING: YOU MAY LOSE YOUR WORK - YOU DIDN'T LEARN THAT FROM ME. OK? OK! THX)

```bash
$ git reset --hard
```

#### Find out when a file was deleted

```bash
$ git log -1 -- views/deleted_file.rb

commit 25345bbed8f37ab5781475006a1cb8199821c19a
Author: falexandrou <fotis@example.com>
Date:   Tue Feb 3 18:16:29 2015 +0200

    remove an unused file
```

#### Restore a file that was deleted

Get the commit that the file was deleted (shown above)

```bash
git checkout 25345bbed8f37ab5781475006a1cb8199821c19a^ -- views/deleted_file.rb
```

Mind the `^` in the commit hash. This means we're restoring the latest revision of the file 1 commit before the commit that deleted the file

#### List and/or clear all items in git stash

```bash
$ git stash list
$ git stash clear
```


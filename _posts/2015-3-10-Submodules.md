---
layout: post
title: Submodules
---

Although nearly all modern programming languages use a package managers, there still is a need to create a git repository inside another. That's where `git submodule` comes in hand.

To add a submodule you simply need the module's ssh url and run the following command:

```bash
$ git submodule add <remote url> <local path>
```

for example

```bash
$ git submodule add git@github.com:falexandrou/devbox.git examples/devbox
```

Then run

```bash
$ git submodule update --init
```

in order to fetch the latest revision and clone the submodule to the local path.

After this point, there is a separate git repository under `examples/devbox` where you can `fetch`, `commit`, `push`, `merge` separately. The submodule then would be modified under root directory and `git diff` would show us the submodule's commit change. Example

```bash
$ git diff
diff --git a/examples/devbox b/examples/devbox
index 7899ee3..2132b9a 160000
--- a/examples/devbox
+++ b/examples/devbox
@@ -1 +1 @@
-Subproject commit 7899ee3a99bbe783082bd4648172b627ab480be3
+Subproject commit 2132b9a64372d46abf3b5e92c07b71b825bdd8cd
```

You may also have multiple levels of nesting in git submodules (ie. submodule inside a submodule) and can be initialized or updated with the `--recursive` option.

There are a few more commands available for us to run for example

```bash
$ git submodule sync
```

where you can reset the submodule's remotes and use what's defined as the module's base url.

Please bear in mind that submodules commands are only available on the repository's root level.

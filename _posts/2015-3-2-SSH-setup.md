---
layout: post
title: SSH Setup
---

When dealing with remote repositories, Git uses SSH to connect to the remote repository in a secure way. In order to use SSH painlessly, we should create SSH keys so that the authentication credentials are not requested every time we ned to access git. There is an option for HTTPS authentication but that would require entering your password each time you need to submit an action to the remote repository.

Hit up your favorite terminal and run `ssh-keygen` and follow the steps

```bash
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/fotis/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/fotis/.ssh/id_rsa.
Your public key has been saved in /Users/fotis/.ssh/id_rsa.pub.
...

```

SSH key is now added under your home path and there are two versions of it. One is the private key, which is for your eyes only and second is the public key which we will add to GitHub. View its contents by running:

```bash
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3Nz......
...... fotis@git-trainer.com
```

copy the output of the key and paste it to GitHub under [your account's settings](https://github.com/settings/ssh) (Add new key)

Test your connectivity by running
```
$ ssh -T git@github.com
Hi falexandrou! You've successfully authenticated, but GitHub does not provide shell access.
```

If you got a friendly greeting message, you're ready to go

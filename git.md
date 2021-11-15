# Using git and Github

This script is just another how-to for git and GitHub. First, make sure you
installed git (either manually or using `brew`) and signed up for GitHub. If
so, we can set up your user account. 

But let me tell you first, what git actually is. Git is a revision control
system. The concept is straightforward: You edit a file and track what you
edited. Afterward, you often push your previously made changes to a repository.
Think of a repo(-sitory) as a box. 

That's enough terminology to get you going. Git is a sophisticated tool and its
terminology is even more so. I don't want to dampen enthusiasm by overloading
things with terminology. It will come along the way. Instead, let's jump right
into practice!

## Git

Before we can control revisions using git, we have to tell it your user mail
and your name. Thus, we have to setup the global user and assign him/her an
email address.

## Set up the global user 

```
git config --global user.name "foo bar"
git config --global user.email "foo@bar.com`
```

---

## Additionals

```
$ git config --global color.ui true
$ git config --global core.editor nvim
```

---

## Github

Test if you are account is recognized on Github

```
ssh -T git@github.com
```

if not copy your public key an github using either... or... and retest

```
pbcopy < ~/.ssh/id_rsa.pub
# ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```
---

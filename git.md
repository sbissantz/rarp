# Using git and GitHub

This script is just another how-to for git and GitHub. First, make sure you
installed git (either manually or using `brew`) and signed up for GitHub. If
so, we can set up your user account. 

But let me tell you first, what git actually is. Git is a revision control
system. The concept is straightforward: You edit a file and track what you
edited. Afterward, you often push your previously made changes to a repository.
Think of a repo(-sitory) as a box. 

That's enough terminology to get you going. Git is a sophisticated tool and its
terminology is even more so. I don't want to dampen enthusiasm by overloading
things right now. It will come along the way. Instead, let's jump right into
practice!

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

Two other settings proved to be handy (at least for me). The first one
generates a (more) colorful output. The second one sets your default editor. I
love doing things the (n)vim way. But feel free to use a different editor
(e.g., Nano, Emacs, etc.).  If the international scientific term for confusion
pops up in your skull -- WTF?! --  You might ask what a text editor is. More
precisely, we're talking about a text editor. Literally speaking, it is a 'tor'
to edit text. Whatever a 'tor' may be. If the term is still not
self-explanatory for you (as it wasn't for me), think of it as MS Word for
plain text files. So why not use MS Word instead? Well, the simple answer
is: you're a reborn nerd! Nerds don't use MS Office -- so shhh!

```
$ git config --global color.ui true
$ git config --global core.editor nvim
```

---

## Github

Now it's time to sign up for GitHub (or, to name an alternative, 'BitBucket').
On the website, click your picture, navigate to 'settings' and select 'SSH and
GPG keys'.  Click on 'new SSH key' and paste (Cmd + V) the output of the
following command:

```
pbcopy < ~/.ssh/id_rsa.pub
```

If this does not work (or if you have to specify a server) try...

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```

## Test

Now it's time to make sure GitHub knows you. I call it the Saturday night club
bouncer test. Do you gain access to the party?

```
ssh -T git@github.com
```

Yaaay! Success. Time to party!

```
Hi sbissantz! You've successfully authenticated, but GitHub does not provide shell access.
```
---

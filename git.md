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

## Using git and GitHub

Please note --right off the start-- the following introduction is a shorty.
It won't tackle the topic with full strength. Instead, the tutorial presents
git in a nutshell. You should be able to jump right off the ground. Nothing
more than that! Alright, so let's get started.


To control your revisions, you need something substantial. Let's say a
directory. Because we are reborn nerds, we use the terminal. Hands off the
mouse folks! Press <command> and <space> and type "terminal". Then type:

```
mkdir -p test_dir ; cd test_dir
```

The snippet creates a directory (`mkdir`) and made it your current working
directory (`cd`).  Double-check with `pwd` which is the instruction to print
working directory. The command should spit out something like
`Users/username/test_dir`.

```
pwd
```

Now it's time to create a repository.  You can talk to Robert (your computer
servant) very definitely: 'Robert, use git to initialize a repository' becomes:

```
git init
```

If Robert mentions something like `Initialized empty Git repository in
/Users/<username>/test_dir/.git/` you are good to go.

---

[...in progress]

Now let's create a bunch of files. 'touch' is your friend. Equipping him with
brace expansion characters allows him to multiplicate the result. So we get
nine test files.

```
touch test_{1..9}
```

´```
echo "I am a test" >> test{1..9}"
```

```
cat "I am a test" >> test{1..9}"
```













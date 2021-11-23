# Using git and GitHub

This script is just another how-to for Git and GitHub. First, make sure you
installed Git (either manually or using `brew`) and signed up for GitHub. If
so, we can set up your user account. 

But let me tell you first, what git actually is. Git is a revision control
system. The concept is straightforward: You edit a file and track what you
edited. Afterward, you often push your previously made changes to a repository.
In simple terms, a repository is more or less a box to store scripts. 

All right, that's enough terminology to get you going. Git is a sophisticated
tool and its terminology is even more so. I don't want to dampen enthusiasm by
overloading things with terminology right now. It will come along the way.
Instead, let's jump right into practice!

## Git

Before we can control revisions using Git, we have to tell it your user mail
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
pops up in your skull -- WTF?! -- you might ask "what the hell is an editor?".
Well, more precisely, we're talking about a text editor. Literally speaking, it
is a 'tor' to edit text. Whatever a 'tor' may be. If the term is still not
self-explanatory for you (as it wasn't for me), think of it as MS Word for
plain text files. So why not use MS Word instead? Well, the simple answer is:
you're a reborn nerd! Nerds don't use MS Office -- so shhh!

```
$ git config --global color.ui true
$ git config --global core.editor nvim
```

---

## Github

Now it's time to sign up for GitHub (or, to name an alternative, 'BitBucket').
Done? Great, then we can move on. As part of good practice we'll use GitHub
with SSH. If you haven't set up SSH already, read the instructions in `ssh.md`
and joint afterwards. 

Let's start rollin'! We start the journey by getting GitHub to know your
account. If you remember the `ssh.md` story, its now time to exchange phone
numbers. Therefore, go to the GitHub website, click on your picture, navigate
to 'settings' and select 'SSH and GPG keys'. Choose 'new SSH key' and paste
(Command + V) the output of the following command:

```
pbcopy < ~/.ssh/id_rsa.pub
```

If this does not work (or if you have to specify a server) try...

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```

## Test

Now it's time to testify that GitHub knows who you are. Once more, if you
remember the `ssh.md` story its like testing that Stacy gave you the correct
number. So let's write her a short message. For those of you, who don't know
the romantic story -- think of the following step as the Saturday night club
bouncer test: Do you gain access to the party?

```
ssh -T git@github.com
```

Yaaay! Success. Time to party!

```
Hi <username>! You've successfully authenticated, but GitHub does not provide
shell access.
```
---

## Using git and GitHub

Please note --right off the start-- the following introduction is a shorty.
It won't tackle the topic with full strength. Instead, the tutorial presents
Git in a nutshell. You should be able to jump right off the ground. Nothing
more than that! With this in mind, let's get started.

To control your revisions, you need something substantial. Let's say a
directory. Because we are reborn nerds, we use the terminal. Hands off the
mouse folks! Press and hold <command> and tap <space>. If you see the Spotlight
Search type "terminal". If you face the scary dark black hole and the bright
light shining prompt enter:

```
mkdir -p test_dir ; cd test_dir
```

The snippet creates a directory (`mkdir`) and made it your current working
directory (`cd`).  Double-check with `pwd` which is the instruction to print
the current working directory. Robert (your computeralized servant) should spit
out something like `Users/<username>/test_dir`.

```
pwd
```

Now it's time to create a repo(sitory). You can talk to Robert very definitely:
'Robert, use git to initialize a repository'. In codeish:

```
git init
```

If Robert mentions something like `Initialized empty Git repository in
/Users/<username>/test_dir/.git/` you are good to go.

---

Great! Time to bring `test_dir` to life. We'll first create a bunch of files.
`touch` will be your friend. Equipping him with brace expansion characters
allows him to multiplicate the result. Its like giving him the power ranger
magic sword: one command -- nine test files.

```
touch test_{1..9}
```

Boom! No sooner said than done. But look; all those files are empty: 

```
cat test_{1..9}
```

To track changes, we need to produce content. But you don't want to edit each
of the nine files manually, right? Robert is loyal. He will help. If you ask
him to write (`echo`) a few words (`"I am a test"`) in all those files
(`test_{1..9}`), he will certainly lend you a hand with it.

```
echo "I am a test" >> test_{1..9}"
```

To prove that Robert kept his word, click the up arrow two times or type:

```
cat test_{1..9}
```

All right, now its time to commit your initial changes to all those files and
push them to GitHub.

```
git commit -m "Initial commit"
```

Usually, you should be a bit more precise when documenting your changes! But
for the sake of understanding the Git way of doing things, the snippet
suffices. If you want to nuancly pin down all the new cool features you've
implemented, make sure to restrict yourself to 80 characters and type `git
commit`. `git commit` will start your previously defined editor (nvim, emacs,
atom,...). Why 80 characters?  Well, 80 is arbitrary. But it is a good rule of
thumb: If you cannot outline the changes you made within 80 characters, you
probably changed too much. Get used to committing smaller junks of code more
often. The tip might prevent you from some ugly merging conflicts and
contributes to a harmonic multi user workflow on large, difficult projects.


All right, time to push!



Oh no! We forgot to set up a remote repository. 

```
git log | grep "commit"
```

You only need the first 10 characters of the hash tag to refer to this commit.

```
git config format.pretty oneline
```

```
git add -i
```

## Epilogue

Goody:

```
brew install --cask github
```




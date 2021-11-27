# Using git and GitHub

This script is just another how-to for Git and GitHub. Before you start, please
make sure you installed Git (either manually or using `brew`) and signed up for
GitHub (or BitBucket). If so, we can set up your user account. 

Alright! Prior to our hands-on tutorial, let me lose a few words about Git.
Git is a revision control system. The concept is straightforward: You modify a
file and document the changes. After a while you'll have a full-blown
documentation of the development process the file went through. Why should you
care? In short, Git is checksummed! It documents every change in file content
and labels it. It is like the best filing cabinet you'll ever have.  You can't
loose a state of your development process because some version of it will be
stored somewhere (a Git file in .git). Once you committed a change, you can't
loose. In addition, others can contribute to your textualized thoughts, moods
and feelings and their commited ideas are also labeled and stored. You guys can
go wild and Nanny McGit will clean up the rubble.

Now you know what Git is. But there is one additional concept I want to leave
you with, before we let of steam: the Remote Repository. In simple terms, a
remote repository is more or less a box to store scripts online. More
specifically, it is a stream of versions of your project which are hosted
"in-" or online. That's enough terminology to get you going. Git is a
sophisticated tool and its terminology is even more so. I don't want to dampen
enthusiasm by overloading things with terminology right now. It will come along
the way.  Instead, let's jump right into practice!

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
push them to GitHub. However, before your can commit your changes, you have to
stage them. In the Git this is associated with the `ÌNDEX`.  The `INDEX` is the
staging area for all commits. This is were all commits reside before they are
pushed to the remote repository. The last commit is indicated by `HEAD` the
pointer to your last commit. All this terminology must sound wired; so lets
embed them in a story to get the concept right. 

Think of the process (committing a change) as you traveling to Zurich by train.
You obviously embody a commit. If you want to leave Landau (the working
directory) to travel to Zurich (the location of the remote repository) you go
to the railroad station (staging area). Others (commits) do so as well. So the
station is kind of an assembly point for all of you (`ÌNDEX`) . When the train
(the push command) enters the station its time to leave. 4 hours later you'll
arrive at Zurich (changes commited). Side note: I hope your internet connection
will make it earlier..

The story is ridiculous -- I know -- but hopefully you know what to do next
(before pushing local changes). Yes? Well, then the story has served its
purpose. No? ..just go ahead. 

```
git add "test_1"
```

All right, you(r commit) can't wait to get off. So lets buy him a ticket:

```
git commit -m "Ticket to Zurich"
```

Usually, you should not ulk arround with commit messages. Be as precise as you
can when documenting your changes! But for the sake of understanding the Git
way of doing things, the snippet suffices. 

However, if you want to nuancly pin down all the new cool features you've
implemented, make sure to restrict yourself to 80 characters and type `git
commit`. `git commit` will start your previously defined editor (nvim, emacs,
atom,...). Why 80 characters?  Well, 80 is arbitrary. But it is a good rule of
thumb: If you cannot outline the changes you made within 80 characters, you
probably changed too much. Get used to committing smaller junks of code more
often. The tip could prevent you from some ugly merging conflicts and
contributes to a harmonic multi user workflow on large, difficult projects.

#
# STOP
#

All right, time to push!? Nope.. We first have to set up a remote repository
and define its location (no its not Zurich; most of the time its an URL).

What this means is, we to create the destination folder for the files
to push. Because our third party application is GitHub, navigate to the
website. On the website click `Repositories` then `New`. Give it a cool name
and `Create repository`. Time to return to your command line. After setting up
the destination folder we need to tell it Git. We'll use the following formula:

```
git remote add origin git@github.com:<username>/<cool_repo>.git
```

In my case the formula transforms to:

```
git remote add origin git@github.com:sbissantz/test_dir.git
```

Double check it with:

```
git remote -v
```

The command `git remote -v` should return something like `origin
git@github.com:sbissantz/test_dir.git (fetch)` and `origin
git@github.com:sbissantz/test_dir.git (push)`. Making a long story short, the
remote repo at GitHub is now the middle of your file solar system. It the
`òrigin` to be more precise. For the sake of completeness, the folder were your
files are at the moment is associated with your (local) master branch. Time to
push? Well, keep cool young padawan! We're going to initiate the push right
now...

In a Nutshell:

```
git push -u 

git add . ; git commit -m "inital commit" ; 
```


As I said, git is a revision control system. So first we need to stage the
files. Therefore we carry the files to a staging area, aka the `INDEX`. Think
of the staging area as a place were all commits resides before the changes















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




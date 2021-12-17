# Using git and GitHub

This script is just another how-to for Git and GitHub. Before you start, please
make sure you installed Git. Open a terminal (`Command` + `Space`, "terminal")
and fire `git --version` in the black hole. Robert should answer with a version
number, e.g.: `git version 2.33.1`. If he tells you `command not found...`
install it either manually or using `brew install git`. What else? Ah, you
should sign up for GitHub ..or Bitbucket ..or any other service to host your
code, (plain) text files, etc. Whenever `git --version` returns a number, we
are ready to go.

Before our hands-on tutorial, let me lose a few words on Git. Git is a revision
control system. The concept is straightforward: You modify a file and document
the changes. After a while, you'll have full-blown documentation of the
development processes the file went through. Why should you care? In short, Git
is checksummed. It documents every change in file content and labels it with a
hash. It is like the best filing cabinet you'll ever have. You can't lose a
state of your development process because some version of it will lay around
somewhere (online, a friends machine, your Git file in .git ...). In short:
Once you commit a change, it's hard to lose it. Distributed version control &
Git's checksumming nature will take care of. More on this in a moment.  In
addition, the Gitverse makes it easy for others to contribute to your
textualized thoughts, moods, and feelings. Their committed ideas are also
labeled and stored. You guys can go wild and Nanny McGit will clean up the
rubble!

Now you know what Git is. But there is one additional concept I want to leave
you with: the Remote Repository. In simple terms, a remote repository is a box
to store scripts online. Specifically, it is a stream of versions of your
project which are hosted "in-" or online. Alright, enough terminology for the
moment. Git is a sophisticated tool and its terminology is even more so. I
don't want to dampen enthusiasm by overloading things with explanations right
now. It will come along the way. Instead, let's jump right into practice!

## Git

Time to set up your account. Before you can control revisions, Git wants to
know, who you are. More specifically, it wants your user mail and your name.
Technically speaking, we have to setup the global user and assign him/her an
email address.

```
git config --global user.name "foo bar"
git config --global user.email "foo@bar.com`
```

---

Two other settings proved to be handy options (at least for me). The first one
generates a (more) colorful output. Then you set your default editor.  For
example, I love doing things the (n)vim way. But feel free to use whichever you
like (e.g., Gedit, Nano, Emacs, etc.). In my experiences, however, friends of
Windows, macOS, and companions, do rarely ever stumble across one of these
editorial workhorses. The main reason is a lack of interest in fiddling with
system files, check?

However, since you are successively becoming a nerd, you start gaining interest
in hackers' vocabs, right? So then. A text editor is simply a neat tool to edit
plain text files. It is like a slimmed-down fast version of MS Office for
system files. It omits almost all conveniences for the sake of speed and low
storage. Well, expect you fell in love with Emacs (as I did years ago). But
that is another story. 

The last global configuration manipulates the output `git log`. If you wanna
know what commit logs are type `git help log` or page down a while (Note: Maybe
this part of the tutorial isn't written yet).

```
$ git config --global color.ui true
$ git config --global core.editor nvim
$ git config --global format.pretty oneline
```

---

To complete the global setting procedure, we want to make sure we are ready to roll. To check everything is set up nicely type:

```
$ git config --list 
```

You can read the snippet very literally: "Git, return a list of my
configurations". Your silicon servant will return `color.ui=true`,
`core.editior=nvim`... and many more. Alright, let's get cracking.

---

### Summary

Time to summarize the most important commands of our section. Note If you wanna
know more about a Git command type `git` verb `help`. For example, if you want
to get help on `git config` enter: `git help config`. You can type `man
git-config`, too. Just make sure to add a dash (`-`). 

| command (snippet) | Description |
| ----------- | ----------- |
| `git config --global user.name "foo bar"`  | Set your user name globally (i.e., for all projects |
| `git config --global user.email "foo@bar"` | Set your email address globally (i.e., for all projects) |
| `git config --list`                        | Show a list of all configurations |

---

## GitHub

Did you already sign up for a GitHub account? ...to use any of its mates is
also fine. Yes? Great!  In the following, I'll stick with GitHub. But once you
understand the general strategy, you can easily adapt any snippet to run with,
let's say, BitBucket. I really prefer its philosophy over GitHub's, but (once
more) this is another story.  We want to dive into practice now! 

As part of good practice, we'll use GitHub with SSH. If you haven't set up SSH
already, read the instructions in `ssh.md` and joint afterward. Alright, Let's
start rollin'! We begin the journey by transferring your public key to your
GitHub profile. If you remember the `ssh.md` story, it's now time to exchange
phone numbers. Thus, navigate to the GitHub website, click on your picture,
select 'settings' and choose 'SSH and GPG keys'. Click 'new SSH key' and paste
(`Command` + `V`) the output of the following command:

```
pbcopy < ~/.ssh/id_rsa.pub
```

If the command does not work (or if you have to specify a server) try...

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```

---

## Test... 1,.. 2,.. 1, 2, 3

Time to testify that GitHub knows who you are. Remember the Clemens Stacy love
story in `ssh.md`? Scene 3: Clemens makes sure Stacy gave him the correct
number. So let's write her a short message. Hint: For those of you, who don't
know their romantic story -- think of the following step as the Saturday night
club bouncer test: Do you gain access to the party (GitHub knows you)?

```
ssh -T git@github.com
```

The bouncer answers:

```
Hi <username>! You've successfully authenticated, but GitHub does not provide
shell access.
```

Alright, Maschomei knows us. Damn! It's a private party..Never mind, we have no
time to party anyway. We gotta continue setting up Git. But this time we know
for certain (a) SSH is working and (b) GitHub knows who we are. 

---

## Using git and GitHub

Please note --right off the start-- the following introduction is a shorty.  It won't tackle the topic with full strength. Instead, the tutorial presents Git in a nutshell. You should be able to jump right off the ground. Nothing more than that! With this in mind, let's get started.

---

### T-t-terminal, terminal!

To control your revisions, you need something substantial. Let's say a
directory. Because we are reborn nerds, we'll use the terminal, Hands off the
mouse folks! Press and hold `command` and tap `space`. If you see the Spotlight
Search type "terminal" (omit quotes). If you face the scary dark black hole and
the bright light shining prompt enter:

```
mkdir -p test_dir ; cd test_dir
```

The snippet creates a directory (`mkdir`) named (`test_dir`) and made it your current working
directory (`cd`). Double-check with `pwd` which is the instruction to print the
current working directory. Robert (your silicon servant) should spit out
`Users/<username>/test_dir`.

```
pwd
```

Now it's time to create a repo(sitory). You can talk to Robert very definitely:
'Robert, use git to initialize a repository. In code-ish, this reads as:

```
git init
```

If Robert mentions something like `Initialized empty Git repository in /Users/<username>/test_dir/.git/` you are good to go.

---

Cool! Time to bring `test_dir` to life. We'll first create a bunch of files.
`touch` will be our friend. Equipping him with brace expansion characters
allows us to multiplicate the result. It is like giving him the power ranger
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

---

### Summary

Time to summarize the section's most important commands. Note: Type `man` (for
manual) followed by a `command` to get more information about it. You can also
use `command --help` which prints the help site. For example, if you did forget
what the `touch` command does (or want to get additional info), ask Robert:
`man touch` or `touch --help`. 

| Command (snippet) | Description |
| ----------- | ----------- |
| `git init` | Initialize an empty git repository in the current directory |
| `touch`  | Creates an empty file |
| `mkdir baz`  | Make directory baz | 
| `pwd`  | Print the path of the current working directory | 
| `cat foo`  | Concatenate a print the content of the file `foo` | 
| `echo foo`  | Print the word `foo` to the screent | 

---

### Status? Check 1..2..3

You know dinner for one! "The same procedure as every year". Git is as repetitive as all birthday parties James went through over the years at Miss Sophies. You will see... But now, we'll zoom into her 90th birthday party you all know from television. Remember the most important procedure James has to repeat? The toast! The Git equivalent is `git status`. So before moving on to Sir Toby (when tracking files), Admiral von Schneider (after modifying files), Mr.  Pomeroy (when staging files), and Mr. Winterbottom (after committing files) you will toast (check `git status`). Miss Sophie admits! As I said: "The same procedure...!". Skål!...or...

```
git status
```

---

### Staging & committing 

All right, now it's time to commit your initial changes to all those files and
push them to GitHub. But wait! Before you are able to commit your changes, you
have to stage them. In Git this is associated with the `ÌNDEX`.  The `INDEX` is
also known as the staging area for all commits. This is where all commits
reside before they are pushed to the remote repository. More specifically it is
a Git file that knows what will be part of your next commit. Moreover, the last
commit is indicated by `HEAD`. Or, to put it another way, `HEAD` the pointer to
your last commit. All this terminology must sound wired; so let's embed them in
a story to get the concept right. 

Think of the process (committing a change) as you travel to Zurich by train.
You obviously embody a commit. If you want to leave Landau (the working
directory) to travel all the way down to Zurich (the location of the remote
repository) you gotta go to the railroad station (staging area). Others
(commits) do so as well. So the station is kind of an assembly point for all of
you (`ÌNDEX`) . When the train (the push command) enters the station its time
to leave. 4 hours later you'll arrive at Zurich (changes committed). Side note:
Hopefully your machine will make it earlier..

The story is ridiculous -- I know -- but hopefully, you know what to do next
(before pushing local changes). Yes? Well, if "staging" is your answer then the
story has served its purpose. No? ...just go ahead. 

```
git add test_1
```

All right, you(r commit) can't wait to get off. So let's buy it a ticket:

```
git commit -m "Ticket to Zurich"
```

Usually, you should not ulk around with commit messages. Be as precise as you
can when documenting your changes! But for the sake of understanding the Git
way of doing things, the snippet suffices. 

However, if you are like Nanny McGit (i.e., you want to nuancly pin down all
the new cool features you've implemented), make sure to restrict yourself to 80
characters and type `git commit`. `git commit` will start your previously
defined editor (nvim, emacs, atom,...). Why 80 characters?  Well, 80 is
arbitrary. But it is a good rule of thumb: If you cannot outline the changes
you made within 80 characters, you probably changed too much. Get used to
committing smaller junks of code more often. The tip could prevent you from
some ugly merging conflicts and contributes to a harmonic multi-user workflow
on large, difficult projects.

Let's sum up the ominous Git Workflow. Do you like fish-stick? Great, then you
know the MSC seal and got a mnemonic gratis. The 3 States are `(m)odified`,
`(s)taged`, and `(c)omitted`. You change something (modify), then you
start/continue to keep track of it (stage), and finally, you document what
you've changed (commit). That's all there is to it! Just Grrrrrr: Initialize a
(G)it repo and the rest is applying the (r)outine over and over
again..(r)outine (r)outine (r)outine (r)outine (r)outine (r)outine. The result
will be a well-documented development process your file(s) went through. Neat!

---

### Summary

Time to summarize the most important commands of the section. Note: If you
wanna know more about a Git command type `git` verb `help`. For example, if you
want to get help on `git config` type: `git help config`. You can type `man
git-config`, too. Just make sure to add a dash (`-`). 


| Command (snippet) | Description |
| ----------- | ----------- |
| `git add foo` |  Add the file `foo` to the staging area |
| `git commit -m "msg"` |  Document previous changes in `"foo"` with `"msg"` |

---

### Remotes and other spheres

All right, time to push!? Nope. First, we have to construe a shelter for your
files online: a remote repository. Besides, we have to indicate its location
(no it is not Zurich; most of the time it's an URL). So in advance, there are
two things two set up.

Since our third-party application is GitHub, navigate to the website. On the
website click `Repositories` then `New`. Give it a cool name and click `Create
repository`. Return to your command line. After setting up the destination
folder on GitHub, we need to tell it, git:

```
git remote add origin git@github.com:<username>/<cool_repo>.git
```

In my case, the formula transforms to:

```
git remote add origin git@github.com:sbissantz/test_dir.git
```

Double-check it with:

```
git remote -v
```

`git remote -v` should return something like `origin git@github.com:sbissantz/test_dir.git (fetch)` and `origin git@github.com:sbissantz/test_dir.git (push)`. To make a long story short, the remote repo at GitHub is now the middle of your file solar system. Literally, it is its `origin`. The solar metaphor is appropriate especially in terms of Gits' "nature". Git is a "distributed version control system" (DVCS). DVCSs distribute the content of the remote repository across multiple users. Everyone gets a physical (well rather "virtual" or "silicon") clone of the remote repository. Why is this helpful? Well, it has a lot in common with the principle of risk diversification in stock deals. Distributing the content across multiple instances minimizes the risk of a total fallout when a single unit dies. However, if you wanna be petty the metaphor is incorrect. Git does not require splitting the portfolio. It duplicates the whole instance instead.  Boom!

If the remote (repository) is set up correctly it's time to pu..pu..pu..push!
Cool, we're almost done. Don't get too nervous young padawan! Hold on tight and
enter (with a touch of coolness):

```
git push -u origin master
```

Once more, try to read the snippet very literally: "Git push my parked stuff
from my master branch to my origin (on GitHub). We won't fiddle around with the
`-u` option now. Setting upstream branches is a more advanced topic. 

But what is this `master` thing? Good question. In Git-ish `master` is the name
which is associated with your local folder (`test_dir`). More specifically, one
must add "with a specific version of..." (and other linguistic subtleties) --
but shhh! We don't want to be too petty -- for the sake of understanding. Let's
focus on the snippet instead. From the background of the latest insight, it
simplifies as follows: "Git push my staged stuff from my test_dir to its origin
(on GitHub). That's what we wanna do. If Robert trumpets out something weird
like...

```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 1.24 KiB | 1.24 MiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:sbissantz/rarp
a3433fc..108b6e1  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

...you finally made it. Congratulations!

---

### Summary

Time to summarize the most important commands of the section. Note: If you
wanna know more about a Git command type `git` verb `help`. For example, if you
want to get help on `git config` type: `git help config`. You can type `man
git-config`, too. Just make sure to add a dash (`-`). 

| Git command (snippet) | Description |
| ----------- | ----------- |
| `git remote add origin url` | Define `url` as the (new) origin for your stuff |
| `git remote -v` | List all remote repositories 
| `git push -u origin` | Push previous changes to the remote repository `origin` |

---




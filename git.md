# Using git and GitHub

This script is just another how-to for Git and GitHub. Before you start, please
make sure you installed Git. Open a terminal (`Command` + `Space`, "terminal")
and fire `git --version` in the black whole. Robert should answer with a
version number, e.g.: `git version 2.33.1`. If he tells you `command not
found...` install it either manually or using `brew install git`. What else?
Ah, you should sign up for GitHub ..or Bitbucket ..or any other service to host
your code, (plain) text files, etc. Whenever `git --version` returns a number,
we are ready to go.

Prior to our hands-on tutorial, let me lose a few words on Git. Git is a
revision control system. The concept is straightforward: You modify a file and
document the changes. After a while you'll have a full-blown documentation of
the development process the file went through. Why should you care? In short,
Git is checksummed. It documents every change in file content and labels it
with a hash. It is like the best filing cabinet you'll ever have. You can't
loose a state of your development process because some version of it will lay
around somewhere (online, a friends machine, your Git file in .git ...). In
short: Once you committed a change, its hard to loose it. Distributed version
control & Git's checksumming nature will take care. More on that in a moment.
In addition, the Gitverse makes it easy for others to contribute to your
textualized thoughts, moods and feelings. Their commited ideas are also labeled
and stored. You guys can go wild and Nanny McGit will clean up the rubble!

Now you know what Git is. But there is one additional concept I want to leave
you with: the Remote Repository. In simple terms, a remote repository is a box
to store scripts online. Specifically, it is a stream of versions of your
project which are hosted "in-" or online. Alright, enough terminology for the
moment. Git is a sophisticated tool and its terminology is even more so. I
don't want to dampen enthusiasm by overloading things with terminology right
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

## Additionals

Two other settings proved to be handy options (at least for me). The first one
generates a (more) colorful output. The second one sets your default editor. I
love doing things the (n)vim way. But feel free to use a different editor
(e.g., Gedit, Nano, Emacs, etc.). If you love the GUI way of doings thing, you
might have missed to stumble across this workhorse. A text editor is simply a
neat tool to edit plain text files. It is like a slimmed-down fast version of
MS Office for system files. It omits almost all conveniences for the sake of
speed and low storage. Well, expect you fall in love with Emacs (as I did years
ago). But that is another story..

```
$ git config --global color.ui true
$ git config --global core.editor nvim
$ git config --global format.pretty oneline
```

---

## Github

Let me start over with a question: Did you already sign up for a GitHub
account? To use any of its companions is also fine. Yes? Great! In the
following, I stick with GitHub. Note: Once you understand the general strategy,
you can easily adapt any snippet to run with, let's say, BitBucket. I really
prefer its philosophy over GitHub's, but (once more) this is another story.
We want to dive into practice now! 

As part of good practice we'll use GitHub with SSH. If you haven't set up SSH
already, read the instructions in `ssh.md` and joint afterwards. Alright, Let's
start rollin'! We begin the journey transferring your public key to your GitHub
profile. If you remember the `ssh.md` story, its now time to exchange phone
numbers. Thus, navigate to the GitHub website, click on your picture, select
'settings' and choose 'SSH and GPG keys'. Click 'new SSH key' and paste
(`Command` + `V`) the output of the following command:

```
pbcopy < ~/.ssh/id_rsa.pub
```

If this does not work (or if you have to specify a server) try...

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```

## Test

Time to testify that GitHub knows who you are. Remember the Clemens Stacy love
story in `ssh.md`? Scene 3: Clemens makes sure Stacy gave him her correct
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

Alright, Maschomei knows us. Damn! Its a private party..Nevermind, we have no
time to party anyway. We gotta continue setting up Git. But this time we know
for certain (a) SSH is working and (b) GitHub knows who we are. 

---

## Using git and GitHub

Please note --right off the start-- the following introduction is a shorty.
It won't tackle the topic with full strength. Instead, the tutorial presents
Git in a nutshell. You should be able to jump right off the ground. Nothing
more than that! With this in mind, let's get started.

To control your revisions, you need something substantial. Let's say a
directory. Because we are reborn nerds, we'll use the terminal, Hands off the
mouse folks! Press and hold `command` and tap `space`. If you see the Spotlight
Search type "terminal" (omit quotes). If you face the scary dark black hole and
the bright light shining prompt enter:

```
mkdir -p test_dir ; cd test_dir
```

The snippet creates a directory (`mkdir`) and made it your current working
directory (`cd`). Double-check with `pwd` which is the instruction to print the
current working directory. Robert (your silicon servant) should spit out
`Users/<username>/test_dir`.

```
pwd
```

Now it's time to create a repo(sitory). You can talk to Robert very definitely:
'Robert, use git to initialize a repository'. In code-ish this reads as:

```
git init
```

If Robert mentions something like `Initialized empty Git repository in
/Users/<username>/test_dir/.git/` you are good to go.

---

Cool! Time to bring `test_dir` to life. We'll first create a bunch of files.
`touch` will be our friend. Equipping him with brace expansion characters
allows us to multiplicate the result. Its like giving him the power ranger
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

### Staging & committing 

All right, now its time to commit your initial changes to all those files and
push them to GitHub. But wait! Before your can commit your changes, you have to
stage them. In the Git this is associated with the `ÌNDEX`.  The `INDEX` is the
also known as the staging area for all commits. This is were all commits reside
before they are pushed to the remote repository. More specifically it is a Git
file which knows what will be part of your next commit. Moreover, the last
commit is indicated by `HEAD`. Or, to put it another way,`HEAD` the pointer to
your last commit. All this terminology must sound wired; so lets embed them in
a story to get the concept right. 

Think of the process (committing a change) as you traveling to Zurich by train.
You obviously embody a commit. If you want to leave Landau (the working
directory) to travel all the way down to Zurich (the location of the remote
repository) you gotta go to the railroad station (staging area). Others
(commits) do so as well. So the station is kind of an assembly point for all of
you (`ÌNDEX`) . When the train (the push command) enters the station its time
to leave. 4 hours later you'll arrive at Zurich (changes committed). Side note:
Hopefully your machine will make it earlier..

The story is ridiculous -- I know -- but hopefully you know what to do next
(before pushing local changes). Yes? Well, if "staging" is your answer, than
the story has served its purpose. No? ...just go ahead. 

```
git add "test_1"
```

All right, you(r commit) can't wait to get off. So lets buy it a ticket:

```
git commit -m "Ticket to Zurich"
```

Usually, you should not ulk arround with commit messages. Be as precise as you
can when documenting your changes! But for the sake of understanding the Git
way of doing things, the snippet suffices. 

However, if you are like Nanny McGit (i.e., you want to nuancly pin down all
the new cool features you've implemented), make sure to restrict yourself to 80
characters and type `git commit`. `git commit` will start your previously
defined editor (nvim, emacs, atom,...). Why 80 characters?  Well, 80 is
arbitrary. But it is a good rule of thumb: If you cannot outline the changes
you made within 80 characters, you probably changed too much. Get used to
committing smaller junks of code more often. The tip could prevent you from
some ugly merging conflicts and contributes to a harmonic multi user workflow
on large, difficult projects.

Let's sum up the uminous Git Workflow. Do you like fish stick? Great, than you
know the MSC seal and got a mnemonic gratis. The 3 States are `(m)odified`,
`(s)taged`, and `(c)omitted`. You change something (modify), then you
start/continue to keep track of it (stage), and finally you document what
you've changed (commit). That's all there is to it! Just Grrrrrr: Initialize a
(G)it repo and the rest is applying the (r)outine over and over
again..(r)outine (r)outine (r)outine (r)outine (r)outine (r)outine. The result
will be a well documented development process your file(s) went through. Neat!

### Remotes

All right, time to push!? Nope.. First, we have to construe an shelter for your
files online: a remote repository. Besides, we have to indicate it location (no
its not Zurich; most of the time its an URL). So in advance there are two
things two set up.

Since our third party application is GitHub, navigate to the website. On the
website click `Repositories` then `New`. Give it a cool name and click `Create
repository`. Return to your command line. After setting up the
destination folder on GitHub, we need to tell it git:

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

#
# Stop
#

`git remote -v` should return something like `origin
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




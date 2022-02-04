# Command reference

---

# git config

| Syntax | Description |
| ------ | ----------- |
| `git config <key>` | View the configuration behind a `<key>` |
| `git config --show-origin <key>` | View the location of the `<key>` configuration | 
| `git config --list` | View all configurations (in all config files) |
| `git config --list --show-origin` | View all configurations and the files were they live |
|  |  |
| `git config --global user.name "foo bar"` | Make `foo bar` your global user's id (`.gitconfig`) |
| `git config --global user.email foo@bar.com` | Make `foo@bar.com` your global user's mail address (`.gitconfig`) |
| `git config --global core.editor <editor>"` | Make `<editor>` your global user's default text editor (`.gitconfig`) |
| `git config --global init.defaultBranch <branch>"` | Make `<branch>` your global user's default initialization branch (`.gitconfig`) |

---

# git help

| Syntax | Description |
| ------ | ----------- |
| `git help <verb>` | Get help with `<verb>` |
| `git <verb> --help` | Get help with `<verb>` |
| `man git-<verb>` | See `<verb>`'s man page |
| `git <verb> -h` | List all options for `<verb>` |

---

# git init

| Syntax | Description |
| ------ | ----------- |
| `git init` | Re-/initialize a git repo in the current directory |
| `git init <dir/>` | Re-/Initialize a git repo in `<dir/>` |

---

# git status

| Syntax | Description |
| ------ | ----------- |
| `git status` | Check the state of your files (e.g., un-/tracked, un/-modified, un-/staged) |
| `git status --short` | Check the state of your files in a short format |

---

# git add

| Syntax | Description |
| ------ | ----------- |
| `git add <untracked_file>` |  Start tracking `<untracked_file>` |
| `git add <file_1> <file_2>` | Start tracking the *untracked* files -- `<file_1>`, `<file_2>` |
| `git add -i` |  Start tracking files interactively |
| `git add .` |  Start tracking all untracked files in the current directory |
| `git add *` |  Start tracking all untracked files |
| `git add *.c` |  Start tracking all untracked with a `.c` suffix  |
|  |  |
| `git add <modified_file>` |  Stage the `<modified_file>` (i.e., add it to the index or the "staging area") |
| `git add <file_1> <file_2>` | Stage the two *modified* files -- `<file_1>`, `<file_2>` |
| `git add -i` |  Stag modified files interactively |
| `git add .` |  Stage all modified files of the current directory |
| `git add *` |  Stage all modified files in your working directory |
| `git add *.c` |  Stage all modified files with a `.c` suffix  |

---

# git commit

| Syntax | Description |
| ------ | ----------- |
| `git commit` | Commit all staged files (with a message from core.editor) |
| `git commit -m <message>` | Commit all stages files with `<message>` |

---

# git clone 

| Syntax | Description |
| ------ | ----------- |
| `git clone <url>` | Clone the repo from `<url>` |
| `git clone <url> <dir/>` | Clone the repo from `<url>` into `<dir/>` |

---

# git diff 

| Syntax | Description |
| ------ | ----------- |
| `git diff` | Show all unstaged changes |
| `git diff <file>` | Show all unstaged changes in `<file>` |
| `git diff --staged` | Show all staged changes that are part of the next commit |
| `git diff --cached` | Show all staged changes that are part of the next commit |

---

# git rm

| Syntax | Description |
| ------ | ----------- |
| `git rm <file>` | Remove the unstaged `<file>` from your WD |
| `git rm <pattern>` | Remove all unstaged files from your WD that match the `<pattern>` |
| `git rm \*` | Remove all unstaged files from your WD 
| `git rm -f <file>` | Remove a staged `<file>` from your WD |
| `git rm --cached <file>` | Stop tracking a file (i.e., remove `<file>` from the staging area, but keep it in your WD | 

---

# git mv 

| Syntax | Description |
| ------ | ----------- |
| `git mv <bad_file> <good_file>` | Rename `<bad_file>` to `<good_file>` |
| `git mv <file> </somedir/else/file>` | Move `<file>` to `</somedir/else/file>` |

---

# git log

| Syntax | Description |
| ------ | ----------- |
| `git log` | Show each commit log |
| `git log -<n>` | Show each of the last `<n>` commit logs  |
| `git log -1` | Show the last commit log  |
| `git log -1 HEAD` | Show the last commit log of the branch indicated by `HEAD` (i.e., the pointer to the current branch) |
| `git log -p` | Show the patch introduced with each commit (i.e., within-file differences) |
| `git log -<n> -p` | Show the patch introduced in each commit for each of the last `<n>` commit logs |
| `git log --stat` | Show the commit logs statistic (i.e., if a file changed; and if so the lines added/removed `++++/---`) |
| `git log --shortstat` | Show a short commit logs statistic (i.e., only the changed/insertions/deletions line from the `--stat` command )
| `git log --pretty=oneline` | Show the commit logs in a prettified one-line format (e.g., abbreviated SHA-1 hashes) |
| `git log --oneline` | Show the commit logs in a one-line format (e.g., abbreviated SHA-1 hashes) |
| `git log --graph` | Add an ASCII graph for the branch and merge history to the commit log history |
| `git log --oneline --graph` | Show the commit logs in a one-line format and add an ASCII graph for the branch and merge history |
|  |  |
| `git log --since="<date>"` | Show commit logs since `<date>` (e.g. `1 year 2 monts 3 weeks, 4 days`) |
| `git log --since <date>` | Show commit logs since `<date>` (e.g. `2.weeks, 2008-03-22"`) |
| `git log --after="<date>"` | Show commit logs after `<date>` |
| `git log --after <date>` | Show commit logs since `<date>` |
| `git log --until="<date>"` | Show commit logs until `<date>` |
| `git log --until <date>` | Show commit logs until `<date>` | 
| `git log --before="<date>"` | Show commit logs before `<date>` |
| `git log --before <date>` | Show commit logs until `<date>` | 
|  |  |
| `git log -S <string>` | Show only commits where a `<string>` within the code changed (e.g., to monitor the changes of a function ) |
| `git log --grep <string>` | Show only commit messages containing `<string>` |
| `git log -- <path/to/file>` | Show only commit logs for a `<(path/to/)file>`  |
|  |  |
| `git log --author='<author>'` | Show only commit from `<author>`  |
| `git log --committer='<author>'` | Show only commit from `<committer>`  |

---

Look for differences that change the number of occurrences of the
           specified string (i.e. addition/deletion) in a file. Intended for the
           scripter’s use.


|  |  |
| `git logcial` | My alias for a log(ical) commit history output -- 

You can add the `logical` alias to your `.gitconfig` using by either using `git
config --global alias.<shorty> <command>. ` or adding `logical = log --color
--graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)
%C(bold blue)<%an>%Creset' --abbrev-commit` manually -- under `[alias]`-- to
your git configuration file.

---

## Tracking branches

The most general

`$ git checkout -b <branch> <remote>/<branch>`
`$ git switch -c <branch> <remote>/<branch>`

1. Git creates `<branch>` locally.
2. `<branch>` starts tracking `<remote>/<branch>` (upstream branch)
3. Git switches to `<branch>`

`$ git switch --track <remote>/<branch>`

1. Git creates `<branch>` locally.
2. `<branch>` starts tracking `<remote>/<branch>` (upstream branch)
3. Git switches to `<branch>`

Prerequisites: Git will only set-up a tracking branch, if (1) `<branch>` does
not exist locally yet and (2) `<branch>` corresponds to a unique name on
`<remote>`. 

## Remote tracking branch

If you want to set up a local <branch> to track the <remote>/<branch> then you
can hack the following formula into the machine:

```
git branch -u <remote>/<branch> <local_branch> 
```

Read it as: The `<local_branch>` `branch` is set up to be the tracking branch
for the `<remote>/<branch>`. However, we should not omit the little `-u` option
which is a shorty for `--set-upstream`. So a more direct translation would be:
Set up `<remote>/<branch>` as upstream branch for `<local_branch>`. The snippet
comes in handy if the name of the local branch differs from the one on the
remote repository, for example:

```
$ git branch -u origin origin/new_features experimental
Branch 'experimental' set up to track remote branch 'new_feature' from
'origin'.
```

If you want to save yourself a little typing, then you can also an equivalent
shorty for above's snippet. This holds, if the branch on the remote should be 
tracked by a local branch with the same name. Then the snippet simplifies to.


```
git branch -u <remote>/<branch>
```

But thinking back (a few commits) the snippet implies, that there is already a
local `<branch>` which is capable to track `<remote>/<branch>`. So actually the
workflow two operations: first, setting up a local `<branch>` and make
`<remote>/<branch>` the upstream branch for `<branch>`. Or, to put it another
way, now `<branch>` tracks (is the tracking branch of) our `<remote>/<branch>`:

```
git branch <branch> 
git branch -u <remote>/<branch> <branch> 
```

The get a two in one version of the snippet you can use `switch` with the
`-c`option or `checkout -b`:

```
git switch -c <branch> <remote>/<branch>
```


## Pushing branches

There are three global option which might help with the upstream-branch
wrangling: `push.default upstream`, `push.default simple`, `push.default
simple`. The first one pushes the current branch to its upstream branch, the
second is like upstream but refuses to push if the upstream branch’s name is
different from the local one and the last one pushes the current branch to a
branch of the same name. I stick with the second option, since I found this to
be the best default for me. But reed, e.g.
[stackoverflow.com](https://stackoverflow.com/questions/23918062/simple-vs-current-push-default-in-git-for-decentralized-workflow)
for additional advice:

```
git config --global push.default simple

```

```
git push -u origin master
```

In the first tutorial I took `git push -u origin master` for granted. Since we
now know a little more about tracking branches, we can dig a little deeper.
`git push -u origin master` does two things: first, it pushes your staged
changes from your local branch `master` to your remote `origin`. Second, it
commissions `master` to track the remote branch `origin/master`. Or, to put it
another way, it sets `origin/master` as upstream branch for your local branch
`master`. 


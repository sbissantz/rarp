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
| `git config --global alias.<alias> <command>"` | Set up an `<alias>` for a `<command>` (`.gitconfig`) |

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
| `git commit` | Commit all staged files (with a message from `core.editor`) |
| `git commit -m <message>` | Commit all stages files with `<message>` |
| `git commit --amend` | Amend the previous commit message (to a message from `core.editor`) |
| `git commit --amend -m <message>` | Amend the previous commit message to `<message>` |
| `git commit -a <message>` | Stage and commit all  modified files (with a message from `core.editor`) |
| `git commit -a -m <message>` | Stage and commit all modified files with `<message>` |

---

# git clone 

| Syntax | Description |
| ------ | ----------- |
| `git clone <url>` | Clone the repo from `<url>` (i.e., into a directory named like the word last word in the `<url>` or the word before the `.git` prefix in the `<url>`) |
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
| `git log -1 HEAD` | Show the last commit log of the `current` branch (i.e.: indicated by `HEAD`) |
| `git log -p` | Show the patch introduced with each commit (i.e., within-file differences) |
| `git log -<n> -p` | Show the patch introduced in each commit for each of the last `<n>` commit logs |
| `git log --stat` | Show the commit logs statistic (i.e., if a file changed; and if so the lines added/removed `++++/---`) |
| `git log --shortstat` | Show a short commit logs statistic (i.e., only the changed/insertions/deletions line from the `--stat` command )
| `git log --pretty=oneline` | Show the commit logs in a prettified one-line format (e.g., abbreviated SHA-1 hashes) |
| `git log --oneline` | Show the commit logs in a one-line format (e.g., abbreviated SHA-1 hashes) |
| `git log --graph` | Add an ASCII graph for the branch and merge history to the commit log history |
| `git log --decorate` | Add all of the references (e.g., tags, branches, etc.) to the commit logs |
| `git log --oneline --graph` | Show the commit logs in a one-line format and add an ASCII graph for the branch and merge history |
| `git log --oneline --decorate --graph --all` | Get an all-in-one supple commit-log output (..look above for details) |
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

# git restore (git reset) 

| Syntax | Description |
| ------ | ----------- |
| `git reset HEAD <file>` | Unstage a staged `<file>` |
| | |
| `git restore <file>` | Unmodify a modified `<file>` |
| `git restore --staged <file>` | Unstage a staged `<file>` |

---

# git remote 

| Syntax | Description |
| ------ | ----------- |
| `git remote` | Show the remote shortnames |
| `git remote -v` | Show the remote shortnames & the remote urls  |
| `git remote -vv` | Show which tracking branches are set |
| `git remote show <remote>` | Get extensive info about `<remote>` (i.e., HEAD, remote references, remote branch(es), tracking branch(es), push & pull info) |
| | |
| `git remote add <remote> <url>` | Add `<remote>` under `<url>` |
| `git remote rename <old_remote> <new_remote>` | Rename `<old_remote>` to `<new_remote>` (Note: does also change the names of remote-tracking branches) |
| `git remote remove <remote>` | Remove `<remote>` to `<new_remote>` (Note: does also change the names of remote-tracking branches) |

---

# git fetch

| Syntax | Description |
| ------ | ----------- |
| `git fetch` | Fetch all info (from the specified remote tracking branch, see: `fetch URL`) |
| `git fetch <remote>` | Synchronize your localdb with `<remote>` |

---

# git pull 

| Syntax | Description |
| ------ | ----------- |
| `git pull` | Fetch & merge all info (from the specified remote tracking branch, see `fetch URL`)  |
| `git pull <remote>` | Fetch all changes from `<remote>` and merge it into your localdb |

---

# git push 

| Syntax | Description |
| ------ | ----------- |
| `git push` | Push local changes (from `current` into `upstream` branch -- i.e.: remote/branch)  |
| `git push <remote> <branch>` | Push local changes from `<branch>` into `<remote>/<branch>`  |
| `git push <remote> <local_branch>:<branch>` | Push the changes from `<local_branch>` into a differently named `<remote>/<branch>` |
| | |
| `git push --tags` | Push local tags (from `current` into `upstream` branch -- i.e.: remote/branch)  |
| `git push <remote> <tag>` | Push a local tag into `<remote>` |
| `git push <remote> --tags` | Push all local tags (`refs/tags`) into `<remote>` |
| | |
| `git push <remote> --delete` | Delete all locally removed tags on `<remote>`, too (after a `git tag -d...`)   |
| `git push <remote> --delete <tag>` | Delete the locally removed `<tag> `on `<remote>`, too   |
| `git push <remote> --delete :refs/tags/<tag>` | Delete the locally removed `<tag> `on `<remote>`, too   |
| | |
| `git push --set-upstream <remote> <good_branch>` | Rename "bad_branch" to `<good_branch>` on `<remote>`, too (i.e., after doing `git branch --move <bad_branch> <good branch>`, and before doing `git push <remote> --delete <bad_branch>`) |
| | |
| `git push <remote> --delete <branch>` | Delete `<remote>/<branch>` |

---

# git checkout 

| `git checkout -- <file>` | Unmodify a modified `<file>` |
| | |
| `git checkout <tag>` | Checkout the versions of files `<tag>` is pointing to (Important: Puts you in the detached HEAD state)|
| `git checkout <branch>` | Checkout `<branch>` | 
| `git checkout -b <branch>` | Create and checkout `<branch>` | 
| `git checkout -b <branch> <tag>` | Checkout the versions of files `<tag>` is pointing to in `<branch>` |
| | |
| `git checkout --track <remote>/<branch>` | Create and checkout `<branch>` after setting it up to track `<remote>/<branch>` |
| `git checkout -b <branch> <remote>/<branch>` | Create and checkout `<branch>` after setting it up to track `<remote>/<branch>` (Note: Helpful if `<branch>` and `<remote>/<branch>` are named differently) |

---

# git switch 

| Syntax | Description |
| ------ | ----------- |
| `git switch -`  | Switch back to the previous branch |
| | |
| `git switch <tag>` | Checkout the versions of files `<tag>` is pointing to (Important: Puts you in the detached HEAD state)|
| `git switch <branch>` | Checkout `<branch>` | 
| `git switch -c <branch>` | Create and checkout `<branch>` | 
| `git switch -c <branch> <tag>` | Checkout the versions of files `<tag>` is pointing to in `<branch>` |
| | |
| `git switch --track <remote>/<branch>` | Create and checkout `<branch>` after setting it up to track `<remote>/<branch>` |
| `git switch -c <branch> <remote>/<branch>` | Create and checkout `<branch>` after setting it up to track `<remote>/<branch>` (Note: Helpful if `<branch>` and `<remote>/<branch>` are named differently) |

---

# git tag 

| Syntax | Description |
| ------ | ----------- |
| `git tag` | List all tags (of the current repo) |
| `git tag -l <pattern>` | Search for tags including `<pattern>` List all tags (of the current repo) |
| | |
| `git tag <tag_lw>` | Create a lightweight `<tag_lw>` (for the latest commit)  |
| `git tag -a <tag>` | Create an annotated `<tag>` (for the latest commit; i.e., SHA-1 hash; tagger name, email, date; tagging message; GPG signature) |
| `git tag -a <tag> <commit>` | Create an annotated `<tag>` for a particular `<commit>` |
| `git tag <tag_lw> <commit>` | Create a lightweight `<tag_lw>` for a particular `<commit>`  |
| | |
| `git tag -d <tag>` | Delete `<tag>` |

---

# git show 

| Syntax | Description |
| ------ | ----------- |
| `git show <object>` | Shows info about `<object>` |
| `git show <tag>` | Shows info about `<tag>` (i.e., SHA-1 hash; tagger name, email, date; tagging message; GPG signature) |

---

# git ls-remote

| Syntax | Description |
| ------ | ----------- |
| `git ls-remote <remote>` | List all remote references |


---

# git branch 

| Syntax | Description |
| ------ | ----------- |
| `git branch`| List local branches |
| `git branch --all`| List local & remote tracking branches |
| `git branch -v`| See all branches and their last commit |
| | |
| `git branch -vv`| See which tracking branches are set up |
| | |
| `git branch <branch>`| Create a new `branch` |
| `git branch -d <branch>`| Delete `branch` |
| `git branch --move <bad_branch> <good branch>`| Rename `<bad_branch>` to `<good_branch>` |
| `git branch --move master main` | Rename `master` to `<main>` (i.e., before doing `git push --set-upstream <remote> main` and `git push <remote> --delete master`) |
| | |
| `git branch --merged`| List all branches that have merged into the `current` branch yet | 
| `git branch --merged <branch>`| List all branches that have merged into `<branch>` yet |
| `git branch --no-merged`| List all branches that have not merged into the `current` branch yet |
| `git branch --merged <branch>`| List all branches that have merged into `<branch>` yet | 
| | |
| `git branch -u <remote>/<branch>`| Set up `<branch>` to track `<remote>/<branch>` | 
| `git branch -u <remote>/<branch> <branch>`| Set up `<branch>` to track `<remote>/<branch>` (Note: helpful if the branch and the remote branch are named differently) |

---

# git merge

| Syntax | Description |
| ------ | ----------- |
| `git merge <topic_branch>`| Merge `<topic_branch>` into the `current` branch (i.e.: indicated by `HEAD`) |
| `git merge <topic_branch> <branch>`| Merge `<topic_branch>` into `<branch>` |

---

# git merge

| Syntax | Description |
| ------ | ----------- |
| `git mergetool` | Resolve a merge conflict graphically |

---

# git mine

| `git unstage <file>` | `git reset -- HEAD <file>` | Alias to unstage a staged `<file>` |
| `git last` | `git log -1 HEAD` | Alias to view the last commit | 
| `git visual` | `!gitk` | Alias for a visual git interface | 
| `git logcial` | `git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit` | Alias for a log(ical) commit history output |

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














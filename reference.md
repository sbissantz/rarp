# Command reference

==

## Tracking branches

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
git branch -u <remote>/<branch> <branch> 
```

Read it as: The local `branch` is set up to be the tracking branch for the
`<remote>/<branch>`. However, we should not neglect the little `-u` option
which is a shorty for `--set-upstream`. So a more direct translation would be:
Set up `<remote>/<branch>` as upstream branch for `<branch>`.

Besides, the snippet obviously comes in handy if the name of the local branch
differs from the one on the remote repository, for example:

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









Branch 'master' set up to track remote branch 'master' from 'origin'.




Obviously this is helpful, when you want to 

This seems redundant, since there are two `<branch>`es and if you the names are
equal





git branch -u origin/serverfix








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

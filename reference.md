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

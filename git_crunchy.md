# Git on crunchy

In a nutshell:

- On the server 
  1. `mkdir /baz/project.git`
  2. `cd /baz/project.git`
  3. `git init --bare`
- On the local machine
  1. `git clone linda@123.45.6.7:baz/project.git`
  2. `git remote add origin linda@123.45.6.7:baz/project.git`
  3.  ...doing stuff
  4. `git push -u origin master`


## Add a new git repo on crunchy

1. `mkdir myrepo.git?`
2. `chgrp committers myrepo.git`
3. `git init --bare --shared=0660 myrepo.git`

Note: If someone wants to contribute add him/her to the commiters group first,
so he/she earns writing privileges. 













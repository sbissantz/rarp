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


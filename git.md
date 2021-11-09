# Using git and Github

This script is just another how-to for git and Github. First, make sure you
installed git and Github (either manually or using brew).  If so, we can set up
your user.

## Git

## Set up the global user 

```
git config --global user.name "foo bar"
```

--- 

## Assign a mail adress

```
git config --global user.email "foo@bar.com`
```

---

## Additionals

```
$ git config --global color.ui true
$ git config --global core.editor nvim
```

---

## Github

Test if you are account is recognized on Github

```
ssh -T git@github.com
```

if not copy your public key an github using either... or... and retest

```
pbcopy < ~/.ssh/id_rsa.pub
# ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```
---

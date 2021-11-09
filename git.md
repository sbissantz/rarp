# Using git and Github

## Git

## Define global user

`git config --global user.name "foo ba`

--- 

## Assign a mail adress

`git config --global user.email "foo@bar.com`

---

## Additionals

`$ git config --global color.ui true`
`$ git config --global core.editor nvim`

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

---

---


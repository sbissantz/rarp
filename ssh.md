# SSH (good practice)
[https://upcloud.com/community/tutorials/use-ssh-keys-authentication/]
---

It is part of good praxtice to use Github with SSH, so we need to generate
your SSH key.

## Pre-Check 

```
ls -ld ~/.ssh 
```
---

## Make a (secure) home for your key

```
mkdir -p ~/.ssh ; chmod 700 ~/.ssh ; ls -ld ~/.ssh
```

---

## Generate new keypair

```
ssh-keygen -t rsa
```
---

## Accessibility 

Copy public key to server or a 3rd party application (e.g. Github)

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
pbcopy < ~/.ssh/id_rsa.pub
```
---

## Save

Set up an SSH Agent and store the passphrase -- avoids reentering the
passphrase over and over again.

```
which $SHELL
ssh-agent /bin/zsh
ssh-add ~/.ssh/id_rsa
```
---

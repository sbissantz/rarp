# SSH (good practice)
[https://upcloud.com/community/tutorials/use-ssh-keys-authentication/]
---

It is part of good praxtice to use SSH. That's why we set up SSH in this
manual. First and foremost, this implied to set up a SSH key. But before
jumping right into practice, let me motivate its use a bit.

SSH is an abbreviation for Secure (Socket) Shell. The concept is built upon a
pre-specified ethic (the ssh protocol), clarifying how interactions between
machines should proceed. A key principle of SSH is authentication. The reward
comes in the form of an encrypted connection to another network.

But How does it work? Well, in this story there are two protagonists. Let's
call them Clemence (SSH Client) and Stacy (SSH Server). Both meet at a party.
First, Clemens tries to get in touch with Stacy. Success! After a while, she
passes him her number (the public key). He stores her number in his iPhone
contacts (the client's known hosts file). After some text messages, they
negotiate where and when to meet (the parameters of connection). After a couple
of dates, they live happily ever after (connection: established).

Obviously, the story is weird. And yes, probably it's less romanti. But common.
You should understand the concept. I hope the story contributed to this
goal (somehow). So let's rock.

## Prologue 

First, I want to make sure you don't have a key already. So let's check the
conventional location where your key might reside. Open a terminal an type:

```
ls -ld ~/.ssh 
```
---

## A safe place 

If you don't have key already, it's time to set things up. We first create a
`.ssh`directory in your homefolder. Then we make sure that only *you* can
access those files. Finally, we check the file ownership to asure everything is
set up correctly.

```
mkdir -p ~/.ssh ; chmod 700 ~/.ssh ; ls -ld ~/.ssh
```

---

## Generate new keypair

Empty directory are not very useful. Thus, we have to fill it with your keys.
In addition, we want to store your keys in the `.ssh` directory.

```
ssh-keygen -t rsa
```
---

Note: Executing the command will suggest a directory; something like
`User/.../.ssh/...`.  We will accept Roberts offer. To confirm just type
<Enter>. 

## Accessibility 

Now your machine is ready to roll. If you want to copy your public key on a
server or third party instance (e.g. Github) you can copy it with one of the
following commands.

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
pbcopy < ~/.ssh/id_rsa.pub
```
---

## SSH agent

Busy dudes set up SSH agents. SSH agents store your passphrase that you don't
have to reenter it over and over again. 

```
which $SHELL
ssh-agent /bin/zsh
ssh-add ~/.ssh/id_rsa
```
 
Note: In macOS there is a very elegant way to setup and store the standard key
in your keychain. Just type:

```
ssh-add --apple-use-keychain
```

Another key? Well, specify its location using the following snippet:

```
ssh-add --apple-use-keychain /path/to/private/key/file
```

You might also consider:

```
ssh-add --apple-load-keychain
```

...to add identities to the agent using any passphrase stored in the user's
keychain. Besides suggests to create a `~~/.ssh/config` file and add:

```
 Host *
   UseKeychain yes
   AddKeysToAgent yes
   IdentityFile ~/.ssh/id_rsa
```
---


# SSH (good practice)

---

It is part of good practice to use SSH. That's why we'll set it up here. First
and foremost, this implies to get an SSH key. But before jumping right into
practice, let me motivate the journey a litte bit.

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

Obviously, the story is weird. And yes, probably it is less romantic. But if
you get some idea of how the concept works, the story served its purpose! So
let's rock.

## Prologue 

First, we should check you don't have a key already. So let's look at
conventional location where your key should reside. Open a terminal an type:

```
ls -ld ~/.ssh 
```
---

If Robert answers `No such file or directory`, it's time to set things up. 

---

## Generate new keypair

To generate a key run:

```
ssh-keygen -t rsa
```
---

Note: When executing your machine suggest a directory path; something like
`User/.../.ssh/...`.  We will accept Roberts offer. To confirm just hit
<Enter>. 


Great. Time to rerun the `ls` command to ensure Robert created the `.ssh`
directory. 

```
ls -ld ~/.ssh 
```

Did you get a cryptic `drwxrwxr-x. 1 <owner> <group> ... .ssh//` as result?
Great! We're almost done. I suggest to change the permission set. This will
ensure only you can read an write to the directory. That's is a neat little
security feature! 

```
chmod -v 700 ~/.ssh ; ls -ld ~/.ssh
```

You will be told that the `mode of '.ssh' changed from 0775 (rwxrwxr-x) to 0700
(rwx------)`. Now only you, the owner of the file, have r(ead) w(rite) and
(e)x(ecute) permissions. 

## Accessibility 

Now your machine is ready to roll. If you want to copy your public key on a
server or third party instance (e.g. GitHub) you can copy it with *one* of the
following commands.

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
pbcopy < ~/.ssh/id_rsa.pub
```

---

## Epilogue

There is one goody left which might come in handy, once you'll use SSH on a
daily basis: an SSH agent.

---

### SSH agent

Busy dudes set up SSH agents. SSH agents store your passphrase that you don't
have to reenter it over and over again. 

```
which $SHELL
ssh-agent /bin/zsh
ssh-add ~/.ssh/id_rsa
```
 
Note: macOS developed a very elegant way to setup and store the standard key
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
keychain. Besides, you might also consider to create a `~~/.ssh/config` file
and add:

```
 Host *
   UseKeychain yes
   AddKeysToAgent yes
   IdentityFile ~/.ssh/id_rsa
```

This seems useful as it persist your password between sessions/restarts of your
box. See Cris' answer
[here](https://superuser.com/questions/88470/how-to-use-mac-os-x-keychain-with-ssh-keys)
for more details. Note that it might seem sufficient to just add `ÙseKeychain
yes` to your `.ssh/config.` as Ben noted
[here](https://superuser.com/questions/88470/how-to-use-mac-os-x-keychain-with-ssh-keys).
If you haven't done it already, it is as simple as:

```
touch .ssh/config ; echo "UseKeychain yes" >> ~/.ssh/config
```
---


# MacOS setup

...for all the things to come

---

Open the Spotlight search by pressing `command` and `space`. Type "terminal"
(omit quotes). If you see a big black something, you are right. The frame
limiting the black something is your terminal. Think of the terminal as a
non-graphical way to interact with your system. The terminal itself comprises 
your shell. Formally, a shell is a command language interpreter. It takes your
input and produces miscellaneous output. So it is kind of a personal servant --
let's call him Robert. 

Ah, before we get going with Robert -- you see the tiny bright white shining
thing on the left? That is your prompt. Mine looks like this `steven@taure ~
%`[^1]. The default convention is often `user@host`. But you can change that
(temporarily) easily (`export $PS1=Robert`).  Anyway, the prompt indicates that
machine is ready to serve. If there is no prompt, you cannot commission your
robotic servant Robert to do stuff. It is as simple as that. For example, paste
`echo "Not available"; sleep 15` and try to enter something like `whoami`
afterwards. It won't work. Robert is literally fallen asleep (i.e., your system
is not ready to operate). So make sure Robert is awake (there is a prompt)
before you start hacking.

[^1]: More precisely, `steven@taure ~%` is a result of `[\u@\h \W]\$`. See `echo
$PS1`.

To interact with Robert you generally slice in some tiny amount of input (a
command), and he delivers the related output. You can enter commands after the
prompt. For example, type `which $SHELL`. The instruction (command + argument)
is the formal way to ask Robert to look up the shell you are currently using.
You might get an answer like `/bin/zsh/`. His answer tells you, you're using
the Z shell (Zsh). Zsh is the shell for the cool kids. I usually prefer the
Bash (since it is the default on most Linux systems). But I guess you don't
want to fiddle around with some wayward details about their differences and
jump right into practice, right?

Alright, let me introduce your two most loyal companions on the black-whole
journey: `man` and `--help`. If you have any questions about a command, ask
Robert with the magic formula: `man [command]` or `[command] --help`. Some
additional helper commands (to look up) are `cd`, `ls`, `uname`, `who`, `ping`,
`ssh` and `sftp`, ...

    Goody: It is not necessary but kind of a conventional standard to give your
    boxes cool names. To do so, you have to change your computers (local)
    hostname. On macOs go to System Preferences > Sharing. The top row shows your
    computer name. I chose "taure" (Q. noun. forest) -- because I'm a nerd --
    but you don't have to use elvish. Feel free to choose whatever you like. 

---

## Xcode

Cool, your licensed to interact with your system in a non-graphical way. Now
it's time to set up your system. Open up a terminal. Type:

```
xcode-select -p 
```

The command should give you some like `/Library/Developer/CommandLineTools`.
If so, your are ready to rock. If not, you have to install the all developer
tools (`XCode`) using:

```
xcode-select --install
```

---

## Homebrew 

Since you're now gradually becoming a nerd, it is a good idea to install
Homebrew. Why? Well, Homebrew is the (missing) package manager for macOS. This
tool comes in handy if you want to install additional packages on your system
which are not preinstalled. It's like a candy shop -- a gateway to everything
your (developer's) "sweet heart" has ever desired (git, wget, rectangle,
fortran, ...). Just hack the following snippet in the terminal, and you are
gold:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

If you want to make sure, everything worked out correctly, run:

```
brew doctor
```

Robert should tell you, that... `Your system is ready to brew`. Any questions
about `brew`? Use `man brew` or `brew --help`. To install a package, for
example `git` type:

```
brew install git
```

---

## Epilogue

That's basically it! Let me finish this tutorial with the Peter Parker
principle and a modified version of Gelman's folk theorem of statistical
computing. Those should guide your upcoming journey: Using the terminal gives
you great power. But with great power comes great responsibility! Whenever you
face computational problems, often the problem resides right behind the
typewriter. So be sure to always check your input first -- before you bring out
the heavy guns! 

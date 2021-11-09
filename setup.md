
# MacOS setup

...for all the things to come

---

Open the Spotlight search by pressing <command> and <space>. Type "terminal"
(omit quotes). If you see a big black something, then you are right. The frame
limiting the black something is your terminal. Think of the terminal as a
non-graphical way to interact with your system. The terminal itself swallows
your shell. Formally, a shell is a command language interpreter. It takes your
input and produces miscellaneous output. So it is kind of a personal servant --
Robert. You slice in some tiny amount of input, and Robert delivers the related
output. For example, type "which $SHELL".  This is the formal way to ask Robert
to look up the shell you are currently using.  You might get an answer like
"/bin/zsh/". This info tells you, that you're using the Z shell. Zsh is the
shell for the cool kids. I usually prefer the Bash (since it is the default on
most Linux systems). But I guess you don't want to fiddle around with some
wayward details about their differences and jump right into practice, right?

Alright, let me introduce your two most loyal companions on this black-whole
journey: "man" and "--help". If you have any questions about a command, ask
Robert with the magic formula: "man [command]" or "[command] --help". Some
additional helper commands (to look up) are `cd`, `ls`, `uname`, `who`, `ping`,
`ssh` and `sftp`, ...

    > Goody: It is not necessary but kind of a conventional standard to give
    > your boxes cool names. To do so, you habe to change your computers
    > (local) hostname.  Go to System Preferences > Sharing. The top row shows
    > your computer name. I chose "taure" (Q. noun. forest) -- because I'm a
    > nerd, but you don't have to use elvish; feel free to choose whatever you
    > like. 

---

öffne ein Terminal: (command + space ; dann in die Spotlightsuche "terminal" eingeben)
im Terminal sicherstellen, dass xcode installiert ist einfach alles nach "()" copy-paste :

(1) xcode-select --install
(2) xcode-select -p (sollte den Output "/Library/Developer/CommandLineTools" erzeugen)





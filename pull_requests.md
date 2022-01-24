# Pull requests

(0) Repositrory forken (auf Github oben rechts)
(1) git clone git@github.com:sbissantz/testtheory.git
(2) cd testtheory
(3) git remote add upstream git@github.com:rkupffer/testtheory.git
(4) git remote -v (sollten 4 angegeben sein -- origin & upstream; jeweils fetch und pull)
[(5) git checkout master ; git pull origin master ; git pull upstream master]
(6) git checkout -b changes
(7) File(s) bearbeiten
(8) git add .
(9) git commit -m "msg"
(10) git push -u upstream (wenn du willst, kannst du auch expliziter `git push -u upstream changes` schreiben)
(11) Auf das geforkte Repo gehen; dort wird dir angezeigt "Pull Request". Das anclicken
(12) Pull Request ausfüllen
(13) Absenden
(14) fertisch!


# Rebase
#

Often, you’ll do this to make sure your commits apply cleanly on a remote branch — perhaps in a project to which you’re trying to contribute but that you don’t maintain. In this case, you’d do your work in a branch and then rebase your work onto origin/master when you were ready to submit your patches to the main project. That way, the maintainer doesn’t have to do any integration work — just a fast-forward or a clean apply.





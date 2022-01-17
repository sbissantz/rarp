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

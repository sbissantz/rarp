# How to connect to ELWE

* Für RARP

(0) Registrieren: (https://login.rarp-kl.de/)
(1) Confirmation: Bestätigt, dass euer Acc funktioniert
(2) Reiter: 'HPC' -- eure Credentials abrufen ("Regirstry info"), die braucht ihr für euren Login.
(3) Passwort festlegen!
Note: VPN (Using ssh requires VPN to your RARP-site)

(ping elwe1.rarp-kl.de)
(For graphical stuff:  X11 extension)
(brew install --cask xquartz)
SSH client: Putty

Wichtige Infos:
Login Node: elwe1.rarp-kl.de
Rarp credentials: uld_<nachname> (most important)
(localUid is login name)
Beispiel: uld_bissantz

+++++++++++++++++++++++++++++++++++
Using SSH: elwe1.rarp-kl.de
Formel: ssh -X elwe<x>.rarp-kl.de (<x>=1, 2)
Beispiel: ssh -X elwe1.rarp-kl.de
+++++++++++++++++++++++++++++++++++

Wie ich mich connecte:
+++++++++++++++++++++++++++++++++++
Terminal:
ssh -X uld_bissantz@elwe2.rarp-kl.de
(-> Passwortabfrage)
+++++++++++++++++++++++++++++++++++

Note: Es gibt auch ein GUI (das habe ich aber nicht getestet)

Using NX
GUI für Elwetritsch: NX
Download: https://www.nomachine.com/
Server: elwe-nx.rhrk.uni-kl.de (anpassen!)
Port: Default Port (4000)

Allgemeine Infos:

Best Practices
https://elwe.rhrk.uni-kl.de/elwetritsch/batch.shtml
Kontakt
https://elwe.rhrk.uni-kl.de/kontakt.shtml
Cluster Status
https://elwe.rhrk.uni-kl.de/

Liebe Grüße
Steven


# Selbst eine Minecraft-Welt generieren

(TODO): Einleitung
Karl Olsberg beschreibt in seinen Büchern, dass er den Seed "100200300400500" in der Minecraft-Version 1.8.1 verwendet hat, um die in seinen Büchern beschrieben Welt zu erzeugen. 

## Welt auf Minecraft/Spigot 1.8.1 anlegen und komplett vor-generieren
Unser Ausgangsproblem ist, dass wir auf den Weltgenerator der Java Edition 1.8.1 angewiesen sind. Minecraft funktioniert so, dass neue Teile der Welt (Chunks) erst generiert werden, wenn ein Spieler diese erstmalig betritt - und zwar nach den dann aktuell geltenden Weltgenerator-Regeln. Diese sind in höheren Versionen anders als in 1.8.1. 

Wir müssen also die DasDorf-Welt schon vorab mit dem 1.8.1-Weltgenerator generieren und können nicht darauf warten, dass ein Spieler sie betritt. 

Dafür gibt es Werkzeuge. Ich habe den alternativen Minecraft-Server Spigot verwendet, da er ein Plugin unterstützt, welches genau die "Vorbefüllungs"-Funktionen mitbringt, die wir brauchen. 

(TODO: Installationsbeschreibung für Spigot)
(TODO: Installationsbeschreibung für WorldBorder)

Nach dem Serverstart bleibt ein Terminal-Fenster geöffnet, in welches man Befehle eingeben kann. 

Ich brauche 3 Befehle: 
* wb set (TODO Befehl nachschlagen)
* wb fill 20 208
* wb fill confirm

"wb set" setzt eine kreisförmige Grenze mit x Blöcken Radius um den Nullpunkt der Welt herum (ich habe initial 2000 Blöcke gewählt)
"wb fill 20 208" bestimmt die Generierungsgeschwindigkeit (20 Chunks pro Sekunde) und dass die Kreis-Grenze beim Generieren um zusätzliche 208 Blöcke "überschritten" wird, damit man nicht an einem Abgrund steht. 
"wb fill confirm" setzt die Generierung in Gang. Nun wird jeder Block innerhalb des Kreises generiert und gespeichert, so als hätte ein Spieler ihn betreten. 

Das kann nun eine Weile dauern. Man bekommt eine Fortschrittsanzeige. Am Ende sollte im Verzeichnis des Spigot-Servers ein Ordner "world" existieren mit etwa 300MB Größe (für mein 2000-Blöcke-Beispiel) 

## Welt schrittweise auf die aktuelle Version von Minecraft Java Edition aktualisieren

(TODO)

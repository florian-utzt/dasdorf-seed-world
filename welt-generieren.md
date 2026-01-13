# Selbst eine Minecraft-Welt generieren
Allgemeine Informationen siehe hier: [README.md](./README.md)

> **Achtung**: Wenn du einfach nur die fertig generierte Welt mit 2000 oder 4000 Blöcken Radius herunterladen möchtest, bist du hier falsch. Gehe zu https://github.com/florian-utzt/dasdorf-seed-world/releases . 

Nachfolgend findest du mein dokumentiertes Vorgehen, um dir deine eigene Welt, ggf. mit anderer Größe, zu erzeugen. 
Karl Olsberg beschreibt in seinen Büchern, dass er den Seed "100200300400500" in der Minecraft-Version 1.8.1 (von 2014!) verwendet hat, um die in seinen Büchern beschrieben Welt zu erzeugen. 
Bis man diese Welt in einer modernen Minecraft-Installation nutzen kann, braucht es einige Upgrade- und Konvertierungsschritte.  
Du brauchst einen Windows-PC, ein paar GB Speicherplatz und ein paar Stunden Zeit. Zudem durchaus etwas fortgeschrittenes PC-Wissen rund um Installationen, Dateien und Kommandozeile. Manche der untenstehenden Schritte sind ggf. schon wieder veraltet, wenn du diese Anleitung nutzt, und müssen improvisiert werden. Viel Erfolg!


## Welt auf Minecraft/Spigot 1.8.1 anlegen
Unser Ausgangsproblem ist, dass wir auf den Weltgenerator der Java Edition 1.8.1 angewiesen sind. Minecraft funktioniert so, dass neue Teile der Welt (Chunks) erst generiert werden, wenn ein Spieler diese erstmalig betritt - und zwar nach den dann aktuell geltenden Weltgenerator-Regeln. Diese sind in höheren Versionen anders als in 1.8.1. 

Wir müssen also die DasDorf-Welt schon vorab mit dem 1.8.1-Weltgenerator generieren und können nicht darauf warten, dass ein Spieler sie betritt.  
Dafür gibt es Werkzeuge. Ich habe den alternativen Minecraft-Server [Spigot](https://www.spigotmc.org/) verwendet, da er ein Plugin unterstützt (WorldBorder), welches genau die "Vorbefüllungs"-Funktionen mitbringt, die wir brauchen. 

Spigot muss aus rechtlichen Gründen selbst kompiliert werden, bringt dafür aber ein sehr einfach zu bedienendes Werkzeug mit: [Buildtools](https://www.spigotmc.org/wiki/buildtools/). Das benötigte Java 8 kann man später gleich noch zum Laufenlassen von Spigot sowie des Minecraft-1.12-Servers benutzen. 

Sobald BuildTools die Datei spigot-1.8.8.jar ausspuckt, packe diese in einen separaten Ordner. Öffne in diesem Ordner ein Terminal und starte den Server:   
`<Pfad deiner Java-Installation>\bin\java.exe -Xmx2G -Xms2G -jar spigot-1.8.8.jar nogui`

Der Server stoppt sofort wieder mit einem Hinweis auf das End User License Agreement (EULA). Öffne die erzeugte Datei eula.txt und setze: `eula=true` . 
Beim erneuten Serverstart wird der Server alle nötigen Dateien sowie eine initiale Welt erzeugen. Nun musst du zwei Setup-Tasks durchführen: 

* (stoppe den Server)
* öffne die server-properties und setze: `level-seed=100200300400500`
* lösche die initialen Ordner world, world_nether und world_the_end

Nun kannst du den Server erneut starten, die erzeugte Welt ist nun exakt die Welt von Das Dorf. Du kannst sie mit einem Minecraft 1.8.1-Client (gibt es über den Minecraft Launcher -> Installationen) bereits bereisen. 

## Das WorldBorder Plugin hinzufügen und die Welt vor-generieren

Lade nun WorldBorder 1.8.4 hier herunter: https://dev.bukkit.org/projects/worldborder/files
Warum genau diese Version? Gemini begründet dies mit "This version was released in June 2015 specifically to bridge the gap between legacy CraftBukkit and the newer Spigot 1.8.x builds."

* Server stoppen
* WorldBorder.jar ins Verzeichnis "plugins" packen
* Server wieder starten. 

Nach dem Serverstart bleibt ein Terminal-Fenster geöffnet, in welches man Befehle eingeben kann. 

Ich brauche 3 Befehle: 
* `wb world set 2000 0 0`
* `wb world fill 20 208`
* `wb world fill confirm`

`wb world set` setzt eine kreisförmige Grenze mit x Blöcken Radius um den Nullpunkt der Welt herum (ich habe initial 2000 Blöcke gewählt)  
`wb world fill 20 208` bestimmt die Generierungsgeschwindigkeit (20 Chunks pro Sekunde) und dass die Kreis-Grenze beim Generieren um zusätzliche 208 Blöcke "überschritten" wird, damit man nicht an einem Abgrund steht.   
`wb world fill confirm` setzt die Generierung in Gang. Nun wird jeder Block innerhalb des Kreises generiert und gespeichert, so als hätte ein Spieler ihn betreten. 

Das Befehlsformat ist immer: wb \<Weltname\> \<Befehl\> \<Parameter\> . Da die Standardwelt bei Spigot einfach "world" heißt, beginnen meine Befehle alle mit "wb world ..."

Das kann nun eine Weile dauern. Man bekommt eine Fortschrittsanzeige. Am Ende sollte im Verzeichnis des Spigot-Servers ein Ordner "world" existieren mit etwa 260MB Größe (für mein 2000-Blöcke-Beispiel) 


## Optional: Welt überprüfen mit mcview
Jetzt ist ein guter Zeitpunkt, einmal zu prüfen, ob die Generierung geklappt hat. Wie gesagt, allein die Ordnergröße muss signifikant gestiegen sein. 

* Kopiere den Ordner "world" in `%appdata%\.minecraft\saves` . 
* Besorge dir die Software MCView: https://github.com/kbinani/mcview 

Du solltest deine Welt nun in mcview öffnen können. 

![](/dasdorf-2000.png)


## Welt schrittweise auf die aktuelle Version von Minecraft Java Edition aktualisieren
Gemini empfiehlt nun, die Welt 1x in Minecraft 1.12.2 zu laden und dann erst in der aktuellsten Version (bei mir 1.21.11). 

Ich nutze dafür ab jetzt den offiziellen Minecraft-Server. Beim Vorgehen kannst du dich an der Beschreibung des Spigot-Servers (oben) orientieren mit folgenden Anpassungen: 
* Die JAR-Dateien für den Server bekommst du vom Minecraft-Wiki und musst sie nicht selbst bauen: 
  * https://minecraft.wiki/w/Java_Edition_1.12.2 -> Box rechts -> Downloads
  * https://minecraft.wiki/w/Java_Edition_1.21.11 -> Box rechts -> Downloads
* Leicht verändertes Ordnerformat: Im Minecraft-Server heißt der Ordner für die Oberwelt ebenfalls "world", die Ordner für Nether und Ende sind DIM1 und DIM-1
* Starte den Minecraft-Server mit den Parametern --forceUpgrade und --eraseCache, damit wirklich alle Blöcke/Chunks beim Upgrade auf die neue Version erwischt werden. 
  * Also: `<Pfad deiner Java-Installation>\bin\java.exe -Xmx2G -Xms2G -jar server.jar nogui --forceUpgrade --eraseCache`
  * Achtung: Für die 1.21er Installation brauchst du ein neueres Java als für die 1.12er und 1.8.1er. 

Vergiss nicht, jeweils vor dem Serverstart deinen aktuellen "world" Ordner in das Serververzeichnis hineinzukopieren! 
In Version 1.12.2 scheint forceUpgrade noch nichts zu bewirken. Bei 1.21.11 dauert der erste Start mit forceUpgrade wesentlich länger. 


## Wichtiger Zwischenschritt: Die Chunks als "fertig" markieren mit MCA Selector
WorldBorder hat uns alle nötigen Chunks schon mal generiert, doch leider unterscheiden sie sich in einigen relevanten Punkten von einem "echten" Chunk, der durch die Anwesenheit eines Spielers generiert wurde. 
Minecraft speichert für jeden Chunk einen Status und außerdem, wie lange sich schon ein Spieler darin aufgehalten hat. Beide Attribute werden von nachgelagerten Tools abgefragt, um unnütze Teile der Welt zu erkennen und somit deren Arbeit zu beschleunigen -> schlecht für uns!

Also müssen wir diese Chunks vervollständigen. 
* Besorge dir das Programm MCA Selector: https://github.com/Querz/mcaselector
* Öffne deinen Weltordner (File -> Open World)
* Tools -> Filter Chunks
  * Wähle "Circle" und gib an: `0;0;2000`. Siehe Screenshot unten. 
* Tools -> Change Fields
  * Status: `minecraft:full`
  * InhabitedTime: `1200`  (entspricht etwa 5 Minuten Spielzeit)

![](/mcaselector.png)  
![](/mcaselector2.png)

Die Welt wird nach Klick auf OK sofort gespeichert, du kannst das Programm einfach schließen. 


## Fertig - für die Java Edition
Falls du die aktuelle Java-Edition auf PC benutzt, bist du hier fertig! Du kannst den "world" Ordner wieder nach `%appdata%\Roaming\.minecraft\saves` kopieren und kannst ihn in deiner Minecraft-Installation benutzen. 

Falls du die Bedrock Edition verwendest (auf PC optional, auf Konsolen ist es immer Bedrock), dann musst du die Welt nun noch konvertieren (siehe unten)

## Bonus-Quest 1: Die Welt von Java nach Bedrock konvertieren (mit Chunker)
* Besorge dir das Programm Chunker: https://www.chunker.app/
* Choose world folder -> gib hier deinen Weltordner aus dem Serververzeichnis an
* wähle als Zielversion die neueste Bedrock-Version, die nicht als "Beta" gekennzeichnet ist. 

Ich musste keine weiteren speziellen Einstellungen vornehmen. Es ist jedoch sehr wichtig, dass du den Vorbereitungsschritt mit MCA Selector (siehe oben) ausgeführt hast, sonst erkennt Chunker nur einen kleinen Teil deiner Welt. Unter Advanced Mode -> Preview kannst du dir die erkannte Welt anzeigen lassen, sie sollte genauso rund aussehen wie in MCedit. 

Chunker spuckt eine Datei mit der Endung .mcworld aus, welche **ungefähr** so groß sein sollte wie dein world-Ordner.  

Diese .mcworld-Datei kannst du direkt in der Bedrock Edition importieren (Neue Welt -> Importieren)

## Bonus-Quest 2: Transfer auf die Nintendo Switch
Es gibt keinen direkten Weg, die mcworld-Datei in die Switch zu importieren. Man muss folgenden Weg nehmen: 

* Einen Minecraft Realm (Online-Server von Microsoft) erstellen und die Welt hochladen. Glücklicherweise gibt es eine kostenlose 30-Tage-Testversion von Realms.
* Auf der Switch mit dem gleichen Microsoft-Account anmelden, dem der Realm gehört, Minecraft starten, in die Realm-Verwaltug gehen und die Welt wieder herunterladen. 
  * dafür verlangt Nintendo, dass der zugehörige Switch-Account eine aktive Nintendo Switch Online Mitgliedschaft besitzt! Auch dafür gibt es eine 7-Tage-Testversion, die man aber nur 1x pro Account ausschöpfen kann. Viel Spaß beim Account-Wechseln...


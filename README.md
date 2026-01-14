# dasdorf-seed-world
> Die Minecraft-Welt aus den Das-Dorf-Büchern mit Seed 100200300400500, nutzbar in aktuellen Minecraft-Versionen. 

![](/dasdorf.png)

Meine Kinder lieben die Minecraft-Bücher "Das Dorf" vom Autor [Karl Olsberg](https://karl-olsberg.jimdoweb.com/b%C3%BCcher/). Mittlerweile sind knapp 40 Bücher rund um Primo, Kolle, Nano und Maffi erschienen.  
Ein besonderer Clou: In den ältesten Büchern ist ein Minecraft-Seed angegeben, mit dem man die beschriebene Welt aus den Büchern selbst bereisen kann.   

**Das Problem:** Das erste Buch erschien vor mehr als 10 Jahren und seither hat sich der Weltgenerator in Minecraft verändert. Auf neuen Minecraft-Versionen erzeugt der Seed "100200300400500" irgendeine Welt, nicht aber die ursprüngliche mit dem namensgebenden Dorf am Rand der Schlucht. Alte Minecraft-Versionen mit der Original-Welt sind nur umständlich auf PC zugänglich, auf Konsolen gar nicht. 

Ich habe die ursprüngliche Welt auf einer alten Minecraft-Installation generiert und in mehreren Zwischenschritten so konvertiert, dass man sie in aktuellen Minecraft-Versionen nutzen kann. 

# Welche Einschränkungen gibt es? 
* Da du eine alte Minecraft-Welt spielst, sind darin neuere Inhalte nicht enthalten. Natürlich ist das Dorf am Rand der Schlucht enthalten, ebenso das Wüstendorf, der Tempel und die beschriebenen Gebirge. Du findest neuere Inhalte wie z.B. Wachtürme jenseits der 2000/4000-Block-Grenze (siehe unten). 
* Inhalte, die rein für das Buch hinzugedacht wurden, kann Minecraft nicht erzeugen, z.B. die Hütte im Wald. Bau sie selbst!
* Lebewesen haben die vielen Konvertierungsschritte eventuell nicht überlebt. Benutze die Spawn-Eier!
* Nether und Ende habe ich nicht mit dem ursprünglichen Weltgenerator vor-generiert, da ich nicht wusste, ob dies überhaupt relevant ist. Feedback willkommen!

**Warum hat die Welt eine feste Größe?**
Unser Ausgangsproblem ist, dass wir auf den Weltgenerator der Java Edition 1.8.1 angewiesen sind. Minecraft funktioniert so, dass neue Teile der Welt (Chunks) erst generiert werden, wenn ein Spieler diese erstmalig betritt - und zwar nach den dann aktuell geltenden Weltgenerator-Regeln. Diese sind in höheren Versionen anders als in 1.8.1.   

Deshalb musste ich die Welt auf der uralten Minecraft 1.8.1 schon vorab komplett generieren. Und dabei eine Entscheidung treffen: Wie viele Blöcke sollen vorbefüllt werden? Eine zu große vorbefüllte Welt kann niemand sinnvoll bereisen, geschweige denn herunterladen. 
Ich habe 2 Varianten erstellt: Eine Welt, die in einem Kreis (Radius 2000 Blöcke) um den Spawnpunkt herum vor-generiert wurde, und eine Welt mit einem Kreisradius von 4000 Blöcken. 

![](/dasdorf-2000.png)

Erreichst du die Grenze, ist das aber nicht das Ende der Welt! Im wahrsten Sinne des Wortes. Sondern ab der 2000/4000-Block-Grenze übernimmt der Weltgenerator deiner aktuellen Minecraft-Version. Das kann zu kuriosen Ergebnissen führen, wenn der neue Weltgenerator an einer bestimmten Stelle eine ganz andere Welt vorgesehen hat, als der alte Weltgenerator. Trotzdem kannst du einfach über die Grenze hinaus wandern und die neue Welt erkunden.

Na, wo verläuft hier wohl die 2000-Block-Grenze? (Screenshot)  
![](/grenze.png)

# Wo finde ich die Minecraft-Welt zum Herunterladen?

Hier: https://github.com/florian-utzt/dasdorf-seed-world/releases

# Welche Datei soll ich herunterladen? 
Die Dateien stehen bereit in mehreren Varianten. 

nach Minecraft-Edition: 
* Für Minecraft Java Edition
* Für Minecraft Bedrock Edition

nach Größe: 
* 2000 Blöcke Kreisradius
* 4000 Blöcke Kreisradius

Finde als erstes heraus, welche Minecraft-Edition du besitzt (Hilfe z.B. hier: https://help.minecraft.net/hc/en-us/articles/6657208607501-Find-Out-Which-PC-Editions-of-Minecraft-You-Own)  
Faustregel: Auf Konsolen wie Playstation, Nintendo Switch, Xbox, ist es sowieso immer die Bedrock Edition. Auf PC hast du im Minecraft Launcher die Wahl zwischen Java und Bedrock. 

Zur Größe: In den meisten Fällen sollte 2000 Blöcke ausreichen (Weltgröße etwa 250 MB). Wähle 4000, wenn du wirklich intensiv mit der Welt spielen möchtest (Weltgröße etwa 1GB). 

# Wie bekomme ich die Welt in mein Minecraft? 

* Für Java Edition unter Windows: Kopiere den "world" Ordner nach: `%appdata%\.minecraft\saves`. Also so, dass es dann einen Ordner `%appdata%\.minecraft\saves\world` gibt. 
* Für Bedrock Edition unter Windows: Gehe auf Spielen -> Neue Welt -> Importieren. Und wähle dann die heruntergeladene .mcworld-Datei aus. 

Transfer auf Konsole: Hier kenne ich nur einen umständlichen Weg für Nintendo Switch, beschrieben [hier](https://github.com/florian-utzt/dasdorf-seed-world/blob/main/welt-generieren.md#bonus-quest-2-transfer-auf-die-nintendo-switch).   
Der dort beschriebene Weg über Minecraft Realms funktioniert sicher auch für andere Konsolen - aber vielleicht gibt es dort auch noch einfachere Wege, eine Datei zu übertragen. 

# Wie hast du das gemacht? 
Ich habe meine ausgeführten Schritte [hier](./welt-generieren.md) aufgeschrieben. 

Wenn du die Erstellung nachvollziehen möchtest, oder dir eine Welt in anderer Größe erstellen möchtest, kannst du dieser Anleitung folgen. 
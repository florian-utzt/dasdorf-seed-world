# dasdorf-seed-world
> Die Minecraft-Welt aus den Das-Dorf-Büchern mit Seed 100200300400500, nutzbar in aktuellen Minecraft-Versionen. 

![](/dasdorf.png)

Meine Kinder lieben die Minecraft-Bücher "Das Dorf" vom Autor [Karl Olsberg](https://karl-olsberg.jimdoweb.com/b%C3%BCcher/). Mittlerweile sind knapp 40 Bücher rund um Primo, Kolle, Nano und Maffi erschienen.  
Ein besonderer Clou: In den ältesten Büchern ist ein Minecraft-Seed angegeben, mit dem man die beschriebene Welt aus den Büchern selbst bereisen kann.   

**Das Problem:** Das erste Buch erschien vor mehr als 10 Jahren und seither hat sich einiges am Weltgenerator in Minecraft verändert. Auf neuen Versionen erzeugt der Seed "100200300400500" irgendeine Welt, aber nicht die ursprüngliche mit dem namensgebenden Dorf am Rand der Schlucht. Alte Minecraft-Version sind nur auf PC zugänglich, auf Konsolen nicht. 

Ich habe die ursprüngliche Welt auf einer alten Minecraft-Installation generiert und in mehreren Zwischenschritten so konvertiert, dass man sie in aktuellen Minecraft-Versionen nutzen kann. 

# Welche Version soll ich herunterladen? 
Die Dateien stehen bereit in mehreren Varianten. 

nach Minecraft-Edition: 
* Für Minecraft Java Edition
* Für Minecraft Bedrock Edition

nach Größe: 
* 2000 Blöcke Kreisradius
* 4000 Blöcke Kreisradius

Finde als erstes heraus, welche Minecraft-Edition du besitzt (Hilfe z.B. hier: https://help.minecraft.net/hc/en-us/articles/6657208607501-Find-Out-Which-PC-Editions-of-Minecraft-You-Own)  
Faustregel: Auf Konsolen wie Playstation, Nintendo Switch, Xbox, ist es sowieso immer die Bedrock Edition. Auf PC hast du im Minecraft Launcher die Wahl zwischen Java und Bedrock. 

Zur Größe: In den meisten Fällen sollte 2000 Blöcke ausreichen (Download etwa 250 MB). Wähle 4000, wenn du wirklich intensiv mit der Welt spielen möchtest. 

# Was sollte ich wissen? 
* Da du eine alte Minecraft-Welt spielst, sind darin neuere Inhalte nicht enthalten. Natürlich ist das Dorf am Rand der Schlucht enthalten, ebenso das Wüstendorf, der Tempel und die beschriebenen Gebirge. Du findest neuere Inhalte wie z.B. Wachtürme jenseits der 2000/4000-Block-Grenze (siehe unten). 
* Inhalte, die rein für das Buch hinzugedacht wurden, kann Minecraft nicht erzeugen, z.B. die Hütte im Wald. Bau sie selbst!
* Lebewesen haben die vielen Konvertierungsschritte eventuell nicht überlebt. Benutze die Spawn-Eier!

**Warum hat die Welt eine feste Größe?**
Unser Ausgangsproblem ist, dass wir auf den Weltgenerator der Java Edition 1.8.1 angewiesen sind. Minecraft funktioniert so, dass neue Teile der Welt (Chunks) erst generiert werden, wenn ein Spieler diese erstmalig betritt - und zwar nach den dann aktuell geltenden Weltgenerator-Regeln. Diese sind in höheren Versionen anders als in 1.8.1.  
Deshalb musste ich die Welt auf der uralten Minecraft 1.8.1 vorab generieren. Und dabei eine Entscheidung treffen: Wie viele Blöcke sollen vorbefüllt werden? Eine zu große vorbefüllte Welt kann niemand sinnvoll bereisen, geschweige denn herunterladen. 

![](/dasdorf-2000.png)

Das ist aber nicht das Ende der Welt! Im wahrsten Sinne des Wortes. Sondern ab der 2000/4000-Block-Grenze übernimmt der Weltgenerator deiner aktuellen Minecraft-Version. Sobald du den Bereich betrittst. Das kann jedoch zu ziemlich kuriosen Ergebnissen führen, wenn der neue Weltgenerator an der Stelle eine ganz andere Welt vorgesehen hat, als der alte. Trotzdem kannst du einfach über die Grenze hinaus wandern und die neue Welt erkunden.

Na, wo verläuft hier wohl die 2000-Block-Grenze? (Screenshot)  
![](/grenze.png)

> Willst du wirklich eine noch größere Welt? Ich habe die nötigen Schritte [hier](./welt-generieren.md) aufgeschrieben. Aber überleg dir das gut. Du brauchst Ausrüstung, Wissen und Zeit. Größer ist nicht immer besser. 

# Wo finde ich die Minecraft-Welt zum Herunterladen?

Hier: https://github.com/florian-utzt/dasdorf-seed-world/releases

# Wie bekomme ich die Welt in mein Minecraft? 

* Für Java Edition unter Windows: Kopiere den "world" Ordner nach: `%appdata%\.minecraft\saves`. Also so, dass es dann einen Ordner `%appdata%\.minecraft\saves\world` gibt. 
* Für Bedrock Edition unter Windows: Gehe auf Spielen -> Neue Welt -> Importieren. Und wähle dann die heruntergeladene .mcworld-Datei aus. 

Transfer auf Konsole: Hier kenne ich nur einen umständlichen Weg für Nintendo Switch, beschrieben [hier](https://github.com/florian-utzt/dasdorf-seed-world/blob/main/welt-generieren.md#bonus-quest-2-transfer-auf-die-nintendo-switch).   
Der dort beschriebene Weg über Minecraft Realms funktioniert sicher auch für andere Konsolen - aber vielleicht gibt es dort auch noch einfachere Wege, eine Datei zu übertragen. 





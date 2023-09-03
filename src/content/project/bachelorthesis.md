---
title: 'Bachelorthesis'
description: 'Automatisierung von Messverfahren zur Bestimmung der Ressourceneffizienz von Software mittels Continuous Integration'
heroImage: '/bachelorthesis.png'
---

## Einführung

Die Informationstechnologie ist längst ein fester Bestandteil unseres Lebens sowie
auch unserer Umwelt. Durch die ständige Weiterentwicklung von Produkten der Informationsund Kommunikationstechnik (IKT) sowie allgemein durch die Digitalisierung, werden die CO2-
Emissionen durch den damit einhergehenden Energieverbrauch beeinflusst. Auf digitaler Ebene ist es
demnach relevant, Software auf ihren Energie- und Ressourcenverbrauch zu untersuchen. Ziel dieser
Publikation ist die Präsentation eines Konzepts zur automatisierten Messung der Ressourceneffizienz
von Softwareprodukten, welches mit Hilfe der kontinuierlichen Integration umgesetzt wird. Als
Basis wurde dafür das Messkonzept des Institut für Softwaresysteme (ISS) am Umwelt-Campus
in Birkenfeld verwendet, welches bisher ohne automatisierte Messungen aufgebaut ist.

## Messkonzept

Als Basis für das Messkonverfahren dient das bisherige Konzept der Green Software Engineering Forschungsgruppe des ISS. 
Die Nutzungsszenarien werden bei dem neuen Konzept mit dem gleichen Ablauf durchgeführt. 
Dabei können verschiedene Automatisierungswerkzeuge verwendet werden. Für manche Werkzeuge müssen die Szenarien programmiert
werden, für andere lassen sie sich ausschließlich über ein drag-and-drop-System erstellen und
wieder andere kombinieren diese beiden Funktionsweisen. Im Rahmen dieser Publikation wird Selenium[^Selenium] als Tool für die 
Automatisierung der Nutzungsszenarien verwendet. 
Aus dem letzten Abschnitt ging hervor, dass auch ein Baseline-Szenario
gemessen werden muss. Neben dem Standardnutzungsszenario muss demnach auch ein
weiteres Szenario für die Baseline entwickelt werden.
Für das entwickelte Messverfahren ist zudem die Hardware-Auslastung besonders interessant.
Bei Ausführung der Nutzungsszenarien wird darauf geachtet, die Funktionen und Module
auszuführen, die besonders für einen Anstieg der Hardware-Ressourcen verantwortlich sind.
Um diese Auslastung zu messen, wird unter Linux das Tool Collectl[^Collectl] verwendet. Das
Tool zeichnet Systeminformationen zur CPU, der Platte, dem Speicher und dem Netzwerk
sowie weitere Informationen jeweils mit Zeitstempel auf. Um die Ergebnisse nach
der Messung auszuwerten, gibt es bei dem Collectl-Befehl eine Option, die Daten im
CSV-Format zu exportieren.
Für die Visualisierung der Ergebnisse aus den Hardware-Messungen wird für diese Ausarbeitung das Tool Autoplot[^Autoplot] verwendet, welches
speziell für diese Arbeit implementiert wurde. Die Software ist in der plattformunabhängigen Programmiersprache R entwickelt. 
Autoplot bekommt die aus Collectl exportierte CSV-Datei übergeben und visualisiert die Messergebnisse.

|               | Collectl-Feld          | Bedeutung                          |
|---------------|------------------------|------------------------------------|
| <b>CPU<b>     | Totl                   | CPU-Auslastung (Prozent)           |
| <b>Disk<b>    | ReadKBTot / WriteKBTot | Gelesene / geschriebene Daten (KB) |
| <b>Memory<b>  | Used                   | Verwendeter Arbeitsspeicher (MB)   |
| <b>Network<b> | RxKBTot / TxKBTot      | Empfangen / übertragen (KB)        |

Für die Auswertung relevante Collectl-Felder werden in obiger Tabelle vorgestellt. Insgesamt
werden die vier Kategorien CPU, Disk, Memory und Network analysiert. Wird das Autoplot-Skript ausgeführt, 
wird aus der aktuell beiliegenden CSV-Datei jeweils eine Bilddatei
pro Kategorie erstellt. Die erzeugten Bilder enthalten je nach Kategorie entsprechend nur
einen Graphen bzw. mehrere, wenn mehr als ein Collectl-Feld für die Kategorie analysiert
wird. Die Messwerte enthalten jeweils einen Zeitstempel, welcher sich auf der X-Achse
aller Graphen befindet. Dargestellt werden die Stempel dabei in Sekunden-Schritten. Der
Mittelwert der Datenverteilung wird durch eine rote horizontale Linie dargestellt. Eine
beispielhafte Grafik zur Visualisierung der CPU-Inanspruchnahme zeigt folgende Abbildung.

<div style="box-shadow: var(--box-shadow--light);margin-inline:auto;text-align:center;border-radius:2%">
    <img src="/CPU.png" alt="Beispielhafte Visualisierung der CPU-Inanspruchnahme">
    <p style="padding-bottom:10px;margin-top:-20px;font-size: 75%;text-align:center;">Abb.: Beispielhafte Visualisierung der CPU-Inanspruchnahme</p>
</div>

Die verschiedenen Komponenten, welche für das Messverfahren benötigt werden, wurden jeweils vorgestellt. 
Die folgende Abbildung zeigt den allgemeinen Ablauf im Gesamten, um einen besseren Überblick über den Zusammenhang der Komponenten zu bekommen.

<div style="box-shadow: var(--box-shadow--light);margin-inline:auto;border-radius:2%">
    <img src="/Automated_CI_Ablauf.png" alt="Allgemeiner Ablauf des Messkonzepts">
    <p style="padding-bottom:10px;margin-top:-20px;font-size: 75%;text-align:center;">Abb.: Allgemeiner Ablauf des Messkonzepts</p>
</div>

Gestartet wird das Messverfahren durch das Einschalten des Messrechners, der hier das System under Test (SUT)
darstellt und als CI-Server dient. Die Einschaltung erfolgt über Wake on LAN (WOL), d.h. der
ausgeschaltete Rechner kann über die eingebaute Netzwerkkarte gestartet werden. WOL wird
zeitgesteuert über ein Skript gestartet. Der im CI-Tool konfigurierte zeitliche Auslöser startet
kurz darauf den Nightly Build, d.h. die Projekte aus dem Verzeichnis werden gebaut. In jeder
CI-Pipeline werden für die Projekte jeweils die gleichen Schritte durchgeführt. Zu Beginn
wird das Softwareprojekt gebaut. Anschließend erfolgt die Messung, welche mehrere Schritte
in einer bestimmten Reihenfolge ausführt. Zuerst müssen ggf. vorbereitende Aktionen
getroffen werden, wie beispielsweise das Starten von Datenbank-Diensten. Anschließend
wird die Anwendung gestartet, sowie die Hardwareaufzeichnung mit Hilfe von Collectl.
Gleichzeitig wird das Nutzungsszenario gestartet. Sobald dieses fertig durchgeführt wurde,
wird die Anwendung gestoppt und es werden abschließende Aktionen getroffen. Im nächsten
Schritt werden Informationen zu den Hardwareressourcen an die Datensammlung und -analyse (DAE) weitergeben und in
diesem Fall durch das Tool Autoplot ausgewertet sowie in Form einer Grafik abgespeichert.
Der Messrechner wird durch einen zeitgesteuerten Cronjob kurz nach Ablauf des letzten
Projektes ausgeschaltet.

## Fazit

In dieser Publikation wurde auf Basis des Messkonzepts des Institut für Softwaresysteme
am Umwelt-Campus in Birkenfeld ein erweitertes Konzept entwickelt, welches mittels
Continuous Integration durchgeführt werden kann. Ziel des vorgestellten Messkonzepts
ist die Unterstützung aller Entwickler im Hinblick auf nachhaltige Software. Mit Hilfe der
Auswertungssoftware Autoplot können verschiedene Messungen von Softwareprodukten
direkt miteinander verglichen werden. Darunter zählen sowohl die Messungen zur Baseline
als auch zum Standardnutzungsszenario. Ist beispielsweise die CPU-Inanspruchnahme
einer Software Montags gering und die nächste Version am folgenden Tag fällt im Bezug
zur CPU-Inanspruchnahme höher aus, fällt dies dank der erstellten Grafiken sofort auf.
Der Vorteil hierbei ist, dass der Entwickler selbst, bis auf den initialen Aufwand, nichts
machen muss und die Ergebnisse automatisiert geliefert bekommt. Durch die Messung
von Softwareprodukten stehen etliche Informationen zu der Hardware-Auslastung zur
Verfügung. Ein konkreter Energieverbrauch kann jedoch nicht genannt werden, da die
Beziehung zwischen Energieverbrauch und Hardware-Inanspruchnahme noch nicht klar ist.
Aushilfe dafür könnte eine Ergänzung des Konzepts schaffen, die neben der Messung der
Hardware-Auslastung auch ebenso den Energieverbrauch automatisch misst.

Mit dem automatisierten Konzept hat man also einige Vorteile, beispielsweise regelmäßige
Untersuchungen zur Ressourceneffizienz einer Software auf automatisiertem Wege, ohne
die Messungen jedes Mal manuell zu starten. Dadurch wird eine Menge an Zeit gespart
und Fehler werden dank automatisierter Prozesse vorgebeugt. Hingegen muss auch erwähnt
werden, dass es dabei viel Zeit kostet, den initialen Aufwand zu bewältigen. Dazu zählt die Einrichtung des CI-Servers, 
die zu untersuchenden Softwareprodukte müssen eingepflegt
werden, wobei es dabei immer wieder zu Problemen kommen kann. Der größte Nachteil
des Messkonzepts ist aktuell jedoch, dass die Werte zum Energieverbrauch komplett fehlen.

## Literatur

[^Selenium]: Selenium https://www.selenium.dev/.
[^Collectl]: Collectl http://collectl.sourceforge.net/.
[^Autoplot]: Autoplot https://github.com/kreutzermaik/autoplot


<style>
    p {
        text-align: justify;
    }
</style>
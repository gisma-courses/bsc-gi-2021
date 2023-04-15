---
title: Lerneinheit 2 - Fragen & Antworten
toc: true
header:
  image: /assets/images/splash_L02.png
  image_description: "Post Boxes in the Marburg Area"
  caption: "Post Boxes in the Marburg Area. CC0 AG UI"
  


---


Das systematische Abfragen von Datenbankinhalten sind Sie aus dem Alltag gewöhnt. Sei es die Abfrage von Zugverbindungen, Kinokarten die Sie online bestellen  oder die Suchanfrage bei Google. <!--more-->
Auch die Integration räumlicher Attribute in Abfragen ist Alltag für Sie. Falls sie zb. die *Location based Services* in Google aktiviert haben werden Sie regelmäßig mit lokalisierter Werbung oder Abstimmungsanfragen bedacht. Doch wie können sie solche Abfragen selber gestalten und was ist die grundsätzliche Wirkungsweise?

## Was wir in dieser Einheit vor haben
In dieser Lerneinheit werden grundlegende Konzepte von Datenbankabfragen erlernt. Weniger formal werden Sie sich um die Extraktion von Daten aus Datentabellen kümmern. Die Verknüpfung von thematischen und räumlichen Abfragen auf Vektordaten sind eine zentrale Analysemethode in den Raumwissenschaften und auch im Alltagsleben sehr verbreitet. 

## Lernziele 

Nach dieser Übung können Sie:

  *  beliebige thematische und räumliche Abfragen auf Vektordatenattribute durchführen 
  *  geometrische und topologische Abfragen unterscheiden
  *  Abfragen verknüpfen


## Benötigte Materialien

### Daten
  * [Marburg digitales Luftbild](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/marburg_RE.tif)
  * [Marburg POI](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_pois.zip)
  * [Marburg ÖPNV  POI](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_transport_poi.zip)
  * [Marburg Verkehr POI](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_traffic_poi.zip)
  * [Marburg Other POI](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_other_poi.zip)
  * [Marburg Wald Flächen](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_nat.zip)
  * [Marburg Strassen](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_roads.zip)

Bedenken Sie bitte, dass die Downloads als Archivdateien vorliegen die entsprechend dekomprimiert werden müssen. Falls notwendig schneiden Sie alle Datensätze auf die Ausdehnung des Marburger Luftbildes aus Aufgabe 1 zu. Alle Daten sind dem [geofabrik OSM Datenbestand](http://download.geofabrik.de/){:target="_blank"} entnommen. 
{: .notice--info}

## Aufgaben Lerneinheit 2

Im ersten Teil der Aufgabe geht es darum aus den unterschiedlichen Datenbeständen die benannten Geoobjekte zu identifizieren und der einfachen Erfolgskontrolle wegen, zu zählen. Weder müssen alle Datensätze notwendigerweise verwendet werden (eine Vorauswahl wurde zwar getroffen aber nur um eine gewisse Übersichtlichkeit für die Übung zu erzeugen) noch sind alle Attribute zwingend in einer Attributtabelle zu finden.

### Aufgabe 02-01


In der Aufgabe 02-01 werden Attributwerte abgefragt. Folglich werden die Merkmale und ihre Ausprägungen öhne einen räumlichen Bezug aus den Tabellen extrahiert.

* Wieviel Ampeln ("traffic_signals") gibt es in Marburg?
* Wieviele Objekte weisen die Merkmalsausprägung "cafe" und "bar" auf.
* Wieviele Objekte sind weisen **nicht** die Merkmalsausprägung "university" auf?
* Wieviele Objekte beinhalten das Wort Café in ihrem Namen (Attribut name) ? 
* Welche Objekte beinhalten zwar das Wort Café in ihrem Namen, aber nicht der die Merkmalsausprägung "cafe" des Attributs flcass?
* Suchen Sie alle Objekte die den exakten Namen "REWE" haben **und** vom Typ "supermarket" sind.
* Suchen Sie alle Objekte die den exakten Namen "REWE" haben **oder** vom Typ "supermarket" sind.
{: .notice--success}


### Aufgabe 02-02


In der Aufgabe 02-02 beschäftigen wir uns mit topologischen und geometrischen Abfragen. Folglich werden die Attributabfragen erweitert um ihre räumlichen Komponenten Lage und Entfernung zueinander.

  - Wieviele Marburg POI befinden sich in Waldflächen?
  - Wieviele Marburg POI sind maximal 150 Meter von Waldflächen entfernt?
  - Wieviele "restaurants" oder "bars"" sind max 150 Meter von Waldflächen entfernt?
  - Wieviele Straßen führen durch Waldflächen?
  - Wie viele Marburg POI liegen im Umkreis von 500 Metern um den Marburger Bahnhof?
  - Wie viele Bars sind maximal 500 Meter von der nächsten Bushaltestelle entfernt?
  - Wie viele Punkte Marburg POI liegen im Umkreis von maximal 250 Metern um Parkplätze?
  - Von wievielen Punkte Marburg POI aus kann ein Arzt/Krankenhaus in weniger als 500 Meter Entfernung gefunden werden?
  - Wie viele Punkte der Kategorie Gastronomie liegen weiter als 1 Kilometer vom Bahnhof und gleichzeitig weniger als 1 Kilometer vom nächsten Briefkasten entfernt?
{: .notice--success}

### Gewichtung der Aufgaben in Lerneinheit 2

| Aufgabenteil | Gewichtung Teilaufgabe | Gewichtung  Gesamt| 
|:-------------|:----------------------:|:-----------------:|
|Aufgabe 02-01 | 0.25  | 0.1  | 
|Aufgabe 02-02 | 0.75  | 0.15  | 
|**Aufgabe 02**|**1.0**| **0.25**  | 


## Hilfestellungen 

### Der Ausdruckseditor
Für die generelle Abfrage auf relational strukturierte Datensätze (Attributtabellen, Datenbanken) ist der [QGIS Ausdruckseditor](https://docs.qgis.org/3.28/de/docs/user_manual/expressions/expression.html){:target="_blank"} das Werkzeug der Wahl. Unter dem Link finden Sie einen Einstieg in die QGIS Dokumentation. Der Ausdruckseditor ist ein Werkzeug das in vielfältiger Weise zum Einsatz kommt und daher aus unterschiedlichen Menu-Kontexten aufgerufen werden kann.

### Arbeiten mit Attributen

Das nachfolgende YouTube Video macht Sie in ca. 10 Minuten mit dem Umgang des Abfrageeditors vertraut. Beachten Sie auch die unterschiedlichen Verwendungszwecke die im Video thematisiert werden.

{% include video id="eFoBztZSIaM" provider="youtube" %}

Im diesem YouTube Video werden Sie auf 90 Minuten umfassend über die praktischen Anwendungsmöglichkeiten der Arbeit mit Attributen unterrichtet. Es ist zwar lang bringt aber viele wichtige Kombinationsmöglichkeiten und Aspekte ein und erschliesst somit ungeahnte Potentiale.

{% include video id="h-mpUkwDdOQ" provider="youtube" %}

### Vertiefende Erläuterungen

Unter [Relationen und Datenbanken - Grundlage räumlicher Informationssysteme](http://minibsc.gis-ma.org/GISBScL2/de/html/index.html){:target="_blank"} finden sie eine vertiefende Lerneinheit. Beachte Sie bitte dass die dort aufgeführten Übungen für ArcGis konzipiert sind.  




### Aufgabe 02-01

Bitte beachten Sie in jedem Fall, dass Ihre Suchbegriffe von den Datenerfasser:innen sowohl groß als auch klein, mit oder ohne Leerzeichen, nur teilweise oder auch mit oder ohne Umlaut erfasst worden sind. Auch typische Schreibfehler sind möglich.  Diese unterschiedlichen Eintragungen ein und derselben Kategorie sollten soweit es sinnvoll erscheint und möglich ist, bei den thematischen Abfragen berücksichtigt werden. 


### Aufgabe 02-02

 Sie können mehrere Abfragen hintereinander durchführen. Hierzu müssen Sie das Abfrageergebnis ggf. als neuen Layer speichern (Rechtsklick auf das selektierte Layer, dann Auswahl, dann Layer aus selektierten Features erstellen). Bitte beachten Sie, dass die so erstellten Layer nur virtuell sind. Sie können Sie aber natürlich z.B. als Geopackage-Datensatz exportieren.


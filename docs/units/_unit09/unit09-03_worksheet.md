---
title: Lerneinheit 3 - Analysen
toc: true
header:
  image: /assets/images/splash_L03.png
  image_description: "SRTM ElevationModel Data Marburg"
  caption: "SRTM Elevation Model Data Marburg. CC0 AG UI"
  

---


Digitale Geländemodelle liegen in der Regel als Rasterdaten vor und werden häufig in GIS-Analysen verwendet. Dabei tragen diese sowohl unmittelbar zur Höheninformation als auch mittelbar als z. B. morphometrische oder hydrologische Basisdatensätze zum prosessorientierten Erkenntnisgewinn bei.

<!--more-->

Der Themenkomplex der digitalen Geländemodelle inkl. deren Erstellung auf Grundlage unterschiedlicher Fernerkundungssensoren ist vielfältig. Die Materialien im Reader skizzieren verschiedene häufig verwendete Ableitungen und räumliche Filter. Diese Konzepte können auf nahezu alle Rasterdaten angewendet werden.


## Was wir in dieser Einheit vor haben

Im Rahmen der Übung werden Sie Informationen aus digitalen Geländemodellen ableiten und sich mit räumlichen Filtermethoden näher beschäftigen.


## Lernziele 

Nach dieser Übung können Sie:

  *  Neue Rasterdaten durch Anwendung typischer Werkzeuge (Algorithmen) erzeugen
  *  Diese abgeleiteten Informationen in Fragestellungen zielgerichtet einsetzen
  *  Abfagen auf solchen Rasterdaten durchführen.


## Benötigte Materialien

### Daten
  * [Copernicus EU-DEM v1.1](https://land.copernicus.eu/imagery-in-situ/eu-dem/eu-dem-v1.1/view){:target="_blank"} Das EU DEM ist das beste frei erhältiche DEM für Gesamt Europa. Allerdings ist es ein Multisource Modell und daher deutlcih abweichend vom SRTM Modell. 
  * [SRTM Geländemodell opentopography](https://portal.opentopography.org/raster?opentopoID=OTSRTM.082015.4326.1){:target="_blank"} oder
  * [SRTM Geländemodell TileDownloader](https://dwtkns.com/srtm30m/){:target="_blank"} (Benötigt eine Registrierung bei [NASA Earthdata](https://urs.earthdata.nasa.gov/users/new){:target="_blank"}) oder
  * [SRTM OpenDEM](https://opendem.info/){:target="_blank"}
  * [Polygon Marburg Stadtgebiet]({{site.baseurl}}/assets/data/marburg_stadtgebiet.gpkg)

## Aufgaben Lerneinheit 3

## Aufgabe 03-01


* Laden Sie sich mindestestens zwei der oben genannten Datensätze des SRTM Geländemodells von Marburg herunter. Machen Sie die Datenquellen in den nachfolgenden Analysen kenntlich.
*   Was repräsentiert der Datensatz? Schauen Sie sich die Metadaten an. Verschaffen Sie sich einen Überblick über die Version und Fehlerwerte.
*   Projizieren Sie beide Geländemodelldatensätze in ETRS89 UTM32 und schneiden es auf den Ausschnitt des Marburger Luftbildes zu.
*   Berechnen Sie für beide Datensätze die Hangneigung, Exposition/Aspect und Topographischen Index (TPI). 
*   Extrahieren Sie für beide Datensätze die berechneten Werte an der Position des Brunnens am Marburger Oberstadt-Marktplatz.
*   Wenden Sie einen 5*5 Mittelwertsfilter auf die Geländehöhe an und ermitteln Sie erneut für den Marktplatz (Position Brunnen) die Werte von Hangneigung, Exposition/Aspect und Topographischen Index (TPI).
* Berechnen Sie unter Benutzung des Datensatzes ([Marburg Stadtgebiet]({{ site.baseurl}}/assets/data/marburg_stadtgebiet.gpkg)), die minimale, maximale und mittlere Hangneigung für die ausgewiesene Fläche. 

* Zeigen Sie die Werte in einer Tabelle
* Benennen Sie die möglichen Ursachen für etwaige Unterschiede der Resultate der von Ihnen verwendeten Datensätzen (Stichpunktliste). 
{: .notice--success}

### Gewichtung der Aufgaben in Lerneinheit 3

| Aufgabenteil | Gewichtung Teilaufgabe | Gewichtung  Gesamt| 
|:-------------|:----------------------:|:-----------------:|
|**Aufgabe 03-01** | **1.0**  | **0.25** | 


## Hilfestellungen 

Die wichtigen Meta-Informationen zu den SRTM Daten finden Sie auf den jeweiligen Seiten der Daten-Provider (z.B. [CGIAR FAQ](https://srtm.csi.cgiar.org/faq/){:target="_blank"} oder [EU-DEM Meta](https://land.copernicus.eu/imagery-in-situ/eu-dem/eu-dem-v1.1?tab=metadata){:target="_blank"}). Beachten Sie dass sich die Geländemodelle teilweise erheblich unterscheiden.

Verwenden Sie zum Ausschneiden des Rasters einen der Marburg-Layer aus den vorherigen Sitzungen als Vorlage.

Das Stichwort für die QGIS Hilfe zum Mittelwertsfilter ist *"neighbors"*  oder auch *"filter"* in der Werkzeugleiste. Als Resultat wird z.B. `r.neighbors` aus der GRASS GIS Funktionssammlung angezeigt. bei *"filter"* gibt es eine Reihe von Treffern. Hier ist `Simple Filter` aus der Funktionssammlung von SAGA GIS ein guter Einstieg.

Verwenden Sie zonale Statistiken um sich die Minimum-/Maximum-/Mittel-Werte eines definierten Gebiets als Tabelle auszugeben. Für Marburg können Sie entweder ein Stadtgebiet nach ihrer Einschätzung als Polygon digitalisieren oder z.B. auf die Suche nach Verwaltungsgrenzen gehen. Hier wäre z.b. die [Bundesamt für Kartographie und Geodäsie Open Data Server](https://gdz.bkg.bund.de/index.php/default/open-data.html){:target="_blank"}  eine gute Startmöglichkeit.
 Sollte Ihnen das zu mühsam sein können  Sie auch die Datei [Marburg Stadtgebiet]({{ site.baseurl}}/assets/data/marburg_stadtgebiet.gpkg)) aus dem Download nutzen. Beachten Sie bitte dass es selbstverständlich zu unterschidlichen Ergebnissen führt, falls Sie unterschiedliche Polygone als Flächenreferenz verwenden.  
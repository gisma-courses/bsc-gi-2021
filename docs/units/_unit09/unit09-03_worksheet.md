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
  * [Copernicus EU-DEM v1.1](https://land.copernicus.eu/imagery-in-situ/eu-dem/eu-dem-v1.1/view){:target="_blank"} Das EU DEM ist das beste frei erhältiche DEM für Gesamt Europa. Allerdings ist es ein Multisource Modell, das heisst es wird aus unterschiedlichen Datenquellen erzeugt und daher ist es räumlich besser aufgelöst und in der reräsentierten Geländehohe signifikant unterschidelich zu den SRTM basierten Höhenmodellen. 
  * [SRTM Geländemodell OpenTopography](https://portal.opentopography.org/raster?opentopoID=OTSRTM.082015.4326.1){:target="_blank"} Shuttle Radar Topography Mission (SRTM GL1) Global 30m Version 3
  * [SRTM Geländemodell TileDownloader](https://dwtkns.com/srtm30m/){:target="_blank"} (Benötigt eine Registrierung bei [NASA Earthdata](https://urs.earthdata.nasa.gov/users/new){:target="_blank"}) Der Infolink der Oberfläche is korrupt, daher für die notwendigen Metadaten siehe die [NASA JPL Seite](https://www2.jpl.nasa.gov/srtm/). ACHTUNG diese Datei muss als ZIPfile eingeladen werden da es sich um ein [SRTMHGT](https://gdal.org/drivers/raster/srtmhgt.html) Format handelt. 
  * [OpenDEM Deutschland](https://opendem.info/downloads/srtm_germany_dtm.zip) Hierzu unbedingt die [Info Seite](https://opendem.info/srtm_processing.html){:target="_blank"} anschauen!
  * [OpenDEM Europa](https://opendem.info/opendemeu_download_highres.html){:target="_blank"} Auch hier gilt zwingend sich die [Info Seite](https://opendem.info/opendemeu_background.html){:target="_blank"} anzuschauen.
  * [Polygon Marburg Stadtgebiet]({{site.baseurl}}/assets/data/marburg_stadtgebiet.gpkg)

## Aufgaben Lerneinheit 3
Die Ableitung aus und Analyse von Rasterdaten ist ein sehr weites Feld. Es umfasst über die  Bildverarbeitung und Fernerkundung auch die direkte Interpretation und Analyse von etwa Geländemodelldaten die eine besonders prominente Rolle als Grundlagendaten für räumliche Anaysen der Echtwelt spielen. Aufgrund der langen Historie und Bedeutung exisiteren eine fast nicht mehr überschaubare Anazahl unterschiedlichster Geländemodell Daten. Insbesondere die bekannten SRTM Daten liegen in zahlosen Varianten vor. Darüberhinaus gibt es qualitativ bessere Daten. Die obige Datenauswahl soll Ihnen vor Augen führen wo sie überall Treffer landen könnten wenn Sie z.B. nach `SRTM DEM Germany Europe` googlen. Natürlich finden Sie zu allen Daten auch die notwendigen Informationen und können dann bewerten ob Sie diese für adäquat halten. Daher sollen Sie in den folgenden Aufgaben mindestens zwei unterschiedliche Datensätze verwenden ([gerne auch alle](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/le3_5dem.zip)).

## Aufgabe 03-01

* Laden Sie sich mindestestens zwei der oben genannten Datensätze des SRTM Geländemodells von Marburg herunter. Machen Sie die Datenquellen in den nachfolgenden Analysen kenntlich. Sie müssen diese Daten evtl. projizieren und auf die Bezugsgröße Mdes Marburg Luftbildes zuschneiden.

*   Was repräsentiert der Datensatz? Schauen Sie sich die Metadaten an. Verschaffen Sie sich einen Überblick über die Version und Fehlerwerte.
*   Projizieren Sie beide Geländemodelldatensätze in ETRS89 UTM32 und schneiden es auf den Ausschnitt des Marburger Luftbildes zu.
*   Berechnen Sie für beide Datensätze die Hangneigung, Exposition/Aspect und Topographischen Index (TPI). *   Extrahieren Sie für beide Datensätze die berechneten Werte an der Position des Brunnens am Marburger Oberstadt-Marktplatz.
*   Wenden Sie einen 5*5 Mittelwertsfilter auf die Geländehöhe an und ermitteln Sie erneut für den Marktplatz (Position Brunnen) die Werte von Hangneigung, Exposition/Aspect und Topographischen Index (TPI).
* Berechnen Sie unter Benutzung des Datensatzes ([Marburg Stadtgebiet]({{ site.baseurl}}/assets/data/marburg_stadtgebiet.gpkg)), die minimale, maximale und mittlere Hangneigung für die ausgewiesene Fläche. 
* Zeigen Sie die Werte in einer Tabelle
* Benennen Sie die möglichen Ursachen für etwaige Unterschiede der Resultate der von Ihnen verwendeten Datensätzen (Stichpunktliste). 
{: .notice--success}

## Aufgabe 03-02
* 
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
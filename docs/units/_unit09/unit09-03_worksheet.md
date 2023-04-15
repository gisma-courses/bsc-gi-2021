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

Im Rahmen der Übung werden Sie Informationen aus digitalen Geländemodellen ableiten und sich mit räumlichen Filtermethoden näher beschäftigen. Darüber hinaus werden beispielhaft komplexere Werkzeug wie etwa die Berechnung eines Bodenfeuchteindex oder Oberflächenabfluss geübt.


## Lernziele 

Nach dieser Übung können Sie:

  *  Digitale Geländemodelle in irer Vielfalt und in ihrer Bedeutung einschätzen 
  *  Abgeleitete Rasterdaten durch Anwendung typischer Werkzeuge (Algorithmen) erzeugen
  *  Diese abgeleiteten Informationen in Fragestellungen zielgerichtet einsetzen
  *  Direkte und statistisch aggregierte Informationen extrahieren


## Benötigte Materialien

### Daten
  * [Copernicus EU-DEM v1.1](https://land.copernicus.eu/imagery-in-situ/eu-dem/eu-dem-v1.1/view){:target="_blank"} Das EU DEM ist das beste und am höchsten aufgelöste homogene DEM für Gesamt-Europa. `ACHTUNG:` Es es ist aus unterschiedlichen Datenquellen erzeugt und daher räumlich besser aufgelöst als die reinen SRTM basierten Höhenmodelle. 
  * [CGIAR-CSI SRTM V4](https://srtm.csi.cgiar.org/srtmdata/){:target="_blank"} Das CGIAR-CSI SRTM V4 ist weltweit der wohl beste homogen nachprozessierte SRTM Datensatz. Zur neuen Version 4 verlautbart CGIAR-CSI es sei "*envisaged that CGIAR-CSI SRTM Version 4 is our definitive and final release [...]*", [siehe CGIAR FAQ](https://srtm.csi.cgiar.org/faq/){:target="_blank"}.
  * [SRTM Geländemodell TileDownloader](https://dwtkns.com/srtm30m/){:target="_blank"}. `ACHTUNG:` (Benötigt eine Registrierung bei [NASA Earthdata](https://urs.earthdata.nasa.gov/users/new){:target="_blank"}) Der Infolink der Oberfläche is korrupt, daher für die notwendigen Metadaten siehe die [NASA JPL Seite](https://www2.jpl.nasa.gov/srtm/){:target="_blank"}. `ACHTUNG:` diese Datei muss als ZIP-File eingeladen werden da es sich um ein [SRTMHGT](https://gdal.org/drivers/raster/srtmhgt.html){:target="_blank"} Format handelt. 
  * [OpenDEM Deutschland](https://opendem.info/downloads/srtm_germany_dtm.zip) `ACHTUNG:` Hierzu zwingend die [Info Seite](https://opendem.info/srtm_processing.html){:target="_blank"} anschauen, da eine umfangreiche Re-Analyse der SRTM Daten stattgefunden hat. 
  * [OpenDEM Europa](https://opendem.info/opendemeu_download_highres.html){:target="_blank"} `ACHTUNG:` Hierzu zwingend die [Info Seite](https://opendem.info/opendemeu_background.html){:target="_blank"} anzuschauen,da eine umfangreiche Re-Analyse der SRTM Daten stattgefunden hat.  .
  * [Polygon Marburg Stadtgebiet]({{site.baseurl}}/assets/data/marburg_stadtgebiet.gpkg)

## Aufgaben Lerneinheit 3
Die Ableitung aus und Analyse von Rasterdaten ist ein sehr weites Feld. Es umfasst über die  Bildverarbeitung und Fernerkundung auch die direkte Interpretation und Analyse von etwa Geländemodelldaten die eine besonders prominente Rolle als Grundlagendaten für räumliche Anaysen der Echtwelt spielen. Aufgrund der langen Historie und Bedeutung exisiteren eine fast nicht mehr überschaubare Anazahl unterschiedlichster Geländemodell Daten. Insbesondere die bekannten SRTM Daten liegen in zahlosen Varianten vor. Darüberhinaus gibt es qualitativ bessere Daten. Die obige Datenauswahl soll Ihnen vor Augen führen wo sie überall Treffer landen könnten wenn Sie z.B. nach `SRTM DEM Germany Europe` googlen. Natürlich finden Sie zu allen Daten auch die notwendigen Informationen und können dann bewerten ob Sie diese für adäquat halten. Daher sollen Sie in den folgenden Aufgaben mindestens zwei unterschiedliche Datensätze verwenden ([gerne auch alle](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/le3_dem.zip)).

## Aufgabe 03-01

* Laden Sie sich mindestestens zwei der oben genannten Datensätze des SRTM Geländemodells von Marburg herunter. Machen Sie die Datenquellen in den nachfolgenden Analysen kenntlich. Sie müssen diese Daten evtl. projizieren und auf die Bezugsgröße des Marburg-Luftbildes zuschneiden.

*   Was repräsentiert der Datensatz? Schauen Sie sich die Metadaten an. Verschaffen Sie sich einen Überblick über die Version und Fehlerwerte.
*   Projizieren Sie beide Geländemodelldatensätze in ETRS89 UTM32 und schneiden es auf den Ausschnitt des Marburger Luftbildes zu.
*   Berechnen Sie für beide Datensätze die Hangneigung, Exposition/Aspect und Topographischen Index (TPI). *   Extrahieren Sie für beide Datensätze die berechneten Werte an der Position des Brunnens am Marburger Oberstadt-Marktplatz.
*   Wenden Sie einen 5*5 Mittelwertsfilter auf die Geländehöhe an und ermitteln Sie erneut für den Marktplatz (Position Brunnen) die Werte von Hangneigung, Exposition/Aspect und Topographischen Index (TPI).
* Berechnen Sie unter Benutzung des Datensatzes ([Marburg Stadtgebiet]({{ site.baseurl}}/assets/data/marburg_stadtgebiet.gpkg)), die minimale, maximale und mittlere Hangneigung für die ausgewiesene Fläche. 
* Zeigen Sie die Werte in einer Tabelle
* Benennen und Begründen Sie die möglichen Ursachen für etwaige Unterschiede der Resultate der von Ihnen verwendeten Datensätzen. (Stichpunktliste). 
{: .notice--success}

## Aufgabe 03-02
* 
{: .notice--success}

### Gewichtung der Aufgaben in Lerneinheit 3

| Aufgabenteil | Gewichtung Teilaufgabe | Gewichtung  Gesamt| 
|:-------------|:----------------------:|:-----------------:|
|Aufgabe 03-01 | 0.5  | 0.15  | 
|Aufgabe 03-02 | 0.5  | 0.15  | 
|**Aufgabe 03** | **1.0**  | **0.3**  | 

## Hilfestellungen 

### Aufgabe 03-01
Die wichtigen Meta-Informationen zu den SRTM Daten finden Sie auf den jeweiligen Seiten der Daten-Provider (z.B. [CGIAR FAQ](https://srtm.csi.cgiar.org/faq/){:target="_blank"} oder [EU-DEM Meta](https://land.copernicus.eu/imagery-in-situ/eu-dem/eu-dem-v1.1?tab=metadata){:target="_blank"}). Beachten Sie, dass sich die Geländemodelle teilweise erheblich unterscheiden. Dies gilt nicht nur für das Copernicus Modell im Vergleich zu den SRTM Modellen sondern auch die SRTM Modelle obwohl sie alle die geliche Datengrundlage haben weichen erheblich voneinander ab. Die Beschäftigung mit den Metadaten ist insbesondere wichtig für ein erfolgreiches Bearbeiten die letzte Teilaufgabe 03-01.

Verwenden Sie zum Ausschneiden des Rasters einen der Marburg-Layer aus den vorherigen Sitzungen als Vorlage.

Das Stichwort für die QGIS Hilfe zum Mittelwertsfilter ist *"neighbors"*  oder auch *"filter"* in der Werkzeugleiste. Als Resultat wird z.B. `r.neighbors` aus der GRASS GIS Funktionssammlung angezeigt. bei *"filter"* gibt es eine Reihe von Treffern. Hier ist `Simple Filter` aus der Funktionssammlung von SAGA GIS ein guter Einstieg.

Verwenden Sie zonale Statistiken um sich die Minimum-/Maximum-/Mittel-Werte eines definierten Gebiets als Tabelle auszugeben. Für Marburg können Sie entweder ein Stadtgebiet nach ihrer Einschätzung als Polygon digitalisieren oder z.B. auf die Suche nach Verwaltungsgrenzen gehen. Hier wäre z.b. die [Bundesamt für Kartographie und Geodäsie Open Data Server](https://gdz.bkg.bund.de/index.php/default/open-data.html){:target="_blank"}  eine gute Startmöglichkeit.
 Sollte Ihnen das zu mühsam sein können  Sie auch die Datei [Marburg Stadtgebiet]({{ site.baseurl}}/assets/data/marburg_stadtgebiet.gpkg)) aus dem Download nutzen. Beachten Sie bitte dass es selbstverständlich zu unterschidlichen Ergebnissen führt, falls Sie unterschiedliche Polygone als Flächenreferenz verwenden.  
---
title: Lerneinheit 1 - Warm Up QGIS
toc: true
header:
  image: /assets/images/splash_u9-1.png
  image_description: "The QGIS Evolution"
  caption: "The QGIS Evolution CC0 AG UI"
  

---
Der Einstieg in eine komplexe Software ist mühsam und verlangt einiges an Frusttoleranz. Durch die Ähnlichkeit der Software-Werkzeuge und -Konzepte ist es sinnvoll *Analog-Wissen* aufzubauen und sich den Zugang zu den Arbeitsabläufen *logisch-strukturiert* und **nicht** durch *auswendig lernen* der einzelnen Arbeitsschritte zu erarbeiten. Das ist nicht geschenkt zumal GIS Softwarepakete wie ArcGIS oder QGIS zu den wohl komplexesten Softwarearchitekturen gehören.
<!--more-->

## Was wir in dieser Einheit vor haben
Zur Mühsal des Erlernes, sowohl neuer konzeptueller als auch technischer Problemfelder, kommt auch noch die Auseinandersetzung mit einer Softwarearchitektur mit einem ungewohnten Graphical-User-Interface (GUI) hinzu. Um diese Einstiegshürde etwas zu abzupuffern fangen Sie Schritt für Schritt an und beginnen in dieser ersten Einheit mit einigen grundlegenden und typischen Aufgaben, die im Wesentlichen dazu dienen sich an die neue Software und Datenformate zu gewöhnen.  

## Lernziele 

Nach dieser Übung können Sie:
  *  QGIS installieren
  *  eine QGIS Projektdatei anlegen
  *  Datenformate und Datenmodelle unterscheiden
  *  Raster- und Vektordatensätze in QGIS öffnen
  *  Eigenschaften der Datenebenen kontrollieren
  *  Geometrien erzeugen (digitalisieren)


## Benötigte Materialien

### Daten
  * [Luftbild](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/marburg_RE.tif) von Marburg und Umgebung (Beispiel RGB-Bild als Rasterdatensatz)
  * [Wald Flächen](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_nat.zip) Ausschnitt aus dem aktuellen (11/2020) Open Streetmap (OSM) Datensatz
  * [Straßen](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/gis_osm_traffic_1.gpkg) Auszug aus dem aktuellen Open Streetmap (OSM) Datensatz
  * [Räumliche Objekte](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_objects.xls) Excel Tabelle.

### Software
  * [QGIS](https://www.qgis.org/de/site/index.html). Die aktuelle Langzeit Release ist Versin 3.22. Es emfiehlt sich sehr bei der Installation dieser Release die folgenden Installationshinweise zu berücksichtigen:
  
* **Windows** [osgeo4W Installers](https://download.osgeo.org/osgeo4w/v2/osgeo4w-setup.exe){:target="_blank"}. 
* **macOS** [Mac Installationsseite](https://www.qgis.org/de/site/forusers/download.html#mac){:target="_blank"}.
* **Linux** [Linux Installationsseite](https://www.qgis.org/de/site/forusers/download.html#linux){:target="_blank"}. 


### Einführende Materialien

  * [Eine sanfte Einführung in GIS](https://docs.qgis.org/3.28/de/docs/gentle_gis_introduction/index.html){:target="_blank"}: bietet einen gelungenen QGIS zentrierten Überblick der GI-Konzepte. Sehr zu empfehlende Zusatz-Lehrmaterialien  
  * [QGIS Benutzerhandbuch 3.28 DE](https://docs.qgis.org/3.28/de/docs/user_manual/index.html){:target="_blank"}: Die aktuelle deutschsprachige Version. Es ist **die** Referenz für Nutzer. 

## Aufgaben Lerneinheit 1

### Aufgabe 01-01

Dieses Arbeitsblatt dient der Einführung in die verschiedenen Datenmodelle im GIS. Zudem lernen Sie, wie Sie eigene Raumdaten ins GIS importieren oder auch selbst im GIS z.B. durch digitalisieren erstellen können.

  * Erstellen Sie bitte ein Verzeichnis das **ohne** Sonderzeichen und Leerzeichen (im gesamten Pfad/Verzeichnisbaum) benannt ist
  * Legen Sie ein QGIS-Projekt an
  * Laden Sie die Datei `marburg_RE.tif` 
  * Informieren Sie sich über die Eigenschaften des Datensatzes. (Projektion, Datenmodell, Werte-Spektrum)
  * Erzeugen Sie ein Unterverzeichnis namens  `Daten` als Unterordner Ihres Projektverzeichnis. Laden Sie von der Downloadseite der [geofabrik](http://download.geofabrik.de/){:target="_blank"} den Datensatz der Hessen enthält herunter. Entpacken Sie dieses Archiv in den Unterordner `Daten`. 
  * Laden Sie nach dem Entpacken des Archivs die Datei `gis_osm_pois_free_1.shp` in Ihr QGIS Projekt.
  * Informieren Sie sich auch bei diesem Datensatz über die Eigenschaften. (Projektion, Datenmodell, Werte-Spektrum).
  * Schneiden Sie den Datensatz `gis_osm_pois_free_1` auf die Ausdehnung des Luftbildes `marburg_RE.tif` zu 
  * Exportieren Sie diese Punktdaten im *geopackage* Datenformat unter dem Namen `mr_points`
  * Importieren Sie die Tabelle `mr_objects.xls` (Datensatz [Räumliche Objekte](https://raw.githubusercontent.com/gisma-courses/geoinfo-basis-qgis/master/docs/assets/data/mr_objects.xls)) als einen räumlichen Layer in ihr QGIS-Projekt
  * Erstellen Sie auf Grundlage des Luftbildes `marburg_RE.tif` mit dem Koordinatensystem **EPSG:4326 WGS84**:
      * Drei beliebige Flächen (Dateiname `mr_poly`), 
      * drei beliebige Linienzüge (Dateiname `mr_line`) 
      * ergänzen Sie schließlich den Layer `mr_points` um 3 beliebige Positionen (Punkte) Ihrer Wahl
Tipp: Sie können zur besseren Orientierung auch eine Webkarte in Ihr Projekt laden (Weitere Informationen unter Hilfestellungen.
{: .notice--success}



### Aufgabe 01-02 

Leider können wir Sie nicht vollständig an dem Thema der korrekten Verortung von Geodatensätzen - also der adäquaten Projektion- vorbei manövrieren. Im Rahmen der Aufgabe 01-01 haben Sie Raster- und Vektordaten in QGIS importiert sowie eigene Vektordaten erstellt. Die räumliche Information der Daten lag jeweils in geographischen Koordinaten vor. Die von Ihnen benutzte Software QGIS führt immer eine *Echtzeitprojektion* durch mit dem Ziel diese Kugelkoordinaten auf den *flachen* Monitor zu projizieren. Dies hat jedoch im eigntlichen Sinn  nichts mit einer kartographischen korrekten Projektion zu tun. Als Fausregel gilt jedoch, dass nahezu alle räumlichen Analysemethoden und geometrische Berechnungen nur auf korrekt projizierten Daten durchgeführt werden können.

Für den Beginn können wir Sie nur sehr nachdrücklich ermuntern das CRS (Coordinate Reference System) bzw KBS (Koordinatenbezugssystem) ihres *Projekts* und jeder Datenebene identisch zu halten. Für Deutschland ist das amtliche System [ETRS89 UTM 32 ](https://epsg.io/25832){:target="_blank"}. Durch diese Sorgfalt kann eine Fehlpositionierung und so einer der häufigsten Alltagsfehler in der GIS Welt vermieden werden.
{: .notice--danger}

* Erstellen Sie ein neues QGIS Projekt. Laden Sie als erstes die Rasterdatei `marburg_RE.tif` und dann im Anschluss die Vektordatensätze `gis_osm_traffic_1` und `mr_nat` ein.
   * Welche Projektionen besitzen die einzelnen Datensätze?
   * In welcher Projektion werden die Daten angezeigt? 
   * Wo können Sie die Projektion definieren, die zur Darstellung der Daten verwendet werden soll?
   * Worin liegen etwaige Probleme einer *on the fly* bzw. *Echtzeit* Projizierung?
{: .notice--success}

### Gewichtung der Aufgaben in Lerneinheit 1

| Aufgabenteil | Gewichtung Teilaufgabe | Gewichtung  Gesamt| 
|:-------------|:----------------------:|:-----------------:|
|Aufgabe 01-01 | 0.5  | 0.05  | 
|Aufgabe 01-02 | 0.5  | 0.05  | 
|**Aufgabe 01**    | **1.0**  | **0.1**  | 


## Hilfestellungen

Als konkreten Einstieg für die Bearbeitung von Aufgabe 1 möchten wir Ihnen noch einige Einstiegshilfen für QGIS anbieten. QGIS ist ein komplexes Softwareprodukt, das nicht nur in  unterschiedlichen Versionen auf allen gängigen OS-Plattformen verfügbar ist, sondern zusätzlich vollständig individuell anpassbar ist. Daher kursieren im Netz aus den vergangenen 20 Jahren eine Vielzahl von Hilfen, Handbüchern und Tutorials - bei weitem nicht jeder Google-Treffer ist geeignet und nicht jedes Tutorial passt auf Ihre genutze Version.

Einen ersten Anlaufpunkt für konkrete Informationen stellt die integrierte Hilfe des Softwarepakets dar. Darüber hinaus ist eine umfangreiche Dokumentation verfügbar. Die jeweils aktuelle [QGIS Landing Page](https://www.qgis.org/de/site/forusers/index.html){:target="_blank"} ist der zentrale Zugang zu allen offiziell vom Projekt verfügbar gemachten Dokumentationen. 

Für alle Hilfeseiten gilt: achten Sie **unbedingt** darauf die Hilfe zu Ihrer passenden QGIS Version anzuschauen. Falls diese (noch) nicht verfügbar ist versuchen Sie es mit der jeweils nächsten Vorgängerversion und besser mit der englischsprachigen Hilfe, da diese die Referenz für alle Übersetzungen darstellt. 

**Achtung** der Übergang von QGIS2.x auf QGIS3.x hat grundlegende Veränderungen mit sich gebracht. Als konkrete Anleitung für die aktuellen Versionen sind QGIS  2.x Tutorials und Hilfen faktisch **unbrauchbar**. 
{: .notice--danger}

### Einrichtung eines QGIS-Projekts 

Wir raten Ihnen **dringend** bei Rechnern mit einem Heimatverzeichnis in der Cloud/im Netz (z.B. in der Uni-Pools) die Daten auf einer **lokalen Festplatte** abzuspeichern.  Hierfür müssen Sie zunächst eine Ordnerstruktur für Ihr Projekt anlegen. Hilfe zur Projektdatei finden Sie unter [Arbeiten mit Projektdateien](https://docs.qgis.org/3.28/de/docs/user_manual/introduction/project_files.html){:target="_blank"}. 

Bitte achten Sie zwingend darauf **keine** Sonderzeichen, Umlaute oder Leerzeichen zu verwenden. 
{: .notice--danger}

### Digitalisieren von Geometriedaten

Die manuelle Erzeugung von Vektordaten wird allgemein als *digitalisieren* bezeichnet. Dabei erzeugen Sie auf z.B. Grundlage von Rasterbilddateien wie Satellitenbildszenen, Luftbildern, thematischen und topographischen Karten, einfachen Screenshots oder anderen Vorlagen Ihre eigenen vektorbasierten Datensätze. Schauen Sie sich dazu die QGIS Hilfe zur  [Digitalisierung](https://docs.qgis.org/3.28/de/docs/user_manual/working_with_vector/editing_geometry_attributes.html){:target="_blank"} an. Ein ausführliches Anwendungsbeispiel finden Sie unter [Digitizing Forest Stands](https://docs.qgis.org/3.28/en/docs/training_manual/forestry/stands_digitazing.html){:target="_blank"}.

### Zuschneiden von Vektordaten 
Diese Aufgabe ist ein gutes Beispiel wie knifflig die Suche nach Hilfe sein kann. Natürlich gilt immer dass Sie das Internet durchsuchen können. Versuchen Sie es zum Beispiel mit "*zuschneiden von vektordaten qgis*". Sie haben viele Treffer aber bei genauer Betrachtung finden Sie nichts über das Zuschneiden von Vektordaten mit Hilfe einer Raster-Datei. Was geschieht beim Zuschneiden? Sie müssen offensichtlich einem Werkzeug mitteilen was die gewünschte Ausdehnung ist. Fangen Sie mit diesem Wissen nochmal an. Nur diesmal nutzen Sie die Werkzeug-Leiste und tippen dort "*zuschneiden*" bzw. "*clip*" ein. Es werden einige Treffer angezeigt. Unter anderem auch *Vektor auf Ausdehnung zuschneiden*. Wenn Sie diesen auswählen können Sie bei der *Ausdehnung* drei Optionen wählen...

###  Tabellen in QGIS importieren
Der Import von Tabellen beinhaltet eine Vielzahl von Fallstricken. Ganz generell nutzen Tabellendaten in QGIS nur dann etwas wenn sie entweder selbst Koordinaten (also geographische Informationen) enthalten oder aber einen Schlüssel wie z.B eine ID die bereits existierenden Geometriedaten zuzuordnen ist. Generell können sie aber folgendem Schema folgen:
[Import von Tabellenblättern oder CSV-Dateien](http://www.qgistutorials.com/de/docs/3/importing_spreadsheets_csv.html){:target="_blank"}.

### Arbeiten mit Projektionen
Das Kapitel 
[Arbeiten mit Projektionen](https://docs.qgis.org/3.28/de/docs/user_manual/working_with_projections/working_with_projections.html){:target="_blank"} ist für Anfänger*innen schwer verständlich. Wichtig ist hier vor allem das korrekte Zuweisen von Projektionen. Für das Umprojizieren von Vektordaten lohnt sich ein Blick in [Reprojecting and Transforming Data](https://docs.qgis.org/3.28/de/docs/training_manual/vector_analysis/reproject_transform.html){:target="_blank"}.
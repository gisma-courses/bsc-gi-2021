---
title: Lerneinheit 4 - Kosten und Kriterien
toc: true
header:
  image: /assets/images/splash_L04.png
  image_description: "Least Cost Path Analysis"
  caption: "Least Cost path Analysis on a MCE cost raster at the MOF. CC0 AG UI"
  


---


In dieser Aufgabe sollen Sie unterschiedliche Analysen auf der Grundlage vorgegebener Kriterien oder Merkmalsausprägungen durchführen. Das heißt Sie sollen die  *Eignung* von Rasterzellen (Raumeinheiten) für eine bestimmte Nutzung bewerten. Sie können Werte so evaluierter Rasterzellen auch nutzen um die *Überwindung*  räumlicher  *Widerstände* oder auch  *Kosten* zu akkumulieren, um für einen spezifischen Zweck geeignete Strecken oder Korridore auszuweisen.

<!--more-->

Nimmt man eine Position  A und eine Position B auf einem solchen Raster als Start und Ziel, kann die kostengünstigste Strecke als Bewegung durch einen Raum mit unterschiedlicher *Reibung* interpretiert werden, d.h. Sie können die Werte eines Pixels als Kosten für das Betreten/Nutzen/Überwinden dieses Pixels interpretieren. Diese Kosten können durchaus mit den kategorialen Merkmalsausprägungen wie z.B. *leicht* oder *beschwerlich*, *billig* oder *teuer*, *attraktiv* oder *unattraktiv* usw. beschrieben werden. Vor diesem Hintergrund müssen die genutzten Kriterien für die Planung einer z.B. "*kostengünstigen Strecke*" immer in Bezug auf die Fragestellung bzw. Zielsetzung bewertet werden. 


  
## Was wir in dieser Einheit vor haben

Im Rahmen der Übung werden Sie eine einfache Eignungsanalyse und eine Kostenpfadanalyse durchführen. Dazu gehört die vollständige Datenvorbereitung und die Interpretation der genutzen Kriterien sowie der Resultate.


## Lernziele 

Nach dieser Übung können Sie:

  *  unterschiedlichste Datenebenen zielorientiert bearbeiten und kombinieren
  *  die Bedeutung verschiedener Kriterien identfizieren und einschätzen
  *  durch Verrechnen geeigneter Datenebenen eine Eignungsanalyse durchführen
  *  eine Kostenanalyse planen und durchführen

## Benötigte Materialien

* Geländemodell des Marburg Open Forest (MOF) in 1 Meter Auflösung
* Corine Landnutzung Daten für den MOF

Die Daten finden Sie im  Zip-Archiv  [Daten-Aufgabe-L04]({{ site.baseurl }}/assets/data/Daten-Aufgabe-L04.zip)
* Open Street Map (OSM) Wegedaten für den  MOF
* Geländemodell des Marburg Open Forest (MOF) in 1 Meter Auflösung
* Corine Landnutzung Daten für den MOF
*  Koordinaten (ETRS89, UTM32 EPSG:25832) Position *Parkplatz*  (478188,5632178), Position Grillhütte (476170,5631657)

## Aufgaben Lerneinheit 4

### Aufgabe 04-01

Sie sollen eine Entscheidungsfindung auf der Grundlage mehrerer Kriterien durchführen. Konkret sollen Sie die Eignung des Uniwalds als Wildkatzenhabitat untersuchen. Hierfür sollen folgende Aussagen gelten:
* Wildkatzen bevorzugen Waldgebiete
* Wildkatzen bevorzugen mittelsteile und steile Hanglagen
* Waldgebiete werden gegenüber Hangebieten bevorzugt
{: .notice--success}
*  Laden Sie die Daten herunter (prüfen Sie diese in gewohnter Weise)
*  Berechnen Sie die Hangneigung 
*  Extrahieren Sie die aus den [Corine Landnutzungsdaten](https://land.copernicus.eu/pan-european/corine-land-cover/clc2018?tab=mapview) alle Waldflächen so daß Sie ein Raster mit den Werten 1 für *Waldflächen* und 0 für *Keine Waldflächen* erhalten. (Sie finden bereits zugeschnittene Corine-Daten im heruntergeladenen Archiv unter dem Dateinamen `clc2018_1m_MOF_25832.tif`). Tip dieser Vorgang wird auch Reklassizierung von Daten genannt. 
*  Zur Vorbereitung der Multikriterien-Evaluation sollen die kontinuierlichen Hangneigungswerte in *ganzzahlige* kategoriale Klassen überführt (reklassifiziert) werden. D.h. bei der Reklassifizierung der Hangneigung in drei Klassen 0-15 Grad = Klasse mit dem Wert 1, 15-30 Grad = Klasse mit Wert 2 und  > 30 Grad = Klasse mit Wert 3 (1=flach, 2=mittlere Neigung und 3=steile) werden kategoriale Zielvariablen erzeugt.
* Legen Sie für **jede Datenebene** eine Gewichtung gemäß der von Ihnen festgelegten Bedeutung in Relation zu ihrer Eignung fest (z.B. Wald/Nichtwald = Faktor 0.5, Hangneigung = Faktor 0.3). Beachten Sie bitte dass Werkzeuge wie das `WMCA Weighted Multicriteria Analysis` eine Gewichtungssumme von genau 1.0 erwarten. Daher müssen die Gewichte entsprechend verteilt werden.
* Legen Sie für **jede Klasse** in diesem Layer eine Bewertung von 0-10 fest (z.B. Wald = 10, Nichtwald = 1, Hangneigung Klasse 1 = 5 etc.) Bedenken Sie bitte dass die Festlegung der Bewertung die Bedeutung der Kriterien für die Fragestellung berücksichtigen muss. 
* Erläutern Sie die Ergebnisse  in max. 2 Sätzen.
{: .notice--success}


## Aufgabe 04-02

Sie sollen einen Cross-Crountry Fitness-Trail durch den Uniwald (Marburg Open Forest, MOF) bei Caldern planen. Der Trail beginnt am Parkplatz in der Nähe des Kreisverkehrs am südöstlichen Rand und endet am Grillplatz am nordwestlichen Ende. Machen Sie sich zunächst mit dem Konzept der Kostenanalyse vertraut (siehe Hilfestellungen und Reader)

Die Vorgaben zur Streckenplanung sind: 
* die Strecke soll bevorzugt durch Wald führen
* die Strecke soll möglichst weit von Wegen entfernt sein
* die Strecke soll maximale Steigungen bevorzugen 
{: .notice--success}


*  Download und Überprüfung der zur Verfügung gestellten Daten
*  Berechnen Sie die Hangneigung 
*  Nutzen Sie reklassifizierten Corine Daten aus Aufgabe 04-01 (*Wald*, *Kein Wald*).
*  Berechnen Sie ein Entfernungsraster das den Abstand zu den Wegen (`OSM_roads_MOF_25832.gpkg`) beinhaltet (räumliche Auflösung wie das Hangneigungsraster).
*  Legen Sie für jede Rasterklasse (z.B. Wald Nicht-Wald) Werte fest, die die *Kosten* bzw den *Reibungswert* zur Überwindung/Nutzung der Zelle abbildet. Sinnvoll ist es also (im Sinne der obigen Vorgaben) unattraktive Zellen mit hohen Werten und attraktive Zellen mit niedrigen Werten zu reklassifizieren. 
* Verrechnen Sie die einzelnen Raster zu einem Gesamtkostenraster. Überlegen Sie sich dabei ob allen drei Kriterien gleichgewichtet eingehen sollen, oder ob Sie z.B. der Hangneigung eine höhere Bedeutung zuweisen wollen (z.B. wegen höherem Trainingseffekt).
* Berechnen Sie auf dieser Grundlage den im Sinne der Vorgaben attraktivsten (=*"kostengünstigsten"*) Weg zwischen dem Start und Zielpunkt.
Beschreiben Sie das Ergebnis, fügen Sie aussagekräftige Grafik(en) ein und begründen Sie stichpunktartig die einzelnen Arbeitsschritte.
{: .notice--success}




### Gewichtung der Aufgaben in Lerneinheit 4

| Aufgabenteil | Gewichtung Teilaufgabe | Gewichtung  Gesamt| 
|:-------------|:----------------------:|:-----------------:|
|Aufgabe 04-01 | 0.4  | 0.16  | 
|Aufgabe 04-01 | 0.6  | 0.24  | 
|**Aufgabe 04** | **1.0**  | **0.4**  | 

## Hilfestellungen 


- Falls Sie das Plugin `WMCA Weighted Multicriteria Analysis` (WMCA) nutzen, müssen die kontinuierlichen Werte für die Hangneigung und für die Entfernung von der Straße in diskrete Klassen umgewandelt werden. Das WMCA Werkzeug kann jedoch maximal 100 Klassen verarbeiten, daher müssen bei Verwendung dieses Werkzeugs die kontinuierlichen Werte reklassifiziert werden (z.B jeweils 25 Meter Entfernungsklassen und alles > 200 Meter Entfernung in ene Klasse, bzw. je 5 Grad Neigung von 0 Grad bis 30 Grad  je eine Klasse und > 30 Grad eine Klasse). Weiterhin entfallen seperate Normalisierung und Gewichtung.
- Falls Sie den `Raster-Rechner` verwenden ist diese Reklassifikation nicht notwendig jedoch müssen Sie dann Gewichtung und Normalisierung in die Berechnung integrieren. 
{: .notice--info}


*  Das Plugin `WMCA Weighted Multicriteria Analysis` (WMCA) ist sehr komfortabel für die gewichtete Multikriterien Analyse. Es wird nach der Installation unter dem Haupt-Menü `Raster` bzw. in der `Erweiterungswerkzeugleiste` angezeigt (für die reguläre Installation müssen Sie *"Auch experimentelle Erweiterungen anzeigen"* unter den Einstellungen aktivieren). **Achtung:** Aktuell (seit 2021) gibt es je nach QGIS Version eine Python Fehlermeldung nach der Installation des Plugins. Bitte nutzen Sie dann den alternativen [Kurs-Repo-Download](https://github.com/gisma/Weighted-Multi-Criteria-Analysis---WMCA/archive/refs/heads/master.zip) des Plugins. Weitere Infos unter [Kurs-WMCA-Repositories](https://github.com/gisma/Weighted-Multi-Criteria-Analysis---WMCA). Installieren Sie das herunter geladene Plugin über das QGIS-Menü `Erweiterungen -> Erweiterungen verwalten und installieren -> Aus Zip installieren`.

* Weitere und deutlich tiefergehende Hilfe für den gesamten Arbeitsablauf finden Sie QGIS-spezifisch unter [Multi Criteria Overlay Analysis (QGIS3)](https://www.qgistutorials.com/en/docs/3/multi_criteria_overlay.html). 
*  Da es sich bei dieser Vorgehensweise um ein häufig angewandtes Raster-GIS-Konzept handelt, werden Sie unter allen GI Softwarepaketen ähnliche Werkzeuge finden. So ist auch etwas das  [MCE Tutorial für SAGA GIS](https://sourceforge.net/projects/saga-gis/files/SAGA%20-%20Documentation/Tutorials/Multi_Criteria_Evaluation_Tutorial/MultiTutorial2.pdf/download) ein hilfreiche Ressource um den Vorgang zu verstehen.
* Typische Rechenoperationen auf Raster Daten u.a. auch das Reklassifizieren von Daten können mit dem [Raster-Rechner](https://docs.qgis.org/3.22/en/docs/) durchgeführt werden. Der `Raster-Rechner` ist als Raster Taschenrechner für zahlreiche Operationen ein extrem wichtiges und mächtiges Werkzeug. Alternativ und für eine einfache Reklassifikation einfacher ist das QGIS- Werkzeug `Nach Tabelle neuklassifizieren`. Für einen Überblick der verfügbaren Werkzeuge der Daten-(Re)klassifikation geben Sie `klassifizieren` oder `reclass` in der Werkzeugleiste ein. Weiterhin finden Sie im Netz zahlreiche Anleitungen zum Thema Reklassifizieren z.B. im Blogbeitrag [How to reclassify a raster layer in QGIS](https://fivequestionz.home.blog/2020/02/08/how-to-reclassify-a-raster-layer-in-qgis/) oder auf etwa auf YouTube [Slope Analysis/Reclassify from a DEM in QGIS 3](https://www.youtube.com/watch?v=7eIFvZ4fU6k). Auch die Hilfeseiten von [GRASS GIS](https://grass.osgeo.org/grass76/manuals/r.reclass.html) und [SAGA GIS](http://www.saga-gis.org/saga_tool_doc/2.2.5/grid_tools_15.html) beschreiben den technischen Vorgang. * Die Normalisierung von Raster Datenwerten kann sehr einfach mit dem SAGA Modul `Grid Normalisation` durchgeführt werden. Alternativ können Sie diese auch mit dem [Raster-Rechner](https://docs.qgis.org/3.22/de/docs/user_manual/working_with_raster/raster_analysis.html#raster-calculator) nach der Formel `xnorm = (x-min(x))/(max(x)-min(x))` berechnen (wobei x das Raster, min(x) und max(x) jeweils das Minimum bzw. Maximum aller Werte des Rasters sind). 
* Die Gewichtung kann dann durch eine einfache Multiplikation (`Raster-Rechner`) des jeweiligen Raster mit dem Gewichtungswert erreicht werden. Z.B. Gleichgewichtung `Raster1*Raster2*Raster3/3` Gewichtung Raster1 Faktor 0.5 Raster2 und Raster3 Faktor 0.25 `0.5*Raster1 + 0.3* Raster2 + 0.2*Raster3`. Falls Sie mit anteiligen Werten von 1 gewichten (Prozent), achten Sie darauf dass die Summe aller Gewichtungsfaktoren 1 ergibt.
Zur exakten Digitalisierung von Punkten ist die Extension `Numerical Digitize` sehr hilfreich. Sie wird nach der Installation in die Digitalisierungs-Leiste eingehangen.
* Zur Kostenanalyse können sie das Plugin `Least Cost Path` installieren. Es wird unter den Verarbeitungswerkzeugen als eigener Menüeintrag `Cost Distance Analysis` angezeigt. Auch hierfür gibt es sowohl für QGIS als auch für die verwandten GRASS- und SAGA-Werkzeuge zahlreiche Videos und Tutorials (z.B. [Least Cost Path](https://www.youtube.com/watch?v=6dodHcHm7ws)). Beachten Sie bei der Google-Suche, dass Sie nur aktuelle und für Ihre QGIS-Hauptversion gültige Anleitungen -also für QGIS 3.x- nutzen. Sollten Sie Interesse an den Konzepten und hinsischlich des Anwendungsbezugs (insbesondere für die Fragestellung auf der Landschaftsskala) haben, lohnt ein Blick in   [Least-Cost Modelling and Landscape Ecology: Concepts, Applications, and Opportunities](https://link.springer.com/article/10.1007/s40823-016-0006-9). 
* Für die Berechnungen von Entfernungen eignet sich das `Nähe/Proximity Werkzeug`. Bitte beachten Sie, dass sie Vektordaten zuerst in Raster Daten umwandeln müssen (`Raster->Conversion->Rastern`). 
* Weitere Unterstützung finden Sie unter [QGIS Materialien](https://gisma-courses.github.io/geoinfo-basis-qgis//unit08/unit08-01_reader_QGIS_01.html)





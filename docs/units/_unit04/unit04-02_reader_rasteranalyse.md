---
title: Geometrische Analysen - Voronoi Polygone
toc: true
toc_label: Inhalt
header:
  image: /assets/images/splash_L03.png
  image_description: "SRTM ElevationModel Data Marburg"
  caption: "SRTM Elevation Model Data Marburg. CC0 AG UI"

panel1:  
  - url: https://minibsc.gis-ma.org/GISBScL3/de/image/thiessen-punkte.gif
    image_path: https://minibsc.gis-ma.org/GISBScL3/de/image/thiessen-punkte.gif
    title: " Unregelmäßig verteilte Punkte im Raum. (z.B. Parkbänke)"
    alt: "Unregelmäßig verteilte Punkte im Raum. (z.B. Parkbänke)"
  - url: https://minibsc.gis-ma.org/GISBScL3/de/image/thiessen-polygone2.gif
    image_path: https://minibsc.gis-ma.org/GISBScL3/de/image/thiessen-polygone2.gif
    title: "Thiessen Polygone zu den Punkten im Raum."
    alt: "Thiessen Polygone zu den Punkten im Raum."    
---


Zum Einstieg in die Thematik der Raumanalyse haben wir die Integration des einfachsten Raumkonzepts, der Voronoi Polygonisierung gestellt. Sie steht beispielhaft für das Erzeugen von geometrisch begründeten raumkontinuierlichen Interpolationskonzepten. Diese Betrachtung wird um einige komplexere Interpolationsverfahren erweitert.


## Distanzbeziehungen: Voronoi Polygone als Ableitung von Entfernung und Nachbarschaft	

Wir erweitern nun unser Wissen über die Analyse von Distanzen zwischen räumlichen Objekten. Es ist häufig sinnvoll, in einer ersten Analyse ohne räumlich einschränkende Bedingungen zu arbeiten, z.B. dann wenn diese Informationen fehlen. Die Bezeichnung „Nähe“ (Proximität) verweist auf eine gewisse Ungenauigkeit. Als qualitative Begriffe können hierfür verwendet werden: „nah“, „weit“ oder „in der Nachbarschaft von“. Für GI-Systeme müssen diese Begriffe objektiviert und operationalisiert werden. Diesem Maß muss folglich ein Distanzkonzept zugrunde gelegt werden z. B. die euklidische Distanz oder Wegzeiten. In einem zweiten interpretativen Schritt muss anschließend entschieden werden, welche Einheiten diese Art der Nähe definieren. Es gibt im Sinne der Zielsetzung einer Fragestellung nur geeignete und weniger geeignete Maße, nicht aber richtige oder falsche. Daher ist es von zentraler Bedeutung, dass man für die untersuchten Objekte eine sinnvolle Nachbarschaftsbeziehung definiert.

In Analysen der Nähe oder Nachbarschaft geht es häufig um Einflussgebiete oder Einzugsgebiete also um räumliche Wirkungs- oder Prozessmuster. Sie kennen bereits solche Fragen andere sind jedioch neu oder komplexer:

  *     Welche oder wie viele Diskotheken liegen im Umkreis von 300m um einen bestimmten Standort (Outdoorcamp)?
  *     Wie viele Täler können von einem Aussichtspunkt eingesehen werden?
  *     Liegt ein bestimmter Standort in der Lärmzone eines Fun-Parks?

In der Folge werden einige Methoden zur Berechnung von Distanzen zwischen Raumobjekten etwas ausführlicher als bisher erörtert. Wegen der unterschiedlichen Art der Diskretisierung des Raums muss -wie bereits gewohnt- zwischen Vektor- und Rastermodell unterschieden werden.

### Voronoi-Polygone 

[Voronoi-Polygone](https://de.wikipedia.org/wiki/Voronoi-Diagramm) (oder auch Thiessen-Polygone) entsprechen einem in der Natur (z. B. Pflanzenzellen) und in den Raumwissenschaften häufig beobachteten Organisationsprinzip, Daher sind die Anwendungsmöglichkeiten mannigfaltig. Zum Beispiel können Voronoi-Polygone in erster Näherung verwendet werden, um aus unregelmäßig und isoliert erhobenen Bodenproben Bodenkarten zu erstellen. Dabei muß die Annahme getroffen werden, dass nichts weiter über den Raum zwischen den beprobten Orten bekannt ist und die Grenzlinie zwischen zwei Stichproben mit unterschiedlichem Bodentyp willkürlich auf halben Weg zwischen ihnen liegt (siehe z.B. Jones 1997, S. 48). Die Voronoi-Polygone können auch verwendet werden, um Einzugsgebiete von Geschäften oder Dienstleistungseinrichtungen abzugrenzen, wenn keine weiteren Informationen über raumwirksame Strukturen zur Verfügung stehen.

Voronoi-Polygone sind also eine elementare Methode, um *Nähe* (Proximität) bzw. *Nachbarschaften* auch aus 0-dimensionalen Daten geometrisch zu bestimmen. Voronoi-Polygone können verwendet werden, wenn Regionen gesucht sind, die jeweils am nächsten zu einem Punkt innerhalb einer Menge von unregelmäßig verteilten Punkten liegen. Ein Voronoi-Polygon definiert im zweidimensionalen Fall eine Fläche um einen Punkt, in der jede Raumstelle näher an diesem Punkt liegt als an irgendeinem anderen Punkt. Solche Konstrukte können auch in höheren Dimensionen gebildet werden, wobei dann Voronoi-Polyeder entstehen.

{% include media1 url="assets/images/unit04/suisse1.html" %}
[Full-screen Version der Karte]({{ site.baseurl }}/assets/images/unit04/suisse1.html){:target="_blank"} 
<figure>
  <figcaption>Die blauen Kreisflächen sind ein lehrbuchhaftes Beispiel für unregelmäßig verteilte Meßpunkte im Raum - in diesem Fall offizielle Regenmessstationen in der Schweiz. Die unterschiedlichen Kreisflächen visualisieren die mittlere langjährige Niederschlagsmenge an der Messstation (nicht in der Legende abgebildet). Die überlagerten und entsprechend der Niederschlagmenge der enthaltenen Messtation eingefärbten Polygone sind die Voronoi- oder Voronoi-Polygone genannten Flächen **nächster Distanz** zu den Punkten (gisma 2021)" </figcaption>
</figure>

Man kann Voronoi-Diagramme auch um eindimensionale Objekte (Linien) bilden, was dann zu komplexeren Formen führt (siehe unten stehende Abbildung). In dieser Unit beschränken wir uns jedoch auf den einfachsten und am häufigsten verwendeten Fall von Voronoi-Polygonen für Punkte. Eine weiterführende Diskussion bietet (Boots 1999).


## Voronoi-Polygone Interaktiv

Die Ermittlung von Voronoi-Polygonen ist auch auf Rasterdaten möglich. Im Raster wird dann nicht mehr von Polygonen gesprochen sondern von *Proximitätszonen*. Von einer Anzahl von Punkten aus, gegeben als einzelne Zellen in einem Raster, kann ganz mit Hilfe einer Distanztransformation die Zugehörigkeit der Zelle zur Mittelpunktszelle bestimmt werden. Die Berechnung im Raster hat den enormen Vorteil, dass zusätzlich zur  euklidischen Distanzmetrike weitere Faktoren wie z.B. Oberflächenreibung oder Kosten als Gewichtungsfaktoren usw. berücksichtigt werden können.

{% include media1 url="assets/images/unit04/Voronoi.html" %}
[Full-screen Version der Modells]({{ site.baseurl }}/assets/images/unit04/Voronoi.html){:target="_blank"} 
<figure>
  <figcaption>Experimentieren Sie. Mit dem Slider können Sie die Anzahl der Punkte bestimmen und mit Setup die Zellenbasierte Berechnung der Proximitätszonen starten. Wenn Sie den Go Button aktivieren, können sie interaktiv die Punkte verschieben und die Neuberechnung verfolgen.</figcaption>
</figure>








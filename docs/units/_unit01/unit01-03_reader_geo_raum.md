---
title: Objekte im Raum
toc: true
toc_label: Inhalt

header:
  image: /assets/images/splash_L01_1.png
  image_description: "MineSeeker World "
  caption: "What is reality? CC0 AG UI"

---


Wie setzen wir in der Geographie am einfachsten und effizientesten die Abstraktion unserer Weltsicht um? Prinzipiell kann die geographische Repräsentation von Raum mit Hilfe zweier unterschiedlicher Konzepte durchgeführt werden: Zum einen können eindeutige Objekte identifiziert werden, sogenannte diskrete Geoobjekte, dem gegenüber steht das Konzept der kontinuierlichen Räume oder Felder. Im Prinzip sind diskrete (Geo-) Objekte alles, was auf irgendeine Weise abgrenzbar und zählbar ist. Also z.B. Autos, Häuser, Fußgänger, Blumen, Bären, Fußballplätze und so weiter. Felder hingegen beschreiben kontinuierliche, sich raum-zeitlich verändernde Attributwerte oder Merkmalsausprägungen von Räumen (zb. Lufttemperatur, Bevölkerung / Hektar).



<html>
<a href="http://upload.wikimedia.org/wikipedia/commons/thumb/d/d1/Fr%C3%A4nkische-Schweiz-westliche-Kante-16-05-2005.jpeg/640px-Fr%C3%A4nkische-Schweiz-westliche-Kante-16-05-2005.jpeg?uselang=de" title="View from the west of the Fränkische Schweiz. In the center of the photo you can see the escarpment outlier // Walberla// "><img src="http://upload.wikimedia.org/wikipedia/commons/thumb/d/d1/Fr%C3%A4nkische-Schweiz-westliche-Kante-16-05-2005.jpeg/640px-Fr%C3%A4nkische-Schweiz-westliche-Kante-16-05-2005.jpeg?uselang=de" width="120%" alt="Fränkische Schweiz Westrand"></a>
</html>
<figure><figcaption>
Abbildung 01-03: Blick auf die Fränkische Schweiz von Westen. In der Bildmitte ist der Zeugenberg Walberla zu sehen (Quelle: <a href="https://commons.wikimedia.org/wiki/User:Arnomane" > Daniel Arnold </a>, <a href="https://commons.wikimedia.org/wiki/File:Fr%C3%A4nkische-Schweiz-westliche-Kante-16-05-2005.jpeg" > via WikiMedia</a>)
</figcaption></figure>


Beginnen wir mit einem geographischen Begriff von Raum, der uns aus dem Alltagswissen vertraut ist. So kennen viele die Region der Fränkischen Schweiz. Wir assoziieren mit solchen *Raumentitäten* eine mehr oder weniger diffuse gleichwohl abgegrenzte Raumausdehnung (Region) oder die Vorstellung einer Landschaft (vgl. Abb. 01-03). Derart als Entitäten empfundenen Räumen werden häufig auch Attribute wie kulinarische, kulturelle oder freizeitorientierte Aspekte zugeordnet. So ist die Fränkische Schweiz sowohl für ihre Weine und lokalen Biere bekannt aber auch beispielsweise für ihre Osterbrunnen (vgl. Abb. 01-04) oder ihr touristisches Potenzial.

Ein weiteres sehr eingängiges Beispiel für solche räumlichen Übergänge stellt das Relief dar (vgl. Abb. 01-05), denn die Erdoberfläche weist eine quasi-kontinuierlich unterschiedliche Höhe auf. Die räumliche Verbreitung dieser Merkmalsausprägung variiert  kontinuierlich. Versucht man vor diesem Hintergrund eine räumliche Abgrenzung der Fränkischen Schweiz so mögen nicht nur die religiösen oder kulinarischen Vorlieben der Bevölkerung, sondern auch z.B. die morphologischen oder edaphischen Eigenschaften der Erdoberfläche die sie bevölkern  inhomogen im Raum verteilt sein. Die Karte der Fränkischen Schweiz (vgl. Abb. 01-06) versucht dies durch ein radiales Verblassen der Farben im Randbereich zu symbolisieren, allerdings ohne zu verdeutlichen wie es zu dieser Abgrenzung kommt.

![]({{ site.baseurl }}/assets/images/unit01/eierbrunnen.jpg)
<figure><figcaption>
Abbildung 01-04: Der Marktplatz von Ebermannstadt mit dem geschmückten Marienbrunnen und Osterbäumen. Beispielhaft für den typischen Osterschmuck der fränkischen Schweiz (Behrendes 2010)
</figcaption></figure>


![]({{ site.baseurl }}/assets/images/unit01/DEM_franken.png)
<figure><figcaption>
Abbildung 01-05: Digitales Geländemodell der Fränkischen Schweiz und angrenzender Regionen. Datengrundlage SRTM Daten 90 Meter räumliche Auflösung (GIS.MA 2009)
</figcaption></figure>

<html>
 <a href="http://upload.wikimedia.org/wikipedia/commons/thumb/2/28/Fraenkische_Schweiz.png/800px-Fraenkische_Schweiz.png" title="Map of the Fränkische Schweiz ">  <img src="http://upload.wikimedia.org/wikipedia/commons/thumb/2/28/Fraenkische_Schweiz.png/800px-Fraenkische_Schweiz.png"  alt="Map of Frankonian Switzerland">  </a>
 </html> 
<figure><figcaption>
Abbildung 01-06: Karte der Fränkischen Schweiz (Quelle: <a href="https://commons.wikimedia.org/wiki/User:Mikmaq" > Mikmaq 2009</a>, <a href="https://commons.wikimedia.org/wiki/File:Fraenkische_Schweiz.png" > via WikiMedia</a>)
</figcaption></figure>


## Diskrete und kontinuierliche Objekte in GI-Systemen

Diskrete Geobjekte sind durch eine klare räumliche Abgrenzbarkeit gekennzeichnet, während räumlich kontinuierliche Ausprägungen zunächst keine eindeutig objektbezogene räumliche Abgrenzbarkeit aufweisen. Diese Regel ist abhängig von der Beobachtungs- oder Interessenskala. Hinzu kommt, dass die binäre Logik computergerechter Datenverarbeitung eine Begrenzung der Informationen notwendig macht. In der Praxis der Geoinformationssysteme werden daher auch kontinuierliche Felder wie räumlich abgegrenzte Objekte behandelt also – unter Berücksichtigung einer für die Fragestellung geeigneten Skala – in diskrete Raumeinheiten aufgeteilt. Der wesentliche Unterschied zu dem Konzept der diskreten Objekte im leeren Raum ist, dass diese mit bekannter Position in einem ansonsten leeren Raum existieren, während in diskrete Objekte zerlegte Kontinua diesen Raum lückenlos und überschneidungsfrei mit ihren Eigenschaften abbilden und beschreiben.

## Abstraktion für Einsteiger

Betrachten Sie das unten stehende Luftbild (Abb. 01-07) und überlegen Sie, wie Sie die Repräsentation dieses Raumes vornehmen würden. Erfassen Sie folgende Merkmale:


*     Landnutzung in Form von Landnutzungsarten
*     Straßennetz
*     Bebauungsfläche

![]({{ site.baseurl }}/assets/images/unit01/Sanspareil_Luftbild_West.jpg)
 <figure><figcaption>
Abbildung 01-07: Luftbild des Felsengarten Sanspareil (Fränkische Schweiz) als Beispiel eines zu repäsentierenden Wirklichkeitsauschnitts. Es wird vernachlässigt, dass ein Luftbild selbst bereits eine Repräsentation der Wahrnehmung des Fotografen ist. (Quelle: <a href="(https://commons.wikimedia.org/wiki/User:Presse03" > Presse03 2009</a>, <a href="(https://de.wikipedia.org/wiki/Datei:Sanspareil_Luftbild_West.jpg" > via WikiMedia</a>)
</figcaption></figure>




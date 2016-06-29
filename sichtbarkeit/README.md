# Sichtbarkeitsberechnung

Gibt's alles schon, z.b. https://wisp.heywhatsthat.com/ , deren Daten über 
die Erdoberfläche scheinen aber ungenau / grob xy-gerastert zu sein, bzw. ist 
nicht ganz klar, wie (im städtischen Raum) das "Bodenniveau" zu interpretieren 
ist.

Speziell für Wien gibt's sehr genaue Daten (50/50/10cm in x/y/z-Richtung) 
von der MA41 aus dem Jahre 2007. Danke an die Funkfeuer-Mailingliste für 
den Link, https://www.wien.gv.at/stadtentwicklung/stadtvermessung/geodaten/

**Lizenzhinweis:** "Die im Rahmen von Open Government Data Wien veröffentlichten 
Daten" (hier konkret sind die Geodaten betroffen) "stehen unter einer Creative 
Commons Namensnennung 3.0 Österreich Lizenz. Datenquelle: Stadt Wien -- data.wien.gv.at"

Überblick zur Lizenz: https://creativecommons.org/licenses/by/3.0/at/deed.de

Weitere Nutzungsbedingungnen: https://open.wien.gv.at/site/open-data/nutzungsbedingungen/


# Datenbeispiel

Hier ein Beispielbild für den Quadranten `55_1` ([Datenquelle](https://www.wien.gv.at/ma41datenviewer/downloads/ma41/geodaten/dom_tif/55_1_dom.zip); [OSM: Wien Liesing zwischen A23 Knoten Inzersdorf im Westen und der Laxenburger Straße im Osten](https://www.openstreetmap.org/search?query=wien%20liesing#map=15/48.1444/16.3497)), 
mittels `gdal_translate` aus GeoTIFF zu PNG gemacht, und dann für's Auge den Kontrast erhöht:

![Ziemlich genaue Höhendaten!](https://github.com/aaaaalbert/funkfeuer-sachen/blob/master/sichtbarkeit/55_1.png)

Beachte die Hochspannungsleitungen, Kräne, Straßenlaternen!

-----


Linksammlung:
* [Geodaten-Viewer](https://www.wien.gv.at/ma41datenviewer/public/start.aspx), 
* [Info über ALS (Airborne Laserscanning)](https://www.wien.gv.at/stadtentwicklung/stadtvermessung/geodaten/als/produkt.html)
* [GeoTIFF](https://trac.osgeo.org/geotiff/) ist das Dateiformat, das man vom Datenviewer herunterladen kann
* Die [GeoTIFF-Specs](http://www.remotesensing.org/geotiff/spec/geotiff1.html)
* [Wikipedia](https://en.wikipedia.org/wiki/World_file) und [ESRI](http://webhelp.esri.com/arcgisdesktop/9.3/index.cfm?pid=3034&topicname=World_files_for_raster_datasets)
über das "World file"-Format
* Von GeoTIFF nach TIFF konvertieren: https://gis.stackexchange.com/questions/61635/how-to-convert-geotiff-tiff

Algorithmisch hab ich bislang nur sehr vage Ideen (Polarkoordinaten-Transformation?), 
die ich für's Erste nicht weiter skizzieren werde.

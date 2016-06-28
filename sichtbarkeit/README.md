# Sichtbarkeitsberechnung

Gibt's alles schon, z.b. https://wisp.heywhatsthat.com/ , deren Daten über 
die Erdoberfläche scheinen aber ungenau / grob xy-gerastert zu sein, bzw. ist 
nicht ganz klar, wie (im städtischen Raum) das "Bodenniveau" zu interpretieren 
ist.

Speziell für Wien gibt's sehr genaue Daten (50/50/10cm in x/y/z-Richtung) 
von der MA41 aus dem Jahre 2007. Danke an die Funkfeuer-Mailingliste für 
den Link, https://www.wien.gv.at/stadtentwicklung/stadtvermessung/geodaten/

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

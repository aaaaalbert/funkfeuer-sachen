# Luftkühlung

Das [Nomogramm](https://github.com/aaaaalbert/funkfeuer-sachen/blob/master/luftkuehlung/nomogramm_luftkuehlung.pdf)
in diesem Verzeichnis drückt aus, mit welcher umgesetzten
Luftmenge bei welchem Temperaturgefälle welche Leistung abgeführt werden
kann, bzw. Umkehraufgaben davon.


### Grundlagen
Die relevante physikalische Größe ist die **spezifische Wärmekapazität**
*c* des vorhandenen Mediums. Sie gibt die Energie an, die man einem
Kilogramm eines Mediums zuführen muss, um es um ein Kelvin zu erwärmen:

 * spezifische Wärmekapazität = Energiemenge / (Masse mal Temperaturdifferenz)

[Wikipedia dazu](https://de.wikipedia.org/wiki/Spezifische_W%C3%A4rmekapazit%C3%A4t).

Für Luft ist das Volumen (in m^3) anschaulicher zu verwenden als die
Masse (in kg), die in der Einheit von *c* steckt.
[Auch hier Wikipedia](https://de.wikipedia.org/wiki/Luft#Physikalische_Gr%C3%B6%C3%9Fen_der_Luft):
Ein Kubikmeter Luft wiegt einen guten Kilo.


### Erweiterung (to-do)
Kältere Luft hat eine höhere Dichte und damit eine höhere spezifische
Wärmekapazität. Das Nomogramm sowie die Abschätzung weiter unten für
"Winterbetrieb" sind für niedrigere Lufttemperaturen insofern pessimistisch.
Sie erwarten einen höheren Luftfluss, als sich mit angepassten Werten für
*c* ergeben würden.

Größenordnungen: 20° kühlere Luft kann um 7% mehr Energie aufnehmen,
10° kühlere um 4%. Magst *Du* ein weiteres Nomogramm bauen? ;-)


### Sinnvolle Annahmen zur Verwendung
* Die zugeführte elektrische Leistung wird vollständig in Wärme umgewandelt.
* Das Temperaturgefälle ist (Maximale gewünschte Betriebstemperatur) minus
  (Temperatur der zugeführten Luft), z.B. 60°C-20°C = 40K.


### Housing
Für den Anwendungsfall im Community-Housing von @FunkFeuer:
* Mittlere elektrische Leistung zirka 8kW
* Temperaturen
  * Betrieb maximal 60°C
  * Außenluft Winter 10°C --> ΔT = 50K
  * Außenluft Sommer 35°C --> ΔT = 25K

Das ergibt einen Winter-Airflow von <600m^3/h oder rund 160l/s,
im Sommer ca. 1.000m^3/h oder rund 280l/s.

Das strömt durch einen angenommenen Lüftungsquerschnitt von 0,25m^2 mit
2,4 bis 4 km/h, grob geometrisch abgeschätzt ohne Klimatechnik-Formeln.


# Quelle
Das Nomogramm basiert auf einer Darstellung auf
[ventilator.de](https://www.ventilator.de/kuehlung-von-servern-computern-mittels-aussenluft), 28.02.2019.

Ich hab dessen Stimmigkeit mit der Formel für spezifische Wärmekapazität
grundsätzlich validiert, aber nicht alle Punkte und Geraden nachgerechnet.

Dieses Repo und damit auch die Beschreibung und zur Verfügung gestellte Bearbeitung
des Nomogramms ist
[unter CC0 lizensiert](https://creativecommons.org/publicdomain/zero/1.0/).
Viel Spaß!

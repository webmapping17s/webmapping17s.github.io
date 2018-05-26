# Adlerweg Beispiel - Etappeninformationen für GPX Tracks Höhenprofile mit Farben nach Steigung

### Aufgabe: *zusätzlich zu den Profilen alle Informationen zu den Etappen als HTML-Bausteine anzeigen*

Ausgehend vom [Adlerweg Beispiel mit Auswahlmenü](https:/webmapping.github.io/ex/gpx_adlerweg_menu.html) für alle Tracks sollen jetzt auch textliche Zusatzinformationen für die einzelnen Etappen auf der HTML-Seite angezeigt werden. Basis für diese Daten ist die CSV Datei [`TW_Adlerweg-Etappen.csv`](https://webmapping.github.io/ex/gpx/TW_Adlerweg-Etappen.csv) die in dieser Form jedoch nicht verwendbar ist. Direktes Laden von CSV-Daten ist in Leaflet nicht vorgesehen, weshalb die CSV Datei in eine Form gebracht werden muss, die wir direkt verwenden können. Folgende Schritte sind dazu notwendig:

1. `TW_Adlerweg-Etappen.csv` in LibreOffice mit Zeichensatz `Westeuropa (Windows-1252/WinLatin 1` öffnen
2. in Spalte 1 den Dateinamen des GPX Tracks eintragen (z.B. AdlerwegEtappe01.gpx). Er wird später als Key für unser zentrales Javascript Datenobjekt verwendet
3. kurze Spaltenüberschriften wählen. Diese werden später als Keys für die Javascript Objekte der einzelnen Records dienen - ein Vorschlag:

        gpx titel kurztext beschreibung von nach bergauf bergab maxhoehe grad laenge gehzeit einkehr orgid

4. den Inhalt dieser veränderten CSV Datei in ein Javascript-Objekt umwandeln
    * http://www.convertcsv.com/csv-to-json.htm ist das Tool der Wahl dazu

            Step 1: Select your input
                -> Option 3 - Paste content into text box below
                -> Tabelleninhalt dorthin kopieren
            Step 5: Generate output
                -> CSV To Keyed JSON
                -> Download Result
                -> im Editor öffnen

5. die Variablendeklaration `window.ETAPPENINFO={...}` hinzufügen, als [`TW_Adlerweg-Etappen.js`](https://webmapping.github.io/ex/gpx/TW_Adlerweg-Etappen.js) speichern und als `<script>` in der HTML-Seite einbauen

Damit können wir in der `loadTrack` Funktion, der wir den Namen der GPX-Datei in der Variablen `gpxFile` übergeben, direkt auf die Etappeninformationen im Objekt `window.ETAPPENINFO[gpxFile]` zugreifen. Der Rest ist einfach: HTML-Bausteine mit `id`-Attributen hinzufügen und über die key/value Paare des entsprechenden Records im JavaScript mit `innerHTML` befüllen - als Beispiel:

            <h1 id="titel"></h1>
            <p id="beschreibung"></p>
            <ul>
                <li>Gehzeit in Stunden: <span id="gehzeit"></span></li>
            </ul>

            <script>
                function loadTrack(gpxFile) {
                    // HTML-info setzen
                    document.getElementById("titel").innerHTML = window.ETAPPENINFO[gpxFile].titel;
                    document.getElementById("beschreibung").innerHTML = window.ETAPPENINFO[gpxFile].beschreibung;
                    document.getElementById("gehzeit").innerHTML = window.ETAPPENINFO[gpxFile].gehzeit;
                }
            </script>

### Das Ergebnis:

[https:/webmapping.github.io/ex/gpx_adlerweg_info.html](https:/webmapping.github.io/ex/gpx_adlerweg_info.html)

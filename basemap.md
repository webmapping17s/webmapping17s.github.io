# basemap.at mit leaflet-hash Plugin

### Aufgabe: basemap.at WMTS-Layer verwenden und Koordinaten bei Zoom/Pan in der Adresszeile des Browsers anzeigen

basemap.at ist die freie Verwaltungsgrundkarte Österreichs und wird von den einzelnen Länder GIS Stationen dezentral gepflegt. Das Ergebnis ist eine hervorragende Alternative zum OpenStreetMap WMTS-Service für das Staatsgebiet Österreichs. Zum Einbau des basemap.at WMTS-Service ist etwas Handarbeit nötig, der mit dem Erkunden des WMTSCapabilities.xml Files beginnt:

1. [http://www.basemap.at/wmts/1.0.0/WMTSCapabilities.xml](http://www.basemap.at/wmts/1.0.0/WMTSCapabilities.xml) ansteuern und `<Layer>` Elemente suchen

    Dort finden sich die nötigen Informationen zum Ableiten der URL für den Leaflet `L.tileLayer()` Aufruf

    * `<ows:Title>` beinhaltet den Titel des Layers
    * `<ows:Abstract>` eine Kurzbeschreibung
    * `<ows:Identifier>` ein Layerkürzel das wir als Key für unsere Layerobjekte verwenden können
    * `<ResourceURL>` ist das URL-Template in dem wir nur einige wenige Ersetzungen durchführen müssen um zur TileLayerURL zu kommen
        * `{Style}` entspricht dem `<ows:Identifier>`Element im `<Style>` Element
        * `{TileMatrixSet}` entspricht dem `<TileMatrixSet>` Element
        * `{TileMatrix}` wird das TileLayerURL `{z}`
        * `{TileRow}` wird das TileLayerURL `{y}`
        * `{TileCol}` wird das TileLayerURL `{x}`
        * die fünf Variationen der ResourceURL zeigen die verfügbaren Hosts `maps1, maps2, maps3, maps4, maps` und werden unser TileLayerURL `{s}`
        * damit kann für alle verfügbaren Layer eine passende TileLayerURL generiert werden - ein Beispiel:

                aus der ResourceURL
                https://maps1.wien.gv.at/basemap/geolandbasemap/{Style}/{TileMatrixSet}/{TileMatrix}/{TileRow}/{TileCol}.png

                wird die TileLayerURL
                https://{s}.wien.gv.at/basemap/geolandbasemap/normal/google3857/{z}/{y}/{x}.png

2. Das Javascriptobjekt mit allen verfügbaren Layern definieren. Die `<ows:Identifier>` des `<Layer>` Elements dienen dabei als key, die TileLayerURLs mit verfügbaren Hosts und Datenquelle als values. am Beispiel des Geoland Grundkarten Layers sieht dieses Objekt so aus:

        var layers = {
            geolandbasemap: L.tileLayer("https://{s}.wien.gv.at/basemap/geolandbasemap/normal/google3857/{z}/{y}/{x}.png", {
                subdomains: ['maps', 'maps1', 'maps2', 'maps3', 'maps4'],
                attribution: 'Datenquelle: <a href="http://www.basemap.at/">basemap.at</a>'
            })
        };

3. Das leaflet-hash Plugin zur Koordinateanzeige inkludieren

    * [https://github.com/mlevans/leaflet-hash](https://github.com/mlevans/leaflet-hash) ansteuern
    * `leaflet-hash.js` downloaden und local speichern
    * als `<script>` Element einbinden
    * am Ende des Javascripts mit der Kartenapplikation folgende Zeile hinzufügen

        var hash = new L.Hash(map);


### Das Ergebnis:

[https:/webmapping.github.io/ex/hash.html](https:/webmapping.github.io/ex/hash.html)

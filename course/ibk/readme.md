# Übersichtskarte Innsbruck in mehreren Varianten

Leaflet Docs: [http://leafletjs.com/reference-1.0.3.html](http://leafletjs.com/reference-1.0.3.html)

1.  Innsbruck mit OSM, Maßstabsleiste sowie einem Marker mit Tooltip, Popup und Webcam Bild Patscherkofel Richtung Innsbruck
    * [ibk_01.html](ibk_01.html)
    * [https://www.tirol.gv.at/umwelt/luft/messnetz-galerie-webcams/livebilder/](https://www.tirol.gv.at/umwelt/luft/messnetz-galerie-webcams/livebilder/)
    * L.map, L.tileLayer, L.marker, .bindTooltip, .bindPopup

2. Übersichtskarte Innsbruck wie oben nur mit basemap.at WMTS Service (Standard Layer)
    * [ibk_02.html](ibk_02.html)
    * [https://basemap.at/](https://basemap.at/)
    * [https://www.basemap.at/wmts/1.0.0/WMTSCapabilities.xml](https://www.basemap.at/wmts/1.0.0/WMTSCapabilities.xml)

            ResourceURL:
            https://maps1.wien.gv.at/basemap/geolandbasemap/{Style}/{TileMatrixSet}/{TileMatrix}/{TileRow}/{TileCol}.png

            übersetzte Leaflet Version der ResourceURL:
            https://{s}.wien.gv.at/basemap/geolandbasemap/normal/google3857/{z}/{y}/{x}.png

3. Übersichtskarte Innsbruck mit allen möglichen basemap.at Layern
    * [ibk_03.html](ibk_03.html)
    * L.control.layers(baselayers)

4. Übersichtskarte Innsbruck mit Overlay für Marker zum Ein-/Ausschalten
    * [ibk_04.html](ibk_04.html)
    * L.control.layers(baselayers, overlays)

5. mehrere Marker als Gruppe hinzufügen
    * [ibk_05.html](ibk_05.html)
    * L.FeatureGroup, .fitBounds

6. mehrere Marker über eine Linie verbinden
    * [ibk_06.html](ibk_06.html)
    * L.polyline

7. Video overlay anzeigen
    * [ibk_07.html](ibk_07.html)
    * L.videoOverlay


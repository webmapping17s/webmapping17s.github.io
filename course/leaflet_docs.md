# Leaflet Dokumentation verwenden

Beispiel: http://leafletjs.com/reference-1.0.3.html#map


## Woraus besteht jeder Leaflet Dokumentationseintrag

* Usage Example

        var map = L.map('map', {
            center: [51.505, -0.09],
            zoom: 13
        });

* Creation Sytnax mit verpflichtenden und optionalen Argumenten

        // id muss, options können angegeben werden (deshalb das Fragezeichen)
        L.map(<String> id, <Map options> options?)

* Options in verschiedensten Gruppen mit folgenden Spalten
    * Name der Option
    * Datentyp
    * Default Wert
    * Description

            // Options werden als "object literal" definiert
            var opts = {
                center: [51.505, -0.09],
                zoom: 13
            }
            var map = L.map('map', opts);

* Events in verschiedensten Gruppen

        // Verwendung im Skript
        map.on('click', function (evt) {
            console.log(evt);
            alert('Inspect this click-event in your console!');
        });

* Methoden in verschiedensten Gruppen mit Rückgabewerten

        // Verwendung im Skript
        var bounds = map.getBounds();
        console.log(bounds);

        // auch über Methoden definierte Objekte haben weitere nützliche Methoden
        console.log(bounds.getNorthWest());
        console.log(bounds.toBBoxString());
        console.log(
            'Die Entfernung (km) von Innsbruck zum Kartenmittelpunkt beträgt',
            map.distance(
                [47.267222,11.392778],
                map.getCenter()
            ) / 1000.0
        )

* Eigenschaften (Properties)

        // können gesetzt oder abgefragt werden
        map.scrollWheelZoom.enable();
        map.scrollWheelZoom.disable();
        console.log(map.scrollWheelZoom.enabled());

* .... und manchmal noch mehr


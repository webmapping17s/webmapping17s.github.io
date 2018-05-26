# Höhenprofil nach Steigung - Vorbereitung

### 1. GPX-Punkte anzeigen

    gpxTrack.eachLayer(function(layer) {
        // ...
    }

- zeige das Objekt mit den Koordinaten und Höhen der GPX-Punkte in der Konsole an


### 2. for-Schleife für Punktepaare
    var punkte = [
        [ 47.51982360, 12.43079420, 662.00000 ],
        [ 47.51982000, 12.43077990, 662.00000 ],
        [ 47.52005000, 12.43077990, 661.00000 ],
        [ 47.52009000, 12.43080990, 661.00000 ],
        [ 47.52010990, 12.43074000, 661.00000 ],
        [ 47.52025000, 12.43080000, 660.00000 ],
        [ 47.52075000, 12.43083000, 658.00000 ],
        [ 47.52074000, 12.43083000, 658.00000 ]
    ];

- schreibe eine for-Schleife für alle Punktepaare mit vorhergehendem und aktuellem Punkt
- zeige die Koordinaten und Höhen der Punktepaare in der Konsole an



### 3. Entfernung und Höhenunterschied berechnen

    var p1 = [ 47.51982360, 12.43079420, 662.00000 ];
    var p2 = [ 47.54730000, 12.33603000, 1565.0000 ];

- berechne Höhenunterschied und Entfernung zwischen den beiden Punkten
- zeige das Ergebnis in der Konsole an


### 4. Steigung berechnen

    var dist = 2500;
    var delta = 150;

- berechne die Steigung (Grad) die sich aus Entfernung und Höhenunterschied ergibt
- zeige das Ergebnis in der Konsole an


### 5. Farbpalette

    var rot = [];
    var gruen = [];

- definiere zwei Farbpaletten mit jeweils 5 Farbstufen (hexadezimal) für Rot bzw. Grün
- die Farben sollen jeweils von hell nach dunkel gehen
- zeige das Ergebnis in der Konsole an


### 6. Javascript switch-statement

    var farbe;
    var steigung;
    switch(true) {
        // ...
    }

- schreibe ein Javascript switch-statement das der Variablen `farbe` je nach Steigung den Wert *rot*, *grün* oder *gelb* zuweist
- rot bedeutet (steigung > 0), grün bedeutet (steigung < 0), gelb bedeutet (steigung === 0)
- siehe https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Statements/switch | https://www.w3schools.com/js/js_switch.asp


### 7. Linie zeichnen

    var p1 = [ 47.51982360, 12.43079420, 662.00000 ];
    var p2 = [ 47.54730000, 12.33603000, 1565.0000 ];

- zeichne eine Polylinie zwischen den beiden Punkten
- die Linie soll rot und 6 Pixel breit sein

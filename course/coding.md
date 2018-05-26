# Coding Tipps

## Fehler im Javascript Code finden

Die Suche nach Fehlern im Javascript Code kann sehr mühsam sein. Deshalb sollte der Code immer übersichtlich formatiert sein und regelmäßig auf Fehler kontrolliert werden. Im Netz finden sich dazu zwei Tools die wir euch ans Herz legen wollen:

1. Online JavaScript beautifier - [http://jsbeautifier.org/](http://jsbeautifier.org/)
    * hilft Einrückungen übersichtlich zu machen
    * geht auch für HTML und CSS
    * kontrolliert **nicht** auf Syntaxfehler

2. ESLint - [http://eslint.org/demo/](http://eslint.org/demo/)
    * zeigt Fehler im Javascript Code direkt an
    * ein Klick auf die roten Fehlerbalken oder Kreuzchen  springt zur entsprechenden Stelle im Code
    * die Links bei den Fehlerbalken geben Erklärungen zur Art des Fehlers
    * für unsere Leaflet Karten bekommen wir viele Fehler mit `'L' is not defined`. Das liegt daran, dass ESLint nichts von der globalen Leafletvariable `L` weiß. gleichzeitig müssen wir ESLint beibringen, das wir mit einem Browser arbeiten, sonst bekommen wir Fehler beim Verwenden von `window`, `document`, `alert`, etc. Mit zwei Kommentaren die ganz am Beginn jedes Skripts stehen müssen können wir diese vermeintlichen Fehlermeldungen unterdrücken:

            /* global L */
            /* eslint-env browser */

            // dieser Code ist jetzt Lint-free!
            window.onload = function () {
                alert(L)
            };

    * ESLint beschwert sich auch über `console.log()` was auch gut so ist, denn nach dem Entwickeln sollten alle Debug-Meldungen in der Konsole verschwinden ...
    * ESLint gibt es auch unter [https://sourceforge.net/projects/notepad-linter/](https://sourceforge.net/projects/notepad-linter/) als Plugin für Notepad++

## Fehler im HTML-Code finden

Viele Fehler im HTML-Code sieht man im Browser schon bei einem Blick in den Quelltext der Seite durch Rot gekennzeichnete Stellen. Im Firefox lässt sich der Quelltext mit Syntaxerkennung bequem über STRG+U anzeigen. Gleich wie bei Javascript hilft auch der [*Online JavaScript beautifier*](http://jsbeautifier.org/) um Einrückungen einheitlich zu gestalten. Die Gültigkeit des HTML-Codes kann schließlich auch Online über die Seite [https://validator.nu/](https://validator.nu/) überprüft werden. Die HTML-Spezifikation der diese Prüfung zugrunde liegt ist sehr umfangreich und wir haben bisher nur die oberste Spitze des Eisbergs kennengelernt. Deshalb ist es wahrscheinlich, dass euch Fehlermeldungen begegnen werden, die euch nicht weiterhelfen den Fehler zu bereinigen. In diesen Fällen meldet euch einfach bei uns und wir werden gemeinsam eine Lösung finden.

## Fehler im CSS-Code finden

Wie bei Javascript und HTML ist auch hier der [*Online JavaScript beautifier*](http://jsbeautifier.org/) das Mittel der Wahl um Einrückungen einheitlich zu gestalten. Die Validierung der CSS Regeln kann Online über die Seite [http://csslint.net/](http://csslint.net/) erfolgen (vielleicht hätten wir dieses Tool schon früher Verwenden sollen, dann wären Fehlermeldungen bei `padding: 0px` (*Values of 0 shouldn't have units specified*) oder `#map { width: 1024px }` (*Don't use IDs in selectors*) ausgeblieben ...). Zur Bereinigung der Fehler und Warnungen gilt ähnliches wie bei HTML: bei Unklarheiten einfach melden.

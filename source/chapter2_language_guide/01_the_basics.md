# Die Grundlagen

Swift ist eine neue Programmiersprache für die Entwicklung von iOS, OS X und watchOS Anwendungen. Dir werden aber viele Teile von Swift bekannt vorkommen, wenn du bereits Erfahrung in der Entwicklung mit C oder Objective-C hast.

Swift beinhaltet eigene Versionen aller fundamentaler Datentypen aus C und Objective-C. Dies beinhaltet u.a. ```Int``` für Ganzzahlen, ```Double``` und ```Float``` für Fliesskommazahlen, ```Bool``` für boolsche Werte und ```String``` für Textdaten. Swift beinhaltet zudem leistungsfähige Versionen der drei Kollektionen ```Array```, ```Set``` und ```Dictionary``` (siehe <a href="04_collection_types.html">Kollektionen</a>).

Genauso wie C verwendet Swift Variablen um Werte zu speichern und darauf zu verweisen. Swift macht zudem starken Gebrauch von nicht veränderbaren Variablen, Konstanten. Diese Konstanten sind viel mächtiger als die Konstanten in C. Konstanten werden überall in Swift verwendet um die Verwendung von unveränderbaren Werten einfacher und sicherer zu machen.

Neben den bekannten Typen führt Swift auch erweiterte Typen ein, welche in Objective-C nicht vorhanden sind. So zum Beispiel Tupel, mit welchen Wertpaare definiert und übergeben werden können. Tupel können verwendet werden, um mehrere Werte aus einer Funktion zurückzugeben.

Des weiteren beinhaltet Swift optionale Typen, mit welchen nicht vorhandene Werte beschrieben werden können. Optionale Typen definieren entweder, dass ein Wert vorhanden ist und den Wert _x_ beinhaltet, oder aber dass gar kein Wert vorhanden ist. Optionale Typen sind ähnlich wie ```nil``` für Zeiger in Objective-C. Optionale Typen können aber mit allen Typen verwendet werden, nicht nur Klassen. Optionale Typen sind sicherer und aussagekräftiger als ```nil```-Zeiger in Objective-C, sie sind deshalb Bestandteil vieler von Swifts mächtigsten Funktionen.

Swift ist eine _typsichere_ Sprache, das bedeutet die Sprache hilft dir dabei klar zu definieren, mit welchen Typen dein Code arbeiten kann. Die Typsicherheit verhindert, dass du fälschlicherweise ein ```Int``` an ein Stück Code übergibst, welches eigentlich ein ```String``` erwartet. Genauso wird verhindert, dass aus Versehen ein optionaler ```String``` an ein Stück Code übergeben wird, welches einen nicht-optionalen ```String``` erwartet. Die Typsicherheit hilft dir Fehler so früh wie möglich während der Entwicklung zu finden und zu korrigieren.


## Konstanten und Variablen

Konstanten und Variablen assoziieren einen Namen (z.B. ```maximaleAnzahlLoginVersuche```oder ```willkommensNachricht```) mit einem Wert eines bestimmten Typs (z.B. die Zahl ```10```oder den Text ```"Hallo"```). Der Wert einer Konstante kann nicht mehr verändert werden, nachdem er einmal gesetzt wurde. Einer Variablen hingegen kann zu einem späteren Zeitpunkt ein neuer Wert zugewiesen werden.


### Konstanten und Variablen deklarieren

Konstanten und Variablen müssen deklariert werden, bevor sie verwendet werden können. Du deklarierst Konstanten mit dem ```let``` Schlüsselwort und Variablen mit ```var``` Hier ein Beispiel, wie Konstanten und Variablen verwendet werden können, um die Anmeldeversuche eines Benutzers zu überwachen:

```Swift
let maximaleAnzahlLoginVersuche = 10
var aktuelleAnzahlVersuche = 0 
```

Dieser Code kann sagt folgendes aus:

"Deklariere eine neue Konstante namens ```maximaleAnzahlLoginVersuche``` und gib ihr den Wert ```10 ```. Anschliessend deklariere eine neue Variable namens ```aktuelleAnzahlVersuche``` und gib ihr den Initialwert ```0```."

In diesem Beispiel wurde die maximale Anzahl Loginversuche als Konstante definiert, weil sich dieser Maximalwert nie verändert. Die Zählvariable für die aktuelle Anzahl von Loginversuchen ist als Variable definiert, da deren Wert nach jedem fehlgeschlagenen Loginversuch um eins erhöht wird.

Du kannst mehrere Konstanten oder mehrere Variablen direkt in einer Zeile deklarieren, indem du sie durch Kommas trennst:

```Swift
var x = 0.0, y = 0.0, z = 0.0
```

>Hinweis: 
Wenn sich ein Wert nicht verändert, deklariere diesen immer als Konstante mit dem ```let```Schlüsselwort. Verwende Variablen nur für Werte, welche später verändert werden müssen.

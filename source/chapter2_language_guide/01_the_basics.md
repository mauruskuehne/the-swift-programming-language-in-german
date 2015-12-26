# Die Grundlagen

Swift ist eine neue Programmiersprache für die Entwicklung von iOS, OS X und watchOS Anwendungen. Dir werden aber viele Teile von Swift bekannt vorkommen, wenn du bereits Erfahrung in der Entwicklung mit C oder Objective-C hast.

Swift beinhaltet eigene Versionen aller fundamentaler Datentypen aus C und Objective-C. Dies beinhaltet u.a. _Int_ für Ganzzahlen, _Double_ und _Float_ für Fliesskommazahlen, _Bool_ für boolsche Werte und _String_ für Textdaten. Swift beinhaltet zudem leistungsfähige Versionen der drei Kollektionen _Array_, _Set_ und _Dictionary_ (siehe <a href="04_collection_types.html">Kollektionen</a>).

Genauso wie C verwendet Swift Variablen um Werte zu speichern und darauf zu verweisen. Swift macht zudem starken Gebrauch von nicht veränderbaren Variablen, Konstanten. Diese Konstanten sind viel mächtiger als die Konstanten in C. Konstanten werden überall in Swift verwendet um die Verwendung von unveränderbaren Werten einfacher und sicherer zu machen.

Neben den bekannten Typen führt Swift auch erweiterte Typen ein, welche in Objective-C nicht vorhanden sind. So zum Beispiel Tupel, mit welchen Wertpaare definiert und übergeben werden können. Tupel können verwendet werden, um mehrere Werte aus einer Funktion zurückzugeben.

Des weiteren beinhaltet Swift optionale Typen, mit welchen nicht vorhandene Werte beschrieben werden können. Optionale Typen definieren entweder, dass ein Wert vorhanden ist und den Wert *x* beinhaltet, oder aber dass gar kein Wert vorhanden ist. Optionale Typen sind ähnlich wie _nil_ für Zeiger in Objective-C. Optionale Typen können aber mit allen Typen verwendet werden, nicht nur Klassen. Optionale Typen sind sicherer und aussagekräftiger als _nil_-Zeiger in Objective-C, sie sind deshalb Bestandteil vieler von Swifts mächtigsten Funktionen.

Swift ist eine _typsichere_ Sprache, das bedeutet die Sprache hilft dir dabei klar zu definieren, mit welchen Typen dein Code arbeiten kann. Die Typsicherheit verhindert, dass du fälschlicherweise ein _Int_ an ein Stück Code übergibst, welches eigentlich ein _String_ erwartet. Genauso wird verhindert, dass aus Versehen ein optionaler _String_ an ein Stück Code übergeben wird, welches einen nicht-optionalen _String_ erwartet. Die Typsicherheit hilft dir Fehler so früh wie möglich während der Entwicklung zu finden und zu korrigieren.

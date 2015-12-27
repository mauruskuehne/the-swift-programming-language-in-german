# Die Grundlagen

Swift ist eine neue Programmiersprache für die Entwicklung von iOS, OS X und watchOS Anwendungen. Dir werden aber viele Teile von Swift bekannt vorkommen, wenn du bereits Erfahrung in der Entwicklung mit C oder Objective-C hast.

Swift beinhaltet eigene Versionen aller fundamentaler Datentypen aus C und Objective-C. Dies beinhaltet u.a. ```Int``` für Ganzzahlen, ```Double``` und ```Float``` für Fliesskommazahlen, ```Bool``` für boolsche Werte und ```String``` für Textdaten. Swift beinhaltet zudem leistungsfähige Versionen der drei Kollektionen ```Array```, ```Set``` und ```Dictionary``` (siehe <a href="TO BE DEFINED">Kollektionen</a>).

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

### Typhinweise

Du kannst bei der Deklaration einer Variable oder Konstanten einen Typhinweis angeben, um genau zu definieren, was für Werte in der Variable oder Konstanten erlaubt sein sollen. Typhinweise werden nach dem Variablen- oder Konstantennamen angegeben. Schreibe nach dem Namen der Konstante oder Variable ein Doppelpunkt un ein Leerzeichen und anschliessend den Namen des Typs.

Dieses Beispiel definiert einen Typhinweis für die Variable ```willkommensNachricht``` um anzugeben, dass darin nur ```String```-Werte gespeichert werden können:

```Swift
var willkommensNachricht: String
```

Der Doppelpunkt in dieser Deklaration bedeutet so viel wie "... ist vom Typ...", der Code kann also folgendermassen gelesen werden:

"Deklariere eine Variable namens ```willkommensNachricht``` vom Typ ```String```."

Mit "vom Typ ```String```" ist gemeint, dass irgend ein ```String```-Wert darin gespeichert werden kann. 

Der Variable ```willkommensNachricht``` kann nun irgend ein Textwert zugewiesen werden:

```Swift
willkommensNachricht = "Hallo"
```

Du kannst mehrere Variablen vom gleichen Typ auf einmal deklarieren. Schreibe die Variablen dafür kommagetrennt auf einer Zeile und den Typhinweis nach dem letzten Variablennamen:

```Swift
var rot, grün, blau: Double
```

>Hinweis:
In der Praxis verwendest du die Typhinweise nur selten. Wenn du einer Variable oder Konstante direkt bei der Deklaration einen Initialwert mitgibst, kann Swift in den meisten Fällen den Typ direkt ableiten (weitere Details findest du unter <a href="TO BE DEFINED">Typsicherheit und Typinferenz</a>. Im ```willkommensNachricht``` Beispiel oben wurde kein Initialwert angegeben, der Typ wurde deshalb per Typhinweis definiert und nicht aus einem Initialwert abgeleitet.

### Benennung von Konstanten und Variablen

Die Namen von Konstanten und Variablen können fast alle Zeichen beinhalten, inklusive Unicode-Zeichen:

```Swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "HundKuh"
```

Die Namen von Konstanten und Variablen dürfen keine Leerzeichen, mathematische Symbole, fehlerhafte Unicode Codepunkte, Private Use Area Unicode Codepunkte oder Rahmenzeichen verwenden. Zudem dürfen die Namen nicht mit einer Nummer beginnen. Nummern können aber innerhalb oder am Ende des Variablennamens verwendet werden.

Nachdem du einmal eine Konstante oder Variable mit einem bestimmten Typ deklariert hast, kannst du sie nicht erneut deklarieren. Das heisst, du kannst sie nicht verändern um einen anderen Typ darin zu speichern. Du kannst auch keine Variablen in Konstanten oder Konstanten in Variablen umwandeln.

>Hinweis: Wenn du eine Konstante oder Variable gleich nennen möchtest wie ein Swift-Schlüsselwort, musst du das Schlüsselwort mit einfachen Anführungszeichen (`) umschliessen. Dies solltest du aber wenn möglich vermeiden.

Du kannst den Wert einer existierenden Variable auf einen anderen kompatiblen Wert ändern. In diesem Beispiel wird der Wert von ```freundlichesWillkommen``` von ```Hallo!``` auf ```Bonjour!``` geändert:

```Swift
var freundlichesWillkommen = "Hallo!"
freundlichesWillkommen = "Bonjour!"
// freundlichesWillkommen hat neu den Wert "Bonjour!"
```

Im gegensatz zu Variablen kann der Wert von Konstanten nicht mehr verändert werden, nachdem ihr einmal ein Wert zugewiesen wurde. Wird trotzdem versucht der Wert einer Konstante zu verändern, führt dies zu einem Kompilierfehler:

```Swift
let sprachName = "Swift"
sprachName = "Swift++"
// Dies ergibt einen Kompilierfehler, sprachName darf nicht verändert werden
```


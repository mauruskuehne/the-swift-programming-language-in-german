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

Im Gegensatz zu Variablen kann der Wert von Konstanten nicht mehr verändert werden, nachdem ihr einmal ein Wert zugewiesen wurde. Wird trotzdem versucht der Wert einer Konstante zu verändern, führt dies zu einem Kompilierfehler:

```Swift
let sprachName = "Swift"
sprachName = "Swift++"
// Dies ergibt einen Kompilierfehler, sprachName darf nicht verändert werden
```

### Ausgabe von Konstanten und Variablen

Du kannst den aktuellen Wert von Konstanten oder Variablen mit der Funktion ```print(_:separator:terminator:)``` ausgeben:

```Swift
print(freundlichesWillkommen)
// gibt "Bonjour!" aus
```

Die Funktion ```print(_:separator:terminator:)``` ist eine globale Funktion welche einen oder mehrere Werte je nach Situation in die passende Ausgabe schreibt. In Xcode schreibt die ```print(_:separator:terminator:)``` Funktion beispielsweise in das Konsolen-Ausgabefenster. Die Parameter ```separator``` und ```terminator``` haben Standardwerte, du kannst sie also beim Aufruf der Funktion weglassen. Standardmässig beendet die Funktion die Ausgabe mit einem Zeilenumbruch. Um einen Wert ohne Zeilenumbruch auszugeben, kann als ```terminator```-Wert einfach ein leeres ```String```-Element übergeben werden (Beispiel: ```print(einWert, terminator: "")```). Weitere Informationen zu Standardwerten kannst du unter <a href="TO BE DEFINED">Standardwerte für Parameter</a> finden.

Swift verwendet _Stringinterpolation_ um die Namen von Konstanten und Variablen als Platzhalter in einem längeren ```String``` zu verwenden. Swift ersetzt diese Platzhalter mit dem aktuellen Wert der Variable oder Konstante. Umschliesse den Namen in runden Klammern und setze ein Backslash vor die öffnende Klammer:

```Swift
print("Der aktuelle Wert von freundlichesWillkommen ist \(freundlichesWillkommen)")
// Ausgabe: "Der aktuelle Wert von freundlichesWillkommen ist Bonjour!"
```

>Hinweis: Weitere Informationen zur Verwendung der Stringinterpolation findest du unter <a href="TO BE DEFINED">String Interpolation</a>.

### Kommentare

Mit Kommentaren kannst du Texte in den Code schreiben, welche nicht ausgeführt werden. So können zum Beispiel Notizen oder Erinnerungen direkt zum Code hinzugefügt werden. Kommentare werden beim kompilieren vom Swift-Compiler ignoriert.

Kommentare in Swift sind sehr ähnlich wie in C. Einzeilige Kommentare beginnen mit zwei Schrägstrichen (```//```):

```Swift
// Das ist ein Kommentar
```

Mehrzeilige Kommentare beginnen mit einem Schrägstrich und einem Sternchen (```/*```) und enden mit einem Sternchen und einem Schrägstrich (```*/```):

```Swift
/* Dies ist ebenfalls ein Kommentar,
der aber über mehrere Zeilen verteilt ist */
```

Im Gegensatz zu C können mehrzeilige Kommentare in Swift verschachtelt werden. Du kannst die Kommentare verschachteln, indem du einen mehrzeiligen Kommentar beginnst und dann einen zweiten mehrzeiligen Kommentar innerhalb des ersten Kommentares beginnst. Es wird dann zuerst der zweite Kommentar geschlossen, anschliessend der erste Kommentar:

```Swift
/* dies ist er Anfang des ersten mehrzeiligen Kommentars
/* dies ist der zweite mehrzeilige Kommentar */
dies ist das Ende des ersten mehrzeiligen Kommentars */
```

Verschachtelte mehrzeilige Kommentare ermöglichen es, grosse Codeabschnitte schnell und einfach auszukommentieren. Selbst dann, wenn der Code bereits mehrzeilige Kommentare beinhaltet.

### Semikolons

Im Gegensatz zu anderen Sprachen benötigt Swift kein Semikolon am Ende eines Befehls. Du kannst es aber hinzufügen, wenn du möchtest. Semikolons werden zwingend benötigt, wenn du mehrere, separate Befehle auf einer Zeile schreiben möchtest:

```Swift
let katze = "🐱"; print(katze)
// Gibt "🐱" aus
```

### Integer

Integer sind ganze Zahlen ohne Bruchanteil, also zum Beispiel ```42``` oder ```-23```. Integer sind entweder vorzeichenbehaftet (positiv, null oder negativ) oder vorzeichenlos (positiv oder null).

Swift bietet Integer mit oder ohne Vorzeichen in den Grössen 8, 16, 32 oder 64 Bit. Diese Integer haben ähnliche Namenskonventionen wie in C, ein vorzeichenloser 8-Bit Integer ist also vom Typ ```UInt8```, ein 32-Bit Integer mit Vorzeichen ist vom Typ ```Int32```. Wie alle Typen in Swift beginnen die Typnamen mit einem Grossbuchstaben.

#### Grenzwerte der Integer 

Du kannst auf die Grenzwerte eines Integer-Types über die Eigenschaften ```min``` und ```max``` zugreifen:

```Swift
let minWert = UInt8.min // minWert entspricht 0 und ist vom Typ UInt8
let maxWert = UInt8.max // maxWert entspricht 255 und ist vom Typ UInt8
```

Die Werte dieser Eigenschaften sind immer vom passenden numerischen Typ (also z.B. ```UInt8``` im Beispiel oben). Die Eigenschaften können deshalb in Ausdrücken direkt mit anderen Werten des gleichen Typs verwendet werden.

#### Int

In den meisten Fällen musst du keine spezifische Integergrösse auswählen. Swift bietet einen zusätzlichen Integer-Typ, ```Int```. ```Int``` hat immer die gleiche Grösse wie die native Busbreite der Plattform.

* Auf einer 32-Bit Plattform hat ```Int``` die gleiche Grösse wie ```Int32```
* Auf einer 64-Bit Plattform hat ```Int``` die gleiche Grösse wie ```Int64```

Sofern du keine spezifischen Integergrössen benötigst, solltest du immer ```Int``` für ganzzahlige Werte in deinem Code verwenden. Dies hilft dabei, den Code konsistent und kompatibel zu halten. Selbst auf 32-Bit Plattformen können mit ```Int``` alle Werte zwischen ```-2'147'483'648 ``` und ```2'147'483'647``` gespeichert werden. Dies sollte für die meisten Fälle reichen.

#### UInt

Zusätzlich bietet Swift mit ```UInt``` weiteren vorzeichenlosen Integer-Typ. Dieser ist ebenfalls immer gleich gross wie die native Busbreite der Plattform.


* Auf einer 32-Bit Plattform hat ```UInt``` die gleiche Grösse wie ```UInt32```
* Auf einer 64-Bit Plattform hat ```UInt``` die gleiche Grösse wie ```UInt64```

>Hinweis: 
Verwende ```UInt``` nur, wenn du wirklich einen vorzeichenlosen Integer-Typ von der Grösse der nativen Busbreite benötigst. Wenn dies nicht der Fall ist, solltest du ```Int``` verwenden. Dies auch wenn du weisst, dass du darin keine negativen Werte speichern wirst. Konsistente Verwendung von ```Int``` für ganzzahlige Werte macht deinen Code kompatibler, benötigt keine Konvertierungen zwischen den Integer-Typen und ermöglicht die häufigere Verwendung der Typinferenz (siehe <a href="TO BE DEFINED">Typsicherheit und Typinferenz</a>).

### Fliesskommazahlen

_Fliesskommazahlen_ sind Zahlen mit einem Bruchanteil, also zum Beispiel ```3.14159```, ```0.1``` oder ```-273.15```.

Fliesskommazahlen-Typen können einen viel grösseren Zahlenbereich abdecken als Integer-Typen. Zudem können sie Zahlen beinhalten die viel grösser oder kleiner sind als in einem ```Int```.  Swift bietet zwei Typen für vorzeichenbehaftete Fliesskommazahlen:

* ```Double``` repräsentiert eine 64-Bit Fliesskommazahl
* ```Float``` repräsentiert eine 32-Bit Fliesskommazahl

>Hinweis:
```Double``` hat eine Genauigkeit von mindestens 15 Dezimalstellen, die Genauigkeit von ```Float``` kann unter Umständen bei nur 6 Dezimalstellen liegen. Welchen Typ du verwenden sollst hängt von der Art und der Grösse der Werte ab mit denen du arbeitest. In Situationen wo beide Typen verwendet werden könnten, solltest du ```Double``` verwenden.

### Typsicherheit und Typinferenz

Swift ist eine _typsichere_ Programmiersprache. Eine typsichere Sprache unterstützt dich dabei, klar zu definieren, mit was für Typen dein Code arbeiten kann. Wenn ein Teil deines Codes einen ```String``` erwartet, kannst du ihm nicht aus Versehen einen ```Int``` übergeben.

Da Swift typsicher ist, werden beim kompilieren _typprüfungen_ durchgeführt und alle unpassenden Typen als Fehler markiert. Dies ermöglicht es dir schon früh im Entwicklungsprozess Fehler zu finden und zu korrigieren.

Typprüfungen helfen dir Fehler zu vermeiden, wenn du mit Werten verschiedener Typen arbeitest. Dies bedeutet aber nicht, dass du für alle deine Variablen und Konstanten einen Typ bei der Deklaration angeben musst. Wenn du keinen Typ angibst, ermittelt Swift mittels _Typinferenz_ den passenden Typ für die Variable oder Konstante. Typinferenz ermöglicht es dem Compiler den Typ eines Ausdruckes automatisch anhand der von dir angegebenen Werte zu ermitteln.

Dank der Typinferenz benötigt Swift viel weniger Typdeklarationen als andere Sprachen wie zum Beispiel C oder Objective-C. Konstanten und Variablen sind immer noch explizit typisiert, aber du musst den Typ nicht mehr selber angeben.

Die Typinferenz ist besonders hilfreich bei der Deklaration von Konstanten oder Variablen mit einem Initialwert. Dies wird oft durch die Zuweisung eines _Literalwertes_ (oder einfach nur _Literal_) zur Konstante oder Variable bei der Deklaration erreicht. (Ein Literalwert ist ein Wert der direkt in deinem Code steht, wie ```42``` und ```3.14159``` in den untenstehenden Beispielen).

Wenn du zum Beispiel ohne weitere Typangabe den Literalwert ```42``` einer neuen Konstante zuweist, leitet Swift daraus ab, dass die Konstante vom Typ ```Int``` soll. 

```Swift
let sinnDesLeben = 42
// Der abgeleitete Typ von sinnDesLeben ist Int
```

Genauso kannst du bei einem Fliesskommazahl-Literal den Typ weglassen. Swift leitet daraus automatisch ab, dass du ein ```Double``` deklarieren wolltest:

```Swift
let pi = 3.14159
// Der abgeleitete Typ von pi ist Double
```

Swift wählt bei Fliesskommazahlen immer ```Double``` (anstelle von ```Float```).

Wenn du nun ein Integer-Literal und ein Fliesskommazahl-Literal in einem Ausdruck kombinierst, wird daraus der Typ ```Double``` abgeleitet.

```Swift
let nochEinPi = 3 + 0.14159
// Der abgeleitete Typ von nochEinPi ist ebenfalls Double
```

Der Literalwert ```3``` an sich hat keinen expliziten Typ. Der passende Typ ```Double``` wird daraus abgeleitet, dass auch eine Fliesskommazahl in der Addition vorhanden ist.

### Numerische Literale

Ganzzahlige Literale können auf verschiedene Arten geschrieben werden:

* Als _dezimale_ Zahl ohne Präfix
* Als _binäre_ Zahl mit dem Präfix ```0b```
* Als _oktale_ Zahl mit dem Präfix ```0o```
* Als _hexadezimale_ Zahl mit dem Präfix ```0x```

Alle Literale in unterem Beispiel haben den dezimalen Wert ```17```:

```Swift
let dezimalZahl = 17
let binaereZahl = 0b10001      // 17 in binärer Schreibweise
let oktaleZahl = 0o21          // 17 in oktaler Schreibweise
let hexadezimaleZahl = 0x11    // 17 in hexadezimaler Schreibweise
```

Fliesskommazahlen können entweder dezimal (ohne Präfix) oder hexadezimal (mit dem Präfix ```0x```) geschrieben werden. Sie müssen immer auf beiden Seiten des Dezimalpunktes eine (hexadezimale) Zahl haben. Dezimale Fliesskommazahlen können optional auch einen _Exponent_ haben, der durch ein grosses oder kleines ```e``` angegeben wird. Hexadezimale Fliesskommazahlen haben immer einen Exponent, angegeben durch ein grosses oder kleines ```p```.

Für Dezimalzahlen mit einem Exponent ```exp``` wird die Basis mit 10<sup>exp</sup> multipliziert:

* ```1.25e2``` entspricht 1.25 x 10<sup>2</sup> oder ```125.0```
* ```1.25e-2``` entspricht 1.25 x 10<sup>-2</sup> oder ```0.0125```

Für Hexadezimalzahlen mit einem Exponent ```exp``` wird die Basis mit 2<sup>exp</sup> multipliziert:

* ```0xFp2``` entspricht 15 x 2<sup>2</sup> oder ```60```
* ```0xFp-2``` entspricht 15 x 2<sup>-2</sup> oder ```3.75```

Alle Fliesskommazahl-Literale in unterem Beispiel haben den Dezimalwert ```12.1875```:

```Swift
let dezimalDouble = 12.1875
let exponentDouble = 1.21875e1
let hexadezimalDouble = 0xC.3p0
```

Numerische Literale können zusätzlich formatiert werden, damit sie leichter lesbar sind. Sowohl Ganzahl- als auch Fliesskommazahl-Werte können mit voranstehenden Nullen aufgefüllt werden oder mit Unterstrichen gruppiert werden. Keine der beiden Formatierungsvarianten verändert den effektiven Wert des Literals:

```Swift
let voranstehendeNullenDouble = 000123.456
let eineMillion = 1_000_000
let bisschenMehrAlsEineMillion = 1_000_000.000_000_1
```

### Numerische Typkonvertierungen

Wenn möglich solltest du immer den Typ ```Int``` für all deine ganzzahligen Variablen und Konstanten verwenden, selbst wenn du weisst, dass darin nie negative Zahlen vorkommen werden. Wenn du den Standardtyp verwendest, sind die Variablen und Konstanten direkt kompatibel und sie entsprechen dem abgeleiteten Typ der Integer-Literalwerte.

Verwende die anderen Integer-Typen nur, wenn du sie wirklich benötigst. Mögliche Gründe dafür wären externe Quellen, Performanceoptimierungen, Speicherverbrauch oder andere Optimierungen. Wenn du in diesen Fällen die Typen mit expliziten Grössen verwendest, kannst du mögliche Überläufe einfacher erkennen und du hast implizit die Eigenschaft der Daten dokumentiert.

#### Konvertieren von Ganzzahlen

Der speicherbare Zahlenbereich in einer Konstante oder Variable ist bei jedem numerischen Typ unterschiedlich. Eine ```Int8``` Konstante oder Variable kann Zahlen zwischen ```-128``` und ```127``` enthalten, wohingegen eine ```UInt8``` Konstante oder Variable die Zahlen von ```0``` bis ```255``` speichern kann. Versuchst du einer Konstante oder Variable einen Wert ausserhalb des möglichen Zahlenbereichs zuzuweisen, führt dies zu einem Kompilierfehler:

```Swift
let kannNichtNegativSein: UInt8 = -1
// UInt8 kann keine negativen Zahlen speichern, die Zeile führt deshalb zu einem Kompilierfehler
let zuGross : Int8 = Int8.max + 1
// Int8 kann keine Zahlen speichern die grösser sind als sein Maximalwert, 
// dies führt ebenfalls zu einem Kompilierfehler
```

Da jeder numerische Typ unterschiedliche Zahlenbereiche speichern kann, musst du bei jeder Konversion zwischen zwei numerischen Typen explizit zustimmen. Dieses Vorgehen verhindert versteckte Konvertierungsfehler und hilft dir die gewünschte Konvertierung explizit im Code anzugeben.

Um von einem numerischen Typ in einen anderen Typ zu konvertieren, musst du eine neue Zahl des gewünschten Typs mit dem existierenden Wert initialisieren. Im Beispiel ist die Konstante ```zweitausend``` vom Typs ```UInt16``` und die Konstante ```eins``` vom Typ ```UInt8```. Sie können nicht direkt addiert werden, da sie nicht den gleichen Typ haben. Stattdessen wird im Beispiel ein neuer ```UInt16``` Wert mit dem Wert aus ```eins``` initialisiert durch den Aufruf von ```UInt16(eins)```. Dieser neue ```UInt16``` wird dann anstelle des Originals (```eins```) verwendet.

```Swift
let zweitausend: UInt16 = 2_000
let eins: UInt8 = 1
let zweitausendUndEins = zweitausend + UInt16(eins)
```

Da nun beide Seiten der Addition vom Typ ```UInt16``` sind, kann die Addition durchgeführt werden. Der abgeleitete Typ der Konstanten ```zweitausendUndEins``` ist ebenfalls ```UInt16```, da es sich dabei um die Summe von zwei ```UInt16``` Werten handelt.

```EinTyp(mitInitialWert)``` ist der übliche Weg um einen Swift-Typ zu initialisieren und einen Initialwert zu übergeben. Hinter den Kulissen hat ```UInt16``` eigentlich einen Initialisierer, der einen ```UInt8``` entgegen nimmt. Dieser wird verwendet um aus dem bestehenden ```UInt8``` einen neuen  ```UInt16``` zu erstellen. Es kann hier nicht jeder Typ übergeben werden, es muss ein Typ sein, für den ```UInt16``` einen Initialisierer bereitstellt. Wie bestehende Typen  (sowie eigene Typdefinitionen) um neue Initialisierer erweitert werden können ist unter <a href="TO BE DEFINED">Extensions</a> beschrieben.

# Die Grundlagen

Swift ist eine neue Programmiersprache für die Entwicklung von iOS, OS X und watchOS Anwendungen. Dir werden aber viele Teile von Swift bekannt vorkommen, wenn du bereits Erfahrung in der Entwicklung mit C oder Objective-C hast.

Swift beinhaltet eigene Versionen aller fundamentaler Datentypen aus C und Objective-C. Dies beinhaltet u.a. ```Int``` für Ganzzahlen, ```Double``` und ```Float``` für Fliesskommazahlen, ```Bool``` für boolsche Werte und ```String``` für Texte. Swift beinhaltet zudem leistungsfähige Versionen der [drei Kollektionen](TO BE DEFINED) ```Array```, ```Set``` und ```Dictionary```.

Genauso wie C verwendet Swift Variablen, um Werte zu speichern und darauf zu verweisen. Swift macht zudem starken Gebrauch von nicht veränderbaren Variablen, sogenannten Konstanten. Diese Konstanten sind viel mächtiger als die Konstanten in C. Konstanten werden überall in Swift verwendet, um die Verwendung von unveränderbaren Werten einfacher und sicherer zu machen.

Neben den bekannten Typen führt Swift auch erweiterte Typen ein, welche in Objective-C nicht vorhanden sind. So zum Beispiel Tupel, mit welchen Wertpaare definiert und übergeben werden können. Tupel können verwendet werden, um mehrere Werte aus einer Funktion zurückzugeben.

Des weiteren beinhaltet Swift optionale Typen, mit welchen nicht vorhandene Werte beschrieben werden können. Optionale Typen definieren entweder, dass ein Wert vorhanden ist und _x_ beinhaltet oder aber dass gar kein Wert vorhanden ist. Optionale Typen sind ähnlich wie ```nil``` für Zeiger in Objective-C. Optionale Typen können aber mit allen Typen verwendet werden, nicht nur Klassen. Optionale Typen sind sicherer und aussagekräftiger als ```nil```-Zeiger in Objective-C, sie sind deshalb Bestandteil vieler von Swifts mächtigsten Funktionen.

Swift ist eine _typsichere_ Sprache. Das bedeutet, die Sprache hilft dir dabei klar zu definieren, mit welchen Typen dein Code arbeiten kann. Die Typsicherheit verhindert, dass du fälschlicherweise ein ```Int``` an ein Stück Code übergibst, welches eigentlich ein ```String``` erwartet. Genauso wird verhindert, dass aus Versehen ein optionaler ```String``` an ein Stück Code übergeben wird, welches einen nicht-optionalen ```String``` erwartet. Die Typsicherheit hilft dir Fehler so früh wie möglich während der Entwicklung zu finden und zu korrigieren.

## Konstanten und Variablen (Constants and Variables)

Konstanten und Variablen assoziieren einen Namen (z.B. ```maximaleAnzahlLoginVersuche```oder ```willkommensnachricht```) mit einem Wert eines bestimmten Typs (z.B. die Zahl ```10``` oder den Text ```"Hallo"```). Der Wert einer Konstante kann nicht mehr verändert werden, nachdem er einmal gesetzt wurde. Einer Variablen hingegen kann zu einem späteren Zeitpunkt ein neuer Wert zugewiesen werden.

### Konstanten und Variablen deklarieren

Konstanten und Variablen müssen deklariert werden, bevor sie verwendet werden können. Du deklarierst Konstanten mit dem ```let``` Schlüsselwort und Variablen mit ```var```. Hier ein Beispiel, wie mit Konstanten und Variablen die Anmeldeversuche eines Benutzers überwacht werden können:

```Swift
let maximaleAnzahlLoginVersuche = 10
var aktuelleAnzahlVersuche = 0 
```

Dieser Code so gelesen werden:

"Deklariere eine neue Konstante namens ```maximaleAnzahlLoginVersuche``` und gib ihr den Wert ```10 ```. Anschliessend deklariere eine neue Variable namens ```aktuelleAnzahlVersuche``` und gib ihr den Initialwert ```0```."

In diesem Beispiel wurde die maximale Anzahl Loginversuche als Konstante definiert, weil sich dieser Maximalwert nie verändert. Die Zählvariable für die aktuelle Anzahl von Loginversuchen ist als Variable definiert, da deren Wert nach jedem fehlgeschlagenen Loginversuch um eins erhöht wird.

Du kannst mehrere Konstanten oder mehrere Variablen direkt in einer Zeile deklarieren, indem du sie durch Kommas trennst:

```Swift
var x = 0.0, y = 0.0, z = 0.0
```

> HINWEIS  
> Wenn sich ein Wert nicht verändert, deklariere diesen immer als Konstante mit dem ```let``` Schlüsselwort. Verwende Variablen nur für Werte, welche später verändert werden müssen.

### Typhinweise (Type Annotations)

Du kannst bei der Deklaration einer Variable oder Konstanten einen Typhinweis angeben, um genau zu definieren, was für Werte in der Variable oder Konstanten erlaubt sein sollen. Typhinweise werden nach dem Variablen- oder Konstantennamen angegeben. Schreibe nach dem Namen der Konstante oder Variable einen Doppelpunkt, ein Leerzeichen und anschliessend den Namen des Typs.

Dieses Beispiel definiert einen Typhinweis für die Variable ```willkommensnachricht```. Damit geben wir an, dass darin nur ```String```-Werte gespeichert werden können:

```Swift
var willkommensnachricht: String
```

Der Doppelpunkt in dieser Deklaration bedeutet so viel wie "... ist vom Typ...", der Code kann also folgendermassen gelesen werden:

"Deklariere eine Variable namens ```willkommensnachricht``` vom Typ ```String```."

Mit "vom Typ ```String```" ist gemeint, dass irgend ein ```String```-Wert darin gespeichert werden kann. 

Der Variable ```willkommensnachricht``` kann nun irgend ein Textwert zugewiesen werden:

```Swift
willkommensnachricht = "Hallo"
```

Du kannst mehrere Variablen vom gleichen Typ auf einmal deklarieren. Schreibe die Variablen dafür kommagetrennt auf einer Zeile und den Typhinweis nach dem letzten Variablennamen:

```Swift
var rot, grün, blau: Double
```

> HINWEIS  
> In der Praxis verwendest du die Typhinweise nur selten. Wenn du einer Variable oder Konstante direkt bei der Deklaration einen Initialwert mitgibst, kann Swift in den meisten Fällen den Typ direkt ableiten (weitere Details findest du unter <a href="TO BE DEFINED">Typsicherheit und Typinferenz</a>). Im ```willkommensnachricht``` Beispiel oben wurde kein Initialwert angegeben, der Typ wurde deshalb per Typhinweis definiert und nicht aus einem Initialwert abgeleitet.

### Benennung von Konstanten und Variablen

Die Namen von Konstanten und Variablen können fast alle Zeichen beinhalten, inklusive Unicode-Zeichen:

```Swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "HundKuh"
```

Die Namen von Konstanten und Variablen dürfen keine Leerzeichen, mathematische Symbole, fehlerhafte Unicode Codepunkte, Private Use Area Unicode Codepunkte oder Rahmenzeichen verwenden. Zudem dürfen die Namen nicht mit einer Nummer beginnen. Nummern können aber innerhalb oder am Ende des Variablennamens verwendet werden.

Nachdem du einmal eine Konstante oder Variable mit einem bestimmten Typ deklariert hast, kannst du sie nicht erneut deklarieren. Das heisst, du kannst sie nicht verändern um einen anderen Typ darin zu speichern. Du kannst auch keine Variablen in Konstanten oder Konstanten in Variablen umwandeln.

> HINWEIS  
> Wenn du eine Konstante oder Variable gleich nennen möchtest wie ein Swift-Schlüsselwort, musst du das Schlüsselwort mit einfachen Anführungszeichen (`) umschliessen. Dies solltest du aber wenn möglich vermeiden.

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

> HINWEIS  
> Weitere Informationen zur Verwendung der Stringinterpolation findest du unter <a href="TO BE DEFINED">String Interpolation</a>.

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

### Integer (Integers)

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

> HINWEIS  
> Verwende ```UInt``` nur, wenn du wirklich einen vorzeichenlosen Integer-Typ von der Grösse der nativen Busbreite benötigst. Wenn dies nicht der Fall ist, solltest du ```Int``` verwenden. Dies auch wenn du weisst, dass du darin keine negativen Werte speichern wirst. Konsistente Verwendung von ```Int``` für ganzzahlige Werte macht deinen Code kompatibler, benötigt keine Konvertierungen zwischen den Integer-Typen und ermöglicht die häufigere Verwendung der Typinferenz (siehe <a href="TO BE DEFINED">Typsicherheit und Typinferenz</a>).

### Fliesskommazahlen (Floating-Point Numbers)

_Fliesskommazahlen_ sind Zahlen mit einem Bruchanteil, also zum Beispiel ```3.14159```, ```0.1``` oder ```-273.15```.

Fliesskommazahlen-Typen können einen viel grösseren Zahlenbereich abdecken als Integer-Typen. Zudem können sie Zahlen beinhalten die viel grösser oder kleiner sind als in einem ```Int```.  Swift bietet zwei Typen für vorzeichenbehaftete Fliesskommazahlen:

* ```Double``` repräsentiert eine 64-Bit Fliesskommazahl
* ```Float``` repräsentiert eine 32-Bit Fliesskommazahl

> HINWEIS  
> ```Double``` hat eine Genauigkeit von mindestens 15 Dezimalstellen, die Genauigkeit von ```Float``` kann unter Umständen bei nur 6 Dezimalstellen liegen. Welchen Typ du verwenden sollst hängt von der Art und der Grösse der Werte ab mit denen du arbeitest. In Situationen wo beide Typen verwendet werden könnten, solltest du ```Double``` verwenden.

### Typsicherheit und Typinferenz (Type Safety and Type Inference)

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

### Numerische Typkonvertierung

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

```EinTyp(mitInitialWert)``` ist der übliche Weg um einen Swift-Typ zu initialisieren und einen Initialwert zu übergeben. Hinter den Kulissen hat ```UInt16``` eigentlich einen Initialisierer, der einen ```UInt8``` entgegen nimmt. Dieser wird verwendet um aus dem bestehenden ```UInt8``` einen neuen  ```UInt16``` zu erstellen. Es kann hier nicht irgend ein Typ übergeben werden. Es muss ein Typ sein, für den ```UInt16``` einen Initialisierer bereitstellt. Wie bestehende Typen  (sowie eigene Typdefinitionen) um neue Initialisierer erweitert werden können ist unter <a href="TO BE DEFINED">Extensions</a> beschrieben.

#### Konvertieren von Ganzzahlen und Fliesskommazahlen

Die Konvertierung von Ganzzahlen zu Fliesskommazahlen muss explizit angegeben werden:

```Swift
let drei = 3
let punktEinsVierEinsFuenfNeun = 0.14159
let pi = Double(drei) + punktEinsVierEinsFuenfNeun
// pi entspricht 3.14159 und hat den abgeleiteten Typ Double
```

In diesem Beispiel wurde die Konstante ```drei``` verwendet, um einen neuen Wert vom Typ ```Double``` zu erstellen. So sind beide Seiten der Addition vom gleichen Typ. Ohne diese Konvertierung kann die Addition nicht durchgeführt werden.

Auch die Konvertierung von Fliesskommazahlen zu Ganzzahlen muss explizit angegeben werden. Ganzzahltypen können mit ```Double``` oder ```Float``` Werten initialisiert werden:

```Swift
let integerPi = Int(pi)
// integerPi hat den Wert 3 und ist vom Typ Int
```

Bei dieser Art der Konvertierung in Ganzzahlen werden die Nachkommastellen der Fliesskommazahlen abgeschnitten. Das bedeutet, aus ```4.75``` wird ```4``` und aus ```-3.9``` wird ```-3```.

> HINWEIS  
> Die Kombinationsregeln für numerische Konstanten und Variablen unterscheiden sich von denen für numerische Literale. Das Literal ```3``` kann direkt mit dem Literal ```0.14159``` addiert werden, da die Literale keinen expliziten Typ haben. Ihr Typ wird erst bei der Evaluation durch den Compiler festgelegt.

## Typalias (Type Aliases)

Ein _Typalias_ definiert einen anderen Namen für einen bereits existierenden Typ. Du kannst einen Typalias mit dem Schlüsselwort ```typealias``` definieren.

ein Typalias ist dann nützlich, wenn du auf einen bestehenden Typ mit einem anderen, kontextuell passenderen Namen zugreifen möchtest. Zum Beispiel wenn du mit Daten einer bestimmten Grösse aus einer externen Quelle arbeitest:

```Swift
typealias AudioSample = UInt16
```

Nachdem du den Typalias definiert hast, kannst du ihn überall dort verwenden, wo du auch den originalen Typen verwenden kannst:

```Swift
var maxGefundeneAmplitude = AudioSample.min
// maxGefundeneAmplitude hat nun den Wert 0
```

In diesem Beispiel ist ```AudioSample``` als Alias für ```UInt16``` definiert. Da es nur ein Alias ist, ist der Aufruf von ```AudioSample.min``` eigentlich ein Aufruf von ```UInt16.min```, welche dann den Initialwert ```0``` für die Variable ```maxGefundeneAmplitude``` zurückgibt. 

## Boolsche Werte (Booleans)

Swift hat einen einfachen boolschen Typ, namens ```Bool```. Boolsche Werte werden auch logische Werte genannt, da sie immer entweder wahr oder falsch sind. Swift bietet dafür zwei boolsche Werte an, ```true``` und ```false```:

```Swift
let orangenSindOrange = true
let ruebenSindLecker = false
```

Der abgeleitete Typ von ```orangenSindOrange``` und ```ruebenSindLecker``` ist ```Bool```, da sie mit boolschen Literalwerten initialisiert wurden. Genau so wie bei ```Int``` und ```Double``` weiter oben, musst du Variablen oder Konstanten nicht explizit als ```Bool``` markieren, wenn du sie direkt beim erstellen auf ```true``` oder ```false``` setzt. Typinferenz hilft dabei, die Initialisierung von Konstanten und Variablen in deinem Code kompakter und lesbarer zu machen, wenn du sie direkt mit einem Wert initialisierst.

Boolsche Werte sind besonders nützlich wenn du mit bedingten Anweisungen arbeitest, zum Beispiel der ```if``` Anweisung:

```Swift

if ruebenSindLecker {
  print("Mmm, köstliche Rüben!")
} else {
  print("Ieeh, Rüben sind schrecklich.")
}
// Gibt "Ieeh, Rüben sind schrecklich." aus
```

Bedingte Anweisungen wie die ```if``` Anweisung werden unter [Kontrollfluss](TO BE DEFINED) detaillierter behandelt. Swifts typsicherheit verhindert, dass nicht-boolsche Werte anstelle eines ```Bool```s verwendet werden. Das folgende Beispiel führt zu einem Kompilierfehler:

```Swift
let i = 1
if i {
  // Dieses Beispiel kompiliert nicht und ergibt einen Fehler
}
```

Folgende Alternative ist hingegen gültig:

```Swift
let i = 1
if i == 1 {
  // Dieses Beispiel kann erfolgreich kompiliert werden
}
```

Das Resultat des Vergleichs ```i == 1``` ist vom Typ ```Bool```, deshalb entstehen keine Probleme bei der Überprüfung der Typen. Vergleiche wie ```i == 1``` werden unter [Basisoperationen](TO BE DEFINED) erläutert.

Genauso wie in den anderen Beispielen zu Swifts Typsicherheit, verhindert dieses Verhalten ungewollte Fehler. Sie sorgt zudem dafür, dass die Absicht hinter einem Codeabschnitt immer klar ersichtlich ist.

## Tupel (Tuples)

Ein Tupel gruppiert mehrere Werte in einen einzelnen zusammengesetzten Wert. Die Werte eines Tupels können von einem beliebigen Typ sein. Die Werte innerhalb eines Tupels müssen nicht alle den gleichen Typ haben.

In nachfolgendem Beispiel ist ```(404, "Not Found")``` ein Tupel, welcher einen _HTTP Statuscode_ beschreibt. ein HTTP Statuscode ist ein spezieller Wert, welcher vom Webserver zurückgegeben wird, wenn du eine Webseite anforderst. Der Statuscode ```404 Not Found``` wird zurückgegeben, wenn die Webseite nicht existiert.

```Swift
let http404Fehler = (404, "Not Found")
// http404Fehler ist vom Typ (Int, String) und entspricht (404, "Not Found")
```

Der Tupel ```(404, "Not Found")``` gruppiert einen ```Int``` und einen ```String```. Der HTTP-Statuscode hat so zwei separate Werte, eine Nummer und einen von menschen lesbarer Text. Der Tupel kann beschrieben werden als "ein Tupel vom Typ ```(Int, String)```".

Du kannst Tupel aus allen möglichen Typkonstellationen erstellen und sie können so viele unterschiedliche Typen beinhalten wie du möchtest. Es hindert dich nichts daran, einen Tupel vom Typ ```(Int, Int, Int)```, ```(String, Bool)``` oder irgend einer anderen Kombination zu erstellen.

Du kannst Tupel wieder in separate Variablen oder Konstanten zerlegen, welche du dann wie gewohnt verwenden kannst:

```Swift
let (statusCode, statusNachricht) = http404Fehler
print("Der Statuscode ist \(statusCode)")
// Gibt "Der Statuscode ist 404" aus
print("Die Statusnachricht lautet \(statusNachricht)")
// Gibt "Die Statusnachricht lautet Not Found" aus
```

Wenn du nur Teile eines Tupels benötigst, kannst du einzelne Werte mit einem Unterstrich (_) beim zerlegen ignorieren:

```Swift
let (nurDenStatusCode, _) = http404Fehler
print("Der Statuscode ist \(nurDenStatusCode)")
// gibt "Der Satuscode ist 404" aus
```

Alternativ kannst du auf die einzelnen Elemente eines Tupels auch direkt via Indexzahlen (von 0 beginnend) zugreifen:

```Swift
print("Der Statuscode ist \(http404Fehler.0)")
// Gibt "Der Statuscode ist 404" aus
print("Die Statusnachricht lautet \(http404Fehler.1)")
// Gibt "Die Statusnachricht lautet Not Found" aus
```

Bei der Definition eines Tupels kannst du den einzelnen Elementen auch einen Namen vergeben:

```Swift
let http200Status = (statusCode: 200, nachricht: "OK")
```

Wenn du die Elemente eines Tupels benennst, kannst du mit den Elementnamen direkt auf die Werte der Elemente zugreifen:

```Swift
print("Der Statuscode ist \(http200Status.statusCode)")
// Gibt "Der Statuscode ist 200" aus
print("Die Statusnachricht lautet \(http404Fehler.nachricht)")
// Gibt "Die Statusnachricht lautet OK" aus
```

Tupel sind besonders nützlich als Rückgabewert von Funktionen. Eine Funktion, die versucht eine Webseite zu laden, könnte einen ```(Int, String)``` Tupel zurückgeben, um den Erfolg oder Fehler beim Laden der Seite zu beschreiben. Durch die Rückgabe von zwei separaten Werten (mit je einem eigenen Typ), kann die Funktion mehr Informationen über das Ergebnis zurückgeben, als nur mit einem einzelnen Wert. Weitere Informationen dazu findest du im Abschnitt [Funktionen mit mehreren Rückgabewerten](TO BE DEFINED)

> HINWEIS  
Tupel sind nützlich für eine temporäre Gruppierung von zusammengehörenden Werten. Sie sind nicht dafür gemacht, komplexe Datenstrukturen aufzubauen. Wenn du die Datenstruktur über längere Zeit benötigst, solltest du sie stattdessen als Klasse oder als Struktur modellieren. Weitere Informationen dazu findest du im Abschnitt [Klassen und Strukturen](TO BE DEFINED).

## Optionale Typen (Optionals)

Du kannst _optionale Typen_ in Situationen verwenden, wo ein Wert unter Umständen nicht vorhanden ist. Ein optionaler Typ sagt aus:

* Es _gibt_ einen Wert und er entspricht _x_

_oder_

* Es gibt _keinen_ Wert

> HINWEIS  
> Das Konzept von optionalen Typen gibt es in C oder Objective-C nicht. Man kann sie am ehesten mit der Objective-C Funktion vergleichen, dass Methoden ```nil``` anstelle eines Objektes zurückgeben können. ```nil``` bedeutet in diesem Fall "es ist kein gültiges Objekt vorhanden". Dies funktioniert aber nur für Objekte, nicht für Strukturen, primitiven Datentypen oder Enumerationswerten. Für diese Typen müssen Objective-C Methoden einen Spezialwert definieren und zurückgeben (zum Beispiel ```NSNotFound```) um das Fehlen eines Wertes anzudeuten. Dieser Ansatz setzt voraus, dass der Aufrufer der Methode weiss, dass es spezielle Werte gibt, die er überprüfen muss. Swifts optionale Typen ermöglichen es dir die Absenz eines Wertes für _alle Typen_ zu definieren. Du musst keine speziellen Konstanten definieren.

Hier ist ein Beispiel wie mit Hilfe von optionalen Typen die Absenz eines Wertes behandelt werden kann. Swifts ```Int``` hat einen Initialisierer, welcher versucht ein ```String```-Wert in einen ```Int```-Wert zu konvertieren. Es kann aber nicht jeder Text in eine Ganzzahl konvertiert werden. Der Text ```"123"``` kann in den numerischen Wert ```123``` konvertiert werden, aber der Text ```"Hallo, Welt"``` hat keinen offensichtlichen numerischen Wert.

Das Beispiel unten verwenden diesen Initialisierer um Konvertierung eines ```String``` in einen  ```Int``` zu probieren:

```Swift
let vielleichtEineZahl = "123"
let konvertierteZahl = Int(vielleichtEineZahl)
// konvertierteZahl hat den abgeleiteten Typ "Int?", oder "optionaler Int"
```

Da der Initialisierer fehlschlagen könnte, gibt er einen _optionalen_ ```Int``` zurück anstatt eines normalen ```Int```. Ein optionaler ```Int``` wird als ```Int?``` bezeichnet, nicht als ```Int```. Das Fragezeichen gibt an, dass der enthaltene Wert optional ist. Das entweder, dass _irgendein_ ```Int```-Wert enthalten ist oder _gar kein Wert_. (Es kann nichts anderes beinhalten. Es ist also sicher kein ```Bool``` oder ```String``` wert darin enthalten. Es enthält entweder einen ```Int```-Wert oder gar nichts).

### nil

Du kannst optionalen Variablen einen wertlosen Zustand versetzen, indem du ihr den Spezialwert ```nil``` zuweist:

```Swift
var serverResponseCode: Int? = 404
// serverResponseCode beinhaltet den richtigen Int Wert 404
serverResponseCode = nil
// serverResponseCode beinhaltet jetzt keinen Wert mehr
```

> HINWEIS  
> ```nil``` kann nicht mit nicht-optionalen Konstanten oder Variablen verwendet werden. Wenn eine Konstante oder Variable in deinem Code mit der Absenz eines Wertes umgehen muss, solltest du sie immer als optionalen Wert des entsprechenden Typs deklarieren.

Optionale Variablen werden automatisch mit ```nil``` initialisiert, wenn du ihnen bei der Deklaration keinen Initialwert übergibst.

```Swift
var umfrageAntwort: String?
// umfrageAntwort wurde automatisch auf nil gesetzt
```

> HINWEIS  
> Swifts ```nil``` ist nicht das gleiche ```nil``` wie in Objective-C. In Objective-C ist ```nil``` ein Zeiger auf ein nicht existierendes Objekt. In Swift ist ```nil``` kein Zeiger, es ist die Absenz eines Wertes eines bestimmten Typs. Optionale Werte irgend eines Typs können auf ```nil``` gesetzt werden, nicht nur Objekttypen.

### If-Anweisung und erzwungenes Auspacken (If Statements and Forced Unwrapping)

Du kannst eine ```if``` Anweisung verwenden um herauszufinden, ob ein optionaler Typ einen Wert beinhaltet. Dies machst du, indem du den optionalen Wert gegen ```nil``` prüfst. Du kannst diese Prüfung mit dem "gleich" Operator (```==```) oder dem "nicht gleich" Operator (```!=```) durchführen.

Wenn ein optionaler Typ einen Wert beinhaltet, gilt dieser als "nicht gleich wie" ```nil```:

```Swift
if konvertierteZahl != nil {
    print("konvertierteZahl beinhaltet einen ganzzahligen Wert.")
}
// Gibt "konvertierteZahl beinhaltet einen ganzzahligen Wert." aus
```

Sobald du dir sicher bist, dass der optionale Typ einen Wert beinhaltet, kannst du den darin enthaltenen Wert durch hinzufügen eines Ausrufezeichens (```!```) am Ende des Namens abrufen. Das Ausrufezeichen bedeutet so viel wie "Ich weiss, dass der optionale Typ einen Wert beinhaltet, bitte verwende ihn". Dies wird _erzwungenes Auspacken_ des optionalen Wertes genannt:

```Swift
if konvertierteZahl != nil {
    print("konvertierteZahl hat einen ganzzahligen Wert von \(konvertierteZahl!).")
}
// Gibt "konvertierteZahl beinhaltet einen ganzzahligen Wert von 123." aus
```

Für mehr Infos zur ```if```-Anweisung, siehe [Kontrollfluss](TO BE DEFINED).

> HINWEIS  
> Wenn ```!``` auf einen optionalen Typ ohne Inhalt angewendet wird, führt dies zu einem Laufzeitfehler. Stelle immer sicher, dass ein Wert vorhanden ist, bevor du versuchst darauf zuzugreifen.

### Binden von optionalen Werten (Optional Binding)

Du kannst _optionale Werte binden_ um herauszufinden, ob darin ein Wert enthalten ist. Wenn ja, wird der Wert direkt als temporäre Konstante oder Variable zur Verfügung gestellt. Die Bindung von optionalen Werten kann mit ```if``` und ```while``` Anweisungen verwendet werden. Der Inhalt eines optionalen Wertes wird geprüft und sofern vorhanden direkt in eine Konstante oder Variable zu extrahiert. Dies geschieht alles als eine einzelne Aktion. ```if``` und ```while``` Anweisungen sind unter [Kontrollfluss](TO BE DEFINED) im Detail beschrieben.

Schreibe die ```if```-Anweisung folgendermassen, um damit einen optionalen Wert zu binden:

```Swift
if let konstantenName = optionalerWert {
    // weitere Anweisungen
}
```

Wir können unser ```vielleichtEineZahl``` Beispiel aus [Optionale Typen](TO BE DEFINED) umschreiben, damit es neu den optionalen Wert bindet, anstatt ihn zwingend auszupacken.

```Swift
if let effektiveZahl = Int(vielleichtEineZahl) {
    print("\'\(vielleichtEineZahl) hat einen Integer-Wert von \(effektiveZahl)")
} else {
    print("\'\(vielleichtEineZahl)\' konnte nicht in einen Integer konvertiert werden.")
```

Dieser Code kann folgendermassen gelesen werden:

"Wenn der von ```Int(vielleichtEineZahl)``` zurückgegebene optionale ```Int``` einen Wert beinhaltet, setze eine neue Konstante ```effektiveZahl``` auf diesen Wert."

Wenn die Konvertierung erfolgreich war, steht die ```effektiveZahl``` Variable im ersten Abschnitt der ```if```-Anweisung zur Verfügung. Sie wurde bereits mit dem Wert aus dem optionalen Typ initialisiert. Es ist also kein ```!```-Suffix nötig um auf den Wert zuzugreifen. In diesem Beispiel wird ```effektiveZahl``` einfach dafür verwendet, um das Resultat der Konvertierung anzuzeigen.

Das Binden von optionalen Werten funktioniert sowohl mit Konstanten, als auch mit Variablen. Wenn du den Wert von ```effektiveZahl``` im ersten Abschnitt der ```if```-Anweisung verändern möchtest, musst du stattdessen ```if var effektiveZahl``` schreiben. Der Wert innerhalb des optionalen Wertes steht dir nun als Variable anstatt einer Konstante zur Verfügung.

In einer ```if```-Anweisung kannst du mehrere optionale Werte auf einmal binden und mit einer ```where```-Klausel auch noch einen boolschen Ausdruck überprüfen:

```Swift
if let ersteZahl = Int("4"), zweiteZahl = Int("42") where ersteZahl < zweiteZahl {
    print("\(ersteZahl) < \(zweiteZahl)")
}
// Gibt "4 < 42" aus
```

### Implizit ausgepackte optionale Typen (Implicitly Unwrapped Optionals)

Wie oben beschrieben erlauben es optionale Typen, dass eine Konstante oder Variable "kein Wert" haben darf. 
```if```-Anweisngen können optionale Typen überprüfen, ob ein Wert existiert und wenn nötig diesen auch direkt binden, damit auf den Wert zugegriffen werden kann.

Manchmal ist es vom Programmverlauf her klar, dass eine optionale Variable oder Konstante _immer_ einen Wert haben wird, nachdem sie einmal gesetzt wurde. In diesen Fällen ist es nützlich, wenn der optionale Wert nicht immer wieder geprüft und ausgepackt werden muss, wenn darauf zugegriffen wird. In diesen Fällen können wir davon ausgehen, dass wir immer einen Wert haben.

Diese Art von optionalen Typen werden _implizit ausgepackte optionale Typen_ genannt. Du schreibst so ein Typ, indem du ein Ausrufezeichen (```String!```) anstelle eines Fragezeichen (```String?```) nach den Typ setzt, den du optional machen möchtest.

Implizit ausgepackte optionale Typen sind nützlich, wenn wir wissen, dass ihnen kurz nach ihrer Definition ein Wert zugewiesen wird und sie definitiv für den Rest ihrer Lebenszeit einen Wert haben. Der Hauptanwendungsfall der implizit ausgepackten optionalen Typen in Swift ist bei der Initialisierung von Klassen. Siehe dazu auch [Nicht-besitzende Referenzen und implizit ausgepackte optionale Eigenschaften](TO BE DEFINED)

Hinter den Kulissen handelt es sich bei implizit entpackten optionalen Typen um ganz normale optionale Typen. Einzig mit dem Unterschied, dass sie auch als nicht-optionale Typen verwendet werden können, ohne dass ihr Wert jedes Mal neu ausgepackt werden muss. Das folgende Beispiel zeigt den Unterschied zwischen einem optionalen ```String``` und einem implizit ausgepackten optionalen ```String```, wenn auf den darunterliegenden Wert zugegriffen werden möchte:

```Swift
let eventuellEinString: String? = "Ein optionaler String."
let erzwungenerString: String = eventuellEinString! // benötigt ein Ausrufezeichen

let wahrscheinlichEinString: String! = "Ein implizit ausgepackter optionaler String."
let impliziterString: String = wahrscheinlichEinString // Ausrufezeichen nicht nötig
```

Du kannst dir implizit ausgepackte optionale Werte so vorstellen, als ob du die Erlaubnis gibst, den optionalen Wert automatisch "auszupacken", wann immer er benötigt wird. Anstelle ein Ausrufezeichen bei jeder Verwendung nach den Namen zu setzen, kannst du es bei der Deklaration direkt beim Typ angeben.

> HINWEIS  
> Wenn ein implizit ausgepackter optionaler Wert beim Versuch sie auszulesen ```nil``` ist, löst du damit einen Laufzeitfehler aus. Das Resultat ist genau das gleiche, wie wenn du das Ausrufezeichen hinter einen normalen optionalen Wert setzt, der ```nil``` beinhaltet.

Du kannst implizit ausgepackte optionale Werte genauso wie normale optionale Werte überprüfen, ob sie einen Wert beinhalten:

```Swift
if wahrscheinlichEinString != nil {
    print(wahrscheinlichEinString)
}
// gibt "Ein implizit ausgepackter optionaler String" aus
```

Du kannst implizit ausgepackte optionale Werte ebenfalls binden, um sie zu überprüfen und den Wert in einer Anweisung auszulesen:

```Swift
if let definitivEinString = wahrscheinlichEinString {
    print(definitivEinString)
}
// Gibt "Ein implizit ausgepackter optionaler String" aus
```

> HINWEIS  
> Verwende keinen implizit ausgepackten optionalen Typ, wenn die Variable zu einem späteren Zeitpunkt ```nil``` beinhalten könnte. Verwende immer einen normalen optionalen Typ für Variablen, wenn du sie während ihrer Lebenszeit auf ```nil``` überprüfen musst.

## Fehlerbehandlung

Mittels Fehlerbehandlung kannst du auf Fehler reagieren, die in deinem Programm während der Ausführung auftreten können.

Optionale Werte können dir mit dem vorhandensein, bzw. dem nicht-vorhandensein eines Wertes mitteilen, ob eine Funktion erfolgreich war oder nicht. Via Fehlerbehandlung kannst du den Grund für den Fehler ermitteln und wenn nötig an einen anderen Teil deines Programmes weitergeben.

Wenn in einer Funktion ein Fehler auftritt, _wirft_ sie einen Fehler. Der Aufrufer der Funktion kann den Fehler _fangen_ und entsprechend darauf reagieren.

```Swift
func kannEinenFehlerWerfen() throws {
    // Diese Funktion kann einen Fehler werfen, muss aber nicht
}
```

Eine Funktion gibt via ```throws```-Schlüsselwort in der Deklaration an, dass sie einen Fehler werfen kann. Wenn du eine Funktion aufrufst, die einen Fehler werfen kann, fügst du das ```try```-Schlüsselwort vor den Ausdruck hinzu.

Swift gibt Fehler automatisch aus dem aktuellen Definitionsbereich weiter, bis er von einer ```catch```-Anweisung behandelt wird.

```Swift
do {
    try kannEinenFehlerWerfen()
    // Es wurde kein Fehler geworfen
} catch {
    // Es wurde ein Fehler geworfen
}
```

Die ```do```-Anweisung erstellt einen neuen Definitionsbereich, welcher es ermöglicht den Fehler an eine oder mehrere ```catch```-Anweisungen zu übergeben.

Hier ist ein Beispiel, wie mittels der Fehlerbehandlung auf verschiedene Fehlerbedingungen reagiert werden kann:

```Swift
func machEinSandwich() throws {
    // ...
}

do {
    try machEinSandwich()
    issEinSandwich()
} catch Error.KeinSauberesGeschirrVorhanden {
    geschirrWaschen()
} catch Error.ZutatenFehlen(let zutaten) {
    lebensmittelEinkaufen(zutaten)
}
```

Die Funktion ```machEinSandwich()``` in diesem Beispiel wirft einen Fehler, wenn kein sauberes Geschirr vorhanden ist oder Zutaten fehlen. Da ```machEinSandwich()``` einen Fehler werfen kann, ist der Funktion das ```try```-Schlüsselwort vorangestellt. Durch Umschliessen des Funktionsaufrufes mit einer ```do```-Anweisung, können alle geworfenen Fehler an die vorhandenen ```catch```-Anweisungen übergeben werden.

Wenn kein Fehler geworfen wurde, wird die ```issEinSandwich()```-Funktion aufgerufen. Wenn ein Fehler geworfen wurde, der dem ```Error.KeinSauberesGeschirrVorhanden```-Fall entspricht, wird die ```geschirrWaschen()```-Funktion aufgerufen. Wenn ein Fehler geworfen wurde, der dem ```Error.ZutatenFehlen```-Fall entspricht, wird die ```lebensmittelEinkaufen(_:)```-Funktion mit dem  ```[String]```-Wert aufgerufen, der vom ```catch```-Muster eingefangen wurde.

Werfen, fangen und weitergeben von Fehlern ist unter [Fehlerbehandlung](TO BE DEFINED) genauer beschrieben.

## Assertionen

In manchen Fällen ist es deinem Code einfach nicht möglich weiterzuarbeiten, da gewisse Bedingen nicht erfüllt sind. In diesen Fällen kannst du eine _Assertion_ in deinem Code auslösen und die Ausführung deines Codes damit verhindern. Du hast damit auch die Möglichkeit die Ursache der fehlenden oder falschen Werte zu analysieren.

### Debugging mit Assertionen

Eine Assertion ist eine Laufzeitprüfung, ob ein boolscher Ausdruck zu ```true``` evaluiert wird. Wortwörtlich genommen _versichert_ eine Assertion, dass eine Bedingung erfüllt ist. Du kannst Assertionen verwenden um sicher zu stellen, dass essentielle Bedinungen erfüllt sind, bevor der Code weiter ausgeführt wird. Wenn deine Bedingung zu ```true``` evaluiert, läuft dein Code normal weiter. Wenn die Bedingung zu ```false``` evaluiert, wird die Ausführung des Codes gestoppt und deine Anwendung wird beendet.

Wenn dein Code eine Assertion auslöst, während er in einer Debugging-Umgebung läuft (z.B. wenn du die Anwendung mit Xcode ausführst), siehst du genau, wo der ungültige Zustand auftrat und du kannst den Zustand deiner Anwendung zum Zeitpunkt der Assertion abfragen. Eine Assertion lässt dich zudem auch eine passende Nachricht angeben, um die Ursache der Assertion zu beschreiben.

Du schreibst eine Assertion in Swift mit der globalen Funktion ```assert(_:_file:line:)```. Du übergibst der funktion einen Ausdruck, der entweder zu ```true``` oder ```false``` evaluiert werden kann. Zudem kannst du eine Nachricht angeben, die ausgegen wird, wenn der Ausdruck zu ```false``` evaluiert wird:

```Swift
let alter = -3
assert(alter >= 0, "Das Alter eine Person kann nicht kleiner als 0 sein")
// Dies löst die Assertion aus, da 'alter' nicht >= 0 ist
```

In diesem Beispiel wird der Code nur weiter ausgeführt, wenn ```alter >= 0``` zu ```true``` evaluiert wird, d.h. der Wert von ```alter``` nicht negativ ist. Wenn der Wert von ```alter``` negativ _ist_, wie im Code oben, dann wird die Assertion ausgelöst und die Anwendung beendet.

Die Nachricht kann auch weggelassen werden, wie in folgendem Beispiel:

``` Swift
assert(alter >= 0)
```

> HINWEIS  
> Assertionen werden deaktiviert, wenn dein Code mit Optimierungen kompiliert wird, zum Beispiel wenn du eine Release-Konfiguration in Xcode verwendet.

### Wann werden Assertionen verwendet?

Verwende Assertionen immer dann, wenn eine Bedingung potentiell nicht erfüllt ist, aber zwingend erfüllt werden muss, dass der Code weiter ausgeführt werden kann. Passende Szenarios für Assertionsprüfungen beinhalten:

* Ein Index wird an eine Indexliste übergeben, aber der Index ist entweder zu hoch oder zu tief.
* Ein Wert wird an eine Funktion übergeben, aber die Funktion kann aufgrund eines ungültigen Wertes ihre Aufgabe nicht erfüllen.
* Ein optionaler Wert enthält aktuell ```nil```, aber ein nicht-```nil``` Wert ist zwingend notwendig um den nachfolgenden Code auszuführen.

Für weitere Infos siehe [Index](TO BE DEFINED) und [Funktionen](TO BE DEFINED)

> HINWEIS  
> Assertionen sorgen dafür, dass deine Anwendung beendet wird. Sie sind kein Ersatz dafür, dass du deinen Code so schreibst, dass ungültige Situationen gar nicht erst eintreten. Es gibt aber trotzdem Fälle, in denen ungültige Zustände möglich sind. In diesen Fällen kann mit Assertionen effektiv sichergestellt werden, dass diese Zustände schon während der Entwicklung entdeckt werden, bevor deine Anwendung veröffentlicht wird.

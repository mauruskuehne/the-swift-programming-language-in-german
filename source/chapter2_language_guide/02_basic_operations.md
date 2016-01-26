# Basisoperatoren

Ein Operator ist ein spezielles Zeichen oder Phrase, mit welchem du Werte prüfen, verändern oder kombinieren kannst. Der Additionsoperator (```+```) beispielsweise zählt zwei Zahlen zusammen (wie in ```let i = 1 + 2```). Ein komplexeres Beispiel wäre der logische AND Operator ```&&``` (wie in ```if zahlenCodeEingegeben && retinaScanErfolgreich```) oder dem Inkrementoperator ```++i```, welcher eine Abkürzung für die Addition von ```1``` zu ```i``` ist.

Swift unterstützt die meisten Standard C-Operatoren und verbessert einige Möglichkeiten um häufige Programmierfehler zu verhindern. Der Zuweisungsoperator (```=```) gibt keinen Wert zurück, so wird er nicht aus Versehen anstelle des Vergleichsoperators (```==```) verwendet. Arithmetische Operatoren (```+```, ```-```, ```*```, ```/```, ```%``` usw.) ermitteln und verhindern Wertüberläufe. So treten keine unerwarteten Resultate auf, wenn mit Zahlen gearbeitet wird, welche größer oder kleiner werden als der Wertebereich des Typs, in dem sie gespeichert sind. Du kannst Wertüberläufe explizit erlauben, indem du die [Wertüberlauf-Operatoren](./25_advanced_options.md) von Swift verwendest.

Im Gegensatz zu C kannst du Resteberechnungen (```%```) von Gleitkommazahlen durchführen. Swift bietet zudem zwei in C nicht vorhandene Bereichsoperatoren (```a..<b``` und ```a...b```) zur Abbildung von Wertebereichen.

Dieses Kapitel beschreibt die üblichen Operatoren in Swift. Im Kapitel [Weitergehende Operatoren](./25_advanced_options.md) sind Swifts weitergehende Operatoren, das Implementieren eigener Operatoren und das Definieren von Standardoperatoren für eigene Typen beschrieben.

## Terminologie

Operatoren sind entweder unär, binär oder ternär:

* _Unäre_ Operatoren operieren auf einem einzelnen Zielobjekt (zum Beispiel ```-a```). Unäre Präfixoperatoren stehen direkt vor dem Zielobjekt (wie ```!b```). Unäre Postfixoperatoren stehen direkt nach dem Zielobjekt (wie ```i++```).
* _Binäre_ Operatoren operieren auf zwei Zielobjekten (zum Beispiel ```2 + 3```). Sie sind _infix_ Operatoren und stehen deshalb zwischen den Zielobjekten.
* _Ternäre_ Operatoren operieren auf drei Zielobjekten. Wie in C gibt es in Swift nur einen ternären Operator, den ternären Bedingungsoperator (```a ? b : c```). 

Die von Operatoren betroffenen Werte werden _Operanden_ genannt. Im Ausdruck ```1 + 2``` steht das Symbol ```+``` für einen binären Operator und seine zwei Operanden sind die Werte ```1``` und ```2```.

## Zuweisungsoperator

Der _Zuweisungsoperator_ (```a = b```) initialisiert oder aktualisiert den Wert von ```a``` mit dem Wert von ```b```:

```Swift
let b = 10
var a = 5
a = b
// a hat nun den Wert 10
```

Wenn auf der rechten Seite der Zuweisung ein Tupel mit mehreren Werten ist, können seine Elemente in einem Schritt in mehrere Konstanten oder Variablen zerlegt werden:

```Swift
let (x, y) = (1, 2)
// x entspricht 1 und y entspricht 2
```

Im Gegensatz zu C und Objective-C gibt der Zuweisungsoperator selbst keinen Wert zurück. Die folgende Anweisung ist deshalb nicht gültig:

```Swift
if x = y {
  // Dies ist nicht gültig, da x = y keinen Wert zurückgibt
}
```

Diese Funktion verhindert, dass der Zuweisungsoperator (```=```) ausversehen anstelle des Vergleichsoperators (```==```) verwendet wird. Swift hilft dir damit, diese Art von Fehlern zu vermeiden.

## Arithmetische Operatoren

Swift unterstützt die vier _arithmetischen Standardoperatoren_ für alle Zahlentypen:

* Addition (```+```)
* Subtraktion (```-```)
* Multiplikation (```*```)
* Division (```/```)

```Swift
1 + 2       // entspricht 3
5 - 2       // entspricht 2
2 * 3       // entspricht 6
10.0 / 2.5  // entspricht 4.0
```

Im Gegensatz zu C und Objective-C erlauben die arithmetischen Operatoren standardmäßig kein Überlauf der Werte. Wenn du dieses Verhalten benötigst, kannst du Swifts Überlaufoperatoren verwenden (wie zum Beispiel ```a &+ b```). Siehe dazu [Überlaufoperatoren](./25_advanced_options.md).

Der Additionsoperator wird auch für das zusammenhängen von ```String```s verwendet:

```Swift
"Hallo, " + "Welt" // entspricht "Hallo, Welt"
```

### Restoperator

Der _Restoperator_ (```a % b```) berechnet wie oft ```b``` in ```a``` Platz hat und gibt den übrig gebliebenen Wert zurück (den _Rest_).

>HINWEIS  
Der Restoperator (```%```) ist in anderen Sprachen als _Modulo-Operator_ bekannt. Aufgrund des Verhaltens mit negativen Zahlen handelt es sich in Swift aber genau genommen um einen Restoperator anstelle eines Modulo-Operators.

Schauen wir uns an, wie der Restoperator funktioniert. Um ```9 % 4``` zu berechnen, müssen wir zuerst herausfinden, wie oft ```4``` in ```9``` Platz hat:

<img src="TO BE DEFINED/> 

```4``` hat zwei Mal Platz in ```9```, der Rest beträgt ```1``` (in Orange dargestellt).

In Swift wird das folgendermßen geschrieben:

```Swift
9 % 4   // entspricht 1
```

Um die Antwort für ```a % b``` zu erhalten, berechnet der Operator folgende Gleichung und gibt ```Rest``` als Ausgabe aus:

```a = (b x ein Multiplikator) + Rest```

Wobei ```ein Multiplikator``` die größte Zahl ist mit der ```b``` multipliziert werden kann, bei der das Ergebnis immer noch in ```a``` Platz hat.

Fügen wir nun ```9``` und ```4``` in die Gleichung ein:

```9 = (4 x 2) + 1```

Die gleiche Methode wird auch verwendet um den Rest für ein negatives ```a``` zu berechnen:

```Swift
-9 % 4  // entspricht -1
```

Wird ```-9``` und ```4``` in die Gleichung eingesetzt, ergibt sich folgendes:

```-9 = (4 x -2) + -1```

Was einem Rest von ```-1``` entspricht.

Das Vorzeichen von ```b``` wird für negative Werte in ```b``` ignoriert. Das bedeutet, dass ```a % b``` und ```a % -b``` immer das gleiche Resultat ergeben.

### Restberechnung mit Gleitkommazahlen

Anders als in C und Objective-C, kann der Restoperator auch mit Gleitkommazahlen verwendet werden:

```Swift
8 % 2.5 // entspricht 0.5

In diesem Beispiel wird ```8``` durch ```2.5``` geteilt. Dies ergibt ```3``` mit einem Rest von ```0.5```. Der Restoperator gibt somit einen ```Double``` Wert von ```0.5``` zurück.

<img src="TO BE DEFINED" />

### Inkrement- und Dekrementoperatoren

Swift bietet genauso wie C einen Inkrementoperator (```++```) und einen Dekrementoperator (```--```) als eine Abkürzung um einen numerischen Wert um ```1``` zu erhöhen oder zu verringern. Du kannst diese Operatoren mit allen Integer- und Gleitkommazahl-Variablen verwenden.

```Swift
var i = 0
++i     // i entspricht nun 1
```

Jedes Mal wenn du ```++i``` aufrufst, wird der Wert von ```i``` um ```1``` erhöht. Grundsätzlich ist ```++i``` eine Abkürzung für ```i = i + 1```. Genauso ist ```--i``` eine Abkürzung für ```i = i - 1```.

Die ```++``` und ```--``` Symbole können als Präfix- oder als Postfix-Operatoren verwendet werden. ```++i``` und ```i++``` sind beides gültige Varianten um den Wert von ```i``` um ```1``` zu erhöhen. Genauso sind ```--i``` und ```i--``` beides gültige Varianten um den Wert von ```i``` um ```1``` zu verringern.

Beachte, dass diese Operatoren ```i``` verändern und auch einen Wert zurückgeben. Wenn du nur den Wert von ```i``` erhöhen oder verringern möchtest, kannst du den zurückgegebenen Wert ignorieren. Wenn du den Rückgabewert _verwendest_, ist er je nachdem unterschiedlich, ob du die Postfix oder die Präfix Variante verwendest. Dabei gelten folgende Regeln:

* Wenn der Operator _vor_ der Variable steht, wird die Variable _vor_ der Rückgabe des Werts erhöht.
* Wenn der Operator _nach_ der Variable steht, wird die Variable _nach_ der Rückgabe des Werts erhöht.

Als Beispiel:

```Swift
var a = 0
let b = ++a
// a und b haben nun beide den Wert 1
let c = a++
// a hat nun den Wert 2, c hat aber immer noch den unveränderten Wert 1
```

Im Beispiel oben wird ```a``` in ```let b = ++a``` inkrementiert, _bevor_ der Wert zurückgegeben wird. Deshalb haben sowohl ```a```, als auch ```b``` den neuen Wert ```1```.

Bei ```let c = a++``` hingegen wird ```a``` _nach_ der Rückgabe des Werts erhöht. Das heißt, ```c``` erhält den alten Wert ```1``` und ```a``` erhält den neuen Wert ```2```.

Sofern du das Verhalten von ```i++``` nicht zwingend benötigst, solltest du immer ```++i``` und ```--i``` verwenden. Sie haben das üblicherweise erwartete Verhalten, dass der Wert von ```i``` zuerst verändert und dann zurückgegeben wird.

### Unärer Minusoperator

Das Vorzeichen eines numerischen Wertes kann gewechselt werden, indem ein ```-``` vorangestellt wird. Dies wird auch der _unäre Minusoperator_ genannt. 

```Swift
let drei = 3
let minusDrei = -drei       // minusDrei entspricht -3
let plusDrei = -minusDrei   // plusDrei entspricht 3 oder "minus minus drei"
```

Der unäre Minusoperator (```-```) wird direkt vor dem Wert geschrieben auf dem er operiert, ohne ein Leerzeichen dazwischen.

### Unärer Plusoperator

Der _unäre Plusoperator_ (```+```) gibt einfach den Wert auf dem er operiert unverändert wieder zurück:

```Swift
let minusSechs = -6
let auchMinusSechs = +minusSechs    // auchMinusSechs entspricht -6
```

Obwohl der unäre Plusoperator nichts macht, kann er verwendet werden um die Symmetrie im Code zu wahren, wenn du mit dem unären Minusoperator für negative Zahlen arbeitest.

## Zusammengesetzte Zuweisungsoperatoren

Wie in C gibt es auch in Swift _zusammengesetzte Zuweisungsoperatoren_, welche die Zuweisung (```=```) mit einer anderen Operation kombinieren. Ein Beispiel dafür ist der _Additions-Zuweisungsoperator_ (```+=```):

```Swift
var a = 1
a += 2
// a hat nun den Wert 3
```

Der Ausdruck ```a += 2``` ist eine Abkürzung für ```a = a + 2```. Die Addition und die Zuweisung werden in einem Operator kombiniert und werden in einem Schritt ausgeführt.

>HINWEIS  
Die zusammengesetzten Zuweisungsoperatoren haben keinen Rückgabewert. Du kannst deshalb ```let b = a += 2``` nicht verwenden.
Dieses Verhalten ist anders als bei den oben erwähnten Inkrement- und Dekrement-Operatoren.

Eine Komplette List der zusammengesetzten Zuweisungsoperatoren findest du unter [Ausdrücke](../chapter3_language_reference/04_expressions.md).

## Vergleichsoperatoren

Swift unterstützt alle Standard C Vergleichsoperatoren.

* Gleich (```a == b```)
* Nicht gleich (```a != b```)
* Größer als (```a > b```)
* Kleiner als (```a < b```)
* Größer als oder gleich (```a >= b```)
* Kleiner als oder gleich  (```a <= b```)

>HINWEIS  
Swift bietet auch zwei _Identitätsoperatoren_ (```===``` und ```!==```), welche prüfen, ob zwei Objektreferenzen auf die gleiche Objektinstanz verweisen. Mehr Informationen findest du unter [Klassen und Strukturen](./09_classes_and_structures.md).

Jeder Vergleichsoperator gibt einen ```Bool``` Wert zurück um anzugeben, ob die Anweisung wahr ist:

```Swift
1 == 1  // wahr, 1 ist gleich 1
2 != 1  // wahr, 2 ist nicht gleich 1
2 > 1   // wahr, 2 ist größer als 1
1 < 2   // wahr, 1 ist kleiner als 2
1 >= 1  // wahr, 1 ist größer als oder gleich 1
2 <= 1  // falsch, 2 ist nicht kleiner als oder gleich 1
```

Vergleichsoperatoren werden oft in Bedingungsanweisungen verwendet, wie zum Beispiel der ```if```-Anweisung:

```Swift
let name = "welt"
if name == "welt" {
    print("Hallo, Welt")
} else {
    print("Tut mir leid, \(name), aber ich kenne dich nicht.")
}
// Gibt "Hallo, Welt" aus, da name gleich ist wie "welt"
```

Mehr zur ```if```-Anweisung ist unter [Kontrollfluss](./05_control_flow.md) beschrieben.

## Ternärer Bedingungsoperator

Der _ternäre Bedingungsoperator_ ist ein spezieller Operator mit drei Teilen in der Form von ```frage ? antwort1 : antwort2```. Er ist eine Abkürzung um eine von beiden Ausdrücken auszuwerten, je nach dem, ob ```frage``` wahr oder falsch ist. Wenn ```frage``` wahr ist, wird ```antwort1``` ausgewertet, sonst ```antwort2```. Der Wert des Ausdrucks wird anschließend zurückgegeben.

Der ternäre Bedingungsoperator ist eine Abkürzung für untenstehenden Code:

```Swift
if frage {
    antwort1
} else {
    antwort2
}
```

Hier ist ein Beispiel, welches die Höhe für eine Tabellenzeile berechnet. Die Zeilenhöhe soll 50 Punkte höher sein als der Inhalt, wenn die Zeile eine Überschrift enthält. Wenn nicht, soll sie 20 Punkte größer sein:

```Swift
let inhaltsHoehe = 40
let hatUeberschrift = true
let zeilenHoehe = inhaltsHoehe + (hatUeberschrift ? 50 : 20)
// zeilenHoehe hat den Wert 90
```

Das obige Beispiel ist eine abgekürzte Variante von untenstehendem Code:

```Swift
let inhaltsHoehe = 40
let hatUeberschrift = true
var zeilenHoehe = inhaltsHoehe
if hatUeberschrift {
    zeilenHoehe = zeilenHoehe + 50
} else {
    zeilenHoehe = zeilenHoehe + 20
}
// zeilenHoehe hat den Wert 90
```

Dank dem ternären Bedingungsoperator kann ```zeilenHoehe``` mit einer Zeile Code auf den richtigen Wert gesetzt werden. Dies ist kompakter als das zweite Beispiel. Zudem muss ```zeilenHoehe``` nicht als Variable definiert werden, da der Wert nicht mehr in der ```if```-Anweisung verändert wird.

Der ternäre Bedingungsoperator ist eine effiziente Abkürzung um zwischen zwei Ausdrücken zu wählen. Verwende den ternären Bedingungsoperator aber mit Vorsicht. Seine Kompaktheit kann zu schwer lesbarem Code führen, wenn er zu oft eingesetzt wird. Vermeide es, mehrere ternäre Bedingungsoperatoren in einer Zeile zu kombinieren.

## Nil-Sammeloperator

Der _Nil-Sammeloperator_ (```a ?? b```) liest aus dem optionalen ```a``` den Wert aus. Wenn kein Wert vorhanden ist (```a``` ist ```nil```), wird der Wert von ```b``` zurückgegeben. Der Ausdruck ```b``` muss vom gleichen Typ sein wie der Wert, der in ```a``` gespeichert ist.

Der Nil-Sammeloperator ist die Kurzschreibweise für folgenden Code:

```Swift
a != nil ? a! : b
```

Der Code oben verwendet den ternären Bedingungsoperator und erzwungenes Auspacken (```a!```) um auf den Wert von ```a``` zuzugreifen, wenn ```a``` nicht ```nil``` ist, sonst wird ```b``` zurückgegeben. Der Nil-Sammeloperator bietet eine elegante Form für diese bedingte Prüfung und das Auspacken des Wertes.

>HINWEIS
Wenn der Wert von ```a``` nicht ```nil``` ist, wird ```b``` nicht evaluiert. Dieses Verhalten wird _Kurzschlussauswertung_ genannt. 

Im unteren Beispiel wird der Nil-Sammeloperator verwendet um zwischen einer benutzerdefinierten Farbe und einer Standardfarbe zu wählen:

```Swift
let standardfarbe = "rot"
var benutzerdefinierteFarbe: String?    // Standardmäßig nil

var benutzterFarbname = benutzerdefinierteFarbe ?? standardfarbe
// benutzerdefinierteFarbe ist nil, benutzterFarbname hat deshalb den Standardwert "rot"
```

Die Variable ```benutzerdefinierteFarbe``` ist als optionaler ```String``` mit einem Standardwert von ```nil``` definiert. Weil ```benutzerdefinierteFarbe``` einen optionalen Typ hat, kannst du den Nil-Sammeloperator beim Zugriff auf den Wert verwenden. Im Beispiel oben wird der Operator für die Ermittlung eines Standardwertes für die ```String```-Variable namens ```benutzterFarbname``` verwendet. Da ```benutzerdefinierteFarbe``` ```nil``` ist, gibt der Ausdruck ```benutzerdefinierteFarbe ?? standardfarbe``` den Wert von ```standardfarbe``` zurück, ```"rot"```.

Wenn du einen nicht-```nil``` Wert der Variable ```benutzerdefinierteFarbe``` zuweist und den Nil-Sammeloperator nochmals ausführst, wird stattdessen der Wert in der Variable ```benutzerdefinierteFarbe``` verwendet:

```Swift
benutzerdefinierteFarbe = "grün"
benutzterFarbname ? benutzerdefinierteFarbe ?? standardfarbe
// benutzerdefinierteFarbe ist nicht nil, benutzterFarbname wird auf "grün" gesetzt.
```

## Bereichsoperatoren

Swift beinhaltet zwei _Bereichsoperatoren_ als Kurzschreibweise um einen Wertebereich auszudrücken.

### Geschlossener Bereichsoperator

Der _geschlossene Bereichsoperator_ (```a...b```) definiert einen Bereich, der von ```a``` bis ```b``` verläuft und die Werte ```a``` und ```b``` beinhaltet. Der Wert von ```a``` darf nicht größer sein als der Wert von ```b```.

Der geschlossene Bereichsoperator ist nützlich, wenn du über einen Bereich iterieren willst, in dem du alle Werte verwenden möchtest, zum Beispiel in einer ```for```-```in```-Schleife:

```Swift
for index in 1...5 {
    print("\(index) mal 5 ist \(index * 5)")
}
// 1 mal 5 ist 5
// 2 mal 5 ist 10
// 3 mal 5 ist 15
// 4 mal 5 ist 20
// 5 mal 5 ist 25
```

Weiteres zur ```for```-```in```-Schleife ist unter [Kontrollfluss](TO BO DEFINED) beschrieben.

### Halb-offener Bereichsoperator

Der _halb-offene Bereichsoperator_ (```a..<b```) definiert einen Bereich der von ```a``` nach ```b``` verläuft, ```b``` aber nicht beinhaltet. Er wird ```halb-offen``` genannt, weil er den ersten Wert beinhaltet, aber nicht den letzten Wert. Wie beim geschlossenen Bereichsoperator darf der Wert von ```a``` nicht größer sein als der Wert von ```b```. Wenn die Werte von ```a``` und ```b``` gleich sind, ist der resultierende Bereich leer.

Halb-offene Bereiche sind besonders nützlich, wenn mit Null-basierten Listen, wie zum Beispiel Arrays, gearbeitet wird. Hier möchte man bis zur Länge der Liste hochzählen:

```Swift
let namen = ["Anna", "Alex", "Brian", "Jack"]
let anzahl = namen.count
for i in 0..<anzahl {
    print("Person \(i + 1) heißt \(namen[i])")
}
// Person 1 heißt Anna
// Person 2 heißt Alex
// Person 3 heißt Brian
// Person 4 heißt Jack
```

Beachte, dass das Array vier Elemente beinhaltet, ```0..<anzahl``` zählt aber nur bis 3 (der Index des letzten Elements im Array), da es ein halb-offener Bereich ist. Weiteres zu Arrays findest du unter [Arrays](./04_collection_types.md).

## Logische Operatoren

_Logische Operatoren_ modifizieren oder kombinieren die logischen boolschen Werte ```true``` und ```false```. Swift unterstützt die in C-basierten Sprachen üblichen logischen Operatoren:

* Logisches NICHT (```!a```)
* Logisches UND (```a && b```)
* Logisches ODER (```a || b```)

### Logischer NICHT Operator

Der _logische NICHT Operator_ (```!a```) invertiert einen boolschen Wert. ```true``` wird so zu ```false``` und ```false``` wird zu ```true```.

Der logische NICHT Operator ist ein Präfixoperator und erscheint direkt vor dem Wert auf den er angewendet wird, ohne Leerzeichen dazwischen. Er wird, wie in folgendem Beispiel, als "nicht ```a```" gelesen:

```Swift
let zugriffErlaubt = false
if !zugriffErlaubt {
    print("ZUGRIFF VERWEIGERT")
}
// gibt "ZUGRIFF VERWEIGERT" aus
```

Der Ausdruck ```if !zugriffErlaubt``` kann als "wenn nicht Zugriff erlaubt" gelesen werden. Die darauffolgende Zeile wird nur ausgeführt, wenn "nicht Zugriff erlaubt" wahr ist, das heißt, ```zugriffErlaubt``` muss ```false``` sein.

Eine bedachte Wahl der Benennung von boolschen Konstanten und Variablen helfen den Code präzise und lesbar zu halten. Es können so zudem doppelte Verneinungen und verwirrende logische Ausdrücke vermieden werden.

### Logischer UND Operator

Der _logische UND Operator_ (```a && b```) ist einen logischen Ausdruck in welchem beide Werte ```true``` sein müssen, damit auch der gesamte Ausdruck ```true``` ist.

Wenn einer von beiden Werten ```false``` ist, wird der gesamte Ausdruck ```false```. Genaugenommen, wenn der _erste_ Wert ```false``` ist, wird der zweite Wert gar nicht erst ausgewertet. Es ist dann gar nicht mehr möglich, dass der gesamte Ausdruck ```true``` wird. Dies wird auch _Kurzschlussauswertung_ genannt.

Dieses Beispiel beachtet zwei ```Bool```-Werte und erlaubt den Zugriff nur, wenn beide Werte ```true``` sind:

```Swift
let codeEingegeben = true
let retinaScanBestanden = false

if codeEingegeben && retinaScanBestanden {
    print("Willkommen!")
} else {
    print("ZUGRIFF VERWEIGERT")
}
// gibt "ZUGRIFF VERWEIGET" aus
```

### Logischer ODER Operator

Der _logische ODER Operator_ (```a || b```) ist ein Infixoperator der aus zwei Pipe-Zeichen besteht. Die verwendest ihn um einen logischen Ausdruck zu erstellen, in welchem nur _eine_ von beiden Werten ```true``` sein muss, damit der gesamte Ausdruck ```true``` wird.

Wie der logische UND Operator weiter oben, verwendet der logische ODER Operator die Kurzschlussauswertung bei der Auswertung des Ausdrucks. Wenn die linke Seite des logischen ODER Operators ```true``` ist, wird die rechte Seite nicht ausgewertet, da der Wert des gesamten Ausdrucks nicht mehr verändert werden kann.

Im Beispiel unten ist der erste ```Bool```-Wert (```hatTuerSchluessel```) aber der zweite Wert (```kenntOverridePasswort```) ist ```true```. Da ein Wert ```true``` ist, wird der gesamte Ausdruck zu ```true``` evaluiert:

```Swift
let hatTuerSchluessel = false
let kenntOverridePasswort = true
if hatTuerSchluessel || kenntOverridePasswort {
    print("Willkommen!")
} else {
    print("ZUGRIFF VERWEIGERN")
}
// gibt "Willkommen!" aus
```

### Verknüpfen logischer Operatoren

Du kannst mehrere logische Operatoren verknüpfen um zusammengesetzte Ausdrücke zu erstellen:

```Swift
if codeEingegeben && retinaScanBestanden || hatTuerSchluessel || kenntOverridePasswort {
    print("Willkommen!")
} else {
    print("ZUGRIFF VERWEIGEN")
}
// gibt "Willkommen!" aus
```

Dieses Beispiel verwendet mehrere ```&&``` und ```||``` Operatoren um einen längeren, zusammengesetzten Ausdruck zu erstellen. Die ```&&``` und ```||``` Operatoren arbeiten aber immer noch nur mit zwei Werten. Es sind also eigentlich drei kleinere Ausdrücke die aneinandergehängt wurden. Das Beispiel kann wie folgt gelesen werden:

Wenn wir den korrekten Code eingegeben haben und den Retinascan bestanden haben oder einen gültigen Türschlüssel haben oder wir das Override-Passwort haben, dann haben wir Zugriff.

Basierend auf den Werten von ```codeEingegeben```, ```retinaScanBestanden``` und ```hatTuerSchluessel``` sind die ersten beiden Unterausdrücke ```false```. Wenn aber das Override-Passwort bekannt ist evaluiert dennoch der gesamte Ausdruck zu ```true```.

>HINWEIS
Die logischen Operatoren ```&&``` und ```||``` in Swift sind links-assoziativ. Zusammengesetzte Ausdrücke mit mehreren logischen Operatoren evaluieren deshalb zuerst den Unterausdruck ganz links.

### Explizite Klammern

Manchmal ist es nützlich Klammen zu setzen auch wenn sie nicht unbgedingt benötigt werden. Die Bedeutung von komplexen Ausdrücken wird so einfacher lesbar. Im Türenbespiel oben macht es Sinn, Klammern um den ersten Unterausdruck des zusammengesetzten Ausdrucks zu machen. Der Sinn des Ausdrucks wird so explizit sichtbar:

```Swift
if (codeEingegeben && retinaScanBestanden) || hatTuerSchluessel || kenntOverridePasswort {
    print("Willkommen!")
} else {
    print("ZUGRIFF VERWEIGERT")
}
// gibt "Willkommen!" aus
```

Die Klammern machen klar, dass die ersten beiden Werte ein Teil der Gesamtlogik sind. Das Resultat des zusammengesetzten Ausdrucks verändert sich nicht, die Absicht hinter dem Ausdruck ist aber klarer für den Leser. Lesbarkeit sollte der Kürze des Codes immer vorgezogen werden. Verwende deshalb Klammern wo nötig, um deine Absichten klar auszudrücken.
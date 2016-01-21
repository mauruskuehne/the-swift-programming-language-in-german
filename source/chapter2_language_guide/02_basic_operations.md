# Basisoperatoren

Ein Operator ist ein spezielles Zeichen oder Phrase, mit welchem du Werte prüfen, verändern oder kombinieren kannst. Der Additionsoperator (```+```) beispielsweise zählt zwei Zahlen zusammen (wie in ```let i = 1 + 2```). Ein komplexeres Beispiel wäre der logische AND Operator ```&&``` (wie in ```if zahlenCodeEingegeben && retinaScanErfolgreich```) oder dem Inkrementoperator ```++i```, welcher eine Abkürzung für die Addition von ```1``` zu ```i``` ist. 

Swift unterstützt die meisten standard C-Operatoren und verbessert einige Möglichkeiten um häufige Programmierfehler zu verhindern. Der Zuweisungsoperator (```=```) gibt keinen Wert zurück, so wird er nicht aus Versehen anstelle des Vergleichsoperators (```==```) verwendet. Arithmetische Operatoren (```+```, ```-```, ```*```, ```/```, ```%``` usw.) ermitteln und verhindern Wertüberläufe. So treten keine unerwarteten Resultate auf, wenn mit Zahlen gearbeitet wird, welche grösser oder kleiner werden als der Wertebereich des Typs, in dem sie gespeichert sind. Du kannst Wertüberläufe explizit erlauben, indem du die [Wertüberlauf-Operatoren](TO BE DEFINED) von Swift verwendest.

Im Gegensatz zu C kannst du Resteberechnungen (```%```) von Gleitkommazahlen durchführen. Swift bietet zudem zwei in C nicht vorhandene Bereichsoperatoren (```a..<b``` und ```a...b```) zur Abbildung von Wertebereichen.

Dieses Kapitel beschreibt die üblichen Operatoren in Swift. Im Kapitel [Weitergehende Operatoren](TO BE DEFINED) sind Swifts weitergehende Operatoren, das Implementieren eigener Operatoren und das Definieren von Standardoperatoren für eigene Typen beschrieben.

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

Im Gegensatz zu C und Objective C erlauben die arithmetischen Operatoren standardmässig kein Überlauf der Werte. Wenn du dieses Verhalten benötigst, kannst du Swifts Überlaufoperatoren verwenden (wie zum Beispiel ```a &+ b```). Siehe dazu [Überlaufsoperatoren](TO BE DEFINED).

Der Additionsoperator wird auch für ```String```-Konkatenierung verwenden:

```Swift
"Hallo, " + "Welt" // entspricht "Hallo, Welt"
```

### Restoperator

Der _Restoperator_ (```a % b```) berechnet wie oft ```b``` in ```a``` Platz hat und gibt den übrig gebliebenen Wert zurück (den _Rest_).

>HINWEIS  
Der RestOperator (```%```) ist in anderen Sprachen als _Modulo-Operator_ bekannt. Aufgrund des Verhaltens mit negativen Zahlen handelt es sich in Swift aber genau genommen um einen Restoperator anstelle eines Modulo-Operators.

Schauen wir uns an, wie der Restoperator funktioniert. Um ```9 % 4``` zu berechnen, müssen wir zuerst herausfinden, wie oft ```4``` in ```9``` Platz hat:

<img src="TO BE DEFINED/> 

```4``` hat zwei Mal Platz in ```9```, der Rest beträgt ```1``` (in Orange dargestellt).

In Swift wird das folgendermassen geschrieben:

```Swift
9 % 4   // entspricht 1
```

Um die Antwort für ```a % b``` zu erhalten, berechnet der Operator folgende Gleichung und gibt ```Rest``` als Ausgabe aus:

```a = (b x ein Multiplikator) + Rest```

Wobei ```ein Multiplikator``` die grösste Zahl ist mit der ```b``` multipliziert werden kann, bei der das Ergebnis immer noch in ```a``` Platz hat.

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

Die ```++``` und ```--``` Symbole können als Präfix- oder als Postfix-Operatoren verwendet werden. ```++i```und ```i++``` sind beides gültige Varianten um den Wert von ```i``` um ```1``` zu erhöhen. Genauso sind ```--i``` und ```i--``` beides gültige Varianten um den Wert von ```i``` um ```1``` zu verringern.

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

Bei ```let c = a++``` hingegen wird ```a``` _nach_ der Rückgabe des Werts erhöht. Das heisst, ```c``` erhält den alten Wert ```1``` und ```a``` erhält den neuen Wert ```2```.

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


a

a
a

a
a

a
a

a
a

a
a

a
a

a
a

a

a

a

adsf
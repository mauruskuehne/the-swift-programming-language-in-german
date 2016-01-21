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

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


Operators are unary, binary, or ternary:

Unary operators operate on a single target (such as -a). Unary prefix operators appear immediately before their target (such as !b), and unary postfix operators appear immediately after their target (such as i++).
Binary operators operate on two targets (such as 2 + 3) and are infix because they appear in between their two targets.
Ternary operators operate on three targets. Like C, Swift has only one ternary operator, the ternary conditional operator (a ? b : c).
The values that operators affect are operands. In the expression 1 + 2, the + symbol is a binary operator and its two operands are the values 1 and 2.



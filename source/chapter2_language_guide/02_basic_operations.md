# Basisoperatoren

Ein Operator ist ein spezielles Zeichen oder Phrase, mit welchem du Werte prüfen, verändern oder kombinieren kannst. Der Additionsoperator (```+```) beispielsweise zählt zwei Zahlen zusammen (wie in ```let i = 1 + 2```). Ein komplexeres Beispiel wäre der logische AND Operator ```&&``` (wie in ```if zahlenCodeEingegeben && retinaScanErfolgreich```) oder dem Inkrementoperator ```++i```, welcher eine Abkürzung für die Addition von ```1``` zu ```i``` ist. 

Swift unterstützt die meisten standard C-Operatoren und verbessert einige Möglichkeiten um häufige Programmierfehler zu verhindern. Der Zuweisungsoperator (```=```) gibt keinen Wert zurück, so wird er nicht aus Versehen anstelle des Vergleichsoperators (```==```) verwendet. Arithmetische Operatoren (```+```, ```-```, ```*```, ```/```, ```%``` usw.) ermitteln und verhindern Wertüberläufe. So treten keine unerwarteten Resultate auf, wenn mit Zahlen gearbeitet wird, welche grösser oder kleiner werden als der Wertebereich des Typs, in dem sie gespeichert sind. Du kannst Wertüberläufe explizit erlauben, indem du die [Wertüberlauf-Operatoren](TO BE DEFINED) von Swift verwendest.

Im Gegensatz zu C kannst du Resteberechnungen (```%```) von Gleitkommazahlen durchführen. Swift bietet zudem zwei in C nicht vorhandene Bereichsoperatoren (```a..<b``` und ```a...b```) zur Abbildung von Wertebereichen.

Dieses Kapitel beschreibt die üblichen Operatoren in Swift. Im Kapitel [Weitergehende Operatoren](TO BE DEFINED) sind Swifts weitergehende Operatoren, das Implementieren eigener Operatoren und das Definieren von Standardoperatoren für eigene Typen beschrieben.

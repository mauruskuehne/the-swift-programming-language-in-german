# Über die Dokumentation

Dieser Teil des Buches beschreibt die formale Grammatik von Swift. Die hier beschrieben Grammatik hat die Intetion, dich mehr Details der Sprache verstehen zu lassen. Es ist nicht das Ziel, dass du einen eigenen Parser oder Compiler schreiben kannst.  

Swift ist recht klein, weil viele Typen, Funktionen und Operatoren, die so gut wie überall in Swift vor kommen, in der Standardbibliothek definiert sind. Obwohl diese Typen, Funktionen und Operatoren nicht Bestandteil von Swift an sich sind, werden sie intensiv in der Dokumentation und den Beispielen dieses Buches genutzt.  

## Wie die Grammatik zu lesen ist

Für die Notation der Grammatik von Swift gibt es einige Konventionen:
- Ein Pfeil (```→```) wird genutzt, um eine Regel zu definieren und wird gelesen als "besteht aus".
- Nonterminalsymbole werden *kursiv* markiert und können auf beiden Seiten einer Regel auftreten.
- Terminalsymbole werden fett und mit konstanter Buchstabenbreite dargestellt. Sie treten nur auf der rechten Seite einer Regel auf.
- Alternativen werden mit einer Pipe (```|```) voneinander getrennt. Wenn Alternativen zu lang oder komplex sind, werden sie voneinander getrennt auf mehrere Zeilen aufgeteilt.
- In manchen Fällen wird ein normaler Font genutzt, um die rechte Seite einer Regel zu beschreiben.
- Optionale Nonterminale und Termine werden mit einem tiefer gesetzten ```opt``` gekenntzeichnet.

Als Beispiel wird im Folgenden die Grammatik für den ```Getter-Setter-Block``` gezeigt:

> GRAMMATIK EINES GETTER-SETTER-BLOCKS  
> getter-setter-block → { getter-clause setter-clause<sub>opt</sub> } | { getter-clause setter-clause }

Diese Definition zeigt, dass ein ```getter-setter-Block``` aus einem ```getter``` und einem optionalen ```setter``` besteht, die in geschweifte Klammern zusammen gefasst werden *oder* aus einem ```setter``` gefolgt von einem ```getter```, ebenfalls in geschweifte Klammern eingeschlossen. Diese Regel ist identisch zu den beiden folgenden Regeln, bei die beiden Alternativen separiert dargestellt sind:  


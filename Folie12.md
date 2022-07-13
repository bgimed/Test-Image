---
question: Was ist die Umgebung im Kontext einer Programmiersprache und wie werden Programme ausgewertet ?
title: Namengebung, Umgebung und Auswertungsregeln
---

## Namensgebung und Umgebung

Ein wichtiger Aspekt einer Programmiersprache ist die Möglichkeit, Objekte über Namen zu referenzieren.

Ein Name identifiziert eine Variable, deren Wert ein Objekt ist.

Umgebung: der Interpreter unterhält eine Art Speicher, um Name-Objekt Paare zu verwalten.
Assoziiere die Werte mit den Symbolen.
Hole die Werte später über die Symbole.
Um den Wert auszurechnen, der durch den Namen repräsentiert wird, reicht es, ihn in der Umgebung aufzulösen.

Beispiel: Die Evaluierung von score ist 30
```
(define score (+ 27 3))
(define total (+ 30 15))
(* 100 (/ score total))
```
Beachte: Wir haben das (implizit) schon gemacht für die Symbole
der arithmetischen Operatoren +, *, usw.
(d.h. den Wert erhalten, der durch diese Namen referenziert wird)


## Auswertungsregel
Selbstauswertend (self-rule) → gib den Wert zurück

Die Werte der Ziffern sind die Zahlen, die sie bezeichnen.

Eingebauter Operator → gib die Sequenz der Maschineninstruktionen zurück, die die entsprechenden Operationen durchführen.

Name (name-rule) → gib den Wert zurück, der in der Umgebung mit diesem Namen assoziiert wurde.

Sonderform → mache etwas Besonderes.

Kombination →

1. Werte die Unterausdrücke (in beliebiger Reihenfolge) aus
2. Wende die Prozedur, die der Wert des am weitesten links
liegenden Unterausdruckes ist (der Operator), auf die
Argumente an – die Werte der restlichen Unterausdrücke
(Operanden).

Beispiel einer Kombination: (+ 4 (* 2 3)).
Die Auswertungsregel ist rekursiv.


Bei einer Kombination ruft die Regel sich selbst auf.
Jedes Element muss ausgewertet werden, bevor die
Gesamtauswertung einer Kombination abgeschlossen werden
kann.

Die Auswertung der folgenden Kombination erfordert die Anwendung der Auswertungsregel auf vier unterschiedliche Kombinationen.
````
 ( * (+ 2 (* 4 6) ) (+ 3 5 7) )
````


### Lesen-Auswerten-Ausgeben-Schleife

define-Regel: Werte nur den zweiten Operanden aus, der Name des ersten Operanden ist an den berechneten Wert gebunden Gesamtwert des Ausdrucks ist undefiniert


Namensregel: Schlage in der aktuellen Umgebung den Wert unter dem Namen nach
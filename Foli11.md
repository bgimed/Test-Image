---
question: Was sind die Grundelemente der Programmierung und wie werden Programme strukturiert ?
title: Grundelmente der Programmierung
---
# Grundelemente der Programmierung

### Strukturierungsmechanismen einer Programmiersprache.
Eine mächtige Programmiersprache ist mehr als ein Hilfsmittel um einen Computer anzuweisen, Aufgaben durchzuführen. 
Sie dient auch als Rahmen, innerhalb dessen wir unsere Ideen über die Problemdomäne organisieren.

Wenn wir eine Sprache beschreiben, sollten wir die Hilfsmittel beachten, die sie uns zum
Kombinieren von einfachen Ideen anbietet, um komplexere Ideen zu bilden.

Jede mächtige Programmiersprache hat **_drei Mechanismen,_** um Prozessideen zu strukturieren:

Primitive Ausdrücke: repräsentieren die einfachsten Einheiten der Sprache.

Kombinationsmittel: Zusammengesetzte Elemente werden aus einfacheren Einheiten konstruiert.

Abstraktionsmittel: Zusammengesetzte Elemente können benannt und weiter als
Einheiten manipuliert werden.



### Strukturierungsmechanismen in der Elektronik

Primitive: Widerstände, Kondensatoren, Induktivitäten, Spannungsquellen, ...
Kombinationsmittel :Richtlinien für das Verdrahten der Schaltkreise
Standardschnittstellen: (z.B. Spannungen, Strömungen) zwischen den
Elementen

Abstraktionsmittel “Black box” Abstraktion – denke über einen Unter-Schaltkreis als eine
Einheit: z.B. Verstärker, Regler, Empfänger, Sender, ...



## Sprachelemente – Die Primitiven

### Zahlen Beispiele: 23, - 36 
Zahlen sind selbstauswertend: Die Werte der Ziffern sind die Zahlen, die sie bezeichnen. 23->23, 36->36

## Boolesche Werte
true und false ebenfalls selbstauswertend

## Namen für eingebaute Prozeduren


Beispiele: +, *, /, -, =,
Was ist der Wert von so einem Ausdruck?
Der Wert von + ist eine Prozedur, die Zahlen addiert
Das werden wir später als „Higher-Order Procedures“ kennenlernen
Auswertung: Nachschlagen des dem Namen zugewiesenen Wertes.



## Besonderheiten bei Zahlen

DrRacket rechnet immer genau, wenn das möglich ist.

Ganze Zahlen und endliche Dezimalzahlen „wie üblich“
Brüche mit periodischem Ergebnis
Darstellung in einem Text: ebenfalls als Bruch, etwa „7/3“
Ausgabe direkt im Fenster: als Periode, etwa - 2.

Nicht jede Zahl kann exakt dargestellt werden

Beschränkungen durch Verwendung des Binärsystems
Faustformel: „mehr Dezimalstellen -> mehr Probleme“
Zahlen unendlicher Länge ohne Periode : #i „inexact“
e: #i2.
pi: #i3.
√2: #1.

Mit Brüchen oder „inexakten“ Zahlen kann normal gerechnet werden – das Ergebnis ist aber ggf. wieder „inexact“

```
(√2)^2 = #i2.
```



## Sprachelemente – Kombinationen:
Der Wert einer Kombination wird bestimmt durch die Ausführung der (durch den Operator) angegebenen Prozedur mit den Werten der Operanden.

Präfixdarstellung (+ 2 3) öffnende Klammer Operator Operanden schließende Klammer

Zusammengesetztes Element ist eine Sequenz von Ausdrücken, eingeschlossen in Klammern.
Die Ausdrücke sind primitiv oder erneut zusammengesetzt.

Beispiel: Numerische Ausdrücke können mit Ausdrücken kombiniert werden,
die primitive Prozeduren repräsentieren (z.B. + oder *), um einen
zusammengesetzten Ausdruck zu erstellen.

Kombinationen können verschachtelt werden – Regeln einfach
rekursiv anwenden.
Eine Kombination bedeutet immer eine Anwendung einer Prozedur.

Klammern können nicht eingefügt oder weggelassen werden,
ohne die Bedeutung des Ausdrucks zu ändern.

```` 
(+ 4 (* 2 3)) = (4 + (2 * 3)) = 10
(* (+ 3 4) (- 8 2))
= ((3 + 4) * (8 - 2))
= 42
````
## Sprachelemente: Abstraktionen

1. Erstelle eine komplexe Sache aus primitiveren Sachen,

2. Benenne sie,

3. Behandle sie als eine primitive Sache.

````
(define score (+ 27 3))

(define PI 3.14)
````
Einfachstes Abstraktionsmittel: define.
Sonderformen: Geklammerte Ausdrücke, die mit einem der wenigen HtDP-TL-Schlüsselwörter starten. Beispiel: define
Mit define kann man einen Wert an einen Namen binden
Beispiel: (define score (+ 27 3))
Die define Sonderform wertet den zweiten Ausdruck nicht aus (in
dem Beispiel: score )
Sie assoziiert diesen Namen mit dem Wert des dritten Ausdruckes in
einer Umgebung.

Der Rückgabewert einer Sonderform ist nicht spezifiziert.
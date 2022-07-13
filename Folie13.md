---
question: Wie Kann man neue Prozeduren definieren und wie sollte man mit Programmierfehlern umgehen ?
title: Prozedurendefinition und Umgang mit Fehler
---
### Definition neuer Prozeduren. 
Haben folgende Kombinationen etwas gemeinsam?
````
 (* 3.14 (* 5 5))

 (* 3.14 (* 23.2 23.2))

 (* 3.14 (* r r))
````
Wie generalisieren wir?

Wie drücken wir die Idee von “Fläche eines Kreises” aus?
Alle sind Beispiele einer Kreisflächenberechnung.
Um wiederkehrende Muster festzuhalten, benutzen wir Prozeduren.

Analog zu einer Funktionsdefinition in der Mathematik. Deshalb verwenden wir auch manchmal den Namen Funktion.

Die define - Sonderform wird benutzt, um neue Prozeduren zu erstellen/definieren
````
#Name Parameter
 (define (area-of-disk r)
#Prozedurrumpf
(* 3.14 (* r r)))

````
Sobald eine Prozedur definiert wurde, kann sie wie eine primitive Prozedur (wie +, * etc.) benutzt werden


```
(area-of-disk 5)
-> ergibt 78.5
```
```
(- (area-of-disk 5) (area-of-disk 3))
-> ergibt (78.5 - 28.26) = 50.24
```
Bereits definierte Prozeduren können zu neuen, mächtigeren Prozeduren kombiniert werden. Berechnen der Fläche eines Rings Anwendung der neuen Prozedur.

```
(area-of-ring 5 3)
= (- (area-of-disk 5) (area-of-disk 3))
= (- (* 3.14 (* 5 5)) (* 3.14 (* 3 3)))
= ... = 50.24
```
```` 
(define (area-of-ring outer inner)
(- (area-of-disk outer)
(area-of-disk inner)))
````


## Informelle Beschreibungen:
Typische Programmspezifikation ist üblicherweise nicht in Form mathematischer Ausdrücke, die in
Programme umzuwandeln sind, sondern informelle Problembeschreibungen Enthalten irrelevante oder mehrdeutige Informationen
Beispiel:

“Die Firma XYZ bezahlt ihren Angestellten 12 € pro Stunde. Ein
Angestellter arbeitet zwischen 20 und 65 Stunden pro Woche.
Entwickeln Sie ein Programm, welches den Lohn eines Angestellten aus der Anzahl der Arbeitsstunden berechnet.“

Problemanalyse
````
(define (lohn stundenanzahl)

(* 12 stundenanzahl))
````


## Fehler

Ihre Programme werden Fehler enthalten
Das ist nichts Schlimmes
Lassen Sie sich durch Fehler nicht verwirren/entmutigen

Mögliche Fehler:

Keine korrekte Klammerung, z.B. (* 3 (5)
Operator eines Prozeduraufrufs ist keine Prozedur, z. B.
(10)
(10 + 20)
Typfehler und andere Laufzeitfehler, z.B.
(+ 3 true)
(/ 3 0)
Probieren Sie aus, was bei fehlerhaften Eingaben passiert und versuchen Sie die Fehlermeldungen zu verstehen!
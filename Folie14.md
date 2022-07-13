---
question: Wie sieht der Design-Prozess eines Programmes aus und was sind die hauptschritte ?
title: Design von Programmen
---
## Design von Programmen:
Das Design von Programmen ist nicht trivial
Folgendes Rezept soll Ihnen helfen, Ihre ersten Programme zu schreiben

Schritt-für-Schritt Beschreibung, was zu tun ist. Später wird dieses Rezept verfeinert.

Jede Programmentwicklung besteht aus mindestens den folgenden vier Aktivitäten:

1. Verstehen, was der Zweck des Programms ist

2. Programmbeispiele ausdenken

3. Den Programmkörper implementieren

4. Testen

Verstehen, was der Zweck des Programms ist: Berechnung der Fläche eines Rings:

Berechnung der Fläche eines Ringes mit einem äußeren Radius ‘outer’ und einem inneren Radius ‘inner’.
Berechnen kann man das durch die Fläche des Kreises mit Radius
‘outer’ minus der Fläche des Kreises mit Radius ‘inner’

>“If you can't write it down in English, you can't code it.“
><cite> Peter Halpern</cite>




### 1 Verstehen, was der Zweck des Programms ist
1. Vergabe eines sinnvollen Namens
2. Definition eines Vertrags.
3. Welche Daten werden konsumiert und produziert?
4. Formulierung einer kurzen Beschreibung des Sinns des
Programms
5. Hinzufügen des Programmkopfes
Beispiel:
````
;; area-of-ring :: number number -> number

;; Berechnet die Flaeche eines Rings

;; mit Radius "outer", dessen
;; Loch den Radius "inner" hat

(define (area-of-ring outer inner) ... )
````
### 2. Programmbeispiele ausdenken

Hilft die Ein-/Ausgaberelation zu charakterisieren.

Es ist oft einfacher, Abstraktes anhand von Beispielen zu verstehen. Beispiele helfen, den Berechnungsprozess eines Programms zu verstehen und logische Fehler zu entdecken.
In unserem Beispiel:
```
 ;; area-of-ring :: number number -> number

 ;; Berechnet die Flaeche eines Rings...

 ;; dessen Loch den Radius "inner" hat

 ;; Beispiel: (area-of-ring 5 2) ergibt 65.94

(define (area-of-ring outer inner) ... )
````



### 3. Den Programmkörper implementieren.

Ersetzung des “...” Platzhalters mit einem Ausdruck.
Ist die Eingabe-Ausgabe Relation eine mathematische Formel, können wir diese meist direkt übersetzen.
Bei einer informellen Beschreibung müssen wir uns den
Berechnungsprozess klarmachen.
Die Beispiele aus Schritt 2 können helfen.
In unserem Beispiel:
````
;; area-of-ring :: number number -> number
;; Berechnet die Flaeche eines Rings...
;; dessen Loch den Radius "inner" hat

;; Beispiel: (area-of-ring 5 2) ergibt 65.94
(define (area-of-ring outer inner)
(- (area-of-disk outer) (area-of-disk inner)))
````

### 4. **_Testen_**
Nutzen Sie die eingebauten Prozeduren der HtDP-TL!
````
( **check-expect** _test expected_ )
````
Vergleicht den “test"-Wert exakt mit dem "expected"-Wert.
Für Gleitkommazahlen problematisch, da Ergebnis nicht unbedingt exakt ist (markiert durch „#i“ vor dem Wert) 
Beispiel: 
````
(check-expect(* 2 2) 4)
````
````
 **(check-within** _testexpected delta_ )
 ````
Prüfung, ob der Testwert(meist Gleitkommazahl) korrekt ist mit Abweichung delta, etwa delta= 0.0001.
Beispiel: 
````
(check-within (area-of-ring 5 2) 65.9 0.5)
````
````
( **check-error** _testmessage_ )`
````
Prüft, ob der Aufruf die erwartete Fehlermeldung liefert
Fehler in Funktion _func_ durch ( **error 'function "message"** ) auslösen
Fehlgeschlagene Tests werden in einem separaten Fenster angezeigt.

“Testing can show the presence of bugs,but not their absence.”
Edsger W. Dijkstra
“Beware of bugs in the above code; I have only proved it correct, not tried it“ Donald E. Knuth



## Hilfsprozeduren 
Wann/wofür sollte man Hilfsprozeduren verwenden?

Beispiel: Schreiben Sie ein Programm, das den Profit eines Kinobesitzers in Abhängigkeit vom Ticketpreis berechnet.

- _Bei 5€ pro Ticket kommen 120 Leute._
- _Pro 0,10€ Rabatt kommen 15 Leute mehr._
- _Jede Aufführung kostet 180€._
- _Jeder Teilnehmer kostet 0,04€._


### Hilfsprozeduren: Schlechtes Design
````
;; How NOT to design a program

(define (profit price)

(- (* (+ 120

(* (/ 15 .10)

(- 5.00 price)))

price)
(+ 180
(* .04
(+ 120
(* (/ 15 .10)
(- 5.00 price)))))))
````


### Hilfsprozeduren: Gutes Design

````
;; How to design a program
(define (profit ticket-price)
(- (revenue ticket-price)
(cost ticket-price)))

(define (revenue ticket-price)
(* (attendees ticket-price) ticket-price))

(define (cost ticket-price)
(+ 180
(* .04 (attendees ticket-price))))

(define (attendees ticket-price)
(+ 120
(* (/ 15 .10) (- 5.00 ticket-price))))
````
### Daumenregel für Hilfsprozeduren

Definieren Sie Hilfsprozeduren für jede Abhängigkeit zwischen Quantitäten der Problembeschreibung oder Quantitäten, die bei den Beispielberechnungen entdeckt wurden.


### Prozeduren als Black-Box-Abstraktionen

Abstraktion dient dazu, Komplexität zu verstecken.

Details werden versteckt, die nicht zum Verständnis des Sachverhalts beitragen (abhängig vom Betrachter)


In der Vorlesung werden wir mehrere fundamentale Arten der Abstraktion kennen lernen.

Eine prozedurale Abstraktion ist eine davon: area-of-ring berechnet die Fläche eines Rings Der Benutzer muss sich nicht um die Details von area-of-ring kümmern

Eingaben Ausgabe.

Wir wissen, was es tut, aber nicht, wie es etwas tut.

Schwarze Kiste (black-box) Abstraktion.
Ein Berechnungsproblem wird oft in natürliche, kleinere Teilprobleme aufgeteilt.


Beispiel: Ringfläche à Zweifache Berechnung einer Kreisfläche

Für Teilprobleme werden Prozeduren geschrieben area-of-disk,... primitive Prozeduren 


Die Prozedur attendees kann als eine „black box“ betrachtet werden.

Sie soll die Anzahl der Teilnehmer berechnen.
Wir wollen nicht wissen, wie sie die Berechnung durchführt.
Diese Details können vernachlässigt werden.

attendees ist eine prozedurale Abstraktion für revenue/cost.

profit, revenue cost, attendees

Eine benutzerdefinierte Prozedur wird über den Namen aufgerufen, genauso wie die primitiven Prozeduren.

Wie die Prozedur arbeitet, bleibt versteckt.

Auf diesem Abstraktionsniveau ist jede Prozedur, die Quadrate berechnet, so gut wie jede andere.
````
(define (square x) (* x x))
(define (square x) (* (* x 10) (/ x 10)))
area-of-ring
area-of-circle
square
````
### Konstantendefinitionen
Richtlinie für Variablendefinitionen:

Bessere Lesbarkeit
Bessere Wartbarkeit
Bei Änderungen muss nur an einer Stelle etwas geändert werden
In unserem Beispiel:
(define PI 3.14)
Benötigt man eine bessere Approximation, ist nur eine Änderung erforderlich
(define PI 3.14159)
```
Taucht eine Konstante in einem Programm haüfig auf, sollten wir ihr einen Namen geben.




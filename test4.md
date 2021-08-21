---
question: Warum is es wichtig zu testen ?
title: Test12312312
---
"Projekt Dojo" geht bei Tesla in die heiße Phase. Der Autohersteller hat komplett eigene KI-Prozessoren entworfen, die in den nächsten Jahren die zugekaufte Hardware ablösen sollen – allen voran Nvidias GPU-Beschleuniger A100. Das Ziel: Hardware, die genau das kann, was man braucht, und das sehr gut ohne jeglichen Ballast. Dazu setzt Tesla auf moderne 7-Nanometer-Strukturbreiten, ausgeklügelte Packaging-Technik und einen ungeahnt hohen Grad an Integration.

Die Basis bildet ein 645 mm² großer Chip namens D1 mit etwa 50 Milliarden Transistoren. Darin sitzen 354 Cluster bestehend aus jeweils einem einzelnen CPU-Kern, begleitet von einer vierfach weiten Skalar- und einer doppelt weiten Vektoreinheit, die nur eine Aufgabe hat: haufenweise Matrizen berechnen. Vierfaches Simultaneous Multithreading (SMT, vier Threads pro CPU-Kern) soll die Auslastung maximieren.

Die Vorstellung erfolgte im Rahmen des Tesla AI Day (im Video ab 1:45:35).

Massig Speicher und viel Rechenleistung
Dem Ganzen stehen 1,25 MByte SRAM pro Cluster und integrierte Switches zur Seite. Das ergibt pro CPU 354 Rechenkerne, 1416 Threads, 442,5 MByte flottes SRAM und 362 TeraFlops Rechenleistung im KI-Datenformat BF16 bei einer Leistungsaufnahme von 400 Watt. Alternativ beherrscht der D1 das neue Datenformat CFP8 (configurable Floating Point), FP32, INT32, INT16 und INT8. Jedes Cluster überträgt Daten mit 512 GByte/s an seine Nachbarn – im gesamten Chip laufen pro Sekunde 10 TByte an Daten.
Tesla will in einem künftigen Rechenzentrum 120 Training Tiles mit insgesamt 3000 D1-Prozessoren unterbringen, was eine BF16- beziehungsweise CFP8-Rechenleistung von 1,1 ExaFlops ergibt. Auf dem Papier ist das etwas weniger als das derzeitige Tesla-Rechenzentrum mit Nvidias A100-Karten, aufgrund der Spezialisierung will man neuronale Netze so trotzdem schneller trainieren. Tesla nutzt die Ergebnisse etwa für den eigenen Fahrassistenten. Erste Training Tiles laufen derzeit mit Taktfrequenzen von 2,0 GHz im Labor.
Tesla will in einem künftigen Rechenzentrum 120 Training Tiles mit insgesamt 3000 D1-Prozessoren unterbringen, was eine BF16- beziehungsweise CFP8-Rechenleistung von 1,1 ExaFlops ergibt. Auf dem Papier ist das etwas weniger als das derzeitige Tesla-Rechenzentrum mit Nvidias A100-Karten, aufgrund der Spezialisierung will man neuronale Netze so trotzdem schneller trainieren. Tesla nutzt die Ergebnisse etwa für den eigenen Fahrassistenten. Erste Training Tiles laufen derzeit mit Taktfrequenzen von 2,0 GHz im Labor.
Cerebras verbaut die WSE-2 in den CS-2-Systemen im 15U-Format. Diese sind wassergekühlt und mit zwölf (9+3) redundant ausgelegten Netzteilen versehen. Laut Cerebras liegt die maximale Leistungsaufnahme eines solchen Systems bei 23 Kilowatt, wovon ein Großteil auf die einzelne Wafer Scale Engine 2 entfällt. Zwei CS-2 passen in ein 42U-Rack, drei in ein höheres 46U-Rack.

Um die Systeme mit der restlichen Infrastruktur zu verbinden, sind zwölf 100-GBit/s-Anschlüsse vorhanden. Die Software-Plattform für die WSE-2 besteht aus dem Cerebras Graph Compiler (CGC), welche zuvor per Machine-Learning-Frameworks wie Pytorch und Tensorflow erstellte Modelle konvertiert, damit diese auf den CS-2 laufen. Hinzu kommen unter anderem APIs, Kernels und Debbuging-Tools für die Entwicklung.

Cerebras will die ersten CS-2 im dritten Quartal 2021 ausliefern, der Preis liegt bei mehreren Millionen US-Dollar. Zu den bisherigen Kunden des CS-1 gehören das Pittsburgh Supercomputing Center für den Neocortex-Supercomputer und das Lawrence Livermore National Laboratory für den Lassen-Supercomputer.

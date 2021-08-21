---
question: Warum is es wichtig zu testen ?
title: Test12312312
---
"Projekt Dojo" geht bei Tesla in die heiße Phase. Der Autohersteller hat komplett eigene KI-Prozessoren entworfen, die in den nächsten Jahren die zugekaufte Hardware ablösen sollen – allen voran Nvidias GPU-Beschleuniger A100. Das Ziel: Hardware, die genau das kann, was man braucht, und das sehr gut ohne jeglichen Ballast. Dazu setzt Tesla auf moderne 7-Nanometer-Strukturbreiten, ausgeklügelte Packaging-Technik und einen ungeahnt hohen Grad an Integration.

Die Basis bildet ein 645 mm² großer Chip namens D1 mit etwa 50 Milliarden Transistoren. Darin sitzen 354 Cluster bestehend aus jeweils einem einzelnen CPU-Kern, begleitet von einer vierfach weiten Skalar- und einer doppelt weiten Vektoreinheit, die nur eine Aufgabe hat: haufenweise Matrizen berechnen. Vierfaches Simultaneous Multithreading (SMT, vier Threads pro CPU-Kern) soll die Auslastung maximieren.

Die Vorstellung erfolgte im Rahmen des Tesla AI Day (im Video ab 1:45:35).

Massig Speicher und viel Rechenleistung
Dem Ganzen stehen 1,25 MByte SRAM pro Cluster und integrierte Switches zur Seite. Das ergibt pro CPU 354 Rechenkerne, 1416 Threads, 442,5 MByte flottes SRAM und 362 TeraFlops Rechenleistung im KI-Datenformat BF16 bei einer Leistungsaufnahme von 400 Watt. Alternativ beherrscht der D1 das neue Datenformat CFP8 (configurable Floating Point), FP32, INT32, INT16 und INT8. Jedes Cluster überträgt Daten mit 512 GByte/s an seine Nachbarn – im gesamten Chip laufen pro Sekunde 10 TByte an Daten.

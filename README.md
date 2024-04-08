---
title: SEW Maturafragen
subtitle: Schuljahr 2023/24
---



# Programmierparadigmen



## Vererbung
[Ausarbeitung](thema1/vererbung.md)


## Polymorphismus
[Ausarbeitung](thema1/polymorph.md)



## Delegates
[Ausarbeitung](thema1/delegates.md)


## Design Pattern
[Ausarbeitung](thema1/design-pattern.md)



# Suchen und Sortieren

## Binäre Suche
[Ausarbeitung](thema2/binary-search.md)



## Binärbaum
[Ausarbeitung](thema2/binary-tree.md)



## Hashing
[Ausarbeitung](thema2/hashing.md)



## Klassische Sortierverfahren
[Ausarbeitung](thema2/klassische-sortierverfahren.md)



# Algorithmen und Datenstrukturen



## Mergesort

Erkläre Funktionsweise und Performance Eigenschaften des Sortierverfahrens **Mergesort**.



## Quicksort

Erkläre Funktionsweise und Performance Eigenschaften des Sortierverfahrens **Quicksort**.



## Verkettete Liste

Erkläre das Funktionsprinzip einer einfach verketteten Liste. Wie werden grundlegende Operationen (Suchen, Einfügen und Löschen) implementiert? Was sind die Performance Eigenschaften?



## Dijkstra Shortest Path

Erkläre den Anwendungsfall und die Funktionsweise des Dijkstra Shortest Path Algorithmus. Verwende ein Beispiel.



# Ausgewählte Themen der Software-Entwicklung



## Dijkstra Shunting-yard Algorithmus

Ein arithmetischer Ausdruck liegt als paarweise geklammerter Ausdruck in einem String vor. Der Ausdruck enthält die 4 Grundrechenarten und einstellige Zahlen. Beispiel:

```
((1+2)*(7-(2*3)))
```

Der Ausdruck soll berechnet werden und das Ergebnis als int Variable vorliegen.

- Erkläre das Verhalten eines Stacks
- Erkläre die Lösungsidee (Dijkstra Algorithmus) für die Auswertung des Ausdrucks mit Hilfe von 2 Stacks
- Zeige und erkläre die Implementierung für einen der beiden Stacks
- Implementiere den Dijkstra Algorithmus



## Rekursion allgemein

Als Dreieckszahl bezeichnet man die Summe der ersten `n` natürlichen Zahlen.

- Wieso nennt man dies eine Dreieckszahl?
- Implementiere rekursiv und iterativ.
- Erkläre/visualisiere den Ablauf der rekursiven Methode für `sum(3)`.
- Bewerte beide Implementierungen hinsichtlich Laufzeit und Speicherverbrauch.
- Erläutere Vor- und Nachteile von Rekursion sowie mögliche Anwendungsfälle.



## Bäume und Rekursion

Diverse Operationen auf binären Suchbäumen lassen sich nicht iterativ implementieren. Dafür ist z.B. Rekursion geeignet.

- Erkläre warum ein Baum eigentlich eine rekursive Datenstruktur ist.
- Wie ist die Anzahl der Knoten eines Baumes zu ermitteln? Erkläre an diesem Beispiel das rekursive Prinzip.
- Was ist mit pre/in/post-Order gemeint und wie ist dies zu implementieren?
- Wie ist die Höhe eines Baumes zu ermitteln?



## Anzahl unterschiedlicher Wörter

Gegeben ist ein Array aus Wörtern:

```c#
string w[]={"der","das","der","die",...};
```

Aufgaben:

- Implementiere mit Hilfe von `List` ein Programm das jenes Wort findet das in diesem Array am **häufigsten** vorkommt.
- Diskutiere Möglichkeiten um das Programm zu beschleunigen
  - Welche Datenstrukturen wären besser geeignet?
  - Welche C# Collection würde die Aufgabenstellung mit einer besseren Performance erledigen – zeige die Implementierung.



# Software Systeme

## C# Collections

Erkläre die C# Collections `List`, `Dictionary` und `Set`. Wie werden diese angewendet? Wie werden diese intern implementiert sein? Welche Performance Eigenschaften ergeben sich daraus?



## Dynamisches Array

Angelehnt an die Funktionalität von `List` soll eine Klasse `DynArray` für ein dynamisches Array aus `int` erstellt werden. Wähle einen Algorithmus der die Anzahl der notwendigen `new` Operationen minimiert.

- Erkläre das Prinzip eines dynamischen Arrays.
- Vergleiche die Performance mit einer verketteten Liste.
- Implementiere die Klasse und die Methoden:
  - `add(int n)` – Einfügen am Ende
  - `add(int i, int n)` – Einfügen an Index i. Alle Elemente ab i werden verschoben.
  - `remove(int i)` – Entfernt das Element an der Stelle i. Alle Element nach i rücken um 1 auf.



## CSV Daten in Objekte einlesen (Bearbeiten, Sortieren)

Gegeben ist eine CSV Datei die nach folgendem Schema aufgebaut ist:

```
 first;last;birth
 Allen;Harrington;22.10.1997
 Megan;Lecuyer;01.12.1996
 Eva;Paul;07.08.1997
 Curtis;Leggett;26.01.1997
```

Aufgabenstellung:

- Erkläre wie diese Daten in einem Programm eingelesen und gespeichert werden könnten. Verwende eine sinnvolle und übersichtliche Zerlegung in Objekte/Klassen.
- Zeige die Implementierung.
- Es soll die älteste Person in dieser Liste gefunden werden. Wie ist dies zu realisieren?
- Zeige die Implementierung.


\pagebreak
## JSON

Erkläre das JSON Datenformat. Wie können JSON Daten in einem C# Programm eingelesen werden?

Über den Google geocode Webservice soll ermittelt werden in welchem Land sich eine Stadt befindet. Der JSON Response sieht wie folgt aus. Implementiere ein C# Programm das die Aufgabenstellung löst.

```
{
   "results" : [
      {
         "address_components" : [
            {
               "long_name" : "Toronto",
               "short_name" : "Toronto",
               "types" : [ "locality", "political" ]
            },
            {
               "long_name" : "Toronto Division",
               "short_name" : "Toronto Division",
               "types" : [ "administrative_area_level_2", "political" ]
            },
            {
               "long_name" : "Ontario",
               "short_name" : "ON",
               "types" : [ "administrative_area_level_1", "political" ]
            },
            {
               "long_name" : "Canada",
               "short_name" : "CA",
               "types" : [ "country", "political" ]
            }
         ],
         "formatted_address" : "Toronto, ON, Canada",
         "geometry" : {
            "location" : {
               "lat" : 46.452469,
               "lng" : -63.379967
            },
         }
      },
   ],
   "status" : "OK"
}
```

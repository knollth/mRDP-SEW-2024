# Vererbung

In der objektorientierten Programmierung (OOP) ist die Vererbung ein Konzept, das es ermöglicht, Eigenschaften und Verhaltensweisen einer Klasse auf eine andere Klasse zu übertragen. Das bedeutet, dass eine abgeleitete Klasse (auch Unterklasse oder Subklasse genannt) alle Eigenschaften und Methoden der Basisklasse (auch Oberklasse oder Superklasse genannt) übernimmt und gleichzeitig eigene spezifische Eigenschaften und Methoden hinzufügen kann. Dies fördert die Wiederverwendung von Code und erleichtert die Erstellung und Wartung von Software.

Nehmen wir an, wir möchten ein Programm zur Modellierung von Fahrzeugen erstellen. Wir haben eine Basisklasse namens "Fahrzeug", die allgemeine Eigenschaften wie "Geschwindigkeit" und Methoden wie "Beschleunigen" und "Bremsen" enthält. Dann möchten wir spezifische Arten von Fahrzeugen modellieren, wie Autos und Motorräder. Anstatt alle Eigenschaften und Methoden für jedes spezifische Fahrzeug wiederholt zu definieren, können wir die Vererbung verwenden.


**Beispiel:**
```csharp
using System;

/Basisklasse Fahrzeug
class Fahrzeug
{
    public int Geschwindigkeit { get; set; }

    public void Beschleunigen(int zusätzlicheGeschwindigkeit)
    {
        Geschwindigkeit += zusätzlicheGeschwindigkeit;
        Console.WriteLine("Das Fahrzeug beschleunigt auf " + Geschwindigkeit + " km/h.");
    }

    public void Bremsen(int bremskraft)
    {
        Geschwindigkeit -= bremskraft;
        Console.WriteLine("Das Fahrzeug bremst auf " + Geschwindigkeit + " km/h.");
    }
}

// Abgeleitete Klasse Auto
class Auto : Fahrzeug
{
    public string Marke { get; set; }

    public void Hupe()
    {
        Console.WriteLine("Das Auto hupt!");
    }
}

// Abgeleitete Klasse Motorrad
class Motorrad : Fahrzeug
{
    public string Typ { get; set; }

    public void Wheelie()
    {
        Console.WriteLine("Das Motorrad macht einen Wheelie!");
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Erzeugen eines Autos
        Auto meinAuto = new Auto();
        meinAuto.Marke = "BMW";
        meinAuto.Beschleunigen(50);
        meinAuto.Hupe();

        // Erzeugen eines Motorrads
        Motorrad meinMotorrad = new Motorrad();
        meinMotorrad.Typ = "Sport";
        meinMotorrad.Beschleunigen(80);
        meinMotorrad.Wheelie();
    }
}
```

In diesem Beispiel erbt die Klasse "Auto" von der Basisklasse "Fahrzeug". Dadurch erbt sie die Eigenschaft "Geschwindigkeit" und die Methoden "Beschleunigen" und "Bremsen". Die Klasse "Motorrad" erbt auch von "Fahrzeug" und erhält somit ebenfalls die allgemeinen Eigenschaften und Methoden. Durch Vererbung können wir jedoch auch spezifische Eigenschaften und Methoden für jedes spezialisierte Fahrzeug hinzufügen, wie die Marke für das Auto oder den Typ für das Motorrad.

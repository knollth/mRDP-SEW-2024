# Polymorphismus

Erkläre das OOP Konzept des **Polymorphismus** anhand eines Beispiels.


Polymorphismus ist ein zentrales Konzept der objektorientierten Programmierung (OOP). Der Begriff "Polymorphismus" bedeutet „viele Formen“ und ermöglicht es Objekten, Methoden auf unterschiedliche, jedoch spezifische Weisen zu implementieren, basierend auf der Klasse oder dem Kontext ihrer Objekte.

**Zwei Arten von Polymorphismus:**

1. Dynamischer Polymorphismus (Überschreiben):
Das Überschreiben von Methoden (Method Overriding) bezieht sich auf die Fähigkeit einer abgeleiteten Klasse, eine Methode der Basisklasse zu ersetzen, indem sie eine Methode mit derselben Signatur (Name und Parameter) verwendet. Dies wird zur Laufzeit aufgelöst und ist der Hauptfokus, wenn wir von Polymorphismus in OOP sprechen.



2. Statischer Polymorphismus, auch als Methodenüberladung bekannt, tritt auf, wenn mehrere Methoden in derselben Klasse denselben Namen haben, sich jedoch in der Anzahl oder den Typen ihrer Parameter unterscheiden. Dies ermöglicht es, dass die Methode basierend auf den übergebenen Argumenten während der Kompilierzeit ausgewählt wird. 

```csharp
using System;

public abstract class Mitarbeiter
{
    // Abstrakte Methode, die jede abgeleitete Klasse implementieren muss
    public abstract void Arbeiten();
}

public class Entwickler : Mitarbeiter
{
    public override void Arbeiten()
    {
        Console.WriteLine("Der Entwickler schreibt Code.");
    }
}

public class Manager : Mitarbeiter
{
    public override void Arbeiten()
    {
        Console.WriteLine("Der Manager plant und überwacht Projekte.");
    }
}

public class Praktikant : Mitarbeiter
{
    public override void Arbeiten()
    {
        Console.WriteLine("Der Praktikant unterstützt bei verschiedenen Aufgaben.");
    }
}

public class Program
{
    public static void ArbeitsTag(Mitarbeiter mitarbeiter)
    {
        mitarbeiter.Arbeiten();
    }

    public static void Main()
    {
        Mitarbeiter entwickler = new Entwickler();
        Mitarbeiter manager = new Manager();
        Mitarbeiter praktikant = new Praktikant();

        // Demonstration von Polymorphismus
        ArbeitsTag(entwickler);   
        ArbeitsTag(manager);      
        ArbeitsTag(praktikant);  
    }
}

```
Eine abstrakten Basisklasse `Mitarbeiter`, von der drei spezifische Klassen (`Entwickler`, `Manager`, `Praktikant`) erben. 
Im Hauptprogramm  werden Instanzen dieser Klassen erstellt und die Methode `MitarbeiterArbeitstag()` wird aufgerufen, um die `Arbeiten()`-Methode für jede dieser Instanzen auszuführen. Dies zeigt, wie unterschiedlich die Implementierungen der Methode `Arbeiten()` sein können, obwohl sie von derselben abstrakten Methode in der Basisklasse abgeleitet sind. 



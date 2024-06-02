# Vererbung

In der objektorientierten Programmierung (OOP) ist die Vererbung ein Konzept, das es ermöglicht, Eigenschaften und Verhaltensweisen einer Klasse auf eine andere Klasse zu übertragen. Das bedeutet, dass eine abgeleitete Klasse (auch Unterklasse oder Subklasse genannt) alle Eigenschaften und Methoden der Basisklasse (auch Oberklasse oder Superklasse genannt) übernimmt und gleichzeitig eigene spezifische Eigenschaften und Methoden hinzufügen kann. Dies fördert die Wiederverwendung von Code und erleichtert die Erstellung und Wartung von Software.

Nehmen wir an, wir möchten ein Programm zur Modellierung von Fahrzeugen erstellen. Wir haben eine Basisklasse namens "Fahrzeug", die allgemeine Eigenschaften wie "Geschwindigkeit" und Methoden wie "Beschleunigen" und "Bremsen" enthält. Dann möchten wir spezifische Arten von Fahrzeugen modellieren, wie Autos und Motorräder. Anstatt alle Eigenschaften und Methoden für jedes spezifische Fahrzeug wiederholt zu definieren, können wir die Vererbung verwenden.


**Beispiel:**
```csharp
using System;

//Basisklasse Fahrzeug
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



In C# gibt es wesentliche Unterschiede zwischen der Vererbung von Interfaces und der Vererbung von Klassen. Hier sind die Hauptunterschiede:

### 1. Syntax und Definition

#### Vererbung von Klassen

Eine Klasse kann nur von einer anderen Klasse erben (Einzelvererbung). Die Basisklasse liefert Implementierungen für ihre Methoden, und die abgeleitete Klasse kann diese Methoden überschreiben oder neue Methoden hinzufügen.

```csharp
public class BaseClass
{
    public void BaseMethod()
    {
        Console.WriteLine("Base method");
    }
}

public class DerivedClass : BaseClass
{
    public void DerivedMethod()
    {
        Console.WriteLine("Derived method");
    }
}
```

#### Vererbung von Interfaces

Eine Klasse oder ein anderes Interface kann von mehreren Interfaces erben (Mehrfachvererbung). Interfaces liefern keine Implementierungen, sondern nur die Methodensignaturen, die die Klassen, die sie implementieren, ausfüllen müssen.

```csharp
public interface IFirstInterface
{
    void FirstMethod();
}

public interface ISecondInterface
{
    void SecondMethod();
}

public class ImplementingClass : IFirstInterface, ISecondInterface
{
    public void FirstMethod()
    {
        Console.WriteLine("First method implementation");
    }

    public void SecondMethod()
    {
        Console.WriteLine("Second method implementation");
    }
}
```

### 2. Implementierung

#### Vererbung von Klassen

Die abgeleitete Klasse erbt die Implementierungen der Basisklasse und kann diese überschreiben.

```csharp
public class BaseClass
{
    public virtual void BaseMethod()
    {
        Console.WriteLine("Base method");
    }
}

public class DerivedClass : BaseClass
{
    public override void BaseMethod()
    {
        Console.WriteLine("Overridden base method");
    }
}
```

#### Vererbung von Interfaces

Eine Klasse, die ein Interface implementiert, muss alle Methoden des Interfaces implementieren. Interfaces bieten keine Implementierung.

```csharp
public interface IMyInterface
{
    void MyMethod();
}

public class ImplementingClass : IMyInterface
{
    public void MyMethod()
    {
        Console.WriteLine("Method implementation");
    }
}
```

### 3. Mehrfachvererbung

#### Vererbung von Klassen

C# unterstützt keine Mehrfachvererbung von Klassen, d.h., eine Klasse kann nur von einer anderen Klasse erben.

```csharp
// Nicht erlaubt:
public class ClassA { }
public class ClassB { }
public class DerivedClass : ClassA, ClassB { } // Fehler
```

#### Vererbung von Interfaces

C# unterstützt Mehrfachvererbung von Interfaces, d.h., eine Klasse kann mehrere Interfaces implementieren.

```csharp
public interface IFirstInterface
{
    void FirstMethod();
}

public interface ISecondInterface
{
    void SecondMethod();
}

public class ImplementingClass : IFirstInterface, ISecondInterface
{
    public void FirstMethod()
    {
        Console.WriteLine("First method implementation");
    }

    public void SecondMethod()
    {
        Console.WriteLine("Second method implementation");
    }
}
```

### 4. Verwendung

#### Vererbung von Klassen

Eine abgeleitete Klasse kann die Methoden der Basisklasse verwenden oder überschreiben. Es gibt eine Implementierung in der Basisklasse, die die abgeleitete Klasse erben kann.

```csharp
public class BaseClass
{
    public virtual void BaseMethod()
    {
        Console.WriteLine("Base method");
    }
}

public class DerivedClass : BaseClass
{
    public override void BaseMethod()
    {
        Console.WriteLine("Overridden base method");
    }
}
```

#### Vererbung von Interfaces

Eine Klasse, die ein Interface implementiert, muss alle Methoden des Interfaces implementieren. Es gibt keine Standardimplementierung im Interface.

```csharp
public interface IMyInterface
{
    void MyMethod();
}

public class ImplementingClass : IMyInterface
{
    public void MyMethod()
    {
        Console.WriteLine("Method implementation");
    }
}
```

### Zusammenfassung

- **Vererbung von Klassen**: Unterstützt Einzelvererbung, ermöglicht es der abgeleiteten Klasse, Implementierungen der Basisklasse zu erben und zu überschreiben.
- **Vererbung von Interfaces**: Unterstützt Mehrfachvererbung, zwingt die implementierende Klasse, alle Methoden der Interfaces zu implementieren, bietet jedoch keine Implementierung.

Beide Mechanismen haben ihre eigenen Anwendungsfälle und werden oft in Kombination verwendet, um flexible und wiederverwendbare Code-Strukturen zu erstellen.


In C# gibt es verschiedene Schlüsselwörter, die bei der Vererbung verwendet werden, um den Zugriff und das Verhalten von Klassenmitgliedern zu steuern. Hier sind die Hauptschlüsselwörter und ihre Bedeutungen:

### 1. `public`
- **Bedeutung**: Die Mitglieder (Methoden, Eigenschaften, Felder) sind für alle Klassen zugänglich, die Zugriff auf die Klasse haben.
- **Verwendung**: Wenn Sie möchten, dass die Mitglieder einer Klasse überall sichtbar sind, verwenden Sie `public`.

```csharp
public class BaseClass
{
    public void PublicMethod()
    {
        Console.WriteLine("Public method");
    }
}
```

### 2. `private`
- **Bedeutung**: Die Mitglieder sind nur innerhalb der Klasse zugänglich, in der sie definiert sind. Sie sind für abgeleitete Klassen oder andere Klassen nicht sichtbar.
- **Verwendung**: Wenn Sie die Mitglieder einer Klasse vor dem Zugriff von außen schützen möchten, verwenden Sie `private`.

```csharp
public class BaseClass
{
    private void PrivateMethod()
    {
        Console.WriteLine("Private method");
    }
}
```

### 3. `protected`
- **Bedeutung**: Die Mitglieder sind innerhalb der Klasse, in der sie definiert sind, und in allen abgeleiteten Klassen zugänglich.
- **Verwendung**: Wenn Sie möchten, dass die Mitglieder einer Klasse in abgeleiteten Klassen zugänglich sind, aber nicht von außen, verwenden Sie `protected`.

```csharp
public class BaseClass
{
    protected void ProtectedMethod()
    {
        Console.WriteLine("Protected method");
    }
}

public class DerivedClass : BaseClass
{
    public void CallProtectedMethod()
    {
        ProtectedMethod();
    }
}
```

### 4. `internal`
- **Bedeutung**: Die Mitglieder sind innerhalb derselben Assembly (Projekt) zugänglich, aber nicht außerhalb davon.
- **Verwendung**: Wenn Sie die Mitglieder einer Klasse innerhalb derselben Assembly zugänglich machen möchten, aber nicht für andere Assemblies, verwenden Sie `internal`.

```csharp
internal class BaseClass
{
    internal void InternalMethod()
    {
        Console.WriteLine("Internal method");
    }
}
```

### 5. `protected internal`
- **Bedeutung**: Die Mitglieder sind entweder innerhalb derselben Assembly oder in abgeleiteten Klassen zugänglich.
- **Verwendung**: Wenn Sie die Mitglieder einer Klasse sowohl innerhalb derselben Assembly als auch in abgeleiteten Klassen zugänglich machen möchten, verwenden Sie `protected internal`.

```csharp
public class BaseClass
{
    protected internal void ProtectedInternalMethod()
    {
        Console.WriteLine("Protected internal method");
    }
}
```

### 6. `private protected`
- **Bedeutung**: Die Mitglieder sind nur innerhalb der Klasse, in der sie definiert sind, und in abgeleiteten Klassen innerhalb derselben Assembly zugänglich.
- **Verwendung**: Wenn Sie die Mitglieder einer Klasse nur in abgeleiteten Klassen innerhalb derselben Assembly zugänglich machen möchten, verwenden Sie `private protected`.

```csharp
public class BaseClass
{
    private protected void PrivateProtectedMethod()
    {
        Console.WriteLine("Private protected method");
    }
}
```

### 7. `virtual`
- **Bedeutung**: Markiert eine Methode oder Eigenschaft in einer Basisklasse, die in einer abgeleiteten Klasse überschrieben werden kann.
- **Verwendung**: Wenn Sie möchten, dass eine Methode in einer Basisklasse in abgeleiteten Klassen überschrieben werden kann, verwenden Sie `virtual`.

```csharp
public class BaseClass
{
    public virtual void VirtualMethod()
    {
        Console.WriteLine("Virtual method");
    }
}
```

### 8. `override`
- **Bedeutung**: Markiert eine Methode in einer abgeleiteten Klasse, die eine `virtual` Methode in der Basisklasse überschreibt.
- **Verwendung**: Wenn Sie eine `virtual` Methode in einer abgeleiteten Klasse überschreiben möchten, verwenden Sie `override`.

```csharp
public class DerivedClass : BaseClass
{
    public override void VirtualMethod()
    {
        Console.WriteLine("Overridden method");
    }
}
```

### 9. `abstract`
- **Bedeutung**: Markiert eine Methode in einer Basisklasse, die keine Implementierung hat und in abgeleiteten Klassen implementiert werden muss. Auch die Klasse selbst kann als `abstract` markiert werden, was bedeutet, dass sie nicht instanziiert werden kann.
- **Verwendung**: Wenn Sie möchten, dass eine Methode in abgeleiteten Klassen zwingend implementiert wird, verwenden Sie `abstract`.

```csharp
public abstract class BaseClass
{
    public abstract void AbstractMethod();
}

public class DerivedClass : BaseClass
{
    public override void AbstractMethod()
    {
        Console.WriteLine("Implemented abstract method");
    }
}
```

### Zusammenfassung

- **`public`**: Vollständig zugänglich.
- **`private`**: Nur innerhalb der eigenen Klasse zugänglich.
- **`protected`**: Innerhalb der eigenen Klasse und abgeleiteter Klassen zugänglich.
- **`internal`**: Innerhalb derselben Assembly zugänglich.
- **`protected internal`**: Innerhalb derselben Assembly oder abgeleiteter Klassen zugänglich.
- **`private protected`**: Innerhalb derselben Assembly und nur in abgeleiteten Klassen zugänglich.
- **`virtual`**: Kann in abgeleiteten Klassen überschrieben werden.
- **`override`**: Überschreibt eine `virtual` Methode in einer Basisklasse.
- **`abstract`**: Muss in abgeleiteten Klassen implementiert werden.
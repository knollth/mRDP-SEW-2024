# Delegates

Delegates in C# sind spezielle Werkzeuge, mit denen Methodenreferenzen gespeichert und verwendet werden können. Sie ermöglichen es, Methoden als Parameter an andere Methoden zu übergeben oder sie in Variablen zu speichern. Dies erlaubt eine flexible und dynamische Code-Struktur, die verschiedene Aktionen je nach Bedarf ausführen kann

 **Delegate für mathematische Operationen:**

Es wird ein Delegat MathOperation definiert, der eine Methode repräsentiert, die zwei Ganzzahlen als Parameter annimmt und eine Ganzzahl zurückgibt.

delegate int MathOperation(int a, int b);


Die Klasse Calculator enthält statische Methoden Add und Subtract, die der Signatur des Delegaten entsprechen und einfache mathematische Operationen ausführen.
```csharp
class Calculator
{
    public static int Add(int a, int b)
    {
        return a + b;
    }

    public static int Subtract(int a, int b)
    {
        return a - b;
    }
}
```
**Verwendung des Delegaten für Berechnungen:**

Im Hauptprogramm wird der Delegat MathOperation verwendet, um entweder die Add- oder Subtract-Methode auszuwählen und sie auf zwei Zahlen anzuwenden.
Durch die Zuweisung des Delegaten zu verschiedenen Methoden können verschiedene mathematische Operationen durchgeführt werden, ohne den Code ändern zu müssen.
Dieser Abschnitt zeigt, wie Delegaten verwendet werden können, um Methoden zur Laufzeit auszuwählen und auszuführen, was die Flexibilität des Codes erhöht.
```csharp
class Program
{
    static void Main(string[] args)
    {
        MathOperation operation = Calculator.Add;
        int result = operation(5, 3); // result = 8

        operation = Calculator.Subtract;
        result = operation(5, 3); // result = 2
    }
}
```

**Nun zur Anwendung von Delegates für die Implementierung einer wiederverwendbaren Methode zum Sortieren eines Arrays:**
Um eine wiederverwendbare Methode zur Sortierung eines Arrays zu implementieren, können auch hier Delegates verwendet werden. Dies geschieht, indem man einen Delegaten verwendet, der eine Vergleichslogik definiert, und dann diese Vergleichslogik an die Sortiermethode übergibt

```csharp
class Program
{
    static void Main(string[] args)
    {
        int[] numbers = { 3, 1, 4, 1, 5, 9, 2, 6 };
        Sorter.BubbleSort(numbers, (x, y) => x.CompareTo(y));

        foreach (int num in numbers)
        {
            Console.Write(num + " "); // Ausgabe: 1 1 2 3 4 5 6 9
        }
    }
}
```


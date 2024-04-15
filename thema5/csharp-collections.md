# C# Collections

Erkläre die C# Collections `List`, `Dictionary` und `Set`. Wie werden diese angewendet? Wie werden diese intern implementiert sein? Welche Performance Eigenschaften ergeben sich daraus?

Performances:

- O(n) => Laufzeit ändert sich mit der Größe der Eingabe
- O(1) => Laufzeit ist konstant, unabhängig von der Größe
- O(log n) => Laufzeit wächst logarithmisch mit der Größe der Eingabe 

### List

Eine Liste ist eine dynamische Datenstrukter in welcher Elemente vom selben Typ gespeichert werden können. Auf diese Elemente kann mithilfe eines Index zuggegriffen werden. Dynamsiche bedeutet das sie bei bedarf verkleinert oder vergrößert weren könne. Die Reihenfolge der Werte kann x-beliebig sein (sortiert od. unsortiert). Die Maximale größer einer Liste sind 2^64 Elemente.
Für die interne implementierung wird in der Regel ein dynamisches Array verwendet um die Elemente zu speichern.

Performance Eigenschaften für den Zugriff auf Elemente 
- O(n) => wenn auf Element mit zufälligem Index zugegriffen wird, 
- O(1) => wenn Elemente am Anfang oder am Ende sind  
- O(log n) => für binäre suche in sortierter Liste 
 
Performance Eigenschaften für das Entfernen oder das Einfügen von Elementen
- O(1) => wenn Elmente am Ende oder am Anfang einer Liste hinzugefügt oder entfernt werden 
- O(n) => wenn Elemente an einer beliebigen stelle eingefügt oder von einer bleibeigen Stelle entfernt werden

Performance Eigenschaften für das Suchen von Elementen
- O(n) => bei linearer Suche 
- O(log n) => für binäre Such in eienr sortierten Liste 



Listen können folgend implementiert werden:
```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main(string[] args)
    {
        List<string> name = new List<string>();

        name.Add("Marina Valenta");
        name.Add("Max Musterman");
        name.Add("Sonja Sonnenblume");

        string I1 = name[1]; 
        Console.WriteLine($"Das Element an Index 1 ist: {I1}");

        name[0] = "Hans Hauser";
        
        foreach (string item in name)
        {
            Console.WriteLine(item);
        }
    }
}

```
### Dictionary

Dictionaries sind dynamischen Datenstrukturen, welche verwendet werden um Key-Value-Paare zu speicher. Die Elemente in einem Dictionary sind ungeordnet (keine festgeleget Reihenfolge). Auf die Werte werden mithilfe des Schlüssels zugegriffen. 
- Key => wird zum identifizeiren des Wertes verwendet, eindeutig 
- Value => Daren die mit dem Key verbunden sind 

Dictionaries verwenden intern Hashtabellen um die Key-Value-Paare zu speichern.

Hashtabellen => Hashtabellen speichern Key-Value-Paare. Die Schlüssel werden mithilfe der Hashfunktion umgewandelt. Der Schlüssel wird zum Index, dies ermöglicht eineen schnellen Zugriff auf die Werte. 

Performance Eigenschaften für das Zugreifen, das Suchen, das Entfernen oder das Einfügen eines Elements
- O(1) 

  
Implementiert werden sie folgend:
```C#
using System;
using System.Collections.Generic;

class Program {
  static void Main(string[] args)
  {

      Dictionary<string, string> village = new Dictionary<string, string>();

     
      village.Add("5121", "Tarsdorf");
      village.Add("2475", "Neudorf");
      village.Add("2560", "Berndorf");

     
      string plz = "2560";
      string name = village[plz];
      Console.WriteLine($"The village name for postal code {plz} is: {name}");

      
      Console.WriteLine("Village Data:");
      foreach (KeyValuePair<string, string> kvp in village)
      {
          Console.WriteLine($"Postleitzahl: {kvp.Key}, Name: {kvp.Value}");
      }
  }
}
```
Der Integer Datentyp repräsentiert den Schlüssel, der String den Wert. 


### Set

Set ist eine ungeordnete Datenstruktur in der jeder Wert nur einmal vorkommen kann (Werte sind eindeutig). Die Elemente sind ungeordnet. 

In C# wird dafür 'HashSet' verwendet. Besonders praktisch ist es beispielsweise beim suchen von Elementen.

Intern wird Hashset entweder mit einer Hashtabelle oder einem Baum implementiert. Bei kleineren Datenmnegen wird eine Hashtabelle verwendet bei größeren eher Bäume.

Performance Eigenschaften für das Zugreifen, Suchen, das Entfernen oder das Einfügen eines Elements
- O(1) 
  
in Extremfällen => O(n)

Implementiert wird HashSet folgend:
```C#
using System;
using System.Collections.Generic;

HashSet<string> city  = new HashSet<string>();

city.add("Hamburg");
city.add("Berlin");
city.add("Wien");


if (meinHashSet.Contains("Berlin"))
{
    Console.WriteLine("Das Element ist vorhanden.");
}
else
{
    Console.WriteLine("Das Element ist nicht vorhanden.");
}

foreach (string element in meinHashSet)
{
    Console.WriteLine(element);
}
```

# List, Dictionary und Set im Vergleich 

Listen sind sehr ähnlich zu normalen Arrays. Sie werden für einfache Zwecke wie aufzählen oder zufälliges Auswählen verwendet. Außerdem eignene sich Listen gut dafür Werte an beliebigen Stellen einzufügen oder zu entfernen.

HashSet und Dictionaries sind für schnellere Vorgänge gedacht. 
HashSet speichern eine Ansammlung von eindeutigen Elementen. Sie ordnene den Werten durch eine Hasfunktion einen Schlüssel zu. Dadurch könnene Duplikate identifiziert werden. 
Dictionaries speichert Key-Value-Paare und ordnet den Wert einen eidneutigen Schlüssel zu. Ebenfalls wird eine Hashfunktion verwendet. Dictionaries eigenen sich dafür schnella uf Wert zuzugreifen. 

Grundlegend sind Dictionaries und HahSet ähnlich. Der Unterschied liegt an der Art wie die Werte gespeichert werden.
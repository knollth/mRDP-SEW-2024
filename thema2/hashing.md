# Hashing

Erkläre wie Hashing als Suchverfahren in einer Datenstruktur eingesetzt werden kann. Was sind die Performance Eigenschaften? Wie werden grundlegende Operationen (Suchen, Einfügen und Löschen) implementiert?

## Einsatz

Hashing kann dazu verwendet werden Elementen, durch die Berechnung aus ihrem key (string oder int Element), ihren index im Speicher zuzuweisen. Dadurch kann in der Theorie eine Laufzeitkomplexität von O(1) erreicht werden, dies würde jedoch unendlich viel Speicherplatz benötigen. 

Durch die Hash und Shifted Sum Funktionen werden aus Strings und Integer Elementen der Index berechnet. Im optimalfall sind diese einzigartig, es kann jedoch auch zu Kollisionen kommen.

Es werden auch zwei Klassen, HashTableEntry und HashTable erstellt. Die Klasse HashTableEntry beinhaltet den key und den zugehörigen Wert. Die Klasse HashTable beinhaltet die gesamte Hash-Tabelle als ein Array aus HashTableEntry Elementen. In der Klasse HashTable befinden sich auch die Funktionen zum Einfügen (Put) und Abrufen (Get) von Daten. Die Hash Funktion befindet sich auch in dieser Klasse.

## Performance

Die best mögliche Laufzeitkomplexität von Hashing ist O(1), dies kann jedoch nur mithilfe von unendlich viel Speicherplatz erreicht werden.
Grundsätzlich gilt: Je mehr Speicher umso mehr Performance kann durch das Verfahren gewonnen werden.

Es ist sehr schnell. Es wird nur ein Schritt bei der Suche nach dem Schlüssel benötigt. Dies ist unabhängig von der Anzahl der gespeicherten Elemente.

Offene Probleme sind: Der Speicherbedarf und Kollisionen.

Beim Speicherbedarf gibt es oft (normalerweise) das Problem, dass es mehr Sclüsselwerte gibt als verfügbaren Speicherplatz. Dadurch entstehen Kollisionen welche mit den separate chaining oder linear probing Verfahren gelöst werden können.

## Grundlegende Operationen

### Put

**Innerhalb der HashTable Klasse:**
```C#
public void Put (HashTableEntry entry) {
    if(table[Hash(HashCode(entry.getk()))] != null) {
        Console.WriteLine("false");
    }
    else {
        table[Hash(HashCode(entry.getk()))] = entry;
    }
}
```

**Im Hauptprogramm:**

```C#
HashTable namen = new HashTable(5);
    
namen.Put(new HashTableEntry("NAME", "STRAßE"));
```

Hier wird eine neue HashTable mit der Bezeichnung namen angelegt, diese soll den Namen als Schlüssel und die Straße als Wert als neues Element in den HashTable hinzufügen. 

### Get

**Innerhalb der HashTable Klasse:**
```C#
public HashTableEntry Get (string key) {
    if(table[Hash(HashCode(key))] != null) {
        return table[Hash(HashCode(key))];
    }
    else {
        return null;
    }
}
```

**Innerhalb des Hauptprogrammes:**
```C#
namen.Get("NAME")
```

Mithilfe der Get Funktion kann ein beliebiges Element durch suche nach seinem key gefunden werden.

### Remove

**Zu verwendende Library:**
```C#
using System.Collections;
```

**Im Hauptprogramm:**
```C#
namen.Remove("NAME");
```

Diese Funktion aus der Library System.Collections entfernt das Element mit dem entsprechenden Schlüssel aus der HashTable.

(Note: Ich konnte keine Lösung außer der Verwendung dieser Library finden)
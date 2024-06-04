# Cheatsheet
# C\#

### Reading Files
```c#
var sr = new StreamReader(“Filename“);
string line;

while ((line = sr.ReadLine()) != null){}
sr.Close();
```

##### Second Option
```c#
using (StreamReader reader = new StreamReader(filePath)){}
```

##### Third Option
```c#
string dataJson = File.ReadAllText(""geolacation.json);
```

### Arrays
```c#
Array.Copy(arr, index, arr, index, Anzahl)
Array.Copy(SourcArry, <- starting Index, DestArry, <-starting Index, how much should be copied)

int[] a;
a.Length // not length()
```

### List
```cs
List<string> list = new List<string>();
list.Add("string");
list.Remove("string");
int length = list.Count;
```

### Dictionary
```cs
Dictionary<string, string> dict = new Dictionary<string, string>();
dict.Add("key", "value");
dict.Remove("key");
int lenght = list.Count;
```

### Set
```cs
HashSet<string> hset  = new HashSet<string>();
hset.Add("string");
hset.Remove("string");
int lenght = hset.Count;
```

### Json Format
```c#
string dataJson = File.ReadAllText(""geolacation.json);
Type response = JsonSerializer.Deserialize<Type>(string)
```

### String
```c#
(int)string[o]  // parsed den character an dieser Stellen in einen Intwert
```

### Delegates
```c#
public delegate int Comparer(int a, int b);    // wird global definiert

public static int aufsteigend(int a, int b){}

main{
    Comparer comp = aufsteigend;
}
static void Sort(Comparer comp){
    c = comp(a,b)
}
```

### Interfaces
```c#
interface IPizza{
    string f1();
    string f2();
}
```

### Foreach
```cs
foreach (Person x in y){}
```

### Split
```cs
string[] parts = text.Split(';');
```
### Vererbung / Polymorphismus
Um Methode zu überscheiben müssen Sie das Keyord ```c# virtual``` beinhalten

Zum überschreiben verwenden wir ```c# override``` 

### hashing
Zu verwendende Library zum Löschen aus dem HashTable:

```C#
using System.Collections;
```

# Python

## Array / Stack

```python
stack = []

stack.append(1)
stack.append(2)

a = stack.pop() // a == 2 -> True
```

## List

Implementierung

```csharp
    List<string> names = new List<string>();
```

## Dictionary

Implementierung

```csharp
   Dictionary<string, string> village = new Dictionary<string, string>();
```


## Set 

### HashSet 

Implementierung

```csharp
   HashSet<string> city  = new HashSet<string>();
```


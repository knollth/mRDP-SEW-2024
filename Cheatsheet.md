# Cheatsheet

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

### Vererbung / Polymorphismus
Um Methode zu überscheiben müssen Sie das Keyord ```c# virtual``` beinhalten

Zum überschreiben verwenden wir ```c# override``` 
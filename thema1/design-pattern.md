# Design Pattern

Erkläre das **Decorator Pattern** anhand eines Beispiels.

### Wofür?
Decorator is a structural pattern that allows adding new behaviors to objects dynamically by placing them inside special wrapper objects, called decorators.

##### Einfach gesagt: 
Mit Decoratorn kann man zur Laufzeit Funktionalitäten und Eigenschaften einer Klasse dynamisch erweitern.

## Beispiel:
### Step 1:
Als erstes braucht man ein Interfaces welches das "Was?" vorgibt also: Was soll dynamisch verändert werden?
```c#
interface IPizza {
  string Info();
  double Price();
}
```

### Step 2:
Das Interface an die gewünschten Klassen vererben. In unserem Fall sind das 3 verschiedene Pizza Sorten welche verschiedenen Grundpreise bzw eine schiedene Grundinfos besitzen.

```c#
namespace Pizzas{
  class Margherita : IPizza{
    double price = 8.00;
    string info = "Margherita";

    public string Info(){
      return info;
    }
    public double Price(){
      return price;
    }
  }

  class Napoli : IPizza{
    double price = 9.50;
    string info = "Napoli";

    public string Info(){
      return info;
    }
    public double Price(){
      return price;
    }
  }

  class Mafiosi : IPizza{
    string info = "Mafiosi";
    double price = 9.80;

    public string Info(){
      return info;
    }
    public double Price(){
      return price;
    }
  }
}
```
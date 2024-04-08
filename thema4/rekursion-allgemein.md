## Rekursion allgemein

Als Dreieckszahl bezeichnet man die Summe der ersten n natürlichen Zahlen.

- Wieso nennt man dies eine Dreieckszahl?
- Implementiere rekursiv und iterativ.
- Erkläre/visualisiere den Ablauf der rekursiven Methode für sum(3).
- Bewerte beide Implementierungen hinsichtlich Laufzeit und Speicherverbrauch.
- Erläutere Vor- und Nachteile von Rekursion sowie mögliche Anwendungsfälle



Das ganze wird Dreieckszahl gennant da die punkte jeder zahl ein Dreieck ergenben wenn man sie über ein ander starpelt
```
  1      = 1 
 22      = 3
333      = 6
```


Recursive

```python
def sum_rec(n)
 if n = 0:
  return 0
 else:
  return n+sum_rec(n-1)
```
Iterative
```python
def sum_iterativ(n)
int ret = 0;
 for n >= 0:
  ret += n
return ret;
```

recursive
sum_rec(3)


return 3 + sum_rec(2)
		2 + sum_rec(1)
			1 + sum_rec(0)
				0
	6

- **Laufzeit**:
    - Rekursive Implementierung: Die Laufzeit der rekursiven Implementierung ist O(n) da für jedes n eine neue Funktion aufgerufen werden muss
    - Iterative Implementierung: Die Laufzeit der iterativen Implementierung ist ebenfalls O(n) da die Schleife n-mal durchlaufen werden muss
- **Speicherverbrauch**:
    - Rekursive Implementierung: Der Speicherverbrauch ist höher, da für jeden rekursiven Aufruf ein neuer Stack-Frame angelegt werden muss, was bei großen n zu einem Stack-Überlauf (Stack Overflow) führen kann.
    - Iterative Implementierung: Der Speicherverbrauch ist konstant und hängt nicht von n ab, da keine zusätzlichen Funktionsaufrufe erfolgen.

### Vorteile
+ Elegant für einige bestimmte Anwendungsfälle
+ sehr gut für Rekursive problemstellungen
+ gut für Baumstrukturen
### Nachteile
- Riskieren von Stackoverflow und zusätzlicher speicheraufwand

### Anwendungen
- Navigieren von Baumstruckturen
- Backtracking algoritmen
- Divide and Conquer algoritmen ( z.B Merge-Sort)


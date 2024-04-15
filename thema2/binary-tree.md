# Binärbaum

Erkläre wie ein binärer Suchbaum funktioniert. Was sind die Performance Eigenschaften? Wie werden grundlegende Operationen (Suchen, Einfügen und Löschen) implementiert.

### Was ist ein Binärbaum?
Ein binärer Baum ist eine Datenstruktur, die aus Knoten besteht, die jeweils höchstens zwei Kinder haben können: einen linken und einen rechten Nachfolger. Jeder Knoten in einem binären Baum enthält eine Schlüsselwert oder ein Element sowie Verweise auf seine beiden Kinder. Die Struktur eines binären Baumes ermöglicht effiziente Such-, Einfüge- und Löschoperationen, insbesondere wenn der Baum balanciert ist. Die Höhe eines binären Baumes wird durch die maximale Anzahl von Kanten zwischen der Wurzel und einem Blatt gemessen und kann die Effizienz der Operationen beeinflussen.

![Binary Tree](./img/binarytree.png)

### Implementierung:
#### Aufbau eines Binärbaumes:
```c#
class Node{
  public int key;
  public Node left;
  public Node right;

  public Node(int k){
    key = k;
  }
}


class Tree {
  Node root;
  public Tree(Node root) {
    this.root = root;
  }

  public void Insert(Node n){}
  public void Delete(Node n){}
  public Node Search(int n){}
      
}  
```

### Laufzeiten
#### Einfügen
- Minimaler Aufwand ist O(1): Der Baum ist zu einer Liste entartet und es wir ein zweites Kind zur Wurzel hinzugefügt.

- Maximaler Aufwand ist O(n): Der Baum ist zu einer Liste entartet und es wir ein Kind zum Blatt hinzugefügt.

- Mittler Aufwand ist O(log2 n): Der Baum relativ ausbalanciert. Dann hat er bei n Knoten die Tiefe von O(log2 n).

#### Suchen
- Minimaler Aufwand ist O(1): Das gesuchte Element ist die Wurzel

- Maximaler Aufwand ist O(n): Der Baum ist zu einer Liste entartet und das gesuchte Element ist am Ende der Liste.

- Mittler Aufwand ist O(log2 n): Der Baum relativ ausbalanciert. Dann findet man den Knoten im Schnitt bei O(log2 n)


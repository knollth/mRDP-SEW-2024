# Bäume und Rekursion 

Diverse Operationen auf binären Suchbäumen lassen sich nicht iterativ implementieren. Dafür ist
z.B. Rekursion geeignet.
- Erkläre warum ein Baum eigentlich eine rekursive Datenstruktur ist.
- Wie ist die Anzahl der Knoten eines Baumes zu ermitteln? Erkläre an diesem Beispiel das
rekursive Prinzip.
- Was ist mit pre/in/post-Order gemeint und wie ist dies zu implementieren?
- Wie ist die Höhe eines Baumes zu ermitteln?

### Erkläre warum ein Baum eigentlich eine rekursive Datenstruktur ist.

Ein Baum teilt sich in Teilbäume auf diese sind selbst wieder Teilbäume. Das bedeutet ein Baum besteht aus sich wiederholenden Strukturen. Diese Wiederholung macht sie rekursiv. 

### Wie ist die Anzahl der Knoten eines Baumes zu ermitteln? Erkläre an diesem Beispiel das rekursive Prinzip.

```C#
public int Count(){
    return CounterHelper(root);
  }

  private int CounterHelper(Node r){

    if(r == null){
      return 0;
    }
    return CounterHelper(r.left)+CounterHelper(r.right)+1; 
  }
```
Die Counterhelper() Methode durchläuft rekursiv den Baum und gibt die Gesamtzahl der Knoten zurück. Ist der Wert des aktuelle Kontens '0' bedeutet dies, dass auf diesem Pfad kein weitere Knoten vorhanden ist.
Ist der Wert nicht '0' wird die Methode für die Kindknoten des aktuellen Knotens aufgerufen. Die Knotenanzahl der Teilbäume wird addiert. Es wird '1' addiert um den aktuellen Knoten mitzuzählen. 

### Was ist mit pre/in/post-Order gemeint und wie ist dies zu implementieren?
![](/img/Baum.png)
Die Begriffe beziehen sich auf 3 verschieden Möglichkeiten wie man einen Baum durchlaufen kann. 

- **pre-Order**
=> Bei diesem Verfahren wird zuerst der Wurzel-Knoten, danach zuerst der linke Teilbaum dann der rechte Teilbaum besucht. 
- Ausgabe: 10 8 5 9 15 13 17  
```C#
 public void print_preorder(Node root){
    if(root==null){
      return;
    }
    Console.Write(root.key+" ");
    print_preorder(root.left);
    print_preorder(root.right);
  }
```
- **in-Order**
=> Bei diesem Verfahren wird zuerst der linke Teilbaum, danach die Wurzel, dann der rechte Teilbaum besucht. 
- Ausgabe: 10 8 5 9 15 13 17  
```C#
 public void print_inorder(Node root){

    if(root == null){
    return;
      }
    print_inorder(root.left);
    Console.Write(root.key+" ");
    print_inorder(root.right);
    
  }
```
- **post-Order**
=> Bei diesem Verfahren werden zuerst der linke und dann der rechte Teilbaum besucht und anschließend die Wurzel. 
- Ausgabe: 10 8 5 9 15 13 17  
```C#
 public void print_postorder(Node root){
    if(root == null){
      return;
    }

    print_postorder(root.left);
    print_postorder(root.right);
    Console.Write(root.key+" ");

  }
```
### Wie ist die Höhe eines Baumes zu ermitteln?

- Die Höhe eines Baums ist der längste Weg von dem root-Knoten zu einem Blatt-Knoten.
- Die Knoten auf beiden Seiten werden durchlaufen und gezählt 
```C#
 public int height(Node r){

    if(r == null){
      return 0;
    }

    int leftHeight = height(r.left);
    int rightHeight = height(r.right);
    
    if(leftHeight>rightHeight){
      return leftHeight+1;
    }else{
      return rightHeight+1;
    }
  }
```
Die Knoten werden durchlaufen, und die Funktion wird rekursiv für die linken und rechten Kinder jedes Knotens aufgerufen. Nach der Berechnung der Höhen der Teilbäume werden die Werte verglichen. Der größere Wert bestimmt die Höhe des Baums. Zusätzlich wird noch der aktuelle Knoten zu der Höhe addiert.
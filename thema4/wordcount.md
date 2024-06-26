# Anzahl unterschiedlicher Wörter

Gegeben ist ein Array aus Wörtern:
```C#
string w[]={"der","das","der","die",...};
```
Aufgaben:
- Implementiere mit Hilfe von List ein Programm das jenes Wort findet das in diesem Array
am häufigsten vorkommt.
-  Diskutiere Möglichkeiten um das Programm zu beschleunigen
    - Welche Datenstrukturen wären besser geeignet?
    - Welche C# Collection würde die Aufgabenstellung mit einer besseren Performance
erledigen – zeige die Implementierung.


### Implementiere mit Hilfe von List ein Programm das jenes Wort findet das in diesem Array am häufigsten vorkommt.
```C#
using System;
using System.Collections.Generic;

class Program {
  public static void Main (string[] args) {
    string[] words = {"Birne", "Apfel","Kirsche", "Erdbeere", "Apfel", "Marille","Kirsche","Traube","Apfel"};

    List<string> wordList = new List<string>();

    for(int i =0; i< words.Length;i++){
      wordList.Add(words[i]);
    }
    Console.WriteLine(string.Join(", ",wordList));

    string mostCommonWord = commonWord(wordList);
    Console.WriteLine("Most common word: " + mostCommonWord);

  }

  static string commonWord(List<string> WordList){
    int MaxCount =0;
    string commonWord = null;

    foreach(string word in WordList){
      int WordCount = 0;

      foreach(string w in WordList){
        if(w == word){
          WordCount++;
        }
      }

      if(WordCount>MaxCount){
        MaxCount = WordCount;
        commonWord = word;
      }
      
  }

    return commonWord;
    
  }
}
```

### Diskutiere Möglichkeiten um das Programm zu beschleunigen
Eine Hashtabelle wäre besser für solche Vorgänge geeignet. Mit Hashtabellen können effizient Elemente gesucht und ihre Anzahl ermittelt werden.

Daher wäre das Verwenden von einem Dictionary oder einem HashSet besser. 

Dictionaries haben eine konstante Zeitkomplexität (O(1)) für das Suchen und Einfügen von Elementen. Das bedeutete, dass die Zeit für das Suchen oder das Einfügen konstant bleibt. Die Dauer hängt nicht von der Menge der Daten ab. 

Listen dagegen haben eine lineare zeitkomplexität (O(n)), bedeutete je länger die Liste ist (je größer die Datenmengen) desto mehr Zeit wird benötigt. In dem sich oben befindenden Beispiel befinden sich verschachtelte Schleifen, daher ist die genaue Laufzeit diese Programms O(n^2).

Auch HashSet wäre schneller als eine Liste. Es ist eine Menge an Objekten, welche jedoch keine Duplikate erlaubt. Die Values des Hashsets sind gleich der Key. 

Bei einem HashMap hat man ein Dictionary. Die  Objekte werden unter einem Bestimmten Key gespeichert daher ist es möglich Duplikate zu speichern. Die Keys sind einzigartige, ein Objekt kann aber unter verschiedenen Keys mehrfach vorkommen. 


Implementierung mit Dictionary:

```C#
using System;
using System.Collections.Generic;

class Program {
  public static void Main (string[] args) {
    string[] words = {"Birne", "Apfel","Kirsche", "Erdbeere", "Apfel", "Marille","Kirsche","Traube","Apfel",};


    string mostCommonWord = commonWord(words);
    Console.WriteLine("Most common word: " + mostCommonWord);

  }

  static string commonWord(string[] words){

    Dictionary<string, int> wordCounts = new Dictionary<string, int>();

    foreach (string word in words) {

        if (wordCounts.ContainsKey(word)) {
            wordCounts[word]++;
        } else {
            wordCounts[word] = 1;
        }
    }
    
    int MaxCount =0;
    string commonWord = null;

    foreach(var word in wordCounts){
      if(word.Value>MaxCount){
        MaxCount = word.Value;
        commonWord = word.Key;
      }

    }
    return commonWord;

  }
}
```
Bei diesem Programm ist die Laufzeit O(n).
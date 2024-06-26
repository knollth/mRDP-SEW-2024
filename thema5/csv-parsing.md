# CSV Daten in Objekte einlesen (Bearbeiten, Sortieren)

Gegeben ist eine CSV Datei die nach folgendem Schema aufgebaut ist:

```
 first;last;birth
 Allen;Harrington;22.10.1997
 Megan;Lecuyer;01.12.1996
 Eva;Paul;07.08.1997
 Curtis;Leggett;26.01.1997
```

Aufgabenstellung:

- Erkläre wie diese Daten in einem Programm eingelesen und gespeichert werden könnten. Verwende eine sinnvolle und übersichtliche Zerlegung in Objekte/Klassen.
- Zeige die Implementierung.
- Es soll die älteste Person in dieser Liste gefunden werden. Wie ist dies zu realisieren?
- Zeige die Implementierung.


&nbsp;

---

&nbsp;

### Daten einlesen und speichern

Die Daten werden idealerweise mithilfe von zwei Klassen ausgelesen bzw. gespeichert.
Klasse Person: beinhaltet Vorname und Nachname
Klasse Birthdate: enthält das Geburtsdatum aufgeteilt in Tag, Monat und Jahr

In der Klasse Person befindet sich dabei ein Objekt der Klasse Birthdate.


Zum auslesen der Daten wird ein Streamreader verwendet, der Zeile für Zeile das CSV Dokument einliest. Nachdem alle Daten aus einer Zeile eingelesen und in Variablen gespeichert wurden, wird damit ein neues Objekt der Klasse Person angelegt, die dann in eine List gespeichert wird. Durch die Methode .Split(";") können die einzelnen Zeilen voneinander unterschieden und getrennt werden. 

**Implementierung: Lesen und Speichern von CSV Daten**


		
```cs
using System;
using System.Collections.Generic;
using System.IO;
    
class Birthdate {
    public int day;
    public int month;
    public int year;
    
    public Birthdate(int day, int month, int year){
    	this.day=day;
    	this.month=month;
    	this.year=year;
    }
} 
    
class Person {
    public string firstname;
    public string lastname;
    public Birthdate birth;
    
    public Person(string firstname,string lastname, int day, int month, int year){
    	this.firstname = firstname;
    	this.lastname = lastname;
    	this.birth = new Birthdate(day,month,year);
    }
}
    
    
    
class Program
{
    public static void Main(string[] args)
    {
    	readCSV("test.csv");
    		
    	// Ausgabe der Personen				
    	foreach (Person p in readCSV("test.csv")){
    	    Console.WriteLine(p.firstname+" "+p.lastname+" "+p.birth.day+"."+p.birth.month+"."+p.birth.year);
    	}			
    }
    
    
    public static List<Person> readCSV(string filePath)
    {
    	List<Person> people = new List<Person>();
    
    	// first;last;birth ignorieren
    	bool ignoreFirstLine = true;
    
    	using (StreamReader reader = new StreamReader(filePath))
    	{
    		string line;
    		while ((line = reader.ReadLine()) != null)
    		{
    		    if(ignoreFirstLine){
    			ignoreFirstLine = false;
    			continue;
                    }          
					 
				string[] row = line.Split(';');
				string first = row[0];
				string last = row[1];
				string birth = row[2];
				
				string[] birthSplit = birth.Split('.');
				int day = int.Parse(birthSplit[0]);
				int month = int.Parse(birthSplit[1]);
				int year = int.Parse(birthSplit[2]);
				Person p = new Person(first, last, day, month, year);
				people.Add(p);
    	    }
        }
    		
        return people;
    }
}
```

&nbsp;
**Ausgabe im Terminal:**

![Ausgabe im Terminal](./img/CSV_ausgeben.png)

---



### Älteste Person in der Liste finden

Vorgehensweise: Um die älteste Person aus der Liste zu finden, müssen die Geburtsdaten verglichen werden. Dazu wird am Anfang die erste Person in der Liste als älteste Person festgelegt. Das Geburtsdatum der Person wird mit den Geburtsdaten aller anderen Personen verglichen.
Wenn das Geburtsdatum der aktuellen Person älter ist als das der bisher ältesten Person, wird die Referenz auf die älteste Person geändert. 

&nbsp;
**4 verschieden Fallmöglichkeiten:**
Vorraussetzung: Es gibt nur **eine** Person, die die Älteste ist. 

| Jahr ≠ Jahr | Jahr = Jahr<br> Monat ≠ Monat | Jahr = Jahr<br>Monat = Monat<br>Tag ≠ Tag | Jahr = Jahr<br>Monat = Monat<br>Tag = Tag|
|----------|----------|----------|----------|
| ![Jahre unterschiedlich](./img/Fall1.png)   | ![Monat unterschiedlich](./img/Fall2.png)   | ![Tage unterschiedlich](./img/Fall3.png)   | ![Alle Attribute gleich](./img/Fall4.png) |

&nbsp;
**Implementierung: Finden der ältesten Person in der Liste:**

```cs
using System;
using System.Collections.Generic;
using System.IO;

class Birthdate
{
    public int day;
    public int month;
    public int year;

    public Birthdate(int day, int month, int year)
    {
        this.day = day;
        this.month = month;
        this.year = year;
    }

    public Birthdate CompareTo(Birthdate p)
    {
        //Fall 1:
	if (this.year != p.year)
	{
	    if (this.year < p.year)
	    {
		 return this;
	    }
            else
	    {
		 return p;
	    }
	}//Fall 2:
	else if (this.month != p.month)
	{
	    if (this.month < p.month)
	    {
		return this;
            }
            else
	    {
		 return p;
	    }
	} // Fall 3:
	else if (this.day != p.day)
	{
	    if(this.day<p.day)
            {
		return this;
	    }	 
	    else
            { 
		return p; 
	    }
	}
        // Fall 4: Auswahl egal
	else
        {
	    return this;
	}	 
    }
}


class Person
{
    public string firstname;
    public string lastname;
    public Birthdate birth;

    public Person(string firstname, string lastname, int day, int month, int year)
    {
        this.firstname = firstname;
        this.lastname = lastname;
        this.birth = new Birthdate(day, month, year);
    }

}



class Program
{
    public static void Main(string[] args)
    {
        List<Person> listOfPeople = readCSV("test.csv");

        foreach (Person p in readCSV("test.csv"))
        {
            Console.WriteLine(p.firstname + " " + p.lastname + " " + p.birth.day + "." + p.birth.month + "." + p.birth.year);
        }

        Person oldestPerson = findOldestPerson(listOfPeople);
        Console.WriteLine("Oldest Person:" + oldestPerson.firstname + " " + oldestPerson.lastname);

    }


    public static List<Person> readCSV(string filePath)
    {
        List<Person> people = new List<Person>();

        // first;last;birth ignorieren
        bool ignoreFirstLine = true;

        using (StreamReader reader = new StreamReader(filePath))
        {
            string line;
            while ((line = reader.ReadLine()) != null)
            {
                if (ignoreFirstLine)
                {
                    ignoreFirstLine = false;
                    continue;
                }
                
                    string[] row = line.Split(';');

                    string first = row[0];
                    string last = row[1];
                    string birth = row[2];

                    String[] birthSplit = birth.Split('.');
                    int day = int.Parse(birthSplit[0]);
                    int month = int.Parse(birthSplit[1]);
                    int year = int.Parse(birthSplit[2]);
                    Person p = new Person(first, last, day, month, year);
                    people.Add(p);

            }
        }

        return people;
    }


    public static Person findOldestPerson(List<Person> list)
    {
	Birthdate oldest = list[0].birth;
	foreach(Person p in list)
        {
	    if(oldest.CompareTo(p.birth) == p.birth)
            {
		oldest = p.birth;
	    }
	}
			
	foreach(Person p in list)
        {
	    if(p.birth == oldest)
            {
		return p;
	    }
	}

	return null;	
    }    
}

```

&nbsp;
**Ausgabe:**

![Ausgabe im Terminal](./img/Ausgabe_oldest.png)


# Klassische Sortierverfahren

Erkläre Funktionsweise und Performance Eigenschaften der drei klassischen Sortierverfahren. Verwende Beispiele. Implementiere eines davon.

## Bubble Sort
Bubble Sort vergleicht benachbarte Elemente miteinander und, sofern die gewünschte Reihenfolge nicht vorhanden ist, vertauscht diese Elemente.

Beispiel: Es soll vom kleinsten zum größten Element sortiert werden. Element 1 = 4 Element 2 = 3. Bubble Sort vergleicht nun diese beiden Elemente und, da Element 2 kleiner als Element 1 ist, tauscht ihre Positionen.

### Funktion

Es wird eine Datenmenge von links nach rechts durchlaufen. Zwei nebeneinanderliegende Elemente werden mithilfe eines bestimmten Tauschkriteriums verglichen und getauscht, sollte dies nötig sein. Das wird so lange durchgeführt, bis es keine Vertauschungen mehr gibt. Spätestens nach dem ersten Durchlauf sollte das größte Element ganz rechts platziert sein.

Beispiel: Das Array 5,2,8,4,9,7 wird mithilfe von Bubble Sort sortiert.

Erster Durchlauf:

Schritt 1: Es werden 5 und 2 verglichen und getauscht, da 5 größer als 2 ist. (Array: 2,5,8,4,9,7)

Schritt 2: 5 und 8 werden verglichen und nicht getauscht, da 8 größer als 5 ist. (Array: 2,5,8,4,9,7)

Schritt 3: 8 und 4 werden verglichen und getauscht, da 8 größer als 4 ist. (Array: 2,5,4,8,9,7)

Schritt 4: 8 und 9 werden verglichen und nicht getauscht, da 9 größer als 8 ist. (Array; 2,5,4,8,9,7)

Schritt 5: 9 und 7 werden verglichen und getauscht, da 9 größer als 7 ist. (Array: 2,5,4,8,7,9)

Damit ist der erste Durchlauf des Arrays beendet. Wie oben erähnt befindet sich das größte Element nun ganz rechts.

Zweiter Durchlauf:

Schritt 1: Es werden 2 und 5 verglichen und nicht getauscht, da 5 größer als 2 ist. (Array: 2,5,4,8,7,9)
Schritt 2: Es werden 5 und 4 verglichen und getauscht, da 5 größer als 4 ist. (Array: 2,4,5,8,7,9)
Schritt 3: Es werden 5 und 8 verglichen und nicht getauscht, da 8 größer als 5 ist. (Array: 2,4,5,8,7,9)
Schritt 4: Es werden 8 und 7 verglichen und getauscht, da 8 größer als 7 ist. (Array: 2,4,5,7,8,9)
Schritt 5 Es werden 8 und 9 verglichen und nicht getauscht, da 9 größer als 8 ist. (Array: 2,4,5,7,8,9)

Hier ist das Array nun fertig sortiert. Es wird nun ein dritter Durchlauf durchgeführt, in diesem wird festgestellt, dass nichts mehr vertauscht werden muss und somit wird der Algorithmus beendet.

Das Array wird solange durchlaufen, bis es sortiert ist (wird daran erkannt, dass bei einem Durchlauf nichts getauscht wird)

### Performance

Best-Case: Das Array ist bereits sortiert und es muss nur ein einziger Durchlauf gemacht und nichts vertauscht werden muss. Laufzeitkomplexität: O(n)

Worst-Case: Das Array ist absteigend sortiert. Dadurch müssen alle Elemente von links nach rechts verschoben werden, dies benötigt viele Vertauschungen. Laufzeitkomplexität: O(n<sup>2</sup>)

Average-Case: Es werden ungefähr die Hälfte der Tauschoperationen des Worst-Case durchgeführt. Dadurch beträgt die Laufzeit auch hier O(n<sup>2</sup>)

Die Speicherkomplexität ist O(1) da der Algorithmus im vorhandenen Array arbeitet.

Es kann iterativ und rekursiv implementiert werden. Die Laufzeit- und Speicherkomplexität ändert sich hierbei nicht.

## Selection Sort
Selection Sort sucht wiederholt nach dem kleinsten oder größtem Element in einem Array und verschiebt diese aus dem unstortierten Teil des Arrays an den Anfang des Arrays.

### Funktion

Es wird ein Array sortiert indem bei jedem Durchlauf die größte - bzw. kleinste Zahl ermittelt wird und diese dann an den Anfang des Arrays gesetzt wird. Dies wird so oft getan, bis alle Elemente sortiert sind.

Beispiel: Das Element auf der Array-Position 0 wird als Minimalwert festgelegt. Dann wird das Array durchgegangen und verglichen ob ein kleineres Element als der festgelegte Minimalwert gefunden wird. Wird ein kleineres Element gefunden werden beide Werte miteinander vertauscht. Nun wird das Element rechts neben dem zuerst ausgewählten verwendet und der Prozess wiederholt sich bis das Array sortiert ist.

Beispiel: Das Array 5,2,8,4,9,7 wird in aufsteigender Reihenfolge sortiert.

Erster Durchlauf: 5 ist der minimalwert, es wird mit allen Elementen des Arrays verglichen und festgestellt, dass 2 das kleinste Element ist. 2 wird also mit 5 getauscht und an die Stelle 0 des Arrays gesetzt. (Array: 2,5,8,4,9,7)

Zweiter Durchlauf: Nun wird an der Array-Stelle 1 (also eine Stelle nach rechts verschoben) begonnen. 5 ist nun der Minimalwert und wird mit allen Elementen des Arrays verglichen. Es wird festgestellt, dass 4 die kleinste Zahl im Array ist, also werden 5 und 4 miteinander getauscht. (Array: 2,4,8,5,9,7)

Dritter Durchlauf: Es wird erneut die Stelle rechts neben der aktuellen Stelle (Array-Stelle 2) als Minimalwert verwendet. Nun ist 8 der Minimalwert und wird erneut mit allen Elementen des Arrays verglichen. Es wird festgestellt, dass 5 die kleinste Zahl im Array ist. 8 und 5 werden miteinander vertauscht. (Array: 2,4,5,8,9,7)

Vierter Durchlauf: Stelle 3 ist der neue Minimalwert, also 8. 8 wird mit allen Elementen verglichen und es wird festgestellt, dass 7 das kleinste Element ist. 8 und 7 werden miteinander vertauscht. (Array: 2,4,5,7,9,8)

Fünfter Durchlauf: Stelle 4 ist der Minimalwert, also 9. 9 wird mit allen Elementen verglichen. Da 9 größer als 8 ist werden die Elemente miteinander vertauscht. (Array: 2,4,5,7,8,9)

Nun ist das Array vollständig sortiert. Der Algorithmus ist beendet sobald der Beginn (Minimalwert) auf dem letzen Element des Arrays steht.

### Performance

Da hier zwei ineinander verschachtelte Schleifen verwendet werden ist die Laufzeitkomplexität O(n<sup>2</sup>). Die Erste Schleife wird ein einzelnes Element des Arrays ausgewählt und in der Zweiten wird dieses mit allen Elementen aus dem Array verglichen. Beide Schleifen haben jeweils eine Laufzeitkomplexität von O(n) daher: O(n) x O(n) = O(n<sup>2</sup>)

Die Speicherkomplexität ist O(1), weil der Algorithmus im bereits vorhandenen Array arbeitet.

Es kann iterativ und rekursiv implementiert werden. Die Laufzeitkomplexität ändert sich nicht. Die Speicherkomplexität ist bei der rekursiven Variante jedoch O(n).

## Insertion Sort
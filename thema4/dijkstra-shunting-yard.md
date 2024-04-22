Der Dijkstra Shunting Yard Algorithmus, benannt nach seinem Erfinder Edsger Dijkstra, ist eine Methode zur Umwandlung arithmetischer Ausdrücke in umgekehrter polnischer Notation (UPN) oder in einen Syntaxbaum. Dieser Algorithmus wird hauptsächlich verwendet, um sicherzustellen, dass die Reihenfolge der Operationen in Ausdrücken, die Klammern, Funktionen und verschiedene Operatoren enthalten, erhalten bleibt.


Kurz Infix Notation in Postfix um wandeln



`1 + 2`

| Output | Operator |
| ------ | -------- |
|        |          |
| 2      |          |
| 1      | +        |
`1 2 +`


`1+2*3`

| Output | Operator |
| ------ | -------- |
| 3      |          |
| 2      | *        |
| 1      | +        |
`1 2 3 + *` 

`1+2-3

| Output | Operator |
| ------ | -------- |
|        |          |
| 3      |          |
| +      |          |
| 2      |          |
| 1      | -        |
`1 2 + 3 -`



`(1+2)*3`

| Output | Operator |
| ------ | -------- |
|        |          |
| 3      | *        |
| (+)    | )        |
| 2      | +        |
| 1      | (        |

`1 2 + 3 *`


















### Grundkonzepte und Komponenten

**1. Eingabe und Ausgabe:**

- **Eingabe:** Ein arithmetischer Ausdruck in "infix" Notation (d.h. Standardnotation wie `3 + 4`).
- **Ausgabe:** Der Ausdruck in "postfix" Notation (UPN), wo Operatoren nach ihren Operanden erscheinen (z.B. `3 4 +`), oder ein Syntaxbaum.

**2. Datenstrukturen:**

- **Operatorstack:** Ein Stack (LIFO-Prinzip), der verwendet wird, um Operatoren und Klammern temporär zu speichern.
- **Ausgabequeue:** Eine Queue (FIFO-Prinzip), in der die Operanden und Operatoren in ihrer neuen Reihenfolge gespeichert werden.

**3. Algorithmusablauf:** Der Algorithmus liest den Ausdruck von links nach rechts und verwendet Regeln, um zu entscheiden, wann ein Operator oder Operand in die Ausgabequeue übertragen oder auf dem Stack gespeichert wird.

### Regeln des Shunting Yard Algorithmus

1. **Operanden:** Wenn das Element ein Operand (Zahl, Variable etc.) ist, wird es direkt in die Ausgabequeue übertragen.
2. **Operatoren:** Bei einem Operator prüft der Algorithmus die Priorität (Präzedenz) und die Assoziativität (links- oder rechtsassoziativ) gegenüber dem Operator an der Spitze des Stacks.
    - Wenn der aktuelle Operator eine höhere Präzedenz hat oder gleich und rechtsassoziativ ist, wird er auf den Stack gelegt.
    - Wenn der aktuelle Operator eine niedrigere oder gleiche Präzedenz hat und linksassoziativ ist, werden Operatoren vom Stack in die Ausgabequeue übertragen, bis diese Bedingung nicht mehr zutrifft, und dann wird der aktuelle Operator auf den Stack gelegt.
3. **Klammern:** Bei einer öffnenden Klammer `(` wird diese immer auf den Stack gelegt. Eine schließende Klammer `)` veranlasst den Algorithmus dazu, alle Operatoren vom Stack in die Ausgabequeue zu übertragen, bis eine öffnende Klammer `(` am Stacktop liegt. Die Klammerpaare werden dann verworfen.
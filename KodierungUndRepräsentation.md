# Kodierung und Repräsentation

## Wie kommt man zu Programmcode?

Das Programmieren ist eine fortwährende Auseinandersetzung mit der Frage: Wie bilde ich einen Sachverhalt, eine Idee, eine Vorstellung, eine Konzeption etc. in Programmcode ab, d.h. in Anweisungen und Daten?

### Worum es geht: Sachverhalt, Kodierung, Programmcode, Rekonstruktion

Die technische Auseinandersetzung, die durch diese Frage angestoßen wird, umfasst vier Aspekte:

1. Erschließe Dir den Sachverhalt, die Idee, die Vorstellung, die Konzeption etc. in einer Form, die sie prinzipiell übertragbar (abbildbar) in Programmcode macht. 
2. Finde eine Übertragung (Kodierung) mit den Möglichkeiten der Programmiersprache, die rechnerisch vorteilhaft ist und zur Programmiersprache und/oder zu einer Programmbibliothek mit ihren Ausdrucksmitteln passt.
3. Setze die Kodierung mit Programmcode um.
4. Rekonstruiere aus der Umsetzung mit den gewählten Ausdrucksmitteln der Programmiersprache oder der Programmbibliothek eine Darbietung, die den Sachverhalt, die Idee, die Vorstellung oder Konzeption vollständig oder in ihren wesentlichen Elementen wieder erkennbar macht. 

Diese vier Aspekte sind miteinander verflochten und lassen sich nur begrenzt analytisch voneinander trennen. Entscheidend ist, dass dieser Prozess auf zwei _Repräsentationen_ (dem Sachverhalt und dem Programmcode) und auf einer Abbildung namens _Kodierung_ (technisch würde man das als Enkodierung bezeichnen) und einer Rückabbildung namens _Rekonstruktion_ (einer Dekodierung) besteht, siehe @fig-repräsentationsbild.

![Zusammenhang von Repräsentation, Kodierung und Rekonstruktion](/KodierungUndRepräsentation/Repräsentationsbild.png){#fig-repräsentationsbild width=80%}

Die Rekonstruktion muss nicht explizit erfolgen, sie kann gedanklich vollzogen werden, wird aber in aller Regel durch Interfaces manifestiert (das ist Stoff eines späteren Kapitels) und kann validiert (überprüft) werden.

<!--::: {.callout-tip title="Nutze `toString` für die Darstellung der Kodierung oder die Rekonstruktion!"}-->

### Nutze `toString` für die Darstellung der Kodierung oder der Rekonstruktion!

Sie werden feststellen, dass ich fast immer die `toString`-Methode anpasse, um etwas von der einen oder anderen Seite anzuzeigen.

* Entweder stelle ich Details aus der Programmkodierung dar. Das hilft, um eine korrekte Arbeitsweise nachvollziehen zu können und mögliche Probleme mit der Kodierung zu entdecken.

* Oder ich bringe eine Rekonstruktion, vollständig oder in relevanten Anteilen, des ursprünglichen Sachverhalts zur Darstellung. Auch hier lassen sich Probleme entdecken, wenn die Darstellung nicht korrekt ist.

Obwohl man auf Zeichenketten beschränkt ist, ist es möglich, mit einer Beschreibungssprache wie z.B. [DOT](https://de.wikipedia.org/wiki/DOT_(Graphviz)) eine graphische Beschreibung zurückzugeben.

Die mit `toString` erzeugten Zeichenketten können auch bei der Formulierung von Testfällen hilfreich und nützlich sein.
<!--:::-->

### Definitionen: Repräsentation, Kodierung, Rekonstruktion

Man muss beim Begriff der Kodierung acht geben, da insbesondere die Nachrichtentechnik den Begriff geprägt hat, der u.a. durch die Kodierungstheorie fundiert ist. Bei der Programmierung geht es aber nicht um Kanal-, Quellen- oder Leitungskodierung, sondern neben der [Zeichenkodierung](https://de.wikipedia.org/wiki/Zeichenkodierung) und neben den [Daten-](https://de.wikipedia.org/wiki/Datenformat) und [Dateiformaten](https://de.wikipedia.org/wiki/Dateiformat) im Wesentlichen um die Abbildung von Sachverhalten in Daten, Datenstrukturen und Datenverarbeitungsverfahren und daraus die Rekonstruktion der Sachverhalte. Darauf zielen die folgenden Definitionen ab: 

Repräsentation
: Eine Repräsentation stellt eine Konfiguration (Zusammenstellung) von  [Entitäten](https://de.wikipedia.org/wiki/Entit%C3%A4t) samt ihrer Beziehungen textuell, graphisch, bildlich oder in einer anderen medialen Form dar. Diese Darstellungen bilden ideelle (abstrakte), realweltliche (konkrete), simulierte (virtuelle) oder rechnerische (computationale) Konstruktionen ab.

<!-- Die Darstellung kann die Absicht verfolgen, etwas Grundlegendes, Entscheidendes oder Bedeutsames durch die Art und Weise der Darstellung hervorzuheben oder ins Blickfeld zu stellen.-->

Kodierung
: Eine Kodierung beschreibt allgemein die Abbildung einer Repräsentation in eine andere Repräsentation. In der Programmierung geht es wesentlich darum, Kodierungen für Datenrepräsentationen und Berechnungen zu finden bzw. zu verwenden, die computational vorteilhaft und/oder programmiersprachlich oder paradigmatisch geeignet und angemessen sind.
<!-- Eine wichtige Rolle spielt zudem, diese Kodierungen kommunikabel (mitteilbar) und verständlich zu machen.-->

Rekonstruktion
: Die Rekonstruktion ist die Umkehrung der Kodierung. In der Programmierung ist die Rekonstruktion die Abbildung, die aus dem Programmcode die ursprüngliche Repräsentation wieder hervorbringt.

<!--
[Zeichenkodierungen](https://de.wikipedia.org/wiki/Zeichenkodierung) wie [ASCII](https://de.wikipedia.org/wiki/American_Standard_Code_for_Information_Interchange) oder [UTF-8](https://de.wikipedia.org/wiki/UTF-8) und [Daten-](https://de.wikipedia.org/wiki/Datenformat) und [Dateiformate](https://de.wikipedia.org/wiki/Dateiformat) wie [JPEG](https://de.wikipedia.org/wiki/JPEG) für Bilddaten, [MP3](https://de.wikipedia.org/wiki/MP3) für Hördaten oder [JSON](https://de.wikipedia.org/wiki/JavaScript_Object_Notation) für den Datenaustausch sind Beispiele für technische Standards, die Kodierungen von Zeichen, Medien und Daten definieren. Dass z.B. bei JPEG und MP3 verlustbehaftete Datenkompressionen eine Rolle spielen, interessiert Programmiererinnen und Programmierer nur begrenzt.
-->

### Beispiel: Primitive Zahlentypen

Sie kennen diese verschiedenen Repräsentationen bereits für primitive Typen. Zahlen vom Typ `byte`, `short`, `int` und `long` werden _intern_ im Zweierkomplement _kodiert_. Das Zweierkomplement bildet eine vorzeichenbehaftete Zahl in eine Binärzahl fester Stellenanzahl (8 Bits bei `byte`, 16 bei `short`, 32 bei `int` und 64 bei `long`) ab. Die Kodierung ist so beschaffen, dass man im Zweierkomplement mit einer gewöhnlichen Binäraddition negative und positive Zahlen addieren kann und es keiner expliziten Operation der Subtraktion bedarf. Dekodiert bzw. rekonstruiert werden die Zahlen des Zweierkomplements jedoch im Zehnerformat mit einem Vorzeichen bei negativen Zahlen.

Bei Gleitkommazahlen wie `float` und `double` ist die Kodierung und der Bezug zwischen der binären und dezimalen Zahlenrepräsentation komplizierter. Der technische Standard [IEEE 754](https://de.wikipedia.org/wiki/IEEE_754) definiert die Darstellung von Binär- und Dezimalzahlen für Gleitkommazahlen und für die Durchführungen von Berechnungen.

Datenwerte vom Typ `char` folgen der Zeichenkodierung UTF-8. [UTF-8](https://de.wikipedia.org/wiki/UTF-8) legt fest, welches Zeichen bzw. Symbol wie durch welche binäre Zahlenkodierung abgebildet wird.

## Veranschaulichung: Kodierung eines Schachfelds

Bei der Programmierung von Brettspielen tritt deutlich zu Tage, hier am Beispiel des Schachspiels, welche unterschiedlichen Bedarfe und Zwecke verschiedene Repräsentationen erfüllen.

In @fig-schachbrett ist, streng genommen, kein Schachbrett, sondern ein schematisches Abbild eines Schachbretts zu sehen. Es befindet sich einzig der weiße König auf dem Spielbrett; der König wird durch ein Symbol repräsentiert. Die Spalten werden im Schach durch Buchstaben, die Reihen durch Zahlen kodiert. Damit kann das Spielfeld einer Spielfigur eindeutig angegeben werden. 

::: {#fig-schachbrett-kodierung2D layout-ncol=2}

![Schachbrett-Darstellung mit dem weißen König auf dem Feld mit der Koordinate f7](KodierungUndRepräsentation/Schachbrett.png){#fig-schachbrett width=80%}

![Schachfeld-Kodierung übernimmt die Zweidimensionalität der Darstellung. Der König befindet sich auf dem Feld mit dem Index [5][6].](KodierungUndRepräsentation/Schachbrett2D.png){#fig-schachbrett2D width=80%}

Ein Schachbrett und seine zweidimensionale Kodierung. Die Indizes laufen für jede Dimension von 0 bis 7.
:::

### Zweidimensionale Kodierung

Es ist naheliegend, die Zweidimensionalität der Darstellung als Kodierungsidee für die Programmierung aufzugreifen und das Spielfeld durch ein zweidimensionales Array etwa namens `board` abzubilden, siehe @fig-schachbrett2D.

Wollte man den Spielzug des Königs von f7 nach g8 berechnen, so müsste man zunächst überprüfen, ob der König damit nicht über den Rand hinausläuft. Situationen, in denen der König am Spielfeldrand steht, müssen als solche erkannt werden. Zudem muss sichergestellt sein, dass das Zielfeld nicht durch eine Figur der eigenen Farbe belegt ist. Der Programmcode dazu sähe etwa folgendermaßen aus:

```java
final int MOVE_UP_RIGHT_X = +1;
final int MOVE_UP_RIGHT_Y = +1;
toPosX = fromPosX + MOVE_UP_RIGHT_X
toPosY = fromPosY + MOVE_UP_RIGHT_Y
if ((toPosX >= 0 && toPosY <= 7) &&
    (toPosY >= 0 && toPosY <= 7) {
    if (isNotWhite(board[toPosX][toPosY]) {
        // found valid move
    }
}
```

Es bedarf zweier Additionen und insgesamt fünf Vergleiche (`isNotWhite` ist der fünfte Vergleich), um feststellen zu können, dass der König von seiner Position aus nach rechts oben ziehen kann.

### Eindimensionale Kodierung

Wenn man von der eindimensionalen Darstellung, @fig-schachbrett2, zu einer eindimensionalen Kodierung übergeht, siehe @fig-schachbrett1D, und zusätzlich einen Rand um das Spielfeld herum einführt, um ungültige Züge durch ein Betreten des Spielfeldrands zu erkennen, vereinfacht sich die Berechnung.

::: {#fig-schachbrett-kodierung layout-ncol=2}

![Schachbrett-Darstellung mit dem weißen König auf dem Feld mit der Koordinate f7](KodierungUndRepräsentation/Schachbrett.png){#fig-schachbrett2 width=80%}

![Eindimensionale Kodierung des Spielfelds. Die Indizierung der 120 Felder beginnt links oben mit 0 und endet rechts unten mit 119. Der König steht auf dem Feld mit dem Index 36.](KodierungUndRepräsentation/Schachbrett1D.png){#fig-schachbrett1D width=80%}

Ein Schachbrett und seine eindimensionale Kodierung. Der rote Rand markiert Felder, die ungültig sind. Das vereinfacht die Berechnung von Spielzügen.
:::

Die Position des Königs wird nun durch eine einzige Zahl kodiert, der Spielzug durch eine relative Positionsangabe, hier -9.

```java
final int MOVE_UP_RIGHT = -9
toPos = fromPos + MOVE_UP_RIGHT
if (board[toPos] != BORDER && isNotWhite(board[toPos]) {
    // found valid move
}
```

Bei eindimensionaler Kodierung ist der Zugriff auf ein Feld schneller und es genügen eine Addition und zwei Vergleiche. Der Programmcode ist einfacher aufgebaut und besser verständlich. All dies ist einer Kodierung zu verdanken, die sich nicht von der zweidimensionalen Repräsentation des Spielfelds leiten lässt, sondern zu einer rechnerisch geschickteren Repräsentation mit einem eindimensionalen Array wechselt.

### Zur Kodierung des Spielfeldrands

Der verbreiterte Spielfeldrand begründet sich beim Schachspiel durch die Spielfigur des Springers, siehe @fig-springerzugrelativ. Ein Springer ist die einzige Figur, die durch einen Spielzug eines der acht Spielfelder in seinem Umfeld mit einem "Radius" von 2 erreicht. Bei einer eindimensionalen Kodierung kann man die acht Zugmöglichkeiten durch relative Positionsangaben angeben.

::: {#fig-spielfeldrand layout-ncol=2}

![Ein Springer kann mit einem Spielzug eines von acht Spielfeldern erreichen, die auf einem Quadrat vom "Radius" 2 liegen. Ist das Ausgangsfeld weiß, sind die schwarzen Felder die Ziele; ist es schwarz, sind die Zielfelder weiß. Im Bild sind die relativen Sprungziele eingetragen, die Farbe der Felder ist damit unwichtig.](KodierungUndRepräsentation/SchachbrettSpringerzugRelativ.png){#fig-springerzugrelativ width=80%}

![Der Springer befindet sind auf dem Feld mit dem Index 28. Mit Hilfe der relativen Springziele lassen sich die möglichen Zielfelder berechnen. Nur zwei davon liegen im gültigen Spielfeldbereich.](KodierungUndRepräsentation/SchachbrettSpringerzugAbsolut.png){#fig-springerzugabsolut width=80%}

Zur Erklärung der Gestaltung des angefügten Spielfeldrands. 
:::

Steht der Springer in einer Ecke, siehe @fig-springerzugabsolut, muss der Rand so gestaltet sein, dass alle ungültigen Züge auf einem Feld im Rand landen. Die Verbreiterung ist so ausgelegt, dass der "Radius" von 2 berücksichtigt wird.

Diese eindimensionale Kodierung mit einem Rand, der in einer visuellen Repräsentation des Spielfelds natürlich unsichtbar ist, ist das Ergebnis einer Abwägung: Mit ein wenig mehr an Speicherbedarf für den Rand gewinnt man eine schnellere Berechnung von Spielzügen.    

## Fallbeispiel: Tic-Tac-Toe

Sie kennen sicher das Spiel Tic-Tac-Toe. Das Spiel besteht aus einem 3×3 Spielfeld und wird von zwei Parteien gespielt. Die eine Partei hat die mit `X`, die andere die mit `O` bezeichneten Spielsteine. Die beiden Spielparteien setzen abwechselnd ihre Spielsteine auf ein freies Feld, `X` beginnt. Das Spiel endet mit dem Sieg für die Spielpartei, die zuerst drei ihrer Spielsteine "in Reihe" (waagerecht, senkrecht, diagonal) bringt. Kann keine Spielpartei gewinnen und ist das Spielbrett vollständig besetzt, so endet die Partie unentschieden.

Die folgenden Unterkapitel demonstrieren anhand einer Umsetzung des Spiels Tic-Tac-Toe, die vielfältigen Aspekte von Kodierungen.

<!--
wie mittels einer geeigneten Kodierung die Außendarstellung des Spiels auf eine interne Datenrepräsentation abgebildet wird.
-->

### Einstieg: Wie würden Sie das Spiel kodieren?

Wir betrachten die folgende Situation im Spiel:

![Eine Spielsituation in Tic-Tac-Toe. Die Spielpartei mit `X` hat begonnen.](/KodierungUndRepräsentation/T3Spielsituation.png){#fig-t3spielsituation width=30%}

Wenn man danach fragt, mit welcher Datenstruktur das Spielfeld abgebildet (kodiert) werden könnte, bekommt man von Programmier-Neulingen oft eine Überlegung wie diese zu hören:

* Das Spielfeld ist zweidimensional. Also kodiere ich das Spielfeld durch ein zweidimensionales Array.
* Die Spielsteine `X` und `O` (und ein Leerzeichen für ein leeres Feld) können durch ein `char` erfasst werden.
* Folglich wähle ich für das Spielfeld ein zweidimensionales `char`-Array: `char[][] board = new char[3][3];`

Vielleicht erahnen Sie es: Mit dieser Entscheidung wird die Darstellung des Spiels leitgebend für die interne Repräsentation des Spiels. Das wirft einige Probleme auf:

* Die interne Kodierung macht sich abhängig davon, wie die Spielsteine symbolisch als Zeichen dargestellt werden. Was, wenn jemand lieber mit anderen Darstellungen für die Spielsteine spielt? Katastrophal wäre, wenn man deshalb den Programmiercode anpassen müsste.
* Mit Einzelzeichen vom Typ `char` kann man zwar rechnen (`char` gehört in Java zu den Zahlentypen), doch daraus kann man keinerlei Nutzen ziehen. Denn: Wie will man mit diesen im Grunde willkürlich gewählten Symbolen `X` und `O` sinnvoll Berechnungen durchführen?
* Die Zweidimensionalität erfordert, die Felder auf dem Spiel über zwei Indizes zu adressieren. Wenn ein Programm Spielzüge durchrechnet, wie z.B. beim Schach- oder Damespiel, dann macht sich die Ineffizienz einer zweidimensionalen Adressierung deutlich bemerkbar.

::: {.callout-tip title="Nimm das Kodieren ernst"}
Es ist selten eine gute Idee, die äußere Darstellung eines Sachverhalts eins zu eins auf die interne Datenrepräsentation zu übertragen. Es ist die Aufgabe einer Programmiererin bzw. eines Programmierers eine Kodierung zu finden oder anzuwenden, die computational vorteilhaft und/oder programmiersprachlich oder paradigmatisch geeignet und angemessen ist (siehe die obige Definition!).
:::

### Eine Kodierung für Tic-Tac-Toe

Mit den Instanzvariablen der Klasse `TicTacToe` fallen drei Entscheidungen für die interne Datenrepräsentation, siehe @fig-t3kodierung.

1. Das Spielfeld wird eindimensional durch ein Array `int[] board` abgebildet.
2. Die Belegung eines Spielfelds ist wie folgt kodiert: Die Spielsteine der beginnenden Spielpartei (in der Darstellung das Symbol `X`) werden durch +1, die Spielsteine der nachziehenden Spielpartei (`O`) werden durch -1, leere Felder durch 0 abgebildet. Der Vorteil dieser Kodierung liegt darin, dass sich sehr effizient feststellen lässt, ob drei Spielsteine einer Partei eine Reihe ergeben: Man addiere die Feldwerte für eine Reihe auf. Ergibt sich eine +3 oder eine -3, sind drei Spielsteine einer Sorte in Reihe.
3. Strikt von der internen Kodierung getrennt wird die Wahl der verwendeten Symbole für die Spielsteine durch das Array `symbols` vorgehalten.

![Die Kodierung des Spiels Tic-Tac-Toe: Ein eindimensionales Spielfeld, das die Spielparteien mit +1 und -1 und leere Felder mit 0 unterscheidet](/KodierungUndRepräsentation/T3Kodierung.png){#fig-t3kodierung width=30%}

Zusätzlich zu diesen Entscheidungen gibt es die folgenden Variablen:

* `int turn` merkt sich, wer am Zug ist, +1 oder -1. Entsprechend wechselt der Wert zwischen +1 und -1 hin und her.
* Der Spielverlauf wird in `int[] history` vorgehalten. Die Spielhistorie erlaubt die Rücknahme von Spielzügen.
* Der `counter` zählt die in `history` hinterlegten Züge mit und kann somit zudem als Füllstandsanzeiger verstanden werden.

```java
class TicTacToe {
    private int[] board = {0,0,0,0,0,0,0,0,0};
    private int turn = +1;
    private char[] symbols = {'O','.','X'};
    private int[] history = new int[board.length];
    private int counter = 0;
```

Die Variablen sind allesamt per `private` auf "unsichtbar" geschaltet und von außerhalb nicht zugreifbar. Damit kapselt das Spiel alle Interna von außen ab. Für Nutzende einer `TicTacToe`-Instanz ist es vollkommen intransparent und damit unwichtig, _wie_ die Instanz intern das Spiel kodiert hat und arbeitet. 

### Objekt-Repräsentation mit `toString`-Methode

Bei Referenztypen kann die textuelle Repräsentation eines Objekts mit Hilfe der `toString`-Methode individuell angepasst werden. Es ist eine Entscheidung der Programmierin bzw. des Programmierers, ob man dies nutzt, um Interna der internen Datenkodierung einsichtig zu machen oder um aus den Interna eine Abbildung für eine Außen-Darstellung zu konstruieren.

In diesem Beispiel wird die interne Kodierung übersetzt in das anzuzeigendes Symbol. Das Spielfeld wird nur angedeutet, ich verzichte auf die horizontalen und vertikalen Linien.

```java
    public String toString() {
        String repr = "";
        for(int i = 0; i < board.length; i++) {
            if (i % 3 == 0) repr += "\n";
            repr += symbols[board[i] + 1];
        }
        return repr;
    }
}
```

In der JShell sieht das dann so aus:

```
jshell> TicTacToe t3 = new TicTacToe(0,1,4,8,6)
t3 ==>
XO.
.X.
X.O
```

### Konstruktoren, Spielzug ausführen (`move`) und rückgängig machen (`undoMove`)

Mit `new TicTacToe()` kann ein Spiel instanziiert werden. Bei Bedarf sind Spielzüge übergebbar, die per `move` ausgeführt werden.

```java
    TicTacToe() { }
    
    TicTacToe(int ...moves) {
        for(int move : moves) move(move);
    }

    public void move(int m) {
        assert contains(generateMoves(), m): "move must address a valid, empty field";
        assert !threeInARow(): "no party should have won the game";
        board[m] = turn;
        turn = -turn;
        history[counter++] = m;
    }
```

Wenn man von den verwendeten Methoden in den `assert`-Anweisungen absieht, ist die Umsetzung für einen Spielzug einfach nachzuvollziehen:

* Der Spielzug `m`, ein Wert von 0 bis 8, entspricht der Angabe des Indexes eines freien Feldes auf dem eindimensionalen Spielbrett.
* Das Feld wird mit dem Wert der am Zug befindlichen Spielpartei belegt. Anschließend wechselt die Spielpartei.
* Der Spielzug wird im Gedächtnis für den Spielverlauf eingetragen.

```
jshell> t3.move(3)

jshell> t3
t3 ==>
XO.
OX.
X.O
```

Die Methode, um einen Spielzug rückgängig zu machen, liest sich fast wie das Inverse (Umgekehrte) der `move`-Methode. Faktisch entspricht dies auch der Intention: ein ausgeführter Zug wird rückabgewickelt.

```java
    public void undoMove() {
        if (counter == 0) return;
        board[history[--counter]] = 0;
        turn = -turn;
    }
```

```
jshell> t3.undoMove()

jshell> t3
t3 ==>
XO.
.X.
X.O
```

### Der Spielzuggenerator `generateMoves` und die Hilfsmethode `contains`

Der Zuggenerator bei Tic-Tac-Toe ist äußerst simpel: Die freien Felder werden in einem Array eingetragen. Die Größe des Arrays ist vorab bestimmbar. (Ich habe mich hier für die Rückgabe eines `int`-Arrays entschieden, damit man keine Kenntnis von Datentypen wie `ArrayList` haben muss.)

```java
    public int[] generateMoves() {
        int[] moves = new int[board.length - counter];
        for(int i = 0, j = 0; i < board.length; i++)
            if (board[i] == 0) moves[j++] = i;
        return moves;
    }
```

In der aktuellen Spielsituation sind folgende Spielzüge möglich:

```
jshell> t3.generateMoves()
$22 ==> int[4] { 2, 3, 5, 7 }
```

Die Hilfsmethode `contains` dient generell zur Feststellung, ob sich ein Zahlenwert vom Typ `int` in einem `int`-Array befindet. Da diese Methode nicht auf den Kontext des aktuellen Objekts und/oder seiner Instanzvariablen basiert und eine generelle Dienstleistung erbringt, ist diese Methode als Klassenmethode (`static`) deklariert. Da diese Dienstleistung aber eine interne Angelegenheit ist und für das Tic-Tac-Toe ansonsten keine Bedeutung hat, ist die Methode außerdem als `private` deklariert.

```java
    private static boolean contains(int[] numbers, int number) {
        for (int n : numbers)
            if (n == number) return true;
        return false;
    }
```

### Sind drei in Reihe? (`threeInARow`)

Es gibt insgesamt acht Möglichkeiten für "Drei in Reihe": es gibt drei Spalten, drei Zeilen und zwei Diagonalen. Statt diese acht Möglichkeiten durch zahlreiche `if`-Anweisungen zu kodieren, kann man auch eine datenorientierte Lösung realisieren. In dem zweidimensionalen Array `rows` werden die acht Möglichkeiten schlicht notiert. Die sich daraus ergebende Ablauflogik zur Feststellung, ob in der aktuellen Spielsituation drei Spielsteine einer Spielpartei in Reihe sind, ist übersichtlich und einfach nachvollziehbar.

```java
    public boolean threeInARow() {
        int[][] rows = {{0,1,2},{3,4,5},{6,7,8},
                        {0,3,6},{1,4,7},{2,5,8},
                        {0,4,8},{2,4,6}};
        for(int[] row : rows) {
            int sum = board[row[0]] + board[row[1]] + board[row[2]];
            if (Math.abs(sum) == 3) return true;
        }
        return false;
    }
```

```
jshell> t3.threeInARow()
$23 ==> false
```

::: {.callout-tip title="Abbildung von Abläufen in Datenstrukturen"}
Sie sehen in der Methode `threeInARow`, wie umfangreiche Anweisungsstrukturen in Datenstrukturen kodiert werden können. Die Repräsentationsebene der Anweisungsstruktur wird zu Teilen in eine Repräsentationsebene von Datenstrukturen abgebildet. Davon sollten Sie Gebrauch machen, wann immer das möglich ist. Der mit der Datenstrukture einhergehende "Restcode" an Anweisungen ist meist deutlich weniger umfangreich, besser verständlich und weniger anfällig gegen "Tippfehler".
:::

<details>
    <summary>Wenn Sie die Umsetzung der Kodierung von Reihen in einem Array sehen, könnte man auf eine effizientere Variante kommen: Je nachdem wo der letzte Spielstein gesetzt wurde, sind nur zwei, drei oder vier Reihen zu überprüfen. Wie müsste der Programmcode angepasst werden, um das umzusetzen?</summary>
Ich möchte hier nur die Idee skizzieren:

* Für das Feld mit dem Index 0 kommen nur die folgenden Reihen infrage: `{{0,1,2}, {0,4,8}, {0,3,6}}`. Entsprechendes gilt für die anderen Eckfelder.
* Für das Feld mit dem Index 1 sind es die Reihen `{{0,1,2}, {1,4,7}}`. Entsprechendes gilt für die Indizes 3, 5 und 7.
* Für das Feld in der Mitte mit dem Index 4 sind es die Reihen `{{0,4,8}, {2,4,6}, {1,4,7}, {3,4,5}}`

Mit jedem Index ist ein zweidimensionales Feld mit den Reihen zu verbinden. Entsprechend ist ein dreidimensionales Array zu konzipieren:

```java
int[][][] idx2rows = {
    {{0,1,2}, {0,4,8}, {0,3,6}}, // Index 0
    {{0,1,2}, {1,4,7}},          // Index 1
    // usw.
    {{0,4,8}, {2,4,6}, {1,4,7}, {3,4,5}} // Index 4
    // usw.
}
```

Abhängig vom letzten Zug können nun die zu begutachtenden Reihen abgerufen werden:

```java
int[][] rows = idx2rows[history[counter - 1]];
```

Der Rest des Codes, d.h. die `for`-Schleife und das abschließende `return`, bleibt unverändert.
</details>

### Rückgabe des Spielverlaufs (`history`)

Die Variable `history`, die den Spielverlauf erinnert, ist `private` gesetzt und von außen nicht einsehbar. Man könnte eine Methode wie `int[] getHistory()` (oder kürzer `int[] history()`) anlegen, die per `return history` das `int`-Array zurückgibt.

Das wäre ein schwerwiegender Fehler: Sie hätten damit die Referenz auf das Array ausgeliefert, was Außenstehenden beliebige Manipulationen an dem Array erlauben würde. Damit hätten Sie Ihren Programmcode unterwandert und könnten dessen [Integrität](https://de.wikipedia.org/wiki/Integrit%C3%A4tsbedingung) nicht mehr garantieren.

Um die Referenz nicht nach außen zu geben, erzeugen wir eine Kopie des Arrays. Und zwar nicht des ganzen Arrays sondern nur von der benötigten Größe.

```java
    public int[] history() {
        int[] moves = new int[counter];
        for(int i = 0; i < moves.length; i++)
            moves[i] = history[i];
        return moves;
    }
```

```
jshell> t3.history()
$24 ==> int[5] { 0, 1, 4, 8, 6 }
```

<details>
    <summary>Die Klasse `java.util.Arrays` (kurz `Arrays` in der JShell) bietet ein paar interessante Methoden im Umgang mit Arrays an, darunter die `copy`-Methode. Setzen Sie die obige Methode mit `copy` um.</summary>
Sie können den obigen Code damit verkürzen zu:

```java
    public int[] history() {
        return Arrays.copy(history, counter);
    }
```
</details>

::: {.callout-note title="Mit immutablen Datenstrukturen gibt es kein Referenzproblem"}
Eine grundsätzlich andere Lösung zu der Herausforderung, die Datenintegrität durch herausgegebene Referenzen nicht zu verletzen, ist die Verwendung von _immutablen_ (unveränderlichen) Datenstrukturen. Wenn sich nichts an einem Objekt ändern lässt, ist es egal, wenn seine Referenz Dritten zugänglich ist. Daher spricht man bei Immutabilität auch von _referentieller Intransparenz_. Auf die Immutabilität kommen wir in anderen Kontexten wieder zurück.
:::

### Veränderte Außendarstellung `!=` interne Datenrepräsentation (`toggle`)

An der Methode `toggle` möchte ich Ihnen demonstrieren, dass die Außendarstellung (Außenrepräsentation) von Tic-Tac-Toe eine Angelegenheit ist, die unabhängig von der internen Datenrepräsentation des Spiels gepflegt und behandelt werden kann.

Wenn Sie die Spielparteien entschließen, die Symbole der Spielsteine zu tauschen, so dass beispielsweise auch `O` ein Spiel beginnen kann, so hat das überhaupt keinen Einfluss auf die interne Kodierung: dort wird stets der Anfang mit +1 gemacht.

```java
    TicTacToe toggle() {
        char c = symbols[0];
        symbols[0] = symbols[2];
        symbols[2] = c;
        return this;
    }
```

```
jshell> t3
t3 ==>
XO.
.X.
X.O

jshell> t3.toggle()
$26 ==>
OX.
.O.
O.X
```

### Zurück zum Anfang: Koordinaten für die Feldangabe

Kommen wir noch einmal zum Anfang zurück: Verständlicherweise könnte der Bedarf vorliegen, einen Spielzug nicht über einen eindimensionalen Feldindex anzugeben, der zudem mit Null beginnt, sondern über eine zweidimensionale Koordinatenangabe, ähnlich wie beim Schach, siehe @fig-t3koordinatensysteme.

::: {#fig-t3koordinatensysteme layout-ncol=2}

![Zahlenkoordinate: Zuerst wird eine untere Zahl für die Spalte, dann eine der Seitenzahlen für die Zeile angegeben](/KodierungUndRepräsentation/T3KoordinatenV1.png){#fig-t3koordinatenv1 width=80%}

![Buchstabe/Zahl-Koordinate: Zuerst wird der Buchstabe, dann die Zahl angegeben. Auch umgekehrt wäre die Kodierung eindeutig.](/KodierungUndRepräsentation/T3KoordinatenV2.png){#fig-t3koordinatenv2 width=80%}

Zwei mögliche Koordinatensysteme für Tic-Tac-Toe
:::

Diese Koordinatensysteme stellen mögliche Kodierungen dar, die mit der Außendarstellung des Spiels verbunden sind. Statt den Code der Klasse `TicTacToe` dafür "anzufassen", stelle ich eine Klasse `Pos` mit der Klassenmethode `of` bereit, die die Umrechnung vornimmt.

```java
class Pos {
    static int of(int x, int y) {
        assert x >= 1 && x <= 3;
        assert y >= 1 && y <= 3;
        return (3 - y) * 3 + (x - 1);
    }
    static int of(char x, int y) {
        return of(x < 'a' ? x - 'A' + 1 : x - 'a' + 1, y);
    }
}
```

### Testing

An den Tests, die ich mit der `assert`-Anweisung umsetze, möchte ich Ihnen zeigen, dass die `toString`-Methode mit der Ausgabe der Spielsituation bei der Formulierung von Testfällen helfen kann. Hier ein paar Beispiele:

```java
assert new TicTacToe().toString().equals("\n...\n...\n...");
assert new TicTacToe().toggle().toString().equals("\n...\n...\n...");
assert new TicTacToe(0,2).toString().equals("\nX.O\n...\n...");
assert new TicTacToe(7,3,0,2).toString().equals("\nX.O\nO..\n.X.");
assert new TicTacToe(0,3,7,2).toggle().toString().equals("\nO.X\nX..\n.O.");
assert new TicTacToe(0,6,1,7,2).threeInARow();
assert new TicTacToe(0,6,1,7,3,8).threeInARow();
```

Die Testfälle für die Klasse `Pos` arbeiten nicht mit Instanzen und müssen die Klassenmethode `of` unmittelbar testen.

```java
assert Pos.of(1,3) == 0 && Pos.of(2,3) == 1 && Pos.of(3,3) == 2;
assert Pos.of(1,2) == 3 && Pos.of(2,2) == 4 && Pos.of(3,2) == 5;
assert Pos.of(1,1) == 6 && Pos.of(2,1) == 7 && Pos.of(3,1) == 8;
assert Pos.of('a',2) == Pos.of('A',2) && Pos.of('a',2) == Pos.of(1,2);
assert Pos.of('b',1) == Pos.of('B',1) && Pos.of('b',1) == Pos.of(2,1);
assert Pos.of('c',2) == Pos.of('C',2) && Pos.of('c',2) == Pos.of(3,2);
```

## Aufgaben

Ergänzen Sie folgende Methoden zu der Klasse `TicTacToe`:

### Verwende eine `ArrayList` für `history`

Verwenden Sie für `history` eine `ArrayList` statt des `int`-Arrays und verzichten Sie damit auf überflüssig gewordene Variablen und Methoden.

<details>
    <summary>Lösen Sie die Aufgabe, schauen Sie erst dann hier nach, welche Variablen bzw. Methoden infrage kommen.</summary>
* Die `ArrayList` kann dynamisch wachsen und schrumpfen, der `counter` als Füllstandsanzeiger wird hinfällig, die `size()` gibt den Füllstand der `ArrayList` an.
* Die Hilfsmethode `contains` ist überflüssig, `ArrayList` liefert diese Methode mit.
* Wenn die Methode `history` ihren Rückgabetyp `int[]` beibehalten soll, muss sie neu implementiert werden. Aber selbst in der Gestalt von `ArrayList<Integer> history()` hat sie ihre Berechtigung: Es darf nicht einfach `history` zurückgegeben werden, weil damit die durch `private` geschützte Referenz nach außen durchgestochen wird und von außen veränderbar wird. Es muss also eine Kopie der `ArrayList` zurückgegeben werden.
</details>

### Speichern und Laden von Spielständen

Mit der Methode `void save(String fileName)` kann der Spielstand in einer Textdatei gespeichert werden. Die Dateiextension `.txt` wird automatisch zu `fileName` ergänzt. Die Methode `void save()` wählt als Dateinamen `"t3"`. Die Datei enthält die Historie, wobei die Zahlen durch Kommata getrennt sind. Wurde noch kein Spielzug gemacht, wird eine leere Datei angelegt. 

Mit der Methode `TicTacToe load(String fileName)` wird ein Spielstand aus der abgespeicherten Historie rekonstruiert. Mit `TicTacToe load()` wird `t3.txt` geladen.

<details>
    <summary>Warum ist es sinnvoller, die Historie für die Rekonstruktion des Spielstands zu speichern, statt eines Abbilds des tatsächlichen Spielstands?</summary>
Es ist gar nicht so einfach, einen gegebenen Spielstand daraufhin zu überprüfen, ob er eine gültige Spielsituation wiedergibt. Denn die zu ladende Textdatei kann ja auch händisch angelegt worden oder schlicht fehlerhaft sein. Zum Beispiel darf die Summe aller Spielsteine auf dem Brett nur 0 oder +1 sein. Ansonsten hat eine Partei Spielsteine ohne Gegenzug auf dem Spielbrett positioniert. Wesentlich einfacher ist die Rekonstruktion eines Spielstands aus der Historie des Spielverlaufs. Die Spielzüge sind bei Verwendung der `move`-Methode (zusammen mit `generateMoves` und `contains`) sehr leicht auf Gültigkeit zu überprüfen. Wenn die Spielzüge gültig sind, muss es die ergebende Spielsitation ebenso sein. Sie setzen also auf der bereits implementierten Spielmechanik (auch der Gültigkeitsprüfung) auf, statt neue Überlegungen umsetzen zu müssen, ob eine gegebene Spielstellung (a) grundsätzlich gültig ist oder nicht und (b) ob sie überhaupt durch einen realen Spielverlauf so entstanden sein könnte.

::: {.callout-tip title=""}
Wenn Sie bei Spielen wie Tic-Tac-Toe oder Brettspielen wie Schach, Mühle oder Dame den Spielstand speichern wollen, sollten Sie das immer über die Speicherung der bis dahin erfolgten Spielzüge tun. Die Rekonstruktion einer Spielsituation aus dem Spielverlauf ist leichter validierbar (überprüfbar) und sie kann korrumpierte Daten erkennen.
:::
</details>

### Hocheffiziente Kodierungen: Bitboards

Wenn es darum geht, bei Spielen möglichst effizient Spielzüge durchzurechnen (etwa bei der Suche nach einem besten Spielzug, wenn der Computer gegen den Menschen antritt), braucht es sehr ausgeklügelte Kodierungen. In dem Text "[Bitboards and Connect Four](https://github.com/denkspuren/BitboardC4/blob/master/BitboardDesign.md)" erkläre ich ausführlich am Beispiel des Spiels "Vier gewinnt", was Bitboards sind und wie sie funktionieren. In dem Video "[Bitboards für Tic-Tac-Toe](https://www.youtube.com/watch?v=5t5jzkO0t7w)" zeige ich Ihnen die Umsetzung für das Spiel Tic-Tac-Toe. 

::: {.callout-tip title=""}
Es gibt im Bereich der Algorithmen und Datenstrukturen für viele Sachverhalte und Problemstellungen sehr raffinierte, effiziente und gründlich analysierte Kodierungen  -- das ist ein Teil dessen, was die Informatik so reizvoll und interessant macht. Machen Sie es sich zur Angewohnheit, zu dem Thema, das Sie beschäftigt, nach solchen Kodierungen zu recherchieren. Es ist unmöglich, selber auf all das zu kommen, was andere schon erfunden und ergründet haben. Vieles wird Ihnen auch durch Programmbibliotheken bereitgestellt.
:::


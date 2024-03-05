
#### Aufgabe (1a)

>Bemerke, wir haben 6 **verschiedene** Personen, die wir in allen möglichen Anordnungen ablichten lassen wollen. Da keine Person mehrfach auftauchen kann, können wir auf eine **Permutation ohne Wiederholungen** schließen und wenden die Formel unter **Defintion 1.1** an. Wir haben
>$$\begin{align}
> P_{n}=n! \quad \overset{n=6}{\longrightarrow} \quad P_{6} = 6! = 720
>\end{align}
>$$
>Somit sind $720$ Anordnungen möglich

#### Aufgabe (1b)

>Wie in Aufgabe (1a) suchen wir alle möglichen Anordnungen, die durch  ** 3 Paare eineiiger Zwillinge** realisiert werden können. Das Attribut der **eineiigen Zwillinge** deutet an, dass diese auf dem Foto als identisch betrachtet werden können. Um den Sacherverhalt darzustellen wenden wir **Definition 1.3 (Multimenge)** an
>$$\begin{align}
> M = \{ \underbrace{\overbrace{1,1}}^{\text{Paar 1}}_{2-\text{mal}},\underbrace{\overbrace{2,2}}^{\text{Paar 2}}_{2-\text{mal}},\underbrace{\overbrace{3,3}}^{\text{Paar 3}}_{2-\text{mal}} \}
>\end{align}$$
>Unter dieser Darstellung können wir einfach **Definition 1.4** anwenden. Mit 
>$$\begin{align}
> n&=6 \\
> k_{1-3} &= 2
>\end{align}$$
>erhalten wir
>$$\begin{align}
>\binom{n}{k_{1},k_{2}, \ldots, k_{r}}&= \frac{n!}{k_{1}!k_{2}!\dots k_{r}!} \\
> &= \frac{6!}{2!2!2!} \\
> &= \frac{720}{2 \cdot 2 \cdot 2} \\
> &= 90
>\end{align}$$

#### Aufgabe (1c)
> Wir bemerken, dass genau 3 aus 10 gesucht sind. Daher können wir feststellen, dass wir nicht Anordnungen einer Gesamtmenge, sondern Varianten (Variationen) oder auch Kombinationen aus einer **Auswahl** suchen.
>
> Um zwischen **Kombination und Variation** zu unterscheiden, müssen wir uns überlegen ob eine Ordnung in unserer Anordnung sinnbehaftet ist. Da wir in unserer Aufgabe alle Möglichkeiten der ersten 3 Plätze von 10 Teilnehmern darstellen wollen, ist eine Ordnung gegeben. Somit können wir die **Kombination ausschließen**. Da jeder Teilnehmer nur einmal teilnimmt, kann eine Wiederholung ebenfalls ausgeschlossen werden.
> 
> Somit können wir **Definition 1.6** anwenden mit
> $$\begin{align}
> n&=10 \\
> k&=3
>\end{align}$$
>folgende Lösung
> $$\begin{alignat}{3} 
> V_{n}^k &= n(n-1)\dots(n-k+1) &&= n^{\underline{k}} &&= \frac{n!}{(n-k)!}\\
> V_{10}^3 &= 10 \cdot 9 \cdot 8 &&= 10^{\underline{3}} &&= \frac{10!}{(10-3)!}\\
> &&&&&=720
>\end{alignat}$$

#### Aufgabe (1d)

> Auch in dieser Aufgabe suchen wir nicht Anordnungen aus einer Gesamtmenge. Wir können den Sachverhalt wie folgt darstellen. Wir haben Aufgaben 1-10. Jede Aufgabe kann mit einer Antwort $A,B,C$ angegeben werden. Da nur eine der Aufgaben richtig ist, sind die Objekte wohl unterscheidbar und können durch ihre Reihenfolge unterschieden werden. **Für eine Aufgabe haben wir eine Variation ohne Wiederholung** mit
> $$\begin{align}
> n&=3 \\
> k&=1
>\end{align}$$
>und erhalten
>$$\begin{align}
> V^k_{n}&=\frac{3!}{(3-1)!} \\
> &= \frac{6}{2} \\
> &= 3
>\end{align}$$
>Das Ergebnis bestätigt auch die offensichtliche Eingebung, dass wenn man eins aus drei ziehen kann, dass es nur 3 mögliche, verschiedene Ausgänge geben kann.
>
>Da in dem Wissenswettstreit diese Auswahl  10 mal vorgenommen wird, erhalten wir
>$$3^{10}= 59\,049$$
>> Ergänzung für die Anwendung von $3^{10}$:
>> Nehmen wir an wir hätten 2 statt 10 Aufgaben. Wir fixieren für die erste Aufgabe Antwort $A$. So können wir unter der Auswahl von Antwort $A$ in der ersten Aufgabe 3 verschiedene weitere Antworten für die zweite Aufgabe wählen. Also
>> $$AA, AB, AC$$
>> Wenn wir für die erste Aufgabe die Antwort $B$ fixieren, können wir ein ähnliches Verhalten beobachten, also
>> $$BA, BB, BC$$
>> Da für die erste Aufgabe 3 Antworten möglich sind, und jeweils 3 weitere Antworten folgen können, haben wir für zwei Aufgaben 
>> $$\begin{matrix}
>AA & AB & AC \\
>BA &BB & BC \\
>CA & CB & CC
>\end{matrix}$$
>, was einer quadratischen Darstellung gleicht, also $3^2$. Würden wir einen dritten Buchstaben hinzufügen, müssten wir für jede Möglichkeit 3 weitere Möglichkeiten hinzufügen. Da es $3^2$ Möglichkeiten bereits sind, wären es demnach $3^2 \cdot 3 = 3^3$. Daher können wir in der Aufgabe ableiten, dass die Anzahl der Aufgaben, also die Anzahl wie oft wir die Variation durchführen, den Exponenten für die Anzahl der Variationen ergibt.


#### Aufgabe 1(e)
> Wir haben insgesamt 8 Spieler zur Verfügung, wenn wir Spieler 1 mit den verbleibenden 7 Spielern. Paaren wir nun Spieler 2, ist hier nun bereits das Spiel mit Spieler 1 erfasst, also verbleiben für diesen nur noch 6 Spieler. Setzen wir das so fort, verbleiben für Spieler $n$ immer noch $n-1$ weitere Spieler.
>
> Daher sind es
> $$\begin{align}
> \sum_{k=1}^{n-1}k & = \frac{n(n-1)}{2}  \\
>  \sum_{k=1}^7 k &= 21
>\end{align}$$
>
>> Wir haben Gebrauch der Gaußschen Summenformel gemacht, die da lautet
>> $$\sum_{k=1}^n k = \frac{n(n+1)}{2}  $$
>> und statt $n$ haben wir $n-1$.

#### Aufgabe 1(f)
> Zunächst bemerken wir, die 6 Objekte sind nicht unterscheidbar, und somit gibt es keine Reihenfolge, die relevant ist. Daher können wir bereits auf eine Kombination schließen. Da wir eine Wiederholung der nicht unterscheidbaren Elemente erwarten, handelt es sich um eine Kombination mit Wiederholung. Deshalb  verwenden wir Definition 1.18 mit
> $$\begin{align}
> n &= 12 \\
> k &= 6  
>\end{align}$$
>Also haben wir
>$$\begin{align}
>^wC^k_{n} &= \binom{n+k-1}{k} \\
>^wC^6_{12} &= \binom{17}{6}  \\
> &= \frac{17!}{(17-6)!} \\
> &= 8\;910\;720
>\end{align}$$


#### Aufgabe 1(g)
> Da wir eine Auswahl treffen, statt eine Anordnung durchzuführen, spielt die Reihenfolge keine Rolle und wir arbeiten mit der Kombination. Die jeweiligen Kartenkategorien sind durch ihre Zugehörigkeit zu Herz, Pik, Karo und Kreuz unterscheidbar. Wir werden zunächst jeweils die Möglichkeiten die jeweiligen Elemente auszuwählen untersuchen.
> 
> Da jeweils die Damen/Asse/Luschen unterscheidbar sind, nur ihre Reihenfolge keine Rolle spielt. Wir wählen wie folgt aus
> - 2 aus 4 Damen => $n=4$ und $k=2$
> - 1 aus 4 Asse => $n=4$ und $k=1$
> - 2 aus 36 Luschen => $n=36$ und $k=2$
> 
> und erhalten:
> 1. Wahl der Damen
> $$\begin{align}
> C^k_{n} &= \binom{n}{k} = \frac{n!}{n!(n-k)!} \\
> C^2_{4} &= \binom{4}{2} = \frac{4!}{2!\cdot2!} \\
>     &= 6
>\end{align}$$
>2. Wahl der Asse:
>$$\begin{align}
> C^1_{4} &= \binom{4}{1} = \frac{4!}{(4-1)!} \\
> &=4
>\end{align}$$
>3. Wahl der Luschen:
>$$\begin{align}
>  C^2_{36} &= \binom{2}{36} = \frac{36!}{2!(36-2)!} \\
> &= 630
>\end{align}$$
>
>Um die gesamte Möglichkeiten zu erhalten, müssen wir jede der Möglichkeiten mit denen der anderen verknüpfen. Dies ist als das Multiplikationsprinzip bekannt und wie der Name andeutet multiplizieren wir die einzelnen Ergebnisse und erhalten
>$$6 \cdot 4 \cdot 630 = 15\;120$$


#### Aufgabe 1(h)
> Um die Aufgabe effektiv zu lösen, teilen wir die Menge der Ziffern in die, die wir ohne Bedingung anordnen können und diese, die unter Bedingung platziert werden
> - Mit Bedingung: $M_{1} = \{ 1,3,5 \}$
> - Ohne Bedingung: $M_{2} = \{ 1,2,4,6 \}$
>
> Den ersten Schritt können wir unabhängig von der Teilaufgabe durchführen. Für jede Variante, die wir ermitteln, können die Elemente aus $M_2$ (ohne Bedingungen) verschiedenartig angeordnet werden, ohne, dass es unsere Bedingung verletzt. Also erhalten wir eine Permutation für $M_2$ mit $n=4$
> $$\begin{align}
> P_{4} &= 4! \\
>    &= 24
>\end{align}$$
>Nun lösen wir für $M_1$ unter den verschiedenen Teilaufgaben
>1. $(1,3,5)$ werden nebeneinander in gegebener Reihenfolge platziert <br>
>Wir stellen uns eine Reihenfolge der Zahlen aus $M_{2}$ vor, beispielsweise:
>$$\begin{align}
> |\; 4 \; | \; 2 \; | \;1\; | \;6\; |   
>\end{align}$$
>Bemerkt die vertikalen Striche, die als Platzhalter für das Paar $(1,3,5)$ stehen. Wir fragen nun, wieviele Möglichkeiten gibt es dieses Paar dort einzufügen. Genau genommen handelt es sich hier um eine Variation, in der wir einen der Positionen aus 5 wählen. Offensichtlich, auch ohne Berechnungen zu bemühen, sehen wir, dass wir lediglich 5 Möglichkeiten haben.
>$$V_{5}^1 = 5\,$$Nach dem Multiplikationsprinzip multiplizieren wir das Ergebnis mit den Permutationen aus unserer Vorbereitung und erhalten
>$$5 \cdot 24 = 120$$
>2. $\{ 1,3,5 \}$ werden nebeneinander aber in beliebiger Reihenfolge platziert <br>
>Wenn die Reihenfolge beliebig ist, suchen wir die Permutationen unter den 3 gegebenen Elementen. Wir erhalten
>$$P_{3} = 3! = 6$$
>Da diese Bedingung eine Erweiterung der Teilaufgabe 1. ist und für jede Möglichkeit in 1. jede Permutation aus 2. verwendet werden kann, verwenden wir wieder das Multiplikationsprinzip und erhalten
>$$5 \cdot 24 \cdot 6 = 720$$
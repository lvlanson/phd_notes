
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
> Da wir eine Auswahl treffen, statt eine Anordnung durchzuführen, spielt die Reihenfolge keine Rolle und wir arbeiten mit der Kombination. Da hier nach beliebigen 2 Damen und beliebigen 2 Luschen gefragt wird, gehen wir davon aus, dass eine Unterscheidung ebenfalls keine Rolle spielt und wir daher eine Kombination mit Wiederholung haben. Ein Romméblatt hat
> - 4 Damen
> - 4 Asse
> - 36 Luschen
> 
> Wir wählen daher
> - Damen: $^wC_{4}^2 = \binom{4+2-1}{2}=\frac{5!}{(5-2)!} = 20$
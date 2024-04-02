### Klassische Wahrscheinlichkeit
#### Aufgabe (1a)

> Um diese Aufgabe vernünftig zu lösen bedienen wir uns Definition 3.6 und 3.7. Um Definition 3.6 vernünftig anzuwenden, ist die Anzahl der möglichen Elementarereignisse notwendig. Im letzten Seminar haben wir dazu Übungen bereits durchgeführt.
> 
> Wir bemerken, es werden 3 ideale Würfel geworfen. Da die Reihenfolge hierbei keine Rolle spielt, können wir die Elementarereignismenge wie folgt angeben
> $$\begin{align}
> \Omega &= \Big\{ \{a, b, c  \} \;\Big|\; 1 \leq a, b,c \leq 6 \Big\} \\
>   &= \Big\{ \{1, 1, 1\}, \{ 1,1,2 \}, \{ 1,2,2 \}, \dots, \{ 6,6,6 \} \}
>\end{align}$$
>, wobei die innere Menge eine **Multimenge** ist (Definition 1.3). Da Mengen (auch Multimengen) keine Reihenfolge besitzen und wir uns überlegen müssen wieviele Elemente in der Elementarereignismenge $\Omega$ vorhanden sind, verwenden wir unsere kombinatorischen Fertigkeiten. 
>
> Die suchen daher wie wir 3 aus 6 mit Wiederholung wählen können, was die **Kombination mit Wiederholung** ist (Definition 1.18). Wir haben also
> $$\begin{align}
> ^wC_{n}^k &= \binom{n+k-1}{k} \\
> ^wC_{6}^3 &= \binom{6+3-1}{3} \\
>     &= \frac{8!}{3!(8-3)!} \\
>     &= 56
>\end{align}$$
>Laut Definition 3.6 hat jedes einzelne Elementarereignis $\omega_{i}$ nun die Wahrscheinlichkeit
>$$P(\omega_{i}) = \frac{1}{56}$$
>Wir lösen nun die Teilaufgaben mithilfe von Definition 3.7
>1. "Wir würfeln genau eine 6" beschreibt die Ereignismenge $A_{1}$ <br> 
>Hier haben wir in der Ereignismenge alle Ereignisse $A_1$, in der wir genau eine 6 finden. Da die Reihenfolge keine Rolle spielt, suchen wir lediglich alle Kombinationen der anderen zwei Würfel. Daher können wir die 6 als gegeben voraussetzen und suchen für die anderen Würfel die Kombinationen ohne 6. Wir formulieren die Kombination mit Wiederholung 2 aus 5 (ohne die 6), also
>$$\begin{align}
>\lvert A_{1} \rvert &= \,^wC_{n}^k \\
>     &= C_{6}^2 \\
>     &= \binom{5+2-1}{2} \\
>     &= \frac{6!}{2!(6-2)!} \\
>     &= 15
>\end{align}$$
>Nach gegebener Definition errechnet sich die Wahrscheinlichkeit für $P(A_{1})$ nun wie folgt
>$$\begin{align}
> P(A_{1}) &= \frac{\lvert A_{1} \rvert }{\lvert \Omega \rvert }   \\
>      &= \frac{15}{56} \\
>      &\approx 0.268
>\end{align}$$
>> Bemerkung: Wir verwenden hier die Kardinalität $\lvert \cdot \rvert$ der Menge $A_{1}$, also wir Zählen alle Elemente in der Menge. In Definition 3.7 haben wir $$\begin{align}
>> \lvert A \rvert &= n  \\
>> \lvert \Omega \rvert &= m  
>>\end{align}$$
> 1. "Wir würfeln mindestens eine 6" beschreibt die Ereignismenge $A_2$ <br>
> Wir stehen nun vor derselben Aufgabe die Elemente der Ereignismenge $A_2$ zu zählen. Da wir in jedem Fall eine 6 haben, interessieren uns wieder nur die anderen 2 Würfel und wir einigen uns darauf, einen Würfel mit einer 6 zu fixieren. Jetzt können wir für die 2 verbleibenden würfel alle beliebigen Kombinationen angeben, also wir wählen 2 aus 6 mit Wiederholung
> $$\begin{align}
> \lvert A_{2} \rvert &= \;^wC^k_{n}  \\
>        &= \,^wC^2_{6} \\
>        &= \binom{6+2-1}{2} \\
>     &= \frac{7!}{2!(7-2)!} \\
>     &= 21
>\end{align}$$
> Wie in der Aufgabe zuvor können wir jetzt die Wahrscheinlichkeit berechnen
> $$\begin{align}
> P(A_{2}) &= \frac{\lvert A_{2} \rvert}{\lvert \Omega \rvert } \\
>      &= \frac{21}{56}\\
>     &=0.375
>\end{align}$$

#### Aufgabe (1b)
> WIe in der Aufgabe zuvor sind wir mit dem Zählen der Elementarereignismenge $\Omega$ und der Ereignismenge $A$ konfrontiert. 
> ###### Elementarereignismenge
> Da die letzten 3 Ziffern in einer Ordnung stehen und wir aus 10 verschiedenen anordnen können, handelt es sich hierbei eine Variation. Weiterhin wissen wir, dass die Ziffern unterschiedlich sind, deshalb kann es hier keine Wiederholungen geben. Wir erhalten daher
> $$\begin{align}
> \lvert \Omega \rvert &= \frac{n!}{(n-k)!} & \\
>       &= \frac{10!}{7!} = 720
>\end{align}$$
> Da nur eine Telefonnummer die richtige ist, ist für die Ereignismenge die Anzahl gegeben als
> $$\lvert A \rvert = 1 $$
> Wir erhalten die Wahrscheinlichkeit
> $$\begin{align}
> P(A) &= \frac{\lvert A \rvert}{\lvert \Omega \rvert }  \\
> &= \frac{1}{720} \\
> &\approx 0.0014
>\end{align}$$

#### Aufgabe (1c)
> Die Anzahl der Elementarereignisse lässt sich hier leicht bestimmen, da wir genau eine Karte von 52 ziehen, also haben wir genau 52 verschiedene Elementarereignisse
> $$\lvert \Omega \rvert = 52 $$
> Wir beschreiben ab jetzt alle Ereignismengen mit $A_i$
> 1. "Die gezogene Karte ist eine Karokarte" beschreibt $A_1$ <br>
> Wir haben genau $$\lvert A_{1} \rvert = \frac{52}{4} = 13$$ Karokarten, also können wir die Wahrscheinlichkeit angeben
> $$\begin{align}
> P(A_{1}) &= \frac{13}{52}  \\
> &= 0.25
>\end{align}$$
>2. "Die gezogene Karte ist Bube, Dame oder König" beschreibt $A_2$ <br>
>Wir haben für jede der 4 Farben für jede dieser 3 Karten, daher können wir die Anzahl der Elementarereignisse angeben als
>$$\lvert A_{2} \rvert  = 12$$
>und die Wahrscheinlichkeit
>$$\begin{align}
> P(A_{2}) &= \frac{12}{52}  \\
> &\approx 0.231
\end{align}$$
>3. "Die gezogene Karte ist eine Karokarte mit Bild (Bube, Dame, König)" beschreibt $A_{3}$ <br>
>Es gibt unter den gegebenen Bedingungen genau 3 Karten, also
>$$\lvert A_{3} \rvert = 3 $$
>Also geben wir die Wahrscheinlichkeit an als
>$$\begin{align}
> P(A_{3}) &= \frac{3}{52} \\
>      &\approx 0.058
>\end{align}$$

### Unabhängigkeit zufälliger Ereignisse
#### Aufgabe (2)

> Um festzustellen, ob Ereignisse unabhängig sind, verwenden wir Definition 3.23 und 3.24. Um diese ordentlich zu verwenden ist es notwendig, dass wir die entsprechenden Mengen konstruieren, die wir auf Unabhängigkeit prüfen wollen. Unser Experiment wurd durch den Wurf einer idealen Münze beschrieben. Daher kodieren wir
> $$\begin{align}
> K &\;\widehat{=} \text{ Kopf} \\
> Z &\; \widehat{=} \text{ Zahl}
>\end{align}$$
>Wir bemerken zuvor, dass $$\begin{align}
> \lvert \Omega \rvert&=P_{3}\\ &= 2^3 =8
>\end{align}$$
> 1. $A$-“gleiche Seiten bei den beiden letzten Würfen.“
> $$A = \{ (K,K,K), (Z,K,K), (K,Z,Z), (Z,Z,Z) \}$$
> 2. $B$-“gleiche Seiten beim 1. und 3. Wurf“
> $$B= \{ (K,Z,K), (K,K,K), (Z,K,Z), (Z,Z,Z) \}$$
> 3. $C$-“gleiche Seiten bei den ersten beiden Würfen“
> $$C= \{ (K,K,Z), (K,K,K), (Z,Z,K), (Z,Z,Z) \}$$
> Nun können wir die Definition 3.19 anwenden
> ######
> 1. Teilaufgabe: Paarweise Lineare Unabhängigkeit (Definition 3.23)
> $$\begin{align}
> P(A \cap B) &= P\Big(\{ (K,K,K), (Z,Z,Z) \}\Big) \\
> &= \frac{2}{8} \\
> &= 0.25 \\
> P(A)P(B) &= \frac{4}{8} \cdot \frac{4}{8} \\
> &=0.25 \\
> &\Rightarrow A \text{ und } B\text{ Linear Unabhängig} \\
> P(A \cap C) &= P\Big(\{ (K,K,K), (Z,Z,Z) \}\Big) \\ 
> &=\frac{2}{8} \\
> &= 0.25 \\
> P(A)P(C) &= 0.25 \\
> &\Rightarrow A \text{ und } C\text{  Unabhängig} \\ 
> P(A \cap C) &= P\Big(\{ (K,K,K), (Z,Z,Z) \}\Big) \\ 
> &=\frac{2}{8} \\
> &= 0.25 \\
> P(A)P(C) &= 0.25 \\
> &\Rightarrow B \text{ und } C\text{ Unabhängig} \\
>\end{align}$$
>Demzufolge sind $A,B,C$ paarweise unabhängig
>2. Teilaufgabe:  Vollständige Unabhängigkeit
>Da wir für $i=2$ in der paarweise Unabhängigkeit alle Varianten schon geprüft haben, folgt nun die Unabhängigkeit über alle Mengen
>$$\begin{align}
> P\left( \bigcap_{k=1}^m A_{k} \right) &= P\Big(\{ (K,K,K), (Z,Z,Z) \}\Big) \\
> &= 0.25 \\
>\prod_{k=1}^m P(A_{k}) &= \left( \frac{1}{2} \right)^3 \\
>            &= 0.125
>\end{align}$$
>Demzufolge sind $A,B,C$ **in ihrer Gesamtheit nicht unbhängig**

### Bedingte Wahrscheinlichkeit
#### Aufgabe (3)
> In dieser Aufgabe werden wir die Erkenntnisse zu bedingter Wahrscheinlichkeit benötigen. Wir strukturieren zunächst die Informationen, die uns in der Aufgabe zur Verfügung stehen.
> Wir formulieren folgende Szenarien
> - Eine Person wird zufällig gewählt, handelt es sich dabei um einen Mann oder eine Frau?
> => Ereignis $F$ kennzeichnet es ist **eine Frau**
> => Ereignis $\lnot F$ kennzeichnet es ist **ein Mann**
> - Eine Person wird zufällig gewählt, ist die Person farbenblind?
> => Ereignis $B$ kennzeichnet die Person ist **farbenblind**
> => Ereignis $\lnot B$ kennzeichnet die Person ist **nicht farbenblind**
>
>Wir haben folgende Wahrscheinlichkeiten gegeben:
>$$\begin{align}
> P(F) &= 0.5 \\
> P(M) &= 0.5\\
> P(B\;|\;F) &= \frac{2}{1000}  \\
>    &= 0.002 \\
> P(B\;|\;M) &= \frac{5}{100} \\
> &= 0.05
>\end{align}$$
> Es ist gefragt unter der Bedingung, dass eine Person farbenblind ist, wie hoch ist die Wahrscheinlichkeit, dass diese ein Mann ist. Wir können dies mathematisch wie folgt darstellen
> $$P(M\;|\;B)$$
> Was uns fehlt, um die Aufgabe zu lösen ist die Wahrscheinlichkeit $P(B)$. Diese erhalten wir, indem wir den **Satz von der Totalen Wahrscheinlichkeit (3.28)** anwenden.
> $$\begin{align}
> P(B) &= \sum_{i=1}^n P(B\;|\;A_{i})P(A_{i}) \\
> P(B) &=P(B\;|\;F)\cdot P(F) + P(B\;|\;M) \cdot P(M) \\
>      &= 0.002 \cdot 0.5 + 0.05 \cdot 0.5 \\
>      &= 0.026
>\end{align}$$
> Jetzt können wir lösen, indem wir uns Satz 3.16 bedienen, der sagt
> $$\begin{align}
>P(A\;|\;B) &=\frac{P(A)}{P(B)}P(B\;|\;A)
>\end{align}$$
>Wir setzen entsprechend ein und erhalten
>$$\begin{align}
>P(M\;|\;B) &=\frac{P(M)}{P(B)}P(B\;|\;M) \\
>   &= \frac{0.5}{0.026} \cdot 0.05 \\
> &= 0.962
>\end{align}$$


#### Aufgabe (4)
> Wir verfahren wie in der Aufgabe zuvor und strukturieren zunächst das gegebene Wissen. Wir bezeichnen
> - $T$ - ist ein Treffer
> - $\lnot T$ -  Ist kein Treffer
> - $G_{i}$ - wählt Gewehr $i$ aus
Wir halten folgende Wahrscheinlichkeiten fest
> $$\begin{align}
> P(T\;|\;G_{1})&= 0.5 \\
> P(T\;|\;G_{2})&= 0.6 \\
> P(T\;|\;G_{3})&= 0.7 \\
> P(T\;|\;G_{4})&= 0.8 \\
> P(T\;|\;G_{5})&= 0.9 \\
> P(G_{i}) &= \frac{1}{5} =0.2 \qquad 1\leq i \leq 5
>\end{align}$$
> 1. Teilaufgabe: <br>
>  Wir suchen $$P(T)$$
>  Schauen wir die gegebenen Größen an lässt sich die Aufgabe mit dem **Satz von der Totalen Wahrscheinlichkeit (3.28)** lösen, also
>  $$\begin{align}
> P(T) &= \sum_{i=1}^5 P(T\;|\;G_{1}) \cdot P(G_{1}) \\
>  &=0.5 \cdot 0.2 + 0.6 \cdot 0.2 + 0.7 \cdot 0.2 + 0.8 \cdot 0.2 +  0.9 \cdot 0.2 \\
> &= 0.2 \cdot (0.5 + 0.6 + 0.7 + 0.8 + 0.9) \\
> &= 0.7
>\end{align}$$
>2. Teilaufgabe: <br>
>Wir suchen
>$$P(G_{5}\;|\;T)$$
>Dazu können wir Satz 3.16 verwenden und erhalten
>$$\begin{align}
> P(G_{5}\;|\;T)&= \frac{P(G_{5})}{P(T)} \cdot P(T\;|\;G_{5})\\
> &= \frac{0.2}{0.7}\cdot 0.9 \\
> &\approx 0.257
>\end{align}$$

#### Aufgabe (5)
> Wir folgen derselben Prozedur wie in den 2 vorangegangenen Aufgaben und kennzeichnen
> - $E$ - Tuberkulose wird erkannt
> - $\lnot E$ - Tuberkulose wird nicht erkannt
> - $K$ - ist an Tuberkulose erkrankt
> - $\lnot K$ - ist nicht an Tuberkulose erkrankt
> 
> Wir fassen die gegebenen Wahrscheinlichkeiten zusammen
> $$\begin{align}
> P(E\;|\;K) &= 0.9 \\
> P(E\;|\;\lnot K) &= 0.01  \\
> P(K) &= 0.001 \\
> P(\lnot K) &= 0.999
>\end{align}$$
>Gesucht wird
>$$\begin{align}
> P(K\;|\;E) 
>\end{align}$$
>Um die gesuchte Größe mit **Satz 3.16** zu finden, benötigen wir $P(E)$. Dies können wir mit dem **Satz von der Totalen Wahrscheinlichkeit (3.28)** finden, also
>$$\begin{align}
> P(E) &= P(E\;|\;K) P(K) + P(E\;|\;\lnot K)P(\lnot K) \\
> &= 0.9 \cdot 0.001 + 0.01 \cdot 0.999 \\
> &= 0.01089
>\end{align}$$
>Letztlich lösen wir mit **Satz 3.16**, also
>$$\begin{align}
> P(K\;|\;E) &= \frac{P(K)}{P(E)} \cdot P(E\;|\;K) \\
> &= \frac{0.001}{0.01089} \cdot 0.9 \\
> &= 0.0826
>\end{align}$$
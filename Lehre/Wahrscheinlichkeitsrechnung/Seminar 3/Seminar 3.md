>[!question]
> 1. Definitionen Verteilung: $p_{i} = p_{k}$?
> 2. Aufgabe 5

>[!def]- Definitionen
>>[!def] Definition Binomialverteilung (4.34)
>> Die Zufallsgröße $X$ heißt binomialverteilt mit den Parametern
>> - $n$ - Gesamtanzahl an Versuchen mit $n \in \mathbb{N}_{0}$
>> - $k$ - Anzahl für Ereignis $A$ eintritt mit $k \leq n$ 
>> - $p$ - Wahrscheinlichkeit, dass Ereignis $A$ eintritt mit $P(A) = p$ 
>> - $(n-k)$ - Anzahl für Ereignis $\overline{A}$ eintritt
>> - $(1-p)$ - Wahrscheinlichkeit, dass Ereignis $P(\overline{A})=(1-p)$ eintritt
>> - $\binom{n}{k}$ - Möglichkeiten die günstigen Ereignisse $A$ für $k$ aus $n$ zu konstruieren
>> 
>> wenn für das Ereignis $A$, welches $k$-mal eintritt, gilt
>> $$p_{k} = P(X=k) = \binom{n}{k}p^k(1-p)^{n-k}$$
>
>>[!def] Definition Verteilungsfunktion Binomialverteilung (4.35)
>>Die Verteilungsfunktion binomialverteilter Zufallsgrößen ist definiert als
>>$$F_{X}(x) = P(X \leq x) = \sum_{k=0}^x \binom{n}{k}p^k(1-p)^{n-k}$$
>
>>[!def] Definition Poissonverteilung (4.38)
>>Die Zufallsgröße $X$ heißt poissonverteilt mit dem Parameter 
>>- $\lambda$ - Anzahl an zu erwartenden Ereignissen mit $\lambda = n\cdot p$
>>- $k$ - das Ereignis $A$ tritt $k$ mal ein in unabhängig wiederkehrenden Intervallen
>> 
>> wenn für die Einzelwahrscheinlichkeiten gilt
>>$$p_{k}= P(X=k) = \frac{\lambda^k}{k!}e^{-\lambda}$$
>
>>[!def] Definition Hypergeometrische Verteilung (4.45)
>>Die Zufallsgröße $X$ heißt hypergeometrisch verteilt mit den Parametern 
>> - $N$ - Anzahl an Objekten ingesamt
>> - $M$ - Anzahl an Objekten, die von Interesse sind, wobei die $M$ in $N$ enthalten sind, also $M \leq N$
>> - $n$ - Anzahl an Objekten, die wir insgesamt aus allen Objekten ziehen
>> - $k$ - Anzahl an Objekten, die wir aus den Objekten von Interesse ziehen, sodass $k \leq n$
>>
>>wenn für die Einzelwahrscheinlichkeiten gilt
>>$$p_{k} = P(X=k) = \frac{\binom{M}{k}\binom{N-M}{n-k}}{\binom{N}{n}}$$


>[!example] Aufgabe (1)
>Bei einer Qualitätskontrolle hat man mit einem Ausschuss von 5% zu rechnen. Berechnen Sie die Wahrscheinlichkeit dafür, dass...
>>[!note]- Wir erkennen eine Binomialverteilung
>>- $A$ - Objekt Ausschuss
>>- $\overline{A}$ -  Objekt kein Ausschuss
>>- $P(A) = 0.05$
>>- $P(\overline{A}) = 0.95$
>>- Zufallsvariable $X$ - Häufigkeit des Eintretens von Ereignis $A$
>>
>1. unter 10 Artikeln kein Ausschuss ist
>
>>[!example]- Lösung
>> Wir erfassen
>> $$\begin{align}
>> X = k &= 0 \\
>> n&=10
>>\end{align}$$
>>Wir lösen mit der Binomialverteilung
>>$$\begin{align}
>> p_{k} = P(X=k) &= \binom{n}{k}p^k(1-p)^{n-k}
>>\end{align}$$
>>und setzen ein
>>$$\begin{align}
>> p_{0}= P(X=0) &= \underbrace{ \binom{10}{0} }_{ =1 }\cdot\underbrace{ 0.05^0 }_{ =1 } \cdot 0.95^{10} \\
>> &= 0.95^{10} \\
>> &= 0.598736939 \tag*{$\checkmark$}
>>\end{align}$$
>
>2. unter 20 Artikeln höchstens ein Artikel defek ist.
>
>>[!example]- Lösung
>> Wir erfassen
>> $$\begin{align}
>> n &= 20 \\
>> k &\in \{ 0,1 \} 
>>\end{align}$$
>> und lösen wieder mit der Binomialverteilung
>> $$\begin{align}
>> p_{0,1} &= P(X \leq 1) \\
>>      &= \sum_{i=0}^1 \binom{20}{i} \cdot 0.05^i \cdot 0.95^{n-i}  \\
>>      &= \binom{20}{0}\cdot 0.05^0 \cdot 0.95^{20} + \binom{20}{1} \cdot 0.05^1 \cdot 0.95^{19} \\
>>      &= 0.95^{20} + 20 \cdot 0.05 \cdot 0.95^{19} \\
>>      &= 0,735839525 \tag*{$\checkmark$}
>>\end{align}$$

>[!example] Aufgabe (2)
>Eine Seminargruppe besteht aus 12 Studenten. Jeder Student besucht mit der Wahrscheinlichkeit $p=0.6$ die Seminare. Mit welcher Wahrscheinlichkeit sind wenigstens $\frac{2}{3}$ der Studenten zum Seminar anwesend?
>
>>[!example]- Lösung
>>>[!note] Wir erkennen die Binomialverteilung
>>> - $\overline{A}$ - Anwesenheit im Seminar
>>> - $A$ - Abwesenheit vom Seminar
>>> - $P(\overline{A})= 0.6$
>>> - $P(A) = 0.4$
>>> - $X = k$ - Zufallsvariable für Anzahl der anwesenden Studenten
>>> - $n=12$ - Anzahl der Studenten gesamt
>>
>>Wir suchen, dass mindestens $\frac{2}{3}$ der Studenten anwesend sind, also dass höchstens $\frac{1}{3}$ der Studenten abwesend sind. Die Gesamtanzahl der Studenten sind $n=12$, also können wir $k$ bestimmen und erhalten
>>$$k = \frac{1}{3}n = 4$$
>> Demnach können wir die Wahrscheinlichkeit mit der **Binomialverteilung** berechnen und erhalten
>> $$\begin{align}
>> p_{[0,4]} &= P(X \leq 4)  \\
>> &= \sum_{k=0}^4 \binom{12}{k}\cdot 0.4^k \cdot 0.6^{n-k} \\
>> &= 0.43817822208  \tag*{$\checkmark$}
>>\end{align}$$
>>>[!note]
>>> Alternativ kann man berechnen (Folgerung aus **Eigenschaften der Verteilung einer Zufallsgröße**)
>>> $$P(X  \geq 8) = P(\overline{X <8}) = P(\overline{X \leq7}) = 1 - P(X \leq 7) \tag*{$\checkmark$}$$


>[!example] Aufgabe (3)
>Die Wahrscheinlichkeit, dass ein Brennelement in einem Kernreaktor den Bedingungen einer Qualitätsprüfung nicht genügt, beträgt $0,0002$. Man ermittle die Wahrscheinlichkeit, dass...
>>[!note]- Wir erkennen die Binomialverteilung
>> und erfassen
>> - $A$ - genügt Qualitätsprüfung
>> - $\overline{A}$ - genügt Qualitätsprüfung nicht
>> - $P(A) = 0.0002$
>> - $P(\overline{A}) = 0.9998$
>
>>[!note] Alternativ geht auch Poissonverteilung mit $n \cdot p = \lambda$
>
>1. höchstens 2 von 5000 dieser Brennelemente die Qualitätsbedingungen nicht erfüllt.
>
>>[!example]- Lösung 
>>Wir haben $n=5000$ und $0 \leq k \leq 2$
>> $$\begin{align}
>> p_{[0,2]} &= P(X \leq 2) \\
>> &= \sum_{k=0}^2 \binom{5000}{k}\cdot 0.0002^k \cdot 0.9998^{5000-k} \\
>> &= 0.919717000274 \tag*{$\checkmark$}
>>\end{align}$$
>
>2. genau 1 von 1000 dieser Brennelemente die Qualitätsbedingungen nicht erfüllt.
>
>>[!example]- Lösung 
>>Wir haben $n=1000$ und $k=1$
>>$$\begin{align}
>> p_{1} &= P(X = 1) \\
>>  &= \binom{1000}{1} \cdot 0.0002^1 \cdot 0.9998^{999} \\
>>  &= 0.163775630415 \tag*{$\checkmark$}
>>\end{align}$$ 
>
>3. keines von 100 dieser Brennelemente die Qualitätsbedingungen nicht erfüllt.
>
>>[!example]- Lösung
>>Wir haben $n=100$ und $k=0$
>>$$\begin{align}
>> p_{0} &= \binom{100}{0}0.0002^0 \cdot 0.9998^{100} \\
>> &= 0.98019671265 \tag*{$\checkmark$}
>>\end{align}$$

>[!example] Aufgabe (4)
>An einer Tankstelle kommen zwischen 16:00 und 18:00 Uhr durchschnittlich 4 Fahrzeuge pro Minute an. Die Anzahl der in einer Minute ankommenden Fahrzeuge sei poissonverteilt. Bestimmen Sie die Wahrscheinlichkeit, dass
>
>>[!note] Gegeben ist die Poissonverteilung
>>Wir erfassen die Größen
>>- $A$ - Fahrzeug erscheint zwischen 16:00 und 18:00 Uhr
>>- $\lambda = 4$
>
>1. kein Fahrzeug ankommt.
>
>>[!example]- Lösung
>>Wir haben $k=0$ und erhalten mit der Poissonverteilung
>>$$p_{k} = P(X= k)= \frac{\lambda^k}{k!}e^{-\lambda}$$
>>und setzen ein
>>$$\begin{align}
>> p_{0} &= P(X=0) \\
>> &= \frac{4^0}{0!}e^{-4} \\
>> &=0.018315639 \tag*{$\checkmark$}
>>\end{align}$$
>>
>
>2. genau ein Fahrzeug ankommt 
>
>>[!example]- Lösung
>>Wir haben $k=1$
>>$$\begin{align}
>> p_{1} &= P(X=1) \\
>> &= \frac{4^1}{1!}e^{-4} \\
>> &= 0.073262556 \tag*{$\checkmark$}
>>\end{align}$$
>
>3. genau zwei Fahrzeuge ankommen
>
>>[!example]- Lösung
>> Wir haben $k = 2$
>> $$\begin{align}
>> p_{2} &= P(X=2) \\
>> &= \frac{4^2}{2!}e^{-4} \\
>> &= 0.146525111 \tag*{$\checkmark$}
>> \end{align}$$
>
>4. mindestens 3 Fahrzeuge ankommen
>
>>[!example]- Lösung
>> Wir haben $3 \leq k \leq 4$ und formulieren über das Gegenereignis
>> $$\begin{align}
>> p_{[3,4]} &= P(3 \leq X \leq 4)  \\
>> &= P(3 \leq X ) \tag{Beschränkt mit 4}\\
>> &= 1 - P(\overline{3 \leq X}) \\
>> &= 1 - P(X < 3) \\
>> &= 1 - P(X \leq 2) \\
>> &= 1 - \sum_{k=0}^2 \frac{4^k}{k!}e^{-4} \\
>> &= 0.761896694446 \tag*{$\checkmark$}
>>\end{align}$$

>[!example] Aufgabe
>Von 100 Losen gewinnt jedes fünfte Los. Es werden 3 Lose gezogen. Wie groß ist die Wahrscheinlichkeit mindestens einen Gewinn zu erhalten? Verwenden Sie die hypergeometrische Verteilung und die Binomialverteilung.
>>[!example]- Lösung Hypergeometrische Verteilung ????
>>Wir erfassen die Parameter
>> - $N = 100$ Lose insgesamt
>> - $M=5$ Gewinnlose von $100$
>> - $n=3$ Lose werden gezogen 
>> - $k \in[1,3]$ Gewinnlose werden gesucht
>>
>> Wir verwenden die Definition
>> $$p_{k} = P(X=k) = \frac{\binom{M}{k}\binom{N-M}{n-k}}{\binom{N}{n}}$$
>> Wir suchen
>> $$P(1\leq X\leq 3)$$
>> Da durch $n=3$ die gesuchte Größe ohnehin beschränkt ist, können wir schreiben
>> $$P(1 \leq X)$$
>> Wir berechnen wieder über das Gegenereignis
>> $$\begin{align}
>> P(1 \leq X) &= 1 - P(\overline{1 \leq X}) \\
>> &= 1 - P(X < 1)  \\
>> &= 1 - P(X = 0) \tag{k=0}\\
>> &= 1 - \frac{\binom{5}{0}\binom{85}{3}}{\binom{90}{3}} \\
>> &= 0.159261150834
>>\end{align}$$
>
>>[!example]- Lösung Binomialverteilung ???
>>Wir erfassen die Parameter
>> - $A$ -  Ereignis ein Gewinn zu ziehen
>> - $\overline{A}$ - Ereignis keinen Gewinn zu ziehen
>> - $n=3$ Lose werden gezogen
>> - $k \in [1,3]$ Gewinne werden gesucht
>> - $p = P(A) =\frac{5}{100}= \frac{1}{20}$
>>
>>Wir verwenden die Binomialdistribution und das Gegenereignis
>>$$\begin{align}
>> P(1\leq X \leq 3) &= P(1 \leq X) \\
>> &= 1 -P(\overline{1 \leq X}) \\
>> &= 1 - P(X < 1) \\
>> &= 1 - P(X = 0) \\
>> &= 1 - \left( \binom{3}{0} \left( \frac{1}{20} \right)^0 \left( \frac{4}{20} \right)^3 \right) \\
>> &= 0.142625
>>\end{align}$$

>[!example] Aufgabe 
>Gegeben seien die Einzelwahrscheinlichkeiten einer Zufallsgröße $X$.
>
>| $i$   | $-3$   | $-2$  | $-1$  | $1$   | $2$   | $4$   | $5$   |
>| --- | ---- | --- | --- | --- | --- | --- | --- |
>| $p_i$ | $0.05$ | $0.1$ | $0.2$ | $0.4$ | $0.1$ | $0.1$ | $0.05$    |
>
>1. Bestimmen Sie die zugehörige Verteilungsfunktion
>
>>[!example] Lösung
>
>2. $P(-2 \leq X < 2)$
>
>>[!example] Lösung  
>
>3. $P(-2 \leq X \leq 2)$
>
>>[!example] Lösung  
>
>4. $P(X>3)$
>
>>[!example] Lösung  
>
>5. $F(-1)$
>
>>[!example] Lösung  
>
>6. $F(5)$
>
>>[!example] Lösung  
>
>7. $E(X)$
>
>>[!example] Lösung  
>
>8. $D^2(X)$
>
>>[!example] Lösung  

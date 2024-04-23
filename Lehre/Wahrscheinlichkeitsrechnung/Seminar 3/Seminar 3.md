>[!def]- Definitionen Zufallsgrößen
>>[!def] Definition Zufallsvariable $X$ (4.3)
>> Eine Zufallsgröße $X$ mit $X: \Omega \to \mathbb{R}$ ist eine Abbildung, die jedem Elementarereignis $\omega \in \Omega$ eine reelle Zahl $x = X(\omega )$ zuordnet.
>
>>[!def] Definition Verteilungsfunktion (4.4)
>> Die Funktion $F_{X}(x):= P(X \leq x) = P\Big(\{ \omega\; | X(\omega) \leq x \}\Big)$ heißt Verteilungsfunktion der Zufallsgröße $X$.
>
>>[!property]  Eigenschaften der Verteilung von Zufallsgrößen
>>1. Definitionsbereich von $F_{X}(x)$ ist $- \infty < x < \infty$
>>2. $0 \leq F_{X}(x) \leq 1$ wegen der Normiertheit von $P$
>>3. $F_{X}(x)$ ist monoton wachsend
>>4. $F_{X}(x)$ ist rechtsseitig stetig $\lim_{ h \to 0 }F_{X}(x+h)=F(X)\; \forall x \in \mathbb{R}$ und $h>0$
>
>>[!property] Folgerungen aus den Eigenschaften der Verteilungsfunktion
>>1. $P(X>x) = 1 - P(x \leq X)$
>>2. $P(a < X \leq b) = F_{X}(b)-F_{X}(a)$
>
>>[!def] Definition Diskrete Zufallsgröße (4.11)
>>Eine diskrete Zufallsgröße nimmt endlich oder abzählbar unendlich viele Realisierungen an.
>
>>[!def] Definition Einzelwahrscheinlichkeiten von Zufallsgrößen (4.13)
>>Die Einzelwahrscheinlichkeiten sind die Wahrscheinlichkeiten, mit denen die Zufallsgröße ihre Werte $i$ annimmt:
>>$$p_{i}= P\Big(\{ \omega \in \Omega: X(\omega)= i \}\Big) \;\; i \in \mathbb{N}_{0}$$
>>oder kurz 
>>$$p_{i} = P(X=i) \;\; i \in \mathbb{N}_{0}$$
>
>>[!def] Definition Verteilung von Zufallsgrößen (4.14)
>>
>>Die Verteilung einer diskreten Zufallsgröße ist definiert durch $$F_{X}(x)=P(X \leq x) = \sum_{i=1}^{i \leq x} p_{i} \;\; \forall \in \mathbb{R}$$
>>$$p_{i} = P(\{ \omega \in \Omega : X(\omega) = i \}) \; \; i \in \mathbb{N}_{0}$$
>
>>[!def] Definition Erwartungswert (4.16)
>>Für eine diskrete Zufallsgröße mit den Einzelwahrscheinlichkeiten $p_{i}$ ist der Erwartungswert definiert als
>>$$\mu = E(X):= \sum_{i} i\cdot  p_{i}$$ 
>
>>[!def] Definition Varianz (4.23)
>>Für eine diskrete Zufallsgröße mit den Einzelwahrscheinlichkeiten $p_{i}$ ist die Varianz (Streuung, Dispersion) definiert als
>>$$\sigma^2 = D^2(X) = E\Big((X- \mu)^2\Big) $$
>
>>[!theorem] Satz Berechnung Varianz (4.24)
>>$$\begin{align}
>> D^2(X) = E(X^2)- E(X)^2
>>\end{align}$$

>[!def] Definitionen Verteilungsfunktionen
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
>>- $\lambda$ - Anzahl an zu erwartenden Ereignissen mit $\lambda = n\cdot p$ (Erwartungswert)
>>- $k$ - das Ereignis $A$ tritt $k$ mal ein in unabhängig wiederkehrenden Intervallen
>> 
>> wenn für die Einzelwahrscheinlichkeiten gilt
>>$$p_{k}= P(X=k) = \frac{\lambda^k}{k!}e^{-\lambda}$$
>>>[!remark]
>>>> Faustregel aus Skript S.53
>>>> $$\begin{align}
>>>> np &<10 \\
>>>> n &>1500 \cdot p
>>>>\end{align}$$
>>>
>>>> Faustregel aus Uniskript online
>>>> $$\begin{align}
>>>> p &<< 0.05 \\
>>>> n &>> 10
>>>>\end{align}$$
>
>>[!def] Definition Hypergeometrische Verteilung (4.45)
>>Die Zufallsgröße $X$ heißt hypergeometrisch verteilt mit den Parametern 
>> - $N$ - Anzahl an Objekten insgesamt
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
>> &= 0.598736939 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. unter 20 Artikeln höchstens ein Artikel defekt ist.
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
>>      &= 0,735839525 \tag*{$\blacktriangleleft$}
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
>> &= 0.43817822208  \tag*{$\blacktriangleleft$}
>>\end{align}$$
>>>[!note]
>>> Alternativ kann man berechnen (Folgerung aus **Eigenschaften der Verteilung einer Zufallsgröße**)
>>> $$P(X  \geq 8) = P(\overline{X <8}) = P(\overline{X \leq7}) = 1 - P(X \leq 7) \tag*{$\checkmark$}$$


>[!example] Aufgabe (3)
>Die Wahrscheinlichkeit, dass ein Brennelement in einem Kernreaktor den Bedingungen einer Qualitätsprüfung nicht genügt, beträgt $0.0002$. Man ermittle die Wahrscheinlichkeit, dass...
>
>>[!note]- WIr erkennen die Poissonverteilung
>> Wir sehen, dass die Wahrscheinlichkeit unsere Bedingung für die Poissonverteilung erfüllt
>> $$0 < p < 0.5$$
>> und in den Teilaufgaben ist die Anzahl der Versuche sehr hoch. Wir erfassen daher
>> $$p = 0.0002$$
>
>1. höchstens 2 von 5000 dieser Brennelemente die Qualitätsbedingungen nicht erfüllt.
>
>>[!example]- Lösung 
>>Wir haben $n=5000$ und $0 \leq k \leq 2$. Wir berechnen
>>$$\begin{align}
>> \lambda &= n \cdot p \\
>> &= 5000 \cdot 0.0002 \\
>> &= 1
>>\end{align}$$ 
>>Somit können wir die Poissonverteilung nun einsetzen,
>> $$\begin{align}
>>P(X \leq 2) &= \sum_{k=0}^2 \frac{\lambda^{k}}{k!} e^{-\lambda}\\
>> &= \sum_{k=0}^2 \frac{1}{k!} e^{-1}\\
>> &= 0.9196986029 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. genau 1 von 1000 dieser Brennelemente die Qualitätsbedingungen nicht erfüllt.
>
>>[!example]- Lösung 
>>Wir haben $n=1000$ und $k=1$. Wir berechnen
>>$$\begin{align}
>> \lambda &= n \cdot p \\
>> &= 1000 \cdot 0.0002 \\
>> &= \frac{1}{5}
>>\end{align}$$
>>Somit können wir die Poissonverteilung nun einsetzen,
>>$$\begin{align}
>> P(X = 1) &= \frac{\lambda^{k}}{k!} e^{-\lambda} \\
>>  &= \frac{1}{5}e^{-1/5} \\
>>  &= 0.1637461506 \tag*{$\blacktriangleleft$}
>>\end{align}$$ 
>
>3. keines von 100 dieser Brennelemente die Qualitätsbedingungen nicht erfüllt.
>
>>[!example]- Lösung
>>Wir haben $n=100$ und $k=0$. Wir berechnen
>>$$\begin{align}
>> \lambda &= n \cdot p \\
>> &= 100 \cdot 0.0002 \\
>> &= \frac{1}{50}
>>\end{align}$$
>>Somit können wir die Poissonverteilung nun einsetzen,
>>$$\begin{align}
>>P(X = 0) &= \frac{\lambda^{k}}{k!} e^{-\lambda}  \\
>> &= \frac{\frac{1}{50}^{0}}{0!} e^{-1/50} \\
>> &= e^{-1/50} \\
>> &= 0.9801986733\tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (4)
>An einer Tankstelle kommen zwischen 16:00 und 18:00 Uhr durchschnittlich 4 Fahrzeuge pro Minute an. Die Anzahl der in einer Minute ankommenden Fahrzeuge sei poissonverteilt. Bestimmen Sie die Wahrscheinlichkeit, dass
>
>>[!note]- Gegeben ist die Poissonverteilung
>>Wir erfassen die Größen
>>- $A$ - Fahrzeug erscheint zwischen 16:00 und 18:00 Uhr
>>- $\lambda = 4$
>>
>>Wir bemerken, dass $n$ sehr hoch sein muss, wenn 4 Fahrzeuge pro Minute kommen.
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
>> &=0.018315639 \tag*{$\blacktriangleleft$}
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
>> &= 0.073262556 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>3. genau zwei Fahrzeuge ankommen
>
>>[!example]- Lösung
>> Wir haben $k = 2$
>> $$\begin{align}
>> p_{2} &= P(X=2) \\
>> &= \frac{4^2}{2!}e^{-4} \\
>> &= 0.146525111 \tag*{$\blacktriangleleft$}
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
>> &= 0.761896694446 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (5)
>Von 100 Losen gewinnt jedes fünfte Los. Es werden 3 Lose gezogen. Wie groß ist dieWahrscheinlichkeit,t mindestens einen Gewinn zu erhalten? Verwenden Sie die hypergeometrische Verteilung und die Binomialverteilung.
>>[!example]- Lösung Hypergeometrische Verteilung 
>>Wir erfassen die Parameter
>> - $N = 100$ Lose insgesamt
>> - $M=20$ Gewinnlose von $100$
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
>> &= 1 - \frac{\binom{20}{0}\binom{80}{3}}{\binom{90}{3}} \\
>> &= \frac{3977}{8085} \\
>> &\approx 0.49\tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!example]- Lösung Binomialverteilung
>>Wir erfassen die Parameter
>> - $A$ - Ereignis ein Gewinn zu ziehen
>> - $\overline{A}$ - Ereignis keinen Gewinn zu ziehen
>> - $n=3$ Lose werden gezogen
>> - $k \in [1,3]$ Gewinne werden gesucht
>> - $p = P(A) =\frac{1}{5}$
>>
>>Wir verwenden die Binomialdistribution und das Gegenereignis
>>$$\begin{align}
>> P(1\leq X \leq 3) &= P(1 \leq X) \\
>> &= 1 -P(\overline{1 \leq X}) \\
>> &= 1 - P(X < 1) \\
>> &= 1 - P(X = 0) \\
>> &= 1 - \left( \binom{3}{0} \left( \frac{1}{5} \right)^0 \left( \frac{4}{5} \right)^3 \right) \\
>> &= \frac{61}{125} \\
>> &\approx 0.49\tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (6)
>Gegeben seien die Einzelwahrscheinlichkeiten einer Zufallsgröße $X$.
>
>| $i$   | $-3$   | $-2$  | $-1$  | $1$   | $2$   | $4$   | $5$   |
>| --- | ---- | --- | --- | --- | --- | --- | --- |
>| $p_i$ | $0.05$ | $0.1$ | $0.2$ | $0.4$ | $0.1$ | $0.1$ | $0.05$    |
>
>1. Bestimmen Sie die zugehörige Verteilungsfunktion
>
>>[!example]- Lösung
>>
>>$$\begin{align}
>> F_{X}(x) = \begin{cases}
>> 0 & x < -3 \\
>> 0.05 & -3 \leq x < -2 \\
>> 0.15 & -2 \leq x < -1 \\
>> 0.35 & -1 \leq x < 1 \\
>> 0.75 & 1 \leq x < 2 \\
>> 0.85 & 2 \leq x < 4 \\
>> 0.95 & x \geq 5
>>\end{cases}
>>\end{align}$$
>>
>> ```tikz
>>\usepackage{pgfplots}
>>\pgfplotsset{compat=1.16}
>>
>>\begin{document}
>>\begin{tikzpicture}
>>\begin{axis}[
>>    ymin=0,
>>    ymax=1,
>>    xtick=data,
>>    xticklabels={$-4$, $-3$, $-2$, $-1$, $1$, $2$, $4$, $5$, $6$},
>>    ylabel={Verteilungsfunktion $F_{X}$},
>>    xlabel={Werte $i$},
>>    width=12cm,
>>    height=8cm,
>>    enlarge x limits=0.15,
>>    enlarge y limits=0.1,
>>    grid=both,
>>    ]
>>    \addplot +[const plot, no marks, black, line width=1.5pt] coordinates {(-4, 0) (-3, 0.05) (-2, 0.15) (-1, 0.35) (1, 0.75) (2, 0.85) (4, 0.95) (5, 1) (6,1)};
>>\end{axis}
>>\end{tikzpicture}
>>\end{document}
>> ```
>> $$\tag*{$\blacktriangleleft$}$$
>
>1. $P(-2 \leq X < 2)$
>
>>[!example]- Lösung  
>> $$\begin{align}
>> P(-2 \leq X < 2) &= P(-3 < X \leq 1) \\
>> &= \underbrace{ P(X \leq 1) }_{ \sum_{i=-3}^1 p_{i} } - \underbrace{ P(X \leq -3) }_{ =\sum_{i=-3}^{-3}p_{i} } \\
>> &=  \sum_{i=-3}^1 p_{i} - \sum_{i=-3}^{-3}p_{i} \tag{4.14} \\
>> &= \Big(\cancel{ 0.05 }+ 0.1 + 0.2 +0.4\Big) - \Big(\cancel{ 0.05 }\Big) \\
>> &= 0.7 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>3. $P(-2 \leq X \leq 2)$
>
>>[!example]- Lösung  
>> $$\begin{align}
>> P(-2 \leq X \leq 2) &= P(-3 < X \leq 2) \\
>> &= P(X\leq 2) - P(X \leq -3) \\
>> &= \sum_{i=-3}^{2} p_{i} - \sum_{i=-3}^{-3} p_{i} \\
>> &= \Big(\cancel{ 0.05 }+ 0.1 + 0.2 +0.4 + 0.1\Big) - \Big(\cancel{ 0.05 }\Big) \\
>> &= 0.8 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>4. $P(X>3)$
>
>>[!example]- Lösung  
>>$$\begin{align}
>> P(X>3) &= 1 - P(3 \leq X) \\
>> &= 1 - F_{X}(3) \\
>> &= 1 - \sum_{i=-3}^3 p_{i}
>> &= 1 - \Big(0.05 + 0.1 +0.2+0.4+0.1\Big) \\
>> &= 1 - 0.85 \\
>> &= 0.15 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>5. $F_{X}(-1)$
>
>>[!example]- Lösung  
>>$$\begin{align}
>> F_{X}(-1) &= P(-1 \leq X) \\
>> &= \sum_{i=-3}^{-1} p_{i} \\
>> &= \Big(0.05 + 0.1 + 0.2\Big) \\
>> &= 0.35 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>6. $F_{X}(5)$
>
>>[!example]- Lösung  
>> $$\begin{align}
>> F_{X}(5) &= P(5 \leq X) \\
>> &= 1 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>7. $E(X)$
>
>>[!example]- Lösung  
>> $$\begin{align}
>> E(X) &= \sum_{i=-3}^5 i \cdot p_{i} \\
>>  &= (-3 \cdot 0.05) + (-2 \cdot 0.1) + (-1 \cdot 0.2) + (1 \cdot 0.4) + (2 \cdot 0.1) + (4 \cdot 0.1) + (5 \cdot 0.05) \tag{4.16}  \\
>>  &= 0.7 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>1. $D^2(X)$
>
>>[!example]- Lösung  
>>$$\begin{align}
>> D^2(X) &= E(X^2) - E(X)^2 \tag{4.24} \\
>> &= \underbrace{ \Big(((-3)^2 \cdot 0.05) + ((-2)^2 \cdot 0.1) + ((-1)^2 \cdot 0.2) + (1^2 \cdot 0.4) + (2^2 \cdot 0.1) + (4^2 \cdot 0.1) + (5^2 \cdot 0.05)\Big) }_{ =E(X^2) } \\
>> &\;\;\;\;\;\;- \underbrace{ \Big((-3 \cdot 0.05)^2 + (-2 \cdot 0.1)^2 + (-1 \cdot 0.2)^2 + (1 \cdot 0.4)^2 + (2 \cdot 0.1)^2 + (4 \cdot 0.1)^2 + (5 \cdot 0.05)^2\Big) }_{ =E(X)^2 } \\
>> &= 4.7 - 0.48999999999999994 \\
>> &= 4.21 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>
>>[!code]- Code für Erwartungswert und Varianz
>> ```python
>> def EX(data):
>> 	steps = list(map(lambda x: x[0] * x[1], data)) # p_i * x_i
>> 	return sum(steps)
>>
>>def EX_square(data): # Berechnet E(X^2)
>>	steps = list(map(lambda x: (x[0]**2) * x[1], data)) # p_i * x_i 
>>	return sum(steps)
>>
>> data = [(-3,0.05), (-2,0.1), (-1,0.2), (1, 0.4), (2, 0.1), (4,0.1), (5,0.05)]
>>
>>mu = EX(data)
>>print("mu", mu) #> 0.7
>> 
>>sigma_square = EX_square(data) - EX(data)**2
>>print("EX_square", EX_square(data)) #> 4.7
>>print("EX**2", EX(data)**2) #> 0.48999999999999994
>>print("sigma_square", sigma_square) #> 4.21
>> ``` 

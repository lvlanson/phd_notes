>[!def]- Defintionen Begriffe und Grundlagen
>
>>[!terminology] 
>> Merkmalsträger - Objekte, die für die statistische Betrachtung relevant sind (Abgrenzung)
>> Merkmale - Eigenschaften/Features
>
>>[!def] Definition Grundgesamtheit (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=90|6.2]])
>>Eine **Grundgesamtheit** ist eine (vollständige) Menge von Objekten, für die ein bestimmtes Merkmal $X$ untersucht wird.
>
>>[!def] Definition Zufallsstichprobe (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=90|6.3]])
>>Zufallsstichprobe (mathematische Stichrpobe) vom Umfang $n$: An $n$ zufällig ausgewählten Objekten einer Grundgesamtheit wird das Merkmal $X$ gemessen bzw. beobachtet. Es ergibt sich ein Beobachtungsvektor $(X_{1},X_{2}, \dots, X_{n})$ von unabhängigen und identisch verteilten Zufallsgrößen $X_{i}$, welche die gleiche Verteilung wie das Merkmal $X$ besitzen. Die Zufallsgrößen $X_{i}$, $(i=1,\dots ,n)$ heißen Stichprobenvariable.
>
>>[!def] Definition Stichprobenbegriffe (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=90|6.4]])
>>Eine Realisierung $(x_{1},x_{2},\dots,x_{n})$ der Zufallsstichprobe $(X_{1},X_{2}, \dots, X_{n})$ heißt **konkrete Stichprobe**. Jede Realisierung $x_{i}$ mit $i=1,\dots,n$ heißt ein **Element der Stichprobe**.
>
>>[!def] Definition Stichprobenfunktion (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=91|6.5]])
>>Eine messbare Funktion $T=T(X_{1},X_{2}, \dots, X_{n})$ der zur Stichprobe gehörenden Zufallsgrößen $X_{1}, X_{2}, \dots, X_{n}$ heißt **Stichprobenfunktion**. Dabei ist $T$ selbst eine Zufallsgröße.
>
>>[!def] Definition Konkrete Stichprobenfunktion (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=91|6.6]])
>>Eine Realisierung $t=t(x_{1},x_{2},\dots,x_{n})$ der Stichprobenfunktion $T$ für eine konkrete Stichprobe $(x_{1},x_{2},\dots x_{n})$ heißt **konkrete Stichprobenfunktion**.

>[!def]- Definitionen Deskriptive Statistike für eindimensionale Daten
>
>>[!def] Definition Geordnete Stichprobe (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=91|6.7]])
>>Die Merkmalsausprägungen werden der Größe nach geordnet. Das heßt es entsteht
>>$$x_{1}^*<x_{2}^*<\dots<x_{n}^*$$
>
>>[!def] Definition Absolute Häufigkeit (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=91|6.8]])
>>Die absolute Häufigkeit von $$x_{i}^*:n_{i} \tag*{$i=1,\dots,m$}$$
>>Dabei gilt
>>$$\sum_{i=1}^m n_{i} = n$$
>>>[!remark] Bemerkung
>>>$n_{i}$ beschreibt die Anzahl der gemessenen Merkmalsträger $x$ unter der konkreten Merkmalsausprägung $x_{i}^*$, wobei $n$ die Gesamtanzahl an Merkamlsträgern ist.
>
>>[!def] Definition Relative Häufigkeit (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=91|6.9]])
>>Die relative Häufigkeit von $x_{i}^*:$
>>$$h_{i}=\frac{n_{i}}{n} \tag*{$i=1,\dots ,m$}$$
>>wobei $0 \leq h_{i} \leq 1 \; \forall i$
>
>>[!def] Definition Relative Summenhäufigkeiten (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=91|6.10]])
>> Die Relative Summenhäufigkeit $x_{i}^*$
>> $$H_{i} = \sum_{j=1}^i h_{j} \tag*{$j=1,\dots,m$}$$
>> Dabei gilt
>> $$H_{m}=\sum_{j=1}^m h_{j}=1$$
>>>[!remark] Bemerkung
>>> Entspricht einer kumulativen Funktion ähnlich der Verteilungsfunktion diskreter Zufallsgrößen.
>
>>[!def] Definition Empirische Verteilung einer Zufallsgröße (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=91|6.11]])
>>Empirische Verteilung von $X$ für eine konkrete Stichprobe vom Unfang $n$:
>>$$\begin{align}
>> \widehat{F}_{n}(x)&= \frac{\text{Anzahl der Merkmalsausprägungen} \leq x}{n}  \\
>> &= \sum_{\substack{i \\ x_{i}^* \leq x}} h_{i} \tag*{$\forall x \in \mathbb{R}$}
>>\end{align}$$ 
>>>[!remark] Bemerkung
>>>Die empirische Verteilung einer Zufallsgröße gibt für eine reelle Zahl $x$ die entsprechende relative Summenhäufigkeit des nächsten $x_{i}^*$ zurück.
>
>>[!def] Definition Klassenmitte (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=92|6.14]])
>>Die **Klassenmitte** ist definiert als
>>$$\overline{x}_{i}= \frac{x_{ir}+x_{il}}{2} \tag*{$i=1,\dots ,k$}$$
>>wobei $x_{il}$ der linke und $x_{ir}$ der rechte Klassenrand ist mit $k$ Klassen.
>
>>[!def] Definition Arithmetisches Mittel (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=94|6.20]])
>>Das **arithmetische Mittel** für diskrete Daten ist gegeben als
>>$$\overline{x}= \frac{1}{n} \sum_{i=1}^k x_{i}$$
>>bzw. für klassierte Daten
>>$$\overline{x} = \frac{1}{n}\sum_{i=1}^k n_{i}\overline{x}_{i}$$
>>mit $k$ Klassen.
>>>[!remark] Bemerkung
>>> Das arithmetische Mittel ist eine Schätzung für $\mu$, allerdings ist es empfindlich durch das Erscheinen von Ausreißern. Robuste Alternativen sind der Median und Modalwert.
>
>>[!def] Definition Empirischer Median (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=94|6.21]])
>>Gegeben sei eine geordnete Stichprobe, dann ist der **Median** definiert als
>>$$x_{0.5}=\begin{cases}
>> x_{\frac{n+1}{2}} & \text{ falls } n \text{ ungerade } \\
>> \frac{1}{2}\left( x_{\frac{n}{2}}+x_{\frac{n}{2}+1} \right) & \text{ falls } n \text{ gerade }
>>\end{cases}$$
>
>>[!def] Definition Empirischer Modalwert (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=94|6.22]])
>>Der **empirische Modalwert** $\overline{x}_{M}$ ist der Wert mit der größten Häufigkeit.
>>>[!remark] Bemerkung
>>>Gibt es mehrere Merkmalsausprägungen mit der gleichen maximalen Häufigkeit, so existiert kein Modalwert.
>
>>[!def] Definition Geometrisches Mittel (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=95|6.23]])
>>Das **geometrische Mittel** für diskrete Daten ist gegeben als
>> $$\overline{x}_{G} = \sqrt[n]{ \prod_{i=1}^n x_{i} }\tag*{$\forall x_{i}>0$}$$
>
>>[!def] Definition Empirische Streuung (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=95|6.26]])
>>Die empirische Streuung für diskrete Daten ist gegeben als
>>$$s^2 = \frac{1}{n-1}\sum_{i=1}^n(x_{i}-\overline{x})^2 = \frac{1}{n-1}\sum_{i=1}^n (x^2_{i}-n\overline{x}^2)$$
>>bzw. für klassierten Daten
>>$$s^2 = \frac{1}{n-1}\sum_{i=1}^k n_{i}(\overline{x}_{i}-\overline{x})^2 = \frac{1}{n-1}\sum_{i=1}^k(n_{i}\overline{x}_{i}^2 - n\overline{x}^2)$$
>>mit $k$ Klassen.
>
>>[!def] Definition Empirische Standardabweichung (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=95|6.27]])
>>Die **empirische Standardabweichung** ist definiert mit
>>$$s=+\sqrt{ s^2 }$$
>
>>[!def] Definition Empirischer Variationskoeffizient (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=95|6.28]])
>>Der **empirische Variationskoeffizient** ist definiert mit
>>$$v=\frac{s}{\overline{x}}$$ mit $\overline{x} \neq 0$
>
>>[!def] Definition Mittlere Absolute Abweichung (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=95|6.29]])
>>Die **mittlere absolute Abweichung** ist definiert mit
>>$$s_{a}=\frac{1}{n}\sum_{i=1}^n \lvert x_{i}-\overline{x} \rvert $$
>
>>[!def] Definition Spannweite (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=95|6.30]])
>>Die **Spannweite** ist definiert mit
>>$$s_{w}=\underset{i}{\text{max}} \{ x_{i} \} - \underset{i}{\text{min}}\{ x_{i} \}\;\;$$

>[!def] Definitionen Deskriptive Statistik für zweidimensionale Daten
>
>>[!def] Defintion Empirische Kovarianz (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=97|6.33]])
>>$$\begin{align}
>> s_{XY} &= \frac{1}{n-1}\sum_{i=1}^n (x_{i} - \overline{x})(y_{i}-\overline{y}) \\
>> &= \frac{1}{n-1} \left( \sum_{i=1}^n x_{i}y_{i} - n \overline{xy} \right)
>>\end{align}$$
>
>>[!def] Definitionen Empirischer Korrelationskoeffizient nach PEARSON (Definition [[../Vorlesungsskript_Mathematik3.pdf#page=98|6.34]])
>> $$\begin{align}
>> r_{XY} &= \frac{s_{XY}}{s_{X}s_{Y}} \\
>>  &= \frac{\sum_{i=1}^n x_{i}y_{i} - n\overline{xy}}{\sqrt{ \left( \sum_{i=1}^n x_{i}^2 - n \overline{x}^2 \right)\left( \sum_{i=1}^n y_{i}^2 - n\overline{y}^2 \right) }}
>>\end{align}$$
>>wobei $s_{X}$ Standardabweichung für $X$ und $s_{Y}$ die Standardabweichung für $Y$ ist.
>
>>[!theorem] Satz Unabhängigkeit von $X$ und $Y$ (Satz [[../Vorlesungsskript_Mathematik3.pdf#page=98|6.38]])
>Für zwei unabhängige Merkmale $X$ und $Y$ gilt $r=0$. Allerdings folgt aus $r=0$ nicht die Unabhängigkeit von $X$ und $Y$.




>[!example] Aufgabe (1)
> Eine Textilfirma analysiert vor Beginn eines neuen Produktionsovrhabens die Größenverteilung eines gewissen Kundenkreises. Dabei wurden unter anderem auch die Körpergrößen (in cm) einer Gruppe von 130 Studenten ermittelt
> $$\begin{align}
> &180, 176, 167, 180, 177, 166, 160, 176, 176, 164, 182, 165, 175, 172, 172, \\  &173, 179, 166, 162, 168, 170, 177, 183, 179, 172, 166, 163, 176, 177, 181
>\end{align}$$
>1. Bestimmen Sie für die Klasseneinteilung $[160,165), [165,170), [170,175),[175,180),[180,185)$
>
>>[!example]- Lösung
>>
>>| Klasse $k$ | Intervall | Absolute Klassenhäufigkeit | $H_{i}$ |
>>| ---------- | ----------- | -------------------------- | ------------------------- |
>>| $1$        | $[160,165)$ | $4$                        | $\frac{4}{30}$            |
>>| $2$        | $[165,170)$ | $6$                        | $\frac{10}{30}$            |
>>| $3$        | $[170,175)$ | $5$                        | $\frac{15}{30}$            |
>>| $4$        | $[175,180)$ | $10$                       | $\frac{25}{30}$           |
>>| $5$        | $[180,185)$ | $5$                        | $\frac{30}{30}$            | 
>>$$\tag*{$\blacktriangleleft$}$$
>
>2. Geben Sie die empirische Verteilungsfunktion für die Klassenteilung an.
>
>>[!example]- Lösung
>>$$\begin{align}
>> \widehat{F}_{n}(x) = \begin{cases}
>> 0  & x<160\\
>> \frac{4}{30} & 160 \leq x < 165 \\
>> \frac{10}{30} & 165 \leq x < 170\\
>> \frac{15}{30} & 170 \leq x < 175\\
>> \frac{25}{30} & 175 \leq x < 180\\
>> \frac{30}{30} & 180 \leq x
>>\end{cases}
>>\end{align}$$
>>$$\tag*{$\blacktriangleleft$}$$
>
>3. Stellen Sie die absolute Klassenhäufigkeit und die empirische Verteilungsfunktion grafisch dar.
>
>>[!example] Lösung
>> OPEN
>
>Bestimmen Sie außerdem folgende Kennwerte bezüglich der Klasseneinteilung:
>
>4. Arithmetisches Mittel
>
>>[!example]- Lösung
>> $$\begin{align}
>> \overline{x} &= \frac{1}{n}\sum_{i=1}^k n_{i} \overline{x}_{i} \\
>> &= \frac{1}{30} (4\cdot 162.5 + 6\cdot 167.5 + 5\cdot 172.5 + 10\cdot 177.5 + 5\cdot 182.5 ) \\
>> &= 173.5 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>5. Empirischer Median
>
>>[!example]- Lösung
>> $$\begin{align}
>> x_{0.5} &= \frac{1}{2}\left( x_{\frac{n}{2}}+x_{\frac{n}{2}+1} \right) \\
>> &= \frac{1}{2}(175+176) \\
>> &= 175.5 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>6. Empirischer Modalwert
>
>>[!example]- Lösung
>> $$x_{M}=4$$
>
>7. Empirische Streuung
>
>>[!example]- Lösung
>>$$\begin{align}
>> s^2 &= \frac{1}{n-1}\sum_{i=1}^k n_{i}(\overline{x}_{i}-\overline{x})^2 \\
>> &= \frac{1}{29}(4\cdot (162.5 - 173.5)^2 + 6\cdot (167.5- 173.5)^2 + 5\cdot (172.5 - 173.5)^2 \\ & \;\;\;\;+ \, 10\cdot (177.5- 173.5)^2 + 5\cdot (182.5- 173.5)^2 )\\
>> &= 43.7931 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>8. Empirische Standardabweichung
>
>>[!example]- Lösung
>> $$\begin{align}
>> s = +\sqrt{ s^2 } = 6.6174 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>9. Empirischer Variationskoeffizient
>
>>[!example]- Lösung
>>$$\begin{align}
>> v &= \frac{s}{\overline{x}} \\
>> &= \frac{6.6174}{173.5}   \\
>> &= 0.0381 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (2)
>Für 6 verschiedene Monate im Jahr 1998 liegen Daten über den Hypothekenzinssatz $X$ \[%\] sowie über den saisonbereinigten Auftragseingang $Y$ \[Mio €\] im Bauhauptgewerbe, welcher auf den privaten Wohnungsbau entfällt vor.
>
>| $X$ | $6$    | $5$    | $7$    | $7$    | $8$    | $9$ |
>| --- | ------ | ------ | ------ | ------ | ------ | --- |
>| $Y$ | $3000$ | $3200$ | $2500$ | $2300$ | $2000$ | $2000$    |
>
>Bestimmen Sie
>1. den empirischen Korrelationskoeffizienten
>
>>[!example] Lösung
>>  Für den Korrelationskoeffizienten berechnen wir
>>  $$r_{XY} = \frac{s_{XY}}{s_{X}s_{Y}} = \frac{\sum_{i=1}^nx_{i}y_{i}-n \overline{xy}}{\left( \sum_{i=1}^n x^2_{i}-n\overline{x}^2 \right)\left( \sum_{i=1}^n y^2_{i}-n\overline{y}^2 \right)}$$
>>  Dafür berechnen wir
>>  $$\begin{align}
>>  s_{XY} &= \frac{1}{n-1}\sum_{i=1}^n (x_{i} - \overline{x})(y_{i}-\overline{y}) \\
>>\end{align}$$
>>mit $$\begin{align}
>> \overline{x} &= 7 \\
>> \overline{y} &= 2500
>>\end{align}$$
>>erhalten wir
>>$$s_{XY} = -680$$
>>Wir berechnen noch
>>$$\begin{align}
>> s_{X} &= 1.4142135623730951 \\
>> s_{Y} &= 505.9644256269407
>>\end{align}$$
>>Wir erhalten also
>>$$\begin{align}
>> r_{XY} &= -\frac{680}{1.4142 \cdot 505.9644} \\
>> &= -0.95032
>>\end{align}$$
>>>[!code]
>>>```python
>>> X = [6,5,7,7,8,9]
>>> Y = [3000,3200,2500,2300,2000,2000]
>>>
>>> oX = sum(X)/len(X) # arithmetisches Mittel von X
>>> oY = sum(Y)/len(Y) # arithmetisches Mittel von Y
>>>
>>> print("arithmetisches Mittel X = ", oX)
>>> print("arithmetisches Mittel X = ", oY)
>>> 
>>> steps = [(x_i - oX)*(y_i - oY) for x_i, y_i in zip(X,Y)] # innere Summenteil von s_XY
>>> s_XY = 1/(len(X)-1) * sum(steps)
>>>
>>>print("s_XY =",s_XY)
>>>
>>>def s_sq(V, oV):
>>>    # s^2 des Merkmalsträgers V mit arithmetischem Mittel oV
>>>    return 1/(len(V)-1) * sum([(v_i - oV)**2 for v_i in V])
>>>
>>>s_sq_X = s_sq(X, oX)
>>>s_sq_Y = s_sq(Y, oY)
>>>
>>>s_X = s_sq_X**(1/2)
>>>s_Y = s_sq_Y**(1/2)
>>>
>>>print("s_X =",s_X,"s_Y =", s_Y)
>>>
>>>r_XY = s_XY/(s_X*s_Y)
>>>
>>>print("r_XY =", r_XY)
>>>```
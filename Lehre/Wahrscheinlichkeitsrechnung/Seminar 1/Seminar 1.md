>[!Example] Aufgabe (1a)
>Wieviele verschiedene siebenstellige Zahlen kann man aus den Ziffern $(1,2,2,3,6,6,6)$ bilden?
>>[!example]- Lösung
>>Wir ordnen 7 Ziffern an, das heißt
>>$$n=7$$
>>Wir haben laut Definition 1.3 die Multimenge
>>$$M=\{ 1 \cdot 1, 2 \cdot 2, 1 \cdot 3, 3 \cdot 6\}$$
>>Wir prüfen den Zeichenvorrat, wie viele Zeichen wir zur Verfügung haben
>>$$\lvert M \rvert = 1 + 2 + 1 +3 = 7$$
>>Daher haben wir eine Permutationen mit Wiederholungen, da wir alle Zeichen anordnen. Wir verwenden Definition 1.4
>>$$\begin{align}
>> \binom{7}{1,2,1,4} &= \frac{7!}{1!\;2!\;1!\;4!} \\
>> &= 420 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!Example] Aufgabe (1b)
>Wieviele Tips sind im Zahlenlotto 5 aus 90 bei einer bestimmten Ziehung möglich?
>>[!example]- Lösung
>> Da wir eine **Auswahl** treffen, handelt es sich hierbei um eine **Kombination**. Da jede Zahl nur einmal gezogen wird, haben wir eine **Kombination ohne Wiederholung**. Unter Verwendung von Definition 1.11 und 1.12 können wir die folgenden Parameter bestimmen.
>> $$\begin{align}
>> n &= 90 \\
>> k &= 5
>>\end{align}$$
>> $$\begin{align}
>> C^5_{90}&= \binom{90}{5} \\ \\
>>     &= \frac{90!}{5!(90-5)!} \\
>>     &= 43\;949\;268 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (1c)
> Wieviele Möglichkeiten gibt es im Zahlenlotto 5 aus 90 bei einer bestimmten Ziehung für einen Dreier?
>>[!example]- Lösung
>>Wir formalisieren die Ziehung wie folgt:
>>- Die Menge aller Treffer $T$ ist _(5 Gewinnerkugeln werden gezogen)_
>>$$T=\{ d_{1}, d_{2},d_{3},d_{4},d_{5}\}$$
>>- Die Menge aller Nicht-Treffer $N$ ist _(5 Gewinnerkugeln von verbleibenden entfernen)_
>>$$N=\{ n_{i} \; | \; 1 \leq i \leq 85 \}$$
>>
>>Wir schließen 
>>$$\begin{align}
>> \lvert T \rvert &= 5 \\ 
>> \lvert N \rvert &= 85 
>>\end{align}$$
>>Nun wollen wir die Mengen konstruieren, die unsere Ziehungen repräsentieren. Wir definieren die Menge "k aus n" ziehen mit
>>$$\begin{align}
>> T^3 &= \{ \{t_{1}, t_2, t_{3}\} \; | \; t_{i} \in T \} \\
>> N^2 &= \{ \{n_{1}, n_{2}\} \; | \; n_{i} \in N\}
>>\end{align}$$
>>Damit ergeben sich folgende Kombination
>>$$\begin{align}
>> C^3_{5} &= \binom{5}{3} \\
>>     &= 10 \\
>> C^{2}_{85} &= \binom{2}{85}  \\
>>     &=  3570
>>\end{align}$$
>>Nach dem Multiplikationsprinzip erhalten wir die Lösung der Aufgabe (Kreuzprodukt abzählen von $T^3 \times N^2$
>>$$C^3_{5} \cdot C^{2}_{85} = 10 \cdot 3570 = 35700 \tag*{$\blacktriangleleft$} $$

>[!example] Aufgabe (1d)
> Wieviele verschiedene Reihenfolgen gibt es für das Aufhängen von 30 Gemälden in einer Ausstellung.
>>[!example]- Lösung
>> Da wir hier 30 Elemente anordnen wollen und dabei alle anordnen, handelt es sich hierbei um eine Permutation. Außerdem können keine Elemente mehrfach auftauchen, daher haben wir eine gewöhnliche Permutation. Die Aufgabe löst sich demnach mti
>> $$\begin{align}
>> P_{30} = 30! \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (1e)
>Eine Lieferung von 25 Geräten, die durch ihre Fabrikatsnummer unterscheidbar sind, enthält vier fehlerhafte Geräte
>1. Wieviele Stichproben vom Umfang 5 sind möglich?
>>[!example]- Lösung
>> Wir bemerken, dass alle Geräte unterscheidbar sind, man könnte formal schreiben die Menge der Geräte ist
>> $$G= \{ g_{1}, g_{2}, \dots, g_{25} \}$$
>> Da wir lediglich aus der Menge auswählen, erhalten wir die Kombination ohne Unterscheidung
>> $$\begin{align}
>> C_{25}^5 &= \binom{25}{5} \\ 
>> &= \frac{25!}{5!\;20!} \\
>> &= 53\;130 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>2. Wieviele Stichproben vom Umfang 5 gibt es, die genau zwei fehlerhafte Geräte enthalten?
>>[!example]- Lösung
>>Wir teilen die Menge der Geräte in die Defekten $D$ und Nicht-Defekten $N$ auf, sodass wir festhalten können
>>$$\begin{align}
>> \lvert D \rvert &= 4 \\
>> \lvert N \rvert &= 21  
>>\end{align}$$
>>Nun wählen wir wie in der Aufgabe (1c) aus. Wir wollen 2 Defekte aus der Menge der Defekten ziehen und 3 aus der Menge der Nicht-Defekten und erhalten folgende Möglichkeiten.
>>$$\begin{align}
>> C^{2}_{4} &= \binom{4}{2} \\
>> &= 6 \\
>> C^{3}_{21} &= \binom{21}{3} \\
>> &= 1330
>>\end{align}$$
>>Nun wenden wir genauso wieder das Multiplikationsprinzip an, um jede Möglichkeit der einen Kombination mit jeder Möglichkeit der anderen Kombination zu verknüpfen.
>>$$\begin{align}
>> C^2_{4} \cdot C^3_{21} = 6 \cdot 1330 = 7980 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe 2 Situation
> Es werden zwei Geräte geprüft, die 
> - ausgefallen (0)
> - funktionsfähig (L)
>
>sein können. Es ergeben sich folgende Elementarereignisse
>$$\begin{align}
> \{ \omega_{0} \} &= 00 \\
> \{ \omega_{1} \} &= 0L \\
> \{ \omega_{2} \} &= L0 \\
> \{ \omega_{3} \} &= LL
>\end{align}$$
>>[!example] Aufgabe (2a)
>> Geben Sie die Menge der Elementarereignisse $\Omega$ an.
>>>[!example]- Lösung 
>>> Definition 2.2 beschreibt, dass $\Omega$ die Menge der Elementarereignisse ist, also $\omega_{i} \in \Omega, \forall i \in \mathbb{N}_{0}$. Das bedeutet, alle Elementarereignisse müssen in der Elementarereignissmenge zusammgefasst sein.
>>> $$\Omega = \{ \omega_{0},\omega_{1},\omega_{2},\omega_{3} \} \tag*{$\blacktriangleleft$}$$
>
>>[!example] Aufgabe (2b)
>> Geben Sie den Ereignisraum $\mathbb{E}$ zu diesem Versuch an.
>>>[!example]- Lösung
>>> Definition 2.8 beschreibt den Ereignisraum als die Menge aller zufälligen Ereignisse in Abhänigkeit zu $\Omega$. Diese ist angegeben als die Potenzmenge. Wir erinnern uns, die Potenzmenge einer $\Omega$ ist die Menge aller Teilmengen von $\Omega$, also
>>> $$\begin{align}
>>> \mathcal{P}(\Omega)= \Big\{& \emptyset, \{ \omega_{0} \}, \{ \omega_{1} \}, \{ \omega_{2} \},\{ \omega_{3} \}, \\ 
>>> & \{ \omega_{0}, \omega_{1}\}, \{ \omega_{0}, \omega_{2}\}, \{ \omega_{0}, \omega_{3}\}, \\
>>> &\{ \omega_{1}, \omega_{2}\}, \{ \omega_{1}, \omega_{3}\}, \{ \omega_{2}, \omega_{3}\}, \\
>>> & \{ \omega_{0}, \omega_{1}, \omega_{2}\},\{ \omega_{0}, \omega_{1}, \omega_{3}\}, \\
>>> & \{ \omega_{0}, \omega_{2}, \omega_{3}\}, \{ \omega_{1}, \omega_{2}, \omega_{3}\}, \Omega\Big\}
>>>\end{align}$$
>>>Um zu überprüfen, ob wir ordentlich alle Elemente erfasst haben, verwenden wir die Eigenschaft, dass die Potenzmenge für $n$ elemente in $\Omega$ genau $2^n$ Elemente enthalten muss. Wir haben genau $16=2^4$ Elemente, demzufolge haben wir alle Elemente erzeugt.
>>>$$\tag*{$\blacktriangleleft$}$$
>
>>[!example] Aufgabe (2c)
>> Geben Sie alle Ereignisse an, die das Ereignis $\{ \omega_{0},\omega_{1} \}$ nach sich zieht.
>>>[!example]- Lösung
>>> Sektion 2.2 Bemerkung (6) beschreibt, was es heißt, dass _"ein Ereignis ein anderes nach sich zieht"_. Wir halten fest für $A,B \subseteq  \Omega$
>>> $$A \text{ zieht } B \text{ nach sich } \Longleftrightarrow A \subset B$$
>>> Übertragen wir diese auf die Aussage der Aufgabe, erhalten wir
>>> $$\{ \omega_{0},\omega_{1} \} \text{ zieht } B \text{ nach sich } \Longleftrightarrow A \subset B$$
>>> Nun suchen wir die Mengen $B$, die die beschriebene Relation $A \subset B \subseteq \Omega$ erfüllen. Daher wählen wir aus Omega folgende Mengen, die diese Relation erfüllen
>>> $$\begin{align}
>>> B_{1} &= \{\omega_{0},\omega_{1}, \omega_{2}\} \\
>>> B_{2} &= \{ \omega_{0},\omega_{1}, \omega_{3} \} \\
>>> B_{3} &= \Omega \tag*{$\blacktriangleleft$}
>>>\end{align}$$
>
>>[!example] Aufgabe (2d)
>> Geben Sie die Komplentärereignisse zu $\{ \omega_{0},\omega_{1} \}$ und $\{ \omega_{3} \}$ an.
>>>[!example]- Lösung
>>>Sektion 2.2 Bemerkung (1) beschreibt das Komplementärereignis. Wir bemerken vor allem, dass das Komplementärereignis von der Grundmenge $\Omega$ abhängig ist. Wir nutzen die angegebene Formel
>>>$$\begin{alignat}{2}
>>> \overline{\{ \omega_{0},\omega_{1} \}} &= \Omega \setminus \{ \omega_{0},\omega_{1} \} &&= \{ \omega_{2}, \omega_{3} \}\\
>>> \overline{\{ \omega_{3} \}} &= \Omega \setminus \{ \omega_{3} \} &&= \{ \omega_{0},\omega_{1},\omega_{2} \} \tag*{$\blacktriangleleft$}
>>>\end{alignat}$$

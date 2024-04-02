>[!example] Aufgabe (1a)
>Aus einer Sendung von 12 Glühbirnen, von denen 4 defekt sind, werden zufällig zwei ausgewählt. Wie groß ist die Wahrscheinlichkeit, dass...
>>[!note] Wissen:  3.2 Klassische Definition der Wahrscheinlichkeit
>
>>[!note]- Vorbereitung und Überlegungen
>>Die Elementarereignisse lassen sich als $0$ - defekt, $1$ - funktionstüchtig darstellen. Wir bemerken, dass die Glühbirnen unterscheidbar sind, daher indizieren wir die defekten und funktionstüchtigen Glühbirnen
>> $$\begin{alignat}{2}
>> \{ \omega_{k} \} &= \{ 0_{i},0_{j} \} \qquad &&\text{mit } 1 \leq i <j\leq 4 \tag{beide defekt}\\
>> \{ \omega_{m} \} &= \{ 0_{i}, 1_{j} \} \qquad &&\text{mit } 1 \leq i \leq 4 \text{ und } 1 \leq j \leq 8 \tag{genau eine defekt}\\
>> \{ \omega_{n} \} &= \{ 1_{i}, 1_{j} \} &&\text{mit } 1 \leq i < j \leq 8 \tag{keine defekt}
>>\end{alignat}$$
>>Die folgenden Aufgaben lassen sich mit **Definition 3.6 und 3.7** lösen, daher müssen wir zählen wieviele Elementarereignisse die beschriebene Charakteristik erfüllen. In den Beschreibungen sind die möglichen Belegungen für die Indizes $k,m,n$ im Moment noch unbekannt.
>>
>>Wir können allerdings schon jetzt berechnen wieviele Elementareignisse sich in $\Omega$ insgesamt befinden. Dies lässt sich charakterisieren als _"Wieviele Möglichkeiten gibt es 2 aus 12 Glühbirnen zu wählen"_. Dies lässt sich berechnen als
>>$$\begin{align}
>> \lvert \Omega \rvert &=C_{12}^2 \\
>>       &= \binom{12}{2}  \\
>>       &= \frac{12!}{2!10!} \\
>>       &= 66
>>\end{align}$$
>>Dies ist $m=66$ für **Definition 3.6**, und wir können die Indizes für $k,m,n$ einschränken mit
>>$$1 \leq k,m,n \leq 66$$
>
>1. ...beide defekt sind?
>
>>[!example]- Lösung
>> Wir definieren das Ereignis _"beide Glühbirnen sind defekt"_ mit
>> $$A = \{ \omega_{k} \; | \ \omega_{k}  = \{ 0_{i},0_{j} \} \; \text{mit } 1 \leq i <j\leq 4 \}$$
>> Wir berechnen _"2 aus 4 zu wählen"_, also
>> $$\begin{align}
>> \lvert A \rvert &=  C_{4}^2  \\
>>  &= \binom{4}{2} \\
>>  &= \frac{4!}{2!2!} \\
>>  &= 6
>>\end{align}$$
>>Die Wahrscheinlichkeit lässt sich nach **Definition 3.7** mit $n=6$ angeben als 
>>$$\begin{align}
>> P(A) &= nP(\omega_{i})  \\
>>      &= \frac{6}{66} \\
>>      &= \frac{1}{11} \tag*{$\blacktriangleleft$}
>>\end{align}$$
>>>[!note] Bemerkung
>>> Genau genommen wählen wir auch 0 von den 8 Defekten, was ergibt
>>> $$C_{8}^0 = \binom{8}{0}= \frac{8!}{0!8!}=1$$
>>> Dies beinflusst die Auswahl jedoch nicht.
>
>2. ...beide funktionsfähig sind?
>
>>[!example]- Lösung
>> Wir definieren das Ereignis _"beide Glühbirnen sind funktionfähig"_ mit
>> $$C = \{\omega_{n} \;| \; \omega_{n} \} = \{ 1_{i}, 1_{j} \}  \text{ mit } 1 \leq i < j \leq 8\}$$
>> Wir berechnen _"2 aus 8 zu wählen"_
>> $$\begin{align}
>> \lvert B \rvert &=  C_{8}^2  \\
>>  &= \binom{8}{2} \\
>>  &= \frac{8!}{2!6!}  \\
>>  &= 28
>>\end{align}$$
>>Die Wahrscheinlichkeit lässt sich nach **Definition 3.7** mit $n=28$ angeben als 
>>$$\begin{align}
>> P(C) &= nP(\omega_{i})  \\
>>      &= \frac{28}{66} \\
>>      &= \frac{14}{33} \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>3. ...mindestens eine defekt ist?
>
>>[!example]- Lösung
>> Es gibt für diese, wie auch für jede andere, mehrere Möglichkeiten eine Lösung zu finden. Folgen wir hier das bisherige Muster, berechnen wir die Möglichkeiten für
>> - genau eine defekt
>> - genau beide defekt
>>
>>was das Ereignis _"mindestens eine ist defekt"_ umfasst.
>>
>>Wir ändern für diese Aufgabe unsere Strategie und beschreiben das Komplementärereignis
>>$$\underbrace{ \text{mindestens eine defekt} }_{ =C } = \underbrace{ \overline{\text{keine defekt}} }_{ =\overline{C} }$$
>>Wir können kontrollieren ob unsere Überlegung korrekt ist, indem wir prüfen
>>$$C \cup \overline{C} = \Omega \tag{Übung}$$
>>Wir verwenden **Definition 3.2 Folgerung (2)**
>>$$P(C) = 1 - P(\overline{C})$$
>>Dafür benötigen wir $P(\overline{C})$. Wir geben das Ereignis $\overline{C}$ an als
>>$$\overline{C} = \{ \omega_{n} \; | \; \omega_{n}  = \{ 1_{i}, 1_{j} \} \text{ mit } 1 \leq i < j \leq 4\}$$
>>wie zuvor zählen wir alle Möglichkeiten _"2 aus 8 zu wählen"_, also
>>$$\begin{align}
>>  \lvert \overline{C} \rvert &= C_{4}^2  \\
>> &= \binom{8}{2} \\
>> &= \frac{8!}{2!6!} \\
>> &=  28
>>\end{align}$$
>>Daher haben wir nach **Definition 3.7** mit $n=6$
>> $$\begin{align}
>> P(\overline{C})&=nP(\omega_{i}) \\
>> &=\frac{28}{66} \\
>>      &= \frac{14}{33}
>>\end{align}$$
>>Wir erhalten demnach
>>$$\begin{align}
>> P(C) &= 1 - P(\overline{C}) \\
>>  &= 1 - \frac{14}{33} \\
>>  &= \frac{19}{33} \tag*{$\blacktriangleleft$} 
>>\end{align}$$


>[!example] Aufgabe (1b)
>6 Ehepaare sind in einem Raum. Es werden 2 Personen zufällig ausgewählt.
>>[!note] Wissen: 3.2 Klassische Definition der Wahrscheinlichkeit
>
>>[!note]- Vorbereitung und Überlegungen
>>Wir können die Situation formal festhalten als
>>$$\{ \{ M_{i},F_{i} \}\; | \; 1\leq i\leq 6 \}$$
>>wobei $M_{i}$ ein Mann und $F_{i}$ eine Frau sind, und bei gleichem $i$ handelt es sich um ein Ehepaar. Die Elementarereignisse können wir formalisieren mit
>>$$\begin{align}
>> \{ \omega_{k} \} &= \{ M_{i}, M_{j} \; | \; 1 \leq i < j \leq 6 \} \tag{2 Männer} \\
>> \{ \omega_{n} \} &= \{ M_{i}, F_{j} \; | 1 \leq i,j \leq 6 \} \tag{1 Mann, 1 Frau} \\
>> \{ \omega _{m} \} &= \{ F_{i}, F_{j} \; | \; 1 \leq i < j \leq 6 \} \tag{2 Frauen}
>>\end{align}$$
>>Wir halten fest wieviele Möglichkeiten es gibt 2 aus den 12 Personen zu wählen mit 
>>$$\begin{align}
>> \lvert \Omega \rvert &= C_{12}^2   \\
>> &= \binom{12}{2} \\
>> &= \frac{12!}{2!10!} \\
>> &= 66
>>\end{align}$$
>>Dies ist $m=66$ für **Definition 3.6**, und wir können die Indizes für $k,m,n$ einschränken mit
>>$$1 \leq k,m,n \leq 66$$
>
>1. Wie groß ist die Wahrscheinlichkeit dafür, dass sie verheiratet sind?
>
>>[!example]- Lösung
>>Wir suchen alle Paare mit
>>$$\{ M_{i}, F_{j} \}$$
>>mit der Eigenschaft $i = j$. Wir definieren das Ereignis
>>$$A = \{ M_{i}, F_{i} \; | \; 1 \leq i = j \leq 6 \}$$
>>Informell wissen wir, dass es genau 6 Paare gibt ($i=j$), daher gibt es genau 6 Möglichkeiten, dass ein Ehepaar gezogen werden kann. Also haben wir mit $n=6$
>>$$\begin{align}
>> P(A) &= nP(\omega_{i})  \\
>>      &= \frac{6}{66} \\
>>      &= \frac{1}{11} \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. Wie groß ist die Wahrscheinlichkeit dafür, dass sie gleichen Geschlechts sind?
>
>>[!example]- Lösung
>>Wir definieren das Ereignis
>>$$B = \{ X_{i}, X_{j} \; | \; X \in \{ F, M \}, \; 1\leq i,j\leq 6 \}$$
>>Wir wollen nun zählen wieviele Möglichkeiten es gibt, so zu ziehen, dass beide Personen gleichen Geschlechts sind. Zunächst können wir _"2 aus 6 zu wählen"_ für die Männer und _"2 aus 6 zu wählen$_ für die Frauen berechnen
>>$$\begin{align}
>> ^{C,F}C_{6}^2 &= \binom{6}{2} \\
>>       &= \frac{6!}{2!4!} \\
>>       &= 15
>>\end{align}$$
>>Da wir sowohl 2 Frauen als auch 2 Männer ziehen können, beziehungsweise die Kombination **vereinen** wollen, verwenden wir das **Additionsprinzip** und erhalten
>>$$n = 15 + 15 = 30$$
>> Damit erhalten wir
>> $$\begin{align}
>> P(B) &= nP(\omega_{i})  \\
>>      &= \frac{30}{66} \\
>>      &= \frac{5}{11} \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (2)
>In einer Klasse sind 5% der Schüler und 4% der Schülerinnen älter als 17 Jahre. 40% der Schüler sind weiblich. Mit welcher Wahrscheinlichkeit ist eine zufällig ausgewählte Person weiblich, wenn sie älter als 17 Jahre ist?
>>[!note] Wissen: 3.5 Definition der bedingten Wahrscheinlichkeit
>
>>[!example]- Lösung
>>Zunächst einigen wir uns auf eine Symbolik
>>- $A$ - älter
>>- $\overline{A}$ - nicht älter
>>- $W$ - weiblich
>>- $\overline{W}$ -  nicht weiblich
>>
>>Wir sammeln nun die gegebenen Informationen aus der Aufgabe
>>$$\begin{align}
>> P(A\;|\; \overline{W}) &= \frac{5}{100} = \frac{1}{20} \\
>> P(A\;|\;W) &= \frac{4}{100} = \frac{1}{25} \\
>> P(W) &= \frac{4}{100} = \frac{2}{5} \\
>> P(\overline{W}) &= \frac{3}{5}
>>\end{align}$$
>>Wir suchen **eine Person ist weiblich unter der Bedingung, dass sie älter als 17 ist**, also
>>$$P(W\;|\;A)$$
>>Wir verwenden **Satz 3.16**, welcher analog zum **Satz von Bayes** unter **Satz 3.29** ist.
>>>[!note]- Wir haben ein vollständiges System an Ereignissen
>>>![[figures/Pasted image 20240329181952.png|center]]
>>>Wir können dies mathematisch prüfen mit **Definition 3.27**
>>>$$\begin{align}
>>> W \cup \overline{W} &= \Omega \\ \\
>>> W \cap \overline{W} &= \emptyset
>>>\end{align}$$
>>$$\begin{align}
>> P(W\;|\;A) &= \frac{P(A\;|\;W)P(W)}{P(A)} \tag{1}
>>\end{align}$$
>>Um Gleichung $(1)$ lösen zu können, fehlt uns die Größe $P(A)$. Diese können wir über den **Satz der totalen Wahrscheinlichkeit (Satz 3.28)** erhalten.
>>$$\begin{align}
>> P(A) &= P(A\;|\overline{W}\;)P(\overline{W}) + P(A\;|\;W)P(W) \\
>>      &= \frac{1}{25}\cdot \frac{2}{5} + \frac{1}{20}\cdot \frac{3}{5} \\
>>      &= \frac{23}{500}
>>\end{align}$$
>>Das Ergebnis können wir nun für Gleichung $(1)$ verwenden und erhalten
>>$$\begin{align}
>> P(W\;|\;A) &= \frac{\frac{1}{25} \cdot \frac{2}{5}}{\frac{23}{500}} \\
>>    &= \frac{8}{23} \tag*{$\blacktriangleleft$}
>>\end{align}$$
>>


>[!example] Aufgabe (3)
>In einer Schule gehören $\frac{2}{3}$ der Schüler zur Sekundarstufe I und $\frac{1}{3}$ der Schüler zur Sekundarstufe II. 20% der Schüler der Stufe I und 30% der Schüler der Stufe II kommen mit dem Bus zur Schule.
>>[!note] Wissen: 3.5 Definition der bedingten Wahrscheinlichkeit
>
>>[!note]- Vorbereitung und Überlegung
>>Zunächst einigen wir uns wieder auf eine Symbolik. Ein Schüler...
>>- $S_1$ - gehört zu Sekundarstufe 1
>>- $\overline{S_{1}}$ - gehört nicht zu Sekundarstufe 1 (gehört zu Sekundarstufe 2)
>>- $B$ - fährt mit dem Bus
>>- $\overline{B}$ -  fährt nicht mit dem Bus
>>
>>Wir fassen die gegebenen Informationen wie folgt zusammen
>>$$\begin{align}
>> P(S_{1}) &= \frac{2}{3} \\ 
>> P(\overline{S_{1}}) &= \frac{1}{3} \\
>> P(B\;|\;S_{1})&= \frac{1}{5} \\
>> P(B\;|\; \overline{S_{1}}) &= \frac{3}{10}
>>\end{align}$$
>>>[!note]- Wir haben ein vollständiges System an Ereignissen
>>>![[figures/Pasted image 20240329181952.png|center]]
>>>Wir können dies mathematisch prüfen mit **Definition 3.27**
>>>$$\begin{align}
>>> S_{1} \cup \overline{S_{1}} &= \Omega \\ \\
>>> S_{1} \cap \overline{S_{1}} &= \emptyset
>>>\end{align}$$
>1. Berechnen Sie den Anteil der Schüler dieser Schule, die mit dem Bus zur Schule kommt.
>
>>[!example]- Lösung
>>Gesucht ist die Wahrscheinlichkeit
>>$$P(B)$$
>> Dies lässt sich mit dem **Satz der totalen Wahrscheinlichkeit (Satz 3.28)** lösen. Wir erhalten die Formel
>> $$\begin{align}
>> P(B) &= P(B\;|\;S_{1})P(S_{1}) + P(B\;|\;\overline{S_{1}})P(\overline{S_{1}}) \\
>>      &= \frac{1}{5} \cdot \frac{2}{3} + \frac{3}{10} \cdot \frac{1}{3} \\
>>      &= \frac{7}{30} \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. Ein Schüler, der mit dem Bus zur Schule kommt, wird zufällig ausgewählt. Mit welcher Wahrscheinlichkeit ist er ein Schüler der Sekundarstufe I?
>
>>[!example]- Lösung
>>Gesucht ist die Wahrscheinlichkeit 
>>$$P(S_{1}\;|\;B)$$
>>Wir verwenden dazu **Satz 3.16** mit dem Ergebnis aus Teilaufgabe 1 $P(B)=\frac{7}{30}$ und erhalten
>>$$\begin{align}
>> P(S_{1}\;|\;B) &= \frac{P(S_{1})}{P(B)}P(B\;|\;\overline{S_{1}}) \\
>>   &= \frac{\frac{2}{3}}{\frac{7}{30}}\cdot \frac{3}{10} \\
>>   &=\frac{4}{7} \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (4)
>$\frac{7}{10}$ der Studenten bestehen die Prüfung in Mathematik 1 und $\frac{8}{10}$ der Studenten bestehen die Prüfung in Mathematik 3. Die Wahrscheinlichkeit für das Bestehen beider Klausuren liegt bei $0.6$.
>>[!note]- Wissen
>> - (Basis) Mengenlehre
>> - 3.1 Axiomatische Definition der Wahrscheinlichkeit
>> - 3.6 Unabhängigkeit zufälliger Ereignisse
>
>>[!note]- Vorbereitung und Überlegung
>>Zunächst einigen wir uns wieder auf eine Symbolik
>>- $M_{1}$ - Student besteht Prüfung Mathematik 1
>>- $\overline{M_{1}}$ - Student besteht Prüfung Mathematik 1 nicht
>>- $M_{3}$ - Student besteht Prüfung Mathematik 3
>>- $\overline{M_{3}}$ - Student besteht Prüfung Mathematik 3 nicht
>>
>>und führen die gegebenen Informationen auf
>>$$\begin{align}
>> P(M_{1}) &= \frac{7}{10} \\
>> P(\overline{M_{1}}) &= \frac{3}{10} \\
>> P(M_{3}) &= \frac{8}{10} = \frac{4}{5}\\
>> P(\overline{M_{3}}) &= \frac{2}{10} = \frac{1}{5} \\
>> P(M_{1} \cap M_{3}) &= \frac{6}{10}= \frac{3}{5}
>>\end{align}$$
>
>1. Sind die Ereignisse "Studierende bestehen die Prüfung in Mathematik 1" und "Studierende bestehen die Prüfung in Mathematik 3" stochastisch unabhängig?
>
>>[!example]- Lösung
>>Wir lösen die Aufgabe mit **Definition 3.19**, sofern die Ereignisse stochastisch unabhängig sind, muss gelten
>>$$P(M_{1} \cap M_{3}) = P(M_{1})P(M_{3})$$ 
>>wir müssen lediglich noch die gegebenen Größen einsetzen und prüfen
>>$$\begin{align}
>> \frac{3}{5} &\neq \frac{7}{10} \cdot \frac{4}{5} \\
>>   &\neq \frac{14}{25}
>>\end{align}$$
>>Daher sind die Ereignisse **stochastisch abhängig**.
>>$$\tag*{$\blacktriangleleft$}$$
>
>2. Wie ist die Wahrscheinlichkeit in der Prüfung Mathematik 3 durchzufallen, wenn Mathematik 1 bestanden wurde?
>
>>[!example]- Lösung
>> In dieser Aufgabe ist folgender Term gesucht
>> $$P(\overline{M_{3}}\; | \; M_{1})$$
>> Wir verwenden dazu **Definition 3.15** und verwenden dazu die gegebenen Größen
>> $$P(B\;|\;A) = \frac{P(A \cap B)}{P(A)}\quad \Longleftrightarrow \quad P(M_{3}\;|\;M_{1}) = \frac{P(M_{3} \cap M_{1})}{P(M_{1})}$$
>> Wir berechnen
>> $$\begin{align}
>> P(M_{3}\;|\;M_{1}) &= \frac{\frac{6}{10}}{\frac{7}{10}} \\
>>  &= \frac{6}{7}
>>\end{align}$$
>>>[!note]- Bemerkung zum Komplement einer bedingten Wahrscheinlichkeit
>>> Wie können wir das Komplement in der bedingten Wahrscheinlichkeit erklären? 
>>> 
>>> Wir haben gegenwärtig einen Elementarereignisraum, der wie folgt aussieht
>>> $$\Omega = \{ M_{1}, \overline{M_{1}}, M_{3}, \overline{M_{3}} \}$$
>>> Wenn wir uns die bedingte Wahrscheinlichkeit ansehen, dann gehen wir davon aus, dass wir ein geordnetes, zweistelliges Ereignis haben, also sehen alle möglichen Ereignisse für eine beliebige bedingte Wahrscheinlichkeit wie folgt aus
>>> $$\{ (M_{1},M_{3}), (M_{1}, \overline{M_{3}}), (\overline{M_{1}}, M_{3}), (\overline{M_{1}}, \overline{M_{3}}) \}$$
>>> wobei wir sagen, dass zum Beispiel bei $(M_{1},M_{3})$  das Ereignis $M_1$ vor $M_3$ eingetreten ist. Wenn wir bei einer bedingten Wahrscheinlichkeit die Bedingung beispielsweise mit $M_1$ fixieren (also wir setzen voraus, dass es eingetreten sein muss), verkleinert sich der Elementarereignisraum der zweistelligen Ereignisse demnach auf 
>>> $$\Omega^B = \{ (M_{1},M_{3}), (M_{1},\overline{M_{3}}) \}$$
>>> Daher können wir sagen
>>> $$P(M_{3}\;|\;M_{1}) +P(\overline{M_{3}}\;|\;M_{1}) = 1$$
>>
>> Die gesuchte Größe ist die komplementäre Wahrscheinlichkeit von $P(M_{3}\;|\;M_{1})$, also erhalten wir 
>> $$\begin{align}
>> P(\overline{M_{3}}\; | \; M_{1}) &= 1 -P(M_{3}\;|\;M_{1}) \\
>>   &= \frac{1}{7} \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>3. Wie groß ist die Wahrscheinlichkeit, dass eine Prüfung bestanden wird?
>
>>[!example]- Lösung 
>>Dass eine Prüfung bestanden wurde heißt sinngemäß, dass ** mindestens eine Prüfung bestanden wurde**. Wir erwarten also, dass ein Student $s$, der diese Attribute erfüllt, wie folgt charakterisiert werden kann.
>>$$s \in M_{1} \lor s \in M_{3}$$
>>Dies entspricht der Definition der Vereinigung von zwei Mengen $M_{1}, M_{2} \subseteq \Omega$, also
>>$$M_{1} \cup M_{3} := \{ s \in M_{1} \lor s \in M_{3} \; |\; \forall s \in \Omega \}$$
>>Mengentheoretisch können wir den Sachverhalt wie folgt illustrieren
>>![[figures/Pasted image 20240331183534.png| center | 400]]
>>Wir berechnen demnach die Wahrscheinlichkeit, dass beide Ereignisse eintreffen können, also $P(M_{1} \cup M_{3})$.
>>
>>Nehmen wir an, dass 
>>$$P(M_{1} \cup M_{3}) = P(M_{1}) + P(M_{3}) \dots \tag{Unvollständig!}$$
>>die gesuchte Größe darstellt. Wir bemerken, dass der Schnitt zwischen $M_1$ und $M_3$ doppelt dargestellt wird (rot schraffiert), da er über beide Ereignisse enthalten ist. Daher müssen wir die Wahrscheinlichkeit des Schnitts zwischen den beiden Mengen abziehen, um die Wahrscheinlichkeit der Vereinigung zu erhalten, also
>>$$P(M_{1} \cup M_{3}) = P(M_{1}) + P(M_{3}) - P(M_{1} \cap M_{3})$$
>>wir erhalten
>>$$\begin{align}
>> P(M_{1} \cup M_{3}) &= \frac{7}{10} + \frac{4}{5} - \frac{3}{5} \\
>>   &= \frac{9}{10} \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>4. Wie groß ist die Wahrscheinlichkeit, dass keine der beiden Prüfungen bestanden wird?
>
>>[!example]- Lösung
>>Wir wollen nun darstellen, dass ein Student $s$ keine Prüfung bestanden hat. Mengentheoretisch haben wir
>>$$s \in \overline{M_{1}} \land s \in \overline{M_{3}}$$
>>Dies entspricht der Definition des Durchschnitts, also für $\overline{M_{1}}, \overline{M_{3}} \subseteq \Omega$
>>$$\overline{M_{1}} \cap \overline{M_{3}} := \{ s \in \overline{M_{1}} \land s \in \overline{M_{3}} \; | \; s \in \Omega \}$$
>>Nach den De Morgan'schen Gesetzen haben wir
>>$$\overline{M_{1}} \cap \overline{M_{3}} = \overline{(M_{1} \cup M_{3})}$$
>>Daher können wir mathematisch sauber begründen, weshalb wir hier über das Komplementärereignis von Aufgabe 4.3 sprechen. Wir können dies wie folgt illustrieren.
>>![[figures/Pasted image 20240331185525.png| center | 400]]
>>Die gelbe Fläche stellt hierbei das gesuchte Ereignis dar, und die blaue Fläche repräsentiert das Ereignis aus Aufgabe 4.3. Daher können wir die gesuchte Wahrscheinlichkeit wie folgt berechnen
>>$$\begin{align}
>> P(\overline{M_{1}} \cap \overline{M_{3}}) &= 1 - P(M_{1} \cup M_{3}) \\
>>  &= 1 - \frac{9}{10} \\
>>  &= \frac{1}{10} \tag*{$\blacktriangleleft$}
>>\end{align}$$


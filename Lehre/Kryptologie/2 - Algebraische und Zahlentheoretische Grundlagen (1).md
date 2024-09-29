>[!remark] Bemerkung
> Damit eine analytische Auseinandersetzung mit asymmetrischen Verschlüsselungsverfahren möglich ist, führen wir zunächst gruppen- (Abstrakte Algebra) und zahlentheoretische Grundlagen ein

## 2.1 Algebraische Grundlagen

^f42169

>[!def] Definition Natürliche und ganze Zahlen
>>[!tip] Wir einigen uns auf folgende Notation
>$$\begin{align}
> \mathbb{N} &= \{ 1,2,3,\dots \} \tag{Natürliche Zahlen} \\
> \mathbb{N}_{0} &= \{ 0,1,2,3,\dots \} \tag{Nichtnegative Ganze Zahlen} \\
> \mathbb{Z} &= \{ \dots,-3,-2,-1,0,1,2,3,\dots \} \tag{Ganze Zahlen}
>\end{align}$$

^f52c1d

>[!def] Definition Zweistellige Operation ([[../../PDFs/judson2022.pdf#page=33|Quelle]]) 
>Eine zweistellige Abbildung $\circ$ auf einer Menge $G$ ist definiert als **<u>zweistellige Operation</u>**, wenn gilt
>$$G \times G \to G$$
>
>>[!remark] Bemerkung
>> Diese Definition sagt aus, dass wir eine Operation nur dann so bezeichnen dürfen, wenn wir zwei Elemente einer Menge mit dieser Operation verknüpfen und dann in jedem Fall ein Element derselben Menge herauskommen muss.
>
>>[!example]- Beispiel 1 $+$ auf $\mathbb{N}$ (Addition)
>> Sei + eine zweistellige Operation auf $\mathbb{N} = \{ 1,2,3\dots \}$. Die Operation sei die uns aus dem Alltag bekannte Addition. Für jede beliebige natürliche Zahl $n_{1}, n_{2}, n_{3}$ gilt:
>> $$n_{1}+n_{2} = n_{3} \in \mathbb{N}$$
>
>> [!example]- Beispiel 2 $-$ auf $\mathbb{N}$ (Subtraktion)
>> Die zweistellige Abbildung $-$ auf $\mathbb{N} = \{ 1,2,3\dots \}$, welche uns als die alltägliche Subtraktion bekannt ist, bildet keine zweistellige Operation, weil für $n_{1}=4$ und $n_{2}=5$ erhalten wir
>> $$n_{1} - n_{2} = 4-5= -1 \not\in \mathbb{N}$$

^ef0786

>[!def] Definition Gruppe (Algebraische Struktur) ([[../../PDFs/judson2022.pdf#page=33|Quelle]])
>Sei $\circ$ eine beliebige Operation auf der Menge $G$. Wir bezeichnen $(G, \circ)$ als **<u>Gruppe</u>**, wenn die Menge $G$ die folgenden Eigenschaften erfüllt
>1. $G$ ist **assoziativ**, das heißt $\forall x_{1},x_{2},x_{3} \in G$:
> $$(x_{1} \circ x_{2})\circ x_{3} = x_{1}\circ (x_{2} \circ x_{3})$$
> 2. $G$ besitzt genau ein **neutrales Element**, das heißt $\exists! e \in G$, sodass $\forall x \in G:$
>  $$x \circ e = e \circ x = x$$
>  3. $G$ besitzt jeweils genau ein **inverse Elemente**, das heißt $\forall x \in G: \exists! x^{-1} \in G$, sodass
>   $$x \circ x^{-1} = x^{-1} \circ x = e$$
> ---
>Wenn zusätzlich gilt
> 
>4. $G$ ist **kommutativ**, das heißt $\forall x_{1}, x_{2} \in G$:
> $$x_{1} \circ x_{2} = x_{2} \circ x_{1}$$
> 
> dann nennen wir $(G, \circ)$ eine **<u>kommutatitve (oder auch abel'sche) Gruppe</u>**
>
>>[!example]- Beispiel $(\mathbb{R}, +)$ 
>>$(\mathbb{R}, +)$ bildet eine kommutatitive Gruppe mit
>>$$\begin{align}
>> e &= 1 \\
>> x^{-1} &= \frac{1}{x} \tag*{$\forall x \in \mathbb{R}$}
>>\end{align}$$
>>und den Eigenschaften Assoziativität und Kommutativität
>
>>[!example]- Beispiel $(GL, \cdot)$
>>Sei die Menge $GL \subset \mathbb{R}^{n \times n}$ der Raum aller invertierbaren Matrizen (das heißt das inverse Element existiert für jede Matrix), dann bildet $(GL, \cdot)$ eine Gruppe, die **nicht kommutativ** ist. Das neutrale Element ist gegeben als die Identitätsmatrix
>>$$I = \begin{pmatrix}
>>1 & 0 & \dots & 0  \\
>>0 & 1  & \dots & 0 \\
>>\vdots & \vdots & \ddots & \vdots \\
>> 0 & 0 & \dots & 1
>>\end{pmatrix}$$
>>Kommutativität gilt nicht für jede Matrix
>>>[!example]- Übung
>>> Sei $A = \begin{pmatrix}
>>> 3 & 2 \\ 
>>> 1 & 3
>>>\end{pmatrix}$ und $B = \begin{pmatrix}
>>> 4 & 4 \\ 4 & 4
>>>\end{pmatrix}$. Bestimmen Sie
>>>$$\begin{align}
>>> (1) \qquad &A \cdot B \\
>>> (2)\qquad &B \cdot A
>>>\end{align}$$
>>>und verifizieren Sie
>>>$$A \cdot B \neq B \cdot A$$

^afad91

>[!def] Definition Äquivalenrelation
>Eine Relation $\sim$ auf einer Menge $G$ heißt **Äquivalenzrelation**, wenn folgende Eigenschaften auf der Relationsmenge $R \subseteq G \times G$ erfüllt sind
>1. Reflexitivität: $\forall x_{1} \in G: (x_{1},x_{1}) \in R$
>2. Symmetrie: $\forall x_{1}, x_{2} \in G: (x_{1},x_{2}) \in R \implies (x_{2},x_{1}) \in R$
>3. Transitivität: $\forall x_{1},x_{2},x_{3} \in G: (x_{1},x_{2}) \in R \; \land (x_{2}, x_{3}) \in R \implies (x_{1},x_{3}) \in R$
>
>>[!remark]- Bemerkung zur Handhabung der Eigenschaften
>>Implikationen sind nur dann falsch, wenn die Prämisse wahr ist und die Schlussfolgerung falsch. 
>>
| $A$ | $B$ | $A \implies B$ |
| --- | --- | -------------- |
| 0   | 0   | 1              |
| 0   | 1   | 1              |
| 1   | 0   | 0              |
| 1   | 1   | 1               |
>>Das heißt, für Symmetrie und Transivität suchen wir Aussagen, die für $A$ wahr ergeben und $B$ falsch ergeben, um zu zeigen, dass es sich um keine Äquivalenzrelation handelt.
>
>>[!example]- Beispiel Operation $=$ auf $\mathbb{R}$
>>Die Relationsmenge für die Gleichheit von Zahlen in $\mathbb{R}$ ist gegeben als 
>>$$R = \{ (x,x) \; | \; x \in \mathbb{R} \} \subset \mathbb{R} \times \mathbb{R}$$
>>Diese ist reflexiv, symmetrisch und transitiv. Als Übung kann dies überprüft werden.

^8daf7c

## 2.2 Modulo und Ganzzahlige Teilung

>[!def] Definition Ganzzahlige Teilung
>Für den Ausdruck mit $a,b \in \mathbb{Z}$ $$a \text{ teilt } b$$ schreiben wir $$a \; | \; b$$ Das heißt
>$$a \; | \; b: \iff \exists k \in \mathbb{Z}: b = k\cdot a$$
>Wir nennen $a$ den **Teiler** von $b$  
>---
>Sofern $a$ die Zahl $b$ nicht teilt schreiben wir analog $a \; \not\mid b$

^9380e8

>[!property] Eigenschaften der Ganzzahligen Teilung
>Für **alle** $a,b,c,n \in \mathbb{Z}$ gilt:
>1. $a \;|\; a$ <span class="right-float">(Reflexivität)</span>
>2. $a \;|\; b \;\land\; b \;|\; c \; \implies \; a \;|\; c$ <span class="right-float">(Transitivität)</span>
>3. $n\;|\;a \implies n \;|\; ab$
>
>>[!proof]- Beweis
>> 1. Siehe Übung
>> 2. Zu zeigen ist $a \;|\; b \;\land\; b \;|\; c \; \implies \; a \;|\; c$
>> 
>> 	
>> Zunächst setzen wir für die Teile der Prämisse die [[#^9380e8|Definition ganzzahliger Teilung]] ein und erhalten
>> 	
>> $$\begin{align}
>> a \;|\; b &:= \exists k_{1}\in\mathbb{Z} : b = ak_{1} \tag{1}\\
>> b \;|\; c &:= \exists k_{2}\in \mathbb{Z}: c = bk_{2} \tag{2}
>>\end{align}$$
>>
>>Wir stellen Gleichung $(2)$ nach $b$ um und erhalten
>>$$\begin{alignat}{2}
>> c &= bk_{2} \qquad&&\Big\vert :k_{2} \\
>> b &= \frac{c}{k_{2}} \tag{3}
>>\end{alignat}$$
>> Gleichungen $(1)$ und $(3)$ drücken beide $b\in\mathbb{Z}$ aus somit können wir diese gleichsetzen und erhalten
>> $$\begin{align}
>> \frac{c}{k_{2}} &= ak_{1}
>>\end{align}$$
>>Durch geschicktes Umstellen erhalten wir die [[#^9380e8|Definition ganzzahliger Teilung]] für $c \in \mathbb{Z}$
>>$$\begin{alignat}{2}
>> \frac{c}{k_{2}} &= ak_{1} \qquad&&\Big\vert \cdot k_{2} \\
>> c &= \underbrace{ k_{1}k_{2} }_{ =k_{3} \in Z }a \\
>> \implies c&=k_{3}a := a \;|\; c \tag*{$\square$}
>>\end{alignat}$$
>>	
>> 3. Siehe Übung

^6a2086

>[!theorem] Satz Teibarkeit von Summen und Differenzen
>Seien $a,b,n \in \mathbb{Z}, n \neq 0$ mit $n\;|\;a$ und $n\;|\;b$, dann gilt auch
>$$n\;|\;a+b \text{ und } n\;|\;a-b$$
>
>>[!proof]- Beweis
>> Wir verwenden die [[#^9380e8|Definition ganzzahliger Teilung]] und können festhalten
>> $$\begin{align}
>> n\;|\;a &:= \exists k_{1} \in \mathbb{Z}: a = k_{1}n \tag{1}\\
>> n\;|\;b &:= \exists k_{2} \in \mathbb{Z}: b = k_{2}n \tag{2} \\
>>\end{align}$$
>>Wir addieren nun die Ausdrücke entsprechend der Behauptung aus dem behaupteten Satz und verwenden die in $(1)$ und $(2)$ bestimmten Ausdrücke und erhalten
>>$$\begin{alignat}{2}
>> a\pm b &= k_{1}n \pm k_{2}n \\
>> a\pm b &= n(k_{1} \pm k_{2}) \qquad&&\Big\vert :n \\
>> \frac{a\pm b}{n} &= k_{1} \pm k_{2}
>>\end{alignat}$$
>>Die Addition bzw. Subtraktion von zwei ganzen Zahlen $k_{1},k_{2}$ ergeben wieder eine ganze Zahl, somit ergibt die Operation $\frac{a\pm b}{n}$ eine ganze Zahl. Demzufolge geht die Division auf und $n$ ist ein Teiler von $a \pm b$, was zu zeigen war.
>>$$\tag*{$\square$}$$

^a40b0b

>[!def] Definition Binäre Modulus Operation 
> Sei $\text{mod}$ eine zweistellige Operation auf $\mathbb{Z}$ und definiert mit $a,b \in \mathbb{Z}$
> $$\text{mod}(a,b) = a \text{ mod } b = r$$
> wobei $r$ als **Rest** für $a = b \cdot q+r$ und $0 \leq r < \lvert b \rvert$ bezeichnet wird.
>>[!remark] Bemerkung
>> Die Modulus-Operation gibt den Rest der ganzzahligen Division von $a$ durch $b$ zurück:
>> $$\frac{a}{b}= q  \; (\text{Rest } r)$$
>
>>[!example]- Beispiel $10 \text{ mod } 3$
>>$$10 \text{ mod } 3 = 1$$
>>weil
>>$$\frac{10}{3} = 3 \;(\text{Rest }1)$$
>>da
>>$$3 \cdot 3 + 1 = 10 \tag*{$\blacktriangleleft$}$$

^9cd06c

>[!theorem] Satz Existenz und Eindeutigkeit des Quotienten und Rests ([[../../PDFs/judson2022.pdf#page=32|Quelle]])
>Seien $a,b \in \mathbb{Z}$ mit $b \neq 0$. Dann gibt es eindeutig bestimmte Zahlen $q,r \in \mathbb{Z}$ mit
>$$\begin{align}
> a &= qb + r \\
> 0 & \leq r < \lvert b \rvert 
>\end{align}$$
>
>>[!proof]- Beweis
>><u>Beweis zur Existenz</u>
>>
>>>[!remark]- Info zum Wohlordnungsprinzip
>>>
>>>Das Wohlordnungsprinzip ist ein wichtiges Element für den Beweis. Es besagt, dass jede nicht-leere Menge, die aus Elementen der natürlichen Zahlen besteht, es ein kleinstes Element geben muss. 
>>>
>>>Nehmen wir beispielsweise die [[#^f52c1d| natürlichen Zahlen]] selbst, wissen wir mit Gewissheit, dass $1$ das kleinste Element ist. Entfernen wir sukzessive die kleinsten Zahlen der Menge, wird immer eine andere kleinste Zahl übrig bleiben.
>>
>>>[!remark]- Info Vorzeichen Funktion $\text{sgn}$ 
>>>Die Vorzeichen Funktion gibt für eine Zahl $a \in \mathbb{R}$ ihr Vorzeichen zurück
>>>$$\begin{align}
>>> \text{sgn}&: \mathbb{R} \to \{ -1,0,1 \} \\[1em]
>>> \text{sgn}&(a)= \begin{cases}
>>> -1 &\text{ wenn } a < 0 \\
>>> 0 & \text{ wenn } a = 0 \\
>>> 1 & \text{ sonst}
>>>\end{cases}
>>>\end{align}$$
>>
>>Sei $$T = \{ a-qb \;|\; q \in \mathbb{Z} \} \cap \mathbb{N}_{0}$$
>>$T$ ist definitiv nicht leer und nicht negativ, daher gibt es nach dem Wohlordnungsprinzip ein kleinstes Element
>>$$r = \min T \tag{1}$$
>>Dieses $r$ ist nach der Beschreibung der Menge $T$ für ein spezielles $\widehat{q} \in \mathbb{Z}$ beschrieben als
>>$$r= a-\widehat{q}b$$
>>mit $r \geq 0$.
>>
>>Unsere Strategie von hieran ist einen Widerspruch zu erzeugen. Daher nehmen wir an, dass $$r \geq \lvert b \rvert \tag{2}$$ gilt, was zu unserer zu beweisenden Aussage gegenteilig ist. Wir *konstruieren ein $r'$*, was einen Widerspruch erzeugt
>>
>>$$\begin{align}
>> r' &= \underbrace{ r }_{ = a-\widehat{q}b} +\lvert b \rvert \tag{3} \\
>> &= a-\widehat{q}b + \lvert b \rvert \\
>> &= a- \underbrace{ (\widehat{q}-\text{sgn}(b)) }_{ =q' }b  \tag{siehe Info}\\
>> &= a- q'b
>>\end{align}$$
>> Da $q' \in \mathbb{Z}$ wissen wir, dass $r' \in T$ maßgeblich nach unserer Konstruktion in $T$ ist. 
>> 
>> Wir fassen nun zusammen, was wir nach unseren Annahmen zusammengetragen haben
>> $$\underbrace{ r' \geq \min{T} = r }_{ \text{nach }(1) } =\underbrace{ r'+\lvert b \rvert }_{ \text{nach } (3)} \underbrace{ \geq r' }_{ \text{nach (2)} } $$
>> was ein Widerspruch ist, somit ist die Existenz von $q$ und $r$ bewiesen
>> $$\tag*{$\square$}$$
>> 
>><u>Beweis Eindeutigkeit</u>
>>Auch hier wenden wir das Prinzip des Widerspruchbeweises an. Dazu nehmen wir an, dass die Existenz der Elemente $q,r \in \mathbb{Z}$ nicht eindeutig ist und dass es andere Elemente $q',r' \in \mathbb{Z}$ existieren mit
>>$$\begin{align}
>> q' \neq q &\text{ und } r' \neq r \\
>>\end{align}$$
>>sodass ebenfalls
>>$$\begin{align}
>> a = q'b + r' \text{ und } 0 \leq r' < \lvert b \rvert 
>>\end{align}$$
>>gilt. Somit lässt sich laut der Annahme unseres Beweises das Element $a$ auf zwei verschiedene Weisen ausdrücken, nämlich
>>$$\begin{align}
>> a&=qb+r \\
>> a&=q'b+r' \\
>>\end{align}$$
>>Diesen können wir nun gleich setzen und erhalten
>> $$\begin{alignat}{2}
>> qb+r &= q'b+r' \qquad&&\Big\vert -r'-qb \\
>> r - r' &= q'b -qb\\
>> r - r' &= (q' -q)b\\
>>\end{alignat}$$
>>Dies entspricht der [[#^9380e8| Definition der ganzzahligen Teilung]], sodass
>>$$b \;|\;(r-r')$$
>>Aufgrund der Eigenschaften festgehaltenen Eigenschaften von $r,r' \in \mathbb{Z}$ schlussfolgern wir, dass
>>$$\lvert r-r' \rvert \leq \underset{}{\text{max}}(r,r') < \lvert b \rvert \; $$
>>Da die Differenz von $r,r'$ in ihrem Betrag kleiner als der Betrag von $b$ ist, kann unmöglich das Produkt $(q'-q)b$ diese Differenz ergeben, außer $r=r'=0$. Da außerdem $b\neq 0$ gilt, muss demzufolge $q'-q=0 \Leftrightarrow q'=q$ ergeben, sodass es keine zwei Elemente $q',r' \in \mathbb{Z}$ geben kann. $$\tag*{$\square$}$$

^30b120

>[!def] Definition Kongruenz-Äquivalenzrelation über den ganzen Zahlen
>Wir definieren die **Kongruenz-Äquivalenzrelation** über den ganzen Zahlen $a,b \in \mathbb{Z}$  kongruent zum **Modul** $n \in \mathbb{N}$ mit
>$$\begin{align}
> a \equiv b \;\;(\text{mod }n) &\iff a \text{ mod } n = b \text{ mod } n \\
>\end{align}$$
>
>
>>[!remark]- Bemerkung zur Verbindung zur binären Modulo Operation
>>Wir können die Kongruenz auch über den binären Modulo Operator ausdrücken, also
>>$$a \equiv b \;\;(\text{mod } n) \iff a \text{ mod } n = b \text{ mod } n$$ 
>
>>[!remark]- Bemerkung zur verkürzten Notation
>>Fortan ist zu
>>$$a \equiv b \;\;(\text{mod } n)$$
>>eine gültige alternative Notation
>>$$a = b \;\;(\text{mod } n)$$
>>wobei die zuerst eingeführte Notation die präzise Notation ist.
>>
>>>[!failure] Achtung $a = b \;\;(\text{mod } n)$ ist nicht dasselbe wie $a = b \;\;\text{mod } n$ !
>
>>[!example]- Beispiel
>>Wir wählen das Modul $n=10$ und die ganzen Zahlen $a=8$ und $b=78$. Wir können sagen
>>$$8 \equiv 78 \;\;(\text{mod } 10)$$
>>weil
>>$$\begin{align}
>> 8 &= 0 \cdot 10 + 8 \\
>> 78 &= 7 \cdot 10 +8
>>\end{align}$$

^360a7d

>[!theorem] Satz Teilbarkeit von Äquivalenzen
> Für $a,b,n \in \mathbb{Z}$ mit $n \neq 0$ gilt
> $$
> a \equiv b \;\;(\text{mod }n) \iff n \;|\; (a-b) $$
>>[!proof]- Beweis
>>Alternativ können wir sagen $$\exists q_{1},q_{2} \in \mathbb{Z}: \begin{matrix}
>> a = q_{1}n + r \\
>> b=q_{2}n + r\end{matrix}$$
>> Also, wir können $q_{1},q_{2} \in \mathbb{Z}$ so wählen, dass der Rest $r$ für $a$ und $b$ gleich ist. Dies ist äquivalent zur Definition da, wenn wir nach $r$ umstellen, erhalten wir
>> $$\begin{align}
>> a -q_{1}n &= r \\
>> b - q_{2}n & = r
>>\end{align}$$
>>Daraus folgt
>>$$\begin{alignat}{2}
>> a- q_{1}n &= b -q_{2}n \qquad&&\Big\vert -b +q_{1}n\\ 
>> a-b &= q_{1}n - q_{2}n \\
>> a-b &= n(q_{1}-q_{2}) \qquad&&\Big\vert :n \\
>> \frac{a-b}{n} &= q_{1}-q_{2}
>>\end{alignat}$$
>>Da $q_{1},q_{2}$ beides ganze Zahlen sind, muss demnach der Quotient $\frac{a-b}{n}$ auch eine ganze Zahl sein. Daher muss, wenn $a \equiv b \;\;(\text{mod } n)$ gilt, auch $n \; |\; a-b$ gelten.
>>$$\tag*{$\square$}$$

^291942

>[!def] Definition Äquivalenzklassen bezüglich der Modulus Äquivalenzrelation
> Wir definieren eine [[#^8daf7c|Äquivalenzklasse]] für $a\in \mathbb{Z}$ bezüglich des **Moduls** $n \in \mathbb{N}$ als
> $$[a] = \{ b \in \mathbb{Z} \; | \; a \equiv b \;\;(\text{mod } n) \}$$
> Diese Form der [[#^8daf7c|Äquivalenzklasse]] werden wir fortan 
> <center><b>Restklasse</b></center>
> nennen.

^638cd1

>[!lemma]
>Die [[#^8daf7c|Äquivalenzklassen]] partitionieren $\mathbb{Z}$ vollständig bezüglich des Moduls $n$ in $n$ disjunkte Partitionen.
>
>Wir bezeichnen fortan $\mathbb{Z}_{n}=\{ [0], [1], \dots, [n-1] \}$ als die Menge aller [[#^8daf7c|Äquivalenzklassen]] bezüglich der Kongruenz-Äquivalenzrelation modulo $n$.
>
>>[!example]- Beispiel $\mathbb{Z}_{3}$
>>Für $\mathbb{Z}_{3}$ haben wir 3 Äquivalenzklassen
>>$$\begin{align}
>> [0]_{3} &= \{ \dots, -6,-3,0,3,6,\dots  \} = \{ 3k \; | \; k \in Z \} \\
>> [1]_{3} &= \{ \dots, -5,-2,1,4,7,\dots  \} = \{ 3k +1\; | \; k \in Z \} \\
>> [2]_{3} &= \{ \dots, -4,-1,2,5,8,\dots  \} = \{ 3k +2\; | \; k \in Z \} \\ \\
>>\end{align}$$
>>sodass
>>$$\mathbb{Z}_{3} = \{ [0]_{3}, [1]_{3}, [2]_{3} \}$$
>
>>[!remark] Bemerkung zur Notation
>> Statt 
>> $$\mathbb{Z}_{n} = \{ [0], [1], \dots, [n-1] \}$$
>> schreiben wir fortan
>> $$\mathbb{Z}_{n} = \{ 0,1,\dots,n-1 \}$$
>
>>[!remark]- Bemerkung zur Partitionierung durch Äquivalenzklassen
>>Da die Äquivalenzklassen disjunkt sind, kann ein Element nur einer einzigen Äquivalenzklasse angehören. Seien $a,b \in G$ und es sei eine Äquivalenzrelation $~$ auf $G$ definiert. Dann gilt
>>$$[a] \cap [b] = \emptyset \text{ oder } [a] = [b]$$
>>Außerdem gilt, dass die Äquivalenzklassen die komplette Menge partitionieren. Das bedeutet, seien $[a]_{i}$ alle $n$ Äquivalenzklassen der Menge $G$, dann muss gelten
>>$$\bigcup_{i=1}^n [a]_{i} = G$$
>
>>[!remark]- Bemerkung zur Bezeichnung Restklassen
>>Wir nennen Äquivalenzklassen unter der Modulus Kongruenzrelation auch **Restklassen**.

^91d168

 
>[!remark] Bemerkung zur "Restklassenarithmetik"
> Wir haben nun erfolgreich die [[#^360a7d| Kongruenz Äquivalenzrelation]] als eine [[#^afad91|algebraische Struktur]] eingeführt. Über die [[#^6a2086|Eigenschaften der ganzzahligen Teilung]] und dem [[#^a40b0b| Satz der Teilbarkeit von Summen und Differenzen]] können wir zusammenfassend sagen, dass für $a,b \in \mathbb{Z}$ und dem [[#^638cd1|Modul]] $n \in \mathbb{N}$
> $$\begin{align}
> \Big((a \text{ mod } n) \pm (b \text{ mod } n)\Big) \;\text{mod } n&= (a\pm b) \text{ mod } n  \tag{1} \\
> \Big((a \text{ mod } n) \cdot (b \text{ mod } n)\Big) \;\text{mod } n&= (a\cdot b) \text{ mod } n  \tag{2}
>\end{align}$$
>gilt. Gleichung $(1)$ entsteht aus der [[#^a40b0b| der Teilbarkeit von Summen und Differenzen]] und Gleichung $(2)$ aus der Eigenschaft $3$ in den [[#^6a2086|Eigenschaften der ganzzahligen Teilung]]. Wir können somit auch einfach mit den Restklassen rechnen. Angenommen wir haben das Modul $n$, also demnach die Gruppe $\mathbb{Z}_{n}$, dann können wir analog für Gleichung $(1)$ und $(2)$ in der Form von [[#^91d168|Restklassen]] schreiben
>$$\begin{align}
> [a] \oplus [b] &:= [a+ b] \tag{1} \\
> [a] \ominus [b] &:= [a- b] \tag{1} \\
> [a] \odot [b] &:= [a \cdot b] \tag{2}
>\end{align}$$
>
>In Worten ausgedrückt können wir sagen, dass wir mit den Resten über Summen und Produkten bei gleichem Modul $n$ rechnen dürfen. Die Summe zweier Reste über $a,b$ ist demnach [[#^360a7d|kongruent]] zu dem Rest der Summe $a+b$. Analog gilt selbiges für das Produkt. Dies wird auch **Restklassenarithmetik**  genannt.
>
> ***Diese Eigenschaft ist fundamental für die Verschlüsselungsalgorithmen und deren Funktionsweisen, die über Restklassenringe bzw. Restklassenkörper aufgebaut werden.***

^e40f84

>[!note] Werkzeug: Verknüpfungstafeln (Caley-Tables)
> Addition und Multiplikation in $\mathbb{Z}_{5}$
> 
> ![[Figures/caley_tables.png|center|700]]
>
> Addition und Multiplikation in $\mathbb{Z}_{5}$ (vereinfachte Darstellung)
> 
> ![[Figures/caley_tables_easy.png|center|650]]

>[!property] Eigenschaften der Operationen of $\mathbb{Z}_{n}$
>1. Die [[#^c5cc22|Operation]] $+ : \mathbb{Z}_{n} \times \mathbb{Z}_{n} \to \mathbb{Z}_{n}$ ein, wobei $\forall a,b \in \mathbb{Z}_{n}$ gilt:
 $+$ bildet eine [[#^afad91|kommutative Gruppe]]  $(\mathbb{Z}_{n},+)$
 > 	- ... ist assoziativ
>	- ... es existiert das neutrale Element $e=0$
>	- ... das inverse Element für $a=-a$
>	- ... ist kommutativ
>1. Die [[#^c5cc22|Operation]] $\cdot : \mathbb{Z}_{n}^* \times \mathbb{Z}_{n}^* \to \mathbb{Z}_{n}^*$ ein, wobei $\mathbb{Z}_{n}^*=\mathbb{Z}_{n}\setminus \{ 0 \}$ und für $\forall a,b \in \mathbb{Z}_{n}$ gilt:
 $\cdot$ bildet eine [[#^afad91|kommutative Halbgruppe]]  $(\mathbb{Z}_{n}^*, \;\cdot\;)$
>	- ... ist assoziativ
>	- ... es existiert das neutrale Element $e=1$
>	- ... das inverse Element für $a$ existiert nicht, wenn $a$ und $n$ gemeinsame Teiler haben
>	- ... ist kommutativ
>3. Die [[#^c5cc22|Operation]] $\cdot : \mathbb{Z}_{n}^* \times \mathbb{Z}_{n}^* \to \mathbb{Z}_{n}^*$ ein, wobei $\forall a,b \in \mathbb{Z}_{n}^*$ gilt:
 $\cdot$ bildet eine [[#^afad91|kommutative Gruppe]] $(\mathbb{Z}_{n}^*, \;\cdot\;)$, wenn $n$ eine Primzahl ist
>	- ... das heißt das inverse Element existiert hier für jedes beliebige Element in $\mathbb{Z}_{n}^*$

^916051

---

>[!example] Übungen
>>[!example] Übung (1)
>> Gegeben ist die Gruppe $\mathbb{Z}_{8}$. Bestimmen Sie folgende Ausdrücke
>> $$\begin{align}
>> &(a)\; 6+7 \\
>> &(b) \; 2^{-1}
>>\end{align}$$
>>in $\mathbb{Z}_{8}$.
>
>>[!example] Übung (2)
>>Finden Sie alle $x \in \mathbb{Z}$, sodass
>>1. $3x \equiv 2 \;\;(\text{mod } 7)$
>>2. $5x +1 \equiv 13 \;\;(\text{mod } 23)$
>>3. $5x + 1 \equiv 13 \;\;(\text{mod } 26)$
>>4. $9x \equiv 3 \;\;(\text{mod } 5)$
>>5. $5x \equiv 1 \;\;(\text{mod } 6)$
>>6. $3x \equiv 1 \;\;(\text{mod } 6)$
>>
>>>[!example]- Beispiel (1)
>>> Laut dem [[#^291942| Satz der Teilbarkeit von Kongruenzen]] wissen wir
>>> $$3x \equiv 2 \;\;(\text{mod } 7) \iff 7 \; | \; (3x-2)$$
>>> Das heißt es existiert ein $k \in \mathbb{Z}$, sodass
>>> $$\begin{align}
>>> 3x-2 &= 7k \\
>>> 3x &= 7k +2
>>>\end{align}$$
>>>Wir suchen nun ein $k \in \mathbb{Z}$, sodass der Ausdruck auf der rechten Seite immer durch $3$ teilbar ist. Wir stellen fest, dass die Werte $$\{ \dots,1,4,7, 10,\dots \}$$
>>> dies erfüllen. Wir drücken die Zahlenfolge über $k= 3n + 1$ aus und setzen ein
>>> $$\begin{align}
>>> 3x&=7(3n+1)+2\\
>>> 3x&=21n+9
>>>\end{align}$$
>>>Wir sehen leicht, dass sich beide Seiten nun durch $3$ teilen lassen, und erhalten somit die Lösung
>>>$$\begin{alignat}{2}
>>> 3x&=21n+9 \qquad&&\Big\vert :3 \\
>>> x &= 7n+3 \tag*{$\blacktriangleleft$}
>>>\end{alignat}$$
>
>>[!example] Übung (3)
>>Zeigen Sie die Gültigkeit (Beweis) für die [[#^6a2086|Eigenschaften ganzzahliger Teilung]] (1) und (3) basierend auf der [[#^9380e8|Definition ganzzahliger Teilung]].

---
### Wichtiger Einschub: Beweisverfahren
>[!def] Prinzip Vollständige Induktion ([[../../PDFs/judson2022.pdf#page=29|Quelle]])
>Sei $S(n)$ eine Aussage über den ganzen Zahlen symbolisiert mit $n \in \mathbb{N}$ und angenommen $S(n_{0})$ ist wahr für eine kleinstes $n_{0} \in \mathbb{N}$. Wenn für alle Zahlen $k \in \mathbb{N}$ mit $k\geq n_{0}$ folgt
>$$S(k)\implies S(k+1)$$ 
>dann ist $S(n)$ wahr für alle $n \in \mathbb{N}$ mit $n \geq n_{0}$.
>
>>[!example]- Beispiel Beweisen Sie folgende Identität: $\sum_{k=1}^n k = \frac{n(n+1)}{2}\;:\forall n\in\mathbb{N}$ (Gauß'sche Summenformel)
>>>[!info]- Info: Einordnung und Einleitung
>>> Dieses Beispiel soll möglichst umfangreich sein, um die grundlegende Logik hinter dieser Art Beweis zu demonstrieren. Zunächst erkennen wir, dass unsere Aussage besagt, dass wenn wir alle Zahlen beginnend von $1$ bis $n$ aufsummieren, dass dies gleich $\frac{n(n+1)}{2}$ sein soll. Dies soll laut der Aussage für jede beliebige [[#^f52c1d|natürliche Zahl]] $n$ gelten. Daher bietet sich hier das Beweisschema der **vollständigen Induktion** an. 
>>> 
>>> Gemäß der Beschreibung oben beginnt der Beweis mit dem Induktionsanfang. Wir müssen zunächst ein korrektes $n_{0}$ festlegen, welches die kleinst-mögliche natürliche Zahl ist, die uns durch die Behauptung angeboten wird. Da die Aussage für alle $n \in \mathbb{N}$ gilt, ist es gemäß unserer [[#^f52c1d|Definition der natürlichen Zahlen]] $$n_{0}=1$$ 
>>> 
>>> Daher prüfen wir im **Induktionsanfang**, welcher **immer** durchgeführt werden muss, ob die Behauptung für das kleinste Element $n_{0}$ überhaupt Stand hält. Wenn dies nicht der Fall ist, so ist an dieser Stelle bereits der Beweis abgeschlossen und ein Widerspruch konnte festgestellt werden.
>>> 
>>> Für eine Identitätsaussage prüfen wir ob die linke Seite (left-hand side *LHS*) dasselbe Ergebnis erzeugt wie die rechte Seite (right-hand side *RHS*)
>>
>><u> Induktionsanfang</u>:
>>$$n_{0}=1$$
>>
>>LHS:
>>$$\begin{align}
>>\sum_{k=1}^n \overset{n=1}{=}\sum_{k=1}^1 = 1
>>\end{align}$$
>>RHS:
>>$$\begin{align}
>> \frac{n(n+1)}{2}\overset{n=1}{=} \frac{1(1+1)}{2} = \frac{2}{2}=1
>>\end{align}$$
>> Demzufolge LHS = RHS $$\tag*{$\checkmark$}$$
>> 
>> ---
>> 
>>>[!info]- Info: Weiterführende Logik
>>> Häufig wird der kommende Teil weggelassen. Zum Zweck des besseren Verständnisses wird die **Induktionsbehauptung** trotzdem hier eingeführt. Die Induktionsbehauptung ist die **Prämisse** für unseren **Induktionsschluss**. Das Prinzip besagt
>>> $$\underbrace{ \underbrace{ S(k) }_{ \text{Prämisse} } \implies \underbrace{ S(k+1) }_{ \text{Implikation} } }_{ \text{Induktionsschluss} }$$
>>> Demnach tut es keinen Schaden formal vollständig die Prämisse nochmal aufzuführen, um strategisch die Verbindung von der Prämisse zur Implikation darzustellen. In der Literatur findet man auch, dass an dieser Stelle die Laufvariable $n$ für eine bessere Separation von Behauptung zu Beweis ausgetauscht wird. Wir verzichten auf diese Praxis.
>>
>> <u> Induktionsbehauptung</u>: $S(n)$
>> $\forall n \in \mathbb{N}$:
>> $$\sum_{k=1}^n k = \frac{n(n+1)}{2}$$
>> 
>> ---
>> 
>>> [!info]- Info: Beweisvorbereitung
>>> Nun bereiten wir den Abschluss des Beweises vor, indem wir unsere Aussage für $S(n)$ so umformulieren, dass diese nun für das Folgeglied unserer Aussage $S(n+1)$ gelten muss. Dafür setzen wir weitesgehend nur an den Stellen, wo $n$ steht ein $n+1$ ein. **Achtung**, es ist besser pauschalt $(n+1)$ immer in Klammern einzusetzen, um Fehler zu vermeiden.
>>> 
>>> Dieser Teil wird der **Induktionsschritt** genannt, weil wir einen Schritt von unserer **Induktionsbehauptung** weiter gehen, also $n \mapsto n+1$.
>> 
>><u> Induktionsschritt</u>: $S(n+1)$
>>$n \mapsto n+1:\forall n \in \mathbb{N}$:
>> $$\sum_{k=1}^{n+1} k = \frac{(n+1)(n+2)}{2}$$
>>  ---
>> 
>>>[!info]-
>>> Nun kommt der wohl wichtigste Teil der vollständigen Induktion. Wir versuchen nun die Brücke zwischen einem willkürlichen $n>n_{0}$ und einem direkten Nachfolger $n+1$ zu knüpfen. Wir wollen zeigen, dass wenn die Aussage für $n$ gilt (**Induktionsbehauptung**) folgen muss, dass die Aussage auch für $n+1$ gilt (**Induktionsschritt**). 
>>> 
>>> Häufig ist der Trick die $n+1$-Aussage so umzuformen, dass man einen Teil von unserer **Induktionsbehauptung** wieder findet und diese in Verbindung mit dem **Induktionsschritt verwenden**, sodass wir die Aussage vollständig beweisen können. Insgesamt handelt es sich hier um eine Implikations, also
>>> $$S(n) \implies S(n+1)$$ 
>>>Erinnert euch, eine Implikation hat folgende Wahrheitstafel <center>(0 - falsch, 1 - wahr)</center>
>>>$$\begin{align}
>>> \begin{matrix}
>>> A & B & A\implies B \\
>>> 0 & 0 & 1 \\
>>> 0 & 1 & 1 \\
>>> 1 & 0 & 0 \\
>>> 1 & 1 & 1
>>>\end{matrix}
>>>\end{align}$$
>>>Das heißt, wenn wir davon ausgehen, dass $S(n)$ wahr ist, und die Aussage dafür verwenden zu zeigen, dass $S(n+1)$ schlüssig ist, dann ist die Aussage wahr. Denn die einzige Möglichkeit, dass die Aussage falsch wird, ist wenn wir $S(n)$ wahr annehmen und daraus die Gültigkeit von $S(n+1)$ nicht darlegbar ist.
>>>
>>>Wir formen nun $S(n+1)$ so um, dass wir $S(n)$ verwenden können. 
>>
>> <u>Induktionsschluss</u>:
>> $$\begin{align}
>> \underbrace{ \sum_{k=1}^{n+1} k }_{ S(n+1) } &= \underbrace{ \sum_{k=1}^{n} k }_{  S(n)} + (n+1)
>>\end{align}$$
>>Wir setzen die entsprechende Identität von der Induktionsbehauptung $S(n)$ ein
>>$$\begin{align}
>> \phantom{\sum_{k=1}^{n+1} k }\quad\;\;\;\;&= \underbrace{ \frac{n(n+1)}{2} }_{ S(n) } + (n+1)
>>\end{align}$$
>>Mit algebraischen Umformungen erhalten wir
>>$$\begin{align}
>>\phantom{\sum_{k=1}^{n+1} k }\quad\;\;\;\; &= \frac{n(n+1)}{2} + \frac{2(n+1)}{2} \\
>> &=\frac{n(n+1) + 2(n+1)}{2} \tag{Ausklammern}\\
>> &= \frac{(n+2)(n+1)}{2}
>>\end{align}$$
>>Nun haben wir gezeigt, dass wir von der linken Seite unseres Induktionsschrittes über die Induktionsbehauptung auf die rechte Seite schließen können und somit ist die Identität bewiesen.
>>$$\tag*{$\square$}$$
>
>>[!example]- Beispiel Beweisen Sie folgende Aussage: $9\;|\;(10^{n+1}+3 \cdot 10^n +5) \; : \;\forall n \in \mathbb{N}$
>>Wir werden diese Aussage ebenfalls mit vollständiger Induktion beweisen, allerdings verzichten wir hier auf den Umfang wie im vorangegangen Beispiel. Die Aussage besagt, dass jede Zahl $10^{n+1}+3 \cdot 10^n +5$ durch $9$ teilbar ist für jedes beliebige $n \in \mathbb{N}$. Der Induktionsanfang ist somit
>>$$n_{0}=1: \quad 10^2+3\cdot 10^1 + 5 = 135 = 9 \cdot 15 \implies 9  \;|\;135 \tag*{$\checkmark$}$$
>>Wir gehen nun davon aus, dass unsere Hauptaussage (**Induktionsbehauptung**) wahr ist und formulieren den **Induktionsschritt** mit $n \mapsto n+1$
>>$$10^{(n+1)+1}+3 \cdot 10^{n+1}+5 = 10^{n+2}+3 \cdot 10^{n+1}+5$$
>>Wie im Beispiel zuvor versuchen wir im **Induktionsschritt** über die **Induktionsbehauptung** die Aussage zu beweisen.
>>$$\begin{align}
>> 10^{n+2}+3 \cdot 10^{n+1}+5 &= 10^{n+2}+3 \cdot 10^{n+1}+ \underbrace{ 50-45 }_{ =5 } \\
>> &= 10 \underbrace{ (10^{n+1}+3\cdot 10^{n}+5) }_{ \text{durch } 9 \text{ teilbar} } -45
>>\end{align}$$
>>Nach der dritten [[#^6a2086|Eigenschaft der ganzzahligen Teilung]] gilt $9 \;|\; S(n) \implies 9 \;|\; 10 \cdot S(n)$. Offensichtlich ist $9 \;|\; 45$. Nach dem [[#^a40b0b| Satz der Teilbarkeit von Differenzen und Summen]] muss demzufolge $$9 \;|\;10(10^{n+1}+3\cdot 10^{n}+5) - 45$$
>>was die behauptete Aussage beweist. $$\tag*{$\square$}$$
>
>>[!example]- Beispiel Zeigen Sie, dass folgende Relation gilt: $2^n > n+4$ für $n \geq 3$
>> Der **Induktionsanfang** gilt für das kleinst mögliche Element, also $n_{0}=3$. Wir haben
>> $$\underbrace{ 2^3 = 8 }_{ \text{LHS} } > \underbrace{ 7 = 3+4 }_{ \text{RHS} } \tag*{$\checkmark$}$$
>> Der **Induktionsschritt** lautet mit $n \mapsto n+1$
>> $$2^{n+1}>n+5$$
>> Wir verwenden dazu die **Induktionsbehauptung**
>> $$\begin{align}
>> \underbrace{ 2^{n+1} }_{ S(n+1) } &=2 \cdot \underbrace{ 2^n }_{ S(n) } > 2\cdot\underbrace{ (n+4) }_{ S(n) } =2n+8>\underbrace{ n+5 }_{ S(n+1) }
>>\end{align}$$
>>Wichtig ist in dieser Kette von Aussagen zu erkennen, dass
>>$$2n+8>n+5$$
>>für jedes $n \in \mathbb{N}$ wahr ist, und somit die Relation bewiesen ist. $$\tag*{$\square$}$$
>
>>[!example] Übungen
>>**Teilbarkeitsaussagen**
>>>[!example] Übung: Zeigen Sie, dass $6 \;|\; 3^n-3 \;:\; \forall n \in \mathbb{N}$
>>
>>>[!example] Übung: Zeigen Sie, dass $3\;|\;4n^3 - n\;:\; \forall n \in \mathbb{N}$
>>
>>>[!example] Übung: Zeigen Sie, dass $6 \;|\; n^3+5n \;:\; \forall n \in \mathbb{N}$
>>
>>**Summenaussagen**
>>>[!example] Übung: Zeigen Sie, dass $\sum_{k=1}^n k^2 = \frac{n \cdot(n+1) \cdot(2n+1)}{6} \;:\; \forall n \in \mathbb{N}$
>>
>>>[!example] Übung: Zeigen Sie, dass $\sum_{k=1}^n (2k-1) =n^2 \; :\; \forall n\in\mathbb{N}$
>>
>>>[!example] Übung: Zeigen Sie, dass $\sum_{k=0}^n 2^k = 2^{n+1}-1\;:\; \forall n\in\mathbb{N}$

^f974a9

---

## 2.3 Zahlentheoretische Grundlagen

### 2.3.1 Größter Gemeinsamer Teiler

>[!def] Definition Größter Gemeinsamer Teiler ($\text{ggT}$)
>Seien $a,b \in \mathbb{Z}$ mit $a$ oder $b$ ungleich $0$, dann ist der **größte gemeinsame Teiler** von $a,b$ definiert mit
>$$\text{ggT}(a,b):=\underset{}{\text{max}}\;\{ n \in \mathbb{N} \; | \; n \text{ ist Teiler von } a \text{ und } b\}$$
>Die Zahlen $a,b$ heißen **teilerfremd**, falls
>$$\text{ggT}(a,b)=1$$
>
>>[!example] Beispiele
>>1. $\text{ggT}(6,9)=\text{ggT}(-6,9)=\text{ggT}(6,-9)=\text{ggT}(-6,-9)=3$
>>2. Seien $a,b \in \mathbb{Z}$ mit $a \;|\; b$, dann ist $\text{ggT}(a,b)=\lvert a \rvert$
>>3. Für alle $a \in \mathbb{Z}$ gilt $\text{ggT}(a,0)=\text{ggT}(0,a)=\lvert a \rvert$

^2a19a0

>[!theorem] Satz Euklidischer Algorithmus
>Seien $a,b \in \mathbb{Z}$ mit $b \neq 0$, dann gilt
>$$\text{ggT}(a,b) = \text{ggT}(b, a \text{ mod }b)$$
>>[!example]- Beispiel per Rekursion $\text{ggT}(75,70)$
>>$$\begin{align}
>> \text{ggT}(75, 70)&= \text{ggT}(70, 75 \text{ mod } 70) \\
>> &= \text{ggT}(70, 5) \\
>> &= \text{ggT}(5, 70 \text{ mod } 5) \\
>> &= \text{ggT}(5, 0) \\
>> &= 5 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!example]- Beispiel per Rekursion $\text{ggT}(111,43)$
>>$$\begin{align}
>> \text{ggT}(111,43) &= \text{ggT}(43, 111 \text{ mod } 43) \\
>> &= \text{ggT}(43, 25) \\
>> &= \text{ggT}(25, 43 \text{ mod } 25) \\
>> &= \text{ggT}(25, 18) \\
>> &= \text{ggT}(18, 25 \text{ mod } 18) \\
>> &= \text{ggT}(18, 7) \\
>> &= \text{ggT}(7, 18 \text{ mod } 7) \\
>> &= \text{ggT}(7, 3) \\
>> &= \text{ggT}(3, 7 \text{ mod } 3) \\
>> &= \text{ggT}(3, 1) \\
>> &= \text{ggT}(1, 3 \text{ mod } 1) \\
>> &= \text{ggT}(1, 0) \\
>> &= 1 \tag*{$\blacktriangleleft$}
>>\end{align}$$
> 
>>[!example]- Beispiel per Hand berechnet $a=129,b=231$
>>Hier ist eine Variante, die für die Berechnung des [[#^42f9e5|erweiterten euklidischen Algorithmus]] praktisch ist.
>>$$\begin{align}
>> 231 &= \color{lime}129 \color{white}\cdot 1 +\color{\yellow} 102 \\
>> \color{lime}129 &= \color{\yellow} 102 \color{white}\cdot \_\_ + \_\_ \\
>> 129 &= \color{lime}102 \color{white}\cdot 1 +\color{\yellow} 27 \\
>> \color{lime}102 &= \color{\yellow} 27 \color{white}\cdot \_\_ + \_\_ \\
>>102 &= \color{lime}27 \color{white}\cdot 3 +\color{\yellow} 21 \\
>> \color{lime}27 &= \color{\yellow} 21 \color{white}\cdot \_\_ + \_\_ \\
>>27 &= \color{lime}21 \color{white}\cdot 1 +\color{\yellow} 6 \\
>> \color{lime}21 &= \color{\yellow} 6 \color{white}\cdot \_\_ + \_\_ \\
>>21 &= \color{lime}6 \color{white}\cdot 3 +\color{\yellow} 3 \\
>> \color{lime}6 &= \color{\yellow} 3 \color{white}\cdot \_\_ + \_\_ \\
>>6 &= \underbrace{ \color{lime}3 }_{ \text{ggT} } \color{white}\cdot 2 +\color{\yellow} 0 \\
>>\end{align}$$
>>
>
>>[!proof]- Beweis
>> Nach dem [[#^30b120| Satz der Existenz des Quotienten und Rests]] wissen wir $\exists q \in \mathbb{Z}:$
>> $$a = qb+r \text{ mit } 0 \leq r < \lvert b \rvert $$
>> Daher lässt sich der Rest $r$ ausdrücken mit
>> $$r=a-qb$$
>> oder auch
>> $$r=a \text{ mod } b$$
>> daher
>> $$a \text{ mod } b = a -qb$$
>> Damit lässt sich die rechte Seite der Identität ausdrücken mit
>> $$\text{ggT}(b, a \text{ mod } b) = \text{ggT}(b, a-qb)$$
>> Daher können wir die Behauptung umformulieren als
>> $$\text{ggT}(a,b)= \text{ggT}(b, \underbrace{ a-qb }_{ =a \text{ mod }b })$$
>> Für $\text{ggT}(a,b)$ erwarten wir den größten Teiler $n \in \mathbb{N}$ zu finden, sodass $n \;|\; a$ und $n \;|\; b$ ([[#^2a19a0|Definition ggT]]). Nach unserer Umformulierung der Identität muss auch $n \;|\; a-qb$ gelten. Wir können aus der linken Seite der Identität $\text{ggT}(a,b)$ folgern 
>> $$n \;|\; a \land n \;|\; b \underbrace{ \implies }_{ (1) } n \;|\; qb \underbrace{ \implies }_{ (2) } n \;|\; a-qb$$
>> Die Folgerung $(1)$ entspringt der [[#^6a2086|dritten Eigenschaft der Teilung ganzer Zahlen]]. Die Folgerung $(2)$ basiert auf dem [[#^a40b0b| Satz über der Teilbarkeit von Summen und Differenzen]]. Aus diesen Folgerungen können wir zeigen, dass die Identität herstellbar ist
>> $$\begin{align}
>> &n \;|\; b \land n \;|\;a- qb \implies n \;|\; qb \\
>> \implies&(a-qb)+qb = a \tag*{$\square$}
>>\end{align}$$
>
>>[!algo] Implementation in Python $\text{gcd}=\text{ggT}$
>>```python
>>def ggT(a,b):
>>	if b==0:
>>		return abs(a)
>>	else:
>>		return ggT(b, a%b)
>>```
>
>>[!remark]- Bemerkung: Geschichte zu Euklid (Informativ)
>> 322 v. Chr. hat der griechische Herrscher Alexander der Große eine Hauptstadt errichtet. Alexander der Große war Schüler des bekannten Philosophen Aristoteles. Mit dem beinahe simultanen Tod der geschichtlichen Persönlichkeiten wurde Alexendria von dem ägyptischen Herrscher Ptolemy $I$ beherrscht. Dieser hat dort das Museum und die große Bibliothek von Alexendria dort errichtet. Diese Einrichtungen wurden zum Epizentrum der Gelehrten und somit auch der Mathematik. Die Gelehrten zogen durch die damals bekannte Welt und sammelten das Wissen verschiedener Kulturregionen und sammelten diese in Alexandria, sodass es erstmalig in der Menschheitsgeschichte eine universelle Wissensbibliothek der damaligen Erkenntnisse gab.
>> 
>>  Ptolemy $I$ und sein Sohn Ptolemy $II$ unterstützten Gelehrte, sodass diese frei forschen konnten. Einer dieser Gelehrten war **Euklid** gewesen, welcher Autor eines der erfolgreichsten Mathebücher überhaupt war:
>>  
>>  <center> Euklid - Die Elemente (Stoichia)</center>
>> 
>> Es wird behauptet, dass dieses Buch für die Mathematik das sei, was das Alphabet zur Sprache ist. Dort wurden neben der Geometrie auch grundlegende Ideen der Zahlentheorie eingeführt. Buch VII enthielt den Algorithmus zum **größten gemeinsamen Teiler**. Buch IX enthält den noch später in unserer Veranstaltung disktuierten [[#^128d63| Satz zu unendlich vielen Primzahlen]].
>> 
>>  Es wird vermutet, dass Euklid gemeinsam mit Studenten des Platon's studiert haben soll. Euklid hat als Gelehrter damals auch Mathematik unterrichtet. Es gibt eine bekannte Sage zu Euklid. Als ein Student ihn fragte,
>>  
>><center>"welcher Nutze die Mathematik doch haben soll?"</center> 
>>
>>hat Euklid angeblich geantwortet, 
>>
>><center>"man solle dem Student drei Pfennig geben und dies soll sein Nutzen sein".</center>

^e21725


>[!theorem] Satz Lemma von Bezout ([[../../PDFs/judson2022.pdf#page=32|Quelle]])
>Seien $a,b \in \mathbb{Z}$ mit $a,b \neq 0$, dann existieren $a',b' \in \mathbb{Z}$, sodass
>$$\text{ggT}(a,b)=aa'+bb'$$
>
>>[!example]- Beispiel $a=8, b=5$
>>Schauen wir auf das Beispiel, so suchen wir für $a=8$ und $b=5$ zwei ganze Zahlen $a',b' \in \mathbb{Z}$, sodass
>>$$\text{ggT}(8,5)=8a'+5b'$$
>>Wir haben $$\text{ggT}(8,5)=1$$
>>also suchen wir  $a',b' \in \mathbb{Z}$, sodass
>>$$1 = 8a'+5b'$$
>>Durch Probieren lässt sich dieser Fall noch lösen, was aber keine zuverlässige Methode ist. Wir finden $a'=2$ und $b'=-3$ und erhalten
>>$$8 \cdot 2+5 \cdot (-3)=1 \tag*{$\blacktriangleleft$}$$
>>>[!remark] Bemerkung: $8$ und $5$ sind teilerfremd, da $\text{ggT}(8,5)=1$
>
>>[!proof]- Beweis
>>Für diesen Beweis verwenden wir das [[#^f974a9| Prinzip der vollständigen Induktion]]. Wir führen die vollständige Induktion für die Variable $b \in \mathbb{Z}$ aus (in den [[#^f974a9| Beispielen]] war $n$ die Laufvariable zum Beweis). Wir zeigen also für $b$, dass es zu je zwei Zahlen $a,b \in \mathbb{Z}$ ganze Zahlen $a',b'\in \mathbb{Z}$ existieren, sodass
>>$$\text{ggT}(a,b)=aa'+bb'$$
>>Damit wir das [[#^f974a9| Prinzip der vollständigen Induktion]] verwenden können, beschränken wir **ohne Beschränkung der Allgemeinheit (o.B.d.A.)** $b \geq 0$, sodass wir ein kleinstes Element für den Induktionsanfang wählen können. Das Vorzeichen zu beschränken, ändert nichts am Gehalt der Aussage.
>>
>><u>Induktionsanfang</u>:
>>$$\begin{align}
>> b=0\implies \text{ggT}(a,0)&= aa'+b'0 \\
>>   \lvert a \rvert &= aa' + 0 \tag{$b \in \mathbb{Z}$}  \\
>>   \frac{\lvert a \rvert}{a}&=a' \\
>>   \text{sgn}(a) &= a' 
>>\end{align}$$
>>So erhalten wir für $a',b' \in \mathbb{Z}$ die Belegung
>>$$\begin{align}
>> a' &= \text{sgn}(a) \\
>> b' &\in \mathbb{Z} \tag{$b'$ ist beliebig}
>>\end{align}$$
>>$$\tag*{$\checkmark$}$$
>>
>><u> Induktionsschritt</u>:
>>
>>Für den **Induktionsschritt** verwenden wir die rekursive Eigenschaft des $\text{ggT}$, also dass über die Definition fallende Werte zu erwarten sind, sodass $b=0$ erreicht ist den Algorithmus terminiert. Wir verwenden kurz die übliche Denkweise, wie als hätten wir eine konkrete Zählvariable $n$. Wir gehen nicht von $n+1$ wie üblich, sondern von $n-1$ aus, und zeigen, dass sich $a',b' \in \mathbb{Z}$ schlüssig über den Rekursionsschritt $n-1$ und unserer (**Induktions-**)**Behauptung** finden lassen. 
>>
>>Den Schritt rückwärts erzeugen wir über den [[#^e21725| Satz des Euklidischen Algorithmus]] dadurch, dass wir $a$ durch $a \text{ mod } b$ reduzieren, also
>>$$\text{ggT}(a,b)= \text{ggT}(b, a\text{ mod }b)$$
>>Wir wissen, dass $a \text{ mod } b$ den Rest $r$ darstellt, also
>>$$r = a \text{ mod } b$$
>>Diese Eigenschaften können wir verwenden, um die Grundaussage in unserem Rekursionsschritt auszudrücken, also von der **Induktionsbehauptung** auf unseren **Induktionsschritt** zu schließen.
>>$$\begin{align}
>> \text{ggT}(a,b)=\text{ggT}(b, \underbrace{ a \text{ mod } b }_{ \substack{\text{Schritt}\\\text{Rückwärts}} }) = \text{ggT}(b,r)
>>\end{align}$$
>>Nach unserer **Induktionsbehauptung** existieren für $b,r \in \mathbb{Z}$ zwei Zahlen $b*,r* \in \mathbb{Z}$, sodass 
>>$$\text{ggT}(b,r)= b \cdot b^* + r \cdot r^* \tag{1}$$
>> Nach dem [[#^30b120| Satz der Existenz und Eindeutigkeit des Quotienten und Rests]] können wir $a \text{ mod } b = r$ darstellen mit
>> $$r = a\text{ mod }b= a-qb$$
>> Diese Erkenntnis setzen wir in Gleichung $(1)$ ein und erhalten
>> $$\begin{align}
>> \text{ggT}(b,r)&=b \cdot b^* + (a-qb) \cdot r^* \\
>> &= b b^*  - qbr^*+ ar^* \\
>> &= b\underbrace{ (b^* - qr^*) }_{ =b' } + a\underbrace{ r^* }_{ =a' }
>>\end{align}$$
>>Durch den Rekursionsschritt rückwärts (**Induktionsschritt**) finden wir also Lösungen für unsere **Induktionsbehauptung**, und zwar
>>$$\begin{align}
>> b' &= b^* - qr^* \\
>> a' &= r^*
>>\end{align}$$
>>Da wir gezeigt haben, dass der [[#^e21725|Euklidische Algorithmus]] terminiert, wird demzufolge auch der induktive Prozess terminieren und die beschriebenen Lösungen produzieren.
>>$$\tag*{$\square$}$$
>
>>[!remark] Bemerkung: Der erweiterte euklidische Algorithmus liefert die entsprechenden Lösungen.
>
>>[!algo] Implementation in Python: Erweiterter Euklidischer Algorithmus $\text{xgcd}=\text{xggT}$
>> Der erweiterte Euklidische Algorithmus ist ein Lösungsalgorithmus für das Lemma von Bezout. Es folgt der Logik des Beweises.
>> 
>> ```python
>> def sgn(x): 
>> 	if x>0: return 1
>> 	if x < 0: return -1
>> 	return 0
>> 
>> def xggT(a,b):
>> 	if b == 0:
>> 		return abs(a), sgn(a), 0
>> 	q = a//b
>> 	r=a%b
>> 	d, bb, rr = xggT(b,r)
>> 	return d, rr, bb-q*rr
>> ```
>
>>[!example]- Beispiel $a=40902$, $b= 24140$
>>In Sage erhalten wir
>> $$\text{xgcd}(40902, 24140) = (\underbrace{ 34 }_{ =\text{ggT} }, \underbrace{ 337 }_{ =a' }, \underbrace{ 24140 }_{ =b' })$$
>> $$\tag*{$\blacktriangleleft$}$$
> 
>>[!example]- Beispiel per Hand berechnet $a=129,b=231$
>>Um den erweiterten euklidischen Algorithmus einfach zu berechnen, berechnen wir ebenfalls den euklidischen Algorithmus per Hand
>>$$\begin{align}
>> 231 &= \color{lime}129 \color{white}\cdot 1 +\color{\yellow} 102 \tag{1}\\
>> \color{lime}129 &= \color{\yellow} 102 \color{white}\cdot \_\_ + \_\_ \\
>> 129 &= \color{lime}102 \color{white}\cdot 1 +\color{\yellow} 27 \tag{2}\\
>> \color{lime}102 &= \color{\yellow} 27 \color{white}\cdot \_\_ + \_\_ \\
>>102 &= \color{lime}27 \color{white}\cdot 3 +\color{\yellow} 21 \tag{3}\\
>> \color{lime}27 &= \color{\yellow} 21 \color{white}\cdot \_\_ + \_\_ \\
>>27 &= \color{lime}21 \color{white}\cdot 1 +\color{\yellow} 6 \tag{4}\\
>> \color{lime}21 &= \color{\yellow} 6 \color{white}\cdot \_\_ + \_\_ \\
>>21 &= \color{lime}6 \color{white}\cdot 3 +\color{\yellow} 3 \tag{5}\\
>> \color{lime}6 &= \color{\yellow} 3 \color{white}\cdot \_\_ + \_\_ \\
>>6 &= \underbrace{ \color{lime}3 }_{ \text{ggT} } \color{white}\cdot 2 +\color{\yellow} 0 \\
>>\end{align}$$
>>Wir formulieren nun für jede markierte Zeile den Rest (gelb) über den Rest der Gleichung, also
>>$$\begin{align}
>> \color{yellow} 3 &= 21 + \color{lime}6 \color{white}\cdot(-3) \tag{5} \\
>> \color{yellow} 6 &= 27 + \color{lime}21 \color{white}\cdot (-1) \tag{4} \\
>> \color{yellow} 21 &= 102 + \color{lime}27 \color{white}\cdot (-3) \tag{3} \\
>> \color{yellow} 27 &= 129 + \color{lime}102 \color{white}\cdot (-1) \tag{2} \\
>> \color{yellow} 102 &= 231 + \color{lime}129 \color{white}\cdot (-1) \tag{1} \\
>>\end{align}$$
>>Wir stellen fest, dass in Zeile $(5)$ eine $\color{lime}6$ auftaucht und in Zeile $(4)$ ebenfalls eine $\color{yellow}6$ zu sehen ist. Wir setzen den Ausdruck für $\color{yellow}6$ in Zeile $(4)$ in $(5)$ ein und erhalten.
>>$$\begin{align}
>> \color{yellow}3 &= 21+\color{lime}(27-21\cdot 1) \color{white} \cdot (-3)
>>\end{align}$$
>>Wir bemerken, dass die Zahl 21 nun mehrfach auftaucht, daher stellen wir die Gleichung so um, dass die 21 zusammengefasst wird.
>>$$\begin{align}
>> \phantom{\color{yellow}3} &= 21+ 27 \cdot (-3) +21\cdot 3 \\
>> &=\color{lime}21\color{white} \cdot 4 + 27 \cdot (-3)
>>\end{align}$$
>>Dieser Mechanismus lässt sich nun auch für die $\color{lime}21$ wiederholen und sich sukzessive fortführen, bis wir alle Gleichungen abgearbeitet haben.
>>$$\begin{align}
>>3 &=\color{lime}21\color{white} \cdot 4 + 27 \cdot (-3) \\
>> &=\color{lime}\Big(102 + 27 \cdot (-3)\Big)\color{white}\cdot 4 - 27 \cdot (-3) \tag*{ aus $(3)$}\\
>> &= 102 \cdot 4 + 27 \cdot (-12) + 27 \cdot (-3) \\
>> &= 102 \cdot 4 + \color{lime}27\color{white} \cdot (-15) \\
>> &= 102 \cdot 4 + \color{lime}\Big(129 + 102 \cdot (-1)\Big)\color{white} \cdot (-15)  \tag*{ aus $(2)$}\\
>> &= 102 \cdot 4 + 129\cdot (-15) + 102  \cdot 15 \\ 
>> &= \color{lime}102\color{white} \cdot 19 + 129\cdot (-15) \\ 
>> &= \color{lime}\Big(231 + 129 \cdot (-1)\Big)\color{white} \cdot 19 + 129\cdot (-15) \tag*{ aus $(1)$}\\ 
>> &= 231\cdot19 + 129 \cdot (-19) + 129\cdot (-15) \\ 
>> &= 231\cdot19 + 129 \cdot (-34) \\ 
>>\end{align}$$
>>Daher haben wir gefunden
>>$$\text{ggT}(231,129) = 231\cdot19 + 129 \cdot (-34) \tag*{$\blacktriangleleft$}$$
^42f9e5


## 2.3.2 Primzahlen
>[!def] Definition Primzahl ([[../../PDFs/judson2022.pdf#page=22|Quelle]])
>Sei $p \in \mathbb{N}$ mit $p > 1$. Wir nennen $p$ eine **Primzahl**, wenn die einzigen Zahlen, die $p$ ganzzahlig teilen, $p$ selbst und $1$ sind. 

^966cde

>[!theorem] Satz Die Existenz von Unendlich vielen Primzahlen (Euklid) ([[../../PDFs/judson2022.pdf#page=22|Quelle]])
>Es existieren unendlich viel Primzahlen
>>[!proof]- Beweis
>> Wir nutzen für den Beweis das **Widerspruchsverfahren**. Dazu nehmen wir an, dass es nur endlich viele Primzahlen gibt, also die Menge der endlich vielen Primzahlen kann angegeben werden mit
>> $$\mathbb{P} = \{ p_{1}, p_{2}, \ldots, p_{n} \}$$
>> Wir geben nun die Zahl $N$ an mit
>> $$N = p_{1} \cdot p_{2} \cdot \ldots \cdot p_{n} + 1$$
>> Es gibt nun zwei Möglichkeiten über die Beschaffenheit von $N$. Zum einen kann $N$ selbst eine Primzahl sein, was allerdings ein Widerspruch zu unserer Annahme wäre, dass $\mathbb{P}$ eine vollständige Liste aller Primzahlen wäre.
>> 
>> Die andere Möglichkeit ist, dass $N$ eine durch Primzahlen faktorisierte Zahl ist. Also muss es eine Primzahl $p_{i} \in \mathbb{P}$ geben, die $N$ teilt. Wir nehmen an, $p_{i}$ teilt ganzzahlig $P$, also
>> $$\begin{align}
>> \frac{N}{p_{i}} &= \frac{p_{1} \cdot p_{2} \cdot \dots \cdot p_{n} + 1}{p_{i}} \\
>> &= \frac{N}{p_{i}} = \underbrace{ \frac{p_{1} \cdot p_{2} \cdot \ldots \cdot p_{n} }{p_{i}} }_{ \in \mathbb{Z}^+} + \underbrace{ \frac{1}{p_{i}} }_{ \not\in\mathbb{Z} }
>>\end{align}$$
>>Da $\frac{1}{p_{i}}$ keine ganze Zahl sein kann, haben wir auch für diesen Fall einen Widerspruch. Somit muss es unendlich viele Primzahlen geben, da es nicht endlich viele geben kann
>>$$\tag*{$\square$}$$

^128d63

>[!theorem] Satz Fundamentalsatz der Arithmetik ([[../../PDFs/judson2022.pdf#page=22|Quelle]])
>Sei $n \in \mathbb{Z}$ mit $n>1$. Dann lässt sich $n$ _eindeutig_ in seine Primfaktoren
>$$n = p_{1}^{e_{1}} \cdot p_{2}^{e_{2}} \cdot \ldots \cdot p_{k}^{e_{k}}$$
>zerlegen, wobei $p_{i} \neq p_{j}$ mit $i \neq j$ und $e_{i}\in \mathbb{N}$.
>>[!proof]- Beweis 
>><u> Existenz</u>:
>>
>> Die Existenz der Primfaktoren für $n$ zeigen wir mit dem [[#^f974a9| Prinzip der vollständigen Induktion]]. Im **Induktionsanfang** ist das kleinst-mögliche $n=2$, also
>> $$n_{0}=2=\underbrace{ 2^1 }_{ p_{1}=2 } \tag*{$\checkmark$}$$
>> Für den **Induktionsschluss** nehmen wir zunächst an, dass $n$ bereits eine Primzahl ist, so hat die Behauptung bereits bestand, also
>> $$n = \underbrace{ n^1 }_{ =p_{1} }$$
>> Angenommen es existiert eine Primzahl $p$, sodass $p \;|\; n$, dann erhalten wir eine ganze Zahl $n'$, sodass
>> $$n' = \frac{n}{p} \tag{Induktionsschritt}$$
>> Durch simples Umstellen erhalten wir
>> $$n=n'p$$
>> was zeigt, dass $n$ sich in Primfaktoren zerlegen lässt, was zu zeigen war. $$\tag*{$\square$}$$
>> 
>><u> Eindeutigkeit</u>:
>>
>> Wir nehmen nun an, dass es zwei verschiedene Faktorisierungen für $n \in \mathbb{Z}^+$ gibt mit Primzahlen $p_{a}, q_{b}$ 
>> $$n=p_{1}^{s_{1}}\cdot \ldots \cdot p_{j}^{s_{j}} = q_{1}^{r_{1}}\cdot \ldots \cdot q_{k}^{r_{k}}\tag{1}$$
>> mit Exponenten $s_{a},r_{b} \in \mathbb{N}$. Wir nehmen dabei an, dass die $p,q$ verschieden sind und dass $s,r\geq 1$. Wir wollen nun zeigen, dass $j=k$ und für zwei Primzahlen $p_{a} = q_{b}$ und dann auch für die Exponenten $s_{a}=r_{b}$ gilt.
>> 
>> Nach der [[#^8daf7c|Symmetrie der Äquivalenzrelation]] gilt, wenn wir die linke Faktorisierung von Gleichung $(1)$ durch $p_1$ teilen können, so muss das auch für die rechte Seite möglich sein. Also
>> $$\underbrace{ p_{1}\;|\;p_{1}^{s_{1}}\cdot \ldots \cdot p_{j}^{s_{j}} }_{ \text{ wenn } p_{1} \text{ teilt...} } \implies \underbrace{ p_{1} \;|\; q_{1}^{r_{1}}\cdot \ldots \cdot q_{k}^{r_{k}} }_{ \text{dann teilt }p_{1} \text{ auch...} } \implies \underbrace{ \exists q_{b} \in \{ q_{1}, \dots,q_{k} \} \text{, sodass } p_{1}=q_{b} }_{ \text{ also existiert ein } q_{b} \text{ was gleich } p_{1} \text{ sein muss} }$$
>>  Wir werden von hieran $q_{b}$ als $q_1$ bezeichnen, um den Beweis übersichtlich zu halten. Also tauschen wir $q_{1}=p_{1}$ aus. Wir erhalten für den **ersten Fall** $s_{1}>r_{1}$
>>  $$\begin{alignat}{2}
>> p_{1}^{s_{1}}\cdot \ldots \cdot p_{j}^{s_{j}} &= p_{1}^{r_{1}}\cdot \ldots \cdot q_{k}^{r_{k}} \qquad&&\Big\vert :p_{1}^{r_{1}} \\
>> p_{1}^{s_{1}-r_{1}}\cdot \ldots \cdot p_{j}^{s_{j}} &= q_{2}\cdot \ldots \cdot q_{k}^{r_{k}} \tag{2}
>>\end{alignat}$$
>> Gleichung $(3)$ ist allerdings unmöglich, da mindestens ein $p_{1}$ übrig bleibt, die auch die rechte Seite teilt. Die [[#^8daf7c|Symmetrie der Äquivalenzrelation]] erwartet aber, dass wenn die linke Seite durch $p_{1}$ teilbar ist, so muss es die rechte Seite sein. Somit erhalten wir für den Fall $s_{1}>r_{1}$ einen Widerspruch.
>> 
>> Der **zweite Fall** für $s_{1}<r_{1}$ ist ebenfalls unmöglich, da $s_{1}-r_{1}<0$ und somit wäre $p_{1}^{s_{1}-r_{1}} \not\in \mathbb{Z}$ und somit wäre dies keine Primzahl mehr.
>> 
>> Daher verbleibt nur Fall, dass $s_{1}=r_{1}$. Dieser Prozess kann iterativ für alle $p_{a}$ und $q_{b}$ wiederholt werden, wodurch die Eindeutigkeit gezeigt ist. $$\tag*{$\square$}$$

^50378b

---

>[!warning] Achtung, Wichtig!
> Es ist kein effizientes Verfahren bekannt, um eine beliebige Zahl $n \in \mathbb{N}$ in seine Primfaktoren zu zerlegen. 
><center> <h3> Das bezeichnen wir als <u>Faktorisierungsproblem</u> </h3></center>
>
>>[!remark]- Bemerkung bekannte Faktorisierungsverfahren
>>Es gibt nicht-effiziente Faktorisierungsverfahren wie beispielsweise
>>- Pollard'sche Rho-Methode
>>- Pollard'sche $p-1$-Methode
>>- Fermat-Methode

^ecfc5d

---

>[!lemma] Lemma Teilbarkeit über Primzahlfaktoren 
>Sei $n \in \mathbb{N}$ mit $n=p_{1} \cdot \ldots \cdot p_{k}$ und $a \in \mathbb{Z}$, dann gilt
>$$n \;|\; a \iff p_{1} \;|\; a \land \ldots \land p_{k} \;|\; a$$
>
>>[!proof]- Beweis
>> Wir zeigen zunächst ($\implies$).
>> 
>> Wenn $n \;|\; a$, dann existiert ein $q \in \mathbb{Z}$, sodass
>> $$\begin{align}
>> q \cdot n &= a \\
>> q \cdot (p_{1} \cdot \ldots \cdot p_{i} \cdot \ldots \cdot p_{k}) &= a \qquad&&\Big\vert :p_{i}  \\
>> q \cdot \underbrace{ \left( p_{1} \cdot \ldots \cdot \frac{p_{i}}{p_{i}} \cdot \ldots \cdot p_{k} \right) }_{ =n' } &= \frac{a}{p_{i}} \\
>> q \cdot n' &= \frac{a}{p_{i}}
>>\end{align}$$
>>Wir bezeichnen $n'=\dfrac{n}{p_{i}}$ für ein beliebigen Primfaktor $p_{i}$ von $n$. Es ist leicht ersichtlich, dass $q \cdot n'$ eine ganze Zahl sein muss, da beide Faktoren ganze Zahlen sind. Daher muss $\dfrac{p_{i}}{a}$ eine ganze Zahl sein und demzufolge $p_{i}\;|\;a$  für jedes beliebige $p_{i}$ gelten. $$\tag*{$\checkmark$}$$
>>Wir zeigen nun die andere Richtung ($\Longleftarrow$)
>>
>>Wenn $p_{1} \;|\; a \land \ldots \land p_{k} \;|\; a$ gilt, dann muss laut dem [[#^50378b|Fundamentalsatz der Arithmetik]] $a$ die Primfaktoren $p_{1}, \dots, p_{k}$ enthalten. Das heißt, es gibt eine Zahl $n=p_{1} \cdot \ldots \cdot p_{k}$ die als Faktor in $a$ enthalten ist. Also muss $n \;|\; a$ gelten
>>$$\tag*{$\square$}$$
>

^3dda16

>[!def] Definition Verteilung der Primzahlen
>Sei $\pi: \mathbb{R}^+ \to \mathbb{N}$ definiert mit
>$$\pi (x):= \#\{ p \; |\; p \text{ ist eine Primzahl und } p\leq x \}$$
>
>>[!remark] Bemerkung
>>Diese Funktion zählt alle Primzahlen, die kleiner als $x \in \mathbb{R}^+$ sind. Eine Funktion, die dies bewiesen exakt bestimmt, ist nicht bekannt.

>[!theorem] Der Primzahlsatz nach Gauß und Hadamard
> $\forall x \in \mathbb{R}^+:$
> $$\pi(x)\approx \frac{x}{\ln(x)}$$
>>[!remark]- Bemerkung zur Bedeutung des Satzes
>>Der Primzahlsatz ist eine Schätzung für die Verteilung der Primzahlen. Man sagt, dass $\dfrac{x}{\ln(x)}$ **asymptotisch zu** $\pi(x)$ **konvergiert**, also
>>$$\lim_{ x \to \infty } \frac{\pi(x)}{\frac{x}{\ln(x)}} = 1 $$
>>Das heißt der Zähler und der Nenner nähern sich an je größer das $x \in \mathbb{R}^+$ wird.
>
>>[!remark]- Bemerkung zur Geschichte (Informativ)
>>Der deutsche Mathematiker Carl Friedrich Gauß (1777-1855) hat diesen Satz 1793 im Alter von 16 Jahren vermutet und der Satz wurde erst im Jahr 1896 über die **asymptotische Konvergenz**  von Jacques Salomon Hadamard und Charles-Jean de La Vallée Poussin bewiesen.
>>
>>![[Figures/gauss_brief.png| center | 600]]
>><center>Abbildung: Brief von Gauß an seinen Freund Johann Franz Encke</center>
>>
>>Die tatsächliche Abschätzung von Gauß war sogar etwas genauer und wird angegeben mit dem Integrallogarithmus
>>$$\text{Li}(x)=\int _{2}^x \frac{1}{\log t} \, dt $$
>>[Quelle für den Brief](https://gauss.adw-goe.de/handle/gauss/199?locale-attribute=de)
>
>>[!example]- Beispiel: Wieviele Primzahlen sind bis $x=9\,999\,999\,999$ zu erwarten?
>>$$\begin{align}
>> \pi(9\,999\,999\,999)&\approx \frac{9\,999\,999\,999}{\ln(9\,999\,999\,999)}  \\
>>&\approx\frac{9\,999\,999\,999}{23.02585093} \\
>>&\approx434\;294\;481.86 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!example]-  Beispiel: Wieviele Primzahlen sind zwischen $999\,999\,999$ und $9\,999\,999\,999$ zu erwarten?
>>$$\begin{align}
>> \pi(9\,999\,999\,999) -\pi(999\,999\,999) &\approx 434\;294\;481.86 - 48\,254\,942.39 \\
>> &\approx 386\,039\,539.47 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!property] Eigenschaft des Primzahlsatzes
>Sei $n \in \mathbb{N}$. Wird eine Zahl $k$ zufällig zwischen $1$ und $n$ gezogen, so ist die Wahrscheinlichkeit eine Primzahl zu ziehen
>$$P(k \in \mathbb{P})=\frac{1}{\log n}$$
>

^7e3f5c

>[!remark]- Bemerkung: Informative Ergänzung zu der Verteilung der Primzahlen (Video)
>
>Dieses Video ist recht kurz und sehr empfehlenswert.
>
>![](https://youtu.be/qeCqjJpqbls?si=S3OSxGvHqvQLTFxK)
>
>Wer viel Zeit und viel Interesse hat, kann sich auch eine schöne Weihnachtsvorlesung ansehen.
>
>![](https://www.youtube.com/watch?v=sZhl6PyTflw)

>[!theorem] Satz Primzahlquotienten
>
>Seien $p$ eine Primzahl und $a,b \in \mathbb{Z}$, dann gilt
>$$p \;|\; ab \implies p \;|\; a \text{ oder } p \;|\; b$$
>>[!proof]- Beweis
>>Angenommen
>>$$p \;\nmid\; a \text{ und } p\;\nmid\;b$$
>>so wären $p,a$ und $p,b$ teilerfremd, also
>>$$\begin{align}
>> \text{ggT}(p,a) &= 1 \\
>> \text{ggT}(p,b) &= 1
>>\end{align}$$
>>Mit dem [[#^42f9e5|Lemma von Bezout]] können wir sagen
>>$$\begin{align}
>> \text{ggT}(p,a) &= 1 = pp_{1}+aa' \tag{1}\\
>> \text{ggT}(p,b) &= 1 = pp_{2}+bb' \tag{2}
>>\end{align}$$
>>mit $p_{1},p_{2},a',b' \in \mathbb{Z}$. Wir stellen nun die Gleichungen $(1)$ und $(2)$ geschickt um und erhalten
>>$$\begin{align}
>>  aa' = pp_{1}-1 \tag{3}\\
>> bb' = pp_{2}-1 \tag{4}
>>\end{align}$$
>>Multiplizieren wir gleichung $(3)$ und $(4)$ erhalten wir
>>$$(aa')(bb')=(1-pp_{1})(1-pp_{2})\tag{5}$$
>>Wir bemerken, dass die linke Seite durch Umstellung $(ab)(a'b')$ enthält. Aus unserer Beweis Prämisse schließen wir
>>$$p \;|\; ab \implies p \;|\; (ab)(a'b')$$
>>nach der [[#^6a2086|der dritten Eigenschaft der ganzzahligen Teilung]]. Also muss demnach $p$ auch den rechten Teil der Gleichung $(5)$ teilen, was wir nun prüfen werden.
>>$$\begin{align}
>>(1-pp_{1})(1-pp_{2}) &= 1-pp_{1}-pp_{2}-p^2p_{1}p_{2} \\
>> &= p(p_{1}-p_{2}-pp_{1}p_{2})+1
>>\end{align}$$
>>Damit die Behauptung stand hält, muss $p\;|\;1$ wegen des [[#^a40b0b| Satzes der Teilbarkeit von Summen und Differenzen]], was aber ein Widerspruch ist, daher muss gelten, dass
>>$$p \;|\; ab \implies p \;|\; a \text{ oder } p \;|\; b \tag*{$\square$}$$
>
>>[!example]- Beispiel $5 \;|\; (4 \cdot 5)$
>> $$\underbrace{ \underbrace{ 5 \;|\; (4 \cdot 5) }_{ \text{ wahr} } \implies \underbrace{ \underbrace{ 5 \;|\; 4 }_{ \text{falsch} } \; \lor \; \underbrace{ 5 \;|\;5 }_{ \text{wahr} } }_{ \text{wahr} } }_{ \text{wahr} }$$

^f65359

>[!def] Definition Modulare Inverse
>Es seien $n \in \mathbb{N}$ und $a \in \mathbb{Z} \setminus \{ 0 \}$. Eine Zahl $b \in \mathbb{Z}$ mit 
>$$a \cdot b \equiv 1 \;\;(\text{mod } n)$$
>wird **modulares Inverses** von $a$ bezüglich $n$ genannt. Wir kennzeichnen das **modulare Inverse** von $a$ als
>$$a^{-1}\equiv b \;\;(\text{mod } n)$$
>
>>[!warning]- Achtung, Wichtig! Rückblick zu den Algebraischen Strukturen
>> Das modulare Inverse bezieht sich auf die [[#^f42169| algebraischen Grundlagen]], genau genommen die [[#^afad91|algebraische Strukturen]]. Dort haben wir den Term des [[#^afad91|inversen Elements]] definiert, welches uns zu einem $a \in G$ ein Element liefert, sodass $$a \odot a^{-1} = e$$ liefert, wobei $e$ das neutrale Element in der algebraischen Struktur $(G, \odot)$ ist. 
>> 
>> Üblicherweise für die gewöhnliche Multiplikation in $(\mathbb{Q}\setminus \{ 0 \},\cdot)$ verstehen wir für jedes beliebige $a \in \mathbb{Q}$ das **inverse Element** als
>> $$a^{-1}= \frac{1}{a}$$
>> Das heißt, nehmen wir Beispielsweise eine ganze Zahl $a=5$, so wäre das **inverse Element** dazu $a^{-1}= \frac{1}{5}$, weil
>> $$a \cdot a^{-1}= 5 \cdot \frac{1}{5}=1$$
>> wobei $1$ das **neutrale Element** in $(\mathbb{Q}\setminus \{ 0 \}, \cdot)$ ist. <b><span style="color:#FF8888">Aber</span></b> würden wir dieselbe Logik für $(\mathbb{Z}_{n}, \cdot)$ anwenden, würden wir ein Problem erhalten. Für $a=5$ würde $a^{-1}\neq \frac{1}{5}$ sein, <b><span style="color:#FF8888">weil es in</span></b> $\mathbb{Z}_{n}\setminus \{ 0 \}$<b><span style="color:#FF8888"> keine gebrochenen Zahlen gibt!</span></b>. Wir arbeiten in diesem Modul mit diskreten Werten, vielmehr mit den [[#^f52c1d|ganzen Zahlen]]. Daher suchen wir eine Zahl $a^{-1}$ die unter dem Modul $n$ sich invers zu $a$ verhält.
>
>>[!example]- Beispiel: $5^{-1}\equiv 4 \;\;(\text{mod } 19)$, weil...
>>$$\begin{alignat}{2}
>> 5^{-1}&\equiv 4 &&\;\;(\text{mod } 19) \qquad&&\Big\vert \cdot 5 \\
>> 1&\equiv 20 &&\;\;(\text{mod } 19)  \\
>> 1&\equiv 1 &&\;\;(\text{mod } 19)  \tag*{$\blacktriangleleft$}
>>\end{alignat}$$ 
>
>>[!example]- Beispiel: $5^{-1} \equiv 23 \;\;(\text{mod } 19)$, weil...
>>Wir bemerken, dass in $\mathbb{Z}_{19}$ $$[23]=[4]$$
>>gilt, daher können wir dank der [[#^638cd1|Restklassen]] schreiben
>>$$\begin{align}
>> 5^{-1} &\equiv 23 &&\;\;(\text{mod } 19) \\
>> 5^{-1} &\equiv 4 &&\;\;(\text{mod } 19)
>>\end{align}$$
>>was wir in der vorangegangen Aufgabe bereits gezeigt haben.
>>$$\tag*{$\blacktriangleleft$}$$
>
>>[!remark] Bemerkung: Das modulare Inverse existiert nicht immer, es existiert nur, wenn $a$ und $n$ teilerfremd sind.
>
>>[!example] Beispiel: $2 \cdot b \equiv 1 \;\;(\text{mod } 4)$, es existiert kein $b$, dass diese Kongruenz erfüllt.

^6f68c0

>[!theorem] Satz Existenz zum Modularen Inversen
>
>$$\forall a\in \mathbb{Z}\setminus\{ 0 \}, \forall n \in \mathbb{N}: \exists a^{-1} \in \mathbb{Z}\setminus\{ 0 \}: aa^{-1} \equiv 1 \;\;(\text{mod } n) \iff \text{ggT}(a,n)=1$$
>
>In Worten:
>
> Es seien $a \in \mathbb{Z}\setminus\{ 0 \}$ und $n \in \mathbb{N}$. Das [[#^6f68c0| modulare Inverse]] von $a$ bezüglich $n$ existiert genau dann, wenn $a$ und $n$ teilerfremd sind.
> 
>>[!proof]- Beweis
>> Wenn $a$ und $n$ teilerfremd sind, so wissen wir durch die [[#^2a19a0|Definition des größten gemeinsamen Teilers]], dass
>> $$\text{ggT}(a,n)= 1$$
>> Daher gibt es nach dem [[#^42f9e5|Lemma von Bezout]] zwei Zahlen $a',n' \in \mathbb{Z}$, sodass
>> $$\text{ggT}(a,n)=1=aa'+nn'$$
>> Da wir beim [[#^6f68c0|modularen Inversen]] modulo $n$ rechnen, haben wir
>> $$1 = aa'+\underbrace{ nn' }_{ \equiv 0  } \;\;(\text{mod } n)$$
>> Durch [[#^e40f84|die Restklassenarithmetik]] und die [[#^6a2086|dritte Eigenschaft der ganzzahligen Teilung]] wissen wir, dass $nn' \text{ mod } n = 0$, also verbleibt
>> $$1 = aa'  \;\;(\text{mod } n)$$
>> Laut dem [[#^42f9e5|Lemma von Bezout]] muss ein $a' \in \mathbb{Z}\setminus\{ 0 \}$ existiert, die diese Gleichung löst.
>> $$\tag*{$\square$}$$
>>>[!remark] Bemerkung: Wären $a,n$ nicht teilerfremd, so würde auf der linken Seite der Gleichung die $1$ nicht erscheinen.
>
>>[!algo]- Implementation in Sage
>>```python
>>def modinv(a,n):
>>	g,aa,nn = xgcd(a,n)
>>	if g == 1:
>>		return aa % n
>>	else:
>>		return None
>>```
>>>[!remark]- Bemerkung zu Sage
>>>Sage ist eine mathematische Programmierumgebung, die in der Programmiersprache **Python** eingebette istt. In *SageMath* werden diverse bekannte mathematische Open-Source Bibliotheken integriert wie 
>>>- NumPy
>>>- SciPy
>>>- matplotlib
>>>- Sympy
>>>- Maxima
>>>- FLINT,
>>>- R usw.
>>>
>>>In den Praktika werden wir in erster Linie in Sage programmieren, dazu ist Grundlagenwissen zur Python Syntax nötig und Funktionen aus der Sage Bibliothek wie beispielsweise der [erweiterte Euklidische Algorithmus - xgcd (Link zur Dokumentation)](https://doc.sagemath.org/html/en/reference/rings_standard/sage/arith/misc.html).

^c7c061

>[!lemma] Lemma Teilbarkeit von Teilerfremden Produkten
>Seien $a,b,c \in \mathbb{Z}$ mit $a,b \neq 0$ und $\text{ggT}(a,b)=1$, dann gilt
>$$a \;|\; c \land b \;|\; c \implies ab \;|\; c$$
>>[!proof]- Beweis
>>Unter Verwendung [[#^42f9e5|Bezouts Lemma]] können wir die Aussage $\text{ggT}(a,b)=1$ mit $a',b' \in \mathbb{Z}$ ausdrücken als
>>$$aa'+bb'=1$$
>>Diese Gleichung können wir auf beiden Seiten mit $c$ multiplizieren und erhalten
>>$$aa'c+bb'c=c \tag{1}$$
>>Der Prämisse können wir nach der [[#^9380e8|ganzzahligen Teilung]] entnehmen
>>$$\begin{align}
>> a \;|\; c &\implies \exists k_{a}\in \mathbb{Z}: a k_{a}=c\\
>> b \;|\; c &\implies \exists k_{b}\in \mathbb{Z}: b k_{b}=c
>>\end{align}$$
>>Da beide Formulierungen Ausdrücke für $c$ sind können wir diese auf der linken Seite von Gleichung $(1)$ einsetzen
>>$$\begin{align}
>> aa'\underbrace{ bk_{b} }_{ =c } + bb'\underbrace{ ak_{a} }_{ =c } &= c \\
>> ab(a'k_{b}+b'k_{a}) &= c
>>\end{align}$$
>>Da die linke Seite offensichtlich durch $ab$ teilbar ist, muss demnach $c$ auch durch $ab$ teilbar sein, was es zu zeigen galt.
>>$$\tag*{$\square$}$$

^251edf

>[!lemma] Lemma Teilerfremde über Teilerfremde Produkte
>Seien $a,b,c \in \mathbb{Z}\setminus\{ 0 \}$, dann gilt
>$$\Big(\text{ggT}(a,b)=1\Big) \land \Big(\text{ggT}(a,c)=1\Big) \iff \Big(\text{ggT}(a,bc)=1\Big)$$
>>[!proof]- Beweis
>>Für $(\implies)$
>>
>>Nach [[#^42f9e5|Bezouts Lemma]] können wir sagen für $a',a'', b',c' \in \mathbb{Z}$
>>$$\begin{align}
>> \text{ggT}(a,b) &\implies 1 =aa'+bb' \\
>> \text{ggT}(a,c) &\implies 1 =aa''+cc' \\
>>\end{align}$$
>>Wir stellen beide Gleichungen um
>>$$\begin{align}
>> bb' &= 1-aa'  \\
>> cc' &= 1-aa''
>>\end{align}$$
>>Jetzt werden beide Gleichungen miteinander multipliziert
>>$$\begin{align}
>> bb'cc' &= (1-aa')(1-aa'') \\
>> bb'cc' &= 1-aa'-aa''-aa'aa'' \\
>> bb'cc' &= 1- a(a'-a''-a'a'') \\
>>  a(a'-a''-a'a'')+ bc(b'c')  &= 1\\
>>\end{align}$$
>>Was die Aussage [[#^42f9e5|Bezouts Lemma]] für $\text{ggT}(a,bc)=1$ ist, also
>>$$ a(a'-a''-a'a'') + bc(b'c')  = 1 \implies \text{ggT}(a,bc)=1$$
>>Für $(\Longleftarrow)$ konstruieren wir für $a$ über [[#^42f9e5|Bezouts Lemma]]
>>$$\text{ggT}(a,bc)\implies a(a'-a''-a'a'') + bc(b'c')  = 1$$
>>und lösen die vorangegangene Implikation rückwärts auf und erhalten die gesuchte Aussage.
>>
>>$$\tag*{$\square$}$$

^2548b2

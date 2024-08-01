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

>[!def] Definition Gruppe (Algebraische Struktur) ([[../../PDFs/judson2022.pdf#page=33|Quelle]])
>Sei $\circ$ eine beliebige Operation auf der Menge $G$. Wir bezeichnen $(G, \circ)$ als **<u>Gruppe</u>**, wenn die Menge $G$ die folgenden Eigenschaften erfüllt
>1. $G$ ist **assoziativ**, das heißt $\forall x_{1},x_{2},x_{3} \in G$:
> $$(x_{1} \circ x_{2})\circ x_{3} = x_{1}\circ (x_{2} \circ x_{3})$$
> 2. $G$ besitzt genau ein **neutrales Element**, das heißt $\exists! e \in G$, sodass $\forall x \in G:$
>  $$x \circ e = e \circ x = x$$
>  3. $G$ besitzt **inverse Elemente**, das heißt $\forall x \in G: \exists! x^{-1} \in G$, sodass
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
>Eine Relation $\sim$ auf einer Menge $G$ heißt Äquivalenzrelation, wenn folgende Eigenschaften auf der Relationsmenge $R \subseteq G \times G$ erfüllt sind
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
>Seien $a,b,n \in \mathbb{Z}$ mit $n\;|\;a$ und $n\;|\;b$, dann gilt auch
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
>>$$3 \cdot 3 + 1 = 10$$

^9cd06c

>[!theorem] Satz Existenz und Eindeutigkeit des Quotienten und Rests
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
>>$T$ ist definitiv nicht leer, daher gibt es nach dem Wohlordnungsprinzip ein kleinstes Element
>>$$r = \min T \tag{1}$$
>>Dieses $r$ ist nach der Beschreibung der Menge $T$ für ein spezielles $\widehat{q} \in \mathbb{Z}$ beschrieben als
>>$$r= a-\widehat{q}b$$
>>mit $r \geq 0$.
>>
>>Unsere Strategie von hieran ist einen Widerspruch zu erzeugen. Daher nehmen wir an, dass $$r \geq \lvert b \rvert \tag{2}$$ gilt, was zu unserer zu beweisenden Aussage gegenteilig ist. Wir definieren für den Beweis und setzen sukzessive ein
>>
>>$$\begin{align}
>> r' &= \underbrace{ r }_{ = a-\widehat{q}b} -\lvert b \rvert \tag{3} \\
>> &= a-\widehat{q}b - \lvert b \rvert \\
>> &= a- \underbrace{ (\widehat{q}-\text{sgn}(b)) }_{ =q' }b  \tag{siehe Info}\\
>> &= a- q'b
>>\end{align}$$
>> Da $q' \in \mathbb{Z}$ wissen wir, dass $r' \in T$ maßgeblich nach unserer Konstruktion von $T$. 
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


>[!def] Definition Kongruenz-Äquivalenzrelation über den ganzen Zahlen
>Wir definieren die **Kongruenz-Äquivalenzrelation** über den ganzen Zahlen $a,b \in \mathbb{Z}$  kongruent zum **Modul** $n$ mit
>$$a \equiv b \;\;(\text{mod }n) \iff n \;|\; (a-b)$$
>und $0\leq r< \lvert n \rvert$
>
>
>>[!remark]- Bemerkung zur Bedeutung
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

>[!def] Definition Äquivalenzklassen bezüglich der Modulus Äquivalenzrelation
> Wir definieren eine [[#^8daf7c|Äquivalenzklasse]] für $a\in \mathbb{Z}$ bezüglich des **Moduls** $n$ als
> $$[a]_{n} = \{ b \in \mathbb{Z} \; | \; a \equiv b \;\;(\text{mod } n) \}$$

>[!lemma]
>Die [[#^8daf7c|Äquivalenzklassen]] partitionieren $\mathbb{Z}$ vollständig bezüglich des Moduls $n$ in $n$ disjunkte Partitionen.
>
>Wir bezeichnen fortan $\mathbb{Z}_{n}=\{ [0]_{n}, [1]_{n}, \dots, [n-1]_{n} \}$ als die Menge aller [[#^8daf7c|Äquivalenzklassen]] bezüglich der Kongruenz-Äquivalenzrelation modulo $n$.
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
>> $$\mathbb{Z}_{n} = \{ [0]_{3}, [1]_{3}, \dots, [n-1]_{3} \}$$
>> schreiben wir fortan
>> $$\mathbb{Z}_{n} = \{ 0,1,\dots,n-1 \}$$
 
>[!remark] Bemerkung zur "Restklassenarithmetik"
> Wir haben nun erfolgreich die [[#^360a7d| Kongruenz Äquivalenzrelation]] als eine [[#^afad91|algebraische Struktur]] eingeführt. Über die [[#^6a2086|Eigenschaften der ganzzahligen Teilung]] und dem [[#^a40b0b| Satz der Teilbarkeit von Summen und Differenzen]] können wir zusammenfassend sagen, dass
> $$\begin{align}
> (a \text{ mod } n) \pm (b \text{ mod } n) &\equiv (a\pm b) \text{ mod } n \;\;(\text{mod } n) \tag{1} \\
> (a \text{ mod } n) \cdot (b \text{ mod } n) &\equiv (a\cdot b) \text{ mod } n \;\;(\text{mod } n) \tag{2}
>\end{align}$$
>gilt. Gleichung $(1)$ entsteht aus der [[#^a40b0b| der Teilbarkeit von Summen und Differenzen]] und Gleichung $(2)$ aus der Eigenschaft $3$ in den [[#^6a2086|Eigenschaften der ganzzahligen Teilung]]. 
>
>In Worten ausgedrückt können wir sagen, dass wir mit den Resten über Summen und Produkten bei gleichem Modul $n$ rechnen dürfen. Die Summe zweier Rester über $a,b$ ist demnach kongruent zu dem Rest der Summe $a+b$. Analog gilt selbiges für das Produkt. Dies wird auch **Restklassenarithmetik**  genannt.
>
> ***Diese Eigenschaft ist fundamental für die Verschlüsselungsalgorithmen und der Funktionsweisen, die über Restklassenringe bzw. Restklassenkörper aufgebaut werden.***
>>[!remark] Bemerkung zur Notation
>>Fortan ist zu
>>$$a \equiv b \;\;(\text{mod } n)$$
>>eine gültige alternative Notation
>>$$a = b \;\;(\text{mod } n)$$
>>wobei die zuerst eingeführte Notation die präzise Notation ist.

>[!property] Eigenschaften der Operationen of $\mathbb{Z}_{n}$
>1. Die [[#^c5cc22|Operation]] $+ : \mathbb{Z}_{n} \times \mathbb{Z}_{n} \to \mathbb{Z}_{n}$ ein, wobei $\forall a,b \in \mathbb{Z}_{n}$ gilt:
 $+$ bildet eine [[#^afad91|kommutative Gruppe]]  $(\mathbb{Z}_{n},+)$
>2. Die [[#^c5cc22|Operation]] $+ : \mathbb{Z}_{n} \times \mathbb{Z}_{n} \to \mathbb{Z}_{n}$ ein, wobei $\forall a,b \in \mathbb{Z}_{n}$ gilt:
 $\cdot$ bildet eine [[#^afad91|kommutative Halbgruppe]]  $(\mathbb{Z}_{n}\setminus\{0\}, \cdot)$
>	- ... ist assoziativ
>	- ... es existiert das neutrale Element $e=1$
>	- ... das inverse Element für $a$ existiert nicht, wenn $a$ und $n$ gemeinsame Teiler haben
>	- ... ist kommutativ
>3. Die [[#^c5cc22|Operation]] $+ : \mathbb{Z}_{n} \times \mathbb{Z}_{n} \to \mathbb{Z}_{n}$ ein, wobei $\forall a,b \in \mathbb{Z}_{n}$ gilt:
 $\cdot$ bildet eine [[#^afad91|kommutative Gruppe]] $(\mathbb{Z}_{n}\setminus \{ 0 \})$, wenn $n$ eine Primzahl ist
>	- ... das heißt das inverse Element existiert hier für jedes beliebige Element in $\mathbb{Z}_{n}$

## 2.3 Zahlentheoretische Grundlagen

>[!def] Definition Primzahl ([[../../PDFs/judson2022.pdf#page=22|Quelle]])
>Sei $p \in \mathbb{Z}^+$ (positive Ganzzahl). Wir nennen $p$ eine **Primzahl**, wenn die einzigen Zahlen, die $p$ ganzzahlig teilen, $p$ selbst und $1$ sind. 

>[!theorem] Satz Die Existenz von Unendlich vielen Primzahlen (Euklid) ([[../../PDFs/judson2022.pdf#page=22|Quelle]])
>Es existieren unendlich viel Primzahlen
>>[!proof]- Beweis
>> Wir nutzen für den Beweis das **Widerspruchsverfahren**. Dazu nehmen wir an, dass es nur endlich viele Primzahlen gibt, also die Menge der Primzahlen kann angegeben werden mit
>> $$\mathbb{P} = \{ p_{1}, p_{2}, \dots, p_{n} \}$$
>> Wir geben nun die Zahl $P$ an mit
>> $$P = p_{1} \cdot p_{2} \cdot \dots \cdot p_{n} + 1$$
>> Es gibt nun zwei Möglichkeiten über die Beschaffenheit von $P$. Zum einen kann $P$ selbst eine Primzahl sein, was allerdings ein Widerspruch zu unserer Annahme wäre, dass $\mathbb{P}$ eine vollständige Liste aller Primzahlen wäre.
>> 
>> Die andere Möglichkeit ist, dass $P$ eine durch Primzahlen faktorisierte Zahl ist. Also muss es eine Primzahl $p_{i} \in \mathbb{P}$ geben, die $P$ teilt. Wir nehmen an, $p_{i}$ teilt ganzzahlig $P$, also
>> $$\begin{align}
>> \frac{P}{p_{i}} &= \frac{p_{1} \cdot p_{2} \cdot \dots \cdot p_{n} + 1}{p_{i}} \\
>> &= \frac{P}{p_{i}} = \underbrace{ \frac{p_{1} \cdot p_{2} \cdot \dots \cdot p_{n} }{p_{i}} }_{ \in \mathbb{Z}^+} + \underbrace{ \frac{1}{p_{i}} }_{ \not\in\mathbb{Z} }
>>\end{align}$$
>>Da $\frac{1}{p_{i}}$ keine ganze Zahl sein kann, haben wir auch für diesen Fall einen Widerspruch. Somit muss es unendlich viele Primzahlen geben, da es nicht endlich viele geben kann
>>$$\tag*{$\square$}$$

>[!theorem] Satz Fundamentalsatz der Arithmetik ([[../../PDFs/judson2022.pdf#page=22|Quelle]])
>Sei $n \in \mathbb{Z}$ mit $n>1$. Dann lässt sich $n$ _eindeutig_ in seine Primfaktoren
>$$n = p_{1} \cdot p_{2} \dots p_{k}$$
>zerlegen, wobei die $p_{i}$ mit $1\leq i\leq k$ nicht notwendigerweise unterschiedlich sein müssen.
>>[!proof] Beweis wird ausgelassen. Kann in der genannten Quelle nachgeschlagen werden.

>[!example] Übungen
>>[!example] Übung (1)
>> Gegeben ist die Gruppe für $\mathbb{Z}_{8}$. Bestimmen Sie folgende Ausdrücke
>> $$\begin{align}
>> &(a)\; 6+7 \\
>> &(b) \; 2^{-1}
>>\end{align}$$
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
>>> Laut [[#^360a7d| Definition der Kongruen-Äquivalenzrelation]] wissen wir
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

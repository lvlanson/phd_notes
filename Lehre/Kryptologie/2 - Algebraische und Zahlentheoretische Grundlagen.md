>[!remark] Bemerkung
> Damit eine analytische Auseinandersetzung mit asymmetrischen Verschlüsselungsverfahren möglich ist, führen wir zunächst gruppen- (Abstrakte Algebra) und zahlentheoretische Grundlagen ein

>[!theorem] Satz Divisions Algorithmus ([[../../PDFs/judson2022.pdf#page=20|Quelle]])
> Seien $a,b \in \mathbb{Z}$ mit $b>0$, dann existieren eindeutige Elemente $q,r \in \mathbb{Z}$, sodass
> $$a = bq + r$$
>>[!proof] Beweis wird ausgelassen. Kann in der genannten Quelle nachgeschlagen werden.

>[!remark] Bemerkung Ganzzahlige Teilung
>Für den Ausdruck _$a$ teilt $b$_ schreiben wir $a \; | \; b$. Dies heißt
>$$a \; | \; b: \iff \exists k \in \mathbb{Z}: b = k\cdot a$$
>Sofern $a$ die Zahl $b$ nicht teilt schreiben wir analog $a \; \not\mid b$

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

>[!def] Definition Die binäre Modulus Operation 
> Sei $\text{mod}$ eine zweistellige Operation auf $\mathbb{Z}$ und definiert mit $a,b \in \mathbb{Z}$
> $$\text{mod}(a,b) = a \text{ mod } b = r$$
> wobei $r$ auch als Rest bezeichnet wird für $a = b \cdot q+r$ und $0 \leq r < \lvert b \rvert$
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

>[!def] Definition Die Kongruenz-Äquivalenzrelation über den ganzen Zahlen
>Wir definieren die **Kongruenz-Äquivalenzrelation** über den ganzen Zahlen $a,b \in \mathbb{Z}$  kongruent zum Modul $n$ mit
>$$a \equiv b \;\;(\text{mod }n) \iff n \;|\; (a-b)$$
>und $0\leq r< \lvert n \rvert$
>
>>[!remark] Bemerkung: $k \; |  \; q$ heißt "k teilt q ganzzahlig"
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
>>Da $q_{1},q_{2}$ beides ganze Zahlen sind, muss demnach der Quotient $\frac{a-b}{n}$ auch eine ganze Zahl sein. Daher muss wenn $a \equiv b \;\;(\text{mod } n)$ gilt, auch $n \; |\; a-b$ gelten.
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
> Wir definieren eine **Äquivalenzklasse** für $a\in \mathbb{Z}$ bezüglich des Moduls $n$ als
> $$[a] = \{ b \in \mathbb{Z} \; | \; a \equiv b \;\;(\text{mod } n) \}$$

>[!lemma]
>Die Äquivalenzklassen partitionieren $\mathbb{Z}$ vollständig bezüglich des Moduls $n$ in $n$ disjunkte Partitionen.
>
>Wir bezeichnen fortan $\mathbb{Z}_{n}=\{ [0], [1], \dots, [n-1] \}$ als die Menge aller Äquivalenzklassen bezüglich der Kongruenz-Äquivalenzrelation modulo $n$.
>
>>[!example]- Beispiel $\mathbb{Z}_{3}$
>>Für $\mathbb{Z}_{3}$ haben wir 3 Äquivalenzklassen
>>$$\begin{align}
>> [0] &= \{ \dots, -6,-3,0,3,6,\dots  \} = \{ 3k \; | \; k \in Z \} \\
>> [1] &= \{ \dots, -5,-2,1,4,7,\dots  \} = \{ 3k +1\; | \; k \in Z \} \\
>> [2] &= \{ \dots, -4,-1,2,5,8,\dots  \} = \{ 3k +2\; | \; k \in Z \} \\ \\
>>\end{align}$$
>>sodass
>>$$\mathbb{Z}_{3} = \{ [0], [1], [2] \}$$
>
>>[!remark]- Bemerkung zur Notation
>> Fortan statt 
>> $$\mathbb{Z}_{n} = \{ [0], [1], \dots, [n-1] \}$$
>> schreiben wir 
>> $$\mathbb{Z}_{n} = \{ 0,1,\dots,n-1 \}$$

>[!def] Definition Operationen auf $\mathbb{Z}_{n}$
>Wir führen die **additive Operation** $+ : \mathbb{Z}_{n} \times \mathbb{Z}_{n} \to \mathbb{Z}_{n}$ ein, wobei $\forall a,b \in \mathbb{Z}_{n}$ gilt:
>$$a+b \equiv (a+b) \;\;(\text{mod } n)$$
>Außerdem definieren wir $\forall a,b \in \mathbb{Z}_{n}$ die **multiplikative Operation** $\cdot : \mathbb{Z}_{n} \times \mathbb{Z}_{n} \to \mathbb{Z}_{n}$ mit
>$$a \cdot b \equiv (a \cdot b) \;\;(\text{mod } n)$$
>
>>[!example]- Beispiel $10 + 4$ bezüglich des Moduls 10
>>$$\begin{alignat}{2}
>> 10 +4 &\equiv (10 + 4) &&\;\;(\text{mod } 10) \\
>> 10 +4 &\equiv 14 &&\;\;(\text{mod } 10) \\
>> 10 +4 &\equiv 4 &&\;\;(\text{mod } 10) \\
>>\end{alignat}$$
>>da die für die Äquivalenzklassen gilt $[4] = [14]$ bezüglich des Moduls 10, da $14 \in [4]$ und folglich auch $4 \in [14]$.
>
>>[!remark] Bemerkung Man nennt dies auch Restklassenarithmetik
>
>>[!remark]- Bemerkung zur Notation
>>Fortan ist zu
>>$$a \equiv b \;\;(\text{mod } n)$$
>>eine gültige alternative Notation
>>$$a = b \;\;(\text{mod } n)$$
>>wobei die zuerst eingeführte Notation die präzise Notation ist.

>[!properties] Eigenschaften der Operationen of $\mathbb{Z}_{n}$
>1. Die Operation $+$ bildet eine kommutative Gruppe $(\mathbb{Z}_{n},+)$
>2. Die Operation $\cdot$ bildet eine kommutative Halbgruppe $(\mathbb{Z}_{n}\setminus\{0\}, \cdot)$
>	- ... ist assoziativ
>	- ... es existiert das neutrale Element $e=1$
>	- ... das inverse Element für $a$ existiert nicht, wenn $a$ und $n$ gemeinsame Teiler haben
>	- ... ist kommutativ
>3. Die Operation $\cdot$ bildet eine kommutative Gruppe $(\mathbb{Z}_{n}\setminus \{ 0 \})$, wenn $n$ eine Primzahl ist
>	- ... das heißt das inverse Element existiert hier für jedes beliebige Element in $\mathbb{Z}_{n}$

>[!example]- Übungen
>>[!example] Übung (1)
>> Gegeben ist die Gruppe für $\mathbb{Z}_{8}$. Bestimmen Sie folgende Ausdrücke
>> $$\begin{align}
>> &(a)\; 6+7 \\
>> &(b) \; 2^{-1}
>>\end{align}$$
>
>>[!example]
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


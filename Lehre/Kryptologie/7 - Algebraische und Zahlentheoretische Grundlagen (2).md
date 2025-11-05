>[!remark] Bemerkung: Motivation zum Kapitel
>Im Kapitel [[2 - Algebraische und Zahlentheoretische Grundlagen (1)]] haben wir grundlegende algebraische Strukturen eingeführt. Wir erinnern uns, dass wir [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppen und kommutative Gruppen]] kennen, die je nachdem die Eigenschaften
>1. Assoziativität
>2. Existenz des neutralen Elements
>3. Existenz der inversen Elemente
>4. Kommutativität
>
>besitzen. Die Forderung dieser Eigenschaften hat es uns ermöglicht eine Struktur aufzubauen, die mithilfe von zahlentheoretischen Eigenschaften in kryptologischen Verfahren mündete. Wir vertiefen nun Konzepte der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)|algebraischen Strukturen]], um damit neue kryptologische Verfahren zu beschreiben.

>[!def] Definition Untergruppe ([[../../PDFs/judson2022.pdf#page=50|Quelle]])
>Sei $(G, \circ)$ eine [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppe]], dann ist $(H, \circ)$ eine Untergruppe mit $H \subseteq G$, genau dann wenn
>$$\begin{align}
> &(1)&&\forall h_{1},h_{2} \in H: h_{1} \circ h_{2} \in H \\
> &(2)&& h_{1} \in H \implies h_{1}^{-1} \in H \\
> &(3)&& e \in H
>\end{align}$$
>wobei $e$ in $(3)$ das neutrale Element in $H$ ist.
>
>>[!example]- Beispiel $2\mathbb{Z}$
>>Sei $G=(\mathbb{Z},+)$, dann ist $(2\mathbb{Z},+)$ eine Untergruppe bezüglich $G$ mit $2\mathbb{Z}=\{ \dots,-4,-2,0,2,4,\dots \}$, weil
>>1. Jede Addition von zwei geraden Zahlen erzeugt wieder eine gerade Zahl 
>>	- Beispiel: $2+2 = 4$ oder $-40 + 28 = -12$
>>2. Zu jeder geraden Zahl existiert ein inverses Element, sodass das neutrale Element $0$ rauskommt
>>	- Beispiel: Zu $4$ existiert das inverse Element $-4$, sodass $4 +(-4) = 0$

>[!remark] Kontrollfrage: Warum ist die Menge der ungeraden Zahlen $\mathbb{Z}\setminus2\mathbb{Z}$ unter der Multiplikation keine Untergruppe von $\mathbb{Z}$?

>[!theorem] Satz Zyklische Untergruppen ([[../../PDFs/judson2022.pdf#page=58|Quelle]])
>Sei $(G, \circ)$ eine Gruppe und $a \in G$, dann ist die Menge
>$$\langle a\rangle = \{ a^{k}\;\mid\;k \in \mathbb{Z} \}$$
> eine **(zyklische) Untergruppe** von $G$
>>[!proof]- Beweis
>> Wir müssen zeigen, dass die [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppeneigenschaften]] gültig sind und wir beginnen damit zu zeigen, dass die Gruppe geschlossen bezüglich der **multiplikativen** algebraischen Operation $\circ$ abgeschlossen ist. Man könnte dies auch analog für eine **additive** algebraische Operation zeigen
>> 
>> Seien $g,h \in \langle a\rangle \subseteq G$, so lassen sich über die Definition von $\langle a\rangle$ die Elemente darstellen als
>> $$\begin{align}
>> g &= \underbrace{ a \circ a \circ \dots \circ a }_{ n\text{-mal} } =a^n \\
>> h&= \underbrace{ a \circ a \circ \dots \circ a }_{ m\text{-mal} }=a^m
>>\end{align}$$
>> mit $n,m \in \mathbb{Z}$. Das heißt, wenn wir berechnen
>> $$g \circ h = a^{n} \circ a^{m} = a^{n + m}$$
>> und da $n +m \in \mathbb{Z}$ muss demnach auch $a^{n+m} \in \langle a\rangle$ sein. Die Assoziativität folgt für $g,h,f \in \langle a\rangle$ aus
>> $$\begin{align}
>> g \circ (h \circ f) &= a^{n} \circ (a^{m} \circ a^l)  \\
&= a^n \circ a^{m+l}  \\
&= a^{n+m+l}  \\
&= a^{n+m}a^l  \\
&= (a^{n} \circ a^{m})a^l  \\
&= (g \circ h) \circ f
>>\end{align}$$
>>Da $0 \in \mathbb{Z}$ muss auch das neutrale Element enthalten sein, da
>>$$a^{0} = e$$
>>Da zu jedem beliebigen $n \in \mathbb{Z}$ das inverse Element $-n \in \mathbb{Z}$ existiert, also
>>$$a^{n}\circ a^{-n}=a^{n+(-n)}=a^{0}=e$$
>>gilt existiert auch jedes inverse Element. Somit ist $\langle a\rangle$ eine Untergruppe von $G$. $$\tag*{$\square$}$$
>
>>[!remark]- Bemerkung zur Additiven Darstellung $(G, \oplus)$
>>Die Definitionen und der Beweis würden sich etwas ändern. Grundlegend wäre die zyklische Untergruppe definiert als 
>>$$\langle a\rangle = \{ na \;\mid\; n \in \mathbb{Z} \}$$
>
>>[!remark]- Bemerkung zur Aussprache
>> Für $a \in G$ und der zyklischen Gruppe $\langle a\rangle$ sagen wir **die von $a$ erzeugte zyklische Untergruppe**.

>[!def] Definition Zyklische Gruppen
>Sei $(G, \circ)$ eine Gruppe. Wenn für ein $a \in G$ gilt 
>$$\langle a \rangle =G$$
>Nennen wir $(G, \circ)$ eine **zyklische Gruppe** und $a$ den **Generator** von $G$.
>
>>[!example]- Beispiel $(\mathbb{Z}_{6},+)$ ist eine zyklische Gruppe (Additiv)
>> Die zyklische Gruppe $(\mathbb{Z}_{6}, +)$ hat sogar zwei verschiedene Generatoren $a\in\{ 1,5 \}$. Wir prüfen für $\langle 1\rangle$
>> $$\begin{align}
>> [0 \cdot 1] &= [0] \\
>> [1 \cdot 1] &= [1] \\
>> [2 \cdot 1] &= [2] \\
>> \vdots & \\
>> [5 \cdot 1] &= [5]
>>\end{align}$$
>>wobei $[a]$ die [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^638cd1|Äquivalenzklasse]] für die $\text{ mod } 6$ Relation ist.
>
>>[!example]- Übung: Prüfen Sie, dass $5$ ein Generator für $(\mathbb{Z}_{6}, +)$ ist.

^1a82a3

>[!theorem] Satz Kommutativität Zyklischer Gruppen
>Jede zyklische Gruppe ist kommutativ.
>
>>[!proof]- Beweis
>> Sei $G$ eine [[#^1a82a3|zyklische Gruppe]]. Es existiert demnach ein [[#^1a82a3|Generator]] $a$, sodass für zwei Elemente $g,h \in G$ gilt
>> $$g \circ h = a^{n} \circ a^{m} = a^{n+m} = a^{m+n}=a^{m} \circ a^{n}= h \circ g$$
>> welches die Kommutativität darstellt.
>> $$\tag*{$\square$}$$ 

>[!def] Definition Einheitengruppe auf den Ganzen Zahlen ([[../../PDFs/judson2022.pdf#page=47|Quelle]])
> Eine Einheitengruppe ist eine [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppe]], die invertierbare Elemente und deren Inversen enthalten. Im Speziellen, die Einheitengruppe auf den ganzen Zahlen ist gegeben als
> $$\mathbb{Z}_{n}^*=\{ 1,\dots,n-1 \}$$
>wobei für jedes Element $a \in \mathbb{Z}_n^*$ gilt $\text{ggT}(a,n)=1$.

^56b25f

>[!def] Definition Primitive Wurzel
>Sei $p$ eine Primzahl. Eine **primitive Wurzel** von $p$ ist eine Zahl $g \in \mathbb{Z}^*_{p}$, sodass
>$$\mathbb{Z}^*_{p}=\{ 1,2,\dots,p-1 \}=\{ g^1 \text{ mod }p, g^2 \text{ mod }p, \dots, g^{p-1} \text{ mod } p \}$$
>
>>[!example]- Beispiel $g=2$ bezüglich $p=11$
>>Wir haben als [[#^56b25f|Einheitsgruppe]] $\mathbb{Z}^*_{11}$ gegeben
>>$$\begin{align}
>> \mathbb{Z}^*_{11} &= \{ 1,2,3,4,5,6,7,8,9,10 \} \\
>> &= \{ \underbrace{ 2^1 }_{ \equiv 2 },\underbrace{ 2^2 }_{ \equiv4 },\underbrace{ 2^3 }_{ \equiv 8 },\underbrace{ 2^4 }_{ \equiv5 },\underbrace{ 2^5 }_{ \equiv 10 },\underbrace{ 2^6 }_{ \equiv 9},\underbrace{ 2^7 }_{ \equiv 7 },\underbrace{ 2^8 }_{ \equiv 3 },\underbrace{ 2^9 }_{ \equiv 6 },\underbrace{ 2^{10} }_{ \equiv 1 } \} \\
>> &= \{ 1,2,3,4,5,6,7,8,9,10 \}
>>\end{align}$$
>>
>
>>[!remark]- Mathematischer Hintergund (Informativ)
>> [[X - Zusatz Mathematik (Informativ)#^c91d0f|Euler's Satz]] ist eine Generalisierung von [[3 - RSA (Rivest Shamir Adleman)#^5e7c61|Fermats kleinem Satz]] und sagt, 
>>>[!theorem] Euler's Satz 
>>>Wenn $n \geq 1$ und $\text{ggT}(a,n)=1$, dann
>>>$$a^{\phi(n)}\equiv 1 \;\;(\text{mod } n)$$
>>
>> Die primitive Wurzel kann allerdings auch mit der sogenannten [[X - Zusatz Mathematik (Informativ)#^86d16a|Ordnung]] einer Zahl [[X - Zusatz Mathematik (Informativ)#^2e5c1d|definiert werden]]. 
>>>[!def] Definition Ordnung von Restklassen 
>>>Sei $n>1$ und $\text{ggT}(a,n)=1$. Die **Ordnung von** $a$ **bezüglich modulo $n$** ist die kleinste ganze Zahl $k$, sodass
>>>$$a^k \equiv 1 \;\;(\text{mod } n)$$
>>
>>>[!def] Definition Primitive Wurzel
>> Sei $a,n \in \mathbb{Z}$ mit $n \neq 0$. Wenn $\text{ggT}(a,n)=1$ und $a$ hat [[X - Zusatz Mathematik (Informativ)#^86d16a|Ordnung]] $\phi(n)$ bezüglich modulo $n$, dann ist $a$ die **primitive Wurzel** von $n$. 
>> 
>> Nach unserer Definition wäre $n$ die Primzahl $p$, also $\phi(p)=p-1$. Daher ist 
>> $$a^{\phi(p)} \equiv 1 \;\;(\text{mod } p)$$
>> In unserer Definition finden wir die Gemeinsamkeit, dass 
>> $$g^{p-1} \equiv 1 \;\;(\text{mod } p)$$
>> 
>> Darüber hinaus garantiert uns das [[X - Zusatz Mathematik (Informativ)#^59492a|Korolar]]
>>>[!lemma] Korolar ([[../../PDFs/burton2010.pdf#page=161|Quelle]])
>>>$$a \text{ ist von Ordnung } k \text{ bezüglich modulo } n \implies a,a^2,\dots,a^k \text{ sind inkongruent bezüglich modulo } n$$
>>
>> dass alle Werte voneinander verschieden sein müssen, sofern $\text{ggT}(a,n)=1$ gilt. Da laut unserer Definition $p$ eine Primzahl ist, muss $\text{ggT}(a,p)=1$ für alle $a<p$ gelten. Daher generiert $a$ alle Werte in $\mathbb{Z}^*_{p}$.

^01650b

>[!remark] Bemerkung zur Erkenntniskette
>
> Mit dem Wissen, dass eine [[#^01650b|primitive Wurzel]] ([[#^1a82a3|Generator]]) alle Elemente der [[#^56b25f|ganzzahligen Einheitengruppe]] $a \in \mathbb{Z}^*_{p}$ über Potenzen der Einheitengruppe generieren kann, sind wir nun in der Lage Kongruenzen der Form
> $$g^x \equiv a \;\;(\text{mod } p)$$
> wobei $x \in \mathbb{Z}_{p}^*$ die gesuchte Größe ist.

>[!def] Definition und Satz Diskreter Logarithmus
>Sei $p$ eine Primzahl und $g$ eine primitive Wurzel von $p$. Dann gibt es zu jedem $a \in \mathbb{Z}^*_{p}$ ein ganzzahliges $x$ mit
>$$a \equiv g^x \;\;(\text{mod } p)$$
>dann ist der **diskrete Logarithmus von $a$ zur Basis $g$  modulo $p$** definiert als
>$$\log_{g}a \equiv x \;\;(\text{mod } p)$$
>
>>[!proof]- Beweis (Informativ)
>>Da $\text{ggT}(g,p)=1$ und $g$ [[X - Zusatz Mathematik (Informativ)#^2e5c1d|primitive Wurzel]] bezüglich $p$ ist, können wir das [[X - Zusatz Mathematik (Informativ)#^59492a|Korolar]] anwenden. Es zeigt, dass $p-1$ verschiedene Elemente erzeugt werden, wenn $g$ [[X - Zusatz Mathematik (Informativ)#^86d16a|Ordnung]] $\phi(p)$ hat. Daher gibt es zu jedem $a \\ \in \mathbb{Z}^*_{p}$ ein ganzzahliges $x$, dass den diskreten Logarithmus löst.
>>$$\tag*{$\square$}$$
>
>>[!example]- Beispiel
>>$$\log_{2}6 \equiv 9 \;\;(\text{mod } 11)$$
>>da
>>$$2^9 \equiv 6 \;\;(\text{mod } 11)$$

^149fe6

---

>[!warning] Achtung, Wichtig!
> Es ist kein effizientes Verfahren bekannt, um für $p,g,a \in \mathbb{Z}^*_{p}$, wobei $p$ eine Primzahl ist, ein $x \in \mathbb{Z}^*_{p}$ zu finden, was den [[#^149fe6|diskreten Logarithmus]] löst.
><center> <h3> Das bezeichnen wir als <u>Diskretes-Logarithmus-Problem</u> </h3></center>
>
>>[!remark]- Bemerkung
>>Es gibt nicht-effiziente Faktorisierungsverfahren wie beispielsweise
>>- Babystep-Giantstep Algorithmus
>>- Pohlig-Hellman Algorithmus

^9e7a61

---
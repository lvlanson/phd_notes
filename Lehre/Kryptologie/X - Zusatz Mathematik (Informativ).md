## X.1 Weitere Erkenntnisse zur Euler'schen Phi-Funktion

>[!theorem] Satz Euler'sche Phi-Funktion von Primpotenzen ([[../../PDFs/burton2010.pdf#page=144|Quelle]])
>Wenn $p$ eine Primzahl ist und $k>0$, dann
>$$\phi(p^k)=p^k-p^{k-1}$$
>>[!proof]- Beweis
>>Wir suchen die Anzahl aller teilerfremden Zahlen zu $p^k$. Dafür gibt es laut [[3 - RSA (Rivest Shamir Adleman)#^f287d3|Definition]] insgesamt $p^k$ viele Kandidaten. Wegen der Beschaffenheit von $p^k$ können nur Vielfache einen $\text{ggT}(p^k,n)>1$ geben, die $p$ als Faktor enthalten. Diese sind
>>$$p,2p,3p,\dots,\underbrace{ p^{k-1}p }_{ =p^k }$$
>>das sind insgesamt $p^{k-1}$. Also ziehen wir diese von der maximalen Anzahl $p^k$ ab und erhalten
>>$$\phi(p^k)=p^k - p^{k-1}$$
>>$$\tag*{$\square$}$$

^11f681

>[!theorem] Satz Multiplikativität der Euler'schen Phi-Funktion ([[../../PDFs/burton2010.pdf#page=145|Quelle]])
>Die Euler'sche Phi-Funktion ist multiplikativ, also für $n,m \in \mathbb{N}$ mit $\text{ggT}(n,m)=1$
>$$\phi(nm)=\phi(n)\phi(m)$$
>>[!proof]- Beweis
>> Wir definieren zunächst eine Menge $A$, die alle teilerfremden Zahlen zu $nm$ listet, bevor wir sie in der [[3 - RSA (Rivest Shamir Adleman)#^f287d3|Euler'schen Phi-Funktion]] zählen, also
>> $$A=\{ k \in \mathbb{N} \;|\; k \leq nm \text{ und } \text{ggT}(k,nm)=1\ \}$$
>> Nun definieren wir eine Funktion $f: A \to B\times C$ abbildet, wobei $B$ die Menge der zu $n$ teilerfremden Zahlen enthält und $C$ respektive zu $m$. Dies lässt sich aus der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^2548b2|Implikation]] herleiten, dass
>> $$\text{ggT}(nm,x)=1 \iff \text{ggT}(n,x)=1 \land \text{ggT}(m,x)=1$$
>> Wir wollen damit zeigen, dass aufgrund der Eigenschaften des Kreuzprodukts bzw. des [[../../PhD Studies/Mathematic Basics/Combinatorics/Counting Techniques#^e662cc|Multiplikationsprinzips]] gilt
>> $$ \underbrace{ \mid A \mid }_{ \phi(nm) } = \underbrace{ \mid B\mid }_{ \phi(n) } \cdot \underbrace{ \mid C\mid }_{ \phi(m) }$$
>> was nur gilt, wenn $f$ bijektiv ist. Es gilt nun lediglich zu zeigen, dass $f$ bijektiv ist. Wir definieren die Funktion $f$ wie folgt
>> $$f(x)=(x \text{ mod } n, x \text{ mod } m)$$
>> für $x \in A$. Wir definieren
>> $$\begin{align}
>> s &= x \text{ mod } n \tag{1} \\
>> t &= x \text{ mod } m \tag{2}
>>\end{align}$$
>>wobei $1 \leq s < n$ und $1 \leq t <m$ gilt, was der Forderung für $\phi(n)$ und $\phi(m)$ entspricht. Dies kann sich mithilfe des [[4 - Angriffe auf RSA#^ca7b4b|chinesischer Restsatzes]] darstellen, welcher uns garantiert, dass es eine **eindeutige** Lösung bezüglich $\text{ mod } nm$ gibt. Da $\text{ggT}(n,m)=1$ können wir den chinesischen Restsatz auch verwenden. Die Eindeutigkeit erfüllt die Forderung der Injektivität, wobei die Surjektivität bereits aus der Definition der Mengen folgt.
>>$$\tag*{$\square$}$$

^45f45f

>[!theorem] Satz Faktorisierung der Euler'schen Phi-Funktion ([[../../PDFs/burton2010.pdf#page=146|Quelle]])
>Sei $n>1$ mit der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^50378b|Faktorisierung]]  $$n=p_{1}^{k_{1}}p_{2}^{k_{2}}\dots p_{r}^{k_{r}}$$
>dann gilt
>$$\begin{align}
> \phi(n)&= \Big(p_{1}^{k_{1}}-p_{1}^{k_{1}-1}\Big)\Big(p_{2}^{k_{2}}-p_{2}^{k_{2}-1}\Big)\dots\Big(p_{r}^{k_{r}}-p_{r}^{k_{r}-1}\Big) \\
> &= n\left( 1-\frac{1}{p_{1}} \right)\left( 1-\frac{1}{p_{2}} \right)\dots\left( 1-\frac{1}{p_{r}} \right)
>\end{align}$$
>>[!proof]- Beweis
>> Wir zeigen über [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^f974a9|vollständige Induktion]] für $r \geq 1$
>> 
>> Der Induktionsanfang ergibt 
>> $$n=p_{1}^{k_{1}}$$
>> und laut dem Satz [[#^11f681|Euler'sche Phi Funktion von Primpotenzen]] ergibt das
>> $$\phi(n)=\phi(p_{1}^{k_{1}})=p_{1}^{k_{1}}-p_{1}^{k_{1}-1}$$
>> was der Forderung des Satzes entspricht. $$\tag*{$\checkmark$}$$
>> 
>> Im Induktionsschritt überlegen wir, ob die Aussage für $r \mapsto r+1$ noch gültig ist. Wir stellen zunächst fest, dass
>> $$\text{ggT}(p_{1}^{k_{1}}p_{2}^{k_{2}}\dots p_{r}^{k_{r}},p_{r+1}^{k_{r+1}})=1$$
>> weil $p_{r+1}$ nicht als Faktor im anderen Argument enthalten ist. Dies erlaubt uns die [[#^45f45f|Multiplikativität der Euler'schen Phi-Funktion]] zu nutzen. Also
>> $$\begin{align}
>> \phi(p_{1}^{k_{1}}p_{2}^{k_{2}}\dots p_{r}^{k_{r}}p_{r+1}^{k_{r+1}})&=\phi(p_{1}^{k_{1}}p_{2}^{k_{2}}\dots p_{r}^{k_{r}})\phi(p_{r+1}^{k_{r+1}}) \\
>> &=\phi(p_{1}^{k_{1}}p_{2}^{k_{2}}\dots p_{r}^{k_{r}})(p_{r+1}^{k_{r+1}}-p_{r+1}^{k_{r+1}-1}) \tag{1}
>>\end{align}$$
>>wobei wir in Gleichung $(1)$ den Satz [[#^11f681|Euler'sche Phi Funktion von Primpotenzen]] angewandt haben. Der vordere Teil der Gleichung $(1)$ entspricht unserer Induktionsbehauptung. Wenn wir einsetzen, erhalten wir die gesuchte Form des Induktionsschlusses, also
>>$$\phi(p_{1}^{k_{1}}p_{2}^{k_{2}}\dots p_{r}^{k_{r}}p_{r+1}^{k_{r+1}})=\Big(p_{1}^{k_{1}}-p_{1}^{k_{1}-1}\Big)\Big(p_{2}^{k_{2}}-p_{2}^{k_{2}-1}\Big)\dots\Big(p_{r}^{k_{r}}-p_{r}^{k_{r}-1}\Big)\Big(p_{r+1}^{k_{r+1}}-p_{r+1}^{k_{r+1}-1}\Big)$$
>>
>>Den zweiten Ausdruck erhalten wir, indem wir jeweils die $p_{i}^{k_{i}}$ ausklammern und somit als Faktor $n$ erhalten.
>>$$\tag*{$\square$}$$

>[!Lemma] Lemma ([[../../PDFs/burton2010.pdf#page=149|Quelle]])
> Sei $n>1, a\in \mathbb{Z}$ und $\text{ggT}(a,n)=1$.  
> 
> Wenn $a_{1},a_{2},\dots, a_{\phi(n)}$ alle zu $n$ teilerfremden Zahlen ($\text{ggT}(a_{i},n)=1$) kleiner als $n$ sind, dann
> $$\begin{align}
> aa_{1} &\equiv a_{1}' \;\;(\text{mod } n) \\
> aa_{2} &\equiv a_{2}' \;\;(\text{mod } n) \\
>  \vdots& \\
> aa_{\phi(n)} &\equiv a_{\phi(n)}' \;\;(\text{mod } n)
>\end{align}$$
>wobei jedes der $a_{i}'$ jeweils **einem** der $a_{j}$ entspricht.
>>[!proof]- Beweis
>> Wir bemerken, dass
>> $$aa_{i} \not\equiv aa_{j} \;\;(\text{mod } n)$$
>> gilt. Angenommen die Kongruenz würde gelten, so hätten wir
>> $$\begin{align}
>> aa_{i} &\equiv aa_{j} &&\;\;(\text{mod } n) \qquad&&\Big\vert \cdot a^{-1} \\ 
>> a_{i} &\equiv a_{j}&&\;\;(\text{mod } n)
>>\end{align}$$
>>was ein Widerspruch wäre, dass wir unterschiedliche $a_{i}$ hätten. Daher kann jedes $aa_{i}'$ nur genau zu einem $a_{j}$ kongruent bezüglich $n$ sein. 
>>
>>Der Zusammenhang [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^2548b2|der Teilerfremde von Produkten]] erlaubt uns folgende Schlussfolgerung zu machen
>>$$\text{ggT}(a,n) = 1 \land \text{ggT}(a_{i},n)=1 \implies \text{ggT}(aa_{i},n)=1$$
>>Wir fixieren eines der $a_{i}$ und definieren $1 \leq b <n$ mit
>>$$b \equiv aa_{i} \;\;(\text{mod } n)$$
>>Dann gilt
>>$$\text{ggT}(b,n)=\text{ggT}(aa_{i},n)=1$$
>>und demnach muss $b$ eine der $a_{j}$ sein.
>>$$\tag*{$\square$}$$

^a735ad

>[!theorem] Euler's Satz ([[../../PDFs/burton2010.pdf#page=149|Quelle]])
>Wenn $n \geq 1$ und $\text{ggT}(a,n)=1$, dann
>$$a^{\phi(n)}\equiv 1 \;\;(\text{mod } n)$$
>>[!proof]- Beweis
>> Ohne Beschränkung der Allgemeinheit beschränken wir $n>1$. Seien $a_{1},a_{2},\dots, a_{\phi(n)}$ alle zu $n$ teilerfremden Zahlen ($\text{ggT}(a_{i},n)=1$) kleiner als $n$, dann wissen wir aus dem [[#^a735ad|vorherigen Lemma]], dass
>> $$\begin{align}
>> aa_{1} &\equiv a_{1}' &&\;\;(\text{mod } n)\\
>> aa_{2} &\equiv a_{2}' &&\;\;(\text{mod } n)\\
>> \vdots&\\
>> aa_{\phi(n)} &\equiv a_{\phi(n)}' &&\;\;(\text{mod } n)\\
>>\end{align}$$
>>Wir multiplizieren nun alle Kongruenzen und erhalten
>>$$\begin{align}
>> (aa_{1})(aa_{2})\dots(aa_{\phi(n)}) &\equiv a'_{1}a'_{2}\dots a'_{\phi(n)} &&\;\;(\text{mod } n) \\
>> &\equiv a_{1}a_{2}\dots a_{\phi(n)} &&\;\;(\text{mod } n)
>>\end{align}$$
>>was aus dem [[#^a735ad|vorherigen Lemma]] folgt. Da auf der Linken Seite $\phi(n)$ mal $a$ multipliziert wird, können wir schreiben
>>$$\begin{align}
>> a^{\phi(n)}(a_{1}a_{2}\dots a_{\phi(n)}) &\equiv a_{1}a_{2}\dots a_{\phi(n)} &&\;\;(\text{mod } n) \qquad&&\Big\vert \cdot (a_{1}a_{2}\dots a_{\phi(n)})^{-1} \\ 
>> a^{\phi(n)} &\equiv 1 &&\;\;(\text{mod } n) \\
>>\end{align}$$
>>$$\tag*{$\square$}$$
>
>>[!remark]- Bemerkung zur Verbindung zum [[3 - RSA (Rivest Shamir Adleman)#^5e7c61|kleinen Satz von Fermat]]
>>Wenn wir $n$ als eine Primzahl $p$ wählen, dann erhalten wir wegen der [[3 - RSA (Rivest Shamir Adleman)#^481d74|Euler'schen Phi-Funktion von Primzahlen]]
>>$$a^{\phi(p)}\equiv a^{p-1} \equiv 1 \;\;(\text{mod } p)$$
>>den [[3 - RSA (Rivest Shamir Adleman)#^5e7c61|kleinen Satz von Fermat]].

^c91d0f

## X.2 Primitive Wurzel

>[!def] Definition Ordnung von Restklassen ([[../../PDFs/burton2010.pdf#page=159|Quelle]])
>Sei $n>1$ und $\text{ggT}(a,n)=1$. Die **Ordnung von** $a$ **bezüglich modulo $n$** ist die kleinste ganze Zahl $k$, sodass
>$$a^k \equiv 1 \;\;(\text{mod } n)$$
>>[!example]- Beispiel $2$ bezüglich modulo $7$
>>$2$ hat die Ordnung $3$ bezüglich modulo $7$, weil
>>$$2^3 \equiv 1 \;\;(\text{mod } 7)$$
>>und es kein kleineres $k \in \mathbb{N}$ gibt, welche diese Kondition erfüllt.
>
>>[!remark]- Bemerkung zur Bedeutung von "Ordnung von $a$ bezüglich modulo $n$"
>>Wenn wir davon sprechen, dass $a$ Ordnung $k$ bezüglich modulus $n$ hat, implizieren wir, dass $\text{ggT}(a,n)=1$ gilt.

^86d16a

>[!theorem] Satz ([[../../PDFs/burton2010.pdf#page=160|Quelle]])
>Sei $a \in \mathbb{Z}$ mit [[#^86d16a|Ordnung]] $k$ bezüglich modulo $n$, dann gilt
>$$a^h \equiv 1 \;\;(\text{mod } n) \iff k \;|\; h$$
>
>>[!proof]- Beweis
>>Wir starten mit $(\Longleftarrow)$
>>
>>Gegeben ist, dass $k \;|\; h$, das bedeutet aufgrund der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^9380e8|ganzzahligen Teilung]]
>>$$\exists j \in \mathbb{Z}: jk = h$$
>>Da $a$ der Ordnung $k$ ist können wir ableiten
>>$$\begin{align}
>> a^k &\equiv 1 &&\;\;(\text{mod } n) \qquad&&\Big\vert (\cdot)^j \\
>> (a^k)^j &\equiv 1^j &&\;\;(\text{mod } n) \\
>> a^{jk} &\equiv 1 &&\;\;(\text{mod } n) \\
>> a^{h} &\equiv 1 &&\;\;(\text{mod } n) \\
>>\end{align}$$
>>$$\tag*{$\checkmark$}$$
>>
>>---
>>
>>Wir setzen mit ($\implies$) fort
>>
>>Wir wollen nun $h$ durch $k$ teilen. Der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^30b120| Existenz und Eindeutigkeit des Quotienten und Rests]] erlaubt uns dies wie folgt darzustellen
>>$$h = jk + r$$
>>mit $j \in \mathbb{Z}$ und $0 \leq r <\lvert k \rvert$.  Das bedeutet
>>
>>$$\begin{align}
>> a^h &\equiv 1 && \;\;(\text{mod } n)\\
>> a^{qk+r} &\equiv 1 &&\;\;(\text{mod } n)  \\
>> (a^k)^q a^r &\equiv 1 &&\;\;(\text{mod } n)
>>\end{align}$$
>>
>>Dadurch $a^k \equiv 1 \;\;(\text{mod } n)$ und $a^h \equiv 1 \;\;(\text{mod } n)$ gilt, muss $a^r \equiv 1 \;\;(\text{mod } n)$ gelten. Da aber $r < k$, erzeugt das einen Widerspruch dazu, dass $a$ von $k$-ter Ordnung ist. Somit muss
>>$$h=jk \implies k \;|\; h \tag*{$\checkmark$}$$
>>$$\tag*{$\square$}$$ 
>
>>[!remark]- Bemerkung zu $k \;|\; \phi (n)$
>>Es gilt auch, dass $k \;|\; \phi(n)$, da
>>$$a^{\phi(n)}=1 \;\;(\text{mod } n)$$
>>unter den gegebenen Bedingungen gilt.

^c447c3

>[!theorem] Satz ([[../../PDFs/burton2010.pdf#page=160|Quelle]])
>Sei $a \in \mathbb{Z}$ mit [[#^86d16a|Ordnung]] $k$ bezüglich modulo $n$, dann gilt
>$$a^i \equiv a^j \;\;(\text{mod } n) \iff i \equiv j \;\;(\text{mod } k)$$
>
>>[!proof]- Beweis
>>Wir starten mit ($\implies$)
>>
>>da $\text{ggT}(a,n)=1$ [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^c7c061|existiert das Inverse]] von $a$ und wir können folgende Äquivalenzumformung machen
>>$$\begin{align}
>> a^i &\equiv a^j &&\;\;(\text{mod } n) \qquad&&\Big\vert \cdot a^{-j} \\
>> a^{i-j} &\equiv 1 &&\;\;(\text{mod } n) \\
>>\end{align}$$
>>Nach dem [[#^c447c3|vorangegangenen Satz]] kann diese Relation nur stimmen, wenn $k \;|\; i-j$. Über den Satz der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Kongruenzen]] können wir schließen, dass
>>$$i \equiv j \;\;(\text{mod } k) \tag*{$\checkmark$}$$
>>---
>>Wir setzen fort mit ($\Longleftarrow$)
>>
>>Es gilt nun aufgrund von dem Satz der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Kongruenzen]]
>>$$i \equiv j \;\;(\text{mod } k) \implies k \;|\; i-j \implies \exists q \in \mathbb{Z}: qk = i-j$$
>>Wir stellen um
>>$$i = qk+j$$
>>und erhalten für
>>$$a^{i} \equiv a^{qk}a^{j} \equiv \underbrace{ (a^{k})^q }_{ \equiv 1} a^j \equiv a^j \;\;(\text{mod } n) \tag*{$\checkmark$}$$
>>$$\tag*{$\square$}$$

^7e0196

>[!lemma] Korolar ([[../../PDFs/burton2010.pdf#page=161|Quelle]])
>$$a \text{ ist von Ordnung } k \text{ bezüglich modulo } n \implies a,a^2,\dots,a^k \text{ sind inkongruent bezüglich modulo } n$$
>>[!proof]- Beweis
>>Angenommen $$a^i \equiv a^j \;\;(\text{mod } n)$$
>>mit $0 \leq i < j <k$. Allerdings garantiert der [[#^7e0196|vorangegangene Satz]], dass
>>$$a^i \equiv a^j \;\;(\text{mod } n) \iff i \equiv j \;\;(\text{mod } k)$$
>>was wiederum bedeutet, dass $i=j$ und demnach $a^i=a^j$, was ein Widerspruch dazu ist, dass es zwei verschiedene $a_{i},a_{j}$ gibt, die äquivalent bezüglich $(\text{mod } n)$ sind.
>>$$\tag*{$\square$}$$

^59492a

>[!theorem] Satz ([[../../PDFs/burton2010.pdf#page=161|Quelle]])
>
>Sei $a \in \mathbb{Z}$ mit Ordnung $k$ bezüglich modulo $n$ und $h>0$, dann gilt
>$$a^h \text{ hat Ordnung } \frac{k}{\text{ggT}(h,k)} \text{ bezüglich modulo } n $$
>
>>[!proof]- Beweis
>> Sei $d= \text{ggT}(h,k)$. Wir formulieren $h,k$ an ihrer Quotienten $h_{1},k_{1}$ bezüglich ihres größten gemeinsamen Teilers um, und erhalten
>> $$\begin{align}
>> h &=h_{1}d \tag{1}\\
>> k &=k_{1}d \tag{2}
>>\end{align}$$
>>Dadurch, dass $d$ bereits der größte gemeinsame Teiler ist, gilt
>>$$\text{ggT}(h_{1},k_{1})=1 \tag{3}$$
>>Wir bemerken, dass folgendes gilt
>>$$(a^h)^{k_{1}} \equiv (a^{h_{1}d})^{k/d} \equiv (a^{h_{1}})^d \equiv 1\;\;(\text{mod } n)$$
>>Angenommen $a^{h}$ hat Ordnung $r$ bezüglich modulo $n$, dann können wir von diesem [[#^c447c3|Satz]] schließen, dass
>>$$r \;|\; k_{1} \tag{4}$$
>>Da $a^h$ Ordnung $r$ bezüglich modulo $n$ hat, können wir sagen
>>$$a^{hr} \equiv (a^h)^r \equiv 1 \;\;(\text{mod } n)$$
>>Außerdem hat $a$ Ordnung $k$ bezüglich modulo $n$, daher können wir aus [[#^c447c3|diesem Satz]] schließen, dass
>>$$k \;|\; hr$$
>>Aus Gleichungen $(1)$ und $(2)$ können wir schließen
>>$$k \;|\; hr \implies k_{1}d \;|\; h_{1}dr \implies k_{1} \;|\; h_{1}r$$
>>Wir hatten aber in Gleichung $(3)$ bereits festgestellt, dass $h_{1}$ und $k_{1}$ keine gemeinsamen Teiler haben, daher muss
>>$$k_{1} \;|\; r \tag{5}$$
>>Aussage $(4)$ und $(5)$ zusammengenommen lassen folgern, dass
>>$$k_{1}=r$$
>>Daher können wir festhalten
>>$$r=k_{1}=\frac{k}{d}=\frac{k}{\text{ggT}(h,k)}$$
>>$$\tag*{$\square$}$$
>
>>[!example]- Beispiel Ordnungen bezüglich modulo 13
>>$$\begin{align}
>> \text{Zahl } &\to \text{ Ordnung}  \\
>> 1 &\to 1 \\
>> 2 &\to 12 \\
>> 3 &\to 3 \\
>> 4 &\to 6 \\
>> 5 &\to 4 \\
>> 6 &\to 12 \\
>> 7 &\to 12 \\
>> 8 &\to 4 \\
>> 9 &\to 3 \\
>> 10 &\to 6 \\
>> 11 &\to 12 \\
>> 12 &\to 2 \\
>>\end{align}$$
>>Wir betonen $2$ hat Ordnung $12$
>>-> $2^2=4$ hat Ordnung $\dfrac{12}{\text{ggT}(2,12)}=\dfrac{12}{2}=6$
>>-> $2^3=8$ hat Ordnung $\dfrac{12}{\text{ggT}(3,12)}=\dfrac{12}{3}=4$

^c43fde

>[!lemma] Korolar ([[../../PDFs/burton2010.pdf#page=161|Quelle]])
> Sei $a \in \mathbb{Z}$ mit Ordnung $k$ bezüglich modulo $n$. 
> 
> Dann hat $a^h$ ebenfalls Ordnung $k$ bezüglich modulo $n$ genau dann, wenn $\text{ggT}(h,k)=1$
>>[!proof]- Beweis
>>Wir beginnen mit ($\Longleftarrow$)
>>
>>Gegeben ist $\text{ggT}(h,k)=1$. Durch den [[#^c43fde|vorangegangenen Satz]] erhalten wir für $a^h$ als Ordnung bezüglich modulo $n$
>>$$\frac{k}{\text{ggT}(h,k)}= \frac{k}{1}=k \tag*{$\checkmark$}$$
>>---
>>Nun setzen wir mit fort mit ($\implies$)
>>
>>Gegeben ist $a^h$ hat Ordnung $k$. Nach [[#^c43fde|demselben Satz]] muss gelten
>>$$\frac{k}{\text{ggT}(h,k)}=k$$
>>Nach Umstellen erhalten wir
>>$$\text{ggT}(h,k)=1 \tag*{$\checkmark$}$$
>>$$\tag*{$\square$}$$

>[!def] Definition Primitive Wurzel ([[../../PDFs/burton2010.pdf#page=162|Quelle]])
> Sei $a,n \in \mathbb{Z}$ mit $n \neq 0$. Wenn $\text{ggT}(a,n)=1$ und $a$ hat Ordnung $\phi(n)$ bezüglich modulo $n$, dann ist $a$ die **primitive Wurzel** von $n$.

^2e5c1d

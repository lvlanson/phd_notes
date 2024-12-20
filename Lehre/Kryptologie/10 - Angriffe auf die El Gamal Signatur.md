## 10.1 Mathematische Grundlagen

>[!remark]- Motivation: Lineare Kongruenzen
>Um einen der kommenden Angriffe richtig verstehen zu können, benötigen wir ein Verständnis darüber *lineare Kongruenzen* lösen zu können. Diese sind von der Form für $a,b,x,n \in \mathbb{Z}$ mit $n \neq 0$
>$$ax \equiv b \;\;(\text{mod } n)$$
>wobei $x$ die gesuchte Größe ist. Dabei suchen wir vor allem $x \in \mathbb{Z}$ die inkongruent bezüglich modulo $n$ sind, bzw. dass verschiedene [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^638cd1|Restklassen]] gesucht werden.

>[!theorem] Satz Größter Gemeinsamer Teiler Kongruenz ([[../../PDFs/burton2010.pdf#page=78|Quelle]])
> Wenn für $a,b,c,n \in \mathbb{Z}$ mit $n \neq 0$ 
> $$ca \equiv cb \;\;(\text{mod } n)$$
> dann
> $$a \equiv b \;\;\left( \text{mod } \frac{n}{d} \right)$$
> mit $d=\text{ggT}(c,n)$
>>[!proof]- Beweis
>>In Kombination von [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Äquivalenzen]] und [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Definition der ganzzahligen Teilung]] können wir die Prämisse umschreiben als
>>$$\begin{align}
>> ca \equiv cb \;\;(\text{mod } n) &\iff n \mid (ca-cb) \\
>> &\iff \exists k \in \mathbb{Z}: ca-cb=kn
>>\end{align}$$
>>Über die Bedingung, dass $d=\text{ggT}(c,n)$ gilt, wissen wir, dass $c$ und $n$ den größten **gemeinsamen Teiler** $d$ haben. Daher lassen sich beide Werte faktorisieren mit
>>$$\begin{align}
>> c &= rd \\
>> n &= sd
>>\end{align}$$
>>mit $r,s \in \mathbb{Z}$ und demzufolge $\text{ggT}(r,s)=1$ (alle gemeinsamen Teiler waren schon mit $d$ vereint). Demzufolge gilt jetzt auch $\text{ggT}(n,s)=\text{ggT}(n,r)=1$, da alle gemeinsamen Faktoren $d$ bereits entfernt wurden. Wir setzen ein und erhalten
>>$$\begin{align}
>> ca-cb&=kn  \\
>> c(a-b)&=kn \\
>> rd(a-b)&=sdn \qquad&&\Big\vert :d \\
>>r(a-b) &=sn
>>\end{align}$$
>>Wir können jetzt aus derselben Logik der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Äquivalenzen]] und [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Definition der ganzzahligen Teilung]] rückschließen
>>$$\begin{align}
>> r(a-b) =sn &\iff n \mid r(a-b) 
>> \end{align}$$
>> Der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^f65359|Satz des Primzahlquotienten]] sagt, dass wenn $n \mid r(a-b) \land n \not\mid r \implies n\mid a-b$, also
>> $$\begin{align}
>> \phantom{r(a-b) =sn} &\iff s \mid a-b \phantom{\;\;\;\;}  \\
>> &\iff a \equiv b \;\;&&(\text{mod } s) \\
>> &\iff a \equiv b \;\;&&\left(\text{mod } \frac{n}{d} \right) \tag*{$\square$}
>> \end{align}$$
>
>>[!remark] Kontrollfrage: Was passiert wenn $n$ eine Primzahl ist?

^9c4913

>[!theorem] Satz Lineare Diophantinische Gleichungen (Informativ) ([[../../PDFs/burton2010.pdf#page=46|Quelle]])
> Die **lineare Diophantinische Gleichung** für gegebene $a,b,c \in \mathbb{Z}$ und gesuchte $x,y \in \mathbb{Z}$
> $$ax +by = c$$
> hat eine Lösung genau dann, wenn
> $$d \;|\; c \text{ mit } d=\text{ggT}(a,b)$$
> Wenn $x_{0},y_{0} \in \mathbb{Z}$ eine mögliche Lösung für die Gleichung ist, dann sind alle Lösungen beschrieben mit
> $$\begin{align}
> x &= x_{0}+\left( \frac{b}{d} \right)t\\
> y &= y_{0}-\left( \frac{a}{d} \right)t\\
>\end{align}$$
> für beliebige $t \in \mathbb{Z}$.
>
>>[!proof]- Beweis
>>
>><u>Existenz der Lösung</u>
>>
>>Wir nehmen zunächst an, dass $x_{0},y_{0} \in \mathbb{Z}$ Lösungen für die Diophantinische Gleichung sind. Das heißt wir haben
>>$$\begin{align}
>> ax+by&=c \\
>> ax_{0}+by_{0}&=c \\
>>\end{align}$$
>>Wir können demnach die Gleichungen gleichsetzen und erhalten
>>$$\begin{align}
>> ax + by &= ax_{0}+by_{0} \qquad&&\Big\vert -ax_{0}-by  \\
>> ax-ax_{0} &= by_{0}-by \\
>> a(x-x_{0}) &= b(y_{0}-y) \tag{1}
>>\end{align}$$
>>Wir erinnern uns daran, dass $d=gc d(a,b)$. Also $d \in \mathbb{N}$ ist eine Zahl, die sowohl $a$ und $b$ teilt. Daher wissen wir nach der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^30b120|Existenz und Eindeutigkeit des Quotienten]], dass jeweils eine Zahl $r,s \in \mathbb{Z}$ existieren, sodass
>>$$\begin{align}
>> a&=dr \tag{2}\\
>> b&=ds \tag{3}
>>\end{align}$$
>>Wenn wir diese Ausdrücke in Gleichung $(1)$ einsetzen, können wir entsprechend $d$ eliminieren
>>$$\begin{align}
>> a(x-x_{0}) &= b(y_{0}-y)  \\
>> dr(x-x_{0}) &= ds(y_{0}-y) \qquad&&\Big\vert :d  \\
>> r(x-x_{0}) &= s(y_{0}-y) \tag{4} \\
>>\end{align}$$
>>Wir stellen folgende Dinge fest
>>1. $\text{ggT}(r,s)=1$ weil wir bereits den größten gemeinsamen Teiler von $a$ und $b$ eliminiert haben (also $d$) und es demnach keine anderen gemeinsamen Teiler geben kann
>>2. $r \;|\; s(y_{0}-y)$, da $x-x_{0}$ eine ganze Zahl ergeben muss
>>-> da $\text{ggT}(s,r)=1$ muss folgen, dass $r \;|\; y_{0}-y$
>>
>> Es folgt nach der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^9380e8|ganzzahligen Teilung]], dass
>> $$\begin{align}
>> \exists t \in \mathbb{Z}:  \\
>> rt=y_{0}-y \tag{5}
>>\end{align}$$ 
>> Setzen wir dieses Ergebnis in Gleichung $(4)$ ein erhalten wir
>> $$\begin{align}
>> r(x-x_{0})&=srt \qquad&&\Big\vert :r  \\
>> x-x_{0}&=st \tag{6}
>>\end{align}$$
>>Formen wir Gleichung $(5)$ und $(6)$ jeweils nach $x$ und $y$ um erhalten wir
>>$$\begin{align}
>> x = x_{0} + st \tag{7}\\
>> y = y_{0}-rt \tag{8}
>>\end{align}$$
>>Wir stellen Gleichungen $(2)$ und $(3)$ nach $r$ und $s$ um, sodass wir diese dann in Gleichungen $(7)$ und $(8)$ einzusetzen
>>$$\begin{align} 
>> s= \frac{b}{d} &\implies x = x_{0}+\frac{b}{d}t\\[0.5em]
>> r=\frac{a}{d} &\implies y = y_{0}-\frac{a}{d}t
>>\end{align}$$
>>$$\tag*{$\checkmark$}$$
>>
>><u>Gültigkeit der Lösung</u>:
>>
>>Wir setzen die gefundenen Lösungen ein und verifizieren, dass sie die versprochene Gleichheit erzeugen.
>>$$\begin{align}
>>  c &= ax +by \\
>> &= a\left(x_{0}+\frac{b}{d}t\right) + b\left(y_{0}-\frac{a}{d}t\right) \\
>> &= ax_{0} + \cancel{ \frac{ab}{d}t } + by_{0} \cancel{ -\frac{ab}{d}t } \\
>> &=ax_{0}+by_{0}  \\
>> &= c
>>\end{align}$$
>> was zeigt, dass die Wahl von $t$ unabhängig ist und den Beweis abschließt.
>> $$\tag*{$\square$}$$
>
>>[!example]- Beispiel $3x+6y=2$ 
>> Da $$\text{ggT}(6,3)= 3$$
>> und $$3 \not\mid 2$$ gibt es keine ganzzahligen Lösungen für diese Gleichung. $$\tag*{$\blacktriangleleft$}$$
>
>>[!example]- Beispiel $10x+12y = 4$ 
>>Da $$\text{ggT}(10,12)=2$$ und $$2 \;|\;4$$
>>gibt es garantiert Lösungen für die Diophantinische Gleichung. Nach [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^42f9e5|Bezout's Lemma]] finden wir eine Lösung für $x,y\in \mathbb{Z}$
>>$$10x+12y=\text{ggT}(10,12)=2 \tag{1}$$
>>In diesem Fall lässt sich schon mit bloßem hinsehen feststellen, dass
>>$$\begin{align}
>> x&=-1 \\
>> y&=1
>>\end{align}$$
>>Eine Lösung für $(1)$ ist demnach
>>$$10(-1)+12(1)=2$$
>>multiplizieren wir die Gleichung mit $2$ erhalten wir eine mögliche Lösung für die Diophantinische Gleichung
>>$$10(-2)+12(2)=4\tag{2}$$
>>
>>Unser Plan ist der Gleichung einen Term hinzuzufügen, der in Summe $0$ ergibt, aber die Faktoren mit $t \in \mathbb{Z}$ parametrisieren. Zuerst suchen wir das größte gemeinsame Vielfache zwischen $10$ und $12$. 
>>$$\begin{align}
>> \text{ggV}(10,12)&= \frac{\lvert 10\cdot12 \rvert }{\text{ggT}(10,12)} \\
>> &= \frac{120}{2} \\
>> &= 60
>>\end{align}$$
>>Wir wissen, dass sich $10$ und $12$ zu $60$ faktorisieren lassen. Wir sagen nun
>>$$\begin{align}
>> 60 - 60 &= 0 \\
>> 10 \cdot 6 - 12 \cdot 5 & = 0 \qquad&&\Big\vert \cdot t \\
>> 10 \cdot 6t - 12 \cdot 5t & = 0 \tag{3}\\
>>\end{align}$$
>> Wir addieren nun Gleichung $(2)$ und $(3)$ und erhalten
>> $$\begin{align}
>> 10(-2)+10 (6t) + 12(2)-12 (5t) &= 4  \\
>> 10(-2+6t) + 12(2-5t) &= 4 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!example]- Beispiel $172x + 20y =1000$ 
>>Da $$\text{ggT}(172,20)=4$$ und $$4 \;|\;1000$$
>>gibt es garantiert Lösungen für die Diophantinische Gleichung. Nach [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^42f9e5|Bezout's Lemma]] finden wir eine Lösung für $x,y\in \mathbb{Z}$
>>$$172x+20y=4 \tag{1}$$
>>Über den [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^42f9e5|erweiterten euklidischen Algorithmus]] finden wir 
>>$$\begin{align}
>> x&=2 \\
>> y&=-17
>>\end{align}$$
>>Daher ist
>>$$\begin{align}
>>172\cdot 2 +20 \cdot(-17)&= 4 \qquad&&\Big\vert \cdot 250 \\
>>172\cdot 500 +20 \cdot(-4250)&= 1000 \tag{2}
>>\end{align}$$
>>Gleichung $(2)$ eine mögliche Lösung der Diophantinische Gleichung. Wir verwenden denselben Trick wie zuvor und suchen das größte gemeinsame Vielfache von $172$ und $20$ und erhalten
>>$$\begin{align}
>>\text{ggV}(172,20)&= \frac{\lvert 172 \cdot 20 \rvert }{\text{ggT}(172,20)} \\
>> &=\frac{3440}{4} \\
>> &=860
>>\end{align}$$
>>Wir suchen wieder Faktorisierungen aus $172$ und $20$, die in Summe $0$ ergeben
>>$$\begin{align}
>>  860 - 860 &= 0 \\
>> 5 \cdot 172 - 43 \cdot 20 &= 0 \qquad&&\Big\vert \cdot t \\ 
>> 5t \cdot 172 - 43t \cdot 20 &= 0 \tag{3}
>>\end{align}$$
>>Wir addieren Gleichung $(3)$ und $(2)$ 
>>$$\begin{align}
>> 172\cdot 500 +20 \cdot(-4250) + 5t \cdot 172 - 43t \cdot 20&= 1000 + 0 \\
>> 172 \cdot(500+5t) + 20(-4250-43t) &= 1000 
>>\end{align}$$
>>Demnach lösen
>>$$\begin{align}
>> x&=500+5t \\
>> y&=-4250-43t \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!remark]- Bemerkung: Geschichte zu Diophantos von Alexandria (Informativ)
>>Diophantos von Alexandria soll irgendwann um 250 n.Chr. gelebt haben. Er wird gerne auch als der Vater der Algebra bezeichnet, was sich aber von der Algebra wie wir sie heute kennen unterscheidet. Sein Schaffen fand sich in einer Reihe mit vielen großen griechischen Mathematikern wie Euklid ([[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^e21725|siehe Geschichte zu Euklid]]). Er war einer der letzten großen griechischen Mathematiker, die aus diesem Zeitalter entsprungen sind.
>>
>>Diophantos war vor allem aufgrund seines Werkes der **Arithmetica** bekannt geworden. Diesem Werk wird ein ähnliches Gewicht die **Die Elemente** von Euklid zugesprochen. Nicht umsonst war für [[3 - RSA (Rivest Shamir Adleman)#^5e7c61|Fermat]] die Arithmetika die Inspiration seine Sätze zu formulieren und sich einen Spaß mit seinen Zeitgenossen zu machen.
>>
>> Zwischen der Zeit ([[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^e21725|Euklids]]) und Diophantos war Alexandria regelmäßig von Angriffen wie beispielsweise der Römer unter Julius Caesar betroffen (300 v.Chr. - 250 n. Chr.). Bei einem der Angriffe Caesars fing die Bibliothek Feuer und viele damalige Schriften waren vernichtet worden. Kleopatra, eine der Ptolemyer, war sich der Bedeutung der damaligen Bibliothek bewusst, weshalb sie diese wieder errichten lies. 
>> 
>> Theodosius der Große herrschte von 379-395 als letzter Kaiser über das gesamte römische Reich. Er verstand es als eine seiner Aufgaben an der Festigung des Christentums im Römischen Reich zu wirken und war daher auch als ein frommer Christ bekannt. Im Jahr 391 kam es zu schweren Auseinandersetzungen zwischen Christen und Heiden in Alexandria, weshalb Theodosius die Zerstörung der Heiligtümer der Heiden anordnete, wozu ebenfalls das Museum und die Bibliothek Alexandrias gehörte. Leider wurden die Gelehrten beim Versuch das gesammelte Wissen zu retten von Christen niedergemetzelt. 
>>
>>Der zweite Kalif der Muslime mit dem Namen Omar überwältigte Ägypten und auch Alexandria im Jahr 634. Die Stadt Alexandria wurde kampflos an die Muslime übergeben. Omar lies daraufhin alle Schriften vernichten, die dem Koran widersprächen. Alle anderen Schriften wären überflüssig und wurden deshalb auf seinen Befehl ebenfalls zerstört. 
>>
>>Diese Tragödie für das Wissen der Antike ließ Werke von Gelehrten wie Euklid und Diophantos unwiederbringlich auf ewig verschwinden. Wundersam sind dennoch Schriften noch gefunden worden, sodass 6 Bücher des Diophantos uns heute bekannt sind.
>>
>>In diesen Büchern sind 150 Probleme festgehalten. Diese Probleme waren in einer Mischung von gesprochener Sprache und mathematische Symbole präsentiert. Sein Grabstein ziert folgende Schrift
>>
>> ---
>> <center>
>> Hier dies Grabmal deckt Diophantos. Schaut das Wunder! <br>
>> Durch des Entschlafenen Kunst lehret sein Alter der Stein. <br>
>>Knabe zu sein gewährte Gott ihm ein Sechstel des Lebens.  <br>
>>Noch ein Zwölftel dazu sprosst' auf der Wange der Bart.  <br>
>>Dazu ein Siebentel noch, da schloss er das Bündnis der Ehe;  <br>
>>nach fünf Jahren entsprang aus der Verbindung ein Sohn. <br>
>>Wehe, das Kind das geliebte, gerade die Hälfte der Jahre hatt' es des Vaters erreicht, als es dem Schicksal erlag.  <br>
>>Darauf vier Jahre hindurch durch der Größen Betrachtung den Kummer von sich scheuchend auch er kam an das irdische Ziel.  <br>
>></center>
>>
>>---
>>Dieses Rätsel verrät uns wie alt Diophantos wurde, ganz in der Manier seiner Bücher.
>>$$\begin{align}
>> x = \frac{x}{6}+\frac{x}{12}+\frac{x}{7}+5+\frac{x}{2}+4 \iff x= 84
>>\end{align}$$

^ea24cf


>[!theorem] Satz Lösungen für Lineare Kongruenzen ([[../../PDFs/burton2010.pdf#page=88|Quelle]])
>
>Die **lineare Kongruenz**
> $$ax \equiv b \;\;(\text{mod } n)$$
> besitzt Lösungen genau dann, wenn
> $$d \;|\; b \text{ mit } d=\text{ggT}(a,n)$$
> Vielmehr sind alle Lösungen von der Form
> $$x \in \left\{  x_{0}, x_{0}+\frac{n}{d}, x_{0}+\frac{2n}{d},\dots x_{0}+\frac{(d-1)n}{d}  \right\}$$
>>[!proof]- Beweis
>>>[!summary] Strategie des Beweises
>>> 1. Wir zeigen, dass es $d$ verschiedene Lösungen gibt. Dabei zeigen wir über einen Widerspruch, dass bei gleichem $\frac{n}{d}$ die $t$ auch gleich sein müssen.
>>> 2. Danach zeigen wir, dass alle anderen Lösungen bereits in der Liste zu finden sein müssen. Dabei nehmen wir an, es gäbe auch eine andere Lösung, die wir aber dann doch in der angegebenen Liste finden.
>>
>>Wir stellen mit der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Äquivalenzen]] und [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Definition der ganzzahligen Teilung]] fest
>>$$\begin{align}
>> ax \equiv b \;\;(\text{mod } n) &\iff n \mid ax-b  \\
>> &\iff \exists y \in \mathbb{Z}: ax - b = ny \\
>> &\iff ax-ny = b \tag{1}
>>\end{align}$$ 
>> Gleichung $(1)$ ist eine [[#^ea24cf|Lineare Diophantinische Gleichung]] und hat die Lösungen
>> $$\begin{align}
>> x &= x_{0}+\left( \frac{b}{d} \right)t\\
>> y &= y_{0}-\left( \frac{a}{d} \right)t
>>\end{align}$$
>> für beliebige $t \in \mathbb{Z}$ unter der Bedingung $$d \;|\; b \text{ mit } d=\text{ggT}(a,n)$$
>> Wir betrachten nun alle nötigen Belegungen von $t \in\{ 0,1,2,\dots,d-1 \}$. Dadurch bekommen wir die Lösungen
>> $$x \in \left\{  x_{0}, x_{0}+\frac{n}{d}, x_{0}+\frac{2n}{d},\dots x_{0}+\frac{(d-1)n}{d}  \right\}\tag{2}$$
>> Wir behaupten, dass diese Lösungen untereinander nicht kongruent modulo $n$ sind. Wir zeigen dies durch Widerspruch und behaupten, es gäbe zwei verschiedene $t_{1},t_{2}$ mit $0 \leq t_{1} < t_{2} \leq d-1$ die 
>> $$\begin{align}
>> x_{0}+ \frac{n}{d}t_{1} &\equiv x_{0} +\frac{n}{d}t_{2} &&\;\;(\text{mod } n) \qquad&&\Big\vert -x_{0} \\
>>  \frac{n}{d}t_{1} &\equiv \frac{n}{d}t_{2} &&\;\;(\text{mod } n) \\
>>\end{align}$$
>>Nach Konstruktion muss $\text{ggT}\left( \frac{n}{d},n \right)=\frac{n}{d}$. Somit ist nach der [[#^9c4913|größten gemeinsamen Teiler Kongruenz]] das neue Modul
>>$$\frac{n}{\frac{n}{d}}=d$$
>>und erhalten
>>$$\frac{n}{d}t_{1} \equiv \frac{n}{d}t_{2} \;\;(\text{mod } n) \implies t_{1} \equiv t_{2} \;\;(\text{mod } d)$$
>>Daraus folgt, dass $d \mid t_{1}-t_{2}$. Das ist ein Widerspruch, da $0 < t_{1}-t_{2} < d$, daher muss gelten
>>$$t_{1}=t_{2}$$
>>
>>Wir zeigen jetzt noch, dass auch alle anderen Lösungen kongruent zu den Lösungen in Zeile $(2)$ sind. Wir können wegen des [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^30b120|Existenz und Eindeutigkeit des Quotienten und Rests]] können wir $t$ darstellen als
>>$$t=dq+r$$
>>mit $0 \leq r < d$, also haben wir
>>$$\begin{align}
>> x_{0}+\frac{n}{d}t &= x_{0}+\frac{n}{d}(qd+r) \\
>>  &= x_{0}+nq+\frac{n}{d}r \\
>>  &\equiv x_{0}+\frac{n}{d}r \;\;(\text{mod } n) \\
>>\end{align}$$
>>was eine der Lösungen aus $(2)$ entspricht. Daher gibt es $d$ verschiedene Lösungen wie in Zeile $(2)$ angegeben. 
>>$$\tag*{$\square$}$$
>
>
>>[!remark] Kontrollfrage: Warum ist die Lösung mit $t=0$ äquivalent zu $t=d$?

^f30315

## 10.2 Angriffsverfahren auf die El Gamal Signatur

>[!theorem] Selbe $k$-Angriff 
>
>>[!warning] Voraussetzung
>>Der Parameter $k$ wurde nicht wie in der [[9 - El Gamal's Kryptosystem#^13979e|El Gamal Signatur]] beschrieben zufällig gewählt und stattdessen wird dasselbe $k$ für verschiedene Nachrichten verwendet.
>>
>>Zusätzlich muss für zwei Nachrichten $m_{1},m_{2}$ gelten
>>$$\text{ggT}(s_{1}-s_{2},p-1) \mid m_{1}-m_{2}$$
>
>>[!algo] Verfahren
>>Gegeben sind die Signaturen
>>- $(r,s_{1})$ für $m_{1}$ mit $$s_{1}=k^{-1}(m_{1}-Ar) \text{ mod }p-1$$
>>- $(r,s_{2})$ für $m_{2}$ mit $$s_{2}=k^{-1}(m_{2}-Ar) \text{ mod }p-1$$
>>
>>Wir multiplizieren beide $s_{i}$ mit $k$ und erhalten
>>$$\begin{align}
>> ks_{1} &\equiv m_{1}-Ar \;\;(\text{mod } p-1) \tag{1}\\ 
>> ks_{2} &\equiv m_{2}-Ar \;\;(\text{mod } p-1)  \tag{2}
>>\end{align}$$
>>
>>Wir ziehen nun Kongruenz $(2)$ von $(1)$ ab und erhalten
>> $$\begin{align}
>> \underbrace{ k }_{ x }\underbrace{ (s_{1}-s_{2}) }_{ a } \equiv \underbrace{ m_{1}-m_{2} }_{ b } \;\;(\text{mod } p-1) \tag{3}
>>\end{align}$$
>>Dies stellt eine [[#^f30315|lineare Kongruenz]] dar mit $g=\text{ggT}(s_{1}-s_{2},p-1)$. Diese stellt die Bedingung, dass $$\text{ggT}(s_{1}-s_{2},p-1) \mid m_{1}-m_{2}$$
>>Da alle Terme $g$ enthalten, reduzieren wir die Kongruenz $(3)$ um $g$
>>$$k \frac{s_{1}-s_{2}}{g} \equiv \frac{m_{1}-m_{2}}{g} \;\;\left( \text{mod } \frac{p-1}{g} \right) $$
>>Damit ist garantiert, dass $\text{ggT}\left( \frac{s_{1}-s_{2}}{g}, \frac{p-1}{g} \right)=1$ und somit existiert das [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^c7c061|modulare Inverse]]
>>$$\begin{align}
>> k \frac{s_{1}-s_{2}}{g} &\equiv \frac{m_{1}-m_{2}}{g} \;\;&&\left( \text{mod } \frac{p-1}{g} \right)  \qquad&&\Big\vert \cdot \left[ \frac{s_{1}-s_{2}}{g} \right]^{-1}_{\frac{p-1}{g}} \\
>> k  &\equiv \frac{m_{1}-m_{2}}{g} \cdot\left[ \left( \frac{s_{1}-s_{2}}{g} \right)^{-1} \right]_{\frac{p-1}{g}} \;\;&&\left( \text{mod } \frac{p-1}{g} \right)   \\
>>\end{align}$$
>>Nach dem [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^30b120|Satz der Existenz und Eindeutigkeit des Quotienten und Rests]] und der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^9380e8|ganzzahligen Teilung]] können wir $k$ mit $0\leq j < g$
>>$$k_{j}=\frac{m_{1}-m_{2}}{g} \cdot x_{0} + j \frac{p-1}{g}$$
>>mit $$x_{0} = \left[ \left( \frac{s_{1}-s_{2}}{g} \right)^{-1} \right]_{\frac{p-1}{g}} \tag{Modulares Inverses}$$
>>
>>Wir finden das richtige $k_{j}$ indem wir iterativ testen
>>$$a^{k_{j}} \equiv r \;\;(\text{mod } p)$$
>>Damit berechnen wir mögliche $A_{j}$ durch Einsetzen
>>$$A_{j}r \equiv m_{1}-ks_{1} \;\;(\text{mod } p-1)$$
>>und prüfen ob
>>$$a^{A_{j}}\equiv B \;\;(\text{mod } p)$$
>> Das richtige $A_{j}$ erfüllt die Kongruenz und wir sind im Besitz des privaten Schlüssels
>> $$\text{private Key } = (p,a,A)$$
>
>>[!remark] Kontrollaufgabe: Fassen Sie die wesentlichen Schritte zur Berechnung des privaten Schlüssels zusammen.

>[!theorem] Angriff für $r \geq p$
>
>>[!warning] Voraussetzung
>> Bob hat nicht geprüft ob $r<p$ ist und hat ein $r\geq p$ verwendet.
>
>>[!algo] Verfahren
>>Wir wollen eine Nachricht $m$ in einer Signatur durch eine andere Nachricht $m'$ austauschen.
>>1. Eine signierte Nachricht $(m,(r,s))$ abfangen, die die Bedingung erfüllen $$\text{ggT}(m,p-1)=1$$
>>2. Wir berechnen $$\begin{align}
>> u &= m'm^{-1} \text{ mod } p-1 \tag{1}\\
>> s'&= su \text{ mod } p-1 \tag{2}
>>\end{align}$$
>>3. Wir berechnen mit dem [[4 - Angriffe auf RSA#^ca7b4b|chinesischen Restsatz]]
>>$$\begin{align}
>> r' &\equiv ru &&\;\;(\text{mod } p-1) \tag{3}\\
>> r' &\equiv r && \;\;(\text{mod } p) \tag{4}
>>\end{align}$$
>>Wir senden unsere gefälschte Nachricht
>>$$(m',(r',s'))$$
>
>>[!proof]- Korrektheitsnachweis
>>Bei Verifikation haben wir
>>$$\begin{align}
>> v_{1}' &= B^{r'}(r')^{s'} \text{ mod }p \\
>> v_{2}' &= a^{m'} \text{ mod } p
>>\end{align}$$
>>Bevor wir die Verifikation durchführen, formulieren wir unsere Aussagen $(1),(2)$ und $(3)$ um mit Hilfe der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^9cd06c|Definition der binären Modulus Operation]], dem [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Satz der Teilbarkeit von Äquivalenzen]] und der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^9380e8|Definition ganzzahliger Teilung]]
>>$$\begin{align}
>> &u = m'm^{-1} \text{ mod }p-1 &&\implies \exists d_{1} \in \mathbb{Z}: u = m'm^{-1} + d_{1}(p-1)  \tag{1}\\
>> &s'= su \text{ mod } p-1 &&\implies \exists d_{2} \in \mathbb{Z}: s' =su + d_{2}(p-1) \tag{2} \\
>> &r'  \equiv ru \;\;(\text{mod } p-1) &&\implies p-1 \mid r'-ru \implies \exists d_{3} \in \mathbb{Z}: &&r'-ru = d_{3}(p-1)  \\ 
>> &&&&&r' = d_{3}(p-1)+ru \tag{3} \\
>> &r' \equiv r  \;\;(\text{mod } p) \tag{4}
>>\end{align}$$
>>Wir verifizieren nun mithilfe der Formulierungen, die wir getroffen haben
>>$$\begin{align}
>> v_{1}' & \equiv B^{r'}(r')^{s'} &&\;\;(\text{mod } p) \\
>>  & \equiv B^{r'}r^{s'} &&\;\;(\text{mod } p) \tag*{$\leftarrow$ von $(4)$}\\
>>  & \equiv B^{\color{lime}ru+d_{3}(p-1)}r^{s'} &&\;\;(\text{mod } p) \tag*{$\leftarrow$ von $(3)$}\\
>>  & \equiv B^{ru+d_{3}(p-1)}r^{\color{lime}su+d_{2}(p-1)} &&\;\;(\text{mod } p) \tag*{$\leftarrow$ von $(2)$}\\
>>  & \equiv B^{ru}\underbrace{ \Big(B^{d_{3}}\Big)^{(p-1)} }_{ \equiv 1 \;\;(\text{mod } p) }r^{su}\underbrace{ \Big(r^{d_{2}}\Big)^{(p-1)} }_{ \equiv 1 \;\;(\text{mod } p) } &&\;\;(\text{mod } p) \tag{Kl. S. Fermat}\\
>>  & \equiv B^{ru} r^{su}&&\;\;(\text{mod } p) \\
>>  & \equiv \Big(B^{r} r^{s}\Big)^u&&\;\;(\text{mod } p) \\
>>  & \equiv \Big(B^{r} r^{s}\Big)^{\color{lime}m'm^{-1} + d_{1}(p-1)}&&\;\;(\text{mod } p) \tag*{$\leftarrow$ von $(1)$}\\
>>  & \equiv \Big(B^{r} r^{s}\Big)^{m'm^{-1}}\underbrace{ \Bigg(\Big(B^{r} r^{s}\Big)^{d_{1}}\Bigg)^{p-1} }_{ \equiv 1 \;\;(\text{mod } p) } &&\;\;(\text{mod } p) \tag{Kl. S. Fermat} \\
>>  & \equiv \Big(\underbrace{ B^{r} r^{s} }_{ = v_{2} }\Big)^{m'm^{-1}} &&\;\;(\text{mod } p)\\
>>  & \equiv v_{2}^{m'm^{-1}} &&\;\;(\text{mod } p)\\
>>  & \equiv \Big(a^{m}\Big)^{m'm^{-1}} &&\;\;(\text{mod } p)\\
>>  & \equiv a^{\overbrace{mm^{-1}}^{=1}m'} &&\;\;(\text{mod } p)\\
>>  & \equiv a^{m'} &&\;\;(\text{mod } p)\\
>>  & \equiv v_{2}' &&\;\;(\text{mod } p) \tag*{$\square$}
>>\end{align}$$
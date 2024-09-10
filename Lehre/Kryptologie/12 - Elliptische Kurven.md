>[!remark]- Bemerkung: Einführende Motivation
>Wir erinnern uns daran, dass wir für den Angriff auf die El Gamal Signatur die [[10 - Angriffe auf die El Gamal Signatur#^ea24cf|linearen Diophantinischen Gleichungen]] eingeführt haben. Dort haben wir uns damit beschäftigt Lösungen für Gleichungen der Gestalt
>$$ax+by = c$$
>zu finden, wobei $a,b,c \in \mathbb{Z}$ gegeben und $x,y \in\mathbb{Z}$ gesucht sind.
>
> Elliptische Kurven sind besondere Diophantinische Gleichungen, die ein Polynom des **Grades 3** sind und deren Lösungen in den reellen Zahlen liegen. Für unsere Zwecke nennen wir auch die Gleichungen elliptische Kurven, die wir auf die [[2 - Algebraische und Zahlentheoretische Grundlagen (1)|ganzen Zahlen]] beschränken. Beispielsweise kann eine solche Diophantinische Gleichung wie folgt aussehen
> $$y^2 = x^3 +ax^2+bx+c$$
> Im Gegensatz zu [[10 - Angriffe auf die El Gamal Signatur#^ea24cf|linearen Diophantinischen Gleichungen]] und quadratischen Diophantinischen Gleichungen (Grad 2) sind **elliptische Kurven ein noch nicht vollständig durchdrungenes Problem**. Mittlerweile haben wir bereits dafür ein Gefühl entwickelt, dass offene Probleme in der Mathematik dafür genutzt werden können, um Verschlüsselungsalgorithmen zu entwickeln.
> 
> Wir werden uns in diesem Kapitel damit beschäftigen, was elliptischen Kurven sind, wie sie funktionieren, wie man damit rechnet und nicht zuletzt wie Verschlüsselungsalgorithmen wie beispielsweise [[3 - RSA (Rivest Shamir Adleman)#^7c14da|RSA]] oder [[9 - El Gamal's Kryptosystem#^13979e|El Gamal]] auf elliptischen Kurven funktionieren.
> 
>![[Figures/real_elliptic_curve.png|center]]
><center> Abbildung: Elliptische Kurve über den reellen Zahlen </center>
>
>$$y^2 = x^3-2x+2$$
>
>![[Figures/zmod_89_elliptic_curve.png|center]]
><center> Abbildung: Elliptische Kurve über den ganzen Zahlen modulo 89</center>
>
>$$y^2 \equiv x^3-2x+2 \;\;(\text{mod } 89)$$


>[!remark] Bemerkung: Geometrische Motivation
> Wir nehmen an dieser Stelle bereits vorweg, dass **generelle elliptische Kurven** der Form
> $$y^2 = x^3 + ax +b$$
> entsprechen, mit $a,b,x,y \in \mathbb{R}$. Für unsere Zwecke werden wir später die Menge der Koeffizienten auf $\mathbb{Z}$ einschränken, aber zu illustrativen Zwecken werden wir die reellen Zahlen erlauben. Die folgende Abbildung illustriert zwei elliptische Kurven mit reellen Koeffizienten ([[../../PDFs/silverman2008.pdf#page=292|Quelle]])
> 
> ![[Figures/elliptic_curves_examples.png|center|800]]
> <center>Abbildung: Zwei mögliche elliptische Kurven</center>
> 
> <u>Addition zwei verschiedener Punkte</u>:
> 
> Wir werden nun beschreiben, wie die Addition zweier Punkte auf der elliptischen Kurve funktioniert. Seien $P,Q$ Punkte auf der elliptischen Kurve $E$. Wir definieren die Operation $\oplus: E \times E\to E$ auf den elliptischen Kurven, sodass
> $$P \oplus Q = R'$$
> An dieser Stelle werden wir kurz die mathematische Betrachtung hinten anstellen und geometrisch motivieren, wie die Addition funktionieren wird. 
> 
> ![[Figures/elliptic_curve_addition.png|center|600]]
> <center>Abbildung: Addition zwei verschiedener Punkte</center>
> 
> Die Sekante $L=\overline{PQ}$ schneidet die elliptische Kurve in nahezu allen Fällen an genau 3 Punkten (wenn die elliptische Kurve der später kommenden Definition entspricht), wovon zwei $P,Q$ sind und der dritte $R$ ist. Um $R'$ zu finden, spiegeln wir $R$ an der $x$-Achse und erhalten $R'$, was der Multiplikation der $y$-Koordinate mit $-1$ entspricht. Dies nennen wir die **geometrische Interpretation der Addition zweier Punkte auf elliptischen Kurven**.
> 
>>[!example]- Beispiel $E$ ist die elliptische Kurve $y^2=x^3-15x+18$
>>Gegeben seien die Punkte der elliptischen Kurve $E$
>>$$\begin{align}
>> P &= (7,16) \\
>> Q &= (1,2)
>>\end{align}$$
>>und die elliptische Kurve $E$
>>$$y^2 = x^3-15x + 18$$
>>>[!example] Übung: Prüfen Sie, dass die Punkte wirklich auf der Kurve liegen
>>
>> Wir können die Sekante $L$ darstellen mit $m=\frac{y_{2}-y_{1}}{x_{2}-x_{1}}$
>> $$\begin{align}
>> y-y_{1}&= m \cdot(x-x_{1}) \\
>> y-16&= \frac{2-16}{1-7} \cdot(x-7) \\
>> y-16&= \frac{7}{3}x - \frac{49}{3} \qquad&&\Big\vert +16 \\
>> y &= \frac{7}{3}x -\frac{1}{3} \tag{1}
>>\end{align}$$
>>
>>Um die Schnittpunkte von der Sekante $L$ mit unserer elliptischen Kurve $E$ zu bestimmen, setzen wir die Gleichung $(1)$ ein
>>
>>$$\begin{align}
>> \left( \frac{7}{3}x -\frac{1}{3} \right)^2 &= x^3 - 15x + 18 \\
>> \frac{49}{9}x^2 - \frac{14}{9}x + \frac{1}{9}&= x^3 - 15x + 18 \qquad&&\Big\vert -\frac{49}{9}x^2 +\frac{14}{9}x -\frac{1}{9}  \\
>>0 &= x^3 -\frac{49}{9}x^2 - \frac{121}{9}x + \frac{161}{9}
>>\end{align}$$
>> Dieses Polynom dritten Grades kann man analytisch lösen. Allerdings wissen wir bereits zwei Lösungen aus den Punkten $P$ und $Q$ und können über Polynomdivision die Punkte $(x-7)$ und $(x-1)$ ausmultiplizieren und erhalten dann die Faktorisierung
>> $$x^3 - \frac{49}{9}x^2 - \frac{121}{9}x + \frac{161}{9}=(x-7)(x-1)\left( x+\frac{23}{9} \right)$$
>> Daher ist die $x$-Koordinate für den dritten Schnittpunkt $R$ gleich $-\frac{23}{9}$ wir setzen den Punkt einfach in die Gleichung unserer Sekante ein und erhalten
>> $$P \oplus Q = R' = \left( -\frac{23}{9},-\frac{170}{27} \right) \tag*{$\blacktriangleleft$}$$
>
> <u> Addition eines Punktes mit sich selbst</u>:
>
>Wenn beide Punkten identisch sind, also im Sinnbild von eben diese quasi aufeinander liegen, wird aus der Sekante eine Tangente. In diesem Fall haben wir dann nur zwei "Schnittpunkte" mit der elliptischen Kurve, wovon einer nur die elliptische Kurve berührt. Die folgende Abbildung ([[../../PDFs/silverman2008.pdf#page=294|Quelle]]) illustriert dieses Szenario
>
>![[Figures/elliptic_curve_addition_2.png|center|600]]
><center>Abbildung: Addition des selben Punktes mit sich selbst</center>
>
>>[!example]- Beispiel $E$ ist die elliptische Kurve $y^2=x^3-15x+18$
>> Wir setzen das Beispiel von eben fort und verwenden den Punkt
>> $$P = (7,16) $$
>> Um den Anstieg der Tangente am Punkt $P$ zu berechnen, differenzieren wir $E$ über $y$ nach $x$. Dabei ist zu bemerken, dass wir $y$ als eine Funktion über $x$ verstehen.
>> $$\begin{align}
>> y^2(x) &= x^3 - 15x + 18 \qquad&&\Big\vert \frac{d}{dx}  \\
>> \frac{d}{dx} \Big(y^2(x)\Big) &=  \frac{d}{dx} \Big(x^3 - 15x + 18\Big)  \\
>> 2y \frac{dy}{dx} &= 3x^2 -15 \qquad&&\Big\vert :2y  \tag{1}\\
>> \frac{dy}{dx} &= \frac{3x^2-15}{2y} \tag{2}
>>\end{align}$$
>>wobei Gleichung $(1)$ durch die Kettenregel $(y^2(x))'= 2y y'(x)$ entsteht. Wenn wir den Punkt $P$ in $(1)$ einsetzen, erhalten wir den Anstieg für unsere Tangente, also
>>$$\begin{align}
>> m &= \frac{3\cdot7^2-15}{32} \\
>> &= \frac{33}{8}
>>\end{align}$$
>> Wir bestimmen noch den Versatz $n$ auf der $y$-Achse der linearen Gleichung
>> $$\begin{align}
>> y&=mx + n \\
>> 16&=\frac{33}{8}\cdot7+n \qquad&&\Big\vert -\frac{33}{8}\cdot_{7} \\
>> -\frac{103}{8}&=n
>>\end{align}$$
>>Somit ist unsere Geraden $L$ beschrieben mit
>>$$y=\frac{33}{8}x-\frac{103}{8} \tag{3}$$
>>Wir setzen $y$ aus $(3)$ in unsere elliptische Kurve ein, wir erhalten
>>$$\begin{align}
>> \left( \frac{33}{8}x-\frac{103}{8} \right)^2 &= x^3 - 15x + 18  \\
>> \frac{1089}{64}x^2 - \frac{6798}{64}x + \frac{10609}{64} &= x^3 - 15x + 18 \\
>> 0 &= x^3 - \frac{1089}{64}x^2 + \frac{2919}{32}x − \frac{9457}{64}
>>\end{align}$$
>>Wie vorher lösen wir dieses Polynom dritten Grades, wobei wir eine Nullstelle mit Multiplizität 2 kennen, also $x=7$. Daher erhalten wir, wenn wir Polynomdivision mit $(x-7)^2$ durchführen
>>$$x^3 - \frac{1089}{64}x^2 + \frac{2919}{32}x − \frac{9457}{64} = (x-7)^2 \cdot \left( x-\frac{193}{64} \right)$$
>>Wir setzen nun den Punkt $x_{R}=\frac{193}{64}$ in die Gleichung der Gerade $L$ ein, um den Punkt $R$ zu erhalten, also
>>$$\begin{align}
>> y_{R} &= \frac{33}{8}\cdot\left( -\frac{193}{64} \right) -\frac{103}{8} \\
>> &=-\frac{223}{512}
>>\end{align}$$
>>Um dann die Koordinaten für $R'$ zu erhalten, müssen wir noch die $y$-Komponente mit $-1$ multiplizieren und erhalten
>>$$P \oplus P= 2P = R' =\left( \frac{193}{64}, \frac{223}{512}\right) \tag*{$\blacktriangleleft$}$$
>
><u>Addition mit dem Inversen</u>:
>
>Ein besonderer Fall ist die Addition mit dem Inversen $P \oplus P' = \mathcal{O}$ mit $P=(a,b)$ und $P'=(a,-b)$, da wie die folgende Abbildung ([[../../PDFs/silverman2008.pdf#page=296|Quelle]]) zeigt 
>
>![[Figures/elliptic_curve_inverse_addition.png|center|600]]
><center>Abbildung: Addition mit dem Inversen  und der Punkt der Unendlichkeit</center>
>kein weiterer Schnittpunkt mit der elliptischen Kurve über die Sekante entsteht. Dabei nennen wir $\mathcal{O}$ den  **Punkt im Unendlichen**
>
>Unter Verwendung dieser Logik nehmen für $P + \mathcal{O}$ wieder die Sekante, jedoch entsteht hier der Schnittpunkt $P'$, sodass wenn wir $P'$ spiegeln wir wieder $P$ erhalten, also
>$$P + \mathcal{O} = P$$

^ec6d6b

>[!def] Definition Körper
> Wir nennen das Tripel $(\mathbb{K}, +, \cdot)$ einen Körper, wenn
> 1. $(\mathbb{K}, +)$ eine additive [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|kommutative Gruppe]] ist
> 2. $(\mathbb{K} \setminus \{ 0 \}, \cdot)$ eine multiplikative [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|kommutative Gruppe]] ist, wobei $0$ das neutrale Element in $(\mathbb{K},+)$ ist
> 3. das **Distributivgesetz** gilt, also $\forall x,y,z \in \mathbb{K}$ $$x(y+z)=xy+xz$$

>[!def] Definition Elliptische Kurve $E$ ([[../../PDFs/silverman2008.pdf#page=295|Quelle]])
> Eine **elliptische Kurve** über einem Körper $\mathbb{K}$ ist die Menge an Lösungen der Gleichung
> $$E: y^2 = x^3 +ax + b$$
> inklusive des Punktes im Unendlichen $\mathcal{O}$, wobei die Konstanten $a$ und $b$ die Bedingung erfüllen
> $$4a^3 + 27b^2 \neq 0$$
> Wir schreiben
> $$E := \{ (x,y) \in \mathbb{K} \times \mathbb{K} \mid y² = x^3 +ax+b \} \cup \{ \mathcal{O} \}$$

^df2758

>[!remark]- Bemerkung: Zur Bedingung $4a^3+27b^2 \neq 0$
>Diese Bedingung garantiert uns, dass wenn wir die elliptische Kurve faktorisieren, dass wir genau $3$ **verschiedene Nullstellen** finden. 
>
>Wir verzichten darauf, dies genauer zu begründen. Es würde einiges an Grundlagen erfordern, die wir aus zeitgrunden aussparen. Wer sich dafür interessiert, kann in [[../../PDFs/washington2008.pdf|diesem Buch]] einen sehr schönen Einstieg in die Mathematik der elliptischen Kurven finden.

>[!remark]- Bemerkung: Wahl des Körper $\mathbb{K}$ für die elliptische Kurve
>Zum Zweck der Visualisierung haben wir für den Körper die reellen Zahlen $\mathbb{R}$ gewählt, damit die Addition geometrisch nachvollziehbar ist. Für die mathematische Disziplin der elliptischen Kurven sind vorwiegend die Körper über den rationalen Zahlen $\mathbb{Q}$, den ganzen Zahlen $\mathbb{Z}$ und der endlichen Mengen $\mathbb{K}_{q}$, wobei $q = p^k$ mit $k\in \mathbb{N}$

>[!theorem] Satz Operation Addition auf Elliptischen Gruppen ([[../../PDFs/silverman2008.pdf#page=297|Quelle]])
>Sei $E: y^2 = x^3+ax+b$ eine elliptische Kurve mit $a,b,x,y \in \mathbb{K}$ und $P,Q,\mathcal{O} \in E$ Punkte auf der elliptischen Kurve, wobei $\mathcal{O}$ **der Punkt in der Unendlichkeit** ist. Wir definieren die Operation $$\oplus: E \times E \to E$$
>mit dem **Additionsalgorithmus auf elliptischen Kurven**
>1. $$P \oplus \mathcal{O}=\mathcal{O} \oplus P = P$$
>2. Wenn $P=(x,y)$ und $Q=-P=(x,-y)$, dann $$P \oplus (-P) = \mathcal{O}$$
>3. Wenn $P=(x_{1},y_{1})$ und $Q=(x_{2},y_{2})$ mit $y_{1} \neq -y_{2}$, dann definieren wir $$\lambda \begin{cases}
> \dfrac{y_{2}-y_{1}}{x_{2}-x_{1}} & \text{ wenn } P\neq Q \\[0.5em]
> \dfrac{3x_{1}^2+a}{2y_{1}} & \text{ wenn } P = Q
>\end{cases}$$
>dann ist der Punkt $P \oplus Q = R' = (x_{3},y_{3})$ definiert als
>$$\begin{align}
> x_{3} &= \lambda^2 -x_{1} -x_{2} \\
> y_{3} &= \lambda(x_{1}-x_{3})-y_{1}
>\end{align}$$
>
>>[!proof]- Beweis
>>Wir verzichten darauf $1$ und $2$ zu beweisen und nehmen diese einfach als gegebene Definition. Tatsächlich lassen sich $1$ und $2$ über den Projektionsraum $\mathbf{P}_{\mathbb{K}}^2$ über homogenisierte Polynome begründen, da wir uns genauer mit dem *Punkt im Unendlichen* beschäftigen müssten. Wer sich dafür interessiert kann dies genau [[../../PDFs/washington2008.pdf#page=32|hier]] nachlesen.
>>
>>Wir wollen uns vor allem mit der Addition beschäftigen, da diese mit simpler Algebra zu zeigen geht, ohne dass wir ein fundamentales Verständnis um die Theorie von elliptischen Kurven aufbauen müssten.
>>
>>Der Parameter $\lambda$ beschreibt den Anstieg der Sekante ($P \oplus Q$) bzw. der Tangente ($P \oplus P$). Die Sekante hat den Anstieg aus dem Steigungsdreieck
>>$$\lambda = \frac{y_{2}-y_{1}}{x_{2}-x_{1}} \tag{1}$$
>>Für die Tangente müssen wir ein klein wenig mehr Arbeit investieren und *implizit differenzieren*, also
>>$$\begin{align}
>> y^2 &= x^3 +ax+b \qquad&&\Big\vert \frac{d}{dx}  \\
>> 2y \frac{dy}{dx} &= 3x^2 + a \qquad&&\Big\vert :2y  \\
>> \frac{dy}{dx} &= \lambda = \frac{3x^2+a}{2y} \tag{2}
>>\end{align}$$
>>Somit konnten wir die Beschaffenheit des Anstiegs $\lambda$ bereits nachweisen. Wir zeigen nun, wie die Koordinaten $x_{3},y_{3}$ ergeben. Wir wissen, dass die Sekante bzw. Tangente eine Gerade der Form
>>$$Y = \lambda X+\nu$$
>>Den Schnittpunkt mit der $y$-Achse können wir bestimmen, indem wir einen der Punkte einsetzen, also
>>$$\begin{align}
>>y_{1} &= \lambda x_{1} + \nu \\
>> \nu &= y_{1} -\lambda x_{1} \tag{3}
>>\end{align}$$
>>Wir setzen die Gleichung der Geraden ein und lösen
>>$$\begin{align}
>> (\lambda X + \nu)^2 &= X^3 + aX + b \tag{4}\\
>> X^3-\lambda^2X^2+(a-2\lambda \nu)X+(B-\nu^2) &=0
>>\end{align}$$
>>Dieses Polynom dritten Grades können wir lösen und uns ist garantiert, dass zwei der Nullstellen $x_{1},x_{2}$ sind und durch unsere Bedingung für die Diskriminante existiert eine von $x_{1},x_{2}$ verschiedene, dritte Nullstelle. Also können wir über die Nullstellen faktorisieren und erhalten
>>$$\begin{align}
>> X^3-\lambda^2X^2+(a-2\lambda \nu)X+(B-\nu^2) &= (X-x_{1})(X-x_{2})(X-x_{3}) \\
>> &= X^3 - (x_{1}-x_{2}-x_{3})X^2 + (x_{1}x_{2} + x_{1}x_{3} +x_{2}x_{3})X -x_{1}x_{2}x_{3}
>>\end{align}$$
>>Demnach haben wir
>>$$\begin{align}
>> X^3-\lambda^2X^2+(a-2\lambda \nu)X+(B-\nu^2) &= X^3 - (-x_{1}-x_{2}-x_{3})X^2 + (x_{1}x_{2} + x_{1}x_{3} +x_{2}x_{3})X -x_{1}x_{2}x_{3}
>>\end{align}$$
>>Über den Koeffizientenvergleich wissen wir, dass
>>$$\begin{align}
>> -\lambda &= -x_{1}-x_{2}-x_{3} \tag{zu $X^2$} 
>>\end{align}$$
>>Also können wir für $x_{3}$ lösen und erhalten
>>$$x_{3} = \lambda - x_{1}-x_{2}$$
>>Aus Gleichung $(4)$ wissen wir um die Beschaffenheit von $y$, also
>>$$y = \lambda x_{3} + \nu$$
>>Wir müssen noch die $y$-Komponente an der $x$-Achse reflektieren und erhalten
>>$$-y = y_{3}=-\lambda x_{3}-\nu$$
>>Wir setzen noch aus Gleichung $(3)$ die Form von $\nu$ ein und erhalten
>>$$\begin{align}
>> y_{3} &= -\lambda x_{3} -(y_{1} -\lambda x_{1}) \\
>> &= -\lambda x_{3} -y_{1} +\lambda x_{1} \\
>> &= \lambda(x_{1}-x_{3}) - y_{1}
>>\end{align}$$
>>was alle zu zeigenden Teile vervollständigt und den Beweis abschließt.
>>$$\tag*{$\square$}$$

^b85a69

>[!theorem] Satz Additive Kommutative Gruppe auf Elliptischen Kurven
> Sei $E$ eine [[#^df2758|elliptische Kurve]]. Die [[#^b85a69|Addition auf elliptischen Kurven]] bildet eine [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|kommutative Gruppe]] $(E, \oplus)$, also
> 1. $\forall P \in E$ und $\mathcal{O} \in E$ $$P+\mathcal{O} = \mathcal{O}+P = P \tag{Existenz der Identität}$$ 
> 2. $\forall P \in E$ und $\mathcal{O} \in E$ $$P + (-P)=\mathcal{O} \tag{Existenz Inverses Element}$$
> 3. $\forall P,Q,R \in E$ $$(P+Q)+R = P + (Q + R) \tag{Assoziativität}$$
> 4. $\forall P,Q \in E$ $$P+Q = Q + P \tag{Kommutatitivität}$$
> 
>>[!proof]- Beweis (wird weitesgehend weggelassen)
>>Der Beweis benötigt etwas mehr Wissen über **den Punkt in der Unendlichkeit**. Wir haben aber im [[#^ec6d6b|Beispiel der geometrischen Motivation]] gezeigt wiedie Existenz der Identität und das inverse Element zustande kommen. Viel mehr haben wir dort auch gezeigt, dass durch die geometrische Konstruktion die Kommutativität gilt.
>>
>>Der Elefant im Raum ist die Assoziativität. Diese erforder tatsächlich eine Menge Arbeit. Wer überprüfen will, warum die Assoziativität gilt, kann dies schön anschaulich in [[../../PDFs/washington2008.pdf#page=34|dieser Quelle]] von Seite 20 bis 35 sehen. Für den Beweis müssen noch neue Konzepte eingeführt werden, die wir aus Zeitgründen hier aussparen.
>
>
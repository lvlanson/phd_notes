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

>[!def] Definition Elliptische Kurve $E$ ([[../../PDFs/silverman2008.pdf#page=295|Quelle]])
> Eine **elliptische Kurve** ist die Menge an Lösungen der Gleichung
> $$E: y^2 = x^3 +ax + b$$
> inklusive des Punktes im Unendlichen $\mathcal{O}$, wobei die Konstanten $a$ und $b$ die Bedingung erfüllen
> $$4a^3 + 27b^2 \neq 0$$
>

>[!remark] Bemerkung: Zur Bedingung $4a^3+27b^2 \neq 0$
>Diese Bedingung garantiert uns, dass wenn wir die elliptische Kurve faktorisieren, dass wir genau $3$ **verschiedene Nullstellen** finden. Wir fordern also, dass es Nullstellen $u,v,w \in \mathbb{C}$ gibt, also
>$$\begin{align}
> x^3 + ax + b &= (x-u)(x-v)(x-w) \\
> \cancel{ x^3 } + ax+ b &= \cancel{ x^3 } - x^2u -x^2v-x^2z +xuv+xuz+xvz-uvz \\
> ax + b &= -x^2\underbrace{ (u+v+z) }_{ =0 }+ x\underbrace{ (uv+uz+vz) }_{ \widehat{=} a }-\underbrace{ uvz }_{ \widehat{= b} }
>\end{align}$$
>Über den mit den Klammern angedeuteten *Koeffizientenvergleich*, können wir folgende Bedingung formulieren
>$$\begin{align}
> a &= uv+uz+vz \\
> b &= -uvz \\
> 0 &= u+v+z
>\end{align}$$
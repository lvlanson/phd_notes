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
> ![[Figures/elliptic_curves_examples.png|center]]
> <center>Abbildung: Zwei mögliche elliptische Kurven</center>
> 
> Wir werden nun beschreiben, wie die Addition zweier Punkte auf der elliptischen Kurve funktioniert. Seien $P,Q$ Punkte auf der elliptischen Kurve $E$. Wir definieren die Operation $\oplus: E \times E\to E$ auf den elliptischen Kurven, sodass
> $$P \oplus Q = R'$$
> An dieser Stelle werden wir kurz die mathematische Betrachtung hinten anstellen und geometrisch motivieren, wie die Addition funktionieren wird. 
> 
> ![[Figures/elliptic_curve_addition.png|center|600]]
> 
> Die Sekante $L=\overline{PQ}$ schneidet die elliptische Kurve in nahezu allen Fällen an genau 3 Punkten (wenn die elliptische Kurve der später kommenden Definition entspricht), wovon zwei $P,Q$ sind und der dritte $R$ ist. Um $R'$ zu finden, spiegeln wir $R$ an der $x$-Achse und erhalten $R'$, was der Multiplikation der $y$-Koordinate mit $-1$ entspricht. Dies nennen wir die **geometrische Interpretation der Addition zweier Punkte auf elliptischen Kurven**.
> 
>>[!example] Beispiel $E$ ist die elliptische Kurve $y^2=x^3-15x+18$
>>Gegeben seien die Punkte der elliptischen Kurve $E$
>>$$\begin{align}
>> P &= (7,16) \\
>> Q &= (1,2)
>>\end{align}$$
>>>[!example] Übung: Prüfen Sie, dass die Punkte wirklich auf der Kurve liegen
>>
>> Wir können die Sekante $L$ darstellen mit $m=\frac{y_{2}-y_{1}}{x_{2}-x_{1}}$
>> $$\begin{align}
>> Y-y_{1}&= m \cdot(X-x_{1}) \\
>> Y-16&= \frac{2-16}{1-7} \cdot(X-7) \\
>> Y-16&= \frac{7}{3}X - \frac{49}{3} \qquad&&\Big\vert +16 \\
>> Y &= \frac{3}{4}X -\frac{1}{3}
>>\end{align}$$


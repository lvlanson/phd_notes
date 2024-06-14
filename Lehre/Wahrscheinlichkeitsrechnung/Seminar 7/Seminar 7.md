>[!def] Definitionen
>>[!def] Definition Zweiseitiges Konfidenzintervall ([[../Vorlesungsskript_Mathematik3.pdf#page=110|Quelle]])
>>Ein Intervall $I=[G_{u}(X), G_{O}(X)]$ heißt **zweiseitiges Konfidenzintervall (KI)** für den unbekannten Parameter $\Theta$ zum Konfidenzniveau $1-\alpha$, falls
>>$$P(G_{u} \leq \Theta \leq G_{o})=1-\alpha$$ 
>>mit
>>-  $G_{u}= G_{u}(X)$ und $G_{o}=G_{o}(X)$ als Stichprobenfunktionen
>>- $g_{u} = G_{u}(x)$ und $g_{o}=G_{o}(x)$ sind für eine konkrete Stichprobe die Realisierungen von $G_{u}$ und $G_{o}$
>>- $[g_{u}, g_{o}]$ ist ein konkretes KI.
>>- $\alpha$ ist die Irrtumswahrscheinlichkeit
>
>>[!def] Definition Linksseitiges Konfidenzintervall ([[../Vorlesungsskript_Mathematik3.pdf#page=110|Quelle]])
>>Ein Intervall $I=[G_{u}(X), G_{o}(X)]$ heißt **linksseitiges Konfidenzintervall (KI)** für den unbekannten Parameter $\Theta$ zum Konfidenzniveau $1-\alpha$, falls
>>$$P(- \infty \leq \Theta \leq G_{o})=1-\alpha$$
>
>>[!def] Definition Rechtsseitiges Konfidenzintervall ([[../Vorlesungsskript_Mathematik3.pdf#page=110|Quelle]])
>>Ein Intervall $I=[G_{u}(X), G_{o}(X)]$ heißt **rechtsseitiges Konfidenzintervall (KI)** für den unbekannten Parameter $\Theta$ zum Konfidenzniveau $1-\alpha$, falls
>>$$P(G_{u} \leq \Theta \leq \infty)=1-\alpha$$ 
>
>>[!algo]- $(1)$ Verfahren $X$ is normalverteilt mit bekannter Varianz $\sigma^2$ ([[../Vorlesungsskript_Mathematik3.pdf#page=112|Quelle]])
>>
>>Gegeben sei $X \sim N(\mu, \sigma)$ mit $\sigma^2$ bekannt und $\Theta = \mu$
>>1. $\widehat{\Theta}= \overline{X}$ (Arithmetisches Mittel)
>>2. Wir schätzen$$\begin{align}
>> \widehat{\Theta}= \overline{X} \sim N\left( \mu, \frac{\sigma^2}{n} \right) \implies  \widetilde{\Theta}&= \frac{\overline{X}-\mu}{\sqrt{ \frac{\sigma^2}{n} }} \\
>>&=\frac{\overline{X}-\mu}{\sigma}-\sqrt{ n } \sim N(0,1) \\
>>\end{align}$$
>>3. Ansatz für ein Konfidenzintervall
>>$$\begin{align}
>> P\left( c_{N(0,1), \frac{\alpha}{2}}\leq \widetilde{\Theta} \leq c_{N(0,1), 1 - \frac{\alpha}{2}}  \right) &= 1 - \alpha\\
>> P\left( - c_{N(0,1), 1-\frac{\alpha}{2}}\leq \widetilde{\Theta} \leq c_{N(0,1), 1 - \frac{\alpha}{2}}  \right)  &= 1 - \alpha \\
>>\end{align}$$
>>4. Umstellen des Ansatzes
>> $$\begin{align}
>> P\left( - c_{N(0,1), 1-\frac{\alpha}{2}}\leq \frac{\overline{x}-\mu}{\sigma}\cdot \sqrt{ n } \leq c_{N(0,1), 1 - \frac{\alpha}{2}}  \right)  &= 1 - \alpha \\
>> P\left( - c_{N(0,1), 1-\frac{\alpha}{2}}\cdot \frac{\sigma}{\sqrt{ n }}-\overline{x}\leq -\mu \leq c_{N(0,1), 1 - \frac{\alpha}{2}} \cdot \frac{\sigma}{\sqrt{ n }}-\overline{x} \right)  &= 1 - \alpha \\
>> P\left(  \underbrace{ c_{N(0,1), 1-\frac{\alpha}{2}}\cdot \frac{\sigma}{\sqrt{ n }}+\overline{x} }_{ =G_{u} }\geq \mu \geq \underbrace{ -c_{N(0,1), 1 - \frac{\alpha}{2}} \cdot \frac{\sigma}{\sqrt{ n }}+\overline{x} }_{ =G_{o} } \right)  &= 1 - \alpha \\
>>\end{align}$$
>
>>[!algo]- $(2)$ Verfahren  $X$ sei normalverteilt mit bekanntem Erwartungswert $\mu$ ([[../Vorlesungsskript_Mathematik3.pdf#page=113|Quelle]])
>>Gegeben sei $X \sim N(\mu, \sigma)$ mit $\sigma^2$ unbekannt und $\Theta = \mu$
>>1.  $\widehat{\Theta}= \overline{X}$
>>2. Wir schätzen $\widehat{\Theta}$ mit
>>$$S=\sqrt{ S^2 }=\sqrt{ \frac{1}{n-1} \sum_{i=1}^n (X_{i}-\overline{X})^2}$$
>>der t-Verteilung, also
>>$$\widetilde{\Theta}=\frac{\overline{X}-\mu}{S}\cdot \sqrt{ n } \sim t(n-1)$$
>>3. Ansatz für ein Konfidenzintervall
>>$$\begin{align}
>> P\left( c_{t(n-1), \frac{\alpha}{2}} \leq \widetilde{\Theta} \leq c_{t(n-1), 1- \frac{\alpha}{2}} \right) &= 1-\alpha \\
>> P\left( -c_{t(n-1), 1-\frac{\alpha}{2}} \leq \widetilde{\Theta} \leq c_{t(n-1), 1- \frac{\alpha}{2}} \right) &= 1-\alpha \tag{Symmetrie}\\
>>\end{align}$$
>>4. Umstellen des Ansatzes
>>$$\begin{align}
>> P\left( -c_{t(n-1), 1-\frac{\alpha}{2}} \leq \frac{\overline{x}-\mu}{s} \cdot \sqrt{ n }\leq c_{t(n-1), 1- \frac{\alpha}{2}} \right) &= 1-\alpha \\
>> P\left( -c_{t(n-1), 1-\frac{\alpha}{2}} \cdot \frac{s}{\sqrt{ n }} + \overline{x} \leq \mu \leq c_{t(n-1), 1- \frac{\alpha}{2}} \cdot \frac{s}{\sqrt{ n }} + \overline{x}\right) &= 1-\alpha \\
>>\end{align}$$
>
>>[!algo]- $(3)$ Verfahren $X$ sei unbekannt verteilt mit bekannter Varianz $\sigma^2$ ([[../Vorlesungsskript_Mathematik3.pdf#page=114|Quelle]])
>>
>> Gegeben sei $X$ beliebig verteilt mit $\sigma^2$ bekannt und $\Theta = \mu$
>> 1. $\widehat{\Theta} = \overline{X}$
>> 2. $\widetilde{\Theta}= \frac{\overline{X}-\mu}{\sqrt{ \frac{\sigma^2}{n} }} = \frac{\overline{X}-\mu}{\sigma}\cdot \sqrt{ n } \overset{n\to \infty}{\sim} N(0,1)$
>> wenn $n>30$, dann wie bei $(1)$ weiter verfahren.
>
>>[!algo]- $(4)$ Verfahren $X$ sei unbekannt verteilt mit bekanntem Erwartungswert $\mu$ ([[../Vorlesungsskript_Mathematik3.pdf#page=115|Quelle]])
>>Gegeben sei $X$ beliebig verteilt mit $\sigma^2$ unbekannt und $\Theta = \mu$
>> 1. $\widehat{\Theta} = \overline{X}$
>> 2. $\widetilde{\Theta}= \frac{\overline{X}-\mu}{\sqrt{ \frac{s^2}{n} }} = \frac{\overline{X}-s}{\sigma}\cdot \sqrt{ n } \overset{n\to \infty}{\sim} N(0,1)$
>> wenn $n$ ausreichend groß ist, dann setzen wir $s= \sqrt{ \sigma }$ und verfahren wie bei $(1)$

>[!example] Aufgabe (1)
>Aus einer großen Lieferung abgepackter Kartoffeln werden $10$ Säcke entnommen. Folgende Gewichte in $kg$ werden notiert
>
>```
>X = [9.5, 10.5, 10.0, 10.0, 10.2, 10.0, 10.4, 9.6, 9.8, 10.0]
>```
>
>Die Gewichte der Packungen seien näherungsweise normalverteilt. Bestimmen Sie ein zweiseitiges Konfidenzintervall.
>
>1. zum Konfidenzniveau $0.95$ für das durchschnittliche Gewicht der Packungen in der Lieferung.
>
>>[!example]- Lösung
>>Wir haben die Situation, dass $X \sim N(\mu,\sigma)$ und $\sigma^2$ unbekannt ist. Demnach verwenden wir Verfahren $(2)$. Aus der Stichprobe stellen wir fest
>>$$n=10$$
>>Wir bestimmen zunächst den Mittelwert mit
>>$$\overline{X}= \frac{1}{n}\sum_{i=1}^n x_{i}$$
>> Wir erhalten
>> $$\overline{X} = 10.0$$
>> Dann bestimmen wir die Standardabweichung
>> $$\begin{align}
>> S &= \sqrt{ S^2 } \\
>> &= \sqrt{ \frac{1}{n-1} \sum_{i=1}^n (X_{i}-\overline{X}) } \\
>> &= 0.3162
>>\end{align}$$
>> Wir verwenden den erarbeiteten Ansatz
>> $$P\left( -c_{t(n-1), 1-\frac{\alpha}{2}} \cdot \frac{s}{\sqrt{ n }} + \overline{x} \leq \mu \leq c_{t(n-1), 1- \frac{\alpha}{2}} \cdot \frac{s}{\sqrt{ n }} + \overline{x}\right) = 1-\alpha $$
>> wobei wir den Fehler $\alpha=0.05$ haben, demnach haben wir
>> $$\begin{align}
>>P\left( -2.262  \cdot \frac{0.3162}{\sqrt{ 10 }} + 10.0 \leq \mu \leq 2.262 \cdot \frac{0.3162}{\sqrt{ 10 }} + 10.0\right) &= 0.95 \\
>> P(9.7738 \leq \mu \leq 10.2262) &= 0.95 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. zum Konfidenzniveau $0.99$ für das durchschnittliche Gewicht der Packungen in der Lieferung.
>
>>[!example]- Lösung
>>Wir verwenden die Ergebnisse der Aufgabe zuvor und setzen an der Stelle
>>$$P\left( -c_{t(n-1), 1-\frac{\alpha}{2}} \cdot \frac{s}{\sqrt{ n }} + \overline{x} \leq \mu \leq c_{t(n-1), 1- \frac{\alpha}{2}} \cdot \frac{s}{\sqrt{ n }} + \overline{x}\right) = 1-\alpha $$
>>mit $\alpha=0.01$ ein, sodass wir erhalten
>>$$\begin{align}
>> P\left( -3.250  \cdot \frac{0.3162}{\sqrt{ 10 }} + 10.0 \leq \mu \leq 3.250 \cdot \frac{0.3162}{\sqrt{ 10 }} + 10.0\right) &= 0.95 \\
>> P(9.675 \leq \mu \leq 10.325) &= 0.95
>>\end{align}$$
>
>3. Welche Auswirkung hat die Änderung des Konfidenzintervals
>
>>[!example]- Lösung
>>Je geringer die Irrtumswahrscheinlichkeit $\alpha$ desto größer das Konfidenzinterval. Das heißt, dass wir sicherer sein wollen, dass das wahre Mittel innerhalb des Intervalls liegt.

>[!example] Aufgabe (2)
>
>$20$ Messungen der Schaftlänge von Zylinderschrauben ergaben eine mittlere Länge von $18 \text{mm}$ und eine Standardabweichung von $28 \mu \text{m}$. Gesucht sind die Konfidenzgrenzen für die Streubreite mit $\sigma$ mit einer Irrtumswahrscheinlichkeit von $5\%$, wenn die Schaftlänge als normalverteilt angenommen werden kann.
>
>Hinweis: Gesucht ist hier ein KI für $\sigma$ (in $\mu \text{m}$) anstatt für $\sigma^2$.
>>[!example] Lösung
>>Wir erfassen folgende Parameter
>>$$\begin{align}
>> n&=20 \\
>> \overline{x}&=18\,000 \\
>> \sigma &= 28
>>\end{align}$$
>>Wir stellen außerdem fest, dass wir Verfahren $(2)$ anwenden, da 


>[!algo]- Code Aufgabe 1.1
>```python
># Daten als Fließkommazahlen erzeugen
>X = [float(_x) for _x in "9.5 10.5 10.0 10.0 10.2 10.0 10.4 9.6 9.8 10.0".split(" ")]
>
># Erwartungswert berechnen
>o_X = sum(X)/len(X) # = 10.0
>
># Standardabweichung berechnen
>s_X = sum([(_x - o_X)**2 for _x in X])/(len(X)-1) # = 0.1
>
>print(f"n={len(X)}\no_X={o_X}\ns_X={s_X}")
>
>#n=10
>#o_X=10.0
>#s_X=0.1
>```

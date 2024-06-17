>[!def]- Definitionen
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

>[!algo] Zweiseitige Konfidenzintervalle für den Erwartungswert
>>[!algo]- $(1)$ $X$ is normalverteilt mit bekannter Varianz $\sigma^2$ ([[../Vorlesungsskript_Mathematik3.pdf#page=112|Quelle]])
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
>>[!algo]- $(2)$ $X$ sei normalverteilt mit unbekannter Varianz $\sigma^2$ ([[../Vorlesungsskript_Mathematik3.pdf#page=113|Quelle]])
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
>>[!algo]- $(3)$ $X$ sei unbekannt verteilt mit bekannter Varianz $\sigma^2$ ([[../Vorlesungsskript_Mathematik3.pdf#page=114|Quelle]])
>>
>> Gegeben sei $X$ beliebig verteilt mit $\sigma^2$ bekannt und $\Theta = \mu$
>> 1. $\widehat{\Theta} = \overline{X}$
>> 2. $\widetilde{\Theta}= \frac{\overline{X}-\mu}{\sqrt{ \frac{\sigma^2}{n} }} = \frac{\overline{X}-\mu}{\sigma}\cdot \sqrt{ n } \overset{n\to \infty}{\sim} N(0,1)$
>> wenn $n>30$, dann wie bei $(1)$ weiter verfahren.
>
>>[!algo]- $(4)$ $X$ sei unbekannt verteilt mit unbekannter Varianz $\sigma^2$ ([[../Vorlesungsskript_Mathematik3.pdf#page=115|Quelle]])
>>Gegeben sei $X$ beliebig verteilt mit $\sigma^2$ unbekannt und $\Theta = \mu$
>> 1. $\widehat{\Theta} = \overline{X}$
>> 2. $\widetilde{\Theta}= \frac{\overline{X}-\mu}{\sqrt{ \frac{s^2}{n} }} = \frac{\overline{X}-s}{\sigma}\cdot \sqrt{ n } \overset{n\to \infty}{\sim} N(0,1)$
>> wenn $n$ ausreichend groß ist, dann setzen wir $s= \sqrt{ \sigma }$ und verfahren wie bei $(1)$

>[!algo] Zweiseitige Konfidenzintervalle für die Varianz
>
>>[!algo]- $(1)$ $X$ sei normalverteilt mit bekanntem Erwartungswert $\mu$ ([[../Vorlesungsskript_Mathematik3.pdf#page=115|Quelle]])
>>1. $\widehat{\Theta}=S^2$ mit $S^2=\frac{1}{n-1}\sum_{i=1}^n (X_{i}- \overline{X})^2$
>>2. $\widetilde{\Theta}=\frac{nS^2}{\sigma^2} \sim \chi^2(n)$
>>3. Ansatz für ein Konfidenzintervall
>>$$\begin{align}
>> P\left( c_{\chi^2(n),\frac{\alpha}{2}}\leq \widetilde{\Theta}\leq c_{\chi^2(n),1-\frac{\alpha}{2}} \right) &= 1 - \alpha \\
>>\end{align}$$
>>4. Umstellen des Ansatzes
>>$$\begin{align}
>> P\left( c_{\chi^2(n),\frac{\alpha}{2}}\leq \frac{ns^2}{\sigma^2}\leq c_{\chi^2(n),1-\frac{\alpha}{2}} \right) &= 1 - \alpha \\
>> P\left( \frac{c_{\chi^2(n),\frac{\alpha}{2}}}{ns^2}\leq \frac{1}{\sigma^2}\leq \frac{c_{\chi^2(n),1-\frac{\alpha}{2}}}{ns^2} \right) &= 1 - \alpha \\
>> P\left( \frac{c_{\chi^2(n),\frac{\alpha}{2}}}{ns^2}\leq \frac{1}{\sigma^2}\leq \frac{c_{\chi^2(n),1-\frac{\alpha}{2}}}{ns^2} \right) &= 1 - \alpha \\
>> P\left( \underbrace{ \frac{ns^2}{c_{\chi^2(n),1-\frac{\alpha}{2}}} }_{ =G_{u} }\leq \sigma^2\leq \underbrace{ \frac{ns^2}{c_{\chi^2(n),\frac{\alpha}{2}}} }_{ =G_{o} } \right) &= 1 - \alpha \\
>>\end{align}$$
>
>>[!algo]- $(2)$ $X$ sei normalverteilt mit unbekanntem Erwarungswert $\mu$ ([[../Vorlesungsskript_Mathematik3.pdf#page=116|Quelle]])
>>Gegeben sei $X \sim N(\mu, \sigma)$ mit $\mu$ unbekannt und $\Theta=\sigma^2$
>>1. $\widehat{\Theta}=S^2$ mit $S^2=\frac{1}{n-1}\sum_{i=1}^n (X_{i}- \overline{X})^2$
>>2. $\widetilde{\Theta}=\frac{(n-1)S^2}{\sigma^2} \sim \chi^2(n-1)$
>>3. Ansatz für ein Konfidenzintervall:
>>$$\begin{align}
>> P\left( c_{\chi^2(n-1),\frac{\alpha}{2}}\leq \widetilde{\Theta}\leq c_{\chi^2(n-1),1-\frac{\alpha}{2}} \right) &= 1 - \alpha \\
>>\end{align}$$
>>4. Umstellen des Ansatzes
>>$$\begin{align}
>> P\left( c_{\chi^2(n-1),\frac{\alpha}{2}}\leq \frac{(n-1)s^2}{\sigma^2}\leq c_{\chi^2(n-1),1-\frac{\alpha}{2}} \right) &= 1 - \alpha \\
>> P\left( \frac{c_{\chi^2(n-1),\frac{\alpha}{2}}}{(n-1)s^2}\leq \frac{1}{\sigma^2}\leq \frac{c_{\chi^2(n-1),1-\frac{\alpha}{2}}}{(n-1)s^2} \right) &= 1 - \alpha \\
>> P\left( \frac{c_{\chi^2(n-1),\frac{\alpha}{2}}}{(n-1)s^2}\leq \frac{1}{\sigma^2}\leq \frac{c_{\chi^2(n-1),1-\frac{\alpha}{2}}}{(n-1)s^2} \right) &= 1 - \alpha \\
>> P\left( \underbrace{ \frac{(n-1)s^2}{c_{\chi^2(n-1),1-\frac{\alpha}{2}}} }_{ =G_{u} }\leq \sigma^2\leq \underbrace{ \frac{(n-1)s^2}{c_{\chi^2(n-1),\frac{\alpha}{2}}} }_{ =G_{o} } \right) &= 1 - \alpha \\
>>\end{align}$$

>[!algo]- Konfidenzintervall für einen Anteilswert ([[../Vorlesungsskript_Mathematik3.pdf#page=118|Quelle]])
>
>Sei $X \sim \text{Null-Eins}(p)$ mit bekannter geschätztem $\widehat{p}$ unbekanntem Parameter $\Theta=p$ und gegeben sei
>$$\begin{align}
> \widehat{\mu} &= \overline{x} \\
> \widehat{\sigma}^2 &= s^2 \\
>\end{align}$$
>und Approximationsbedingung für Moivre/Laplace
>$$n \cdot \widehat{p}(1-\widehat{p}) > 9$$ 
>können wir abschätzen mit
>$$\overline{X}_{n} \overset{asymp.}\sim N\left( \mu, \frac{\sigma}{\sqrt{ n }} \right)$$
>und erhalten das zweiseitige Konfidenzintervall
>$$\text{KI}=\left[ \widehat{p}-c_{N(0,1), 1-\frac{\alpha}{2}} \cdot \sqrt{ \frac{\widehat{p}(1-\widehat{p})}{n} } \quad , \quad \widehat{p}+c_{N(0,1), 1-\frac{\alpha}{2}} \cdot \sqrt{ \frac{\widehat{p}(1-\widehat{p})}{n} } \right]$$

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
>> P(9.675 \leq \mu \leq 10.325) &= 0.95 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>3. Welche Auswirkung hat die Änderung des Konfidenzintervals
>
>>[!example]- Lösung
>>Je geringer die Irrtumswahrscheinlichkeit $\alpha$ desto größer das Konfidenzinterval. Das heißt, dass wir sicherer sein wollen, dass das wahre Mittel innerhalb des Intervalls liegt. $$\tag*{$\blacktriangleleft$}$$

>[!example] Aufgabe (2)
>
>$20$ Messungen der Schaftlänge von Zylinderschrauben ergaben eine mittlere Länge von $18 \text{mm}$ und eine Standardabweichung von $28 \mu \text{m}$. Gesucht sind die Konfidenzgrenzen für die Streubreite mit $\sigma$ mit einer Irrtumswahrscheinlichkeit von $5\%$, wenn die Schaftlänge als normalverteilt angenommen werden kann.
>
>Hinweis: Gesucht ist hier ein KI für $\sigma$ (in $\mu \text{m}$) anstatt für $\sigma^2$.
>>[!example]- Lösung
>>Wir erfassen folgende Parameter
>>$$\begin{align}
>> n&=20 \\
>> \overline{x}&=18\,000 \\
>> s &= 28 \\
>> \alpha &= 0.05
>>\end{align}$$
>>Über die gegebenen Parameter können wir Verfahren $(2)$ für das Konfidenzintervall der Varianz verwenden.
>>$$\begin{align}
>> P\left( \frac{(n-1)s^2}{c_{\chi^2\left( n-1 \right),1-\frac{\alpha}{2}}} \leq \sigma^2 \leq \frac{(n-1)s^2}{c_{\chi^2\left( n-1 \right),\frac{\alpha}{2}}} \right) &= 1-\alpha \\
>> P\left( \frac{19 \cdot 28^2}{c_{\chi^2\left( 19 \right),0.975}} \leq \sigma^2 \leq \frac{19 \cdot 28^2}{c_{\chi^2\left( 19 \right),0.025}} \right) &= 1-\alpha \\
>> P\left( \frac{19 \cdot 28^2}{\underbrace{ c_{\chi^2\left( 19 \right),0.975} }_{ =32.85 }} \leq \sigma^2 \leq \frac{19 \cdot 28^2}{\underbrace{ c_{\chi^2\left( 19 \right),0.025} }_{ =8.91 }} \right) &= 1-0.05 \\
>> P\left( 453.4551 \leq \sigma^2 \leq 1671.8294\right) &= 0.95 \\
>> P\left( 21.2945 \leq \sigma \leq 40.888\right) &= 0.95 \tag*{$\blacktriangleleft$}
>>\end{align}$$ 
>

>[!example] Aufgabe (3)
>Bei der Produktion von bestimmten Bauteilen für elektronische Geräte sei $p$ die Ausschusswahrscheinlichkeit. Um Aufschluss über $p$ zu bekommen, wird eine Stichprobe von $n$ Teilen entnommen, die auf ihre Funktionsfähigkeit überprüft werden.
>
>1. Geben Sie ein Konfidenzintervall für die Ausschusswahrscheinlichkeit an zum Konfidenzniveau von $95\%$ an, wenn $69$ der $600$ überprüften BBauteile defekt sind.
>
>>[!example]- Lösung
>>Wir erfassen die folgenden Parameter
>>$$\begin{align}
>> \alpha &= 0.05 \\
>> k &= 69 \\
>> n &= 600 \\
>> \widehat{p} &= \frac{69}{600} = 0.115
>>\end{align}$$
>>
>>Wir berechnen das Konfidenzintervall über das beschriebene Verfahren
>>$$\begin{align} \\
>> \text{KI} &=\left[ \widehat{p}-c_{N(0,1), 1-\frac{\alpha}{2}} \cdot \sqrt{ \frac{\widehat{p}(1-\widehat{p})}{n} } \quad , \quad \widehat{p}+c_{N(0,1), 1-\frac{\alpha}{2}} \cdot \sqrt{ \frac{\widehat{p}(1-\widehat{p})}{n} } \right] \\
>>  &= \left[ 0.115 - \underbrace{ c_{N(0,1), 0.975} }_{ =1.96 } \cdot \sqrt{ \frac{0.115\cdot0.885}{600} } \quad, \quad 0.115 + \underbrace{ c_{N(0,1), 0.975} }_{ =1.96 } \cdot \sqrt{ \frac{0.115\cdot0.885}{600} } \right] \\
>> &= [0.0895, 0.1405] \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2.  Geben Sie die Größe der Stichprobe an, sodass zum Konfidenzniveau $95\%$ die Länge des Konfidenzintervalls $0.05$ beträgt.
>
>>[!example]- Lösung
>>Hier ist $n$ gesucht, sodass wir haben
>>$$G_{o}-G_{u}=0.05$$
>>also berechnen wir
>>$$\begin{align}
>> G_{o}-G_{u} &= 0.05 \\
>> \cancel{ 0.115 } + 1.96 \cdot \sqrt{ \frac{0.115\cdot0.885}{n}} - (\cancel{ 0.115 } - 1.96 \cdot \sqrt{ \frac{0.115\cdot0.885}{n}}) &= 0.05\\
>> 2 \cdot 1.96 \cdot \frac{0.319}{\sqrt{  n}} &= 0.05 \\
>> 1.2505 &= 0.05 \cdot \sqrt{ n } \\
>> 25.01 &= \sqrt{ n } \\
>> 625.5001 &= n \\
>> \implies n&= 626 \tag*{$\blacktriangleleft$}
>>\end{align}$$


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

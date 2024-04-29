>[!def]- Definitionen Grundlegende Begriffe stetige Zufallsgrößen
>>[!def] Definition Stetige Zufallsgröße ([[../Vorlesungsskript_Mathematik3.pdf#page=57|4.51]])
>>Eine Zufallsgröße heißt stetig, wenn es eine integrierbare Funktion
>>$$f_{X}(x) \geq 0$$
>>mit $x \in \mathbb{R}$ derar gibt, dass sich die Verteilungsfunktion $F_{X}(x)=P(X\leq x)$ für alle $x \in \mathbb{R}$ in der Form
>>$$F_{X}(x)= \int _{-\infty}^x f_{X}(t)\, dt $$
>>darstellen lässt. Die Funktion $f_{X}(x)$ wird als Dichtefunktion bezeichnet.
>
>>[!property] Eigenschaften der Dichtefunktion $f_{X}(x)$
>>1. $\int _{\infty}^\infty f_{X}(x) \, dx=1$
>>2. $f_{X}(x)\geq 0, \, \forall x \in \mathbb{R}$
>
>>[!property] Eigenschaften von Wahrscheinlichkeiten einer stetigen Zufallsgröße ([[../Vorlesungsskript_Mathematik3.pdf#page=58|Source]]) 
>>$$\begin{alignat}{2}
>>P(a \leq X \leq b)&= \int _{a}^b f_{X}(t) \, dt &&= F(b)-F(a) \\
>>P(X>b) &= 1-P(X\leq b)\\
>> &= 1-\int _{-\infty}^b f_{X}(t) \, dt &&=1- F(b) \\
>> P(X=x) &= \lim_{ h \to 0^+ }P(x\leq X \leq x+h) \\
>> &= \lim_{ h \to 0^+ }\int _{x}^{x+h}f_{X}(t) \, dt &&=0    
>>\end{alignat}$$
>
>>[!property] Weitere Eigenschaften
>>$$\begin{align}
>> P(X\leq a) &= P(X<a) = F(a) \\
>> P(X>b) &= P(X\geq b) = 1 - F(b) \\
>> P(a \leq x < b) &= P(a < X < b) \\
>> &= P(a < X \leq b) \\ &= F(b)-F(a)
>>\end{align}$$
>
>>[!def] Defintion Erwartungswert ([[../Vorlesungsskript_Mathematik3.pdf#page=59|4.54]])
>>Für eine stetige Zufallsgröße $X$ mit der Dichtefunktion $f_{X}(x)$ ist der Erwartungswert $\mu=E(X)$ von $X$ definiert als
>>$$\mu = E(X):= \int _{-\infty}^\infty f_{X}(x) \, dx $$
>>falls das uneigentliche Integral absolut konvergent ist, das heißt es gilt
>>$$\int  _{-\infty}^\infty \lvert x \rvert f_{X}(x) \, dx < \infty $$
>
>
>>[!theorem] Satz Nicht-Negetaive Zufallsgrößen/Realisierungen ([[../Vorlesungsskript_Mathematik3.pdf#page=60|4.57]])
>> Für eine nicht negative stetige Zufallsgröße gilt
>> $$\mu=E(X)= \int _{0}^\infty (1- F(x)) \, dx $$
>
>>[!def] Definition $k$-te Moment ([[../Vorlesungsskript_Mathematik3.pdf#page=60|4.59]])
>>Für eine stetige Zufallsgröße $X$ mit der Dichtefunktion $f_{X}(x)$ ist das $k$-te Moment $\alpha_{k}$ mit $k=1,2,\dots$ definiert als
>>$$\alpha_{k}=E(X^k):= \int _{-\infty}^\infty x^k f_{X}(x)\, dx $$
>
>>[!def] Definition $k$-te zentrale Moment ([[../Vorlesungsskript_Mathematik3.pdf#page=60|4.60]])
>>Für eine stetige Zufallsgröße $X$ mit der Dichtefunktion $f_{X}(x)$ mit dem Erwartungswert $\mu$ ist das $k$-te zentrale Moment $\beta_{k}$ mit $k=1,2,\dots$ definiert als
>>$$\beta_{k}=E(X-\mu)^k:= \int _{-\infty}^\infty (x- \mu)^kf_{X}(x) \, dx $$
>
>>[!def] Definition Varianz ([[../Vorlesungsskript_Mathematik3.pdf#page=60|4.61]])
>>Für eine stetige Zufallsgröße $X$ mit der Dichtefunktion $f_{X}(x)$ mit dem Erwartungswert $\mu$ ist die Varianz $\sigma^2$ definiert als zweites zentrales Moment, das heißt
>>$$\sigma^2 = D^2(X)= \int _{-\infty}^\infty (x-\mu)^2 f_{X}(x) \, dx $$

>[!def]- Definitionen Verteilungsfunktionen
>>[!def] Definition Exponentialverteilung ([[../Vorlesungsskript_Mathematik3.pdf#page=62|4.64]])
>>>[!terminology] $X$~$Exp(\lambda)$ 
>>
>>Eine stetige Zufallsgröße unterliegt einer Exponentialverteilung mit dem Parameter $\lambda>0$, wenn sie die Dichtefunktion
>>$$f_{X}(x)= \begin{cases}
>> \lambda e^{-\lambda x} & x > 0 \\
>> 0 & x \leq 0
>>\end{cases}$$
>>besitzt
>
>>[!def] Definition Verteilungsfunktion exponentialverteilter Zufallsgröße ([[../Vorlesungsskript_Mathematik3.pdf#page=62|4.65]])
>>Die Verteilungsfunktion der exponentialverteilten Zufallsgröße ist definiert als
>>$$F_{X}(x) = P(X\leq x)= \begin{cases}
>> 1-e^{-\lambda x} & x>0 \\
>> 0 & x \leq 0
>>\end{cases}$$
>
>>[!property]- Eigenschaft Erwartungswert und Varianz der Exponentialverteilung ([[../Vorlesungsskript_Mathematik3.pdf#page=62|Source]])
>>$$\begin{align}
>> E(X) &= \int _{0}^\infty x \lambda e^{-\lambda x} \, dx  \\
>>     &= \lim_{ b \to \infty }  \int _{0}^b x \lambda e^{-\lambda x} \, dx \\ \\
>>     &= \frac{1}{\lambda} \\
>> D(X) &= E(X^2)- E(X)^2  \\
>> &=\int _{0}^\infty x^2\lambda^{-\lambda x}  \, dx  - \left( \frac{1}{\lambda} \right)^2  \\
>> &= \frac{2}{\lambda^2}-\frac{1}{\lambda^2} \\
>> &= \frac{1}{\lambda^2}
>>\end{align}$$
>
>>[!def] Definition Dichtefunktion der Normalverteilung ([[../Vorlesungsskript_Mathematik3.pdf#page=64|4.69]])
>>>[!terminology] $X$ ~ $N(\mu, \sigma)$
>>
>>Eine stetige Zufallsgröße $X$ unterliegt einer Normalverteilung mit den Paramtern $\mu$ und $\sigma>0$, wenn sie die Dichtefunktion
>>$$f_{X}(t)= \frac{1}{\sigma \sqrt{ 2\pi }}\exp\left( -\frac{(t-\mu)^2}{2\sigma^2} \right)$$
>>mit $t \in \mathbb{R}$ beträgt.
>>>[!note]
>>>- $\mu$ - Zentrum der Verteilung $f_{X}$
>>>- $\sigma$- Breite der Verteilung $f_{X}$
>
>>[!def] Definition Verteilungsfunktion der Normalverteilung ([[../Vorlesungsskript_Mathematik3.pdf#page=64|4.70]])
>>Die Verteilungsfunktion einer normalverteilten Zufallsgröße ist definiert als
>>$$F_{X}(x)= \frac{1}{\sigma \sqrt{ 2\pi }}\int _{-\infty}^x \exp\left( -\frac{(t-\mu)^2}{2\sigma^2} \right)\, dt $$
>
>>[!property] Eigenschaft Erwartungswert und Varianz der Normalverteilung ([[../Vorlesungsskript_Mathematik3.pdf#page=64|Source]])
>> $$\begin{align}
>> E(X)&=\frac{1}{\sigma \sqrt{ 2\pi }}\int _{-\infty}^\infty t \exp\left( -\frac{(t-\mu)^2}{2\sigma^2} \right) \, dt  \\
>> & = \mu \\
>>D(X)&=\frac{1}{\sigma \sqrt{ 2\pi }} \int _{\infty}^\infty(t-\mu)^2 \exp\left( -\frac{(t-\mu)^2}{2\sigma^2} \right)\, dt  \\
>> &= \sigma^2
>>\end{align}$$
>
>>[!def] Definition Standardisierte Normalverteilung ([[../Vorlesungsskript_Mathematik3.pdf#page=64|4.71]])
>>>[!terminology] $X$ ~ $N(0,1)$
>>
>>Die standardisierte Normalverteilung (Standard Normalverteilung) besitzt den Erwartungswert $\mu=0$ und die Standardabweichung $\sigma=1$ und die Dichtefunktion $\forall t \in \mathbb{R}$
>>$$\varphi(t)= \frac{1}{\sqrt{ 2\pi }}\exp\left( -\frac{t^2}{2} \right)$$
>>und die Verteilungsfunktion $\forall t \in \mathbb{R}$
>>$$\phi(x)=\frac{1}{2\pi}\int _{-\infty}^x \exp\left( -\frac{t^2}{2} \right) \, dt $$
>
>>[!property] Eigenschaft Berechnung für $X$ ~ $N(\mu, \sigma)$
>>1. $P(X \leq t)$
>>$$\begin{align}
>> P(X \leq t) &= P\left( \frac{X-\mu}{\sigma}\leq \frac{t-\mu}{\sigma} \right) \\
>> &= P\left( Z \leq \frac{t-\mu}{\sigma} \right)\\
>> &= \sigma\left( \frac{t-\mu}{\sigma} \right)
>>\end{align}$$
>>2.$P(a \leq X \leq b)$
>>$$\begin{align}
>> P(a \leq X \leq b) &= P\left( \frac{a-\mu}{\sigma} \leq \frac{X-\mu}{\sigma} \leq \frac{b-\mu}{\sigma} \right) \\
>> &= P\left(\frac{a-\mu}{\sigma} \leq Z \leq \frac{b-\mu}{\sigma} \right)\\
>> &= \phi \left( \frac{b-\mu}{\sigma} \right) - \phi\left( \frac{a-\mu}{\sigma} \right)
>>\end{align}$$
>
>>[!Theorem] Satz Mittelwert Symmetrische Intervalle der Normalverteilung ([[../Vorlesungsskript_Mathematik3.pdf#page=67|4.76]])
>>Es sei $X$~$N(\mu, \sigma)$ verteilt und $k \in \mathbb{R}^+$. Die Zufallsgröße $Y$ sei $N(0,1)$ verteilt, dann gilt
>>$$\begin{align}
>> P(\lvert X-\mu \rvert < k\sigma ) &= P(\mu-k\sigma \leq X \leq \mu + k \sigma) \\
>> &= 2 \phi(k)-1
>>\end{align}$$

>[!def]- Definitionen Quantile einer Zufallsgröße ([[../Vorlesungsskript_Mathematik3.pdf#page=65|Source]])
>>[!def] Definition $p$-tes Quantil ($p$-Fraktil, Quantil der Ordnung $p$)([[../Vorlesungsskript_Mathematik3.pdf#page=69|4.8]])
>>Als $p$-tes Quantil einer Zufallsgröße $X$ bezeichnet man den Funktionswert $c_{p}$ für den gilt
>>$$F(c_{p})\geq p \text{ und } \lim_{ t \to c_{p}^- }F(t) \leq p $$
>
>>[!property] Besondere Quantile
>>- Median: $c_{0.5}$
>>- Unteres Quantil: $c_{0.25}$
>>- Oberes Quantil: $c_{0.75}$


>[!example] Aufgabe (1)
>Die Lebensdauer $T$ eines Bauteils (in Wochen) sei exponentialverteilt, mit einer erwarteten Lebensdauer von 15 Wochen. Es ist also $T ~ Exp(\lambda)$ mit $\lambda = \frac{1}{15}$. 
>
>>[!example] Gegeben
>>$T$ ~ Lebensdauer in Wochen
>> $\lambda= \frac{1}{15}$
>> $P(X \leq x)= 1-\exp\left( -\frac{1}{\lambda}x \right)$
>
>Bestimmen Sie die Wahrscheinlichkeit, dass das Bauteil...
>1. ... in den ersten 10 Wochen ausfällt.
>
>>[!example]- Lösung
>>$$\begin{align}
>> P(X \leq 10) &= 1-\exp\left( -\frac{1}{15} \cdot 10 \right) \\
>> &= 1-\exp\left( -\frac{2}{3} \right) \\
>> &= 0.486582881 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. ... mindestens 20 Wochen hält.
>
>>[!example]- Lösung
>>$$\begin{align}
>> P(X \geq 20) &= 1- P(X< 20) \\
>> &= 1- P(X\leq 20) \\
>> &= 1- \left( 1- \exp\left( -\frac{1}{15} \cdot 20 \right) \right) \\
>> &= \exp\left( -\frac{4}{3} \right) \\
>> &= 0.2635971381 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>3. ... weniger lang als die erwartete Lebensdauer hält.
>
>>[!example]- Lösung
>>$$\begin{align}
>> P(X < 15) &= P(X\leq 15) \\
>>  &= 1-\exp\left( -\frac{1}{15}15 \right) \\
>>  &=1 - \frac{1}{e} \\
>> &= 0.6321205588 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>4. Bestimmen Sie den Median
>
>>[!example]- Lösung
>>Wir berechnen für $c_{0.5}$
>>$$\begin{alignat}{2}
>> F(c_{0.5}) &= 0.5 \\
>>1- \exp\left( -\frac{1}{15}c_{0.5} \right) &=0.5 \\
>> \exp\left( -\frac{1}{15}c_{0.5} \right) &= 0.5 \qquad&&\Big\vert \ln(\,.) \\
>> -\frac{1}{15}c_{0.5} &= \ln(0.5) \qquad&&\Big\vert \cdot (-15) \\
>> c_{0.5} &= -15 \ln(0.5) \\
>> &= 10.3972077084 \tag*{$\blacktriangleleft$}
>>\end{alignat}$$

>[!example] Aufgabe (2)
> Die Zeit zwischen 2 nacheinander in einer Telefonzentrale ankommenden Gespräche kann als exponentialverteilt angesehen werden. Sie betrage im Mittel 10 Sekunden. Wie groß ist die Wahrscheinlichkeit, dass zwischen 2 aufeinanderfolgender Gespräche mehr als 5 Minuten vergehen?
>>[!example]- Lösung
>>Wir haben 
>>- $X$ ~ Pause zwischen zwei Telefonaten in Sekunden 
>>- $X$ ~ $Exp(\lambda)$
>>- $5 \text{ min } \equiv 300 \text{ sek}$
>>- $\lambda = \frac{1}{10} \iff \frac{1}{\lambda}=10 = E(X)$
>>
>>Wir berechnen demnach
>>$$\begin{align}
>> P(X > 300) &= 1- P(X \leq 300) \\ 
>> &= 1-  \left( 1-\exp\left( -\frac{1}{10} \cdot 300\right) \right) \\
>> &= \exp(-30) \\
>> &\approx 9.4 \cdot 10^{-14} \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (3) 
>Die Zufallsgröße $X$ sei normalverteilt mit $\mu=1$ und $\sigma=2$. Man ermittle
>
>>[!example] Gegeben
>>$X$ ~ $N(\mu=1, \sigma=2)$ 
>
>1. $P(X<2)$
>
>>[!example]- Lösung
>>$$\begin{align}
>> P(X<2) &= P(X\leq 2) \\
>>\end{align}$$
>>Wir berechnen das Argument für $\phi$ für die Berechnung der Normalverteilung.
>>$$\frac{t-\mu}{\sigma}=\frac{2-1}{2}= \frac{1}{2}$$
>>Aus der Tabelle lesen wir
>>$$P(X\leq 2)= 0.69146 \tag*{$\blacktriangleleft$}$$
>
>2. $P(0 \leq X < 2)$
>
>>[!example]- Lösung
>>Wir verwenden 
>>$$P(a \leq X \leq b) = \phi \left( \frac{b-\mu}{\sigma} \right) - \phi\left( \frac{a-\mu}{\sigma} \right)$$
>>wobei $P(0 \leq X < 2)=P(0 \leq X \leq 2)$
>>$$\begin{align}
>> \frac{a-\mu}{\sigma}&=-\frac{1}{2} \\
>> \frac{b-\mu}{\sigma}&=\frac{1}{2}
>>\end{align}$$
>>Wir erhalten
>>$$\begin{align}
>> P(a \leq X \leq b) &= 0.69146 - (1-0.69146) \\
>> &= 0.38292
>>\end{align}$$
>
>3. und bestimme $\alpha \in \mathbb{R}$, sodass $P(X\geq \alpha)=0.0548$
>
>>[!example]- Lösung
>>$$\begin{align}
>> P(X \geq \alpha)&=  0.0548  \\
>> 1-P(X\leq \alpha)&= 0.0548 \\
>> P(X\leq \alpha)&= 0.9452
>>\end{align}$$
>>Wir haben 
>>$$\begin{align}
>>\frac{\alpha-\mu}{\sigma}&=\frac{\alpha-1}{2}
>>\end{align}$$
>>Für die Standardnormalverteilung haben wir
>>$$P(X\leq 1.6)= 0.9452$$
>>Daher lösen wir
>>$$\begin{alignat}{2}
>>1.6 &= \frac{\alpha-1}{2} \qquad&&\Big\vert \cdot 2 \\
>>3.2 &= \alpha-1  \qquad&&\Big\vert +1 \\
>>4.2 &= \alpha  \tag*{$\blacktriangleleft$}
>>\end{alignat}$$

>[!example] Aufgabe (4)
>Die Äpfel einer speziell gezüchteten Sorte haben ein mittleres Gewicht von 160g. Die Standardabweichung liegt bei 50g. Das Gewicht der Äpfel unterliege der Normalverteilung.
>
>>[!example] Gegeben
>>$$\begin{align}
>> \mu&=160 \\
>> \sigma &= 50
>>\end{align}$$
>
>
>Wie groß ist die Wahrscheinlichkeit, dass ein Apfel ...
>1. ... weniger als 100g wiegt?
>
>>[!example]- Lösung
>> Gesucht ist
>> $$P(X \leq 100)$$
>> Wir berechnen das Argument für $\phi$ für die Berechnung der Normalverteilung.
>>$$\begin{align}
>> \frac{x-\mu}{\sigma}&=\frac{100-160}{50} \\
>> &= \frac{-60}{50} \\
>> &= -\frac{6}{5} \\
>> &= -1.2
>>\end{align}$$
>>$$\begin{align}
>> P(X \leq 100)&= P(Z \leq -1.2) \\
>> &= 1 - P(Z \leq 1.2)  \\
>> &= 1- 0.88493 \\
>> &= 0.11507 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. ... bis 20g vom mittleren Gewicht abweicht.
>
>>[!example]- Lösung
>>Gesucht ist
>>$$\begin{align}
>> P(160-20 \leq X \leq160+20) 
>> \end{align}$$
>> Damit wir Satz 4.76 anwenden können müssen wir die Identität
>> $$k\cdot \sigma=20$$
>> lösen. Wir haben $\sigma=50$ und erhalten
>> $$\begin{alignat}{2}
>> 50k&=20 \qquad&&\Big\vert :50 \\
>> k &= \frac{2}{5}
>>\end{alignat}$$
>>Wir verwenden die Lösungsformel
>>$$\begin{align}
>> 2\phi(k)-1&= 2\phi\left( \frac{2}{5} \right)-1 \\
>> &=2\phi\left( 0.4 \right)-1 \\
>> &=2\cdot0.65542	-1 \\ 
>> &= 0.31084 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>>
>
>3. Welches mittlere Gewicht müssten die Äpfel haben, damit 60% der Äpfel mehr als 150g wiegen?
>
>>[!example]- Lösung
>>Gesucht ist $\mu$, sodass 
>>$$P(X\geq 150)=0.6$$
>>Weiterhin gegeben ist 
>>$$\sigma = 50$$
>>Zunächst bringen wir unsere Wahrscheinlichkeitsfunktion in Standardform
>>$$\begin{align}
>> P(X\geq 150) &= 1-P(X\leq 150) 
>>\end{align}$$
>>Wir suchen daher jetzt ein $\mu$, sodass die Identität ergibt
>>$$1-P(X\leq 150)=0.6 \iff P(X\leq 150)=0.4$$
>>Also berechnen wir mit $Z$ ~ $N(0,1)$
>>$$\begin{align}
>> P(X \leq 150) &= 0.4 \\
>> P\left( Z\leq \frac{\mu-150}{50} \right) &= 0.4 \\
>> \phi\left(\frac{\mu-150}{50} \right) &= 0.4 \\
>> \phi^{-1}\left(  0.4\right) &= \frac{150-\mu}{50} \\
>> -\phi^{-1}\left(1-  0.4\right) &= \frac{150-\mu}{50} \tag{Symmetrie Eigenschaft} \\
>> -\phi^{-1}\left(0.6\right) &= \frac{150-\mu}{50} \\
>> -0.25 &=\frac{150-\mu}{50} \qquad&&\Big\vert \cdot 50;\; + \mu\\
>> -12.5+\mu &=150 \qquad&&\Big\vert +12.5\\ 
>>\mu &= 162.5  \tag*{$\blacktriangleleft$}
>>\end{align}$$
>>>[!pic] Symmetrie Eigenschaft
>>>![[symmetrie_normalverteilung.png|center|500]]

>[!example] Aufgabe (5)
> Bei einer Klausur mit einer maximalen Punktzahl von 100 Punkten seien die Resultate (näherungsweise) normalverteilt. Die mittlere Punktezahl liegt bei 60 und die Standardabweichung bei 10.
>>[!example] Gegeben
>>$$\begin{align}
>> \mu&=60 \\
>> \sigma &= 10 \\
>> X &\sim N(60,10)
>>\end{align}$$
>> 
> 1. Bestimmen Sie den Anteil der Studenten, die durchgefallen sind, wenn zum Bestehen mindestens 50 Punkte erforderlich sind.
> 
>>[!example]- Lösung
>>$$\begin{align}
>> P(X<50)&= P(X\leq 50) \\
>> &= \phi\left( \frac{50-60}{10} \right) \\
>> &= \phi(-1) \\
>> &= 1-\phi(1) \\
>> &= 1-0.84134 \\
>> &= 0.15866 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. Die Note 2.0 wird vergeben, wenn 80 bis 95 Punkte in der Klausur erreicht wurden. Bestimmen Sie den Anteil der Studenten, die diese Note erhalten.
>
>>[!example]- Lösung
>>$$\begin{align}
>> P(80 \leq X \leq 95) &= F(95)-F(80) \\
>> &=P(X\leq 95)-P(X\leq 80) \\
>> &= \phi\left( \frac{95-60}{10} \right) - \phi\left( \frac{80-60}{10} \right)\\
>> &= \phi\left( 3.5 \right) - \phi\left( 2.0 \right)\\
>> &= 0.99977 - 0.97725\\ 
>> &= 0.02252 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>3. Auf welchen Wert muss die Mindestpunktezahl zum Bestehen festgelegt werden, wenn nur 10% der Studenten durchfallen sollen?
>
>>[!example]- Lösung
>>Gesucht ist $x$ für
>>$$P(X\leq x)=0.1$$
>>Wir erhalten für $Z \sim N(0,1)$
>>$$\begin{align}
>> P(X\leq x) &= 0.1 \\
>> P\left( Z\leq \frac{x-\mu}{\sigma} \right) &= 0.1 \\
>> \phi\left( \frac{x-60}{10} \right) &= 0.1 \\
>> \phi^{-1}(0.1) &= \frac{x-60}{10} \\
>> -\phi(-1)(1-0.1) &= \frac{x-60}{10} \tag{Symmetrie Eigenschaft} \\
>> -\phi(-1)(0.9) &= \frac{x-60}{10} \\
>> -\phi(-1)(0.9) &= \frac{x-60}{10} \\
>> -1.28 &= \frac{x-60}{10} \qquad&&\Big\vert \cdot 10 \\
>> -12.8 &= x-60 \qquad&&\Big\vert +60 \\
>> 47.2 &= x-60 \tag*{$\blacktriangleleft$}\\
>>\end{align}$$
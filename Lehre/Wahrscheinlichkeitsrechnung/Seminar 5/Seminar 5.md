>[!def] Definitionen
>>[!theorem] Satz Ungleichung von Tschebyscheff (Satz [[../Vorlesungsskript_Mathematik3.pdf#page=74|5.1]])
>>Es sei $X$ eine Zufallsgröße mit $E(X)= \mu$ und $D^2(X)= \sigma < \infty$. Dann gilt
>>$$P(\lvert X-\mu \rvert \geq \varepsilon ) \leq \frac{\sigma^2}{\varepsilon^2} \tag*{$\forall \varepsilon>0$}$$
>>bzw.
>>$$P(\lvert X-\mu \rvert < \varepsilon ) \geq 1 - \frac{\sigma^2}{\varepsilon^2} \tag*{$\forall \varepsilon>0$}$$
>
>>[!theorem] Satz Schwaches Gesetz der Großen Zahl (Satz [[../Vorlesungsskript_Mathematik3.pdf#page=67|5.10]])
>>Es sei $(X_{i})$ mit $i=1,2,\dots,n$ eine Folge unabhängig, identisch verteilte Zufallsgrößen mit dem Erwartungswert $E(X_{i})=\mu < \infty$ und $$\overline{X}_{n}=\frac{1}{n}\sum^{n}_{i=1}X_{i}$$
>>Dann gilt
>>$$\lim_{ n \to \infty } P(\lvert \overline{X}_{n}-\mu \rvert  \geq \varepsilon) = 0$$
>>für ein beliebiges $\varepsilon>0$ und $\overline{X}_{n} \overset{p}{\to} \mu$, beziehungsweise
>>$$\lim_{ n \to \infty } P(\lvert \overline{X}_{n}-\mu \rvert  < \varepsilon) = 1$$
>>für ein beliebiges $\varepsilon>0$ und $\overline{X}_{n} \overset{p}{\to} \mu$
>>>[!proof]- Beweis
>>>Wir definieren zunächst
>>>$$S_{n}=X_{1}+X_{2}+ \dots + X_{n}$$
>>>Wir wollen Tschebyscheff's Ungleichung verwenden, dazu benotigen wird das arithmetische Mittel und die Varianz der Folge von Zufallsvariablen  $\overline{S}_{n}, \text{Var}(\overline{S}_{n})$. Wir kennzeichnen das arithmetische Mittel der identischen Verteilung $X$ als $\mu_{X}$ and analog die Varianz mit $\sigma^2_{X}$. Wir bestimmen also
>>> $$\begin{align}
>>> E(S_{n}) = \overline{S}_{n} &= \frac{X_{1}+ X_{2}+ \dots+ X_{n}}{n} \\
>>> &= \frac{n\mu_{X}}{n} \tag{identisch verteilt} \\
>>> &= \mu_{X} \\
>>> \text{Var}(\overline{S}_{n})&= \text{Var}\left( \frac{1}{n}(X_{1}+ X_{2}+ \dots+ X_{n}) \right) \\
>>> &=\frac{1}{n^2} \text{Var}(X_{1}+ X_{2}+ \dots+ X_{n}) \tag{Var quadratisch} \\
>>> &= \frac{1}{n^2} \underbrace{ (\text{Var}(X_{1})+ \text{Var}(X_{2}) + \dots + \text{Var}(X_{n})) }_{ n-\text{mal} } \\
>>> &= \frac{n\sigma_{X}^2}{n^2} \\
>>> &= \frac{\sigma_{X}^2}{n}
>>>\end{align}$$
>>>Damit können wir Tschebyscheff's Ungleichung verwenden
>>>$$\begin{align}
>>> P(\lvert X-\mu \rvert \geq \varepsilon ) \leq  \frac{\text{Var}(\overline{S}_{n})}{\varepsilon^2} = \frac{\sigma^2_{X}}{n \varepsilon^2} \tag{Standarditisiert}
>>>\end{align}$$
>>>Mit $n \to \infty$ erhalten wir
>>>$$\begin{align}
>>> \lim_{ n \to \infty } P(\lvert X-\mu \rvert \geq \varepsilon ) = 0 \tag*{$\square$}
>>>\end{align}$$
>
>>[!theorem] Satz Globaler Grenzwertsatz nach Lindeberg/Levy (Satz [[../Vorlesungsskript_Mathematik3.pdf#page=81|5.19]])
>>Es sei $(X_{i})$ mit $i=1,2,\dots$ eine Folge unabhängig, identisch verteilte Zufallsgrößen mit $E(X_{i})= \mu$ und endlicher Varianz, das heißt $D^2(X_{i})= \sigma^2 < \infty$ Für die (zentrierten und normierten) Summen
>>$$\begin{align}
>> Z_{n} &= \frac{\sum_{i=1}^n (X_{i}-\mu)}{\sqrt{ \sum_{i=1}^n \sigma^2 }}  \\
>> &= \frac{\sum_{i=1}^nX_{i}-n\mu}{\sqrt{ n }\sigma} \tag*{$n=1,2,\dots$}
>>\end{align}$$
>>mit den Verteilungsfunktionen $F_{Z_{n}}(x)=P(Z_{n}\leq x)$ gilt dann
>>$$\lim_{ n \to \infty } F_{Z_{n}}(x)= \phi(x)=\frac{1}{\sqrt{ 2\pi }}\int _{-\infty}^x e^{-t^2/2}\, dt $$
>
>>[!remark] Bemerkung 5.20
>>Unter den Voraussetungen des Satzes gilt
>>$$\begin{align}
>> \sum_{i=1}^n X_{i} &\overset{asymp}\sim N(n\mu, \sqrt{ n }\sigma^2) \\
>>  \sum_{i=1}^n X_{i} &\overset{asymp}\sim N\left( \mu, \frac{\sigma^2}{n} \right)\\
>>\end{align}$$
>
>>[!theorem] Satz Globaler Grenzwertsatz nach Moivre/Laplace (Satz [[../Vorlesungsskript_Mathematik3.pdf#page=83|5.22]])
>>Es sei $(X_{i})$ mit $i=1,2,\dots$ eine Folge unabhängig, identisch Null-Eins-verteilter Zufallsgrößen, das heißt 
>>$$\begin{align}
>> P(X_{i}=1)&=p \\
>> P(X_{i}=0)&=1-p
>>\end{align}$$
>>mit $0<p<1$. Es sei weiter $Y_{n}=\sum_{i=1}^n X_{i}$ dann ist $Y_{n}$ binomialverteilt mit $E(Y_{n})=np$ und $D^2(Y_{n})=np(1-p)$ Für die (zentrierten und normierten Summen
>>$$Z_{n}= \frac{Y_{n}-np}{\sqrt{ np(1-p) }} \tag*{$n=1,2,\dots$}$$
>>mit den Verteilungsfunktionen
>>$$F_{Z_{n}}(x)=P(Z_{n}\leq x)$$
>>Dann gilt
>>$$\lim_{ n \to \infty } F_{Z_{n}}(x)=\phi(x)=\frac{1}{\sqrt{ 2\pi }}\int _{-\infty}^x e^{-t^2/2} \, dt $$
>
>>[!remark] Bemerkung 5.23
>>Unter der Faustregel $np(1-p)>9$ können wir
>>$$\begin{align}
>> \sum_{i=1}^n X_{i} &\overset{asymp}\sim N\left( np,  np(1-p)  \right) \\
>>\end{align}$$
>
>>[!remark] Bemerkung 5.24
>>Wenn $n$ nicht sehr groß ist, kann eine Stetigkeitskorrektur von $0.5$ verwendet werden
>> $$P(x_{1} \leq Y_{n} \leq x_{2}) \approx \phi\left( \frac{x_{2}\mathbf{+0.5}-np}{\sqrt{ np(1-p) }} \right)-\phi\left( \frac{x_{1}\mathbf{-0.5}-np}{\sqrt{ np(1-p) }} \right)$$
>
>>[!theorem] Satz Lokaler Grenzwertsatz von Moivre/Laplace (Satz [[../Vorlesungsskript_Mathematik3.pdf#page=84|5.22]])
>> Es sei $(X_{i})$ mit $i=1,2,\dots$ eine Folge unabhängig, identisch Null-Eins-verteilter Zufallsgrößen, das heißt 
>>$$\begin{align}
>> P(X_{i}=1)&=p \\
>> P(X_{i}=0)&=1-p
>>\end{align}$$
>>mit $0<p<1$. Es sei weiter $Y_{n}=\sum_{i=1}^n X_{i}$ dann ist $Y_{n}$ binomialverteilt mit $E(Y_{n})=np$ und $D^2(Y_{n})=np(1-p)$ Für die (zentrierten und normierten Summen
>>$$Z_{n}= \frac{Y_{n}-np}{\sqrt{ np(1-p) }} \tag*{$n=1,2,\dots$}$$
>>mit den Verteilungsfunktionen
>>$$F_{Z_{n}}(x)=P(Z_{n}\leq x)$$
>>und
>>$$\Delta x = \frac{(k+1)-np}{\sqrt{ np(1-p) }}- \frac{k-np}{\sqrt{ np(1-p) }}=\frac{1}{\sqrt{ np(1-p) }}$$
>>dann gilt
>>$$\lim_{ n \to \infty } \frac{p_{k}^{(n)}}{\varphi\left( \frac{k-np}{\sqrt{ np(1-p) }} \cdot \Delta x\right)}=1$$
>>Dabei ist $$p_{k}^{(n)} = P(Y_{n}=k)=\binom{n}{k}p^k (1-p)^{n-k}$$ 
>>mit $k=0,\dots,n$ und $n \in \mathbb{N}$ die Einzelwahrscheinlichkeit der Binomialverteilung und $$\varphi(x)=\frac{1}{\sqrt{ 2\pi }}e^{-x^2/2}$$ die Dichtefunktion der Standard-Normalverteilung.
>


>[!example] Aufgabe (1)
>Eine Zufallsvariable $X$ habe den Erwartungswert $E(X)=10$ und die Varianz $D^2(X)=4$
>>[!example] Gegeben
>>$$\begin{align}
>> E(X) = \mu &= 10 \\
>> D^2(X)= \sigma^2 &= 4 \\
>> \sigma &= 2 \tag{Def 4.23 + 4.27}
>>\end{align}$$
>1. Welche Aussage kann über die Wahrscheinlichkeit des Ereignisses $(7 < X < 13)$ gemacht werden.
>
>>[!example]- Lösung
>>Nach der Tschebyscheff'schen Ungleichung können wir die Wahrscheinlichkeit anhand der gegebenen Parameter einschränken, da wir im gegebenen Ereignis um $3$ vom Erwarungswert $\mu=10$ abweichen, also haben wir für $\varepsilon=3$
>>$$\begin{align}
>> P(\lvert X-10 \rvert < 3 ) &\geq 1 - \frac{2^2}{3^2}  \\
>> &\geq 1- \frac{4}{9} \\
>> &\geq \frac{5}{9} \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. Welche Aussage kann über die Wahrscheinlichkeit des Ereignisses $(7 < X < 13)$ gemacht werden, wenn $X$ normalverteilt ist.
>
>>[!example]- Lösung
>> $X \sim N(10,2)$
>> $Z \sim N(0,1)$
>> $$\begin{align}
>> P(7 < X < 13) &= P(X\leq 13)-P(X\leq 7) \\
>> &= P\left( Z \leq \frac{13-10}{2} \right) - P\left( Z \leq \frac{7-10}{2} \right) \\
>> &= \phi\left( \frac{13-10}{2} \right) - \phi\left( \frac{7-10}{2} \right) \\
>> &= \phi\left( \frac{3}{2} \right) - \phi\left( -\frac{3}{2} \right) \\
>> &= 2\underbrace{ \phi\left( \frac{3}{2} \right) }_{ = 0,93319} - 1 \\
>> &= 0.86638 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (2)
>$(X_{i})$ mit $i=1,2,\dots$ sei eine Folge unabhängiger, identisch verteilter Zufallsgrößen mit den Einzelwahrscheinlichkeiten $P(X_{i}=k)=0.1$ mit $k=0,1,\dots,9$ und $i=1,2,\dots$. Gesucht ist die Wahrscheinlichkeit, dass das arithmetische Mittel $\overline{X}_{50}$ größer als $5$ ist.
>>[!example]- Lösung
>>Wir identifizieren die folgenden Parameter
>>$$\begin{align}
>> n&=50 \\
>> \varepsilon &= 5
>>\end{align}$$
>>und betonen, dass die Zufallsgrößen identisch verteilt sind. 
>>
>>Gesucht ist die Größe 
>>$$P(\overline{X}_{50}\geq 5 )$$
>>Daher können wir Erwartungswert und Varianz entsprechend bestimmen mit $p_{i}=0.1$
>>$$\begin{align}
>> E(X_{i}) &= \sum_{i=0}^{9} i \cdot p_{i} \\ 
>> &= \frac{1}{10} \sum_{i=0}^{9} i \\
>> &= 4.5
>>\end{align}$$
>>Die Varianz ist zu berechnen mit
>>$$\begin{align}
>> D^2(X_{i}) &= \frac{1}{10}\sum_{i=0}^{9}(x_{i}-\mu)^2 \\
>> &= 8.25
>>\end{align}$$
>>Also
>>$$\sigma = \sqrt{ 8.25 } = 2.872281323$$
>>Wir bemerken
>>$$\overline{E}_{50}= \mu = 4.5$$
>>und wissen, dass unter des **globalen Grenzwertsatzes**
>>$$\overline{X}_{n} \overset{asymp}{\sim}N\left( \mu, \frac{\sigma}{\sqrt{ n }} \right)$$
>>Wir berechnen nun 
>>$$\begin{align}
>> P(\overline{E}_{50} \geq 5) &= 1-P(\overline{E}_{50} \leq 5) \\
>> &= 1 - P\left( Z \leq \frac{5-4.5}{\frac{\sqrt{ 8.25 }}{\sqrt{ 50 }}} \right) \\
>> &= 1 - \phi\left( \frac{0.5}{0.40620192} \right) \\
>> &= 1- \phi(1.23091491) \\
>> &= 1-0.89065 \\
>> &= 0.1093 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (3)
> Bei einer Maschine sind $2\%$ der erzeugten Produkte unbrauchbar. Die Produkte werden in Kisten zu je 1000 Stück verpackt. Die Zufallsgröße $X$ beschreibt die zufällige Anzahl unbrauchbarer Artikel. Wie groß ist die Wahrscheinlichkeit, dass eine Kiste mehr als 30 defekte Stücke enthält.
>>[!example]- Lösung
>>Wir **erfassen** folgende gegebene Größen.
>>$$\begin{align}
>> p &= 0.02 \tag{Wkt. Unbrauchbar} \\
>> n &= 1000
>>\end{align}$$
>>**Gesucht** ist die Größe 
>>$$P(X > 30)$$
>>Wir erkennen, dass $X$ **diskret** verteilt ist. Außerdem überlegen wir welche Verteilungsfunktion am ehesten geeignet ist, um diese Aufgabe zu lösen. Naheliegend sind **die Binomial- und Poissonverteilung**. Um uns entsprechend zu entscheiden, prüfen wir nach unserer **Faustregel**. Wir verwenden die Poissonverteilung, wenn die folgende Relation wahr ist
>>$$\begin{align}
>> n \cdot p < 10 \implies \underbrace{ 1000 \cdot 0.02 }_{ =20 } \not<10
>>\end{align}$$
>>Also verwenden wir die Binomialverteilung und erhalten
>>$$\begin{align}
>> P(X>30)&= 1-P(X \leq 30) \\
>> &= 1 - \sum_{k=0}^{30}\binom{1000}{k}0.02^{k}0.8^{1000-k}
>>\end{align}$$
>>Wir stellen fest, dass die Werte für unsere Methoden zu groß werden. Zunächst prüfen wir die Faustregel
>>$$\begin{align}
>> np(1-p)&>9 \\
>> 1000 \cdot 0.02 \cdot 0.08 &> 9  \\
>> 19.6 &> 9 \tag*{$\checkmark$}
>>\end{align}$$
>>Wir behelfen uns mit den erfassten Grenzwertsätzen, im Speziellen mit dem **globalen Grenzwertsatz nach Moivre/Laplace**. Wir wissen, dass
>>$$\begin{align}
>> \sum_{i=1}^n X_{i} &\overset{asymp}\sim N\left( np,  \sqrt{ np(1-p) } \right)
>>\end{align}$$
Daher berechnen wir für $N(\tilde{\mu}, \tilde{\sigma})$
>>$$\begin{align}
>> \tilde{\mu} &= n  p \\
>> &= 1000 \cdot 0.02 \\
>> &= 20 \\
>> \tilde{\sigma} &= \sqrt{ n  p (1-p)} \\
>> &= \sqrt{ 19.6 } \\
>> &= 4.42719
>>\end{align}$$
>>Wir arbeiten jetzt mit der geschätzten Normalverteilung für die Zufallsvariable $Y \sim N(20, 4.42719)$. Wir standardisieren über $Z$ dementsprechend
>>$$\begin{align}
>> P(X>30) &= 1 - P(X\leq 30)  \\
>> &= 1 - P(Y \leq 30) \\ 
>> \end{align}
>> $$
>> **Ohne Stetigkeitskorrektur**
>> $$\begin{align}
>> \phantom{P(X>30)}&= 1 - P\left( Z \leq \frac{30-20}{4.42719} \right) \\
>> &= 1- \phi(2.25877) \\
>> &= 1 - 0.9878 \\
>> &= 0.0122 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>>**Mit Stetigkeitskorrektur** nach Bemerkung 5.24
>>$$\begin{align}
>>\phantom{P(X>30)}&= 1 - P\left( Z \leq \frac{30+0.5-20}{4.42719} \right) \\
>> &= 1- \phi(2.37171) \\
>> &= 1- 0.9911 \\
>> &= 0.0089 \tag*{$\blacktriangleleft$}
>>\end{align}$$

>[!example] Aufgabe (4*)
> Die Wahrscheinlichkeit des Eintretens eines Ereignisses $A$ bei jedem von $n$ unabhängigen Versuchen ist gleich $0.75$. Gesucht ist die Wahrscheinlichkeit, dass die relative Häufigkeit von $A$ um weniger als $0.01$ von $0.75$ abweicht, wenn ...
>>[!example] Gegeben
>>Gegeben ist 
>>$$\begin{align}
>> P(A) &= 0.75 \\
>>\end{align}$$
>>Wir definieren dazu folgende Zufallsvariable $X \sim \text{Binom}(10\,000, 0.75)$ wobei $X$ angibt wie häufig $A$ bei $n$ unabhängigen Versuchen eintritt. Wir suchen die Abweichung vom Mittelwert um einen Anteil von $0.01$ der Gesamtversuche.
> 1. ... $10\,000$ Versuche durchgeführt werden
>
>>[!example]- Lösung
>>Da $n$ sehr hoch ist, bleibt zu vermuten, dass die Werte schlecht berechenbar. Wir prüfen anhand der Faustregel 
>>$$\begin{align}
>> np(1-p)&>9  \\
>> 10\,000 \cdot 0.75  \cdot 0.25 &> 9 \\
>> 1875 &> 9 \tag*{$\checkmark$}
>>\end{align}$$
>>weshalb wir über die Normalverteilung $Y \sim N(\tilde\mu, \tilde\sigma)$ die Wahrscheinlichkeit abschätzen
>>$$\begin{align}
>> \tilde{\mu} &= n \cdot p \\
>> &= 10\,000 \cdot 0.75 \\
>> &= 7500 \\
>> \tilde{\sigma}&=\sqrt{ np(1-p) } \\
>> &= \sqrt{ 10\,000 \cdot 0.75 \cdot 0.25 } \\
>> &= \sqrt{ 1875 } \\
>> &= 43.30127
>>\end{align}$$
>>Wir suchen die Abweichung vom Mittelwert um $0.01$ der Gesamtversuche, also
>>$$10\,000\cdot 0.01=100$$
>>also
>>$$\begin{align}
>> P(7400 \leq Y \leq 7600) &= P\left( \frac{7400-7500}{43.30127} \leq Z \leq \frac{7600-7500}{43.30127}\right) \\
>> &= P\left( -2.3094 \leq Z \leq 2.3094\right) \\
>> &= 2\phi(2.3094) - 1 \\
>> &= 2 \cdot 0.9896 - 1 \\
>> &= 0.9792 \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>2. ... $100$ Versuche durchgeführt werden
>
>>[!example]- Lösung
>>Wir führen kurz kommentiert dieselben Rechnungen durch
>> **Faustregel**
>> $$\begin{align}
>> np(1-p)&>9  \\
>> 100 \cdot 0.75  \cdot 0.25 &> 9 \\
>> 18.75 &> 9 \tag*{$\checkmark$}
>>\end{align}$$
>>**Normalverteilungsabschätzung**
>>$$\begin{align}
>> \tilde{\mu} &= n \cdot p \\
>> &= 75 \\
>> \tilde{\sigma}&=\sqrt{ np(1-p) } \\
>> &= \sqrt{ 18.75 } \\
>> &= 4.33013
>>\end{align}$$
>>**Abweichung** um $1$, also
>>$$\begin{align}
>> P(74 \leq Y \leq 76) &= P\left( \frac{74-75}{4.33013} \leq Z \leq \frac{76-75}{4.33013}\right) \\
>> &= P\left( -2.3094 \leq Z \leq 2.3094\right) \\
>> &= 2\phi(0.23094) - 1 \\
>> &= 2 \cdot 0.5910 - 1 \\
>> &= 0.182 \tag*{$\blacktriangleleft$}
>>\end{align}$$
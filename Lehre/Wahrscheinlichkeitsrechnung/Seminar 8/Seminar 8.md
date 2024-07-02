>[!terminology] 
> - $H_{0}$ - Nullhypothese
> - $H_{1}$ - Alternativhypothese (Negation von $H_{0}$)

>[!def]- Definitionen Parametertests für einfache Stichproben ([[../Vorlesungsskript_Mathematik3.pdf#page=120|Quelle]])
>
>>[!terminology] 
>> - $\Gamma$ - Paramaterbereich
>> - $\Theta$ - Unbekannter Paramater
>> - $\Gamma_{0}$ - Paramaterbereich für Nullhypothese $H_{0}$ -> $H_{0} \in \Gamma_{0}$
>> - $\Gamma_{1}$ - Paramaterbereich für Alternativhypothese $H_{1}$ -> $H_{1} \in \Gamma_{1}$
>> -> $\Gamma_{0} \cap \Gamma_{1} = \emptyset$ und $\Gamma_{0} \cup \Gamma_{1} = \Gamma$
>
>>[!def] Definition 7.19
>> Linksseitiger Test
>> $$H_{0}: \Theta \geq \Theta_{0} \text{ und } H_{1}: \Theta < \Theta_{0}$$
>> das heißt
>> $$\Gamma_{0} = [\Theta_{0}, \infty) \text{ und } \Gamma_{1}=(-\infty, \Theta_{0})$$
>
>>[!def] Definition 7.20
>> Rechtsseitiger Test
>> $$H_{0}: \Theta \leq \Theta_{0} \text{ und } H_{1}: \Theta > \Theta_{0}$$
>> das heißt
>> $$\Gamma_{0} = (-\infty, \Theta_{0}] \text{ und } \Gamma_{1}=(\Theta_{0}, \infty]$$
>
>>[!def] Definition 7.21
>>Zweiseitiger Test
>>$$H_{0}: \Theta= \Theta_{0} \text{ und } H_{1}: \Theta \neq \Theta_{0}$$
>>das heißt
>>$$\Gamma_{0} = \{ \Theta_{0} \} \text{ und } \Gamma_{1}=\mathbb{R}\setminus \{ \Theta_{0} \}$$

>[!algo] Verfahren Erwartungswert einfache Stichproben 
>
>>[!algo]- Zweiseitiger Einstichproben-Gauß-Test (Varianz Bekannt, normalverteilt) ([[../Vorlesungsskript_Mathematik3.pdf#page=123|Quelle]])
>><u> Behauptung:</u> $\mu=\mu_{0}$
>>1. **Hypothesen:** $$H_{0}: \mu=\mu_{0} \text{ und } H_{1}: \mu \neq \mu_{0}$$
>>2. **Signifikanzniveau:** $$\alpha \to \frac{\alpha}{2} \tag{links und rechts}$$
>>3. **Testfunktion:** $$\begin{align} \\
>> &T=\overline{X}=\frac{1}{n}\sum_{i=1}^n X_{i} \sim N\left( \mu_{0}, \frac{\sigma}{\sqrt{ n }} \right) \tag{Normalverteilt}\\
>> \to \;& T= \frac{\overline{X}-\mu_{0}}{\sigma}\sqrt{ n } \sim N(0,1) \tag{Standardisiert}
>>\end{align}$$
>>mit Realisierung $t=\frac{\overline{t}-\mu_{0}}{\sigma}\sqrt{ n }$
>>4. **Kritischer Bereich:**
>>$$K=\Big( -\infty, c_{N(0,1), \frac{\alpha}{2}}\Big) \cup \Big( c_{N(0,1), -\frac{\alpha}{2}}, \infty\Big)$$
>>5. **Testentscheidung**
>> - $t\in K \implies$ Ablehnung von $H_{0}$ und Annahme von $H_{1}$ mit Irrtumswahrscheinlichkeit $\alpha$ 
>> - $t \not\in K \implies$ keine Ablehnung von $H_{0}$
>
>>[!algo]- Zweiseitiger Einstichproben-$t$-Test (Varianz Unbekannt, normalverteilt) ([[../Vorlesungsskript_Mathematik3.pdf#page=125|Quelle]])
>><u> Behauptung:</u> $\mu=\mu_{0}$
>>1. **Hypothesen:** $$H_{0}: \mu=\mu_{0} \text{ und } H_{1}: \mu \neq \mu_{0}$$
>>2. **Signifikanzniveau:** $$\alpha \to \frac{\alpha}{2} \tag{links und rechts}$$
>>3. **Testfunktion:** $$\begin{align} \\
>> &S^2= \frac{1}{n-1}\sum_{i=1}^n (\overline{X}-X_{i})^2 \tag{Empirische Varianz}\\
>> &T=\frac{\overline{X}-\mu_{0}}{S}\sqrt{ n } \sim t(n-1) \tag{$t$-verteilt}\\
>>\end{align}$$
>>mit Realisierung $t=\frac{\overline{x}-\mu_{0}}{s}\sqrt{ n }$
>>1. **Kritischer Bereich:**
>>$$K=\Big( -\infty, -c_{t(n-1), 1-\frac{\alpha}{2}}\Big) \cup \Big( c_{t(n-1), 1-\frac{\alpha}{2}}, \infty\Big)$$
>>5. **Testentscheidung**
>> - $t\in K \implies$ Ablehnung von $H_{0}$ und Annahme von $H_{1}$ mit Irrtumswahrscheinlichkeit $\alpha$ 
>> - $t \not\in K \implies$ keine Ablehnung von $H_{0}$
>
>>[!algo]- Einseitiger Einstichproben-Gauß-Test (Varianz Bekannt, normalverteilt) ([[../Vorlesungsskript_Mathematik3.pdf#page=124|Quelle]])
>><u> Behauptung:</u> $\mu \geq\mu_{0}$ linksseitig, bzw. $\mu \leq_{0}$ rechtsseitig
>>1. **Hypothesen:** $$\begin{align}
>> H_{0}: \mu \geq \mu_{0} &\text{ und } H_{1}: \mu < \mu_{0} \tag{linksseitig} \\
>> H_{0}: \mu \leq \mu_{0} &\text{ und } H_{1}: \mu > \mu_{0} \tag{rechtsseitig}
>>\end{align}$$
>>2. **Signifikanzniveau:** $$\alpha  \tag{links oder rechts}$$
>>3. **Testfunktion:** $$\begin{align} \\
>> &T=\overline{X}=\frac{1}{n}\sum_{i=1}^n X_{i} \sim N\left( \mu_{0}, \frac{\sigma}{\sqrt{ n }} \right) \tag{Normalverteilt}\\
>> \to \;& T= \frac{\overline{X}-\mu_{0}}{\sigma}\sqrt{ n } \sim N(0,1) \tag{Standardisiert}
>>\end{align}$$
>>mit Realisierung $t=\frac{\overline{t}-\mu_{0}}{\sigma}\sqrt{ n }$
>>4. **Kritischer Bereich:**
>>$$\begin{align}
>>  K&=\Big(-\infty, c_{N(0,1), \alpha}\Big) \tag{Linksseitig} \\
>>  K&=\Big(c_{N(0,1),1- \alpha}, \infty\Big) \tag{Rechtsseitig} \\
>> \end{align}$$
>>5. **Testentscheidung**
>> - $t\in K \implies$ Ablehnung von $H_{0}$ und Annahme von $H_{1}$ mit Irrtumswahrscheinlichkeit $\alpha$ 
>> - $t \not\in K \implies$ keine Ablehnung von $H_{0}$
>
>>[!algo]- Einseitiger Einstichproben-$t$-Test (Varianz Unbekannt, normalverteilt) ([[../Vorlesungsskript_Mathematik3.pdf#page=125|Quelle]])
>><u> Behauptung:</u> $\mu \geq\mu_{0}$ linksseitig, bzw. $\mu \leq_{0}$ rechtsseitig
>>1. **Hypothesen:** $$H_{0}: \mu=\mu_{0} \text{ und } H_{1}: \mu \neq \mu_{0}$$
>>2. **Signifikanzniveau:** $$\alpha \tag{links oder rechts}$$
>>3. **Testfunktion:** $$\begin{align} \\
>> &S^2= \frac{1}{n-1}\sum_{i=1}^n (\overline{X}-X_{i})^2 \tag{Empirische Varianz}\\
>> &T=\frac{\overline{X}-\mu_{0}}{S}\sqrt{ n } \sim t(n-1) \tag{$t$-verteilt}\\
>>\end{align}$$
>>mit Realisierung $t=\frac{\overline{x}-\mu_{0}}{s}\sqrt{ n }$
>>1. **Kritischer Bereich:**
>>$$\begin{align}
>> H_{0}: \mu \geq \mu_{0} \text{ und } H_{1}: \mu < \mu_{0} &\implies K=(-\infty, c_{t(n-1), \alpha}) \tag{linksseitig} \\
>> H_{0}: \mu \leq \mu_{0} \text{ und } H_{1}: \mu > \mu_{0} &\implies K=(c_{t(n-1), 1-\alpha}, \infty) \tag{rechtsseitig}
>>\end{align}$$
>>5. **Testentscheidung**
>> - $t\in K \implies$ Ablehnung von $H_{0}$ und Annahme von $H_{1}$ mit Irrtumswahrscheinlichkeit $\alpha$ 
>> - $t \not\in K \implies$ keine Ablehnung von $H_{0}$




>[!algo]- Verfahren Zweiseitiger/Einseitiger $\chi^2$-Streuungstest([[../Vorlesungsskript_Mathematik3.pdf#page=126|Quelle]])
><u> Behauptung:</u> $$\begin{align}
> \sigma^2&=\sigma_{0}^2$ \tag{zweiseitig} \\
> \sigma^2 &\geq \sigma_{0}^2 \tag{linksseitig} \\
> \sigma^2 &\leq \sigma_{0}^2 \tag{rechtsseitig}
>\end{align}$$
>1. **Hypothesen:** $$\begin{align}
> H_{0}:\sigma^2=\sigma_{0}^2 &\text{ und } H_{1}: \sigma^2\neq\sigma_{0}^2 \tag{zweiseitig} \\
> H_{0}: \sigma^2 \geq \sigma^2_{0} &\text{ und } H_{1}: \sigma^2 < \sigma^2_{0} \tag{linksseitig} \\
> H_{0}: \sigma^2 \leq \sigma^2_{0} &\text{ und } H_{1}: \sigma^2 > \sigma^2_{0}  \tag{rechtsseitig}
>\end{align}$$
>2. **Signifikanzniveau:** $$\begin{align}
> \alpha &\to \frac{\alpha}{2} \tag{links und rechts} \\
> &\;\;\alpha \tag{ links oder rechts}
>\end{align}$$
>3. **Testfunktion:** $$\begin{align} \\
> &T=\frac{(n-1)S^2}{\sigma^2_{0}} \sim \chi^2(n-1) \tag{$t$-verteilt}\\
>\end{align}$$
>mit Realisierung $t=\frac{(n-1)s^2}{\sigma^2_{0}}$
>1. **Kritischer Bereich:**
>$$\begin{align}
> K &= \Big( 0, c_{\chi^2(n-1), \frac{\alpha}{2}} \Big) \cup \Big(c_{\chi^2(n-1), 1-\frac{\alpha}{2}}, \infty\Big) \tag{Beidseitig} \\
> K&=\Big(0, c_{\chi^2(n-1), \alpha}\Big)\tag{linksseitig}\\
>  K&=\Big(c_{\chi^2(n-1),1- \alpha}, \infty\Big)\tag{rechtsseitig}
>\end{align}$$
>5. **Testentscheidung**
> - $t\in K \implies$ Ablehnung von $H_{0}$ und Annahme von $H_{1}$ mit Irrtumswahrscheinlichkeit $\alpha$ 
> - $t \not\in K \implies$ keine Ablehnung von $H_{0}$

>[!algo]- Verfahren Zweiseitiger/Einseitiger Einstichproben-Gaußtest für den Anteilswert ([[../Vorlesungsskript_Mathematik3.pdf#page=126|Quelle]])
><u> Behauptung:</u> $$\begin{align}
> p&=p_{0} \tag{zweiseitig} \\
> p &\geq p_{0} \tag{linksseitig} \\
> p &\leq p_{0} \tag{rechtsseitig}
>\end{align}$$
>1. **Hypothesen:** $$\begin{align}
> H_{0}:p=p_{0} \text{ und } H_{1}: p\neq p_{0} \tag{zweiseitig} \\
> H_{0}:p\geq p_{0} \text{ und } H_{1}: p< p_{0} \tag{linksseitig} \\
> H_{0}:p\leq p_{0} \text{ und } H_{1}: p> p_{0} \tag{rechtsseitig} \\
>\end{align}$$
>2. **Signifikanzniveau:** $$\begin{align}
> \alpha &\to \frac{\alpha}{2} \tag{links und rechts} \\
> &\;\;\alpha \tag{ links oder rechts}
>\end{align}$$
>3. **Testfunktion:** Über die Null-Eins Verteilung$$\begin{align} \\
> &T=\frac{\widehat{P}-p_{0}}{\sqrt{ p_{0}(1-p_{0}) }}\sqrt{ n } \;\;\overset{n\to \infty}\sim \;\;N(0,1)\tag{asympt. normal verteilt}\\
>\end{align}$$
>mit Realisierung $t=\frac{\widehat{p}-p_{0}}{\sqrt{ p_{0}(1-p_{0}) }}\sqrt{ n }$
>1. **Kritischer Bereich:**
>$$\begin{align}
> K &= \Big( -\infty, c_{N(0,1), \frac{\alpha}{2}}\Big) \cup \Big( c_{N(0,1), 1-\frac{\alpha}{2}}, \infty\Big) \tag{Beidseitig} \\
>  K&=\Big(-\infty, c_{N(0,1), \alpha}\Big) \tag{Linksseitig} \\
>  K&=\Big(c_{N(0,1),1- \alpha}, \infty\Big) \tag{Rechtsseitig}
>\end{align}$$
>5. **Testentscheidung**
> - $t\in K \implies$ Ablehnung von $H_{0}$ und Annahme von $H_{1}$ mit Irrtumswahrscheinlichkeit $\alpha$ 
> - $t \not\in K \implies$ keine Ablehnung von $H_{0}$


>[!example] Aufgabe (1)
>Es wird die Hypothese aufgestellt, Intelligenzquotienten seien normalverteilt mit einem Erwartungswert $100$. Diese Hypothese soll bei einem Signifikanzniveau von $10$% zweiseitig überprüft werden. Zu diesem Zweck wird eine Stichprobe vom Umfang $1000$ erhoben, in der sich ein mittlerer IQ von $101$ und eine empirische Standardabweichung von $15$ ergibt. Wie lautet die Testentscheidung?
>>[!example]- Lösung
>>Gegeben ist
>>$$\begin{align}
>> \mu_{0} &=100   \tag{Nullhypothese}\\
>> \alpha&=0.1 \tag{Irrtumswahrscheinlichkeit}\\
>> n&=1000 \tag{Stichprobenumfang}\\
>> \overline{x} &= 101 \tag{Mittelwert}\\
>> s &= 15 \tag{empirische Standardabweichung}
>>\end{align}$$
>>**Wir testen den Erwartungswert beidseitig über eine einzelne Stichprobe mit unbekannter Varianz**. Wir verwenden dasdementsprechende Verfahren mit der $t$-Verteilung.
>>1. $H_{0}: \mu=100$ und $H_{1}: \mu \neq 100$
>>2. $\alpha = 0.1$ -> $\frac{\alpha}{2}=0.05$ kritischer Bereich links und rechts
>>3. $T\sim t(999)$ $$\begin{align}
>> t &= \frac{101-100}{15}\sqrt{ 1000 } \\
>> &=2.108185
>>\end{align}$$
>>4. $\,$
>>$$\begin{align}
>> K &= \Big( -\infty, -c_{t(n-1), 1-\frac{\alpha}{2}}\Big) \cup \Big( c_{t(n-1), 1-\frac{\alpha}{2}}, \infty\Big) \\
>> &= \Big( -\infty, -c_{t(999), 0.95}\Big) \cup \Big( c_{t(999), 0.95}, \infty\Big) \\
>> &= \Big( -\infty, - 1.646\Big) \cup \Big(  1.646, \infty\Big)
>>\end{align}$$
>>
>>5. $t \in K$ => Ablehnung $H_{0}$, Annahme $H_{1}$ mit $\alpha=0.01$ Irrtumswahrscheinlichkeit $$\tag*{$\blacktriangleleft$}$$

>[!example] Aufgabe (2)
>In einer Zufallsstichprobe vom Umfang $n=100$ ergibt sich ein durchschnittliches Alter von $44$ Jahren, bei einer empirischen Standardabweichung von $s=12$ Jahren. Kann mit diesem Befund bei einem einseitigen Signifikanzniveau von $5$% die Hypothese bestätigt werden, dass das Durchschnittsalter in der Grundgesamtheit bei $42.5$ Jahren liegt?
>>[!example]- Lösung
>> Gegeben ist
>> $$\begin{align}
>> n&=100 \tag{Stichprobenumfang} \\
>> \overline{x} &= 44 \tag{Arithmetische Mittel}\\
>> s &= 12 \tag{Empirische Standardabweichung} \\
>> \alpha &= 0.05 \tag{Einseitiges Signifikanzniveau}\\
>> \mu_{0} &= 42.5 \tag{Hypothese}
>>\end{align}$$
>>**Wir testen den Erwartungswert einseitig über eine einzelne Stichprobe mit unbekannter Varianz**. Wir testen rechtsseitig.
>> 1. $H_{0}: \mu \leq42.5$ und $H_{1}: \mu > 42.5$
>> 2. $\alpha=0.05$
>> 3. $T\sim t(99)$ $$\begin{align}
>> t &= \frac{44-42.5}{12}\sqrt{ 100 } \\
>> &=1.25
>>\end{align}$$
>>4. $\,$
>>$$\begin{align}
>> K &= \Big(  c_{t(n-1), \alpha}, \infty\Big) \\
>> &= \Big(c_{t(99), 0.95} ,\infty\Big) \\
>> &= \Big( 1.66, \infty\Big) 
>>\end{align}$$
>>5. $t \not\in K \implies$ $H_{0}$ wird nicht abgelehnt. $$\tag*{$\blacktriangleleft$}$$

>[!example] Aufgabe (3)
>Es wird behauptet, dass die Streuung der deutschen Einkommen mit einer Standardabweichung von $440€$ bemessen werden kann. In einer Zufallsstichprobe vom Umfang $n=200$ ergibt sich eine empirische Standardabweichung von $500€$. Wie lautet bei einem einseitigen Signifikanzniveau von $5$% die Testentscheidung?
>
>>[!example]- Lösung
>>Gegeben ist
>>$$\begin{align}
>> \sigma_{0}^2 &= 440^2 \tag{Hypothese}\\
>> n &= 200 \tag{Stichprobenumfang} \\
>> s &= 500 \tag{Empirische Standardabweichung} \\
>> \alpha &= 0.05 \tag{Einseitiges Signifikanzniveau}
>>\end{align}$$
>>
>> **Wir testen die Varianz einseitig über eine einzelne Stichprobe**. Wir testen rechtsseitig
>> 1. $H_{0}: \sigma_{0}^2 \leq 440^2$ und $H_{1}: \sigma_{0}^2 > 440^2$
>> 2. $\alpha = 0.05$
>> 3. $T \sim \chi^2(199)$ $$\begin{align}
>> t&=\frac{(n-1)s^2}{\sigma^2_{0}} \\
>> &=\frac{199\cdot500^2}{440^2} \\
>> &= 256.97
>>\end{align}$$
>>4. $\,$ $$\begin{align}
>>K&=\Big(c_{\chi^2(n-1),1- \alpha}, \infty\Big)\\
>>&=\Big(c_{\chi^2(199),0.95}, \infty\Big) \\
>>&=\Big(232.912, \infty\Big) \\
>>\end{align}$$
>>5. $t \in K \implies$ die Hypothese wird abgelehnt.

>[!example] Aufgabe (4)
>Bei $200$ Würfen mit einem Würfel erhielt man $k$-mal die Augenzahl $6$. Prüfen Sie mit dem Signifikanzniveau $\alpha=0.05$, ob es sich dabei um einen "unverfälschten" Würfel handelt, wenn
>1. $k=30$ ist.
>
>>[!example]- Lösung
>> Gegeben sind
>> $$\begin{align}
>> n &= 200 \tag{Stichprobenumfang} \\
>> \widehat{p} &= \frac{30}{200} = 0.15 \tag{Empirische Wahrscheinlichkeit} \\
>> p_{0} &= \frac{1}{6} = 0.1666 \tag{Null Hypothese} \\
>> \alpha &= 0.05 \tag{Fehler}
>>\end{align}$$
>>
>> Wir verwenden den zweiseitigen Einstichproben-Gaußtest für den Antweilswert
>> 1.  Hypothesen $$H_{0}:\widehat{p}=p_{0} \text{ und } H_{1}: \widehat{p}\neq p_{0}$$
>> 2. $\alpha\to \frac{\alpha}{2}=0.025$
>> 3. $T \overset{n \to \infty}\sim N(0,1)$ with
>>  $$\begin{align}
>> t&=\frac{\widehat{p}-p_{0}}{\sqrt{ p_{0}(1-p_{0}) }}\sqrt{ n } \\
>> &=\frac{0.15-0.1666}{\sqrt{ 0.1666\cdot 0.8334 }}\sqrt{ 200 } \\
>> &=-0.60725
>>\end{align}$$
>> 4. $\,$ $$\begin{align}
>> K &= \Big( -\infty, c_{N(0,1), \frac{\alpha}{2}}\Big) \cup \Big( c_{N(0,1), 1-\frac{\alpha}{2}}, \infty\Big)  \\
>>  &= \Big( -\infty, c_{N(0,1), 0.025}\Big) \cup \Big( c_{N(0,1), 1-0.025}, \infty\Big)  \\
>>  &= \Big( -\infty, -c_{N(0,1), 1-0.025}\Big) \cup \Big( c_{N(0,1), 1-0.025}, \infty\Big)  \\
>>  &= \Big( -\infty, -c_{N(0,1), 0.975}\Big) \cup \Big( c_{N(0,1), 0.975}, \infty\Big)  \\ 
>>  &= \Big( -\infty, -1.96\Big) \cup \Big( 1.96, \infty\Big)  \\ 
>> \end{align}$$
>>
>>5. $t \not\in K \implies$ Der Würfel wird als unverfälscht angenommen $$\tag*{$\blacktriangleleft$}$$
>
>
>2. $k=22$ ist.
>
>>[!example]- Lösung
>> Gegeben sind
>> $$\begin{align}
>> n &= 200 \tag{Stichprobenumfang} \\
>> \widehat{p} &= \frac{22}{200} = 0.11 \tag{Empirische Wahrscheinlichkeit} \\
>> p_{0} &= \frac{1}{6} = 0.1666 \tag{Null Hypothese} \\
>> \alpha &= 0.05 \tag{Fehler}
>>\end{align}$$
>>
>> Wir verwenden den zweiseitigen Einstichproben-Gaußtest für den Antweilswert
>> 1.  Hypothesen $$H_{0}:\widehat{p}=p_{0} \text{ und } H_{1}: \widehat{p}\neq p_{0}$$
>> 2. $\alpha\to \frac{\alpha}{2}=0.025$
>> 3. $T \overset{n \to \infty}\sim N(0,1)$ with
>>  $$\begin{align}
>> t&=\frac{\widehat{p}-p_{0}}{\sqrt{ p_{0}(1-p_{0}) }}\sqrt{ n } \\
>> &=\frac{0.11-0.1666}{\sqrt{ 0.1666\cdot 0.8334 }}\sqrt{ 200 } \\
>> &=-2.14816
>>\end{align}$$
>> 4. Wie in Teilaufgabe (1) $$\begin{align}
>> K &= \Big( -\infty, c_{N(0,1), \frac{\alpha}{2}}\Big) \cup \Big( c_{N(0,1), 1-\frac{\alpha}{2}}, \infty\Big)  \\
>>  &= \Big( -\infty, -c_{N(0,1), 0.975}\Big) \cup \Big( c_{N(0,1), 0.975}, \infty\Big)  \\ 
>>  &= \Big( -\infty, -1.96\Big) \cup \Big( 1.96, \infty\Big)  \\ 
>> \end{align}$$
>>
>>5. $t \in K \implies$ Der Würfel wird als verfälscht angenommen $$\tag*{$\blacktriangleleft$}$$
>
>>[!note] Hinweis: Bei einem unverfälschten Würfel tritt die Augenzahl $6$ mit $p_{0}=\frac{1}{6}$ auf.
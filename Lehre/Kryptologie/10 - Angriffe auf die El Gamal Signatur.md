## 10.1 Mathematische Grundlagen

>[!remark]- Motivation: Lineare Kongruenzen
>Um einen der kommenden Angriffe richtig verstehen zu können, benötigen wir ein Verständnis darüber *lineare Kongruenzen* lösen zu können. Diese sind von der Form für $a,b,x,n \in \mathbb{Z}$ mit $n \neq 0$
>$$ax \equiv b \;\;(\text{mod } n)$$
>wobei $x$ die gesuchte Größe ist. Dabei suchen wir vor allem $x \in \mathbb{Z}$ die inkongruent bezüglich modulo $n$ sind, bzw. dass verschiedene [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^638cd1|Restklassen]] gesucht werden.

>[!theorem] Satz Lineare Diophantinische Gleichungen ([[../../PDFs/burton2010.pdf#page=46|Quelle]])
> Die **lineare Diophantinische Gleichung** mit $a,b,x,y \in \mathbb{Z}$
> $$ax +by = c$$
> hat eine Lösung genau dann, wenn
> $$d \;|\; c \text{ mit } d=\text{ggT}(a,b)$$
> Wenn $x_{0},y_{0}$ eine mögliche Lösung für die Gleichung ist, dann sind alle Lösungen beschrieben mit
> $$\begin{align}
> x &= x_{0}+\left( \frac{b}{d} \right)t\\
> y &= y_{0}+\left( \frac{a}{d} \right)t\\
>\end{align}$$
>
>>[!proof] Beweis


>[!theorem] Satz Lösungen für Lineare Kongruenzen ([[../../PDFs/burton2010.pdf#page=88|Quelle]])
> Die **lineare Kongruenz**
> $$ax \equiv b \;\;(\text{mod } n)$$
> hat eine Lösung genau dann, wenn
> $$d \;|\; b \text{ mit } d=\text{ggT}(a,n)$$
>>[!proof] Beweis
>>

## 10.2 Angriffsverfahren auf die El Gamal Signatur

>[!theorem] Selbe $k$-Angriff 
>
>>[!warning] Voraussetzung
>>Der Parameter $k$ wurde nicht wie in der [[9 - El Gamal's Kryptosystem#^13979e|El Gamal Signatur]] beschrieben zufällig gewählt und stattdessen wird dasselbe $k$ für verschiedene Nachrichten verwendet.
>
>>[!algo] Verfahren
>>Gegeben sind die Signaturen
>>- $(r,s_{1})$ für $m_{1}$ mit $$s_{1}=k^{-1}(m_{1}-Ar) \text{ mod }p-1$$
>>- $(r,s_{2})$ für $m_{2}$ mit $$s_{2}=k^{-1}(m_{2}-Ar) \text{ mod }p-1$$
>>
>>Wir multiplizieren beide $s_{i}$ mit $k$ und erhalten
>>$$\begin{align}
>> ks_{1} &\equiv k^{-1}(m_{1}-Ar) \;\;(\text{mod } p-1) \tag{1}\\ 
>> ks_{2} &\equiv k^{-1}(m_{2}-Ar) \;\;(\text{mod } p-1)  \tag{2}
>>\end{align}$$
>>
>>Wir ziehen nun Kongruenz $(2)$ von $(1)$ ab und erhalten
>> $$\begin{align}
>> k(s_{1}-s_{2}) \equiv m_{1}-m_{2} \;\;(\text{mod } p-1)
>>\end{align}$$


>[!theorem]
>
>>[!warning] Voraussetzung
>
>>[!algo] Verfahren
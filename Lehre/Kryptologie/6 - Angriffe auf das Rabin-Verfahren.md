>[!theorem] Gleiche Nachricht und Unterschiedliche Moduli Angriff
>
>>[!warning] Voraussetzung
>>Eine Nachricht $m$ wird mit zwei verschiedenen, teilerfremden öffentlichen Schlüsseln $n_{1},n_{2}$ verschlüsselt und an zwei Empfänger versendet.
>
>>[!algo] Verfahren
>>Wir haben die Chiffren
>>$$\begin{align}
>> c_{1} &= m^2 \text{ mod }n_{1}\\
>> c_{2} &= m^2 \text{ mod }n_{2}
>>\end{align}$$
>>Dies ergibt ein modulares Gleichungssystem, welches mit dem [[4 - Angriffe auf RSA#^ca7b4b|chinesischen Restsatz]] lösbar ist, also
>>$$x = m^2 = \Big(\big[n_{2}^{-1}\big]_{n_{1}}n_{2}c_{1}+\big[n_{1}^{-1}\big]_{n_{2}}n_{1}c_{2}\Big) \text{ mod } (n_{1}n_{2})$$
>>Aufgrund 
>>$$m<n_{1} \land m < n_{2} \implies m^2 < n_{1}n_{2}$$
>>können wir einfach die gewöhnliche Quadratwurzel ziehen, um $m$ zu erhalten
>
>>[!remark] Diskussion: Warum würde es nicht genügen die einfache Quadratwurzel zu ziehen, wenn die Prämisse $m<n_{1} \land m<n_{2}$ nicht wahr wäre?
>
>>[!remark] Kontrollfrage: Warum müssen $n_{1}, n_{2}$ teilerfremd sein?

>[!theorem] Redundante Nachrichten Angriff
>
>>[!warning] Voraussetzung
>> Zwei der vier Klartextkandidaten $m_{1},m_{2},m_{3},m_{4}$ sind bekannt.
>
>>[!algo] Verfahren
>>Seien $m_{2},m_{4}$ die [[5 - Rabin Verfahren#^eb3c6e|Klartextkandidaten]]. Die Lösungsformel charakterisiert diese als
>>$$\begin{align}
>> m_{2} &\equiv \big[q\big]^{-1}_{p} \cdot q \cdot c_{p} - \big[p\big]_{q}^{-1}\cdot p \cdot c_{q} &&\;\;(\text{mod } n) \\
>> m_{4} &\equiv -\big[q\big]^{-1}_{p} \cdot q \cdot c_{p} - \big[p\big]_{q}^{-1}\cdot p \cdot c_{q} &&\;\;(\text{mod } n)
>>\end{align}$$
>>Ziehen wir $m_{4}$ von $m_{2}$ ab, erhalten wir
>>$$m_{2}-m_{4} = 2\big[q\big]^{-1}_{p} \cdot q \cdot c_{p}$$
>>Diese Identität können wir nutzen, um den $\text{ggT}$ mit $n$ zu bestimmen
>>$$\text{ggT}(m_{2}-m_{4},n) = \text{ggT}(2\big[q\big]^{-1}_{p} \cdot q \cdot c_{p}\;,\; p \cdot q) = q$$
>>Da $q$ der größte gemeinsame Teiler ist, lässt sich nun $p$ einfach bestimmen
>>$$p = \frac{n}{q}$$
>
>>[!remark] Kontrollfrage: Warum genügt es $p,q$ zu finden, dass der Angriff erfolgreich ist?

^a8d780

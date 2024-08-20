<!-- Eventuell irgendwann hier Euler's Criterion einfügen?-->
## 5.1 Mathematische Grundlagen

>[!theorem] Satz Modulare Quadratwurzel (Sonderfall)
> Sei $a \in \mathbb{Z}_{p}$ und $p$ mit $p \equiv 3 \;\;(\text{mod } 4)$. Wir definieren die modulare Quadratzahl
> $$b \equiv a^2 \;\;(\text{mod } p)$$
>Dann kann die modulare Quadratwurzel gelöst werden mit
>$$b^{\frac{p+1}{4}} \equiv \pm a \;\;(\text{mod } p)$$
>>[!proof]- Beweis
>>Unter Verwendung der oben definierten Variablen, setzen wir ein und zeigen direkt
>>$$\begin{align}
>> b^{\frac{p+1}{4}} &\equiv \left(a^{2}\right)^{\frac{p+1}{4}} &&\;\;(\text{mod } p) \\
>>  &\equiv a^{2 \cdot \frac{p+1}{4}} &&\;\;(\text{mod } p) \\
>>  &\equiv a^{\frac{p+1}{2}} &&\;\;(\text{mod } p) \\
>>  &\equiv a^{\frac{p-1+2}{2}} &&\;\;(\text{mod } p) \\
>>  &\equiv a^{\frac{p-1}{2}}a^{\frac{2}{2}} &&\;\;(\text{mod } p) \\
>>  &\equiv \underbrace{ \left( a^{\frac{1}{2}} \right)^{p-1} }_{ \equiv 1 \;\;(\text{mod } p) } a &&\;\;(\text{mod } p) \tag{Kleiner Satz Fermat} \\
>> &\equiv a &&\;\;(\text{mod } p) \tag*{$\square$}
>>\end{align}$$
>
>>[!remark]- Bemerkung zu der Forderung $p \equiv 3 \;\;(\text{mod } 4)$
>>Aufgrund dieser Forderung wissen wir aufgrund der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^638cd1|Restklassen]], dass
>>$$\exists k \in \mathbb{Z}: p=\underbrace{ 4k +3 }_{ \equiv 3 \;\;(\text{mod } 4) }$$
>>Damit garantieren wir, dass der Exponent in $b^{\frac{p+1}{4}}$ eine ganze Zahl bleibt, da das stets eine Forderung ist bei den [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^ef0786|Operationen]] auf $\mathbb{Z}$. Wir sehen das an
>>$$\begin{align}
>> b^{\frac{p+1}{4}} = b^{\frac{4k+3+1}{4}} = b^{\frac{4(k+1)}{4}} = b^{k+1}
>>\end{align}$$

^d2662c

## 5.2 Rabin Verschlüsselungsverfahren

>[!algo] Kryptografisches Verfahren: Rabin Verfahren (1979)
>>[!schlüsselerzeugung] 
>> Wähle zwei große Primzahlen $p,q$ mit
>> $$p,q \equiv 3 \;\;(\text{mod } 4)$$
>> sodass der **private Schlüssel** $(p,q)$ ist. Der **öffentliche Schlüssel** $(n)$ lässt sich berechnen als
>> $$n = p \cdot q$$
>
>>[!verschlüsselung] 
>> <u>Verschlüsselung</u>:
>> $$c = m^2 \text{ mod }n$$
>> <u>Entschlüsselung</u>:
>> 
>> Die Lösung von
>> $$c=m^2 \text{ mod }n$$
>> nach $m$
>> 
>>>[!verschlüsselung] Nach $m$ lösen
>>>Die Lösung nach $m$ ist nicht so offensichtlich, wie es auf den ersten Blick scheinen mag. Die Nachricht $m$ setzt sich anteilig aus einer Wurzel bezüglich modulo $p$ und $q$ zusammen ([[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^3dda16|Teilbarkeit über Primzahlfaktoren]]), wovon jeweils jedes positiv oder negativ bedingt durch die Quadratwurzel sein kann, also
>>>$$\begin{align}
>>> m^2 &\equiv c &&\;\;(\text{mod } p) \\
>>> m^2 &\equiv c &&\;\;(\text{mod } q) \\
>>>\end{align}$$
>>>Wir definieren nun zwei Variablen $c_{p}$ und $c_{q}$ als Quadratwurzeln bezüglich respektive modulo $p$ und $q$ 
>>>$$\begin{align}
>>> c_{p}^2 &\equiv c &&\;\;(\text{mod } p) \\
>>> c_{q}^2 &\equiv c &&\;\;(\text{mod } q) \\
>>>\end{align}$$
>>>Demnach
>>>$$\begin{align}
>>> m^2 &\equiv c_{p}^2 &&\;\;(\text{mod } p) \\
>>> m^2 &\equiv c_{q}^2 &&\;\;(\text{mod } q) \\
>>>\end{align}$$
>>>Wenn wir jeweils [[#^d2662c| "die modulare Wurzeln ziehen"]], erhalten wie verschiedene Lösungskombinationen für $m$.
>>>>[!warning] Achtung: Die Quadratwurzel bezüglich modulo $p$, wobei $p$ eine Primzahl ist, muss besonders bestimmt werden. Siehe [[#^d2662c| Modulare Quadratwurzel]]
>>>$$\begin{align}
>>>m_{1} &= c_{p} &&\;\;(\text{mod } p) &\land&&m_{1}=c_{q} &&\;\;(\text{mod } q) \tag{M-GLS 1}\\  
>>>m_{2} &= c_{p} &&\;\;(\text{mod } p) &\land&&m_{2}=-c_{q} &&\;\;(\text{mod } q) \tag{M-GLS 2}\\  
>>>m_{3} &= -c_{p} &&\;\;(\text{mod } p) &\land&&m_{3}=c_{q} &&\;\;(\text{mod } q) \tag{M-GLS 3}\\  
>>>m_{4} &= -c_{p} &&\;\;(\text{mod } p) &\land&&m_{4}=-c_{q} &&\;\;(\text{mod } q) \tag{M-GLS 4}\\  
>>>\end{align}$$
>>>Dies sind vier modulare Gleichungssysteme (M-GLS), welche mit dem [[4 - Angriffe auf RSA#^ca7b4b|chinesischen Restsatz]] gelöst werden kann, also
>>>$$m_{i} = \Big(\pm\big[q\big]_{p}^{-1} \cdot q \cdot c_{p}  \pm \big[q\big]^{-1}_{q} \cdot p \cdot c_{q}\Big) \text{ mod }n$$
>>>wobei durch Lesen der Nachrichten $m_{i}$ mit $(i=1,2,3,4)$ die richtige Nachricht $m$ gewählt wird.
>
>>[!korrektheitsnachweis]
>>Aus gleichen Gründen wie beim Korrektheitsnachweis für [[3 - RSA (Rivest Shamir Adleman)#^7c14da|RSA]] genügt es zu zeigen, dass das Verfahren für $p$ gültig ist, da es umgekehrt für $q$ dann ebenfalls gilt und rückschließend für $n$. 
>>
>>Wenn wir das Lösungsverfahren zur Entschlüsselung auf die Chiffre $c=m^2 \text{ mod }n$ anwenden, erhalten wir
>>$$(m^{2})^{\frac{p+1}{4}} \equiv m^{\frac{p-1}{2}}m^1 \equiv \underbrace{ \left( m^{\frac{1}{2}} \right)^{p-1} }_{ \equiv 1 \;\;(\text{mod } p) }m \equiv \pm m \;\;(\text{mod } p) \tag*{$\square$}$$
>
>>[!warning] Achtung: Die verbleibenden Klartextkandidaten $m_{i}$ müssen gelöscht werden, da sonst ein [[6 - Angriffe auf das Rabin-Verfahren#^a8d780|Angriff]] möglich ist.
>
>>[!remark] Kontrollfrage: In der [[4 - Angriffe auf RSA#^a904cc|Low Encryption Attack]] ziehen wir auch die $e$-te Wurzel, warum können wir das dort ohne besondere Lösungsformel machen?
>
>>[!remark] Kontrollfrage: Warum fordern wir für $p,q \equiv 3 \;\;(\text{mod } 4)$?
>
>>[!remark] Kontrollfrage: Welcher mathematische Hintergrund sorgt dafür, dass wir $4$ Kandidaten $m_{i}$ einer Klartextnachricht erhalten?
>

^eb3c6e


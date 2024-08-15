<!-- Eventuell irgendwann hier Euler's Criterion einfügen?-->
## 5.1 Mathematische Grundlagen

>[!theorem] Satz Modulare Quadratwurzel$c_{p}^2 \equiv c \;\;(\text{mod } p) \implies c_{p}\equiv c^{(q+1)/4} \;\;(\text{mod } p)$

## 5.2 Rabin Verschlüsselungsverfahren

>[!algo] Kryptografisches Verfahren: Rabin
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
>>>Die Lösung nach $m$ ist nicht so offensichtlich, wie es auf den ersten Blick scheinen mag. Die Nachricht $m$ setzt sich anteilig aus einer Wurzel bezüglich modulo $p$ und $q$ zusammen ([[2 - Algebraische und Zahlentheoretische Grundlagen#^3dda16|Teilbarkeit über Primzahlfaktoren]]), wovon jeweils jedes positiv oder negativ bedingt durch die Quadratwurzel sein kann, also
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
>>>Wenn wir jeweils "die Wurzeln ziehen", erhalten wie verschiedene Lösungskombinationen für $m$.
>>>>[!warning] Achtung: Die Quadratwurzel bezüglich modulo $p$, wobei $p$ eine Primzahl ist, muss besonders bestimmt werden.
>>>$$\begin{align}
>>>m_{1} &= c_{p} &&\;\;(\text{mod } p) &\land&&m_{1}=c_{q} &&\;\;(\text{mod } q) \tag{M-GLS 1}\\  
>>>m_{2} &= c_{p} &&\;\;(\text{mod } p) &\land&&m_{2}=-c_{q} &&\;\;(\text{mod } q) \tag{M-GLS 2}\\  
>>>m_{3} &= -c_{p} &&\;\;(\text{mod } p) &\land&&m_{3}=c_{q} &&\;\;(\text{mod } q) \tag{M-GLS 3}\\  
>>>m_{4} &= -c_{p} &&\;\;(\text{mod } p) &\land&&m_{4}=-c_{q} &&\;\;(\text{mod } q) \tag{M-GLS 4}\\  
>>>\end{align}$$
>>>Dies sind vier modulare Gleichungssysteme (M-GLS), welche mit dem [[4 - Angriffe auf RSA#^ca7b4b|chinesischen Restsatz]] gelöst werden kann, also
>>>$$m_{i} = \Big(\pm\big[q\big]_{p}^{-1} \cdot q \cdot c_{p}  \pm \big[q\big]^{-1}_{q} \cdot p \cdot c_{q}\Big) \text{ mod }n$$
>>>wobei durch Lesen der Nachrichten $m_{i}$ mit $(i=1,2,3,4)$ die richtige Nachricht $m$ gewählt wird.
>>>

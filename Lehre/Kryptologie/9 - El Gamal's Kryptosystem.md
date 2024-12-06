
>[!remark]- Bemerkung: Zur Entstehung
> Das El Gamal's Kryptosystem wurde von Taher Elgamal 1984 entwickelt. Es nimmt sich [[8 - No-Key Protokolle#^d70a98| Diffie Hellman's Schlüsselaustausch]] als Vorbild und folgt dem von Diffie und Hellman's vorgeschlagenen Konzept [[3 - RSA (Rivest Shamir Adleman)#^7402b5|neuer asymmetrischer Verschlüsselungsverfahren]].

>[!algo] Kryptografisches Verfahren: El Gamal's Verschlüsselung (1984) ([[../../PDFs/elgamal1985.pdf|Quelle]])
>
>>[!schlüsselerzeugung]
>>Man wählt eine große Primzahl $p$ und eine [[7 - Algebraische und Zahlentheoretische Grundlagen (2)#^01650b|primitive Wurzel]] $a$ von $p$.
>> - privater Schlüssel: $(p,a,A)$ mit $$A \in_{R} \mathbb{Z}^*_{p}$$
>> - öffentlicher Schlüssel: $(p,a,B)$ mit $$B=a^A \text{ mod }p \tag{1}$$
>
>>[!verschlüsselung] 
>>Sei $m<p$ eine zu verschlüsselnde Nachricht. Man wählt $k\in_{R}\mathbb{Z}_{p}^*$ und berechnet
>>
>><u>Verschlüsselung</u>:
>>
>>$$(C_{1}, C_{2})= (a^k \text{ mod }p ,  B^k \cdot m \text{ mod }p) \tag{2}$$
>>
>><u>Entschlüsselung</u>:
>>
>>$$m = C_{1}^{-A}\cdot C_{2} \text{ mod } p \tag{3}$$
>>mit
>>$$C_{1}^{-A} \equiv (C_{1}^{-1})^A \;\;(\text{mod } p)$$
>
>>[!korrektheitsnachweis]
>>Wir verwenden die Beschreibung des Verschlüsselungsverfahrens.
>>$$\begin{align}
>> m &\equiv C_{1}^{-A}\cdot C_{2} &&\;\;(\text{mod } p) \tag*{$\leftarrow(3)$}\\
>> &\equiv (a^k)^{-A}\cdot B^k \cdot m &&\;\;(\text{mod } p) \tag*{$\leftarrow(2)$}\\
>> &\equiv a^{-Ak}\cdot (a^{A})^k \cdot m &&\;\;(\text{mod } p) \tag*{$\leftarrow(1)$}\\
>> &\equiv a^{-Ak}\cdot a^{Ak} \cdot m &&\;\;(\text{mod } p) \\
>> &\equiv a^{-Ak+Ak} \cdot m &&\;\;(\text{mod } p) \\
>> &\equiv a^{0} \cdot m &&\;\;(\text{mod } p) \\
>> &\equiv m &&\;\;(\text{mod } p) \\
>>\end{align}$$
>>$$\tag*{$\square$}$$
>
>>[!remark] Kontrollfrage: Warum basiert das Verfahren auf dem Diskreten Logarithmus Problem?
>
>>[!remark] Kontrollfrage: Warum ist es unerheblich, welches $k \in \mathbb{Z}_{p}^*$ zur Verschlüsselung gewählt wird?
>
>>[!remark] Kontrollfrage: Warum muss Alice zum Entschlüsseln das $k \in \mathbb{Z}_{p}^*$ nicht kennen?

^90f6e7

>[!def] Definition Digitale Signatur Verfahren (Buch p.440)
>Ein digitales Signaturverfahren erlaubt es einem *Unterzeichner*, welcher ein **Schlüsselpaar eines asymmetrischen Verschlüsselungsverfahrens** erzeugt hat, **eine Nachricht mit einem privaten Schlüssel zu signieren**.
>
>Der Empfänger kann mit dem digitalen Signaturverfahren mithilfe **des öffentlichen Schlüssels** prüfen, dass *der Unterzeichner* Urheber der Nachricht ist.

^95db8e

>[!algo] Kryptografisches Verfahren: El Gamal Signatur
>
>>[!schlüsselerzeugung] Voraussetzung
>>Es existieren die Schlüssel
>>- öffentlicher Schlüssel: $(p,a,B)$
>>- privater Schlüssel: $(p,a,A)$
>
>>[!verschlüsselung] Signatur
>>Alice möchte eine Nachricht $m<p$ signieren. Alice wählt dazu $k < p-1$ mit $\text{ggT}(k, p-1)=1$.
>>
>><u>SIgnaturerstellung</u>:
>>
>>Alice berechnet:
>>$$\begin{align}
>> r&= a^k \text{ mod }p \tag{1}\\
>> s &= k^{-1}(m-Ar) \text{ mod }p-1 \tag{2}
>>\end{align}$$
>>wobei $k^{-1}= [k]^{-1}_{p-1}$ das [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^6f68c0|modulare Inverse]] bezüglich $p-1$ ist.
>>
>>Alice sendet:
>>$$(m,(r,s))$$
>>wobei $(r,s)$ die digitale Signatur ist.
>>
>><u>Verifikation</u>:
>>
>>Bob prüft ob $r<p$, falls das nicht gilt, verwirft er die Signatur. Er berechnet außerdem
>>$$\begin{align}
>> v_{1} &= B^r r^s \text{ mod }p \tag{3}\\
>> v_{2} &= a^m \text{ mod }p \tag{4}
>>\end{align}$$
>>
>>und prüft ob $v_{1}=v_{2}$:
>>- $v_{1} = v_{2}? \overset{\text{ja}}\longrightarrow$ Bob akzeptiert die Signatur
>>- $v_{1} = v_{2}? \overset{\text{nein}}\longrightarrow$ Bob lehnt die Signatur ab
>
>
>>[!korrektheitsnachweis]
>>Wir verwenden die Beschreibung des Verschlüsselung- (E) und Signaturverfahrens (S). Wenn die Signatur von Alice stammt, dann gilt:
>>$$\begin{align}
>> v_{1} &\equiv B^r r^s &&\;\;(\text{mod } p)\tag*{$\leftarrow S(4)$} \\
>> &\equiv (a^A)^r (a^k)^s &&\;\;(\text{mod } p)\tag*{$\leftarrow E(1),S(1)$}\\
>> &\equiv a^{Ar} a^{ks} &&\;\;(\text{mod } p)
>>\end{align}$$
>>
>>Wir verwenden $S(2)$ um den Ausdruck $ks$ zu erzeugen, also
>>$$\begin{align}
>> s &\equiv k^{-1}(m-Ar) &&\;\;(\text{mod } p-1)\\
>> ks &\equiv m-Ar &&\;\;(\text{mod } p-1)
>>\end{align}$$
>>Diese Kongruenz können wir in eine gewöhnliche Identität umwandeln mit der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^30b120|Existenz und Eindeutigkeit des Quotienten]], sodass $\exists d \in \mathbb{Z}:$
>>$$ks = m-Ar + d(p-1)$$
>> Diesen Ausdruck nutzen wir, um den Beweis fortzustetzen
>> $$\begin{align}
>> &\equiv a^{Ar} a^{m-Ar + d(p-1)} &&\;\;(\text{mod } p)\\
>> &\equiv a^{Ar} a^{m} a^{-Ar} a^{d(p-1)} &&\;\;(\text{mod } p)\\
>> &\equiv a^{0} \underbrace{ a^{m} }_{ \equiv v_{2} }  \underbrace{ (a^{d})^{(p-1)} }_{ \equiv 1 } &&\;\;(\text{mod } p)\\ 
>> &\equiv v_{2} &&\;\;(\text{mod } p) \tag*{$\leftarrow S(4)$}
>>\end{align}$$
>>$$\tag*{$\square$}$$
>
>
>>[!remark] Kontrollfrage: Warum fordern wir im Signaturverfahren, dass $\text{ggT}(k,p-1)=1$?

^13979e

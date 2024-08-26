## 8.1 Diffie- Schlüsselaustausch

>[!remark] Motivation
> Wie können sich zwei Parteien auf ein gemeinsames Geheimnis über ungesicherte Kommunikationskanäle einigen?
> 
> Das folgende Verfahren beschreibt wie zwei Parteien sich auf ein Geheimnis bzw. Schlüssel einigen können.

>[!algo] Kryptografisches Verfahren: Diffie Hellmann Schlüsselaustausch (1976) ([[../../PDFs/li2010.pdf|Quelle]])
>
>>[!proof] Parameter
>> Alice und Bob einigen sich auf eine Primzahl $p$ und eine entsprechende [[7 - Algebraische und Zahlentheoretische Grundlagen (2)#^01650b|primitive Wurzel]] $g$ bezüglich $p$.
>
>>[!verschlüsselung] Verfahren 
>>Die Notation $\in_{R}$ kennzeichnet, dass ein Element zufällig gewählt wird.
>>1. Alice wählt $a \in_{R} \mathbb{Z}^*_{p}$ und sendet an Bob: $$A=g^a \text{ mod } p$$
>>2. Bob wählt $b \in_{R} \mathbb{Z}^{*}_{p}$ und sendet an Alice: $$B=g^b \text{ mod }p$$
>>3. Alice berechnet $$B^a \text{ mod }p$$
>>4. Bob berechnet $$A^b \text{ mod } p$$
>> 
>> Alice und Bob besitzen nun den gemeinsamen Schlüssel
>> $$K=B^a \text{ mod }p=A^b \text{ mod }p$$
>
>>[!Korrektheitsnachweis]
>>Wir setzen einfach sukzessive die Definitionen im Verfahren ein und verwenden die Potenzgesetze
>>$$A^b \overset{1.}{\equiv} (g^a)^b \equiv g^{ab} \equiv g^{ba} \equiv (g^b)^a \overset{2.}{\equiv} B^a \;\;(\text{mod } p) \tag*{$\square$}$$
>
>>[!remark]- Bemerkung zur Sicherheit
>>Die Sicherheit des Verfahrens beruht auf dem [[7 - Algebraische und Zahlentheoretische Grundlagen (2)#^9e7a61|diskreten Logarithmus Problem]]. Um die Potenzen von Alice und Bob zu finden, muss folgendes gelöst werden
>>$$\begin{align}
>> \log_{g} A &\equiv a \;\;(\text{mod } p)\\
>> \log_{g} B &\equiv b \;\;(\text{mod } p)
>>\end{align}$$
>
>>[!Remark]- Bemerkung zum Namen (Informativ)
>>Dieses Verfahren wird auch das *Diffie-Hellman-Merkle* Verfahren genannt, da Ralph Merkle wesentliche Beiträge zur Konzeption des Verfahrens geleistet hat.

^d70a98

## 8.2 Shamir's No-Key-Scheme

>[!algo] Krytografisches Verfahren: Shamir's No-Key-Scheme
>
>>[!proof] Parameter
>>Alice und Bob einigen sich auf eine große Primzahl $p$. Alice möchte eine Nachricht $m \in \mathbb{Z}_{p}$ verschlüsseln und versenden.
>
>>[!verschlüsselung] Verfahren
>>Alice:
>>1. wählt $a,a' \in \mathbb{Z}_{p-1}$ mit $aa' \equiv 1 \;\;(\text{mod } p-1)$
>>2. sendet an Bob: $$C = m^a \text{ mod } p$$
>>
>>Bob:
>>
>>3. wählt $b,b' \in \mathbb{Z}_{p-1}$ mit $bb'\equiv_{1} \;\;(\text{mod } p-1)$
>>4. sendet an Alice: $$D=C^b \text{ mod }p$$
>>
>>Alice:
>>
>>5. sendet an Bob:$$E=D^{a'} \text{ mod }p$$
>>
>>Bob:
>>
>>6. Berechnet 
>>$$m=E^{b'} \text{ mod }p$$
>
>>[!korrektheitsnachweis]
>>Zunächst zeigen wir, dass $$m^{aa'} \equiv m^{bb'} \equiv m \;\;(\text{mod } p)$$ gilt. Über die Verfahrensbeschreibung wissen wir, dass
>>$$aa' \equiv bb' \equiv 1 \;\;(\text{mod } p-1) \tag{1}$$
>>Wir zeigen fortgehend für $aa'$ die Gültigkeit, die allerdings aus denselben Konditionen auch für $bb'$ folgt. Für die Kongruenz $(1)$ folgt durch den [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^30b120|Satz Existenz und Eindeutigkeit des Quotienten und Rests]]
>>$$aa'=q(p-1)+1$$
>>Wir setzen daher ein
>>$$m^{aa'} \equiv m^{q(p-1)+1} \equiv \underbrace{ (m^{q})^{p-1} }_{ \equiv 1 (\text{mod } p) }m \equiv m \;\;(\text{mod } p) \tag{2}$$ 
>>
>>Mit der Erkenntnis von Kongruenz $(2)$ arbeiten wir das Verfahren vom letzten Schritt rückwärts ab und zeigen, dass die originale Nachricht folgen muss
>>$$\begin{align}
>> m &\equiv E^{b'} &&\;\;(\text{mod } p) \tag{6.}\\
>>   &\equiv (D^{a'})^{b'} &&\;\;(\text{mod } p) \tag{5.}\\ \\
>>  &\equiv D^{a'b'} &&\;\;(\text{mod } p) \\
>> &\equiv (C^{b})^{a'b'} &&\;\;(\text{mod } p) \tag{4.} \\
>> &\equiv C^{ba'b'} && \;\;(\text{mod } p) \\
>> &\equiv (m^{a})^{ba'b'} && \;\;(\text{mod } p) \tag{2.} \\
>> &\equiv m^{aba'b'} && \;\;(\text{mod } p) \\
>> &\equiv m^{aa'bb'} && \;\;(\text{mod } p) \\
>> &\equiv (\underbrace{ m^{aa'} }_{ \equiv m })^{bb'} && \;\;(\text{mod } p) \\
>> &\equiv \underbrace{ m^{bb'} }_{ \equiv m } && \;\;(\text{mod } p) \\
>> &\equiv m && \;\;(\text{mod } p) \\
>>\end{align}$$
>>$$\tag*{$\square$}$$
>
>>[!remark] Kontrollfrage: Warum basiert dieses Verfahren auf dem Diskreten Logarithmus Problem?
>
>>[!remark] Kontrollfrage: Warum wählen wir $(p-1)$ als Modul in der Kongruenz $$aa' \equiv bb' \equiv 1 \;\;(\text{mod } p-1)$$
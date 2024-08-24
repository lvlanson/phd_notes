>[!remark] Motivation
> Wie können sich zwei Parteien auf ein gemeinsames Geheimnis über ungesicherte Kommunikationskanäle einigen?
> 
> Das folgende Verfahren beschreibt wie zwei Parteien sich auf ein Geheimnis bzw. Schlüssel einigen können.

>[!algo] Kryptografisches Verfahren: Diffie Hellmann Schlüsselaustausch ([[../../PDFs/li2010.pdf|Quelle]])
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
>>[!remark] Bemerkung zur Sicherheit
>>Die Sicherheit des Verfahrens beruht auf dem [[7 - Algebraische und Zahlentheoretische Grundlagen (2)#^9e7a61|diskreten Logarithmus Problem]]. Um die Potenzen von Alice und Bob zu finden, muss folgendes gelöst werden
>>$$\begin{align}
>> \log_{g} A &\equiv a \;\;(\text{mod } p)\\
>> \log_{g} B &\equiv b \;\;(\text{mod } p)
>>\end{align}$$
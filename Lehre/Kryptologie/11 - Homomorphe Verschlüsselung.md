>[!remark]- Motivation
> Homomorphe Verschlüsselung erlaubt es uns im Schlüsselraum zu rechnen, sodass die Ergebnisse äquivalent im Klartextraum sind. Nehmen wir einen beliebigen homomorphen Verschlüsselungsalgorithmus, der eine Klartextnachricht $m \in \mathbb{Z}$ verschlüsselt.
> $$\begin{align}
> \text{Enc}(m) &= c \\
> Dec(c) &= m
>\end{align}$$
> 
> So erlaubt uns die homomorphe Verschlüsselung unter der homomorphen Operation Addition (kann auch die Multiplikation sein)
> $$\text{Dec}(c_{1}+c_{2})=m_{1}+m_{2} = \text{Dec}(c_{1})+ \text{Dec}(c_{2})$$
>
>Bereits mit dem Aufkommen der ersten asymmetrischen Verschlüsselungsverfahren, diskutierte [[../../PDFs/rivest1978.pdf|Rivest, Adleman und Dertouzos (1978)]] den Nutzen von Verfahren, die es erlauben im Schlüsselraum direkt zu rechnen. Dabei zeichnen sie das Szenario, dass eine Bank mögliche Anfragen wie 
> - den Durchschnitt von Krediten
> - die Summe an Einnahmen durch Kredite für den nächsten Monat
> - wie viele Kredite über $5000\$$ vergeben wurden
> 
> beantwortet werden sollen, ohne die Beschaffenheit der Daten zu teilen.
> 
> Homomorphe Verschlüsselung galt bis 2009 als der *heilige Gral* in der Kryptologie. Bis dahin gab es Verschlüsselungsalgorithmen, die bis zu einem gewissen Grad erlaubten im Schlüsselraum Berechnungen durchzuführen. 2009 gelang es [[../../PDFs/gentry2009.pdf|Craig Gentry]] einen vollständig homomorphen Verschlüsselungsalgorithmus zu entwickeln. Seither wird viel an diesen Algorithmen geforscht.
> 
> ![[Figures/zeitachse_krypto.png|center]]
> <center>Abbildung: Zeitachse zu Homomorphen Verschlüsselungsalgorithmen <br> PHE - Partially Homomorphic Encryption <br> SWHE - Somewhat Homomorphic Encryption <br> FHE - Fully Homomorphic Encryption</center>
> 
> ([[../../PDFs/acar2017.pdf|Bildquelle]])
> 
> 
> Diese Konzepte spielen in kritischen Bereichen wie Cloud Computing, maschinelles Lernen in verteilten Netzen oder auch Finanztransaktionen eine wichtige Rolle. Quasi überall wo sensibler Datenaustausch mit Berechnungen aufeinandertrifft.
> 
> Wir beschäftigen uns in der Lehrveranstaltung nur mit dem Grundkonzept und illustrieren anhand der bekannten Algorithmen, dass einige dieser bereits begrenzt über homomorphe Eigenschaften verfügen.

## 11.1 Mathematische und Terminologische Grundlagen

>[!def] Definition Gruppen Homomorphismus ([[../../PDFs/judson2022.pdf#page=145|Quelle]])
>Ein **Homomorphismus** zwischen zwei Gruppen $(G, \cdot)$ und $(H, \circ)$ ist eine Abbildung $$\phi:G\to H$$ sodass für $g_{1},g_{2} \in G$
>$$\phi(g_{1} \cdot g_{2})= \phi(g_{1}) \circ \phi(g_{2})$$
>>[!example]- Beispiel
>>Sei $(G, \odot)$ eine [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppe]] und $g \in G$. Wir defineren die Abbildung
>>$$\phi: \mathbb{Z} \to G$$
>>mit $$\phi(n)=g^n$$
>>Dann ist $\phi$ ein **Gruppenhomomorphismus**, da
>>$$\phi(n+m)= g^{n+m}= g^ng^m=\phi(n)\phi(m) \tag*{$\blacktriangleleft$}$$
>
>>[!remark] Kontrollfrage: Warum verlangen wir im Beispiel, dass $G$ eine [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppe]] ist?

>[!def] Definition Homomorphe Verschlüsselung ([[../../PDFs/acar2017.pdf#page=5|Quelle]]) 
> Seien $M$ der Klartextraum und $C$ der Schlüsseltextraum. Ein Verschlüsselungsschema wird als **homomorph** über einer Operation $\star$ bezeichnet, wenn für den Verschlüsselungsalgorithmus $\text{Enc}: M \to C$ gilt
> $$\text{Enc}(m_{1}) \star \text{Enc}(m_{2}) = \text{Enc}(m_{1} \star m_{2})$$

^ccc183

>[!def] Definition Homomorphes Verschlüsselungsschema ([[../../PDFs/acar2017.pdf#page=5|Quelle]])
>Ein **homomorphes Verschlüsselungsschema** besteht aus vier Algorithmen
>1.  $\text{KeyGen}(\lambda)$ - erzeugt das Schlüsselpaar $(pk, sk)$ in Abhängigkeit eines Sicherheitsparameters $\lambda$
>2. $\text{Enc}(m)$ - verschlüsselt eine Nachricht $m$ und gibt die Chiffre $c$ zurück
>3. $\text{Dec}(c)$ - entschlüsselt eine Chiffre $c$ und gibt die originale Nachricht $m$ zurück
>4. $\text{Eval}(c_{1},\dots,c_{n})$ - nimmt eine Reihe von Chiffren $c_{1},\dots,c_{n}$ und bildet diese über eine vordefinierte Reihe an Operationen ab und gibt das Resultat $c$ zurück.
>
>>[!remark]- Bemerkung: Einordnung
>>Die ersten 3 Punkte unterscheiden sich nicht von den Algorithmen, die wir bisher kennengelernt haben. 
>>
>>Der Sicherheitsparameter $\lambda$ entspricht bei RSA beispielsweise der Bittiefe des Moduls. Üblicherweise ist die Schlüsselerzeugung auch noch von einem *Funktionalitätsparameter* abhängig, der Komplexitätseigenschaften des Verfahrens bestimmt. Diesen Parameter erwähnen wir an dieser Stelle kurz, da er in Verwendung dieser Algorithmen von großer Bedeutung ist. 
>>
>> Es existiert auch noch ein Hilfsparameter $\alpha$, welcher für anspruchsvollere homomorphe Verschlüsselungsalgorithmen den maximalen Umfang von Operationen im Schlüsselraum bestimmt. Mehr dazu könnt ihr [[../../PhD Studies/Cryptology/Homomorphic Encryption/Surveys/Basic Definitions#^5f3338|hier]] lesen.
>>
>> Die $\text{Eval}$ Funktion kann verschiedene Arten von Funktionen darstellen. Diese müssen allerdings durch $\text{AND}$ und $\text{OR}$ Gates darstellbar sein, bzw. durch die Addition und Multiplikation im Schlüsselraum. Man nennt hierbei die Menge aller darstellbaren Operationsabfolgen *Circuits* $\mathcal{C}$ und eine konkrete Abfolge einen *Circuit*. Die Anzahl der Operationen hat einen direkten (teilweise massiven) Einfluss auf die Komplexität verschiedener Aspekte wie Schlüsselerzeugung oder Berechnungen im Schlüsselraum, weshalb damit üblicherweise versucht wird sparsam umzugehen. Dies ist dadurch bis heute noch ein Forschungsfeld, welches viel Aufmerksamkeit in der Kryptologie erhält.

>[!def] Definition Teilweise Homomorphe Verschlüsselungsschema ([[../../PDFs/armknecht2015a.pdf#page=14|Quelle]])
> Wir bezeichnen ein homomorphes Verschlüsselungsschema als **teilweise homomorph**, wenn die $\text{eval}$-Funktion eine eingeschränkte Menge an Operationen erlaubt.
>
>>[!remark] Bemerkung: Hierbei gilt, dass wir die homomorphe Eigenschaft lediglich bezüglich **einer Auswahl an Operationen** haben.

^e93583

>[!def] Definition Vollständiges Homomorphes Verschlüsselungsschema ([[../../PDFs/armknecht2015a.pdf#page=14|Quelle]])
>Wir bezeichnen ein homomorphes Verschlüsselungsschema als **vollständig homomorph**, wenn die $\text{eval}$-Funktion beliebige Operationen auf den Chiffren erlaubt und die Größe der Chiffren unabhängig von der Anzahl oder Komplexität der durchgeführten Operationen bleibt.


>[!theorem] Satz Teilweise Homomorphes RSA
> [[3 - RSA (Rivest Shamir Adleman)#^7c14da|RSA]] ist ein [[#^e93583|teilweise homomorphes Verschlüsselungsschema]] mit beliebiger $\text{eval}$-Größe bezüglich der Multiplikation.
> 
>>[!proof]- Beweis
>>Ohne Beschränkung der Allgemeinheit zeigen wir die homomorphe Eigenschaften anhand zwei Elemente. Es ist leicht ersichtlich, dass dies sich auf beliebig viele erweitern lässt. 
>>
>>Seien $m_{1},m_{2} \in \mathbb{Z}_{n}$ und $pk=(e,n), sk=(d,n)$
>>$$\begin{align}
>> \text{Enc}(m)&= m^e \text{ mod }n = c \\
>> \text{Dec}(c)&=c^d \text{ mod }n = m
>>\end{align}$$
>> Wir prüfen die Identität der Definition der [[#^ccc183|homomorphen Verschlüsselung]], also
>> $$\begin{align}
>> \text{Enc}(m_{1}\cdot m_{2})&= (m_{1} \cdot m_{2})^e  \\
>> &= m_{1}^e \cdot m_{2}^e \\
>> &= \text{Enc}(m_{1}) \cdot \text{Enc}(m_{2}) \tag*{$\square$}
>>\end{align}$$
>
>>[!remark]- Bemerkung: Keine Additive Homomorphe Charakteristik
>> Das RSA Verfahren hat keine homomorphe Eigenschaften bezüglich der Addition
>>$$\begin{align}
>> \text{Enc}(m_{1} + m_{2}) &= (m_{1}+m_{2})^e \\
>> &= \sum_{k=0}^e \binom{e}{k}m_{1}^{k}m_{2}^{e-k}  \\
>> &\neq \text{Enc}(m_{1})+\text{Enc}(m_{2})
>>\end{align}$$
>>aufgrund des binomischen Lehrsatzes 
>>>[!theorem]- Binomischer Lehrsatz
>>>Für $a,b \in \mathbb{R}$ und $n \in \mathbb{N}$ gilt
>>>$$(a+b)^n=\sum_{k=0}^n\binom{n}{k}a^nb^{n-k} $$
>>>wobei der Binomialkoeffizient definiert ist mit
>>>$$\binom{n}{k}=\frac{n!}{k!(n-k)!}$$

>[!theorem] Satz Teilweise Homomorphes El Gamal Verschlüsselung
>[[9 - El Gamal's Kryptosystem#^90f6e7|Das El Gamal Verschlüsselungsverfahren]] ist ein [[#^e93583|teilweise homomorphes Verschlüsselungsschema]] mit beliebiger $\text{eval}$-Größe bezüglich der Addition.
>>[!proof]- Beweis
>>Ohne Beschränkung der Allgemeinheit zeigen wir die homomorphe Eigenschaften anhand zwei Elemente. Es ist leicht ersichtlich, dass dies sich auf beliebig viele erweitern lässt. 
>>
>>Seien $m_{1}, m_{2} \in \mathbb{Z}_{n}$ und $pk=(p,a,B), sk=(p,a,A), k \in_{R} Z^*_{p}$ mit
>>$$\begin{align}
>> \text{Enc}(m) &= (a^k \text{ mod } p, B^k \cdot m \text{ mod }p) = (C_{1},C_{2})\\
>> \text{Dec}(C_{1},C_{2}) &= C_{1}^{-A} \cdot C_{2} \text{ mod } p = m
>>\end{align}$$
>>Wir definieren für die Addition zweier Chiffren $c=(C_{1}, C_{2})$ und $\widehat{c}=(C_{1},\widehat{C}_{2})$mit selben $k \in_{R} \mathbb{Z}^*_{p}$
>>$$\begin{align}
>>c+\widehat{c}&= (C_{1}, C_{2})+ (C_{1}, \widehat{C}_{2}) \\
>> &= (C_{1}, C_{2}+\widehat{C}_{2})
>>\end{align}$$
>>Wir prüfen damit die Identität der Definition der [[#^ccc183|homomorphen Verschlüsselung]], also
>>$$\begin{align}
>> \text{Enc}(m_{1}+m_{2}) &= (a^k \text{ mod }p, B^k \cdot (m_{1}+m_{2}) \text{ mod }p) \\
>> &= (a^k \text{ mod }p, B^k \cdot m_{1} \text{ mod }p + B^k \cdot m_{2}) \\
>> &=(a^k \text{ mod } p, B^k \cdot m_{1} \text{ mod }p) + (a^k \text{ mod } p, B^k \cdot m_{2} \text{ mod } p) \\
>> &= \text{Enc}(m_{1})+\text{Enc}(m_{2}) \tag*{$\square$}
>>\end{align}$$
>
>>[!remark]- Bemerkung: Keine Multiplikative Homomorphe Charakteristik
>>Es ist leicht ersichtlich durch
>>$$\begin{align}
>> \text{Enc}(m_{1} \cdot m_{2}) &= (a^k \text{ mod }p, B^k \cdot m_{1}\cdot m_{2} \text{ mod }p) \tag{1}\\
>> &\neq \text{Enc}(m_{1}) \cdot \text{Enc}(m_{2})
>>\end{align}$$
>>da sich in Zeile $(1)$ der Koeffizient $B^k$ nicht auf beide Nachrichten $m_{1},m_{2}$ aufteilen lässt.

>[!remark]- Bemerkung: Weitere Informationen zu Homomorpher Verschlüsselung (Informativ)
> Die vollständig homomorphen Verschlüsselungsschemen (VHV) lassen sich immer auf [[../../PhD Studies/Cryptology/Homomorphic Encryption/Lattice Based/1 - Elementary Lattice Definitions|diskrete Gitter]] zurückführen. Der erste VHV wurde von [[../../PDFs/gentry2009.pdf|Gentry (2009)]] entwickelt und nutzte genau diese Gitterstrukturen. Dieses mathematische Gebiet enthält ebenfalls [[../../PhD Studies/Cryptology/Homomorphic Encryption/Lattice Based/2 - Computational Problems on Lattices|Einweg-Probleme]], in denen Berechnungen in eine Richtung sehr simpel sind, aber umgekehrt extrem schwierig sind (ähnlich wie das [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^ecfc5d| Faktorisierungsproblem]] und das [[7 - Algebraische und Zahlentheoretische Grundlagen (2)#^9e7a61|diskrete Logarithmusproblem]]). 
> 
> Diese Algorithmen leiden alle an Effizienz-Problemen mit wachsenden Schlüsselraumfunktionen ($\text{eval}$). Neben den Effizienz-Problemen müssen auch zusätzliche Maßnahmen getroffen werden, um ein Rauschen möglichst kleinzuhalten, da sonst eine korrekte Verschlüsselung gefährdet ist.
> 
> Homomorphe Verschlüsselung ist nach wie vor ein großes Thema, worin auch große Fortschritte gemacht. Dieses Thema erfordert allerdings eine gründliche Auseinandersetzung mit den mathematischen Konzepten von Gitterstrukturen, um deren Sicherheit belegen zu können.
>
> Nicht zuletzt liegt ohnehin die Zukunft der Verschlüsselung in Algorithmen der Gitterstrukturen, da diese bereits **nachweislich quantensicher** sind. Quantencomputer sind in der Lage effizient Shors Algorithmus durchzuführen, welcher große Zahlen faktorisieren kann, und somit die klassischen asymmetrischen Verschlüsselungsverfahren angreifbar machen.
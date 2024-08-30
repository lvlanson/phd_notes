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
> - wieviele Kredite über $5000\$$ vergeben wurden
> 
> beantwortet werden sollen, ohne die Beschaffenheit der Daten zu teilen.
> 
> Homomorphe Verschlüsselung galt bis 2009 als der *heilige Gral* in der Kryptologie. Bis dahin gab es Verschlüsselungsalgorithmen, die bis zu einem gewissen Grad erlaubten im Schlüsselraum Berechnungen durchzuführen. 2009 gelang es [[../../PDFs/gentry2009.pdf|Craig Gentry]] einen vollständig homomorphen Verschlüsselungsalgorithmus zu entwickeln. Seither wird viel an diesen Algorithmen geforscht.
> 
> ![[../../Pasted image 20240830171529.png|center]]
> <center>Abbildung: Zeitachse zu Homomorphen Verschlüsselungsalgorithmen <br> PHE - Partially Homomorphic Encryption <br> SWHE - Somewhat Homomorphic Encryption <br> FHE - Fully Homomorphic Encryption</center>
> 
> ([[../../PDFs/acar2017.pdf|Bildquelle]])
> 
> 
> Diese Konzepte werden in kritischen Bereichen wie Cloud Computing, maschinelles Lernen in verteilten Netzen oder auch Finanztransaktionen. Quasi überall wo sensibler Datenaustausch mit Berechnungen aufeinandertrifft.
> 
> Wir beschäftigen uns in der Lehrveranstaltung nur mit dem Grundkonzept und illustrieren anhand der bekannten Algorithmen, dass einige dieser bereits begrenzt über homomorphe Eigenschaften verfügen.

## 11.1 Mathematische und Terminologische Grundlagen

>[!def] Definition Gruppen Homomorphismus ([[../../PDFs/judson2022.pdf#page=145|Quelle]])
>Ein **Homomorphismus** zwischen zwei Gruppen $(G, \cdot)$ und $(H, \circ)$ ist eine Abbildung $$\phi:G\to H$$ sodass für $g_{1},g_{2} \in G$
>$$\phi(g_{1} \cdot g_{2})= \phi(g_{1}) \circ \phi(g_{2})$$
>>[!example]- Beispiel
>>Sei $G$ eine [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppe]] und $g \in G$. Wir defineren die Abbildung
>>$$\phi: \mathbb{Z} \to G$$
>>mit $$\phi(n)=g^n$$
>>Dann ist $\phi$ ein **Gruppenhomomorphismus**, da
>>$$\phi(n+m)= g^{n+m}= g^ng^m=\phi(n)\phi(m) \tag*{$\blacktriangleleft$}$$
>
>>[!remark] Kontrollfrage: Warum verlangen wir im Beispiel, dass $G$ eine [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^afad91|Gruppe]] ist?

>[!def] Definition Homomorphe Verschlüsselung ([[../../PDFs/acar2017.pdf#page=5|Quelle]]) 
> Seien $M$ der Klartextraum und $C$ der Schlüsseltextraum. Ein Verschlüsselungsschema wird als **homomorph** über einer Operation $\star$ bezeichnet, wenn für den Verschlüsselungsalgorithmus $\text{Enc}: M \to C$ gilt
> $$\text{Enc}(m_{1}) \star \text{Enc}(m_{2}) = \text{Enc}(m_{1} \star m_{2})$$

>[!def] Definition Homomorphes Verschlüsselungsschema ([[../../PDFs/acar2017.pdf#page=5|Quelle]])
>Ein **homomorphes Verschlüsselungsschema** besteht aus vier Algorithmen
>1.  $\text{KeyGen}(\lambda)$ - erzeugt das Schlüsselpaar $(pk, sk)$ in Abhängigkeit eines Sicherheitsparameters $\lambda$
>2. $\text{Enc}(m)$ - verschlüsselt eine Nachricht $m$ und gibt die Chiffre $c$ zurück
>3. $\text{Dec}(c)$ - entschlüsselt eine Chiffre $c$ und gibt die originale Nachricht $m$ zurück
>4. $\text{Eval}(c_{1},\dots,c_{n})$ - nimmt eine Reihe von Chiffren $c_{1},\dots,c_{n}$ und bildet diese über eine vordefinierte Reihe an Operationen ab und gibt das Resultat $c$ zurück.
>
>>[!remark] Bemerkung: Einordnung
>>Die ersten 3 Punkte unterscheiden sich nicht von den Algorithmen, die wir bisher kennengelernt haben. 
>>
>>Der Sicherheitsparameter $\lambda$ entspricht bei RSA beispielsweise der Bittiefe des Moduls. Üblicherweise die Schlüsselerzeugung auch noch von einem *Funktionalitätsparameter* abhängig, der Komplexitätseigenschaften des Verfahrens bestimmt. Diesen Parameter erwähnen wir an dieser Stelle kurz, da er in Verwendung dieser Algorithmen von großer Bedeutung ist.
>>
>> Die $\text{Eval}$ Funktion kann verschiedene Arten von Funktionen darstellen. Beispielsweise können $\min, \max$, der Logarithmus oder beliebige andere Operationen darunter fallen. Die Wahl der Operationen ist jedoch in Abhängigkeit von der Konstruktion des Schemas beschränkt. Vielmehr hat die Anzahl der Operationen einen direkten (teilweise massiven) Einfluss auf die Komplexität verschiedener Aspekte wie Schlüsselerzeugung oder Berechnungen im Schlüsselraum, weshalb damit üblicherweise versucht wird sparsam umzugehen. Dies ist dadurch bis heute noch ein Forschungsfeld, welches viel Aufmerksamkeit in der Kryptologie erhält.
>> 
>> Wenn Funktionen in der $\text{Eval}$ Funktion sich als AND und XOR Gates darstellen lassen, wird eine konkrete Abfolge von Operationen auch als Circuit (Schaltkreis) bezeichnet.

>[!def] Definition Teilweise Homomorphe Verschlüsselung ([[../../PDFs/acar2017.pdf#page=2|Quelle]])
>Seien $(M, \circ)$ und $(C, \odot)$ Gruppen und $\text{Dec}:C\to M$ ein Verschlüsselungsalgorithmus, dann ist die Verschlüsselung **teilweise homomorph**, wenn für $\forall c_{1},\dots,c_{n} \in C$
>$$\text{Dec}(c_{1} \circ\dots \circ c_{n})= \text{Dec}(c_{1})\odot\dots\odot\text{Dec}(c_{n})$$
>für beliebig viele $n$.
>
>>[!remark] Bemerkung: Hierbei gilt, dass wir die homomorphe Eigenschaft lediglich bzeüglich einer Operation haben.

>[!def] Definition Teilweise Homomorphe Verschlüsselung
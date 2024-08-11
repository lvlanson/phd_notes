>[!remark]- Bemerkung Vorlesungsstrategie zu den Verschlüsselungsalgorithmen (Informativ)
> Ich möchte an dieser Stelle mit euch teilen, was die Strategie ist, um diese Themen möglichst eingänglich zu bearbeiten. Wir werden noch ein wenig Mathematik leisten müssen, die ich an dieser Stelle nicht mehr als die fundamentalsten Grundlagen betrachte, sondern als schon fortgeschrittenere Konzepte, die wir für die Verschlüsselungsalgorithmen brauchen. 
> 
> Wir werden die Kapitel zu den Verschlüsselungsalgorithmen so gestalten, dass wir uns zunächst das Werkzeug für die Verschlüsselungsalgorithmen vollständig erarbeiten, um dann sauber und ausführlich mit Referenzen die Algorithmen zu beschreiben und deren Korrektheit zu beweisen.

>[!remark]- Bemerkung Geschichte zu RSA (Informativ)
> Das [[../../PDFs/rivest1978a.pdf|RSA]] Verschlüsselungsverfahren wurde 1978 von den drei Mathematikern **Rivest, Shamir** und **Adleman** veröffentlicht. Diese Veröffentlichung markierte einen Meilenstein in der Kryptologie. Mit der Veröffentlichung von RSA wurde das erste **asymmetrische Verschlüsselungsverfahren veröffentlicht**. In der [[1 -  Einführung#^36fe79|Klassifizierung der kryptografischen Verfahren]] haben wir RSA als eine der großen kryptografischen Klassen gekennzeichnet.
> 
> 1976 haben die Mathematiker Diffie und Hellmann ein Paper (quelle: https://ee.stanford.edu/~hellman/publications/24.pdf) veröffentlicht, indem diese den Bedarf für neue kryptografische Ansätze formuliert haben. Es heißt übersetzt
> 
> ---
> 
> <center>Die Ausdehnung an Anwendungen von Telekommunikationsprozessen <br>haben den Bedarf an neuen Arten kryptographischer Systeme geweckt,<br> die den Bedarf an sicheren Übertragunskanälen für den Schlüsselaustausch  <br>  minimieren sollen und ein Äquivalent einer Signatur zur Verfügung stellen sollen.</center>
> 
> ---
> <p align="right" style="font-family:cursive"><i>Whitfield Diffie, Martin E. Hellmann</i></p>
> 
> In diesem wegweisenden Paper beschreiben die Autoren, dass die zunehmende Verfügbarkeit an leistungsfähigen Computersystemen im kommerziellen Bereich und der damit einhergehenden Zunahme der Kommunikation der Bedarf an passenden Kryptosystemen notwendig sei.
> 
> Bis dahin wurden symmetrische Verfahren zur sicheren Telekommunikation verwendet, die allerdings erfordert, dass der Kommunikationsschlüssel, welcher für die Ver- und Entschlüsselung verwendet wird, über einen sicheren Kanal geteilt wird.
> 
> Zu der Zeit, als sich diese Fragen gestellt wurden, war dies ein herausforderndes Problem. Die Autoren charakterisieren es damit, dass es unverhältnismäßig sei auf analogem Weg Schlüssel auszutauschen, um über Telekommunikation symmetrisch verschlüsselt zu kommunizieren.
> 
> Schon fast visionär beschreiben **Diffie und Hellmann** ein System, wo es ein Schlüsselpaar gibt, wobei einer als $e$ und der andere als $d$ bezeichnet wird. Als Bemerkung, das Paper wurde auf Englisch verfasst und $e$ steht für **Encryption** (Verschlüsselung) und $d$ für **Decryption** (Entschlüsselung). 
> 
> Diffie und Hellmann beschreiben, dass der Verschlüsselungsschlüssel $e$ in einem öffentlich zugänglichen "Fach" allen Teilnehmern zugänglich sein soll, sodass diese damit eine Nachricht $m$ verschlüsseln, also $(e,m) \mapsto c$. Nur der Besitzer des Schlüsselpaars $(e,d)$ und somit Besitzer des geheimen Entschlüsselungsschlüssels $d$ soll in der Lage sein, die originale Nachricht zu rekonstruieren, also $(d,c) \mapsto m$.
>
> Hier wird das erste mal der Begriff des *Public Key Cryptosystem* eingeführt. Es soll nach Diffie und Hellmann folgenden Bedingungen unterliegen
> 1. Sei $E$ ein Verschlüsselungsalgorithmus, $D$ ein Entschlüsselungsalgorithmus, so muss $E^{-1}=D$ sein, also für eine Nachricht $m$ muss gelten $$D(E(m))=m$$
> 2. Für beliebige Schlüssel $(e,d)$ und beliebige Nachrichten $m$ sind die Algorithmen $E$ und $D$ effizient.
> 3. Für nahezu alle Schlüssel $(e,d)$ ist die Entschlüsselung $E$ mit Kenntnis der Verschlüsselung $D$ ohne Kenntnis des geheimen Schlüssels $d$ praktisch nicht berechenbar.
> 4. Für beliebige Schlüssel $(e,d)$ sind die Verknüpfungen von Ver- und Entschlüsselung effizient. 
> 
> Mithilfe und unter Berufung auf die Veröffentlichung von Diffie-Hellman haben **Rivest, Shamir und Adleman** das RSA System entwickelt. 

## 3.1 Mathematische Grundlagen

>[!theorem] Kleiner Satz von Fermat (Sylvia Forman, Agnes M. Rash (auth.) - The Whole Truth About Whole Numbers_ An Elementary Introduction to Number Theory (2015, Springer))
>
> Für jede Primzahl $p$ und jede Zahl $a \in \mathbb{Z}$ mit $\text{ggT}(a,p)=1$ gilt
> $$a^{p-1} \equiv 1 \;\;(\text{mod } p)$$
> oder äquivalent dazu
> $$a^{p} \equiv a \;\;(\text{mod } p)$$
>>[!proof]- Beweis mit vollständiger Induktion
>> Ohne Beschränkung der Allgemeinheit schränken wir ein $a>0$, damit wir den Grundsatz des [[2 - Algebraische und Zahlentheoretische Grundlagen#^f974a9|Prinzips der Vollständigen Induktion]] verwenden können.
>> 
>> Wir verwenden für den Beweis die zweite Kongruenz $a^p \equiv a \;\;(\text{mod } p)$. Für den **Induktionsanfang** haben wir $a_{0}=1$
>> $$1^{p} \equiv 1 \;\;(\text{mod } p) \tag*{$\checkmark$}$$
>> ist eine wahre Aussage für beliebige $p$, da $1^{p-1}=1$.
>> 
>> Im **Induktionsschritt** haben wir $a \mapsto a+1$ und erhalten
>> $$(a+1)^p \equiv a+1 \;\;(\text{mod } p)$$
>> Wir werden $(a+1)^p$ auflösen müssen, dazu verwenden wir den binomischen Lehrsatz. Diesen erwähnen wir kurz an dieser Stelle ohne Beweis
>>>[!theorem] Binomischer Lehrsatz
>>>Für $a,b \in \mathbb{R}$ und $n \in \mathbb{N}$ gilt
>>>$$(a+b)^n=\sum_{k=0}^n\binom{n}{k}a^nb^{n-k} $$
>>>wobei der Binomialkoeffizient definiert ist mit
>>>$$\binom{n}{k}=\frac{n!}{k!(n-k)!}$$
>>
>>Daher können wir $(a+1)^p$ auflösen mit 
>>$$\begin{align}
>> (a+1)^p &\equiv \sum_{k=0}^p\binom{p}{k}a^p &&(\text{mod } p)\\ 
>> &\equiv \underbrace{ \binom{p}{0} }_{ =1 }a^0 + \binom{p}{1}a^1 + \binom{p}{2}a^2 + \dots + \underbrace{ \binom{p}{p} }_{ =1 }a^p \;\;&&(\text{mod } p) \\
>> &\equiv 1 + \underbrace{ \frac{p!}{1!(p-1)!} }_{ =p } a+ \underbrace{ \frac{p!}{2!(p-2)!} }_{ =\frac{p(p-1)}{2} }a^2 + \dots. +a^p &&(\text{mod } p) \\
>> &\equiv 1+pa+ \frac{p(p-1)}{2}a^2+\dots+a^p &&(\text{mod } p)
>>\end{align}$$
>>Da alle Binomialkoeffizienten zwischen $1$ und $a^p$ den Faktor $p$ enthalten sind diese nach [[2 - Algebraische und Zahlentheoretische Grundlagen#^e40f84|Restklassenarithmetik]] kongruent $0$, also
>>$$\begin{align}
>> &\equiv 1 + 0 + 0 +\dots + a^p &&\;\;(\text{mod } p) \\
>> &\equiv 1 + a^p &&\;\;(\text{mod } p) \tag{1}
>>\end{align}$$
>>Unsere **Induktionsbehauptung** besagt $$a^p = a \;\;(\text{mod } p)$$
>>daher können wir die letzte Zeile in Kongruenz $(1)$ vereinfachen als
>>$$ \equiv 1+a \;\;(\text{mod } p)$$
>>Somit haben wir gezeigt, dass der **Induktionsschritt** 
>>$$(a+1)^p \equiv 1+a \;\;(\text{mod } p)$$
>>über die **Induktionsbehauptung** gültig ist und somit unsere Aussage bewiesen ist
>>$$\tag*{$\square$}$$
>
>>[!proof]- Beweis mit Zahlentheorie
>> Nehmen wir folgende Liste an Zahlen
>> $$1 \cdot a, 2 \cdot a, 3 \cdot a, \dots (p-1)\cdot a \tag{1}$$
>> Wir planen nun jede Zahl dieser Liste $\text{ mod } p$ zu rechnen. Wir überlegen wie die Liste sich nach dieser Operation verändern muss.
>> 
>> Unserer Voraussetzung können wir entnehmen, dass $\text{ggT}(a,p)=1$ gilt. Weiterhin wissen wir, dass alle Zahlen kleiner als $p$ per Definition der [[2 - Algebraische und Zahlentheoretische Grundlagen#^966cde|Primzahlen]] zur Primzahl teilerfremd sein müssen. Daher können wir feststellen, dass $p$ keine der obenen genannten ganzzahlig teilt. 
>> 
>> Wir nehmen nun an, dass alle Elemente nach der Operation $\text{ mod }p$ in der Liste verschiene Elemente erzeugt, da wir $p-1$ Elemente haben und alle teilerfremd zu $p$ sind erwarten wir 
>> $$1,2,3,\dots,(p-1) \tag{2}$$
>> Um dies zu zeigen, gehen wir davon aus, dass es angenommen zwei Elemente aus Liste $(1)$ gibt, die gleich sind. Also es seien $k,m \in \{ 1,\dots,(p-1) \}$ mit 
>> $$k \neq m \tag{3}$$
>> und wir behaupten, es gäbe demzufolge
>> $$k\cdot a \equiv m \cdot a \;\;(\text{mod } p)$$ 
>> Laut der [[2 - Algebraische und Zahlentheoretische Grundlagen#^360a7d|Kongruenz Äquivalenzrelation]] können wir diese Kongruenz ausdrücken als
>> $$\begin{align}
>> k\cdot a\equiv m\cdot a \;\;(\text{mod } p) &\iff p\;|\; k\cdot a - m\cdot a \\
>> &\iff p \;|\; a \cdot(k-m)
>>\end{align}$$
>>Nach dem [[2 - Algebraische und Zahlentheoretische Grundlagen#^f65359|Satz der Primzahlquotienten]] muss einer der Faktoren von $p$ teilbar sein. Da unserer Voraussetzungen nach $\text{ggT}(a,p)=1$, also $p\nmid a$, muss demzufolge $p \;|\; (k-m)$ dann gelten, wenn es angenommen zwei gleiche Zahlen gäbe. Von $p \;|\; (k-m)$ können wir über die [[2 - Algebraische und Zahlentheoretische Grundlagen#^360a7d|Kongruenz Äquivalenzrelation]] rückschließen, dass
>>$$k \equiv m \;\;(\text{mod } p)$$
>> was ein Widerspruch zu unserer Behauptung $(3)$ ist. Daher muss die Liste $(2)$ entstehen, wenn wir Liste $(1)$ $\text{ mod } p$ rechnen. Daher können wir behaupten, wenn wir jeweils die Elemente der Listen miteinander multiplizieren
>> $$(1 \cdot a)(2 \cdot a)(3 \cdot a)\dots((p-1)\cdot a) \equiv 1 \cdot 2 \cdot 3 \dots (p-1) \;\;(\text{mod } p)$$
>> Wenn wir auf der linken Seite alle $a$ aufmultiplizieren und dazu bemerken, dass diese Produkte die Fakultäten $(p-1)!$ sind, erhalten wir
>> $$a^{p-1}(p-1)! \equiv (p-1)! \;\;(\text{mod }  p) \tag{4}$$
>> Da $p$ eine Primzahl ist und alle Faktoren $b$ in $(p-1)!$ kleiner als $p$ sind mit $\text{ggT}(p,b)=1$, wissen wir, dass das modulare Inverse für jeden Faktor $b$ laut [[2 - Algebraische und Zahlentheoretische Grundlagen#^c7c061| dem Satz der Existenz des modularen Inversen]] existieren muss.
>> 
>> Tatsächlich ist jedes $b \in \{ 1,2,3,\dots,p-1 \}$ sein eigenes [[2 - Algebraische und Zahlentheoretische Grundlagen#^6f68c0|modulares Inverses]] bezüglich Modulo $p$, was wir schnell zeigen werden.
>>>[!proof]- Zwischenbeweis 
>>>Wir zeigen für eine Primzahl $p$
>>>$$ b \text{ ist sein eigenes modulares Inverses,}$$
>>>$$\underbrace{ \text{genau dann wenn } }_{ \iff } b \equiv 1 \;\;(\text{mod } p) \text{ oder } b \equiv p-1 \;\;(\text{mod } p)$$
>>>Wir zeigen beide Richtungen der Äquivalenz ($\iff$). Wir starten mit
>>>
>>>1. ($\implies$), sei $p$ Primzahl
>>>
>>>---
>>>
>>>$$b^2\equiv 1\;\;(\text{mod } p)\implies b \equiv 1\;\;(\text{mod } p) \lor b \equiv p-1 \;\;(\text{mod } p)$$
>>>
>>>---
>>> An dieser Stelle haben wir bereits die Aussage, dass $b$ sein eigenes Inverses ist, umformuliert zu
>>> $$\begin{align}
>>> b \cdot b &\equiv 1 &&\;\;(\text{mod } p) \\
>>> b^2 &\equiv 1 &&\;\;(\text{mod } p) \\
>>> b^2 -1 &\equiv 0 &&\;\;(\text{mod } p) \\
>>> (b+1)(b-1) &\equiv 0 &&\;\;(\text{mod } p) \\
>>>\end{align}$$
>>>Da der Rest $0$ ist, ist das äquivalent zur Aussage $p \;|\;(b+1)(b-1)$. Damit diese wahr ist, muss laut [[2 - Algebraische und Zahlentheoretische Grundlagen#^f65359|dem Satz des Primzahlquotienten]] 
>>>$$p \;|\; (b+1)(b-1) \implies \underbrace{ p\;|\;(b+1) }_{ (1) } \lor \underbrace{ p \;|\;(b-1) }_{ (2) }$$
>>>Das heißt, eine der beiden Teilungen muss wahr sein, demzufolge für den Fall $(2)$, also $p \;|\;(b-1)$ haben wir
>>>$$\begin{align}
>>> b -1 &\equiv 0 &&\;\;(\text{mod } p) \\
>>> b &\equiv 1 && \;\;(\text{mod } p)
>>>\end{align}$$
>>>
>>>Für den anderen Fall $(1)$ bemerken wir vorab, dass $p \equiv 0 \;\;(\text{mod } p)$ generell gilt, also stellen wir fest für $p \;|\;(b+1)$
>>>
>>>$$\begin{align}
>>> b+1 &\equiv 0 &&\;\;(\text{mod } p) \\
>>> b &\equiv -1 &&\;\;(\text{mod } p) \\
>>> b & \equiv 0 - 1 && \;\;(\text{mod } p) \\
>>> b & \equiv p -1 && \;\;(\text{mod } p)
>>>\end{align}$$
>>>
>>> Wir haben jetzt erfolgreich eine Richtung der Äquivalenz gezeigt ($\implies$), wir müssen nun zeigen, dass wir auch in die andere Richtung schließen können ($\Longleftarrow$), also
>>> 
>>> 2. ($\Longleftarrow$)
>>> 
>>> ---
>>>
>>>$$b \equiv 1\;\;(\text{mod } p) \lor b \equiv p-1 \;\;(\text{mod } p)\implies b^2 \equiv 1 \;\;(\text{mod } p)$$
>>>
>>>---
>>>
>>>Wir starten bei
>>>$$\begin{align}
>>> b &\equiv 1 &&\;\;(\text{mod } p) \qquad&&\Big\vert (\cdot)^2  \\
>>> b^2 &\equiv 1^2 &&\;\;(\text{mod } p) \\
>>> b^2 &\equiv 1 &&\;\;(\text{mod } p) \\
>>>\end{align}$$
>>>daher folgt, dass wenn $b \equiv 1 \;\;(\text{mod } p)$ dass $b$ sein eigenes modulares Inverses sein muss.
>>>
>>>Wir setzen fort mit 
>>>$$\begin{align}
>>> b &\equiv p-1 &&\;\;(\text{mod } p) \\
>>> b &\equiv -1 && \;\;(\text{mod } p) \qquad&&\Big\vert (\cdot)^2 \tag{3} \\ 
>>> b^2 &\equiv 1 &&\;\;(\text{mod } p)
>>>\end{align}$$
>>>
>>>Zeile $(3)$ kommt daher zustande, da durch [[2 - Algebraische und Zahlentheoretische Grundlagen#^a40b0b| den Satz der Teilbarkeit von Summen und Differenzen]] wieder $p \equiv 0 \;\;(\text{mod } p)$ gilt.
>>>
>>>---
>>>
>>>Somit sind beide Richtungen der Äquivalenz gezeigt und die Aussage bestätigt. $$\tag*{$\square$}$$
>>
>>Da dies durch den Zwischenbeweis zweifelsfrei verwendet werden kann, können wir einfach beide Seiten mit den Faktoren $(p-1)!$ multiplizieren und alle Faktoren so paaren, dass diese sich mit ihrem modularen Inversen aufheben, also
>>$$\begin{align}
>> a^{p-1}(p-1)! &\equiv (p-1)! &&\;\;(\text{mod }  p) \qquad&&\Big\vert \cdot(p-1)! \\
>> a^{p-1}\underbrace{ (1\cdot1) }_{ \equiv 1 }\underbrace{ (2\cdot 2) }_{ \equiv 1 }\dots\underbrace{ \Big((p-1)(p-1)\Big) }_{ \equiv 1 } &\equiv \underbrace{ (1\cdot1) }_{ \equiv 1 }\underbrace{ (2\cdot 2) }_{ \equiv 1 }\dots\underbrace{ \Big((p-1)(p-1)\Big) }_{ \equiv 1 } &&\;\;(\text{mod }  p)  \\ 
>> a^{p-1} &\equiv 1 && \;\;(\text{mod } p)
>>\end{align}$$
>>was es zu zeigen galt.
>>$$\tag*{$\square$}$$
>
>>[!example]- Beispiel $a= 2$ und $p=3$
>>$$\begin{align}
>> 2^{3-1} &\equiv 1 &&\;\;(\text{mod } 3) \\
>> 2^2 &\equiv 1 &&\;\;(\text{mod } 3) \\
>> 4 &\equiv 1 &&\;\;(\text{mod }  3) \\
>> 1 &\equiv 1 &&\;\;(\text{mod } 3) \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!example]- Beispiel $a = 34$ und $p=3$
>> $$\begin{align}
>> 34^{3-1} &\equiv 1&&\;\;(\text{mod } 3) \\
>> 34^{2} &\equiv 1&&\;\;(\text{mod } 3) \\
>> \underbrace{ 34 }_{ \equiv 1 } \cdot \underbrace{ 34 }_{ \equiv 1 } &\equiv 1&&\;\;(\text{mod } 3) \\
>> 1 \cdot 1 &\equiv 1&&\;\;(\text{mod } 3) \\
>> 1 &\equiv 1&&\;\;(\text{mod } 3) \\
>>\end{align}$$ 
>
>>[!remark]- Bemerkung zur Person Pierre de Fermat (Informativ)
>>Entgegen der Erwartung handelt es sich bei Fermat nicht um einen klassischen Mathematiker. Fermat lebte von 1601-1665 in Frankreich und war ein Staatsbediensteter, der als Hofrat und ebenfalls in der Justiz als Richter im Einsatz war. Man nannte Fermat auch den *Fürsten der Amateure* im Hinblick auf seine mathematischen Tätigkeiten, da er Mathematik mehr oder minder nur in seiner Freizeit als ambitioniertes Hobby betrieb.
>>
>>![[Figures/fermat.png|center|180]]
>><center>Abbildung: Portrait von Fermat</center>
>>
>>Fermat hatte regelmäßig Kontakt zu einem Zahlentheoretiker seiner Zeit (Pater Mersenne) und beschäftigte sich daneben auch mit dem Werk *Arithmetica* eines wohlbekannten griechischen Mathematikers Diophantos von Alexandria. Während er dieses Werk las und bearbeitete, inspirierte es Fermat neue Sätze zu entwickeln. Diese Sätze versandte Fermat in Briefform an professionelle Mathematiker seiner Zeit ohne einen Beweis anzuhängen, mit dem neckischen Hinweis doch den Beweis für seine Aussage zu finden. 
>>
>> ![[Figures/arithmetika.png|center|250]]
>> <center> Abbildung: Cover des Buches Arithmetica</center>
>>
>>Dies war eine Provokation an seine professionellen Kollegen, die das natürlich nicht auf sich sitzen lassen konnten. Nicht selten kamen diese Briefe mit dem Hinweis, dass die Beweise doch offensichtlich seien. Der Philisoph Renè Descartes nannte Fermat einen *Aufschneider* und der Engländer John Wallis bezeichnete ihn als *den verdammten Franzosen*.
>>
>>Der wohl berühmteste Satz ist Fermat's letzter Satz, welcher die Mathematik ca. 350 Jahre in Rätsel stürzte. Er ist simpel auszudrücken. Für ganze positive Zahlen $a,b,c,n$ 
>>$$a^n+b^n = c^n$$
>>gibt es keine Lösung, wenn $n>2$. Fermat behauptete, dass er einen *wahrhaft wunderbaren* Beweis wisse. Diese Hinweis hat man als Randnotiz in seiner Ausgabe der Arithmetica gefunden. Fermat hatte seiner Zeit viele Behauptungen aufgestellt und kein Interesse gehabt nachhaltig die Erkenntnisse für die Nachwelt festzuhalten. Nach seinem Tod haben Mathematiker seine Behauptungen gesammelt und sukzessive nachgewiesen oder auch widerlegt. Fermat's letztes Satz hat sich jedoch als die härteste aller Aussagen gezeigt und hat Größen wie beispielsweise Euler verzweifeln lassen.
>>
>>Andrew Wiles hat 1993 diesen Satz in einem 200 seitigen Beweis nachgewiesen. Dieser Beweis beinhaltete Erkenntnisse und Methoden, die der Mathematikwelt bis zu dem Zeitpunkt völlig unbekannt waren und hat Gebiete der Mathematik verbunden, deren Verbindung nicht vorstellbar war. Neckisch seiner Natur hat er 350 Jahre noch professionelle Mathematiker nach seinem Tod mit seinen Satz geplagt.
>>
>>Fermat war und anderem mit *Blaise Pascal* Mitbegründer der Wahrscheinlichkeitsrechnung.
>>
>>- Literaturempfehlung: Fermat's Letzter Satz von Simon Singh
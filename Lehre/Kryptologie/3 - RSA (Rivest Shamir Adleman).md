>[!remark]- Bemerkung Vorlesungsstrategie zu den Verschlüsselungsalgorithmen (Informativ)
> Ich möchte an dieser Stelle mit euch teilen, was die Strategie ist, um diese Themen möglichst eingänglich zu bearbeiten. Wir werden noch ein wenig Mathematik leisten müssen, die ich an dieser Stelle nicht mehr als die fundamentalsten Grundlagen betrachte, sondern als schon fortgeschrittenere Konzepte, die wir für die Verschlüsselungsalgorithmen brauchen. 
> 
> Wir werden die Kapitel zu den Verschlüsselungsalgorithmen so gestalten, dass wir uns zunächst das Werkzeug für die Verschlüsselungsalgorithmen vollständig erarbeiten, um dann sauber und ausführlich mit Referenzen die Algorithmen zu beschreiben und deren Korrektheit zu beweisen.

>[!remark]- Bemerkung Geschichte zu RSA (Informativ)
> Das [[../../PDFs/rivest1978a.pdf|RSA]] Verschlüsselungsverfahren wurde 1978 von den drei Mathematikern **Rivest, Shamir** und **Adleman** veröffentlicht. Diese Veröffentlichung markierte einen Meilenstein in der Kryptologie. Mit der Veröffentlichung von RSA wurde das erste **asymmetrische Verschlüsselungsverfahren veröffentlicht**. In der [[1 -  Einführung#^36fe79|Klassifizierung der kryptografischen Verfahren]] haben wir RSA als eine der großen kryptografischen Klassen gekennzeichnet.
> 
> 1976 haben die Mathematiker Diffie und Hellmann ein Paper ([[../../PDFs/diffie1976.pdf|Quelle]]) veröffentlicht, indem diese den Bedarf für neue kryptografische Ansätze formuliert haben. Es heißt übersetzt
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

^7402b5

## 3.1 Mathematische Grundlagen

>[!theorem] Kleiner Satz von Fermat ([[../../PDFs/forman2015.pdf#page=223|Quelle]])
>
> Für jede Primzahl $p$ und jede Zahl $a \in \mathbb{Z}$ mit $a \neq 0$ und $\text{ggT}(a,p)=1$ gilt
> $$a^{p-1} \equiv 1 \;\;(\text{mod } p)$$
> oder äquivalent dazu
> $$a^{p} \equiv a \;\;(\text{mod } p)$$
>>[!proof]- Beweis mit vollständiger Induktion
>> Ohne Beschränkung der Allgemeinheit schränken wir ein $a>0$, damit wir den Grundsatz des [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^f974a9|Prinzips der Vollständigen Induktion]] verwenden können.
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
>>Da alle Binomialkoeffizienten zwischen $1$ und $a^p$ den Faktor $p$ enthalten sind diese nach [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^e40f84|Restklassenarithmetik]] kongruent $0$, also
>>$$\begin{align}
>> &\equiv 1 + 0 + 0 +\dots + a^p &&\;\;(\text{mod } p) \\
>> &\equiv 1 + a^p &&\;\;(\text{mod } p) \tag{1}
>>\end{align}$$
>>Unsere **Induktionsbehauptung** besagt $$a^p = a \;\;(\text{mod } p)$$
>>daher können wir die letzte Zeile in Kongruenz $(1)$ vereinfachen als
>>$$ \equiv 1+a \;\;(\text{mod } p)$$
>>Somit haben wir gezeigt, dass der **Induktionsschritt** 
>>$$(a+1)^p \equiv a+1 \;\;(\text{mod } p)$$
>>über die **Induktionsbehauptung** gültig ist und somit unsere Aussage bewiesen ist
>>$$\tag*{$\square$}$$
>
>>[!proof]- Beweis mit Zahlentheorie
>> Nehmen wir folgende Liste an Zahlen
>> $$1 \cdot a, 2 \cdot a, 3 \cdot a, \dots (p-1)\cdot a \tag{1}$$
>> Wir planen nun jede Zahl dieser Liste $\text{ mod } p$ zu rechnen. Wir überlegen wie die Liste sich nach dieser Operation verändern muss.
>> 
>> Unserer Voraussetzung können wir entnehmen, dass $\text{ggT}(a,p)=1$ gilt. Weiterhin wissen wir, dass alle Zahlen kleiner als $p$ per Definition der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^966cde|Primzahlen]] zur Primzahl teilerfremd sein müssen. Daher können wir feststellen, dass $p$ keine der obenen genannten ganzzahlig teilt. 
>> 
>> Wir nehmen nun an, dass alle Elemente nach der Operation $\text{ mod }p$ in der Liste verschiene Elemente erzeugt, da wir $p-1$ Elemente haben und alle teilerfremd zu $p$ sind erwarten wir 
>> $$1,2,3,\dots,(p-1) \tag{2}$$
>> Um dies zu zeigen, gehen wir davon aus, dass es angenommen zwei Elemente aus Liste $(1)$ gibt, die gleich sind. Also es seien $k,m \in \{ 1,\dots,(p-1) \}$ mit 
>> $$k \neq m \tag{3}$$
>> und wir behaupten, es gäbe demzufolge
>> $$k\cdot a \equiv m \cdot a \;\;(\text{mod } p)$$ 
>> Laut dem Satz der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Kongruenzen]] können wir diese Kongruenz ausdrücken als
>> $$\begin{align}
>> k\cdot a\equiv m\cdot a \;\;(\text{mod } p) &\iff p\;|\; k\cdot a - m\cdot a \\
>> &\iff p \;|\; a \cdot(k-m)
>>\end{align}$$
>>Nach dem [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^f65359|Satz der Primzahlquotienten]] muss einer der Faktoren von $p$ teilbar sein. Da unserer Voraussetzungen nach $\text{ggT}(a,p)=1$, also $p\nmid a$, muss demzufolge $p \;|\; (k-m)$ dann gelten, wenn es angenommen zwei gleiche Zahlen gäbe. Von $p \;|\; (k-m)$ können wir über den Satz der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Kongruenzen]] rückschließen, dass
>>$$k \equiv m \;\;(\text{mod } p)$$
>> was ein Widerspruch zu unserer Behauptung $(3)$ ist. Daher muss die Liste $(2)$ entstehen, wenn wir Liste $(1)$ $\text{ mod } p$ rechnen. Daher können wir behaupten, wenn wir jeweils die Elemente der Listen miteinander multiplizieren
>> $$(1 \cdot a)(2 \cdot a)(3 \cdot a)\dots((p-1)\cdot a) \equiv 1 \cdot 2 \cdot 3 \dots (p-1) \;\;(\text{mod } p)$$
>> Wenn wir auf der linken Seite alle $a$ aufmultiplizieren und dazu bemerken, dass diese Produkte die Fakultäten $(p-1)!$ sind, erhalten wir
>> $$a^{p-1}(p-1)! \equiv (p-1)! \;\;(\text{mod }  p) \tag{4}$$
>> Da $p$ eine Primzahl ist und alle Faktoren $b$ in $(p-1)!$ kleiner als $p$ sind mit $\text{ggT}(p,b)=1$, wissen wir, dass das modulare Inverse für jeden Faktor $b$ laut [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^c7c061| dem Satz der Existenz des modularen Inversen]] existieren muss.
>> 
>> Tatsächlich ist jedes $b \in \{ 1,2,3,\dots,p-1 \}$ sein eigenes [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^6f68c0|modulares Inverses]] bezüglich Modulo $p$, was wir schnell zeigen werden.
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
>>>Da der Rest $0$ ist, ist das äquivalent zur Aussage $p \;|\;(b+1)(b-1)$. Damit diese wahr ist, muss laut [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^f65359|dem Satz des Primzahlquotienten]] 
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
>>>Zeile $(3)$ kommt daher zustande, da durch [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^a40b0b| den Satz der Teilbarkeit von Summen und Differenzen]] wieder $p \equiv 0 \;\;(\text{mod } p)$ gilt.
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
>>gibt es keine Lösung, wenn $n>2$. Fermat behauptete, dass er einen *wahrhaft wunderbaren* Beweis wisse. Diese Hinweise hat man als Randnotiz in seiner Ausgabe der Arithmetica gefunden. Fermat hatte seiner Zeit viele Behauptungen aufgestellt und kein Interesse gehabt nachhaltig die Erkenntnisse für die Nachwelt festzuhalten. Nach seinem Tod haben Mathematiker seine Behauptungen gesammelt und sukzessive nachgewiesen oder auch widerlegt. Fermat's letztes Satz hat sich jedoch als die härteste aller Aussagen gezeigt und hat Größen wie beispielsweise Euler verzweifeln lassen.
>>
>>Andrew Wiles hat 1993 diesen Satz in einem 200 seitigen Beweis nachgewiesen. Dieser Beweis beinhaltete Erkenntnisse und Methoden, die der Mathematikwelt bis zu dem Zeitpunkt völlig unbekannt waren und hat Gebiete der Mathematik verbunden, deren Verbindung nicht vorstellbar war. Neckisch seiner Natur hat er 350 Jahre noch professionelle Mathematiker nach seinem Tod mit seinen Satz geplagt.
>>
>>Fermat war und anderem mit *Blaise Pascal* Mitbegründer der Wahrscheinlichkeitsrechnung.
>>
>>- Literaturempfehlung: Fermat's Letzter Satz von Simon Singh

^5e7c61

>[!def] Definition Euler'sche Phi-Funktion ([[../../PDFs/forman2015.pdf#page=229|Quelle]])
> Sei $n \in \mathbb{N}$
> $$\phi(n):= \# \{ k \in \mathbb{N} \;|\; k \leq n \text{ und } \text{ggT}(k,n)=1\}$$
>>[!remark]- Bedeutung
>>Die Euler'sche Phi-Funktion zählt alle zu $n$ teilerfremden Zahlen, die inklusiv zwischen $1$ und $n$ liegen.
>
>>[!example]- Beispiel $\phi(4)$
>>$$\begin{align}
>> \phi(4)&=\#\{ 1,3 \} \\
>> &= 2
>>\end{align}$$
>
>>[!example]- Beispiel $\phi(11)$
>>$$\begin{align}
>> \phi(11) &= \# \{ 1,2,3,4,5,6,7,8,9,10 \} \\
>> &= 10
>>\end{align}$$
>
>>[!remark]- Bemerkung zur Person Leonhard Euler (Informativ)
>>Leonhard Euler ist ein in der Schweiz geborener Mathematiker, der von 1707-1783 lebte. In seinen ersten zwanzig Lebensjahren bildete er sich in den Bereichen der Theologie, Medizin, Astronomie, Physik, orientalische Sprachen und auch Mathematik in Basel. Er schloss sein Universitätsstudium mit einem Masterabschluss im Alter von 17 Jahren. Zu damaligen Zeiten war *Mathematiker* kein sicheres Berufsfeld, vor allem nicht die theoretische Mathematik. Daher gestaltete sich seine Berufswahl als schwierig. 
>>
>>![[Figures/euler_1.png|center|500]]
>><center>Abbildung: Porträt von Euler (1753)</center>
>>
>>Während seine damaligen Lehrer und Freunde als Mathematiker nach St. Petersburg in Russland zogen, wurde Euler als Mitglied der medizinischen und physiologischen Teilen der Akademie aufgenommen. Seine Freunde die *Bernoullis* haben ihn vor Ort empfohlen, weshalb er dort seine Position antreten konnte. Am Tag seiner Ankunft wurde der Tod der damaligen Zarin und Stifterin der Akademie Katharina I. bekannt gegeben, weshalb viel Unruhe in der Stadt St. Petersburg war. Euler wurde daraufhin nicht wie geplant in die medizinische Fakultät, sondern in die mathematische Fakultät gesetzt.
>>
>>Nach kurzen Exkursen in die Naturphilosophie wurde Euler mit 26 Jahren höchstrangige Mathematiker an der Akademie in S.t Petersburg. Spätere politische Unruhen und das Abwerben des damaligen Königs Friedrich II. brachten ihn an die königlich preußische Akademie der Wissenschaften zu Berlin. Euler war zu dem Zeitpunkt 33 Jahre alt. Unstimmigkeiten an der Berliner Akademie und Krieg sorgten dafür, dass es Katharina der Großen gelang Euler zurück nach St. Petersburg zurück zu werben. Er wurde dort zum Hofmathematiker ernannt. Zu dem Zeitpunkt war er 59 Jahre alt. Er forschte und lebte dort bis zu seinem Tod 1783 im Alter von 76 Jahren.
>>
>>![[Figures/euler_2.png|center|500]]
>><center>Abbildung: Porträt Euler von Joseph Frédéric Auguste Darbès (1778)</center>
>>
>>Euler hatte recht früh mit Problemen seiner Sehkraft zu kämpfen. 1766 war er nahezu erblindet. Damit er weiter Bücher und Artikel schreiben konnte, hatte er die Hilfe eines Assistenten, sodass er noch 1770 eines seiner bedeutendsten Werke zur Lehre veröffentlichte: *Vollständige Anleitung zur Algebra*.
>>
>>Ein akademischer Kollege schrieb zu Euler,
>>
>>---
>>
>> <center>So wie Menschen atmen, so wie Adler sich in der Luft halten, so rechnet Euler ohne ersichtliche Mühe.</center>
>> 
>>---
>><p align="right" style="font-family:cursive"><i>François Arago</i></p>
>>
>>Euler hat zeit seines Lebens über 500 Bücher und Veröffentlichungen geschrieben. Selbst 50 Jahre nach seinem Tod sind noch sukzessive Artikel von ihm erschienen, sodass die Liste an Veröffentlichungen auf 886 angestiegen ist. Er hat jedes Jahr im Schnitt 800 Seiten geschrieben. Kein anderer Mathematiker hat jemals vergleichbar viel, und zudem auch noch bedeutende Veröffentlichungen geleistet.

^f287d3

>[!theorem] Satz Euler'sche Phi-Funktion von Primzahlen
>Sei $p$ eine Primzahl, dann gilt
>$$\phi(p)=p-1$$
>
>>[!example] Übung: Beweisen Sie die Aussage.
>

^481d74

<!--
>[!theorem] Satz Euler'sche Phi-Funktion von Primzahlpotenzen
>Sei $p$ eine Primzahl und $a \in \mathbb{N}$, dann gilt
>$$\phi(p^a)= p^a-p^{a-1}$$
>
>>[!proof]- Beweis
>>Wir bezeichnen $n=p^a$. Laut dem [[2 - Algebraische und Zahlentheoretische Grundlagen|Fundamentalsatz der Algebra]] wissen wir, dass die einzigen Faktoren in $n$ die Primzahl $p$ ist. Daher können nur Vielfache von $p$ einen gemeinsamen Teiler haben, also
>>$$\text{ggT}(p^a, k \cdot p) = p$$
>>für $k \in \mathbb{N}$. Genau genommen existieren maximal $a-1$ verschiedene Zahlen, die sich mit $p$ zusammensetzen lassen sodass $k \cdot p \leq p^a$ ist, also
>>$$1 \cdot p, \;2\cdot p,\;3 \cdot p,\; 4 \cdot p,\; \dots\;,\; \underbrace{ p^{a-1}\cdot p }_{ =p^a }$$
>>Alle anderen müssen teilerfremd zu $p^a$ sein, daher ziehen wir die $p^{a-1}$ gefundenen Zahlen ab, also
>>$$\phi(p^a)=p^a-p^{a-1}$$
-->

>[!theorem] Satz Euler'sche Phi-Funktion des Produkts von zwei Primzahlen
>Seien $p,q \in \mathbb{Z}$  Primzahlen, dann gilt
>$$\phi(p \cdot q)= \phi(p)\cdot \phi(q)=(p-1)(q-1)$$
>>[!proof]- Beweis
>>Wir wissen, dass es maximal $n=p\cdot q$ Zahlen gibt, die zwischen $1$ und $p \cdot q$ liegen. Daher ist unsere Strategie die Zahlen zu zählen, die $p \cdot q$ teilen und diese Anzahl von $n$ abzuziehen.
>>
>>Da sowohl $p$ und $q$ Primzahlen sind, kann $n$ nur mit Vielfachen von jeweils $p$ und $q$ gemeinsame Teiler haben. Die Zahl $n=p \cdot q$ muss gemeinsame Teiler mit folgenden Zahlen haben
>>$$\begin{align}
>> 1p,\;2p\;,\;3p\;,\;\dots\;,\;q\cdot p \tag{$p$ verschiedene}\\
>> 1q,\;2q\;,\;3q\;,\;\dots\;,\;p\cdot q \tag{$q$ verschiedene}\\
>>\end{align}$$
>>Wir bemerken, dass $q \cdot p$ zwei mal gezählt wird. Daher sind das 
>>$$q + p - 1$$
>>verschiedene Zahlen, wenn wir das doppelte Element $q \cdot p$ einmal abziehen. Diese Anzahl ziehen wir nun von der Gesamtmöglichen Anzahl $n=p \cdot q$ ab, also
>>$$\begin{align}
>> \phi(p \cdot q) &= pq - (q+p-1) \\
>>  &= pq - q-p+1 \\ 
>> &= (p-1)(q-1)
>>\end{align}$$
>>Laut dem [[#^481d74|Satz der Euler'schen Phi-Funktion von Primzahlen]] können wir das darstellen als
>>$$\phi(p \cdot q) = \phi(p) \cdot \phi(q)$$
>>was es zu zeigen galt. $$\tag*{$\square$}$$


## 3.2 Das RSA Verfahren

>[!remark] Bemerkung: Struktur der Verfahren
>Wir werden die Verfahren einteilen in
> - Schlüsselerzeugung
> - Verschlüsselung/Entschlüsselung/Signatur
> - Korrektheitsnachweis

>[!algo] Kryptografisches Verfahren: RSA
>
>>[!schlüsselerzeugung]
>>
>>1. Bob wählt zwei große Primzahlen $p$ und $q$
>>2. Bob berechnet $$\begin{align}
>> n &=pq \tag{Modul}\\
>> \phi(n)&=(p-1)(q-1) \tag{Phi-Funktion}
>>\end{align}$$
>>3. Bob löscht $p$ und $q$
>>4. Bob wählt $$e \in \mathbb{N} \tag{Encryption-Key}$$ mit den Bedingungen $$\begin{align}
>>&(1)&&1 < e < \phi(n)  \\
>>&(2)&&\text{ggT}\big(e, \phi(n)\big) = 1
>>\end{align}$$
>>5. Bob teilt seinen **öffentlichen Schlüssel** $(n,e)$ mit
>>6. Bob berechnet $$d \in \mathbb{N} \tag{Decryption-Key}$$ mit $$\begin{align}
>> &(1) &&1<d<\phi(n) \\
>> &(2) && ed \equiv 1 \;\;(\text{mod } \phi(n)) \tag{Modulares Inverses}
>>\end{align}$$
>>7. Bob löscht $\phi(n)$ und hält seinen **privaten Schlüssel** $(n,d)$ geheim
>
>>[!verschlüsselung] 
>> Sei 
>> - $m \in \mathbb{Z}_{n}$ - zu verschlüsselnde Nachricht
>> - $(n,e)$ - öffentlicher Schlüssel
>> - $(n,d)$ - privater/geheimer Schlüssel
>>
>> **<u>Verschlüsselung</u>**:
>> $$c = m^e \text{ mod }n$$
>> Wir nennen $c \in \mathbb{Z}_{n}$ die Chiffre.
>> 
>> **<u>Entschlüsselung</u>**:
>> $$m = c^{d} \text{ mod }n$$
>
>>[!korrektheitsnachweis]
>>
>>Wir wollen zeigen, dass wenn wir eine Nachricht $0  \leq m <n$ ver- und entschlüsseln, dass wir dann dieselbe Nachricht wieder erhalten. Dies ist der Ausgangspunkt für Korrektheitsnachweise von Verschlüsselungsverfahren.
>>
>>Wir wissen, wenn wir eine Nachricht ver- und entschlüsseln, haben wir
>>$$\begin{align}
>> c &= m^e \text{ mod }n \tag{}\\
>> m &= c^{d} \text{ mod }n 
>>\end{align}$$
>>kombiniert ergibt das
>>$$\begin{align}
>> m &= (m^e)^d \text{ mod } n \\
>> m &= m^{ed} \text{ mod } n
>>\end{align}$$
>>Wir wechseln an dieser Stelle die Schreibweise von dem [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^9cd06c| binären Modulus]] zur [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^360a7d|Kongruenz]], da ohnehin verlangt ist, dass $m \in \mathbb{Z}_{n}$ liegen muss, also
>>$$m \equiv m^{ed} \;\;(\text{mod } n)$$
>>Wir beginnen damit zu argumentieren, weshalb es genügt die Kongruenz bezüglich einer der beiden Primzahlen $p,q$ statt für $n$ zu zeigen. Zunächst zum Zweck des einfacheren Verständnisses formulieren wir die Kongruenz um, indem wir alle Argumente auf eine Seite ziehen, also
>>$$m - m^{ed} \equiv 0\;\;(\text{mod } n)$$
>>Wir wissen, dass wenn der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^9cd06c|Rest]] $0$ ist bezüglich $n$, dass die Teilung aufgeht, also
>>$$n \;|\; m-m^{ed}$$
>>Aus der Verfahrensbeschreibung wissen wir, dass $n=p\cdot q$ ist. Wegen des [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^3dda16|Lemmas der Teilbarkeit über Primfaktoren]] können wir schließen
>>$$\begin{align}
>> n \;|\; m-m^{ed} &\iff p \cdot q \;|\; m-m^{ed}  \\
>> &\iff p \;|\; m-m^{ed} \land q \;|\; m-m^{ed}
>>\end{align}$$
>>Für $p$ können wir daher sagen
>>$$\begin{align}
>> m - m^{ed} &\equiv 0 &&\;\;(\text{mod } p) \\
>> m &\equiv m^{ed} &&\;\;(\text{mod } p) \tag{1}
>>\end{align}$$
>>
>> Es genügt die Aussage für $p$ zu zeigen, da diese auch für $q$ gilt, da beides Primzahlen sind und die Eigenschaften der Primzahlen hier maßgeblich für den Nachweis entscheidend sind. 
>> 
>> Zunächst prüfen wir den Sonderfall $m=0$.
>> $$0 \equiv 0^{ed} \;\;(\text{mod } p)$$
>> Dies scheint auf den ersten Blick offensichtlich wahr. Wir sollten aber bedenken, dass für den Fall $ed = 0$ die Aussage falsch wäre, da $0^0 = 1$. Jedoch sind $e,d>1$, daher kann der Fall nicht eintreten. Wir prüfen den Fall $m=0$ an dieser Stelle, da wir im verbleibenden Beweis den [[#^5e7c61|kleinen Satz von Fermat]] verwenden werden und dafür $m \neq 0$ gelten muss.
>> 
>> Wir setzen als den Beweis fort für $1 \leq m < n$. In Kongruenz $(1)$ wollen wir den Term $ed$ im Exponenten auflösen. Wir erinnern uns an die Schlüsselerzeugung unter 6.2, wo $ed$ beschrieben ist als
>> $$\begin{align}
>> ed &\equiv 1 &&\;\;(\text{mod } \phi(n)) \qquad&&\Big\vert -1 \\ 
>> ed -1 &\equiv 0 &&\;\;(\text{mod } \phi(n))
>>\end{align}$$
>>Da der Rest $0$ ist wissen wir wieder
>>$$\phi(n) \;|\; ed-1$$
>>Daher [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^9380e8|existiert nach der ganzzahligen Teilung]] eine ganze Zahl $k \in \mathbb{Z}$, sodass
>>$$\begin{align}
>>  ed - 1&= k \cdot \phi (n) \qquad&&\Big\vert +1 \\
>>  ed &=k \cdot \phi (n)+1 
>>\end{align}$$
>>Wir setzen nun den gefundenen Ausdruck in Kongruenz $(1)$ ein und erhalten
>>$$\begin{align}
>> m &\equiv m^{ed} &&\;\;(\text{mod } p) \\
>> m &\equiv m^{k \cdot \phi(n) + 1} &&\;\;(\text{mod } p) \\
>> m &\equiv m^{k \cdot \phi(n)} \cdot m^1 &&\;\;(\text{mod } p) \\
>>\end{align}$$
>>Wir erinnern uns, dass $\phi(n)=(p-1)(q-1)$ unter 2. in der Schlüsselerzeugung definiert wurde. Daher setzen wir ein
>>$$\begin{align}
>> m &\equiv m^{k (p-1)(q-1)} \cdot m &&\;\;(\text{mod } p) \\
>>\end{align}$$ 
>>Da ein Produkt im Exponenten steht, dürfen wir laut den Potenzgesetzten das umschreiben, also $a^{b \cdot c} = \left(a^b\right)^c$. Wir erhalten also
>>
>>$$\begin{align}
>> m &\equiv \left(m^{k (q-1)}\right)^{(p-1)} \cdot m &&\;\;(\text{mod } p)
>>\end{align}$$
>> Weil $m,k,q$ alles ganze Zahlen sind, muss auch $m^{k(q-1)}$ eine ganze Zahl $a \in \mathbb{Z}$ sein. Laut dem [[#^5e7c61|kleinen Satz von Fermat]] erhalten wir
>> $$\begin{align}
>> m &\equiv \left(\underbrace{ m^{k (q-1)} }_{ =a \in \mathbb{Z} }\right)^{(p-1)} \cdot m &&\;\;(\text{mod } p) \\
>> m &\equiv \underbrace{ a^{(p-1)} }_{ \equiv 1 \,(\text{mod }p) } \cdot m &&\;\;(\text{mod } p) \\
>> m &\equiv 1 \cdot m &&\;\;(\text{mod } p) \\
>> m &\equiv m &&\;\;(\text{mod } p) \\
>>\end{align}$$
>>was zu zeigen war.
>>$$\tag*{$\square$}$$
>
>>[!remark] Diskussion: Warum löscht Bob $p,q$ und $\phi(n)$ während der Schlüsselerzeugung?
>
>>[!remark] Kontrollfrage: Warum müssen wir den Gültigkeitsnachweis aufteilen in $m = 0$ und $1 \leq m < n$?
>
>>[!remark] Kontrollfrage: Was würde passieren, wenn $m \geq n$?
>
>>[!remark] Kontrollfrage: Warum ist es wichtig, dass wir in der Schlüsselerzeugung unter 6.2 das modulare Inverse fordern?
>
>>[!remark] Kontrollfrage: Warum ist es wichtig, dass wir in der Schlüsselerzeugung unter 4.2 fordern, dass $\phi(n)$ und $e$ teilerfremd sind?

^7c14da

## 3.3 Laufzeitoptimierungen

>[!attention] Laufzeit der Ver- und Entschlüsselung
>Wenn wir $m^e \text{ mod } n$ oder $c^d \text{ mod }n$ rechnen, erwarten wir enorm viele Multiplikationen durchzuführen, da das Modul $n$ sehr groß gewählt wird und somit $e,d$ ebenfalls enorm groß sein können. Diese Operation wird **modulare Exponentiation** genannt. Um diese Operation in der Berechnung zu optimieren, gibt es verschiedene Algorithmen, die die Laufzeit drastisch senken können. Wir schauen uns dazu die **Repeated Squaring Method** an

>[!algo] Algorithmus: Schnelle Modulare Exponentiation: Repeated Squaring Method 
>>[!def] Definition Repeated Squaring Method ([[../../PDFs/cormen2022.pdf#page=956|Quelle]])
>>Seien $a,b \in \mathbb{Z}^+$. Wir definieren die Auflösung von $a^b$ über die wiederholte Quadratur (**Repeated Squaring**) über die Rekursion
>>$$\begin{align}
>> a^b = \begin{cases}
>> 1 & \text{ wenn } b=0 \\
>> (a^{b/2})^2 & \text{ wenn } b > 0 \text{ und } b \text{ ist gerade} \\
>> a \cdot a^{b-1} &\text{ wenn } b>0 \text{ und } b \text{ ist ungerade}
>>\end{cases}
>>\end{align}$$
>
>>[!example]- Beispiel $b=23$ Rekursive Aufschlüsselung
>>$$\begin{align}
>> a^{23} &= \color{Lavender}a \cdot a^{22} \tag*{$b=23$ ungerade} \\
>>  &= a \cdot \color{Lavender}\left(a^{11} \right)^2 \tag*{$b=22$ gerade} \\
>>  &= a \cdot \left(\color{Lavender}a \cdot a^{10}\color{}\right)^2 \tag*{$b=11$ ungerade} \\
>>  &= a \cdot \left(a \cdot \color{Lavender}\left(a^{5}\right)^2\color{}\right)^2 \tag*{$b=10$ gerade} \\
>>  &= a \cdot \left(a \cdot \left(\color{Lavender}a \cdot a^{4}\color{}\right)^2\right)^2 \tag*{$b=5$ ungerade} \\
>>  &= a \cdot \left(a \cdot \left(a \cdot \color{Lavender}\left(a^{2}\right)^2\color{}\right)^2\right)^2 \tag*{$b=4$ gerade} \\
>>  &= a \cdot \left(a \cdot \left(a \cdot \left(\color{Lavender}(a\color{})^{2}\right)^2\right)^2\right)^2 \tag*{$b=2$ gerade} \\
>>  &= a \cdot \left(a \cdot \left(a \cdot \left((\color{Lavender}a \cdot a^0\color{white})^{2}\right)^2\right)^2\right)^2 \tag*{$b=1$ ungerade} \\
>>  &= a \cdot \left(a \cdot \left(a \cdot \left((a)^{2}\right)^2\right)^2\right)^2 \tag*{$b=0$ terminiert} \\
>>  \;\tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!lemma]- Schlussfolgerung zur Laufzeitoptimierung
>>Aufgrund der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^6a2086|dritten Eigenschaft der ganzzahligen Teilung]] können wir jeden Rekursionsschritt $\text{ mod }n$ rechnen, wodurch die Laufzeit für $a^b$ von $\mathcal{O}(b)$ auf $\mathcal{O}(2\cdot \lfloor \log_{2}(b) \rfloor)$ bezüglich der Multiplikationsschritte reduziert wird.
>>
>>Der Algorithmus zerlegt $b$ quasi in seine binäre Repräsentation, daher schließen wir auf den Logarithmus zur Basis $2$. Im schlimmsten Fall haben wir jeweils $\log_{2}(b)$ Quadraturen und Multiplikationen
>
>>[!example]- Beispiel $b=23, a=5, n=7$ (Fortsetzung)
>>Wir übernehmen unseren gefundenen Ausdruck vom letzten Beispiel
>>$$\begin{align}
>> a^{23} &\equiv  a \cdot \left(a \cdot \left(a \cdot \left((a)^{2}\right)^2\right)^2\right)^2 &&\;\;(\text{mod } n) \\
>>  &\equiv  5 \cdot \left(5 \cdot \left(5 \cdot \left(\underbrace{ (5 \cdot 1)^{2} }_{ =25 }\right)^2\right)^2\right)^2 &&\;\;(\text{mod } 7) \\
>>  &\equiv  5 \cdot \left(5 \cdot \left(5 \cdot \left(\underbrace{ 25 }_{ \equiv 4 }\right)^2\right)^2\right)^2 &&\;\;(\text{mod } 7) \\
>>  &\equiv  5 \cdot \left(5 \cdot \left(5 \cdot \underbrace{ 16 }_{ \equiv 2 }\right)^2\right)^2 &&\;\;(\text{mod } 7) \\
>>  &\equiv  5 \cdot \left(5 \cdot \left(\underbrace{ 10 }_{ \equiv 3 }\right)^2\right)^2 &&\;\;(\text{mod } 7) \\
>>  &\equiv  5 \cdot \left(5 \cdot \underbrace{ 9 }_{ \equiv_{2} }\right)^2 &&\;\;(\text{mod } 7) \\
>>  &\equiv  5 \cdot \left(\underbrace{ 10 }_{ \equiv 3 }\right)^2 &&\;\;(\text{mod } 7) \\
>>  &\equiv  5 \cdot \underbrace{ 9 }_{ =2 } &&\;\;(\text{mod } 7) \\
>>  &\equiv  10  &&\;\;(\text{mod } 7) \\
>>  &\equiv  3  &&\;\;(\text{mod } 7) \\ \\
>> \; \tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!lemma]- Beobachtung zur Rekursiven Zerlegung
>> Wenn wir $b$ in $a^b$ in seine binäre Repräsentation zerlegen, erhalten wir die Bildungsvorschrift, welche Operationen in unserer Zerlegung wie erfolgen, wobei
>> - $0 \implies$ Quadrieren 
>> - $1 \implies$ Quadrieren und mit $a$ multiplizieren
>
>>[!example]- Beispiel $b=23$ Binäre Interpretation (Fortsetzung)
>> $b=23$ lässt sich binär darstellen als
>> $$10111_{2} =23_{10}$$
>> Wir starten mit $a^0$ und leiten ab
>> $$\begin{align}
>> &a \cdot (a^0)^2 = a\tag{1} \\ 
>> &a^2 \tag{0} \\
>> &a \cdot \left(a^2\right)^2 \tag{1}\\
>> &a \cdot \left(a \cdot \left(a^2\right)^2\right)^2 \tag{1}\\
>> &a \cdot \left(a \cdot \left(a \cdot \left(a^2\right)^2\right)^2\right)^2 \tag{1}\\ \\
>> \,\tag*{$\blacktriangleleft$}
>>\end{align}$$
>
>>[!algo] Implementation in Sage
>>```python
>># Rekursive Berechnungsvorschrift
>> def pot_recursive(a,n):
>> 	if n==0: return 1
>> 	elif n%2 == 1: return a * pot_recursive(a, n//2) **2
>> 	else: return pot_recursive(a,n//2)**2 
>> 	
>> # Binäre Berechnungsvorschrift
>> def pot_binary(a,n):
>>	if n==0: return 1 
>>	n = bin(n)[2:] # die ersten 2 Zeichen (Indikatoren) weglassen z.B. 0b100101
>>				   #                                                   ^^	
>>	result = 1 # Startwert
>>	for i,n_i in enumerate(n):
>>		result *= result
>>		if n_i == '1': 
>>			result *= a
>>	return result 
>>```
>
>>[!example] Übung: Implementieren Sie, dass die schnelle Exponentiation zur schnellen modularen Exponentiation wird. Es soll als drittes Argument den Modulus $n$ erhalten.

## 4.1 Mathematische Grundlagen 

>[!theorem] Chinesischer Restsatz ([[../../PDFs/forman2015.pdf#page=197|Quelle]])
>
>>[!remark]- Motivation: Ein Bekanntes Konzept - Gleichungssysteme
>> Aus der Schule und der linearen Algebra kennen wir bereits das Konzept der Gleichungssysteme. Wir kennen Beispiele wie, dass zwei Studenten für eine Studentenfeier einkaufen gehen. Student 1 bezahlt für 25 Flaschen Bier und 5 Flaschen Wein $57.2$€. Student 2 bezahlt für 30 Flaschen Bier und 3 Flaschen Wein $47.67$€. Vorausgesetzt beide Studenten haben für die Bierflaschen und Weinflaschen dieselben Preise bezahlt, können wir das folgende Gleichungssystem aufstellen
>> 
>> $$\begin{align}
>> 25x + 5y &= 57.2 \tag{Student 1} \\
>> 30x + 3y &= 47.67 \tag{Student 2}
>>\end{align}$$
>>wobei $x$ für die Anzahl der Bierflaschen und $y$ für die Anzahl der Weinflaschen stehen. Lösen wir das nach den bekannten Lösungsverfahren erhalten wir
>>$$\begin{align}
>> x&=0.89 \tag{Anzahl Bierflaschen}\\
>> y&=6.99 \tag{Anzahl Weinflaschen}
>>\end{align}$$
>>
>>Ein ähnliches Konzept können wir auch für modulare Gleichungen beschreiben, also **modulare Gleichungssysteme**. In unserer Veranstaltung beschränken wir uns auf Systeme mit **einer unbekannten Größe**. Ein solches Gleichungssystem kann wie folgt aussehen.
>>$$\begin{align}
>> x &\equiv 3 &&\;\;(\text{mod } 5) \\
>> x &\equiv 5 &&\;\;(\text{mod } 7)
>>\end{align}$$
>>Diese Gleichung besagt, es soll ein $x$ geben, dass wenn modulo $5$ gerechnet $3$ ergibt und modulo $7$ gerechnet $5$ ergibt.
>
>Seien $n_{1},\dots,n_{k} \in \mathbb{N}$ paarweise teilerfremd. Dann **gibt es** für alle $a_{1},\dots,a_{k}\in\mathbb{Z}$ ein $x \in \mathbb{Z}$, sodass
>$$\begin{align}
> x &\equiv a_{1}&&\;\;(\text{mod } n_{1}) \\
> x &\equiv a_{2}&&\;\;(\text{mod } n_{2}) \\ 
> &\quad\vdots \\
> x &\equiv a_{k}&&\;\;(\text{mod } n_{k}) \\
>\end{align}$$
> Genauer gesagt, $x \in \mathbb{Z}_{N}$ mit $N=n_{1}\cdot \ldots \cdot n_{k}$ ist **eindeutig**.
>
>>[!proof]- Beweis
>>Wir teilen den Beweis in zwei Teile auf, und zwar in den **Existenzbeweis** und den **Eindeutigkeitsbeweis**.
>>
>>**<u>Existenzbeweis</u>**:
>>
>>Der Beweis ist konstruktiv, das bedeutet wir beschreiben wie wir über unsere Erkenntnisse eine Lösung konstruieren können, wodurch die Existenz nachgewiesen wäre.
>>
>> Zunächst können wir festhalten, dass unser $x$ die Rester $a_{1},\dots,a_{k}$ in irgendeiner Form enthalten muss. Daher beginnen wir $x$ wie folgt zu charakterisieren
>> $$x = a_{1} \underline{\qquad\qquad} + a_{2} \underline{\qquad\qquad}+\ldots+a_{k}\underline{\qquad\qquad}$$
>> Die Strategie ist unsere Summanden so zu konstruieren, dass wenn wir modulo eines der $n_{i}$ rechnen, dass das entsprechende $a_{1}$ übrig bleibt. 
>> 
>> Damit ein belieibiges $a_{i}$ übrig bleibt, wenn wir modulo $n_{i}$ rechnen, muss es alle anderen Module enthalten. Dafür verwenden wir $N=n_{1}\cdot \ldots \cdot n_{k}$ und definieren den Faktor $\frac{N}{n_{i}}$. Dieser Faktor enthält somit alle Module außer $n_{i}$. Wir erweitern unsere Konstruktion von $x$ mit
>> $$x=a_{1}\cdot \frac{N}{n_{1}} \underline{\qquad\quad} + a_{2}\cdot \frac{N}{n_{2}} \underline{\qquad\quad}+\ldots+a_{k}\cdot \frac{N}{n_{k}}\underline{\quad\qquad}$$
>>>[!remark]- Zwischenbemerkung zur Logik
>>>Würden wir unser aktuelles $x$ Modulo $n_{1}$ rechnen, würden zumindest schonmal alle Summanden bis auf den ersten zu $0$ werden
>>> $$x=\underbrace{ a_{1}\cdot \frac{N}{n_{1}}U \underline{\qquad\quad} }_{ \equiv? \;\;(\text{mod } n_{1}) } + \underbrace{ a_{2}\cdot \frac{N}{n_{2}} \underline{\qquad\quad} }_{ \equiv 0 \;\;(\text{mod } n_{1}) }+\ldots+\underbrace{ a_{k}\cdot \frac{N}{n_{k}}U\underline{\quad\qquad} }_{ \equiv0 \;\;(\text{mod } n_{1}) }$$
>>> Da $N$ den Faktor $n_{1}$ enthält, muss die Teilung laut [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^6a2086|dritten Eigenschaft der ganzzahligen Teilung]] aufgehen und somit den Rest $0$ enthalten. Im ersten Summanden haben wir aber $n_{1}$ zuvor durch $\frac{N}{n_{1}}$ rausgerechnet, weshalb der Ausgang der Rechnung an der Stelle ungewiss ist.
>>
>> Wir können nun garantieren, dass wenn wir modulo $n_{i}$ rechnen, dass alle Summanden wegfallen außer $a_{i}\cdot \dfrac{N}{n_{i}}$. Jedoch können wir keine Aussagen darüber treffen, welcher Wert entsteht, wenn wir
>> $$a_{i}\cdot \dfrac{N}{n_{i}} \text{ mod } n_{i}$$
>> Wir erwarten jedoch, dass das Ergebnis am Ende $a_{i}$ ist, wenn wir diesen Summanden $\text{ mod } n_{i}$ rechnen. Damit wir das erreichen, müssen wir eine Zahl $q$ finden, sodass
>> $$\frac{N}{n_{i}} \cdot q \equiv 1 \;\;(\text{mod } n_{i})$$
>> Da alle $n_{i}$ paarweise teilerfremd sind, wissen wir, dass $q=\left[ \dfrac{N}{n_{i}} \right]^{-1}_{n_{i}}$ das [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^c7c061|modulare Inverse]] bezüglich des Moduls $n_{i}$ ist. Das bedeutet, wenn wir noch das modulare Inverse als Faktor bezüglich des spezifischen $n_{i}$ hinzufügen, dass dann garantiert $a_{i}$ als Ergebnis entsteht. Also
>> $$\begin{align}
>> x&=a_{1}\cdot \frac{N}{n_{1}} \cdot \left[ \dfrac{N}{n_{1}} \right]^{-1}_{n_{1}} + a_{2}\cdot \frac{N}{n_{2}} \cdot \left[ \dfrac{N}{n_{2}} \right]^{-1}_{n_{2}}+\ldots+a_{k}\cdot \frac{N}{n_{k}}\cdot \left[ \dfrac{N}{n_{k}} \right]^{-1}_{n_{k}} \\
>> &= \sum_{i=1}^k a_{i} \frac{N}{n_{i}}\left[ \frac{N}{n_{i}} \right]_{n_{i}}^{-1}
>>\end{align}$$
>>Damit ist gezeigt, dass ein $x$ existiert, welches das modulare Gleichungssystem erfüllt.
>>$$\tag*{$\square$}$$
>>
>>**<u>Eindeutigkeitsbeweis</u>**:
>>
>>Nehmen wir an, dass zwei **verschiedene** $x,x' \in \mathbb{Z}_{N}$ existieren, die das modulare Gleichungssystem erfüllen, also
>>$$\begin{align}
>> x \equiv x' &\equiv a_{1}&&\;\;(\text{mod } n_{1}) \\
>> x \equiv x' &\equiv a_{2}&&\;\;(\text{mod } n_{2}) \\ 
>> \quad\vdots \\
>> x \equiv x' &\equiv a_{k}&&\;\;(\text{mod } n_{k}) \\
>>\end{align}$$
>>Konzentrieren wir uns auf die linke Seite der Kongruenz erhalten wir
>>$$\begin{align}
>> x &\equiv x' &&\;\;(\text{mod } n_{i}) \\
>>\end{align}$$
>>Aufgrund des Satzes der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Kongruenzen]] können wir sagen
>>$$n_{i} \;|\; (x-x')$$
>>für $1 \leq i \leq k$. Da alle $n_{i}$ paarweise teilerfremd sind, haben wir
>>$$n_{i}\;|\;(x-x') \land n_{j}\;|\;(x-x') \implies n_{i} \cdot n_{j} \;|\; (x-x')$$
>>laut der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^251edf|Teilbarkeit von teilerfremden Produkten]]. Durch das [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^2548b2|Lemma zu Teilerfremde über Teilerfremde Produkte]] wissen wir, dass für ein weiteres $n_{l}$ gilt
>>$$\text{ggT}(n_{i}, n_{l})=1 \land \text{ggT}(n_{j}, n_{l}) = 1 \implies \text{ggT}(n_{i}\cdot n_{j}, n_{l})=1$$
>>Daher lässt sich die eben präsentierte Logik über alle Module anwenden, das heißt 
>>$$\begin{align}
>> n_{1}n_{2}\dots n_{k} &\;|\;(x-x') \\
>> N &\;|\;(x-x') \tag{$N=n_{1}n_{2}\dots n_{k}$}\\
>>\end{align}$$
>>Nach dem Satz der [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^291942|Teilbarkeit von Kongruenzen]] können wir wieder rückschließen
>>$$x \equiv x' \;\;(\text{mod } N) $$ 
>>Laut der Definition [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^30b120|der Eindeutigkeit und Einschränkung des Rests]], muss gelten
>>$$x = x'$$
>>was ein Widerspruch dazu ist, dass es zwei verschiedene geben kann.
>>$$\tag*{$\square$}$$
>
>>[!theorem] Lösungsformel Abgeleitet vom Beweis
>>$$x \equiv \sum_{i=1}^k a_{i} \frac{N}{n_{i}}\left[ \frac{N}{n_{i}} \right]_{n_{i}}^{-1} \;\;(\text{mod } N)$$
>
>>[!example]- Ausführliches Beispiel
>>Gegeben seien folgende Gleichungen:
>>
>>$$
>>\begin{align}
>>& x \equiv 3 \pmod 5 \newline
>>& x \equiv 5 \pmod 7 \newline
>>& x \equiv 7 \pmod 9 
>>\end{align}
>>$$
>>
>>Um das <b>Ergebnis x</b> zu ermitteln, müssen wir die Koeffizienten folgender Gleichung bestimmen
>>
>>$$ x = \underbrace{3 \cdot \underline{\hspace{3cm}}}_{\large{\substack{\equiv\ 3 \mod 5 \\ \equiv\ 0 \mod \color{Salmon}7 \\ \equiv\ 0 \mod \color{Salmon} 9}}} + \underbrace{5 \cdot \underline{\hspace{3cm}}}_{\large{\substack{\equiv\ 0 \mod \color{LimeGreen}5 \\ \equiv\ 5 \mod 7 \\ \equiv\ 0 \mod \color{LimeGreen} 9}}} + \underbrace{7 \cdot \underline{\hspace{3cm}}}_{\large{\substack{\equiv\ 0 \mod \color{LimeGreen}5 \\ \equiv\ 0 \mod \color{LimeGreen}7 \\ \equiv\ 7 \mod 9}}}$$
>>
>>In der ersten Spalte wurden die Elemente <font color="Salmon">rot</font> markiert, die bezüglich der anderen Module nach $0$ auflösen müssen. Dies gilt dann analog für dieselben <font color="LimeGreen">grün</font> markierten.
>>
>>Damit wir die in den Spalten formulierten Bedingungen erreichen können, müssen wir das modulare Inverse der markierten Module berechnen. Das hat den Effekt, dass wenn der jeweilige Term Modulus der markierten Zahlen gerechnet wird, die unmarkierte Zahl übrig bleibt. Das lässt sich wie folgt darstellen: 
>>
>>$$ 
>>\begin{aligned}[t] 
>>3 \cdot \underbrace{7 \cdot 9 \cdot \biggl[7\cdot9\biggr]^{-1}_5}_{\equiv 1 \mod (7 \cdot 9)} & \mod (315) \newline \newline
>>3\cdot1 & \mod (315) \newline
>>3 & \mod (315)
>>\end{aligned}
>>$$
>>
>>
>>Das modulare Inverse wird in der folgenden Darstellung als $x_i$ angegeben. Damit aktualisiert sich unsere Gleichung wie folgt:
>>
>>$$\begin{align} 
>>x &= 3 \cdot \color{Salmon}7 \cdot \color{Salmon}9 \color{white}\cdot x_1 + 5 \cdot \color{LimeGreen}5 \cdot \color{LimeGreen}9 \color{white}\cdot x_2 + 7 \cdot \color{Goldenrod}5 \cdot \color{Goldenrod}7 \color{white}\cdot x_3
>>\end{align}$$
>>
>>Um $x_1$ zu bestimmen, müssen wir das modulare Inverse zu den Koeffizienten $7 \cdot 9$ bezüglich des Modulus $5$ berechnen. Demzufolge müssen wir folgende Gleichung lösen:
>>
>>$$ x_1 \cdot 7 \cdot 9 = 1 \pmod{5} $$
>>
>>Die Lösung für $x_1$ ist in dem Fall $\pmb{2}$. Diese Lösung setzen wir dann in die entsprechende Lücke der Gleichungen ein und erhalten mit den Lösungen $x_2 = \pmb{5}$ und $x_3 = \pmb{8}$ die vollständige Gleichung, mit der wir die Lösung des chinesischen Restsatzer erhalten.
>>
>>$$\begin{aligned}[t] 
>>x &\equiv 3 \cdot 7 \cdot 9 \cdot \pmb{2} + 5 \cdot 5 \cdot 9 \cdot \pmb{5} + 7 \cdot 5 \cdot 7 \cdot \pmb{8} & \;\;(\text{mod } 315) \newline
>>&\equiv 3463 & \;\;(\text{mod } 315)\newline
>>&\equiv 313 & \;\;(\text{mod }  315)
>>\end{aligned}$$
>
>>[!example]- Übung: Chinesischer Restsatz mit $2$ Gleichungen
>>Finden Sie das kleinste $x \in \mathbb{Z}$, sodass
>>$$\begin{align}
>> x &\equiv 6 && \;\;(\text{mod } 7) \\
>> x &\equiv 5 && \;\;(\text{mod } 11)
>>\end{align}$$
>
>>[!example]- Übung: Chinesischer Restsatz mit $3$ Gleichungen
>>Finden Sie das kleinste $x \in \mathbb{Z}$, sodass
>>$$\begin{align}
>> x &\equiv 1 && \;\;(\text{mod } 2) \\
>> x &\equiv 2 && \;\;(\text{mod } 3) \\
>> x &\equiv 3 && \;\;(\text{mod } 5)
>>\end{align}$$
>
>>[!remark]- Bemerkung zur Herkunft des Chinesischen Restsatzes (Informativ) ([[../../PDFs/imhausen2007.pdf#page=155|Quelle]])
>>
>> Die Art des Problems wurde das erste Mal nachweislich in einer chinesischen Schrift "Sunzi suan jing" 400-500 nach Christus entdeckt. Der Titel der Schrift übersetzt sich als "Klassische Mathematik des Meister Sonne". Der Autor des Stückes wird mit dem Militärstrategen Sunzi in assoziiert, der ebenfalls Autor von "Meister Sonnes Kunst des Krieges" war. Die Autorschaft des Buches ist allerdings eine umstrittene Theorie, die lediglich auf Indizien beruhen. Das Buch beginnt mit einem prosaischen Vorwort 
>> 
>> ---
>> <center>
>> Meister Sonne sagt: Mathematik herrscht über die Länge und Tiefe von Himmel und Erde; <br>beeinflusst das Leben aller Kreaturen; bestimmt das Alpha und das Omega <br>der fünf Tugenden (Nächstenliebe, Gerechtigkeit, Anstand, Wissen und Ehrlichkeit); <br>hat die Funktion der Eltern von Yin und Yang, gründet die Symbole der Sterne und deren Konstellation;<br> manifestiert die Dimensionen der leuchtenden Himmelskörper (Sonne, Mond und Sterne);<br> hält die Balance der fünf Phasen (Metall, Holz, Wasser, Feuer und Erde);<br> reguliert den Anfang und das Ende der vier Jahreszeiten; formuliert die Ursprünge der unzähligen Dinge;<br> und bestimmt die Prinzipien der sechs Künste <br>(Anstand, Musik, Bogenschießen, Wagenlenken, Kaligraphie und Mathematik). 
>> 
>> [...]
>> 
>> Mathematik hat tausende Jahre Bestand gehalten und wird umfangreich ohne Grenzen eingesetzt.<br> Wer seine Lehre ablehnt, der wird nicht in der Lage zu sein Exzellenz und Gründlichkeit zu erreichen.<br> Es gibt tatsächlich eine Menge zu meistern, wenn man die Mathematik in Perspektive betrachtet.<br> Wenn man sich für Mathematik interessiert, wird man geistig voll bereichert; andererseits,<br> wenn man sich von diesem Fach fernhält, fühlt man sich intellektuell unzureichend.<br> Wenn man Mathematik bereitwillig wie ein junger Mensch mit offenem Geist studiert, wird man sofort<br> erleuchtet. Wenn man sich jedoch der Mathematik wie ein alter Mann mit einem starren Verhalten nähert,<br> wird man darin nicht geschickt sein. Daher, wenn man Mathematik erfolgreich lernen möchte,<br> muss man sich selbst disziplinieren und auf vollkommene Konzentration hinarbeiten;<br> auf diese Weise ist Erfolg im Lernen garantiert.
>> 
>> </center>
>> <p align="right" style="font-family:cursive"><i>Sunzi suan jing</i></p>
>> 
>> ---
>> 
>> Dieses Buch liefert allerdings keine konkrete Methode, wie solche Probleme gelöst werden können.
>>
>
>>[!remark] Kontrollfrage: Warum müssen die $n_{i}$ teilerfremd sein?
>
>>[!remark] Kontrollfrage: Warum muss $0\leq x<N$ gelten?

^ca7b4b

## 4.2 Angriffsverfahren auf RSA

>[!remark]- Bemerkung zu den Angriffsverfahren
>Jedes der Verfahren basiert auf den größten Schwachstellen
> - Nachlässigkeit in der sicheren Umsetzung der Protokolle
> - Mangelndes Verständnis zu den Verschlüsselungsverfahren
> 
> Aus der Geschichte wissen wir, dass eine der Gründe im zweiten Weltkrieg, weshalb die Enigma geknackt wurde, war die Nachlässigkeit der deutschen Soldaten beim Umsetzen der Sicherheitsprotokolle. Ebenfalls war es ungeschickt, dass Nachrichten mit dem bekannten Gruß an den Führer endeten, was Angriffe auf das damalige Verfahren erleichterte.
> 
> Ähnliche Ideen werden wir bei den kommenden Verfahren beobachten, die **bestimmte Voraussetzungen** erwarten, damit ein Angriff möglich wird.

>[!theorem] Low Encryption Attack/ Hastad's Broadcast Attack ([[../../PDFs/boneh1999.pdf#page=8|Quelle]])
>
>>[!warning] Voraussetzung
>> Chiffren $c_{i} \in \mathbb{Z}_{n}$ werden an zwei oder mehrere Empfänger gesendet, die alle denselben kleinen Verschlüsselungsexponenten $e$ verwenden.
>
>>[!algo] Verfahren
>> Gegeben sind die Chiffren
>> $$\begin{align}
>> c_{1} &\equiv m^e &&\;\;(\text{mod } n_{1}) \\
>> c_{2} &\equiv m^e && \;\;(\text{mod } n_{2})
>>\end{align}$$
>>Dieses System stellt das Problem des [[#^ca7b4b|chinesischen Restsatzes]] dar, wobei $m^e=x$ unsere Unbekannte ist. Für die einfachere Darstellung, schreiben wir das System als
>>$$\begin{align}
>> c_{1} &\equiv x &&\;\;(\text{mod } n_{1}) \\
>> c_{2} &\equiv x && \;\;(\text{mod } n_{2})
>>\end{align}$$
>>Unter Verwendung der erarbeiteten Lösungsformel
>>$$x \equiv c_{1}n_{2}[n_{2}]^{-1}_{n_{1}}+c_{2}n_{1}[n_{1}]^{-1}_{n_{2}} \;\;(\text{mod } n_{1} \cdot n_{2})$$
>>Da unser $x=m^e$ ist, müssen wir noch die $e$-te Wurzel ziehen um $m$ zu erhalten. Demnach
>>$$m =\sqrt[\leftroot{4}\uproot{2}\scriptstyle e]{x} = \sqrt[\leftroot{4}\uproot{2}\scriptstyle e]{m^e}$$
>
>>[!remark] Diskussion: Warum muss $e$ klein sein?

^a904cc

>[!theorem] Common Modulus Attack ([[../../PDFs/schneier1996.pdf#page=394|Quelle]])
>
>>[!warning] Voraussetzung
>>Eine Chiffre $c \in \mathbb{Z}_{n}$ wird an zwei Empfänger gesendet mit
>>$$\begin{align}
>> \text{public key 1: } (n,e_{1}) \\
>> \text{public key 2: } (n,e_{2}) \\
>>\end{align}$$
>>mit $\text{ggT}(e_{1},e_{2})=1$
>
>>[!algo] Verfahren
>> Da $$\text{ggT}(e_{1},e_{2})=1$$
>> können wir das [[2 - Algebraische und Zahlentheoretische Grundlagen (1)#^42f9e5|Lemma von Bezout]] anwenden. Also es muss zwei Zahlen existieren $s,t \in \mathbb{Z}$, sodass
>> $$se_{1}+te_{2} = 1$$
>> Die Nachricht $m$ können wir einfach herleiten über
>> $$m\equiv m^1 \equiv m^{se_{1}+te_{2}}\equiv (m^{e_{1}})^s(m^{e_{2}})^t \equiv c_{1}^s c_{2}^t \;\;(\text{mod } n)$$
>> Durch kurzes Überlegen können wir feststellen, dass eine der Zahlen $s$ oder $t$ negativ sein muss, daher
>> $$c_{1}^{s}=(c_{1}^{-1})^{-s}$$
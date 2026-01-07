## 14.1 Erweiterung der Mathematischen Probleme

>[!remark] Bemerkung
> Zuvor hatten wir die grundlegendsten mathematischen Probleme auf diskreten Gittern definiert, die unmittelbar aus Minkowski's erstem Satz folgen. Wir werden nun in der Abstraktionsebene scheinbar neue Probleme formulieren, die sich allerdings auf die Gitterprobleme zurückführen lassen. 2009 hat Oded Regev in einer mit dem Gödel Preis ausgezeichneten Arbeit nachweisen können, dass schwierige Gitter Probleme sich auf ein Prinzip namens **Learning with Errors (LWE)** reduzieren lassen. Das bedeutet im Umkehrschluss, jedes kryptographische Verfahren, was auf **LWE** basiert, basiert demzufolge auf schwierig lösbaren Gitterproblemen. Regev zeigte, dass **LWE** sich auf folgende Gitterprobleme reduzieren lässt 
> - $\textbf{GAPSVP}_{\gamma}$: 
>   - Gegegeben ist ein Gitter $\mathcal{L}$ und $d>0$ eine Distanz. Sei $\gamma(n)> 0$ ein Relaxionsparameter. Das Problem ist ein Entscheidungsproblem, das fragt $$ \text{GAPSVP}_{\gamma(n)}(d) = \begin{cases} \text{Ja} & \text{wenn } \lambda_1(L) \leq d \\ \text{Nein} & \text{wenn } \lambda_1(L) > \gamma(n)\cdot d\end{cases} $$
>   - es ist garantiert, dass $d$ in eine der beiden Instanzen fällt
>   - wenn $\gamma(n) = 2^{(n-1)/2}$ können wir mit Hilfe von A. Lenstra, H. Lensta, L. Lovász (LLL)-Algorithmus in polynomieller Zeit entscheiden
>       - der Algorithmus basiert auf dem Resultat Minkowski's erstem Satz
>       - demnach muss $\gamma(n) \ll 2^{(n-1)/2}$
> - $\textbf{SIVP}_{\gamma}$:
>   - Gegeben ist ein Gitter $\mathcal{L}$. Sei $\gamma(n)>0$ ein Relaxionsparameter. Das Problem ist ein Suchproblem, das uns die eine Basis zurückgeben soll, sodass $$ \text{SIVP}_{\gamma(n)} = \{\boldsymbol{b}_{1}, \ldots, \boldsymbol{b}_{n}\} \text{ sodass } \left\vert\left\vert\, \boldsymbol{b}_{i} \,\right\vert\right\vert \leq \gamma(n)\lambda_n(\mathcal{L}) \; \text{mit } 1 \leq i \leq n$$
>   - eine Basis zu finden, die eine kürzeste Basis im Gitter ist, würde essentiell das kürzeste Vektor Problem lösen, und ist daher enorm schwierig zu lösen

<!-- >[!def] Definition Binärer Modulus über den reellen Zahlen -->
<!-- > Sei $x \in \mathbb{R}$ und $n \in \mathbb{N}$. Dann definieren wir den binären Modulus über den reellen Zahlen als  -->
<!-- > $$ x \text{ mod } n := x - n \left\lfloor \frac{x}{n} \right\rfloor $$ -->
<!---->
<!-- >[!example] Beispiele  -->
<!-- > $$\begin{align} -->
<!-- > 5,234 \text{ mod } 1 &= 0,234 \\ -->
<!-- > 3,45 \text{ mod } 2 &= 1,45 \\ -->
<!-- > -2,9 \text{ mod } 4 &= 1,1 \\  -->
<!-- > -12,9 \text{ mod } 4 &= 3,1 -->
<!-- >\end{align}$$ -->
<!---->
<!-- >[!remark] Bemerkung -->
<!-- > Die Gruppe $(\mathbb{R}\setminus n\mathbb{Z}, +)$ der rellen Zahlen Modulus $n$ bildet eine additive Gruppe. Jedoch ist die Multiplikation nicht abgeschlossen. -->

>[!def] Definition Learning Parity with Noise (LPN)
>Sei $k \in \mathbb{N}$. Alice legt ein Geheimnis $\boldsymbol{s} \in \mathbb{Z}_{2}^k$ fest. Weiterhin sei $0 < \varepsilon < \frac{1}{2}$. Bob kann Alice um einen Hinweis auf das Geheimnis anfragen. Mit jeder Anfrage wählt Alice ein $\boldsymbol{a}_{i} \in \mathbb{Z}^k_2$. Nach $n \in \mathbb{N}$ Anfragen steht uns folgendes System an Gleichungen zur Verfügung 
>$$\begin{align} \langle\, \boldsymbol{s} \, , \, \boldsymbol{a}_{1} \,\rangle &\approx_{\varepsilon} \boldsymbol{b}_{1} \quad \text{(mod 2)} \\ \langle\, \boldsymbol{s} \, , \, \boldsymbol{a}_{2} \,\rangle &\approx_{\varepsilon} \boldsymbol{b}_{2} \quad \text{(mod 2)} \\
> & \vdots \\
>\end{align}$$
> wobei $b_i \in \mathbb{Z}_{2}$ mit einer Wahrscheinlichkeit $\varepsilon$ korrekt ist. Alice sendet Bob den Hinweis $(\boldsymbol{a}_{i}, b_i)$.
>
> **LPN fragt nach $n$ Anfragen das Gehemnis $\boldsymbol{s}$ zu nennen.**

>[!remark] Bemerkung
> Der beste bekannte Algorithmus benötigt $n = 2^{k/\log(k)}$ Anfragen um $\boldsymbol{s}\in \mathbb{Z}_{2}^k$ mit hoher Wahrscheinlichkeit bestimmen zu können. Dieser Algorithmus hat eine subexponentielle Laufzeit in $k$. Dieser ist bekannt als der Blum-Kalai-Wasserman Algorithmus.

>[!remark] Bemerkung
> Angenommen wir würden jedes $b_i$ präzise berechnen, dann bräuchten wir lediglich $k$ Anfragen stellen, da wir ein lineares Gleichungssystem mit $k$ unbekannten und $k$ Gleichungen erhalten.

## 14.2 Learning with Errors (LWE)

>[!def] Definition Learning with Errors (LWE)
> Sei $k \in \mathbb{N}$ der Sicherheitsparameter und $q \geq 2$ ein Modulus. Sei weiterhin $\chi$ eine Verteilung über $\mathbb{Z}_q$ (typischerweise eine diskrete Gaußverteilung). Alice wählt ein Geheimnis $\boldsymbol{s} \in \mathbb{Z}_q^k$. 
> 
> Ein **LWE-Sample** ist ein Paar $(\boldsymbol{a}, b) \in \mathbb{Z}_q^k \times \mathbb{Z}_q$, das wie folgt erzeugt wird:
> - wähle $\boldsymbol{a} \in_R \mathbb{Z}_q^k$.
> - $e \in_R \chi$ Rauschen.
> - berechne $b = \big[\langle \boldsymbol{a}, \boldsymbol{s} \rangle + e \big]_q$.
> 
> Es werden zwei Varianten des LWE-Problems unterschieden:
> 1. **Search-LWE**: Gegeben eine Liste von Samples $(\boldsymbol{a}_i, b_i)$, finde das Geheimnis $\boldsymbol{s}$.
> 2. **Decision-LWE**: Unterscheide eine Liste von Samples $(\boldsymbol{a}_i, b_i)$ von einer Liste rein zufällig gewählter Paare aus $\mathbb{Z}_q^k \times \mathbb{Z}_q$.

>[!remark] Bemerkung zum Zusammenhang mit LPN
> LWE kann als Verallgemeinerung von **LPN** betrachtet werden. Während LPN über dem Körper $\mathbb{Z}_2$ arbeitet, operiert LWE über $\mathbb{Z}_q$. Die Schwierigkeit von LWE liegt darin, dass ohne Kenntnis des Fehlers $e$ das Lösen des linearen Gleichungssystems durch die akkumulierten Fehler NP-hart wird.

## 14.3 BFV (Brakerski, Fan, Vercauteren)
>[!remark] Bemerkung
> Wir werden an dieser Stelle viel Entwicklung überspringen und nicht direkt auf die LWE Version von 2005 eingehen. Generell ist die Idee für jede LWE Version immer dieselbe, wir haben ein verrauschtes lineares Gleichungssystem, welches ohne Informationen zum privaten Schlüssel nicht zu lösen ist. 
>
> Entwicklungen in LWE haben sich damit beschäftigt dieses Verfahren für homomorphe Verschlüsselung zu optimieren. Wir werden an dieser Stelle ein Verfahren einführen, welches LWE als homomorphes Verschlüsselungsverfahren umgesetzt hat. Das Verfahren wie es original beschrieben wurde, hat eine andere algebraische Struktur zu Effizienzzwecken implementiert. Wir werden auf uns bekannte Strukturen zurückgreifen, um das Verfahren konzeptionell einzuführen. Mit etwas Selbststudium können die Grundlagen zu Polynomialringen erarbeitet werden, sodass man das Originalkonstrukt nachvollziehen kann.
>
> Alle große homomorphe Verschlüsselungsfamilien basieren auf dem LWE Prinzip und setzen dieses jeweils etwas anders um, welches unterschiedliche Vor- und Nachteile hat. Es ist jedoch zu bemerken, dass die Umsetzung dieser Familien nicht mehr vanilla LWE ist, jedoch konnte gezeigt werden, dass diese das LWE Problem etwas anders umgesetzt haben. Diese homomorphen Verschlüsselungsfamilien sind
> - BFV (Brakerski, Fan, Vercauteren)
> - BGV (Brakerski, Gentry, Vaikunathan)
> - TFHE (Fully Homomorphic Encryption over the Torus)
> - CKKS (Cheon, Kim, Kim, Song)

>[!def] Definition Zentriertes Restklassenrepräsentation
> Sei $q \in \mathbb{N}$. Wir definieren das zentrierte Restklassenrepräsentation als
> $$ \mathbb{Z}_{q} = \left\{  \left\lfloor -\frac{q - 1}{2}  \right\rfloor, \left\lfloor -\frac{q - 1}{2} + 1 \right\rfloor, \, \ldots \,, 0, \, \ldots \, , \left\lfloor \frac{q - 1}{2} - 1  \right\rfloor , \left\lfloor \frac{q - 1}{2} \right\rfloor   \right\} $$

>[!example] Beispiele
> 1. $\mathbb{Z}_{3} = \{ -1, 0, 1\}$
> 2. $\mathbb{Z}_{4} = \{-2, -1, 0 , 1 \}$
> 3. $\mathbb{Z}_{256} = \{ -128, -127, \ldots, 0, \ldots, 126, 127 \}$

>[!remark] Bemerkung
> Bisher haben wir mit der **kanonischen Repräsentation** der Restklassen gearbeitet, das heißt wir haben Elemente in $\mathbb{Z}_{q}$ dargestellt mit
> $$ \mathbb{Z}_{q} = \{0, 1, \ldots , q-1\} $$
> Wir werden später sehen, dass es aus Effizienzgründen wichtig ist für die homomorphe Verschlüsselungsverfahren Koeffizienten in der **zentrierten Repräsentation** darzustellen.

>[!remark] Bemerkung
> Wir werden das kryptographische System jetzt schrittweise einführen. Wir führen ein
> - Verfahrensparameter 
> - Verschlüsselungs-/Entschlüsselungsalgorithmus
> - Homomorphe Addition
> - Homomorphe Multiplikation
> - Korrektheit der Aussagen

>[!remark] Bemerkung
> Um die Notation etwas einfacher zu halten, schreiben wir für den **binären Modulus** $$a \text{ mod } b := [a]_{b}$$

### 14.3.1 Schlüsselerzeugung

>[!def] Definition Rejection Sampling einer Diskrete Gaußdistribution
> Sei $\mathcal{N}(0, \sigma)$ die nicht-normalisierte Normalverteilung mit Dichtefunktion $f(x) = \exp\left(\frac{-\pi x^2}{\sigma^2}\right)$ und $\chi = \mathcal{N}_{\mathbb{Z}, B}(0, \sigma)$ die diskrete $B$-beschränkte Normalverteilung mit $B = k \sigma$.
>
> Um ein $x$ in $\chi$ zu (rejection-) samplen, wählen wir
> - $x \in_R [-B, B] \cap \mathbb{Z}$
> - $p \in_{R} [0,1]$
>
> wir bestimmen
> $$\begin{cases} \text{AKZEPTIEREN} & p < f(x)\\ \text{ABLEHNEN - wiederholen} & p \geq f(x)\end{cases}$$
> Wir wiederholen bis wir ein adäquates $x \in \mathbb{Z}$ gefunden haben.

>[!def] Definition (Haupt)Schlüsselerzeugung
> Seien $k \in \mathbb{N}$ der Sicherheitsparameter und
> - $\mathbb{Z}_{t}$ der Klartextraum mit $t > 1$ und $t \in \mathbb{N}$
> - $\mathbb{Z}_{q}^k$ der Ciphertextraum mit $q \gg t$ und $q=t^k$ für $k \in \mathbb{N}$
>
> wobei wir $t$ den **Klartext**- und $q$ den **Ciphertextkoeffizienten** nennen.
>
> - Privater Schlüssel: $sk = \boldsymbol{s} \in_{R} \mathbb{Z}_{2}^k$
> - Öffentlicher Schlüssel: $pk = (p_{0}, \boldsymbol{p}_{1}) \in \mathbb{Z}_{q} \times \mathbb{Z}_{q}^k$ 
>   - wähle $\boldsymbol{a} \in_R \mathbb{Z}_{q}^k$
>   - sei $\chi = \mathcal{N}_{\mathbb{Z}, B}(0, \sigma)$ mit $B = k \sigma$
>   - wähle $e \in_R \chi$, sodass $e \in \mathbb{Z}_{q}$
>   - berechne: $$\begin{align}
>   p_0 &= [-(\boldsymbol{a}^T \boldsymbol{s} + e)]_q \\
>   \boldsymbol{p}_1 &= \boldsymbol{a}
>\end{align}$$

>[!remark] Bemerkungen Bedeutung Parameter $t$ und $q$
> - In der Literatur werden $t$ und $q$ nicht immer so gewählt, dass $t$ zwangsläufig $q$ teilen muss. In diesem Fall wird $\Delta$ abgerundet. Um die Nachweise etwas einfacher zu halten, wählen wir diese als Teiler zueinander. Es ist üblich $t$ und $q$ jeweils als Potenzen von $2$ zu wählen.

>[!remark] Bemerkung Bedeutung Evaluierungsschlüssel
> Damit wir möglichst viele multiplikative Operationen durchführen können, benötigen wir einen **Evaluierungsschlüssel**. Dieser Schlüssel wird für die Relinearisierung der Chiffren nach der Multiplikation von Chiffren benötigt, wofür es zwei verschiedene Methoden gibt. Die erste Methode verwendet eine Basenreduktion (**Radix Base Reduction**), während die zweite kurzzeitig das Modul (**Modulus Switching**) wechselt. Wir werden uns hier ausschließlich mit der **Basenreduktion** beschäftigen.

>[!remark] Bemerkung Skalarprodukt
> Wie bereits zur Einführung des Skalarprodukts erwähnt, gibt es verschiedene Schreibweisen für das Skalarprodukt. Damit folgende Ausführungen übersichtlich bleiben, schreiben wir das Skalarprodukt fortan als
> $$\langle\, \boldsymbol{x}_{1} \, , \,\boldsymbol{x}_{2}\,\rangle = \boldsymbol{x}_{1}^T \boldsymbol{x}_{2}$$


>[!def] Definition Evaluierungsschlüsselerzeugung
> Sei $\boldsymbol{s} \in \mathbb{Z}_{2}^k$ der private Schlüssel. Außerdem sei 
> - $T > 2$ die Base 
> - $\ell = \left\lfloor \log_T(q)\right\rfloor$ die Anzahl der Koeffizienten der Basenreduktion
> - $\boldsymbol{a}_{i} \in \mathbb{Z}_{q}^k$ zufällige öffentliche Schlüsselkomponenten mit $0 \leq i \leq l$
> - $e_{i} \in_R \chi$ Rauschen mit $0 \leq i \leq l$, sodass $\boldsymbol{e}_{i} \in \mathbb{Z}_{q}$
>
> der Evaluierungsschlüssel für die **Relinearisierung** wird bestimmt mit
> $$rlk = (r_0, \boldsymbol{r}_{1}) = \Big(\big[-\left(\boldsymbol{a}_{i}^T\boldsymbol{s}+\boldsymbol{e}_{i}\right)+T^i \cdot \boldsymbol{s}^2\big]_{q},\; \boldsymbol{a}_{i}\Big)_{i=0}^\ell$$

^3009de

>[!remark] Bemerkung
> Der Evaluierungsschlüssel $rlk$ besteht aus $\ell+1$ Tupeln  $(\mathbb{Z}_{q} \times \mathbb{Z}_{q}^k)_{i=0}^{\ell}$.


### 14.3.2 Verschlüsselung und Entschlüsselung

>[!def] Definition Verschlüsselung
> Sei $m \in \mathbb{Z}_{t}$ eine Nachricht und gegeben ist der öffentliche Schlüssel $pk=(p_{0}, \boldsymbol{p}_{1})$. Eine Klartextnachricht wird verschlüsselt, indem folgende Komponenten bestimmt werden
> - $u \in_R \mathbb{Z}_{2}$ Auswahlmaske
> - $e_{0}, \boldsymbol{e}_{1} \in \chi$ Rauschen, sodass $e_0 \in \mathbb{Z}_{q}$ und $\boldsymbol{e}_{1} \in \mathbb{Z}_{q}^k$
> - $\Delta = \dfrac{q}{t}$ Skalierungsfaktor
> 
> Die Chiffre $C = (c_{0}, \boldsymbol{c}_{1})$ wird bestimmt mit
> $$\begin{align}
> c_0 &= \big[u \cdot p_0 + e_0 + \Delta \cdot m\big]_q  \\
> \boldsymbol{c}_1 &= \big[u \cdot \boldsymbol{p}_1 + \boldsymbol{e}_1\big]_q
>\end{align}$$

>[!def] Definition Entschlüsselung
> Sei $\boldsymbol{s} \in \mathbb{Z}_{2}^k$ der private Schlüssel und $C = (c_{0}, \boldsymbol{c}_{1})$ die Chiffre, dann kann die Klartextnachricht reproduziert werden mit
> $$m = \left[\left\lfloor \dfrac{t \cdot [c_{0} + \boldsymbol{c}_{1}^T\boldsymbol{s}]_{q}}{q} \right\rceil\right]_{t}$$

>[!proof] Beweis Korrekter Entschlüsselung
> Wir wollen zeigen, dass folgende Identität wahr ist
> 
> $$m = \left[\left\lfloor \dfrac{t \cdot [c_{0} + \boldsymbol{c}_{1}^T \boldsymbol{s}]_{q}}{q} \right\rceil\right]_{t}$$
> Zunächst betrachten wir lediglich den Zähler in der Chiffre. Dazu verwenden wir die Definitionen des Verschlüsselungsprozesses und setzen sukzessive ein.
>  $$\begin{align*}
>        [{\color{violet}c_{0}}+ {\color{teal}\boldsymbol{c}_{1}^T} \boldsymbol{s}]_{q}&= [{\color{violet}u \cdot p_{0} + e_{0}+ \Delta m} + ({\color{teal}u \cdot \boldsymbol{p}_{1}+\boldsymbol{e}_{1}})^T\boldsymbol{s}]_{q} \\
>        &= [\underbrace{ -u(\boldsymbol{a}^T \boldsymbol{s}+ e) }_{ =p_{0} }+ e_{0} + \Delta m + (u \cdot \boldsymbol{a}+ \boldsymbol{e}_{1})^T\boldsymbol{s}]_{q} \\
>        &= [\cancel{ -u\boldsymbol{a}^T\boldsymbol{s} }- u \cdot \boldsymbol{e} + e_{0} + \Delta m + \cancel{ u\boldsymbol{a}^T\boldsymbol{s} } + \boldsymbol{s}^T\boldsymbol{e}_{1}]_{q} \\
>        &= [\Delta m + \underbrace{ e_{0} + \boldsymbol{s}^T\boldsymbol{e}_{1} - u\cdot e }_{ = v}]_{q} \\
>        &= [\Delta m + \boldsymbol{v}]_{q}
>\end{align*}$$
> wobei $v$ das akkumulierte Rauschen ist. Wir schreiben die Identität um, sodass für 
> $$[\Delta m + v]_{q} \equiv \Delta m + v + qr \quad(\text{mod } q)$$
> wobei $r \in \mathbb{Z}$. Wir setzen ein und erhalten 
>$$\begin{align} 
> \frac{t \cdot [c_{0}+ \boldsymbol{c}_{1}^T \boldsymbol{s}]_{q}}{q} &= \frac{t \cdot (\Delta m+ v + rq )}{q} \\
> &=  \frac{t}{q}\Delta m+ \frac{t}{q}v + tr 
>\end{align}$$
> Da wir $\Delta = \dfrac{t}{q}$ definiert
> $$\frac{t}{q}\Delta m+ \frac{t}{q}v + tr = m+ \frac{t}{q}v + tr$$
> Wir setzen den Term nun in den originalen Entschlüsselungsausdruck ein und erhalten
> $$m = \left[\left\lfloor  m+ \frac{t}{q}v + tr\right\rceil\right]_{t}$$
> Wir bemerken, dass $m$ nicht gerundet werden muss, und da $m\in \mathbb{Z}_{t}$ bleibt $m$ unverändert bezüglich $[ \cdot ]_{t}$. Außerdem, da $tr$ ein ganzzahliges Vielfaches von $t$ ist, bleibt es beim Runden unverändert und verschwindet bei $[ \cdot ]_{t}$. Es verbleibt
> $$m = m + \left[\left\lfloor  \frac{t}{q}v \right\rceil\right]_{t}$$
> Damit wir abschätzen können wie sich der Rundungsprozess verhalten wird benötigen wir die **Maximums-Norm**
> $$\left\vert\left\vert\, \boldsymbol{x} \,\right\vert\right\vert_\infty = \max\{x_i \in \boldsymbol{x}\}$$
>>[!Remark] Bemerkung 
>> Mathematisch gesehen schummeln wir etwas, da die Norm für Vekotren bestimmt ist und wir sie für Skalare anwenden. Wir arbeiten allerdings hauptsächlich mit Skalaren, da BFV sehr vereinfacht haben. Die Homogenität würde uns normalerweise erlauben das Skalar als Absolutwert rauszuziehen. Wir werden das an dieser Stelle nicht erlauben und betrachten die Maximumsnorm auf dem Skalar als der größte Wert, den dieser Skalar in der Maximumsnorm werden kann.
>
>Wir erinnern uns, dass $v= e_{0} + \boldsymbol{s}^T\boldsymbol{e}_{1} - ue$ ist. Wir wollen nun abschätzen wie groß das Rauschen maximal werden kann, damit wir wissen was das Ergebnis vom Runden im ungünstigsten Fall sein wird.
> $$\begin{align}
> \left\vert\left\vert\, \frac{t}{q} v \,\right\vert\right\vert_\infty &= \left\vert\left\vert\, \frac{t}{q} \left( e_{0} + \boldsymbol{s}^T\boldsymbol{e}_{1} - ue \right)\,\right\vert\right\vert_\infty \\
>  &= \Bigg\vert \underbrace{\frac{t}{q}}_{> 0} \Bigg\vert \cdot \left\vert\left\vert\, e_0 + \boldsymbol{s}^T\boldsymbol{e}_1 - ue\,\right\vert\right\vert_\infty \tag{Homogenität} \\
> &\leq \frac{t}{q} \cdot \Big( \left\vert\left\vert\, e_0 \,\right\vert\right\vert_\infty + \left\vert\left\vert\, \boldsymbol{s}^T\boldsymbol{e}_1 \,\right\vert\right\vert_\infty + \left\vert\left\vert\, ue \,\right\vert\right\vert_\infty \Big)
>\end{align}$$
> Wir können nun die einzelnen Rauschterme einfach abschätzen. Wir erinnern uns, dass $\boldsymbol{e}_{i}$ von einer $B$-beschränkten diskreten Normalverteilung stammen. Die Terme $\boldsymbol{s}$ und $u$ stammen aus binären Distributionen. Daher kann wissen wir wie groß diese Terme maximal sein können.
> $$\begin{align}
>   \left\vert\left\vert\, e_0 \,\right\vert\right\vert_\infty &= B \\
> \left\vert\left\vert\, ue \,\right\vert\right\vert_\infty &= 1 \cdot B = B \\
> \left\vert\left\vert\, \boldsymbol{s}^T \boldsymbol{e}_1 \,\right\vert\right\vert &\leq \left\vert\left\vert\, \boldsymbol{s} \,\right\vert\right\vert_1 \cdot \left\vert\left\vert\, \boldsymbol{e}_1\,\right\vert\right\vert_\infty \tag{1}\\
> &= k\cdot B
>\end{align}$$
> Wobei wir in $(1)$ die Eigenschaft des Skalarprodukts verwenden (Höldersche Ungleichung). Jeder Faktor in $\boldsymbol{s}$ kann maximal $1$ sein, da es $k$ davon gibt, entspricht das der $\left\vert\left\vert\, \cdot \,\right\vert\right\vert_1$-Norm. Daher lässt sich der verbleibende Term abschätzen mit
> $$\left\vert\left\vert\, \frac{t}{q} v \,\right\vert\right\vert_\infty \leq \frac{t}{q} (2B + kB) = \frac{t}{q} B(2 + k)$$
> Damit der Term beim Runden verschwindet, fordern wir
> $$\frac{t}{q} B(2 + k) < \frac{1}{2}$$
> Unter der Annahme, dass die Parameterwahl so getroffen wurde, dass dies wahr ist, verschwindet der Term beim Runden und wir erhalten
> $$m = m + \underbrace{\left[\left\lfloor  \frac{t}{q}v \right\rceil\right]_{t}}_{=0} = m$$
> Dies zeigt, dass die Entschlüsselung korrekt ist. $$\tag*{$\square$}$$

>[!remark] Bemerkung
> Im Beweis zur Korrektheit des Verfahrens konnten wir eine wichtige Relation zwischen der Wahl der Parameter und der Korrektheit des Verfahrens herstellen, nämlich
> $$\frac{t}{q} B(2 + k) < \frac{1}{2}$$
> Dies führt zu einem wichtigen Kriterium zur Parameterwahl.

>[!lemma] Lemma
> Wenn die Parameterwahl des Verfahrens
> $$B(2 + k) < \frac{\Delta}{2}$$
> erfüllt, ist eine korrekte Entschlüsselung garantiert

>[!proof] Beweis
> Folgt weitesgehend aus dem Beweis korrekter Entschlüsselung. Da $\Delta = \dfrac{q}{t}$, erhalten wir
> $$\begin{align}
> \frac{t}{q} B(2 + k) &< \frac{1}{2}\\
> \Delta^{-1} B(2+k) &< \frac{1}{2} \\
> B(2+k) &< \frac{\Delta}{2}
>\end{align}$$

### 14.3.3 Homomorphe Operationen
### Addition 
>[!remark] Bemerkung zur Darstellung der Entschlüsselung
> Im Beweis zur Korrektheit der Entschlüsselung sind wir an einer entscheidenden Stelle angekommen, und zwar dass jede BFV Entschlüsselung im Zähler der Entschlüsselung sich wie folgt darstellen lässt
> $$c_0 + \boldsymbol{c}_{1}^T \boldsymbol{s} = \Delta m + v$$
> Für die homomorphen Operationen werden wir diese Identität fortan verwenden, um die Korrektheit zu zeigen.

>[!lemma] Lemma BFV Homomorph Additiv
> BFV ist additiv homomorph. Die Addition zweier Chiffren $C_1 = \left( c_0^{(1)}, \boldsymbol{c}_{1}^{(1)}\right)$ und $C_2 = \left( c_0^{(2)}, \boldsymbol{c}_{1}^{(2)}\right)$ ist definiert als
> $$\begin{align}
> C_1 \oplus C_2 = \left(\left[c_0^{(1)} + c_0^{(2)}\right]_q, \left[\boldsymbol{c}_1^{(1)} + \boldsymbol{c}_1^{(2)}\right]_q\right)   
>\end{align}$$

>[!proof] Beweis
> Um zu zeigen, dass diese Vorschrift die korrekten Chiffren liefert, müssen wir zeigen, dass
> $$\text{Dec}(C_1) + \text{Dec}(C_2) = \text{Dec}(C_1 \oplus C_2)$$
> wahr ist. Also, 
> $$\begin{align}
> \text{Enc}(C_1 \oplus C_2) &= (\Delta m_1 + v_1) + (\Delta m_2 + v_2) \\
> &= \Delta(\underbrace{m_1 + m_2}_{=m_3}) + \underbrace{v_1 + v_2}_{= v_3} \\
> &= \text{Enc}(C_1 \oplus C_2) \\
> &= \text{Enc}(C_3) \tag*{$\square$}
>\end{align}$$

>[!lemma] Lemma Entschlüsselung einer addierten Chiffre
> Sei $C_3 = C_1 \oplus C_2$. Dann lässt sich $C_3$ korrekt entschlüsseln, wenn
> $$2 \frac{t}{q} (B2+k) = 2 \Delta^{-1}B(2+k) < \frac{1}{2}$$
> bzw. 
> $$\Delta^{-1}B(2+k) < \frac{1}{4}$$

>[!remark] Bemerkung
> Da wir $q \gg t$ gewählt haben, ist $\Delta^{-1} = \dfrac{t}{q}$ sehr klein.

>[!lemma] Lemma Anzahl der Additionen
> Ein Circuit soll $n$ Additionen erlauben, dann müssen die Verfahrensparameter folgende Ungleichung erfüllen
> $$B(2+k) < \frac{\Delta}{2n}$$

>[!proof] Beweis
> Sei $C_{n+1} = \sum_{i=1}^{n} C_i$. Dann ist das kumulierte Rauschen abzuschätzen mit
> $$n\Delta^{-1} B(2+k) < \frac{1}{2}$$
> bzw.
> $$B(2+k) < \frac{\Delta}{2n}$$
--- 
### Multiplikation

>[!remark] Bemerkung Herausforderungen mit der Multiplikation
> Die Multiplikation in FHE ist immer eine Herausforderung. Im Gegensatz zur Addition erhalten wir hier eine Chiffre, die tatsächlich aus 3 Komponenten bestehen wird.  Um das Problem zu illustrieren, stellen wir eine Entschlüsselung einer Chiffre als eine Funktion bezüglich unseres privaten Schlüssel $\boldsymbol{s} \in \mathbb{Z}_{2}^k$ dar. Sei $ct_i$ die Entschlüsselungsfunktion bezüglich einer chiffre $C_1$.
> $$ct_i(\boldsymbol{s}) = c_0^{(i)} + \boldsymbol{c}_{1}^{(i)^T} \boldsymbol{s}$$
> Multiplizieren wir zwei Chiffren $C_3 = C_1 \odot C_2$, so erhalten wir
> $$\begin{align}
> ct_3(\boldsymbol{s}) &= ct_1(\boldsymbol{s}) \cdot ct_2(\boldsymbol{s}) \\
> &= \left(c_0^{(1)} + \boldsymbol{c}_1^{(1)^T} \boldsymbol{s}\right) \cdot \left(c_0^{(2)} + \boldsymbol{c}_1^{(2)^T} \boldsymbol{s}\right) \\
> &= \underbrace{c_0^{(1)}c_0^{(2)}}_{=\widehat{c}_0} + \underbrace{\left(c_0^{(1)}\boldsymbol{c}_1^{(2)} + c_0^{(2)}\boldsymbol{c}_1^{(1)} \right)^T}_{=\widehat{\boldsymbol{c}}_1} \boldsymbol{s} + \underbrace{\boldsymbol{c}_1^{(1)^T} \boldsymbol{c}_1^{(2)}}_{=\widehat{c}_2} \underbrace{\boldsymbol{s}^2}_{= \boldsymbol{s}^T \boldsymbol{s}}\\
> &= \widehat{c}_0 + \widehat{\boldsymbol{c}}_1^T \boldsymbol{s} + \widehat{c}_2 \boldsymbol{s}^2
>\end{align}$$
> was ein Polynom zweiten Grades in $\boldsymbol{s}$ ist. Zunächst würde eine korrekte Entschlüsselung nun eine spezielle Entschlüsselung mit $\boldsymbol{s}^2$ erfordern, was technisch gesehen möglich ist. Jedoch würden künftige Operationen die Entschlüsselungskomplexität und das damit induzierte Rauschen exponentiell vergrößern.
>
> Relinearisierung hat das Ziel durch einen Relinearisierungsschlüssel die Chiffre **linear zu approximieren**, bzw. zu relinearisieren. Dazu wird im Evaluierungsschlüssel der private Schlüssel $\boldsymbol{s}$ quadratisch eingebettet und während der Relinearisierung maskiert. Es ist wichtig zu bemerken, dass in diesem Prozess ein Rauschterm entsteht. Wir werden nachgehend in einem naiven Beispiel sehen, weshalb hier anspruchsvolle Methoden entwickelt wurden, um das zusätzliche Rauschen zu minimieren.

>[!Lemma] Lemma BFV Homomorph Multiplikativ
> BFV ist homomorph multiplikativ. Die Multiplikation zweier Chiffren $C_1 = \left( c_0^{(1)}, \boldsymbol{c}_{1}^{(1)}\right)$ und $C_2 = \left( c_0^{(2)}, \boldsymbol{c}_{1}^{(2)}\right)$ mit
>$$C_3 = C_1 \otimes C_2$$
> Wir definieren die **quadratische Chiffre** $\widehat{C}$
> $$\begin{align}
> \widehat{c}_0 &= \left[\left\lfloor \frac{tc_0^{(1)} c_0^{(2)}}{q} \right\rceil\right]_q \\
> \widehat{\boldsymbol{c}}_1 &= \left[\left\lfloor \frac{t\left(c_0^{(1)} \boldsymbol{c}_1^{(2)} + c_0^{(2)} \boldsymbol{c}_1^{(1)}\right)}{q} \right\rceil\right]_q \\
> \widehat{c}_2 &= \left[\left\lfloor \frac{t \boldsymbol{c}_1^{(1)^T} \boldsymbol{c}_1^{(2)}}{q} \right\rceil\right]_q
> \end{align}$$
> Die Ausgabe der Multiplikation ist 
> $$C_3 = \left(c_0^{(3)}, \boldsymbol{c}_{1}^{(3)}\right) = Relin(\widehat{C}_{3}, rlk)$$
> wobei $rlk$ der Evaluierungsschlüssel ist.

>[!proof] Beweis
> Wir bemerken zunächst, dass jeder Bestandteil der quadratischen Chiffren den Faktor $\dfrac{t}{q}= \Delta^{-1}$ enthält. Aus der letzten Bemerkung wissen wir, dass die Entschlüsselung sich effektiv runterbrechen lässt auf
> $$\left[ \left\lfloor  \frac{t}{q} \left(\widehat{c}_{0} + \widehat{\boldsymbol{c}}_{1}^T \boldsymbol{s} + \widehat{c}_{2}\boldsymbol{s}^2\right)\right\rceil\right]_{t} \tag{1}$$
> Aufgrund der Herleitung wissen wir, dass 
> $$\widehat{c}_{0} + \widehat{\boldsymbol{c}}_{1}^T \boldsymbol{s} + \widehat{c}_{2}\boldsymbol{s}^2\ = \left(c_0^{(1)} + \boldsymbol{c}_{1}^{(1)^T}\boldsymbol{s}\right)\left(c_0^{(2)} + \boldsymbol{c}_{1}^{(2)^T}\boldsymbol{s}\right) = (\Delta m_1 + v_1)(\Delta m_2 + v_2)$$
> Setzen wir das in Term (1) ein erhalten wir
> $$\begin{align}
> \left[ \left\lfloor  \frac{t}{q} \left( \Delta m_1 + v_1\right)(\Delta m_2 + v_2)\right\rceil\right]_{q} &= \left[ \left\lfloor  \frac{t}{t} \left( \Delta^2 m_1 m_2 + \Delta m_1 v_2 + \Delta m_2 v_1 + v_1 v_2\right)\right\rceil\right]_{t} \\
> &= \left[ \left\lfloor  \Delta m_1 m_2 + m_1 v_2 + m_2 v_1 + \frac{t v_1 v_2}{q} \right\rceil\right]_{t} 
> \end{align}$$
> was eine korrekte Chiffre darstellt mit $m_3 = m_1 m_2$ und $v_3 = m_1v_2 + m_2 v_1 + \frac{tv_1v_2}{q}$, sodass
> $$\text{Dec}(C_1 \otimes C_2) = \text{Dec}(C_3) = \Delta m_3 + [\lfloor v_3 \rceil]_{t}\tag*{$\square$}$$

>[!Lemma] 
> Das durch eine Multiplikation induzierte Rauschen $v_{mult}$ lässt sich abschätzen mit
> $$\left\vert\left\vert\, v_{mult} \,\right\vert\right\vert_\infty \leq B(k+2)t$$

>[!proof] Beweis
> In der Multiplikation entsteht der Term $v_3$. Damit die Entschlüsselung uns garantiert das korrekte $m_3$ liefert, verlangen wir, dass
> $$\left\vert\left\vert\, v_{mult} \,\right\vert\right\vert_\infty < \frac{1}{2}$$
> Wir prüfen wie groß das Rauschen maximal werden kann, also
> $$\begin{align}
> \left\vert\left\vert\, v_{mult} \,\right\vert\right\vert_\infty &= \left\vert\left\vert\, m_1v_2 + m_2 v_1 + \frac{tv_1v_2}{q} \,\right\vert\right\vert_{\infty} \\
> &\leq \left\vert\left\vert\, m_1 v_2 \,\right\vert\right\vert_\infty + \left\vert\left\vert\, m_2v_1 \,\right\vert\right\vert_{\infty} + \left\vert\left\vert\, \frac{t}{q} v_1v_2 \,\right\vert\right\vert_\infty \tag{Dreiecksungleichung}
>\end{align}$$
> wir erinnern uns, dass $v_i = e_0 + \boldsymbol{s}^T \boldsymbol{e}_{1} - ue$. Für den weiteren Beweis lassen wir die Indizes weg und nehmen an, dass die Terme gleich sind, da wir ohnehin nur an einer Maximalschätzung interessiert sind. Ohne Beschränkung der Allgemeinheit erhalten wir
> $$\begin{align}
> 2\left\vert\left\vert\, m v \,\right\vert\right\vert_\infty + \left\vert\left\vert\, \frac{t}{q} v^2 \,\right\vert\right\vert_\infty &= 2\left\vert\left\vert\, m (e_0 + \boldsymbol{s}^T \boldsymbol{e}_{1} - ue) \,\right\vert\right\vert_\infty  + \frac{t}{q} \left\vert\left\vert\, v \,\right\vert\right\vert_\infty^2\\
> &\leq 2\Big( \left\vert\left\vert\, me_0 \,\right\vert\right\vert_\infty + \left\vert\left\vert\, m \boldsymbol{s}^T \boldsymbol{e}_1 \,\right\vert\right\vert_\infty + \left\vert\left\vert\, -mue \,\right\vert\right\vert_\infty \Big) + \frac{t}{q} \left\vert\left\vert\, v \,\right\vert\right\vert_\infty^2 \\ 
>\end{align}$$
> Wir schätzen die Terme einzeln ab. Für $\left\vert\left\vert\, v \,\right\vert\right\vert_\infty$  nutzen wir das Resultat aus der Abschätzung der Addition und erhalten $$\begin{align}
> \left\vert\left\vert\, me_0 \,\right\vert\right\vert_\infty &= \frac{Bt}{2} \\
> \left\vert\left\vert\, m \boldsymbol{s}^T \boldsymbol{e}_1 \,\right\vert\right\vert_\infty &= \frac{t}{2} \left\vert\left\vert\, \boldsymbol{s} \,\right\vert\right\vert_1 \cdot \left\vert\left\vert\, \boldsymbol{e}_1 \,\right\vert\right\vert_\infty = \frac{Btk}{2} \\
> \left\vert\left\vert\, -mue \,\right\vert\right\vert_\infty &= \frac{Bt}{2} \\
> \left\vert\left\vert\, v \,\right\vert\right\vert_\infty^2 &= (B(k+2))^2 
>\end{align}$$
> Führen wir die Terme zusammen erhalten wir
> $$\begin{align}
> \left\vert\left\vert\, v_{mult} \,\right\vert\right\vert_\infty &\leq 2 \left(\frac{Bt}{2}+ \frac{Btk}{2}+ \frac{Bt}{2}\right)  + \frac{t}{q}(B(k+2))^2 \\
> &= Bt(k+2) + \frac{t}{q}(B(k+2))^2 \\
> &= Bt(k+2) \left(1+ \frac{1}{q}B(k+2) \right) \\
> &\approx Bt(k+2)
>\end{align}$$
> Da $q$ mit $q \gg t$ sehr groß ist, ist der Term mit $1/q$ verschwindend klein, weshalb wir nur den Term $Bt(k+2)$ als Abschätzung des Rauschwachstums durch eine Multiplikation angeben. $$\tag*{$\square$}$$

>[!remark] Bemerkung zur Anzahl der Multiplikationen
> Damit wir eine sinnvolle Aussage zur Anzahl der Multiplikationen treffen können, müssen wir uns zunächst darum kümmern die quadratische Chiffre zu relinearisieren, da wir ansonsten exponentielles Wachstum auf das abgeschätzte Rauschen erhalten würden.

>[!remark] Motivation Naive Relinearisierung
> Zur Veranschaulichung führen wir eine naive Relinearisierung ein. Die Idee ist wie zuvor angedeutet den privaten Schlüssel quadratisch im Schlüssel einzubetten. Dazu definieren wir
> $$rlk := \left( \left[ - (\boldsymbol{a}_{0}^T \boldsymbol{s} + e_{0}) + \boldsymbol{s}^2\right]_{q},  \boldsymbol{a}_{0}\right) = (r_0, \boldsymbol{r}_{1})$$
> wobei $\boldsymbol{a}_{0} \in_R \mathbb{Z}_{q}^k$ und $e_0 \in \chi$. Sei $\widehat{C}= \left( \widehat{c}_{0}, \widehat{\boldsymbol{c}}_{1}, \widehat{c}_{2}\right)$ eine quadratische Chiffre, dann definieren wir die **naive Relinearisierung** als
> $$Relin\left( \widehat{C} \right) = (c_0, \boldsymbol{c}_{1})$$
> mit 
>$$\begin{align}
> c_0  &=\big[\widehat{c}_{0} + r_0 \widehat{c}_{2}\big]_q \\
> &=\big[\widehat{c}_{0} - \widehat{c}_{2}\boldsymbol{a}_0^T\boldsymbol{s} - \widehat{c}_{2}e_0 + \widehat{c}_{2}\boldsymbol{s}^2\big]_q \\
> \boldsymbol{c}_1  &=\big[\widehat{\boldsymbol{c}}_{1} + \boldsymbol{r}_1 \widehat{c}_{2}\big]_q \\
> &=\big[\widehat{\boldsymbol{c}}_{1} + \widehat{c}_{2}\boldsymbol{a}_0\big]_q 
>\end{align}$$
> und erhalten den relinearisierten Schlüssel $C = (c_0, \boldsymbol{c}_{1})$. Wir zeigen kurz, dass wenn wir eine relinearisierte Chiffre entschlüsseln, dass wir effektiv weiterhin denselben Ausdruck entschlüsseln. Dazu betrachten wir wieder die Chiffren als eine Funktion in $\boldsymbol{s}$ und schreiben
> $$\begin{align}
> c_0 + \boldsymbol{c}_1^T\boldsymbol{s} &= \underbrace{\widehat{c}_{0} - \widehat{c}_{2}\boldsymbol{a}_0^T\boldsymbol{s} - \widehat{c}_{2}e_0 +  \widehat{c}_{2}\boldsymbol{s}^2}_{=c_0'} + \big(\underbrace{\widehat{\boldsymbol{c}}_{1} + \widehat{c}_{2}\boldsymbol{a}_0}_{=\boldsymbol{c}_1'}\big)^T\boldsymbol{s} \\
> &= \widehat{c}_{0} + \widehat{\boldsymbol{c}}_{1}^T\boldsymbol{s}  + \widehat{c}_{2}\boldsymbol{s}^2 \underbrace{-\widehat{c}_{2}e_0}_{\text{relin error} } 
> \end{align}$$
> was zeigt, dass wir weiterhin denselben Ausdruck entschlüsseln, wenn die quadratische Chiffre relinearisiert wurde. Relinearisierungsverfahren sind für gewöhnlich anspruchsvoller, um das Relinearisierungsrauschen möglichst klein zu halten. Wir können einfach sehen, dass
>$$\left\vert\left\vert\, -\widehat{c}_{2} e_0 \,\right\vert\right\vert_\infty = \frac{Bq}{2}$$
> da $\widehat{c}_{2} \in \mathbb{Z}_{q}$.

>[!lemma] Lemma Basenreduktions Relinearisierung Multiplikativer Chiffren
> Sei $\widehat{C} = \left( \widehat{c}_{0}, \widehat{\boldsymbol{c}}_{1}, \widehat{c}_{2} \right)$ eine quadratische multiplikative Chiffre. Außerdem sei $$rlk= \left(r_0^{(i)}, \boldsymbol{r}_{1}^{(i)}\right)_{i=0}^{\ell} = \Big(\big[-\left(\boldsymbol{a}_{i}^T\boldsymbol{s}+e_{i}\right)+T^i \cdot \boldsymbol{s}^2\big]_{q},\; \boldsymbol{a}_{i}\Big)_{i=0}^\ell$$ der [[#^3009de|Relinearisierungsschlüssel]]. Die Relinearisierung wird wie folgt durchgeführt
>$$\begin{align}
> \widehat{c}_2 &= \sum_{i=0}^{\ell} \widehat{c}_2^{(i)} T^i \tag{Basenzerlegung zur Basis $T$}\\
> c_0 &= \left[ \widehat{c}_0 + \sum_{i=0}^{\ell} r_0^{(i)} \cdot \widehat{c}_2^{(i)}\right]_q \\
> \boldsymbol{c}_1 &= \left[ \widehat{\boldsymbol{c}}_1 + \sum_{i=0}^{\ell} \boldsymbol{r}_1^{(i)} \cdot \widehat{c}_2^{(i)}  \right]_q
>\end{align}$$
> Es wird die relinearisierte Chiffre $C = (c_0, \boldsymbol{c}_{1})$ zurückgegeben.

>[!proof] Beweis 
> Wir zeigen, dass die Relinearisierung $C = (c_0, \boldsymbol{c}_{1})$ die quadratische Chiffre enthält. Wir nehmen die Definitionen und erhalten
>$$\begin{align}
>\widehat{c}_2 &= \sum\limits_{i=0}^\ell \widehat{c}_2^{(i)}T^i \tag{Basenzerlegung}\\ 
>c_{0} &= \left[ \widehat{c}_{0} + \sum\limits_{i=0}^{\ell} r_0 \cdot \widehat{c}_2^{(i)}  \right]_{q} \\
>&= \left[ \widehat{c}_{0} + \sum\limits_{i=0}^{\ell} \Big(-(\boldsymbol{a}_i^T\boldsymbol{s}+e_i) +T^i\boldsymbol{s}^2\Big) \widehat{c}_2^{(i)}  \right]_{q} \\
>&=\Bigg[ \widehat{c}_{0} + \sum\limits_{i=0}^{\ell} -\widehat{c}_2^{(i)}(\boldsymbol{a}_i^T\boldsymbol{s}+e_i)  +{\underbrace{\sum\limits_{i=0}^{l}T^i\widehat{c}_2^{(i)}}_{ = \widehat{c}_2}}\boldsymbol{s}^2  \Bigg]_{q} \\
>&=\left[ \widehat{c}_{0} + \sum\limits_{i=0}^{\ell} -\widehat{c}_2^{(i)}(\boldsymbol{a}_i^T\boldsymbol{s}+e_i)  +\widehat{c}_2\boldsymbol{s}^2  \right]_{q} \\
>\boldsymbol{c}_{1} &= \left[ \widehat{\boldsymbol{c}}_{1} + \sum\limits_{i=0}^{\ell} \boldsymbol{r}_1 \widehat{c}_2^{(i)}  \right]_{q} \\
>&= \left[ \widehat{\boldsymbol{c}}_{1} + \sum\limits_{i=0}^{\ell}\boldsymbol{a}_i \widehat{c}_2^{(i)}  \right]_{q}
>\end{align}$$
> Wenden wir nun die Verschlüsselung in der reduzierten Schreibweise an, erhalten wir
> $$\begin{align}
> c_{0} +  \boldsymbol{c}_{1}^T\boldsymbol{s} &= \widehat{c}_{0} + \sum\limits_{i=0}^{\ell} -\widehat{c}_2^{(i)} (\boldsymbol{a}_i^T\boldsymbol{s}+e_i)  +\widehat{c}_2\boldsymbol{s}^2 + \left(\widehat{\boldsymbol{c}}_{1} + \sum\limits_{i=0}^{\ell}\boldsymbol{a}_i \widehat{c}_2^{(i)} \right)^T\boldsymbol{s} \\
>             &= \widehat{c}_{0} + \widehat{\boldsymbol{c}}_{1}^T\boldsymbol{s} +\widehat{c}_2\boldsymbol{s}^2 \cancel{- \sum\limits_{i=0}^{\ell}\widehat{c}_2^{(i)} \boldsymbol{a}_i^T\boldsymbol{s} + \sum\limits_{i=0}^{\ell}\widehat{c}_2^{(i)} \boldsymbol{a}_i^T\boldsymbol{s} } -\sum\limits_{i=0}^{\ell}\widehat{c}_2^{(i)} e_i\\
>             &= \underbrace{\widehat{c}_{0} + \widehat{\boldsymbol{c}}_{1}^T\boldsymbol{s} +\widehat{c}_2\boldsymbol{s}^2}_{\widehat{C}} -\sum\limits_{i=0}^{\ell}\widehat{c}_2^{(i)} e_i
> \end{align}$$
> wobei $r=\sum_{i=0}^{\ell}\widehat{c}_{2}^(i)e_i$ der Relinearisierungsfehler ist. Wir konnten zeigen, dass die quadratische Chiffre $\widehat{C}$ korrekt eingebettet wurde. $$\tag*{$\square$}$$

>[!lemma] Lemma
> Das durch eine **relinearisierte Multiplikation** induzierte Rauschen $v_{relin}$  lässt sich abschätzen mit
> $$\left\vert\left\vert\, v_{relin} \,\right\vert\right\vert_\infty \leq B(k+2)t + (\ell + 1) TB $$

>[!proof] Beweis
> Im vorherigen Beweis konnten wir sehen, dass sich die Relinearierung in der Entschlüsselung reduzieren lässt auf
> $$\widehat{C} - \sum_{i=0}^{\ell} \widehat{c}_{2}^{(i)}e_i$$
> Wir wissen aus dem Lemma des multiplikativen Rauschens, dass während der Entschlüsselung von $\widehat{C}$ wir ein Rauschen von
> $$\left\vert\left\vert\, v_{mult} \,\right\vert\right\vert_\infty \leq B(k+2)t$$
> erwarten können. Es verbleibt der Term $$\begin{align}
\left\vert\left\vert\, \sum_{i=0}^{\ell} \widehat{c}_2^{(i)}e_i \,\right\vert\right\vert_\infty \leq \sum_{i=0}^{\ell} \left\vert\left\vert\, \widehat{c}_{2}^{(i)} e_i\,\right\vert\right\vert_\infty \tag{Dreiecksungleichung} \\
\end{align}$$
> Da $\widehat{c}_{2}^{(i)}$ zur Basis $T$ dargestellt wurde, erhalten wir
> $$\left\vert\left\vert\, \sum_{i=0}^{\ell} \widehat{c}_2^{(i)}e_i \,\right\vert\right\vert_\infty \leq \ell TB$$
> Daher lässt sich das Rauschen durch relinearisierte Multiplikation abschätzen als
> $$\left\vert\left\vert\, v_{relin} \,\right\vert\right\vert \leq B(k+2)t + (\ell+1) TB$$

>[!lemma] Lemma Korrekte Entschlüsselung nach $n$ Multiplikationen
> Damit eine Entschlüsselung nach $n$ Multiplikationen korrekt ist, muss gelten
> $$\Big(B(k+2) + (\ell+1)TB\Big)t^n< \frac{\Delta}{2}$$
> bzw.
> $$B(k+2) + (\ell+1)TB < \frac{\Delta}{2t^n}$$

>[!proof] Beweis
> Sei $\widetilde{C}$ eine Chiffre nach einer relinearisierten Multiplikation und $C$ eine frische Chiffre (frisch verschlüsselt). Wir schauen uns die Entschlüsselung des Produktes dieser Chiffren an in der reduzierten Schreibweise. Wir lassen für die Rauschabschätzung die Indizes für die Klartextnachrichten weg.
> $$\begin{align}
> \text{Dec}\left( \widetilde{C} \otimes C\right)&= \left[\left\lfloor \frac{t}{q} (\Delta m + v_{relin}) (\Delta m + v) \right\rceil\right]_t \\
> &= \Delta m + \left[\left\lfloor m(v_{relin} + v) + \frac{t(v_{relin} + v)}{q} \right\rceil\right]
>\end{align}$$
> Für die Abschätzung des Rauschens betrachten wir lediglich den dominanten Term $m(v_{relin} + v)$, da durch $q \gg t$ der Beitrag insignifikant ist. Wir haben also
> $$\begin{align}
> \left\vert\left\vert\, m(v_{relin} + v) \,\right\vert\right\vert_\infty &\leq \underbrace{\frac{t}{2}}_{\left\vert\left\vert\, m \,\right\vert\right\vert_\infty}\Big(\underbrace{B(k+2)t + (\ell+1)TB}_{\left\vert\left\vert\, v_{relin} \,\right\vert\right\vert_{\infty}} + \underbrace{B(k+2)}_{=\left\vert\left\vert\, v \,\right\vert\right\vert_\infty}\Big) \\
> &= \frac{1}{2} \Big( B(k+2)t^2 + B(k+2)t + (\ell+1)TBt \Big) \\
> &\leq B(k+2)t^2 + B(k+2)t + (\ell+1)TBt\\
>\end{align}$$
> Nach $n$ Multiplikationen erhalten wir
> $$\left\vert\left\vert\, m(v_{relin}^{(n-1)} + v) \,\right\vert\right\vert \leq \left(\sum_{i=1}^{n} B(k+2)t^{i} \right) + \left( \sum_{i=0}^{n-1}(\ell+1)TBt^i \right)$$
> Damit wir schönere Ausdrücke erhalten wollen wir die Form der geometrischen Summe anwenden für ein positives $t>0$ (Achtung, wenn $t$ negativ sein kann, dürfen wir die geometrische Summe so nicht schreiben), also
> $$\sum_{i=0}^{n} t^i = \frac{t^{n+1}-1}{t-1}$$
> Wir fahren fort mit
>$$\begin{align}
> \left\vert\left\vert\, m(v_{relin}^{(n-1)} + v) \,\right\vert\right\vert &\leq B(k+2)\left(\sum_{i=1}^{n} t^{i} \right) + (\ell+1)TB\left( \sum_{i=0}^{n-1}t^i \right) \\
>  &\leq B(k+2)\left(\sum_{i=0}^{n} t^{i} \right) + (\ell+1)TB\left( \sum_{i=0}^{n}t^i \right) \\
>  &\leq \Big(B(k+2) (\ell + 1)TB \Big)\left(\sum_{i=0}^{n} t^{i} \right)  \\
> &= \Big(B(k+2) + (\ell+1)TB\Big) \frac{t^{n+1}-1}{t-1} 
>\end{align}$$
> Wir schätzen den Ausdruck weiter ab, damit er etwas handlicher ist. Wir schauen uns den Faktor $\frac{t^{n+1}-1}{t-1}$ an und haben
> $$\begin{align}
> \frac{t^{n+1}-1}{t-1} &= \frac{t^{n+1}}{t-1} - \frac{1}{t-1} \\
> &\leq \frac{t^{n+1}}{t} - \frac{1}{t-1} \\
> &\leq t^n - \frac{1}{t-1}
>\end{align}$$
> Da $\frac{1}{t-1}$ verhältnismäßig klein ist, vernachlässigen wir diesen Term und runden auf 
> $$\approx t^n$$
> Das ergibt das kumulierte Rauschen nach $n$ relinearisierten Multiplikationen auf
> $$\left\vert\left\vert\, v_{relin}^{(n)}  \,\right\vert\right\vert \approx \Big(B(k+2) + (\ell+1)TB\Big)t^n$$
> Beim Entschlüsseln Skalieren wir mit $\Delta^{-1}$ zurück und erhalten final als Bedingung
> $$\Big(B(k+2) + (\ell+1)TB\Big)t^n < \frac{\Delta}{m} \tag*{$\square$}$$

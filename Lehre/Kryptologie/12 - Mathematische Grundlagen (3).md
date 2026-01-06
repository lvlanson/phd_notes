### 13.1 Einführung Gitter (Lattices)
>[!remark] Motivation
>In den vergangenen Kapiteln haben wir hauptsächlich auf Restklassenstrukturen $\mathbb{Z}_{n}$ gearbeitet. Wir erweitern dieses Konzept jetzt auf mehrdimensionale Restklassenstrukturen.

>[!remark] Notation
> Von hieran werden wir mit Vektoren arbeiten. Vektoren werden immer in fetter Druckschrift gekennzeichnet, also $\boldsymbol{x} \in V$. Wenn nicht anders gekennzechnet entspringen Vektoren aus einem $n$-dimensionalen Vektorraum. 

>[!def] Definition $n$-dimensionale Gitter $\mathcal{L}$
> Wir bezeichnen ein $n$-dimensionales Gitter $\mathcal{L} \subset \mathbb{R}^n$ wenn gilt:
> 1. $\mathcal{L}$ bildet eine additive Untergruppe
> 2. $\mathcal{L}$ ist diskret, das heißt:
> Es existiert ein $\lambda >0$, sodass alle Gitterpunkte $\boldsymbol{x}, \boldsymbol{y} \in \mathcal{L}$ mindestens Distanz $\lambda$ haben, also
> $$ \lambda = \min_{\boldsymbol{x},\boldsymbol{y} \in \mathcal{L}} d(\boldsymbol{x}, \boldsymbol{y})$$
> wobei die euklidische Distanz definiert ist als $$ d(\boldsymbol{x}, \boldsymbol{y}) = || \boldsymbol{x} - \boldsymbol{y} ||_E = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}$$
>
> Das durch $\boldsymbol{b}_1, \ldots, \boldsymbol{b}_n \in \mathbb{R}^n$ aufgespannte Gitter ist definiert als
> $$\mathcal{L}(\boldsymbol{b}_1, \ldots, \boldsymbol{b}_m) = \left\{\sum_{i=1}^n x_i \boldsymbol{b}_i \; | \; x_i \in \mathbb{Z} \right\}$$
> mit $\boldsymbol{b}_i \in \mathbb{R}^n$ seien Basisvektoren in $0 < m \leq n$. Wir bezeichnen das Gitter als Gitter mit vollem Rang, wenn $m = n$ gilt.

>[!remark] Bemerkung zur Notation
> Ein Gitter wird üblicherweise über eine Basis $\boldsymbol{B} = (\boldsymbol{b}_1, \ldots, \boldsymbol{b}_m)$ mit $m \leq n$ erzeugt. Also $$\mathcal{L} = \mathcal{L}(\boldsymbol{B}):= \boldsymbol{B}\cdot \mathbb{Z}^m = \left\{\sum_{i=1}^m z_i \boldsymbol{b}_i \; | \; z_i \in \mathbb{Z}\right\}$$
> In der Literatur wird ein Gitter auch gesondert mit großen griechischen Symbolen gekennzeichnet wie zum Beispiel $\Lambda = \mathcal{L}(\boldsymbol{B})$. $\mathcal{L}$ hingegen wird als Operator verstanden, der über eine Basis $\boldsymbol{B}$ dieses Gitter erzeugt, also $\Lambda = \mathcal{L}(\boldsymbol{B})$. Wir werden ab hier einfach nur von $\mathcal{L}$ sprechen, um die Notation etwas zu vereinfachen.
 
>[!example] Beispiel
> - das einfachste Gitter $\mathbb{Z}^n$
> - das skalierte Gitter $n\mathcal{L}$
> - das Schachbrett Gitter $\{\boldsymbol{x} \in \mathcal{L}: \left(\sum_{i} x_i\right) \text{ mod } 2 = 0\}$
> 
>Bild eines Gitters in $\mathbb{R}^2$:
>![[Figures/z2gitter.png | center | 450]]

^cbb503


>[!remark] Bemerkung zu Basen in Gittern
> Seien $\boldsymbol{b}_1, \ldots, \boldsymbol{b}_n \in \mathcal{L} \subset \mathbb{R}^n$ Basisvektoren von $\mathcal{L}$, dann spannt $\text{span}(\boldsymbol{b}_1, \ldots, \boldsymbol{b}_n)$ den $\mathbb{R}^n$ auf und erzeugt mit $\mathcal{L}(\boldsymbol{b}_1, \ldots, \boldsymbol{b}_n)$ das entsprechende Gitter. Wenn wir beliebige andere linear unabhängige Vektoren $\boldsymbol{b}_1', \ldots, \boldsymbol{b}_n' \in \mathcal{L}$, dann können diese zwar ebenfalls den $\mathbb{R}^n$ aufspannen, jedoch müssen diese nicht zwangsläufig das Gitter $\mathcal{L}(\boldsymbol{b}_1, \ldots, \boldsymbol{b}_n)$ erzeugen.
> 
> Beispielsweise seien
> $$\begin{align} \boldsymbol{b}_1 &= \begin{pmatrix} 1 \\ 2 \end{pmatrix} \\ \boldsymbol{b}_2 &= \begin{pmatrix} 1 \\ -1 \end{pmatrix} \end{align} $$
> dann sind $$ \begin{align} \boldsymbol{b}_1' &= \boldsymbol{b}_1 + \boldsymbol{b}_2 = \begin{pmatrix} 2 \\ 1 \end{pmatrix} \\ 
> \boldsymbol{b}_2' &= \boldsymbol{b}_1 - \boldsymbol{b}_2 = \begin{pmatrix} 0 \\ 3 \end{pmatrix} \end{align}$$
> linear unabhängige Vektoren. Zwar ist $\text{span}(\boldsymbol{b}_1, \boldsymbol{b}_2) = \text{span}(\boldsymbol{b}_1', \boldsymbol{b}_2')$, jedoch $\mathcal{L}({\boldsymbol{b}_1, \boldsymbol{b}_2}) \neq \mathcal{L}(\boldsymbol{b}_1', \boldsymbol{b}_2')$.

>[!def] Definition Norm eines Vektors
> Die Norm ist eine Funktion auf Vektoren. Für alle Vektoren $\boldsymbol{u},\boldsymbol{v} \in V$ und alle Skalare $\alpha \in \mathbb{K}$ muss gelten 
> 1. $||\boldsymbol{u}|| \geq 0$ (positive Definitheit)
> 2. $||\boldsymbol{u}|| = 0 \iff \boldsymbol{u} = \boldsymbol{0}$ 
> 3. $||\alpha \boldsymbol{u}|| = |\alpha| \cdot ||\boldsymbol{u}||$ (absolute Homogenität) 
> 4. $||\boldsymbol{u} + \boldsymbol{v}|| \leq ||\boldsymbol{u}|| + ||\boldsymbol{v}||$ (Dreiecksungleich)

>[!remark] Bemerkung
> Die Norm $||  \cdot  ||_{E}$ aus der oben genannten Definition ist die **euklidische Norm**. Für $\boldsymbol{x} \in \mathbb{R}^n$ ist sie definiert als
> $$|| \boldsymbol{x}|| = \sqrt{\sum_{i=1}^n |x_i|^2}$$ 

### 13.2 Determinanten von Gittern

>[!remark] Motivation
> Wir werden jetzt das Werkzeug uns zusammensammeln, um das nächste nicht-effizient lösbare mathematische Problem zu formulieren, worauf moderne homomorphe kryptologische Verfahren basieren. 

>[!def] Definition Fundamentales Parallelepiped von Gittern
> Sei $\boldsymbol{B} = (\boldsymbol{b}_1, \ldots \boldsymbol{b}_n)$ eine Basis des Gitters $\mathcal{L}$, also $\mathcal{L}(\boldsymbol{B})$. Dann definieren wir das **fundamentale Parallelepiped von Gittern** $\mathcal{P}(\boldsymbol{B})$ mit $$ \mathcal{P}(\boldsymbol{B}) := \boldsymbol{B} \cdot [0, 1)^n$$

>[!example] Beispiel
> Ein Beispiel zum fundamentalen Parallelepiped kann in der Grafik zum Beispiel von [[#^cbb503 |oben]] gefunden werden. Dort ist die grau schraffierte Fläche das **fundamentale Parallelepiped**.

>[!remark] Bemerkung
> Seien $\boldsymbol{B}, \boldsymbol{B}'$ äquivalente Basen, das heißt sie erzeugen dasselbe Gitter $\mathcal{L}(\boldsymbol{B}) = \mathcal{L}(\boldsymbol{B}')$, dann folgt daraus dass das Volumen der entsprechenden fundamentalen Parallelepipeds gleich ist, also $\text{vol}(\mathcal{P}(\boldsymbol{B})) =\text{vol}(\mathcal{P}(\boldsymbol{B}'))$.
>
> Wir sind interessiert daran das **Volumen des Parallelepipeds** zu berechnen. Dazu müssen wir uns spezieller mathematischer Werkzeuge bedienen. Diese führen wir nachfolgend ein.

>[!def] Definition Inneres Produkt / Skalarprodukt
> Das innere Produkt des Vektorraums $V$ über Körper $\mathbb{K}$
> $$ \langle \cdot , \cdot \rangle: V \times V \to \mathbb{K}$$
> muss folgende Eigenschaften erfüllen. Für $\boldsymbol{u}, \boldsymbol{v}, \boldsymbol{w}$ und $\alpha, \beta \in \mathbb{K}$ gilt
> 1. Konjugiert Symmetrisch $\langle \boldsymbol{u}, \boldsymbol{v} \rangle = \overline{\langle \boldsymbol{v}, \boldsymbol{u}\rangle}$
> 2. Linear im ersten Argument $\langle \alpha \boldsymbol{u} + \beta \boldsymbol{v}, \boldsymbol{w} \rangle =  \alpha\langle\boldsymbol{u}, \boldsymbol{w}\rangle + \beta \langle \boldsymbol{v}, \boldsymbol{w}\rangle$
> 3. Positiv Definit $\boldsymbol{u} \neq \boldsymbol{0} \Longrightarrow \langle \boldsymbol{u}, \boldsymbol{u} \rangle > 0$

>[!remark] Bemerkung Eigenschaften
> Die erste und zweite Eigenschaft sind relevant für Vektorräume mit imaginären Einheiten. Für unsere Vektorräume können wir sagen, dass das Skalarprodukt symmetrisch und billinear ist, also
> 1. $\langle\boldsymbol{u}, \boldsymbol{v}\rangle = \langle\boldsymbol{v}, \boldsymbol{u}\rangle$
> 2. $\langle \alpha \boldsymbol{u} + \beta \boldsymbol{v}, \boldsymbol{w} \rangle =  \alpha\langle\boldsymbol{u}, \boldsymbol{w}\rangle + \beta \langle \boldsymbol{v}, \boldsymbol{w}\rangle$ und 
>  $\langle \boldsymbol{u}, \alpha \boldsymbol{v} + \beta \boldsymbol{w} \rangle =  \alpha\langle\boldsymbol{u}, \boldsymbol{v}\rangle + \beta \langle \boldsymbol{u}, \boldsymbol{w}\rangle$


>[!remark] Bemerkung Geometrische Interpretation des Skalarprodukts
> Das Skalarprodukt hilft uns Winkel zwischen Vektoren zu bestimmen, also der Winkel $\alpha$ zwischen $\boldsymbol{u}, \boldsymbol{v} \in V$ kann bestimmt werden mit $$ \alpha = \arccos \left(\frac{\langle \boldsymbol{u}, \boldsymbol{v} \rangle}{||\boldsymbol{u}||\,||\boldsymbol{v}||}\right)$$
>bzw.
>$$\langle \boldsymbol{u}, \boldsymbol{v} \rangle = \cos(\alpha) || \boldsymbol{u}|| \cdot ||\boldsymbol{v} ||$$
>Wir sehen, wenn $\alpha = 90°$, dann folgt $\langle \boldsymbol{u}, \boldsymbol{v} \rangle = \cos(90) = 0$.

>[!remark] Bemerkung Verbindung zur Norm
> Die Norm kann allgemein über das Skalarprodukt ausgedrückt werden, also für $\boldsymbol{u} \in V$
> $$ || \boldsymbol{v} || = \sqrt{\langle \boldsymbol{u}, \boldsymbol{u} \rangle}$$

>[!lemma] Proposition Inneres Produkt in Gittern
> Für das innere Produkt verwenden wir für dieses Thema das gewöhnliche Skalarprodukt. Für $\boldsymbol{u}, \boldsymbol{v} \in \mathcal{L}$ verwenden wir
> $$ \langle \boldsymbol{u}, \boldsymbol{v} \rangle = \boldsymbol{u}^T\boldsymbol{v} = \sum_{i=1}^n u_i\cdot v_i$$
> Wir dürfen annehmen, dass die oben genannten Eigenschaften hier erfüllt sind. Die Überprüfung dieser ist eine gute Übung.

>[!def] Definition Gram-Schmidt Orthogonalisierung
> Seien $\boldsymbol{u}_1, \ldots, \boldsymbol{u}_n$ linear unabhänige Vektoren. Dann erzeugt das folgende Verfahren die paarweise orthogonalen Vektoren $\boldsymbol{u}_1^*, \ldots, \boldsymbol{u}_n^*$.
> $$\begin{align}
> \boldsymbol{u}_1^* &= \boldsymbol{u}_1 \\
> \boldsymbol{u}_2^* &= \boldsymbol{u}_2 - \boldsymbol{u}_1^* \cdot \frac{\langle \boldsymbol{u}_2, \boldsymbol{u}_1^*\rangle}{\langle \boldsymbol{u}_1^*, \boldsymbol{u}_1^* \rangle}\\
> \boldsymbol{u}_3^* &= \boldsymbol{u}_3 - \boldsymbol{u}_1^* \cdot \frac{\langle \boldsymbol{u}_3, \boldsymbol{u}_1^*\rangle}{\langle \boldsymbol{u}_1^*, \boldsymbol{u}_1^* \rangle}- \boldsymbol{u}_2^* \cdot \frac{\langle  \boldsymbol{u}_3, \boldsymbol{u}_2^*\rangle}{\langle \boldsymbol{u}_2^*, \boldsymbol{u}_2^* \rangle} \\
> \vdots & \\
> \boldsymbol{u}_n^* &= \boldsymbol{u}_n - \sum_{i=1}^{n-1} \boldsymbol{u}_i^* \cdot \frac{\langle \boldsymbol{u}_n, \boldsymbol{u}_i^*\rangle}{\langle \boldsymbol{u}_i^*, \boldsymbol{u}_i^* \rangle}
> \end{align}$$

>[!remark] Bemerkung und Beispiel zum Orthogonalisierungprozess
> Nehmen wir für den Moment an, dass wir im $\mathbb{R}^2$ sind und zwei Vektoren haben $\boldsymbol{u}, \boldsymbol{v} \in \mathbb{R}^2$. Wir wollen $\boldsymbol{u}$ auf $\boldsymbol{v}$ projizieren und suchen den Projektionsvektor $\boldsymbol{p} \in \text{span}\{\boldsymbol{v}\}$.
>
> ![[Figures/orth_proj_1.png|center|300]]
> Um die Arbeit einfacher zu machen, macht es Sinn $\boldsymbol{v}$ zunächst auf eine normierte Länge von $1$ zu bringen. Die Norm eines Vektors gibt uns seine Länge zurück. Demnach, wenn wir einen Vektor durch seinen Norm dividieren, hat er dann genau Länge $1$. Wir definieren daher als erstes den nomierten Vektor
> $$\widehat{\boldsymbol{v}} = \frac{\boldsymbol{v}}{||\boldsymbol{v}||}$$
> Die Normiertheit von $\widehat{\boldsymbol{p}}$ hilft uns dabei die Länge der orthogonalen Projektion $\boldsymbol{p}$ zu bestimmen. Wir sehen uns die folgende Abbildung an
>
>![[Figures/orth_proj_2.png|center|300]] 
> Um die Länge $\ell$ zu bestimmen, verwenden wir hier den Kosinussatz, also 
> $$\cos(\alpha) = \frac{\ell}{||\boldsymbol{u}||} \iff \ell = \cos{\alpha}||\boldsymbol{u}||$$
> Wir bemerken, dass das Skalarprodukt $\langle \boldsymbol{u}, \widehat{\boldsymbol{v}} \rangle$ uns genau die Länge $\ell$ zurückgibt, also
> $$\begin{align} \langle \boldsymbol{u}, \widehat{\boldsymbol{v}} \rangle &= \cos(\alpha) ||\boldsymbol{u}|| \, \underbrace{||\widehat{\boldsymbol{v}}||}_{ = 1}  \\ 
>&= \cos(\alpha) ||\boldsymbol{u}||
>&= \ell = ||\boldsymbol{p}||
> \end{align}$$
> Da $\widehat{\boldsymbol{p}}$ bereits dieselbe Richtung von $\boldsymbol{p}$ hat, müssen wir lediglich um $\ell$ skalieren und erhalten damit die orthogonale Projektion
> $$\begin{align}
> \boldsymbol{p} &= \ell \cdot \widehat{\boldsymbol{v}}\\
> &= \langle \boldsymbol{u}, \widehat{\boldsymbol{v}} \rangle \cdot \widehat{\boldsymbol{v}} \tag{Skalarprodukt für $\ell$}\\
> &= \left\langle \boldsymbol{u}, \frac{\boldsymbol{v}}{||\boldsymbol{v}||} \right\rangle \frac{\boldsymbol{v}}{||\boldsymbol{v}||} \tag{Normiertheit von $\boldsymbol{v}$}\\
> &= \frac{1}{||\boldsymbol{v}||^2} \langle \boldsymbol{u}, \boldsymbol{v} \rangle \cdot \boldsymbol{v}  \tag{Linearität Skalarprodukt} \\
> &= \frac{\langle{\boldsymbol{u}, \boldsymbol{v}\rangle}}{\langle{\boldsymbol{v}, \boldsymbol{v}\rangle}} \cdot \boldsymbol{v} \tag{Zusammenhang Skalarprodukt und Norm}
> \end{align}$$
> Die Kathete zu $\boldsymbol{p}$ erhalten wir, indem wir $\boldsymbol{p}$ von ${boldsymbol{u}}$ abziehen, also
> $$ \begin{align}
> \boldsymbol{u}^*  &= \boldsymbol{u} - \boldsymbol{p} \\
> &= \boldsymbol{u} - \frac{\langle{\boldsymbol{u}, \boldsymbol{v}\rangle}}{\langle{\boldsymbol{v}, \boldsymbol{v}\rangle}} \cdot \boldsymbol{v} 
> \end{align}$$
> In höher dimensionalen Beispielen, nehmen wir die gefundenen Basen und spannen mit diesen eine Hyperebene auf $U_{k-1}= \text{span}\{\boldsymbol{u}_1, \ldots, \boldsymbol{u}_{k-1}\}$ und projizieren $\boldsymbol{u}_k$ darauf. Die Projektion $\boldsymbol{p}$ is nun die Projektion auf die Summe aller bereits gefundenen orthogonalen Basisvektoren, also $\boldsymbol{p}_k = \sum_{i=1}^{k-1} \frac{\langle \boldsymbol{u}_k, \boldsymbol{u}_i^*\rangle}{\langle \boldsymbol{u}_i^*, \boldsymbol{u}_i^*\rangle}$. Wir verfahren ab hier wie bereits festgestellt.

>[!lemma] Lemma Volumen des Parallelepipeds
> Seien $\boldsymbol{b}_1^*, \ldots, \boldsymbol{b}_n^*$ orthogonale Basisvektoren von $\mathcal{L}$, dann ist das Volumen des Parallelepipeds
> $$\text{vol}(\mathcal{L}) = \prod_{i=1}^n \boldsymbol{b}_i^* $$

>[!remark] Bemerkung zur Volumenberechnung
> Das Parallelepiped ist ein hochdimensionales Parallelelogramm, ähnlich wie der Würfel zum Quadrat oder das Quader zum Rechteck. In einem Parallelogramm benötigen wir Grundseite und Höhe um den Flächeninhalt zu berechnen
>
> ![[Figures/parallelogramm.png|center|300]]
> Nehmen wir wieder für einen Moment an, wir sind im zwei dimensionalen Raum, wie in der Abbildung zu sehen. Wenn wir das Gram-Schmidt Orthogonalisierungsverfahren anwenden, haben wir immer einen Vektor als Grundseite, in dem Fall der Abbildung $\boldsymbol{b}_1^* = \boldsymbol{b}_1$. Das Gram-Schmidt Orthogonalisierungsverfahren liefert uns das $\boldsymbol{h}$ aus der Abbildung, da $$\boldsymbol{h} = \boldsymbol{b}_2^* = \boldsymbol{b}_2 - \frac{\langle \boldsymbol{b}_1^*, \boldsymbol{b}_2\rangle}{\langle \boldsymbol{b}_1^*, \boldsymbol{b}_1^*\rangle} \boldsymbol{b}_1^*$$

### 13.3 Sukzessive Minima

>[!def] Definition Sukzessive Minimale Distanz $\lambda_i$ eines Gitters $\mathcal{L}$
> Sei $\mathcal{B}(r) = \{ \boldsymbol{x} \in \mathbb{R}^n \; | \; ||\boldsymbol{x}|| < r \}$ der offene Ball mit Zentrum $0$. Die $i$-te sukzessive minimale Distanz eines Gitters $\mathcal{L}$ ist definiert als
> $$ \lambda_i(\mathcal{L}) := \inf \{r \; | \; \dim(\text{span}(\mathcal{L} \cap \mathcal{B}(r))) \geq i\} $$

>[!remark] Bemerkung zur Definition
> Diese Definition mag etwas kompliziert aussehen. Zunächst beschreibt die Definition die Länge des $i$-ten kürzesten Vektors aus einer Menge von $i$ linear unabhängigen, kürzesten Vektoren im Gitter. Im Kern der Definition spannen wir einen Vektorraum über einen Schnitt zwischen einem offenen Ball und dem Gitter auf. Der $\dim$ Operator verrät uns wieviele linear unabhängige Vektoren in dem aufgespannten Schnitt zu finden sind. Wir geben das kleinste $r$ zurück, was uns mindestens $i$ linear unabhängige Vektoren liefert. Es ist zu bemerken, dass es ein höchstes $\lambda_i$ als $\lambda_n$ gibt, da ein Gitter vollen Ranges niemals mehr als $n$ linear unabhängige Vektoren haben kann.
>
> Auch bedenkt, dass das **Infimum** sagt, dass wir das **größte Element** suchen, was die Relation erfüllt. Dieses muss laut Definition des **Infimums** nicht zwangsläufig in der Menge selbst liegen.
>![[Figures/successive_minima.png|center|500]]

>[!remark] Bemerkung zur Bedeutung
> $\lambda_1$ beschreibt nicht nur den kürzesten Vektor im Gitter $\mathcal{L}$, sondern beschreibt außerdem die kürzest-mögliche Distanz zwischen zwei Gitterpunkten, also $$\lambda_1(\mathcal{L}) = \min_{\boldsymbol{x} \neq \boldsymbol{y} \in \mathcal{L}} || \boldsymbol{x} - \boldsymbol{y} ||$$

>[!remark] Bemerkung Weiteres Vorgehen
> Wir wissen nun
> - was ein Gitter $\mathcal{L}$ ist
> - was die $i$-te sukzessive minimale Distanz $\lambda_i$ ist
>
> Wir wollen nun zeigen, dass die Vektoren $\boldsymbol{v}_i$ mit Länge $\lambda_i=||\boldsymbol{v}_i||_E$ existieren.

>[!theorem] Satz Existenz einer positiven minimalen Distanz eines Gitters
> Sei $\boldsymbol{B}$ eine Base des Gitter $\mathcal{L}$ und $\mathcal{B}^*$ die entsprechende Gram-Schmidt Orthogonalisierung. Dann erfüllt das erste Minimum des Gitters
> $$\lambda_1 \geq \min_j ||\boldsymbol{b}_j^*|| > 0$$
> mit $\boldsymbol{b}^*_{i} \in \boldsymbol{B}^*$.
>>[!proof]- Beweis
>> Für diesen Beweis müssen wir uns einer bekannten und wichtigen Eigenschaft bedienen
>>>[!Lemma] Cauchy-Schwartz Ungleichung
>>> Seien $\boldsymbol{u}, \boldsymbol{v}$ aus einem Vektorraum $V$ mit innerem Produkt $\langle \cdot,\cdot\rangle$. Es gilt
>>> $$|\langle \boldsymbol{u}, \boldsymbol{v}\rangle| \leq ||\boldsymbol{u}|| \, ||\boldsymbol{v}||$$
>>
>> Sei $\boldsymbol{x} \in \mathbb{Z}^n$ und $\boldsymbol{B}$ eine entsprechende Basis für $\mathcal{L}$. Grundsätzlich ist zu zeigen, dass
>> $$ ||\boldsymbol{B}\boldsymbol{x}|| \geq || \boldsymbol{b}_i^*|| \geq \min_j ||\boldsymbol{b}_j^*||$$
>> Das heißt, dass jede Linearkombination mindestens die Länge eines unserer orthogonalisierten Basisvektoren hat, bzw. mindestens so groß sein muss wie unser kleinster orthogonalisierte Basisvektor.
>>
>>>[!remark] Bemerkung
>>> Da $\lambda_{1} =\underset{\boldsymbol{x} \in \mathbb{Z}^n}{\inf} ||\boldsymbol{Bx}||$ wissen wir, dass ein $j$ existiert, sodass $\lambda_{1} \geq \min_{j}\lvert\lvert \boldsymbol{b}_{j}^* \rvert\rvert$, da $\lvert\lvert \boldsymbol{b}_{j} \rvert\rvert \geq \lvert\lvert \boldsymbol{b}^*_{j} \rvert\rvert$
>>
>> Die **Strategie** für diesen Beweis wird wie folgt sein
>> - wir zeigen, dass $|\langle \boldsymbol{Bx}, \boldsymbol{b}_i^*\rangle| = ||\boldsymbol{b}_i^*||^2 x_i$ gilt (1)
>> - für $x_i \neq 0$ wissen wir $| x_i | > 0$ und können zeigen, dass jede Linearkombination mit $x_i$ größer oder gleich der Norm unseres orthogonalisierten Basisvektors ist (2)
>> - somit muss unser kürzester Vektor mindestens so groß sein, und ist somit größer als $0$
>>
>> Wir einigen uns zunächst darauf, dass für den Vektor $\boldsymbol{x}$ der Index $i$ der größte ist für den gilt $x_i \neq 0$. Das heißt sofern ein $x_k = 0$ existert, ist der Index $k > i$. Wir vereinfachen die Schreibweise der Gram-Schmidt Orthogonalisierung etwas, indem wir schreiben $\mu_{ij} = \frac{\langle \boldsymbol{b}_i^*, \boldsymbol{b}_j\rangle}{\langle\boldsymbol{b}_i^*, \boldsymbol{b}_i^*\rangle}$, sodass 
>> $$ \boldsymbol{b}_i^* = \boldsymbol{b}_i - \sum_{j=1}^n \mu_{ij}\boldsymbol{b}_j^*$$
>> 1. Wir wissen, dass $\boldsymbol{Bx} = \sum_{j=1}^{i} \boldsymbol{b}_jx_j$. Also
>> $$ \begin{align} 
>> \langle \boldsymbol{Bx}, \boldsymbol{b}_i^*\rangle &= \sum_{j=1}^i \langle \boldsymbol{b}_j x_i, \boldsymbol{b}_i^* \rangle \tag{Definition $\boldsymbol{Bx}$} \\ 
>> &= \sum_{j=1}^i \langle \boldsymbol{b}_j, \boldsymbol{b}_i^* \rangle x_i \tag{Linearitaet Skalarprodukt} \\
>> &= \langle \boldsymbol{b}_i, \boldsymbol{b}_i^*\rangle x_i \tag{Orthogonalitaet durch Gram-Schmidt} \\
>> &= \left\langle \boldsymbol{b}_i^* + \sum_{j=1}^i \mu_{ij} \boldsymbol{b}_j^*, \boldsymbol{b}_i^*\right\rangle x_i \tag{Definition Gram-Schmidt} \\
>> &= \langle \boldsymbol{b}_i^*, \boldsymbol{b}_i^*\rangle x_i + \mu_{ij}\underbrace{\left\langle \sum_{j=1}^i \boldsymbol{b}_j^*, \boldsymbol{b}_i \right\rangle}_{=0} x_i \tag{Linearitaet Skalarprodukt}\\
>> &= ||\boldsymbol{b}_i^*||^2 x_i \tag{Norm als Skalarprodukt}
>> \end{align}$$
>> 2. Da $x_i \neq 0$ können wir den Beweis abschließen mit
>> $$\begin{align}
>>|\langle \boldsymbol{Bx}, \boldsymbol{b}_i^* \rangle| = ||\boldsymbol{b}_i^*||^2 \cdot |x_i| \geq ||\boldsymbol{b}_i^*||^2 \tag*{$\square$}
>> \end{align}$$

>[!remark] Bemerkung
> Wir haben nun gezeigt, dass die minimale Distanz $\lambda_1$ in einem Gitter und der entsprechende Vektor dazu existiert. Dies lässt sich entsprechend auf jede beliebige sukzessive Distanz $\lambda_i$ erweitern.

---

## 13.4 Minkowskis Satz

^f6d48f

>[!theorem] Blichfeldts Satz
> Für jedes beliebige Gitter $\mathcal{L}$ and für jede beliebige messbare Menge $S \subseteq \text{span}(\mathcal{L})$ gilt, wenn $\text{vol}(S) > \text det(\mathcal{L})$, dann existieren zwei verschiedene Punkte $\boldsymbol{z}_1, \boldsymbol{z}_2 \in S$, sodass $\boldsymbol{z}_1 -\boldsymbol{z}_2 \in \mathcal{L}$.
>>[!proof]- Beweis
>> Zunächst partitionieren wir die Menge $S$ bezüglich der Parallelepipeds. Dazu definieren die Partition von S bezüglich $\boldsymbol{x} \in \mathcal{L}$ als
>> $$ S_{\boldsymbol{x}} = S \cap (\mathcal{P}(\boldsymbol{B}) + \boldsymbol{x})$$
>> wobei $\mathcal{P}(\boldsymbol{B}) + \boldsymbol{x} = \{ \boldsymbol{b}_i + \boldsymbol{x} \; | \; \boldsymbol{b_i} \in \mathcal{P}(\boldsymbol{B})\}$ die Verschiebung des Parallelepipeds um $\boldsymbol{x}$ ist. 
>>> [!pic]- Illustration
>>>Die folgenden Abbildungen beschreiben für ein $2$-dimensionales Gitter, was wir soweit definiert haben
>>>
>>>![[./Figures/blichfeldt_1.png | center | 500]]
>>> <center> Abbildung 1: Gitter und Menge S </center>
>>>
>>> wobei $\boldsymbol{b}_1, \boldsymbol{b}_2 \in \mathcal{L}$ Basisvektoren des Gitters $\mathcal{L}$ sind und $\mathcal{P}(\boldsymbol{B})$ das entsprechende fundamentale Parallelepiped ist. In Orange finden wir die Menge $S$, die das Gitter schneidet.
>>>
>>>![[./Figures/blichfeldt_2.png |  center | 500]] 
>>> <center> Abbildung 2: Schnitt mit verschobenen Parallelepipeds </center>
>>>
>>> In Grün sehen wir zwei verschobene Parallelepipeds, die $S$ schneiden. Den Schnitten haben wir als $S_{\boldsymbol{x}}$ definieret. Wir erkennen auch in der 2-dimensionalen Abbildung, dass die verschobenen Parallelepipeds $S$ partitionieren.
>> 
>> Da $S_{\boldsymbol{x}}$ die Menge $S$ partitionieren, können wir folgende Aussagen treffen
>> - da $S = \bigcup_{\boldsymbol{x} \in \mathcal{L}} S_{\boldsymbol{x}}$ wissen wir, dass alle $S_{\boldsymbol{x}}$ die Menge $S$ wieder zusammensetzen
>> - da $\mathcal{L}$ abzählbar ist, können wir das Volumen von $S$ als Summe der Volumen der einzelnen $S_{\boldsymbol{x}}$ darstellen, also $\text{vol}(S) = \sum_{\boldsymbol{x} \in \mathcal{L}} \text{vol}(S_{\boldsymbol{x}})$ 
>>
>> Wir definieren jetzt die rückverschobene Menge 
>> $$S_{\boldsymbol{x}}' = S_{\boldsymbol{x}} - \boldsymbol{x} = (S- \boldsymbol{x}) \cap \mathcal{P}(\boldsymbol{B})$$
>>>[!remark] Bemerkung 
>>> Wie in Abbildung 2 zu sehen ist, können Schnitte wie $\mathcal{P}(\boldsymbol{B}) + \boldsymbol{x}_2$ kleiner als ein vollständiges Parallelepiped sein, weshalb diese Schnitte paarweise unterschiedlich aussehen können. Dies wollen wir nachgehend noch mathematisch zeigen.
>>
>> Wir stellen fest
>> - $\text{vol}(S_{\boldsymbol{x}}) = \text{vol}(S_{\boldsymbol{x}}')$
>> - $S'_{\boldsymbol{x}} \subseteq \mathcal{P}(\boldsymbol{B})$
>>
>> Weiterhin wollen wir behaupten, dass alle Mengen $S_{\boldsymbol{x}}'$ nicht disjunkt sind, also $S_{\boldsymbol{x}}' \cap S_{\boldsymbol{y}}' \neq \emptyset$ mit $\boldsymbol{x}, \boldsymbol{y} \in \mathcal{L}$. Dies müssen wir zunächst noch zeigen. Wir zeigen über **Widerspruch** und nehmen zunächst an, dass diese disjunkt sind. Angenommen sie sind disjunkt, dann muss gelten
>> $$ \sum_{\boldsymbol{x} \in \mathcal{L}} \text{vol}(S_{\boldsymbol{x}}') = \text{vol}\left(\bigcup_{\boldsymbol{x} \in \mathcal{L}} S_{\boldsymbol{x}}'\right) \leq \text{vol}(\mathcal{P}(\boldsymbol{B})) \tag{1}$$
>>>[!remark] Bemerkung
>>> Wenn die Mengen nicht disjunkt sind, muss es Überlappungen geben zwischen den verschiedenen $S_{\boldsymbol{x}}'$, weshalb in der Summe Schnitte mehrfach gezählt werden, welche im Volumen der Vereinigung nicht mitgezählt werden. Daher kann die obige Gleichung nur wahr sein, wenn die Mengen disjunkt sind.
>>
>> Außerdem aus der Prämisse des Satzes können wir die Gültigkeit annehmen, dass
>> $$\sum_{\boldsymbol{x} \in \mathcal{L}} \text{vol}(S_{\boldsymbol{x}}') = \sum_{\boldsymbol{x} \in \mathcal{L}} \text{vol}(S_{\boldsymbol{x}}) = \text{vol}(S) > \text{det}(\mathcal{L}) \tag{2}$$
>> Kombinieren wir Aussagen $(1)$ und $(2)$ erhalten wir
>> $$\text{det}(\mathcal{L}) < \sum_{\boldsymbol{x} \in \mathcal{L}} \text{vol}(S_{\boldsymbol{x}}) \leq \text{vol}(\mathcal{P}(\boldsymbol{B}))$$
>> Laut der Definition der Determinante eines Gitters muss aber gelten, dass $\text{det}(\mathcal{L}) = \text{vol}(\mathcal{P}(\boldsymbol{B}))$, was ein Widerspruch ist. Daher kann es nicht-disjunkte $S_{\boldsymbol{x}}'$ geben.
>> 
>> Seien für den restlichen Beweis $S_{\boldsymbol{x}}', S_{\boldsymbol{y}}'$ zwei nicht-disjunkte Mengen, also $S_{\boldsymbol{x}}' \cap S_{\boldsymbol{y}}' \neq \emptyset$. Dann finden wir einen Vektor $\boldsymbol{z}$ in $S_{\boldsymbol{x}}' \cap S_{\boldsymbol{y}}'$ und definieren
>>$$\begin{align}
>> \boldsymbol{z}_1 &= \boldsymbol{z} + \boldsymbol{x} \tag{3} \\
>> \boldsymbol{z}_2 &= \boldsymbol{z} + \boldsymbol{y} \tag{4}
>>\end{align}$$
>>
>> Wir stellen fest
>> - da $\boldsymbol{z} \in S_{\boldsymbol{x}}'$ folgt, dass $\boldsymbol{z}_1 = \boldsymbol{z} + \boldsymbol{x} \in S_{\boldsymbol{x}} \subseteq S$
>> - da $\boldsymbol{z} \in S_{\boldsymbol{y}}'$ folgt, dass $\boldsymbol{z}_2 = \boldsymbol{z} + \boldsymbol{y} \in S_{\boldsymbol{y}} \subseteq S$
>> - da $\boldsymbol{z}_1 \neq \boldsymbol{z}_2 \implies \boldsymbol{x} \neq \boldsymbol{y}$
>>
>> Ziehen wir Gleichung $(3)$ von $(4)$ ab, erhalten wir die gesuchte Folgerung
>> $$\boldsymbol{z}_1 -\boldsymbol{z}_2 = \boldsymbol{x} - \boldsymbol{y} \in \mathcal{L} \tag*{$\square$}$$

^2f1ad4


>[!remark] Bemerkung
> Für folgenden Satz benötigen wir eine Definition, der eine Eigenschaft von Mengen beschreibt.

>[!def] Definition Konvexe Mengen
> Eine nicht leere Menge $X\subset \mathbb{R}^n$ wird **konvex** genannt, wenn für $\boldsymbol{x}, \boldsymbol{y} \in X$ und $\lambda \in [0,1]$ gilt, dass $(1-\lambda)\boldsymbol{x} + \lambda\boldsymbol{y} \in X$ ist.
>>[!remark] Bemerkung
>> Diese Definition sagt nichts anderes, als dass jede Gerade, die durch die Menge geht, vollständig in der Menge enthalten sein muss
>> 
>>![[./Figures/convexity.png | center | 500]]
>><center> Abbildung: Links eine konvexe Menge,<br> bei der die Gerade vollständig durchdringt.<br>Rechts eine nicht-konvexe Menge,<br>bei der die Gerade die Menge verlässt.</center>

>[!theorem] Minkowskis Gitterpunktsatz (Minkowskis Erster Satz)
> Sei $\mathcal{L}$ ein beliebiges Gitter mit vollem Rang $n$ und $S \subset \text{span}(\mathcal{L})$ eine beliebige konvexen Menge, die symmetrisch um den Koordinatenursprung ist. Wenn $\text{vol}(S) > 2^n \text{det}(\mathcal{L})$, dann muss $S$ einen vom Nullvektor verschiedenen Vektor $\boldsymbol{v} \in S \cap \mathcal{L} \setminus \{\boldsymbol{0}\}$ enthalten.
>>[!proof]- Beweis
>> Wir behelfen uns mit einer weiteren Menge 
>> $$S' = \left\{\frac{\boldsymbol{x}}{2} \; | \; \boldsymbol{x} \in S\right\}$$
>> welche alle Elemente von $S$ halbiert enthält. Vielmehr muss sich das Volumen dementsprechend pro Dimension mit halbieren, also
>> $$\text{vol}(S') = 2^{-n} \text{vol}(S) > \text{det}(\mathcal{L})$$
>>>[!remark] Bemerkung
>>> Dies ist gültig, da der Satz verlangt, dass $\text{vol}(S) > 2^n \text{det}(\mathcal{L})$ gilt.
>> 
>> Die Bedingungen für [[#^2f1ad4|Blichfeldts Satz]] sind somit erfüllt und wir können daraus schließen, dass zwei Vektoren $\boldsymbol{z}_1, \boldsymbol{z}_2 \in S'$ existieren, sodass $\boldsymbol{z}_1 - \boldsymbol{z}_2 \in \mathcal{L}$ gilt.
>> Wir stellen fest
>> - durch die Definition von $S'$ existieren $2\boldsymbol{z}_1, 2\boldsymbol{z}_2 \in S$
>> - da $S$ symmetrisch um den Koordinatenursprung ist, existiert $-2\boldsymbol{z}_2 \in S$
>> 
>> Da $S$ konvex ist, können wir die Definition der konvexen Mengen verwenden (mit $\lambda=\frac{1}{2}$), also dass der Punkt zwischen $2\boldsymbol{z}_1$ und $-2\boldsymbol{z}_2$ auch in $S$ liegen muss, also
>> $$\frac{2\boldsymbol{z}_1 + (-2\boldsymbol{z}_2)}{2} = \boldsymbol{z}_1 - \boldsymbol{z}_2 \in S$$
>> Somit existiert ein vom Nullvektor verschiedener Vektor $\boldsymbol{v} = \boldsymbol{z}_1 - \boldsymbol{z}_2$  in $S$. $$\tag*{$\square$}$$

^dd575b


>[!lemma] Korollar 
> Für ein beliebiges Gitter $\mathcal{L}$ mit vollem Rang gilt
> $$\lambda_1(\mathcal{L}) \leq \sqrt{n} \, \text{det}(\mathcal{L})^{1/n}$$
>>[!proof] Beweis
>> Sei $\mathcal{B}(r)$ ein Ball mit Radius $r$. Dann können wir einen Hyperwürfel in diesem Ball finden, dessen Seitenlängen sich einfach über das sukzessive Anwenden des Satzes des Pythagoras bestimmen lassen. Sei $2r$ die Diagonale durch den Hyperwürfel, dann lassen sich die Kantenlänge $a$ des Hyperwürfels bestimmen mit 
>>$$\begin{align}
>> (2r)^2 &= na^2 \\
>> 4r^2 &= na^2 \\
>> 2r &= \sqrt{n}a \\
>> \frac{2r}{\sqrt{n}} &= a
>>\end{align}$$
>> Das Volumen des Hyperwürfels $\mathcal{H}_r = \left[ -\dfrac{r}{\sqrt{n}}, \dfrac{r}{\sqrt{n}}\right]$ ist bestimmt mit
>> $$\text{vol}(\mathcal{H}_r) = \left(\frac{2r}{\sqrt{n}}\right)^n$$
>> somit wissen wir
>> $$\text{vol}(\mathcal{B}(r)) > \text{vol}(\mathcal{H}_r) = \left(\frac{2r}{\sqrt{n}}\right)^n$$ Nehmen wir für den Radius des Balls
>> $$r = \sqrt{n} \cdot \text{det}(\mathcal{L})^{1/n}$$ sodass das Volumen des Hyperwürfels sich wie folgt darstellt
>> $$\text{vol}\left(\mathcal{H}_{\sqrt{n}\cdot \text{det}(\mathcal{L})^{1/n}}\right) = 2\text{det}(\mathcal{L})$$
>> Nach [[#^dd575b|Minkowskis Gitterpunktsatz]] ist der Ball $\mathcal{B}(\sqrt{n}\text{det}(\mathcal{L})^{1/n}) > 2^n \text{det}(\mathcal{L})$ und enthält daher einen vom Nullvektor verschiedenen Vektor $\boldsymbol{v} \in \mathcal{B}(\sqrt{n}\cdot \text{det}(\mathcal{L}^{1/n})$. Der Vektor $\boldsymbol{v}$ kann maximal so lang sein wie der Radius des Balls indem er existiert, also
>> $$\lambda_1 = ||\boldsymbol{v}|| \leq \sqrt{n}\cdot\text{det}(\mathcal{L}^{1/n})$$
>> was die Aussage beweist. $$\tag*{$\square$}$$

>[!remark] Bemerkung zur Bedeutung Minkowskis Erstem Satzes
> Minkowski's erster Satz liefert uns eine obere Schranke für den kürzesten Vektor in einem Gitter mit vollem Rang $n$. Ein Vektor $\boldsymbol{v} \in \mathcal{L}$ ist höchstens
>$$ \lambda_1 = ||\boldsymbol{v}|| \leq \sqrt{n}\cdot\text{det}(\mathcal{L}^{1/n})$$

## 13.5 Mathematische Gitterprobleme

>[!remark] Bemerkung
> Wie gehabt nutzen wir nicht-effizient lösbare mathematische Probleme um kryptographische Verfahren zu bauen. Auf Basis der Abschätzung Minkowskis für die Länge eines kürzesten Vektors lassen sich solche Probleme für die Gitter formulieren. Bis heute ist kein effizientes Verfahren bekannt weder einen kürzesten Vektor in einem Gitter zu finden, noch überhaupt die Länge des kürzesten Vektors zu bestimmen.

>[!def] Definition Shortest Vector Problem (SVP)
> Sei $\boldsymbol{B} \in \mathbb{Z}^{m \times n}$ eine Basis für ein Gitter $\mathcal{L}$. SVP sucht den kürzesten nicht-null Vektor $\boldsymbol{Bx} \in \mathcal{L}$ mit $\boldsymbol{x} \in \mathbb{Z}^n\setminus\{\boldsymbol{0}\}$, sodass
> $$||\boldsymbol{Bx}|| \leq ||\boldsymbol{By}||$$
>für jeden anderen beliebigen Vektor $\boldsymbol{y} \in \mathbb{Z}^n\setminus\{\boldsymbol{0}\}$.

>[!def] Definition Closest Vector Problem (CVP)
> Sei $\boldsymbol{B}\in \mathbb{Z}^{m \times n}$ eine Basis für ein Gitter $\mathcal{L}$ und sei $\boldsymbol{z} \in \mathbb{Z}^m$ ein Zielvektor. CVP sucht einen Vektor $\boldsymbol{Bx} \in \mathcal{L}$ der am nächsten zu $\boldsymbol{t}$ ist, also sodass für $\boldsymbol{x} \in \mathbb{Z}^n$ gilt
>$$|| \boldsymbol{Bx} - \boldsymbol{t}|| \leq ||\boldsymbol{By} - \boldsymbol{t}||$$
> für beliebige $\boldsymbol{y} \in \mathbb{Z}^n$.

>[!remark] Bemerkung
> Mathematische Probleme im kryptographischen Kontext lassen sich unter folgende Unterprobleme gliedern. Diese Unterprobleme werden im Kontext der Gitterprobleme erklärt.
> - das **Suchproblem**: einen nicht-null Vektor zu finden, der eines der oben genannten Probleme löst
> - das **Optimierungsproblem**: die Länge des kürzesten Vektors bzw. die Distanz des nächsten Vektors zu finden
> - das **Entscheidungsproblem**: für eine gegebene Größe $r > 0$ zu entscheiden, ob ein Vektor $\boldsymbol{x}$ existiert, der entweder mindestens so groß ist, bzw. mindestens in dieser Distanz zu einem gegebenen Vektor $\boldsymbol{t}$ ist


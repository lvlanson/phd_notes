---
id: 13 - Mathematische Grundlagen (3)
aliases: []
tags: []
---
### 13.1 Einführung Gitter (Lattices)
>[!remark] Motivation
>In den vergangenen Kapiteln haben wir hauptsächlich auf Restklassenstrukturen $\mathbb{Z}_{n}$ gearbeitet. Wir erweitern dieses Konzept jetzt auf mehrdimensionale Restklassenstrukturen.

>[!remark] Notation
> Von hieran werden wir mit Vektoren arbeiten. Vektoren werden immer in fetter Druckschrift gekennzeichnet, also $\boldsymbol{x} \in V$. Wenn nicht anders gekennzechnet entspringen Vektoren aus einem $n$-dimensionalen Vektorraum. 

>[!remark] Bemerkung Vergleich Modul und Vektorraum
> Ein Modul ist die Verallgemeinerung eines Vektorraums. Ein Vektorraum setzt voraus, dass sowohl $(G, \oplus)$ also auch $( \setminus\{0\}, \odot)$ kommutative Gruppen sind, neben der Gültigkeit der Axiome für $\forall \boldsymbol{u}, \boldsymbol{v} \in G^n$ and $\lambda, \mu \in G$ 
>$$\begin{align} (\gamma \cdot \mu) \cdot \boldsymbol{u} &= \gamma \cdot (\mu \cdot \boldsymbol{u}) \\
\gamma \cdot (\boldsymbol{u} + \boldsymbol{v}) &= \gamma \cdot \boldsymbol{u} + \gamma \cdot \boldsymbol{v} \\
(\lambda + \mu) \cdot \boldsymbol{u} &= \lambda \cdot \boldsymbol{u} + \mu \cdot \boldsymbol{u} \end{align}$$
>
> In einem Modul jedoch ist die algebraische Struktur $(G\setminus\{0\}, \odot)$ keine kommutative Gruppe, sondern ein Ring. Für ein Ring gilt, dass dieser 
> 1. assoziativ ist
> 2. ein neutrales Element besitzt
> 3. ~ein inverses Element besitzt~
> 4. (kommutativ ist) (optional -> kommutativer Ring)

>[!def] Definition $n$-dimensionale Gitter $\mathcal{L}$
> Wir bezeichnen ein $n$-dimensionales Gitter $\mathcal{L} \subset \mathbb{R}^n$ wenn gilt:
> 1. $\mathcal{L}$ bildet eine additive Untergruppe
> 2. $\mathcal{L}$ ist diskret, das heißt:
> Es existiert ein $\lambda >0$, sodass alle Gitterpunkte $\boldsymbol{x}, \boldsymbol{y} \in \mathcal{L}$ haben mindestens Distanz $\lambda$, also
> $$ \lambda = \min_{\boldsymbol{x},\boldsymbol{y} \in \mathcal{L}} d(\boldsymbol{x}, \boldsymbol{y})$$
> wobei die euklidische Distanz definiert ist als $$ d(\boldsymbol{x}, \boldsymbol{y}) = || \boldsymbol{x} - \boldsymbol{y} ||_E = \sqrt{\sum_{i=1}^n (x_i - y_i)^2}$$
>
> Konkreter, seien $\boldsymbol{b}_1, \ldots, \boldsymbol{b}_n$ linear unabhängige Basisvektoren. Dann ist ein Gitter definiert als
> $$\mathcal{L}(\boldsymbol{b}_1, \ldots, \boldsymbol{b}_m) = \left\{\sum_{i=1}^n x_i \boldsymbol{b}_i \; | \; x_i \in \mathbb{Z} \right\}$$
> mit $\boldsymbol{b}_i \in \mathbb{R}^n$ und $0 < m \leq n$. Wir bezeichnen das Gitter als Gitter mit vollem Rang, wenn $m = n$ gilt.

>[!example] Beispiel
> - das einfachste Beispiel ist $\mathbb{Z}^n$
> - das skalierte Gitter $n\mathcal{L}$
> - das Schachbrett Gitter $\{\boldsymbol{x} \in \mathcal{L}: \left(\sum_{i} x_i\right) \text{ mod } 2 = 0\}$
>Bild eines Gitters in $\mathbb{R}^2$:
>![[Figures/z2gitter.png | center | 450]]

^cbb503

>[!remark] Bemerkung zur Notation
> Üblicherweise wird ein Gitter mit großen griechischen Symbolen gekennzeichnet wie zum Beispiel $\Lambda$. $\mathcal{L}$ hingegen wird als Operator verstanden, der über eine Basis $\boldsymbol{B}$ dieses Gitter erzeugt, also $\Lambda = \mathcal{L}(\boldsymbol{B})$. Wir werden ab hier einfach nur von $\mathcal{L}$ sprechen, um die Notation etwas zu vereinfachen.
 
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
> 1. $||\boldsymbol{u}|| \geq 0$
> 2. $||\boldsymbol{u}|| = 0 \iff \boldsymbol{u} = \boldsymbol{0}$
> 3. $||\alpha \boldsymbol{u}|| = |\alpha| \cdot ||\boldsymbol{u}||$
> 4. $||\boldsymbol{u} + \boldsymbol{v}|| \leq ||\boldsymbol{u}|| + ||\boldsymbol{v}||$
>
> Die Norm aus der oben genannten Definition ist die **euklidische Norm**, es gibt jedoch weitere Normen.

### 13.2 Determinanten von Gittern

>[!remark] Motivation
> Wir werden jetzt das Werkzeug uns zusammensammeln, um das nächste nicht-effizient lösbare mathematische Problem zu formulieren, worauf moderne homomorphe kryptologische Verfahren basieren. 

>[!def] Definition Fundamentales Parallelepiped von Gittern
> Sei $\boldsymbol{B} = (\boldsymbol{b}_1, \ldots \boldsymbol{b}_n)$ eine Basis des Gitters $\mathcal{L}$, also $\mathcal{L}(\boldsymbol{B})$. Dann definieren wir das **fundamentale Parallelepiped von Gittern** $\mathcal{P}(\boldsymbol{B})$ mit $$ \mathcal{P}(\boldsymbol{B}) := \boldsymbol{B} \cdot [0, 1)^n$$

>[!example] Beispiel
> Ein Beispiel zum fundamentalen Parallelepiped kann in der Grafik zum Beispiel von [[#^cbb503 |oben]] gefunden werden. Dort ist die grau schraffierte Fläche das **fundamentale Parallelepiped**.

>[!remark] Bemerkung
> Seien $\boldsymbol{B}, \boldsymbol{B}'$ äquivalente Basen, das heißt sie erzeugen dasselbe Gitter $\mathcal{L}(\boldsymbol{B}) = \mathcal{L}(\boldsymbol{B}')$, dann folgt daraus dass das Volumen der entsprechenden fundamentalen Parallelepipeds gleich ist, also $\text{Vol}(\mathcal{P}(\boldsymbol{B})) =\text{Vol}(\mathcal{P}(\boldsymbol{B}'))$.
>
> Wir sind interessiert daran das **Volumen des Parallelepipeds** zu berechnen. Dazu müssen wir uns spezieller mathematischer Werkzeuge bedienen. Diese führen wir nachfolgend ein.

>[!def] Definition Inneres Produkt / Skalarprodukt
> Das innere Produkt des Vektorraums $V$ über Körper $\mathbb{K}$
> $$ \langle \cdot , \cdot \rangle: V \times V \to \mathbb{K}$$
> muss folgende Eigenschaften erfüllen. Für $\boldsymbol{u}, \boldsymbol{v}, \boldsymbol{w}$ und $\alpha, \beta \in \mathbb{K}$ gilt
> 1. Konjugiert Symmetrisch $\langle \boldsymbol{u}, \boldsymbol{v} \rangle = \overline{\langle \boldsymbol{v}, \boldsymbol{u}\rangle}$
> 2. Linear im ersten Argument $\langle \alpha \boldsymbol{u} + \beta \boldsymbol{v}, \boldsymbol{w} \rangle =  \alpha\langle\boldsymbol{u}, \boldsymbol{w}\rangle + \beta \langle \boldsymbol{v}, \boldsymbol{w}\rangle$
> 3. Positiv Definit $\boldsymbol{u} \neq \boldsymbol{0} \Longrightarrow \langle \boldsymbol{x}, \boldsymbol{x} \rangle > 0$

>[!remark] Bemerkung Eigenschaften
> Die erste und zweite Eigenschaft sind relevant für Vektorräume mit imaginären Einheiten. Für unsere Vektorräume können wir sagen, dass das Skalarprodukt symmetrisch und billinear ist, also
> 1. $\langle\boldsymbol{u}, \boldsymbol{v}\rangle = \langle\boldsymbol{v}, \boldsymbol{u}\rangle$
> 2. $\langle \alpha \boldsymbol{u} + \beta \boldsymbol{v}, \boldsymbol{w} \rangle =  \alpha\langle\boldsymbol{u}, \boldsymbol{w}\rangle + \beta \langle \boldsymbol{v}, \boldsymbol{w}\rangle$ und 
>$\langle \boldsymbol{u}, \alpha \boldsymbol{v} + \beta \boldsymbol{w} \rangle =  \alpha\langle\boldsymbol{u}, \boldsymbol{v}\rangle + \beta \langle \boldsymbol{u}, \boldsymbol{w}\rangle$


>[!remark] Bemerkung Geometrische Interpretation des Skalarprodukts
> Das Skalarprodukt hilft uns Winkel zwischen Vektoren zu bestimmen, also der Winkel $\alpha$ zwischen $\boldsymbol{u}, \boldsymbol{v} \in V$ kann bestimmt werden mit $$ \alpha = \arccos \left(\frac{\langle \boldsymbol{u}, \boldsymbol{v} \rangle}{||\boldsymbol{u}||\,||\boldsymbol{v}||}\right)$$
>bzw.
>$$\langle \boldsymbol{u}, \boldsymbol{v} \rangle = \cos(\alpha) || \boldsymbol{v} \cdot \boldsymbol{w} ||$$
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
> \end{align}

>[!remark] Bemerkung und Beispiel zum Orthogonalisierungprozess
> Nehmen wir für den Moment an, dass wir im $\mathbb{R}^2$ sind und zwei Vektoren haben $\boldsymbol{u}, \boldsymbol{v} \in \mathbb{R}^2$. Wir wollen $\boldsymbol{u}$ auf $\boldsymbol{v}$ projizieren und suchen den Projektionsvektor $\boldsymbol{p} \in \text{span}\{\boldsymbol{v}\}$.
>
> ![[Figures/orth_proj_1.png|center|300]]
> Um die Arbeit einfacher zu machen, macht es Sinn $\boldsymbol{v}$ zunächst auf eine normierte Länge von $1$ zu bringen. Die Norm eines Vektors gibt uns seine Länge zurück. Demnach, wenn wir einen Vektor durch seinen Norm dividieren, hat er dann genau Länge $1$. Wir definieren daher als erstes den nomierten Vektor
> $$\widehat{\boldsymbol{v}} = \frac{\boldsymbol{v}}{||\boldsymbol{v}||}$$
> Die Normiertheit von $\widehat{\boldsymbol{p}}$ hilft uns dabei die Länge der orthogonalen Projektion $\boldsymbol{p}$ zu bestimmen. Wir sehen uns die folgende Abboldung an
>
>![[Figures/orth_proj_2.png|center|300]] 
> Um die Länge $\ell$ zu bestimmen, verwenden wir hier den Cosinussatz, also 
> $$\cos(\alpha) = \frac{\ell}{||\boldsymbol{u}||} \iff \ell = \cos{\alpha}||\boldsymbol{u}||$$
> Wir bemerken, dass das Skalarprodukt $\langle \boldsymbol{u}, \boldsymbol{v} \rangle$ uns genau die Länge $\ell$ zurückgibt, also
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
> $$\text{Vol}(\mathcal{L}) = \prod_{i=1}^n \boldsymbol{b}_i^* $$

>[!remark] Bemerkung zur Volumenberechnung
> Das Parallelepiped ist ein hochdimensionales Parallelelogramm, ähnlich wie der Würfel zum Quadrat oder das Quader zum Rechteck. In einem Parallelogramm benötigen wir Grundseite und Höhe um den Flächeninhalt zu berechnen
>
> ![[Figures/parallelogramm.png|center|300]]
> Nehmen wir wieder für einen Moment an, wir sind im zwei dimensionalen Raum, wie in der Abbildung zu sehen. Wenn wir das Gram-Schmidt Orthogonalisierungsverfahren anwenden, haben wir immer einen Vektor als Grundseite, in dem Fall der Abbildung $\boldsymbol{b}_1^* = \boldsymbol{b}_1$. Das Gram-Schmidt Orthogonalisierungsverfahren liefert uns das $\boldsymbol{h}$ aus der Abbildung, da $$\boldsymbol{h} = \boldsymbol{b}_2^* = \boldsymbol{b}_2 - \frac{\langle \boldsymbol{b}_1^*, \boldsymbol{b}_2\rangle}{\langle \boldsymbol{b}_1^*, \boldsymbol{b}_1^*\rangle} \boldsymbol{b}_1^*$$

### 13.3 Sukzessive Minima

>[!def] Definition Minimale Distanz $\lambda_1$ eines Gitters $\mathcal{L}$
> Die minimale Distanz eines Gitters $\mathcal{L}$ wird bezeichnet als
> $$\lambda_1(\mathcal{L}) := \min_{\boldsymbol{v} \in \mathcal{L} \setminus\{\boldsymbol{0}\}} ||\boldsymbol{v}||_E$$
> wobei $||\boldsymbol{v}||_E$ ist die Norm von $\boldsymbol{v}$ und wir berechnen diese als
> $$||\boldsymbol{v}||_E = \sqrt{\sum_{i} v_i^2}$$

>[!def] Definition Sukzessive Minimale Distanz $\lambda_i$ eines Gitters $\mathcal{L}$
> Sei $\overline{\mathcal{B}}(r) = \{ \boldsymbol{x} \in \mathbb{R}^n \; | \; ||\boldsymbol{x}|| \leq r \}$ der geschlossene Ball mit Zentrum $0$. Die $i$-te sukzessive minimale Distanz eines Gitters $\mathcal{L}$ ist definiert als
> $$ \lambda_i(\mathcal{L}) := \min \{r \; | \; \dim(\text{span}(\mathcal{L} \cap \overline{\mathcal{B}}(r))) \geq i\} $$

>[!remark] Bemerkung zur Definition
> Diese Definition mag etwas kompliziert aussehen. Zunächst beschreibt die Definition die Länge des $i$-ten kürzesten Vektors aus einer Menge von $i$ linear unabhängigen, kürzesten Vektoren im Gitter. Im Kern der Definition spannen wir einen Vektorraum über einen Schnitt zwischen einem offenen Ball und dem Gitter auf. Der $\dim$ Operator verrät uns wieviele linear unabhängige Vektoren in dem aufgespannten Schnitt zu finden ist. Wir geben das kleinste $r$ zurück, was uns mindestens $i$ linear unabhängige Vektoren liefert. Es ist zu bemerken, dass es ein höchstes $\lambda_i$ als $\lambda_n$ gibt, da ein Gitter vollen Ranges niemals mehr als $n$ linear unabhängige Vektoren haben kann.
>![[Figures/successive_minima.png|center|500]]

>[!remark] Bemerkung zur Bedeutung
> $\lambda_1$ beschreibt nicht nur den kürzesten Vektor im Gitter $\mathcal{L}$, sondern beschreibt außerdem die kürzest-mögliche Distanz zwischen zwei Gitterpunkten, also $$\lambda_1(\mathcal{L}) = \min_{\boldsymbol{x} \neq \boldsymbol{y} \in \mathcal{L}} || \boldsymbol{x} - \boldsymbol{y} ||$$

>[!remark] Bemerkung Weiteres Vorgehen
> Wir wissen nun
> - was ein Gitter $\mathcal{L}$ ist
> - was die $i$-te sukzessive minimale Distanz $\lambda_i$ ist
> Wir wollen nun zeigen, dass die Vekotren $||\boldsymbol{v}_i||_E$ mit Länge $\lambda_i$ existieren.

>[!theorem] Satz Existenz der minimalen Distanz eines Gitters
> Sei $\mathcal{B}$ eine Base des Gitter $\mathcal{L}$ und $\mathcal{B}^*$ die entsprechende Gram-Schmidt Orthogonalisierung. Dann, das erste Minimum des Gitters erfüllt
> $$\lambda_1 \geq \min_j ||\boldsymbol{b}_j^*|| > 0$$
>>[!proof]- Beweis
>> Für diesen Beweis müssen wir uns einer bekannten und wichtigen Eigenschaft bedienen
>>>[!Lemma] Cauchy-Schwartz Ungleichung
>>> Seien $\boldsymbol{u}, \boldsymbol{v} \in V$ aus einem Vektorraum mit innerem Produkt. Es gilt
>>> $$|\langle \boldsymbol{u}, \boldsymbol{v}\rangle| \leq ||\boldsymbol{u}|| \, ||\boldsymbol{v}||$$
>>
>> Sei $\boldsymbol{x} \in \mathbb{Z}^n$ und $\boldsymbol{B}$ eine entsprechende Basis für $\mathcal{L}$. Grundsätzlich ist zu zeigen, dass
>> $$ ||\boldsymbol{B}\boldsymbol{x}|| \geq || \boldsymbol{b}_i^*|| \geq \min_j ||\boldsymbol{b}_j^*||$$
>> Also, dass jede Linearkombination mindestens die Länge eines unserer orthogonalisierten Basisvektoren hat, bzw. mindestens so groß sein muss wie unser kleinster orthogonalisierte Basisvektor. Durch die Orthogonalisierung gilt $|| \boldsymbol{b}_i^*|| \leq ||\boldsymbol{b}_i ||$, und dadurch folgt aus $\lambda_1 = \inf ||\boldsymbol{B}\boldsymbol{x}||$, dass unsere kleinste Distanz unserer originalen Basisvektoren $\lambda_1 \geq \min_j ||\boldsymbol{b}_j^* ||$ sein muss.
>>
>> Die **Strategie** für den Beweis wird wie folgt sein. Wir zeigen zunächst, dass $|\langle \boldsymbol{Bx}, \boldsymbol{b}_i^*\rangle| \geq ||\boldsymbol{b}^*_i||^2$ gilt (1). Darüber wollen wir zeigen, dass auch $||\boldsymbol{Bx}||\cdot ||\boldsymbol{b}_i^*|| \geq ||\boldsymbol{b}_i^*||^2$ gilt (2). Da alle Basisvektoren linear unabhängig sind, muss $\boldsymbol{b}_i \neq 0$. Somit ist es uns dann erlaubt auf beiden Seiten $||\boldsymbol{b}_i^*||$ zu eleminieren und erhalten $||\boldsymbol{Bx}, \boldsymbol{b}_i^*||$.
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
>> \end{align}
>> 2. Da $x_i \neq 0$ können wir den Beweis abschließen mit
>> $$\begin{align}
>>|\langle \boldsymbol{Bx}, \boldsymbol{b}_i^* \rangle| = ||\boldsymbol{b}_i^*||^2 \cdot |x_i| \geq ||\boldsymbol{b}_i^*||^2 \tag*{$\square$}
>> \end{align}$$

>[!theorem] Satz Existenz des Gittevektors zur minimalen Distanz
> Sei $\lambda_1$ die minimale Distanz des Gitters $\mathcal{L}$, Dann existiert ein $\boldsymbol{x} \in \mathcal{L}$ sodass $||\boldsymbol{x}|| = \lambda_1$.








>[!def] Definition Module über Restklassen
> Seien $n,q \in \mathbb{N}$, dann nennen wir $$\mathbb{Z}_q{^n} = \{\boldsymbol{a} \text{ mod } q \; | \; \boldsymbol{a} \in \mathbb{Z}^n\}$$ den **Vektorraum über Restklassen**. Wobei wir definieren
> $$\boldsymbol{a} \text{ mod } q = \begin{pmatrix} a_1 \text{ mod } q \\ \vdots \\ a_n \text{ mod } q \end{pmatrix}$$

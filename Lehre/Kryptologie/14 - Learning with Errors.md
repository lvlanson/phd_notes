>[!remark] Bemerkung Vergleich Modul und Vektorraum
> Ein Modul ist die Verallgemeinerung eines Vektorraums. Ein Vektorraum setzt voraus, dass sowohl $(G, \oplus)$ also auch $( \setminus\{0\}, \odot)$ kommutative Gruppen sind, neben der Gültigkeit der Axiome für $\forall \boldsymbol{u}, \boldsymbol{v} \in G^n$ and $\lambda, \mu \in G$ 
>$$\begin{align} (\gamma \cdot \mu) \cdot \boldsymbol{u} &= \gamma \cdot (\mu \cdot \boldsymbol{u}) \\
\gamma \cdot (\boldsymbol{u} + \boldsymbol{v}) &= \gamma \cdot \boldsymbol{u} + \gamma \cdot \boldsymbol{v} \\
(\lambda + \mu) \cdot \boldsymbol{u} &= \lambda \cdot \boldsymbol{u} + \mu \cdot \boldsymbol{u} \end{align}$$
>
> In einem Modul jedoch ist die algebraische Struktur $(G\setminus\{0\}, \odot)$ keine kommutative Gruppe, sondern ein Ring. Für ein Ring gilt, dass dieser 
> 1. assoziativ ist
> 2. ein neutrales Element besitzt
> 3. ~~zu jedem Element ein inverses Element existiert~~
> 4. (kommutativ ist) (optional -> kommutativer Ring)

>[!def] Definition Minimale Distanz $\lambda_1$ eines Gitters $\mathcal{L}$
> Die minimale Distanz eines Gitters $\mathcal{L}$ wird bezeichnet als
> $$\lambda_1(\mathcal{L}) := \min_{\boldsymbol{v} \in \mathcal{L} \setminus\{\boldsymbol{0}\}} ||\boldsymbol{v}||_E$$
> wobei $||\boldsymbol{v}||_E$ ist die Norm von $\boldsymbol{v}$ und wir berechnen diese als
> $$||\boldsymbol{v}||_E = \sqrt{\sum_{i} v_i^2}$$



>[!def] Definition Module über Restklassen
> Seien $n,q \in \mathbb{N}$, dann nennen wir $$\mathbb{Z}_q{^n} = \{\boldsymbol{a} \text{ mod } q \; | \; \boldsymbol{a} \in \mathbb{Z}^n\}$$ den **Vektorraum über Restklassen**. Wobei wir definieren
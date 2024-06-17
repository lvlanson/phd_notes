>[!def] Definition Lattice $\mathcal{L}$ ([[../../../../../PDFs/peikert2015.pdf#page=8|Source]])
> An $n$-dimensional _lattice_ $\mathcal{L}$ is any subset of $\mathbb{R}^n$ that is both
> 1. an additive subgroup
> 	- the neutral element exists: $\mathbf{0} \in \mathcal{L}$
> 	- the inverse element exists: $\forall \mathbf{x} \in \mathcal{L}: \exists!-\mathbf{x}\in \mathcal{L}$
> 	- is closed under addition: $\forall \mathbf{x},\mathbf{y}\in\mathcal{L}:\mathbf{x}+\mathbf{y}\in\mathcal{L}$
> 2. discrete
> 	- $\forall \mathbf{x} \in \mathcal{L}$ there exists a neighborhood in $\mathbb{R}^n$ in which $\mathbf{x}$ is the only lattice point
> 
>>[!example]- Examples
>>1. $\mathbb{Z}^n$
>>2. Let $\mathcal{L}$ be a lattice, then $c\mathcal{L}$ is a lattice with $c \in \mathbb{R}$
>>3. $\{ \mathbf{x} \in \mathbb{Z}^n \; | \; x_{i} \in \mathbf{x}  \text{ is even} \}$
>

>[!def] Definition Minimum Distance of a Lattice ([[../../../../../PDFs/peikert2015.pdf#page=8|Source]]) 
>The minimum distance of a lattice $\mathcal{L}$ is given as the shortest nonzero lattice vector, i.e.
> $$\lambda_{1}(\mathcal{L}):= \min_{\mathbf{v}\in\mathcal{L}\setminus \{ \mathbf{0} \}} \lvert\lvert \mathbf{v} \rvert\rvert $$
> where $\lvert\lvert \cdot \rvert\rvert$ denotes the Euclidean norm (unless specified otherwise).

^5efb92

>[!def] Definition Successive Minimima $\lambda_{i}(\mathcal{L})$ ([[../../../../../PDFs/peikert2015.pdf#page=9|Source]])
>The $i$-th successive minimum is defined as the smallest radius $r$ such that the closed ball $\overline{B}(\mathbf{0}, r)$ contains $i$ linearly independent vectors.

>[!def]- Definitions Abstract Algebra
>>[!def] Definition Subgroup ([[../../../PDFs/judson2022.pdf#page=50|Source]])
>>Let $G$ be a group. A subgro[](../../../../PDFs/judson2022.pdf#page=50) group restricted under the operation of $G$.
>>>[!remark]- Recall Group
>>>A group is closed under ope[](../../../../../PDFs/judson2022.pdf#page=50)nt and an inverse element.
>
>
>>[!def] Definition Coset ([[../../../PDFs/judson2022.pdf#page=86|Source]])
>>Let $G$ be a group and $H$ be a subgroup of $G$. The **left coset of $H$** is defined with **representative** $g \in G$ as the set
>>$$gH:= \{ gh\;:\;h \in H \}$$ 
>>The **right coset of $H$** with **representative** $g \in G$ analogously
>>$$Hg:= \{ hg \;:\;h \in H \}$$
>
>>[!remark]
>>If the left and right cosets coincide or it is clear what kind of coset is we will speak about, we will call it simply **coset**.
>
>>[!theorem] Theorem Cosets Partitioning ([[../../../PDFs/judson2022.pdf#page=87|Source]])
>>Let $H$ be a subgroup of a group $G$. Th[](../../../../PDFs/judson2022.pdf#page=87)ion $G$. That is, the group $G$ is the disjoint union of the left cosets of $H$ in $G$.
>
>>[!theorem] Theorem Number of Left and R[](../../../../../PDFs/judson2022.pdf#page=87)#page=86|Source]])
>>Let $H$ be a subgroup of a group $G$. *The number of[](../../../../PDFs/judson2022.pdf#page=86)umber of right cosets of $H$ in $G$*.

>[!lemma] Lemma Quotient Group of Cosets
>A lattice [](../../../../../PDFs/judson2022.pdf#page=86)bb{R}^n/\mathcal{L}$ of cosets
>$$\mathbf{c}+\mathcal{L}=\{ \mathbf{c}+\mathbf{v} \;:\; \mathbf{v} \in \mathcal{L} \} \text{ with } \mathbf{c} \in \mathbb{R}^n$$
> with the induced operation
> $$(\mathbf{c}_{1}+\mathcal{L})+ (\mathbf{c}_{2}+\mathcal{L})= (\mathbf{c_{1}}+\mathbf{c_{2}}+\mathcal{L})$$

>[!def] Definition Fundamental Domain ([[../../../../../PDFs/judson2022.pdf#page=87|Source]])
> A **fundamental domain** if $\mathcal{L}$ is a set $\mathcal{F}\subset \mathbb{R}^n$ that contains exactly one representative $\overline{\mathbf{c}}\in(\mathbf{c}+\mathcal{L})\cap \mathcal{F}$ of every coset $\mathbf{c}+\mathcal{L}$
>>[!example]-
>>- $[0,1)$ for the integer lattice $\mathbb{Z}$
>>- $\left[ -\frac{1}{2}, \frac{1}{2} \right)$ for the integer lattice $\mathbb{Z}$

>[!def] Definition Lattice Basis ([[../../../../../PDFs/peikert2015.pdf#page=9|Source]])
>The basis of a lattice is a set of vectors $\{ \mathbf{b}_{1}, \mathbf{b}_{2},\dots , \mathbf{b}_{k} \}\subset \mathcal{L}$ such that
>$$\mathcal{L} = \mathcal{L}(\mathbf{B}) := \mathbf{B} \cdot \mathbb{Z}^k = \left\{  \sum_{i=1}^k z_{i}\mathbf{b}_{i} \; : \; z_{i} \in \mathbb{Z}  \right\}$$
>The integer $k$ is called the _rank_ of the basis, and is invariant of the lattice.
>>[!pic] Illustration ([[../../../../../PDFs/sabani2024.pdf#page=4|Source]])
>>![[../Figures/lattice_bases.png|center|280]]

>[!def] Definition Unimodular Matrix ([[../../../../../PDFs/peikert2015.pdf#page=9|Source 1]], [[../../../../../PDFs/judson2022.pdf#page=163|Source 2]])
>A matrix $\mathbf{U} \in \mathbb{Z}^{n \times n}$ is called unimodular if
>$$\det(U) = \pm 1$$
>
>>[!example]-
>>$$\begin{align}
>> \mathbf{U} &= \begin{pmatrix}
>> 3 & 1 \\ 5 & 2
>>\end{pmatrix} \\
>> \det(\mathbf{U}) &= 1
>>\end{align}$$

>[!remark]
>For this analysis, we consider full rank bases $k = n$.

>[!lemma] Lemma ([[../../../../../PDFs/peikert2015.pdf#page=9|Source]])
> Let $\mathbf{B}$ be a basis of lattice $\mathcal{L} = \mathcal{L}(\mathbf{B})$ and $\mathbf{U}$ an unimodular matrix. The matrix
> $$\mathbf{B} \cdot \mathbf{U}$$
> is also a basis for $\mathcal{L}$.
>>[!proof]-
>> First, we prove linear independence. By the [[../../../PDFs/hornrogara.pdf#page=32|Sylvester Inequality (0.4.5 (c))]] we have 
>> If $\mathbf{A} \in \mathbb{R}^{m \times k}$ [](../../../../PDFs/hornrogara.pdf#page=32)bf{A}) +  \text{rank}(\mathbf{B}) - k \leq \text{rank} (\mathbf{AB}) \leq \min(\text{rank} (\mathbf{A}), \text{rank} (\mathbf{B}))$$
>> Since $B$ and $U$ are full rank and both qua[](../../../../../PDFs/hornrogara.pdf#page=32)(\mathbf{B}\cdot \mathbf{U})=n$$
>> Hence, $\mathbf{B}\cdot \mathbf{U}$ is full rank, therefore the column vectors are linearly independent and form a basis.
>>
>>We continue to show that any vector in $\mathcal{L}(\mathbf{B})$ must be a linear combination of $\mathbf{B}\cdot \mathbf{U}$. Since $\mathbf{B}$ is a basis for $\mathcal{L}$, we know that
>>$$\mathbf{v} = \sum_{i=1}^n \alpha_{i}\mathbf{b}_{i}$$
>>for some $\alpha_{i} \in \mathbb{Z}$ and $\mathbf{b}_{i}$ being the columns of $\mathbf{B}$. Denote the vector
>>$$\mathbf{b}_{i}' = \mathbf{B}\cdot \mathbf{u}_{i}$$
>>for $\mathbf{u}_{i} \in \mathbf{U}$. Since $\mathbf{B} \cdot \mathbf{U}$ is full rank, we know all $\mathbf{b}_{i}'$ form a basis. Now denote the following linear combination
>>$$\mathbf{w} = \sum_{i=1}^n \beta_{i}\mathbf{b}_{i}'$$
>>with $\beta_{i} \in \mathbb{Z}$. We make the following observation
>>$$\begin{align}
>> \mathbf{w} &= \sum_{i=1}^n \beta_{i}\mathbf{b}_{i}' \\
>>  &= \sum_{i=1}^n \beta_{i}(\mathbf{B}\cdot \mathbf{u}_{i}) \\
>> &=\mathbf{B} \left( \sum_{i=1}^n \beta_{i} \mathbf{u}_{i}  \right)
>>\end{align}$$
>>denote $\mathbf{w}' = \left( \sum_{i=1}^n \beta_{i} \mathbf{u}_{i}  \right)$, we get
>>$$\mathbf{w} = \mathbf{B}\mathbf{w}'$$
>>Since $\mathbf{B}$ is a basis for $\mathcal{L}$, we know $\mathbf{w} \in \mathcal{L}$. Note, $\beta_{i}$ are arbitrary integers, hence the product of $\mathbf{B} \cdot \mathbf{U}$ spans the same lattice $\mathcal{L}$ as $\mathbf{B}$ does.

>[!def] Definition Fundamental Parallelepiped ([[../../../../../PDFs/peikert2015.pdf#page=9|Source]])
>Let $\mathbf{B}$ be a basis for $\mathcal{L}$ and a fundamental domain $\mathcal{F}$  of $\mathcal{L}$. Then the **fundamental parallelepiped** can be given as
>$$\mathcal{P}(\mathbf{B}):= \mathbf{B} \cdot F$$
>>[!example]-
>>A commonly used origin-centered fundamental parallelepiped can be given as
>>$$\mathcal{P}(\mathbf{B})=\mathbf{B}\cdot \left[ -\frac{1}{2}, \frac{1}{2} \right)^n$$ 
>
>>[!pic]- Illustration
>>![[Figures/parallelepiped.png|center|400]]
>><center>Figure: Some Arbitrary Parallelepiped</center>

>[!def] Definition Determinant of Lattice $\mathcal{L}$ ([[../../../../../PDFs/sabani2024.pdf#page=5|Source]])
>Let $\mathcal{L}=\mathcal{L}(\mathbf{B})$ be a lattice of rank $n$ and $\mathbf{B}$ a basis of $\mathcal{L}$. The determinant of $\mathcal{L}$ denoted by $\det (\mathcal{L})$ is the $n$-dimensional volume of $\mathcal{P}(\mathbf{B})$, i.e.
>$$\begin{align}
> \det(\mathcal{L}(\mathbf{B}))&=\text{vol}(\mathcal{P}) \\
> \det(\mathcal{L})&=\sqrt{ \det(\mathbf{B}^T\mathbf{B}) }
>\end{align}$$

>[!def] Definition Inner Product with Lattices ([[../../../../../PDFs/sabani2024.pdf#page=5|Source]])
>Let $V$ be an arbitrary vector space over a lattice $\mathcal{L}$. An inner product on $V$ is a function $\left\langle \,,\, \right\rangle: V \times V \to \mathcal{L}$ which satisfies
>1. $\left\langle x\,,\,x \right\rangle\geq 0\;\; \forall x \in V$ and $\left\langle x\,,\,x \right\rangle = 0$ iff $x=0$
>2. $\left\langle x+y\,,\,z \right\rangle=\left\langle x\,,\,z \right\rangle \lor \left\langle y\,,\,z \right\rangle \forall x,y,z \in V$
>3. $\left\langle ax\,,\,y \right\rangle = a\left\langle x\,,\,y \right\rangle \forall x,y \in V$ and $a \in \mathcal{L}$
>4. $\left\langle x\,,\,y \right\rangle = \left\langle y\,,\,x \right\rangle, \;\; \forall x,y \in V$

>[!def] The Dual Lattice $L^*$ ([[../../../../../PDFs/peikert2015.pdf#page=9|Source]])
>The **dual lattice** (also known as reciprocal lattice) of some lattice $\mathcal{L} \subset \mathbb{R}^n$ is defined as
>$$\mathcal{L}^* := \{ \mathbf{w}: \left\langle \mathbf{w}\,,\,\mathcal{L} \right\rangle \subseteq \mathbb{Z}  \}$$
>
>>[!remark]
>>The dual lattice $\mathcal{L}^*$ is the set of points whose inner product with the lattice $\mathcal{L}$ are exclusively integers.


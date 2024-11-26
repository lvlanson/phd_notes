### 0.1 Field of Fractions

>[!remark] Motivation Field of Fractions
>**<span style="color:#e9ffad">Field of Fractions</span>** over an [[../Judson/1 - Algebraic Structures#^f48d09|integral domain]] are a generalization of the rational numbers field $\mathbb{Q}$ over the integral domain $\mathbb{Z}$. Note, that for any $a,b \in \mathbb{Z}$ with $b \neq 0$ we can define a rational number $\frac{a}{b} \in \mathbb{Q}$. Therefore, there exists an equivalence relation $\sim$ on $\mathbb{Q}$ such that for $(a,b), (c,d) \in \mathbb{Z} \times \mathbb{Z}$ we have 
>$$\begin{align}
> (a,b) \sim (c,d): &\iff  ad = bc \\
> &\iff \frac{a}{b} = \frac{c}{d}
>\end{align}$$
>This observation can be generalized for any **<span style="color:#e9ffad">field of fractions $K_{D}$ over an integral domain $D$</span>**.

>[!lemma] Proposition Cancellation Law in Integral Domains
>Let $D$ be an integral domain and $a,b,c \in D$. Given $a \neq 0$ we can assert
>$$ab=ac \implies b=c$$
>>[!proof]-
>>$$\begin{align}
>> ab &= ac \\
>> ab - ac &= 0 \\
>> a(b-c) &= 0
>>\end{align}$$
>>Observe, since $D$ is an integral domain, either $a=0$ or $(b-c)=0$. Since we stated that $a \neq 0$, therefore $$b-c = 0 \implies b = c$$ 
>>Therefore, $a$ can be cancelled in an integral domain. $$\tag*{$\square$}$$

^4a1cd9

>[!lemma] Proposition Equivalence Relation on Fractions in an Integral Domain
>Let $D$ be an [[../Judson/1 - Algebraic Structures#^f48d09|integral domain]] and $(a,b), (c,d) \in D \times D$. We define the relation $$\begin{align}
> (a,b) \sim (c,d):&\iff ad = bc \\
> &\iff \frac{a}{b} = \frac{c}{d}
>\end{align}$$
>This relation is an **<span style="color:#3884ff">equivalence relation</span>**.
>>[!proof]-
>>1. <u>Reflexivity</u>: 
>>Let $(a,b) \in D\times D$ 
>>$$\begin{align}
>> (a,b) \sim (a,b): \iff &ab = ab \tag*{$\checkmark$}
>>\end{align}$$
>>2. <u>Symmetry</u>:
>>Let $(a,b), (c,d) \in D \times D$
>>$$\begin{align}
>> (a,b) \sim (c,d): \iff \frac{a}{b} &= \frac{c}{d} \\
>> \frac{c}{d} &= \frac{a}{b} \implies (c,d) \sim (a,b) \tag*{$\checkmark$}
>>\end{align}$$
>>3. <u>Transitivity</u>:
>>Let $(a,b), (c,d), (e,f) \in D\times D$
>>$$\begin{align}
>> \underbrace{ (a,b) \sim (c,d) }_{ (i) } \land \underbrace{ (c,d) \sim (e,f) }_{ (ii) }
>>\end{align}$$
>>We have
>>$$\begin{alignat}{3}
>> (a,b) \sim (c,d): &\iff ad &&= bc \qquad&&\Big\vert \cdot f\tag{i} \\
>> &\phantom{\iff} adf&&= {\color{#58A4ff}cfb}\\
>> (c,d) \sim (e,f): &\iff cf &&= de \qquad&&\Big\vert \cdot b\tag{ii} \\
>> &\phantom{\iff}{\color{#58A4ff}cfb} &&= deb
>>\end{alignat}$$
>>By aligning our results from $(i)$ and $(ii)$ we get
>>$$\begin{align}
>> adf &= deb \\
>> afd &= ebd \\
>> af &= eb  \\
>> af &= be \implies (a,b) \sim (e,f)  
>>\end{align}$$
>>Where we used the [[#^4a1cd9|cancellation property of integral domains]]. Therefore, we have
>>$$(a,b) \sim (c,d) \land (c,d) \sim (e,f) \implies (a,b) \sim (e,f) \tag*{$\square$}$$

>[!lemma] Proposition Addition on Fractions in an Integral Domain
>Let $D$ be an integral domain and define the **<span style="color:#3884ff">addition on fractions of in integral domain</span>** with $(a,b),(c,d) \in D \times D$
>$$\begin{alignat}{3}
>+&: (D\times D) &&\times (D\times D) &&\to D\times D \\
>+&: (a,b) &&\times (c,d) &&\mapsto (ad+bc, bd)
>\end{alignat}$$
>>[!remark] Remark on Behavior in $\mathbb{Q}$
>>The rational numbers behave accordingly
>>$$\begin{align}
>> \frac{a}{b} + \frac{c}{d} = \frac{ad+bc}{bd}
>>\end{align}$$
>
>>[!proof]
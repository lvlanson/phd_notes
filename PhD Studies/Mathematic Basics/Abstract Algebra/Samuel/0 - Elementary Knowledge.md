>[!remark] Motivation
>We define algebraic structures to handle inverse elements and refine division on integral domains.  
>
>- **Fields of Fractions:**  
>Fields of fractions extend an integral domain $D$ to include inverses of nonzero elements, which are otherwise undefined in $D$. For example, in the integral domain $\mathbb{Z}$, the inverse of $3$ does not exist. The field of fractions $\mathbb{Q}$ includes $\frac{1}{3}$, addressing this limitation. Fields of fractions thus enable a richer arithmetic system where division is always possible (except by zero).  
><br>
>- **Euclidean Domains:**  
>Euclidean domains introduce a norm function $\phi: D \to \mathbb{N}$, enabling a division algorithm with a remainder. This allows for residue classes and computations such as greatest common divisors (GCDs) and modular arithmetic. For instance, in $\mathbb{Z}$, the norm $\phi(a) = |a|$ ensures that $a = bq + r$, where $r = 0$ or $|r| < |b|$.  


### 0.1 Field of Fractions

>[!remark] Motivation Field of Fractions
>**<span style="color:#e9ffad">Field of Fractions</span>** over an [[../Judson and Dummit/1 - Algebraic Structures#^f48d09|integral domain]] are a generalization of the rational numbers field $\mathbb{Q}$ over the integral domain $\mathbb{Z}$. Note, that for any $a,b \in \mathbb{Z}$ with $b \neq 0$ we can define a rational number $\frac{a}{b} \in \mathbb{Q}$. Therefore, there exists an equivalence relation $\sim$ on $\mathbb{Q}$ such that for $(a,b), (c,d) \in \mathbb{Z} \times \mathbb{Z}$ we have 
>$$\begin{align}
> (a,b) \sim (c,d): &\iff  ad = bc \\
> &\iff \frac{a}{b} = \frac{c}{d}
>\end{align}$$
>This observation can be generalized for any **<span style="color:#e9ffad">field of fractions $K_{D}$ over an integral domain $D$</span>**.

>[!lemma] Proposition Equivalence Relation on Fractions in an Integral Domain
>Let $D$ be an [[../Judson and Dummit/1 - Algebraic Structures#^f48d09|integral domain]] and $(a,b), (c,d) \in D \times D$. We define the relation $$\begin{align}
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
>>Where we used the [[../Judson and Dummit/3 - Rings#^4a1cd9|cancellation law of integral domains]]. Therefore, we have
>>$$(a,b) \sim (c,d) \land (c,d) \sim (e,f) \implies (a,b) \sim (e,f) \tag*{$\square$}$$

>[!lemma] Proposition Addition on Fractions in an Integral Domain ([Source](https://math.libretexts.org/Bookshelves/Abstract_and_Geometric_Algebra/Abstract_Algebra%3A_Theory_and_Applications_(Judson)/18%3A_Integral_Domains/18.01%3A_Fields_of_Fractions))
>Let $D$ be an integral domain and define the **<span style="color:#3884ff">addition on fractions of in integral domain</span>** with $(a,b),(c,d) \in D \times D$
>$$\begin{alignat}{3}
>+&: (D\times D) &&\times (D\times D) &&\to D\times D \\
>+&: (a,b) &&\times (c,d) &&\mapsto (ad+bc, bd)
>\end{alignat}$$
>Then the **<span style="color:#3884ff">addition on fractions of integral domains</span>** is well defined.
>>[!remark] Remark on Behavior in $\mathbb{Q}$
>>The rational numbers behave accordingly
>>$$\begin{align}
>> \frac{a}{b} + \frac{c}{d} = \frac{ad+bc}{bd}
>>\end{align}$$
>
>>[!proof]-
>>Let $D$ be an integral domain. Suppose we have
>>$$\begin{align}
>> (a_{1},b_{1}) &= (a_{2}, b_{2}) \tag{$a_{1} b_{2}=a_{2}b_{1}$} \\
>> (c_{1},d_{1}) &= (c_{2}, d_{2}) \tag{$c_{1} d_{2}=c_{2}d_{1}$} 
>>\end{align}$$
>>for $a_{1,2},b_{1,2},c_{1,2},d_{1,2} \in D$. We need to show that
>>$$\begin{align}
>> (a_{1},b_{1}) + (c_{1},d_{1}) &= (a_{2},b_{2}) + (c_{2},d_{2}) \\
>> (a_{1}d_{1}+b_{1}c_{1},b_{1}d_{1}) &= (a_{2}d_{2}+b_{2}c_{2},b_{2}d_{2}) 
>>\end{align}$$
>>By multiplying the denominators of the one side with the numerator with the other side, we expect to yield the same expression if the addition is closed, since we know that the equivalence relation $(a,b) \sim (c,d) \iff ad = bc$ is defined on $D\times D$.
>>$$\begin{align}
>>(a_{1}d_{1}+b_{1}c_{1})b_{2}d_{2} &=(a_{2}d_{2}+b_{2}c_{2}) b_{1}d_{1} \\
>> \underbrace{ a_{1}b_{2} }_{ =\color{#58A4ff}a_{2}b_{1} }d_{1}d_{2} + b_{1}b_{2}\underbrace{ c_{1}d_{2} }_{ =\color{#58A4ff}c_{2}d_{1} } &= {\color{#58A4ff}a_{2}b_{1}}d_{1}d_{2} + b_{1}b_{2}{\color{#58A4ff}c_{2}d_{1}} \\
>> b_{1}d_{1}a_{2}d_{2} + b_{1}d_{1}b_{2}c_{2} &= b_{1}d_{1}a_{2}d_{2} + b_{1}d_{1}b_{2}c_{2} \tag*{$\square$}
>>\end{align}$$

>[!lemma] Proposition Multiplication on Fractions in an Integral Domain ([Source](https://math.libretexts.org/Bookshelves/Abstract_and_Geometric_Algebra/Abstract_Algebra%3A_Theory_and_Applications_(Judson)/18%3A_Integral_Domains/18.01%3A_Fields_of_Fractions))
>Let $D$ be an integral domain and define the **<span style="color:#3884ff">multiplication on fractions of in integral domain</span>** with $(a,b),(c,d) \in D \times D$
>$$\begin{alignat}{3}
>\cdot&: (D\times D) &&\times (D\times D) &&\to D\times D \\
>\cdot&: (a,b) &&\times (c,d) &&\mapsto (ac, bd)
>\end{alignat}$$
>Then the **<span style="color:#3884ff">multiplication on fractions of integral domains</span>** is well defined.
>
>>[!remark] Remark on Behavior in $\mathbb{Q}$
>>The rational numbers behave accordingly
>>$$\begin{align}
>> \frac{a}{b} \cdot \frac{c}{d} = \frac{ac}{bd}
>>\end{align}$$
>
>>[!proof]-
>>Let $D$ be an integral domain. Suppose we have
>>$$\begin{align}
>> (a_{1},b_{1}) &= (a_{2}, b_{2}) \tag{$a_{1} b_{2}=a_{2}b_{1}$} \\
>> (c_{1},d_{1}) &= (c_{2}, d_{2}) \tag{$c_{1} d_{2}=c_{2}d_{1}$} 
>>\end{align}$$
>>for $a_{1,2},b_{1,2},c_{1,2},d_{1,2} \in D$. We need to show that
>>$$\begin{align}
>> (a_{1},b_{1}) \cdot (c_{1},d_{1}) &= (a_{2},b_{2}) \cdot (c_{2},d_{2}) \\
>> (a_{1}c_{1},b_{1}d_{1}) &= (a_{2}c_{2},b_{2}d_{2}) 
>>\end{align}$$
>>Using again the equivalence relation $(a,b) \sim (c,d) \iff ad = bc$, hence
>>$$\begin{align}
>>a_{1}c_{1}b_{2}d_{2} &= a_{2}c_{2}b_{1}d_{1} \\
>>\underbrace{ {\color{#58A4ff}a_{1}b_{2}} }_{ =a_{2}b_{1} }\underbrace{ {\color{#38ffa9}c_{1}d_{2}} }_{ =c_{2}d_{1} } &= a_{2}b_{1}c_{2}d_{1} \\
>>a_{2}b_{1}c_{2}d_{1} &= a_{2}b_{1}c_{2}d_{1} \tag*{$\square$}
>>\end{align}$$

>[!theorem] Theorem Fractions on Integral Domains are Fields ([Source](https://math.libretexts.org/Bookshelves/Abstract_and_Geometric_Algebra/Abstract_Algebra%3A_Theory_and_Applications_(Judson)/18%3A_Integral_Domains/18.01%3A_Fields_of_Fractions))
>Let $D$ be an integral domain and $F_{D} = D \times D$ with the operations 
>$$\begin{align}
> (a,b) + (c,d) &= (ad+bc,bd) \tag{Addition} \\
> (a,b) \cdot (c,d) &= (ac,bd) \tag{Multiplication}
>\end{align}$$
>Then $F_{D}$ forms a field.
>
>>[!proof]-
>>1. <u>Additive Commutative Group</u>
>> Associativity: $\forall a,b,c,d,e,f \in D$
>> $$\begin{align}
>> (a,b)+\Big((c,d)+(e,f)\Big)&= (a,b) +(cf+ed, df) \\
>> &= (adf + bcf+bed,bdf) \\
>> &= (ad+bc,bd)+(e,f) \\
>> &= \Big((a,b)+(c,d)\Big) + (e,f \tag*{$\checkmark$})
>>\end{align}$$
>>Neutral Element: $e = (0,1)$
>>$$\begin{align}
>> (a,b)+(0,1)= (0,1)+(a,b)&= (0b+1a,1b) \\
>> &=(a,b) \tag*{$\checkmark$}
>>\end{align}$$
>>Inverse Element: $-(a,b) =(-a,b)$
>>$$\begin{align}
>> (-a,b)+(a,b)&= (ab-ab,b^2) \\
>> &= (0,b^2) \\
>> &= (0,1) \tag*{$\checkmark$}
>>\end{align}$$
>>Due to equivalency $(0,b^2) \sim (0,1)$
>>$\,$
>>Commutativity:
>>$$\begin{align}
>> (a,b)+(c,d)&= (ad+bc,bd) \\
>> &= (c,d)+(a,b) \tag*{$\checkmark$}
>>\end{align}$$
>>
>>2. <u>Multiplicative Commutative Group</u>
>>Associativity: $\forall a,b,c,d,e,f \in D$
>>$$\begin{align}
>> (a,b)\cdot\Big((c,d)\cdot(e,f)\Big) &= (a,b)\cdot(ce,df) \\
>> &=(ace,bdf) \\
>> &=(ac,bd)\cdot(e,f) \\
>> &= \Big((a,b)\cdot(c,d)\Big) \cdot(e,f) \tag*{$\checkmark$}
>>\end{align}$$
>>Neutral Element: $e=(1,1)$
>>$$\begin{align}
>> (a,b) \cdot(1,1) = (1,1) \cdot(a,b) &= (a,b) \tag*{$\checkmark$}
>>\end{align}$$
>>Inverse Element: $(a,b)^{-1} =(b,a)$
>>$$\begin{align}
>> (a,b)\cdot(b,a) &= (ab,ab) \\
>> &=(1,1) \tag*{$\checkmark$}
>>\end{align}$$
>>Due to the equivalency $(ab,ab) \sim(1,1)$
>>$\,$
>>Commutativity:
>>$$(a,b)\cdot(c,d) = (ac,bd) = (ca,db) = (c,d)\cdot(a,b) \tag*{$\checkmark$}$$
>>
>>3. <u>Distributivity</u>
>>$\forall a,b,c,d,e,f  \in D$
>>$$\begin{align}
>> (a,b)\cdot\Big((c,d)+(e,f)\Big) &= (a,b) \cdot (cf+ed,df) \\
>> &= (acf+aed,bdf) \\ 
>> &= (abcf+abed, b^2df) \\
>> &= (ac,bd)+(ae,bf) \\
>> &= (a,b)\cdot(c,d)+(a,b)\cdot(e,f)
>>\end{align}$$
>>Note that
>>$$(acf+aed,bdf) = (abcf+abed,b^2df)$$
>>because
>>$$\begin{align}
>> bdf(abcf+abde) &= (acf+ade)b^2df \\
>> ab^2cdf^2 + ab^2d^2ef &= ab^2cf^2+ab^2d^2ef \tag*{$\checkmark$}
>>\end{align}$$
>>
>>This establishes the theorem. $$\tag*{$\square$}$$

^771c8d

### 0.2 Euclidean Domains

>[!def] Definition Norm on a Ring
>A **<span style="color:#38ffa9">norm on a ring $R$</span>** is a function
>$$\phi: R \to \mathbb{N}$$
>with $\phi(0) = 0$. A **<span style="color:#38ffa9">positive norm</span>** has $\phi(r)>0$ for all $r \in R$

>[!def] Definition Euclidean Domain
>A **<span style="color:#38ffa9">Euclidean domain</span>** is an integral domain $D$ with a norm $\phi$ such that for any $a,b \in D$, there exists $q,r \in D$ such that
>$$a = q\cdot b+r$$
>with $\phi(r)< \phi(b)$. The element $q$ is called the **<span style="color:#38ffa9">quotient</span>** and $r$ is the **<span style="color:#38ffa9">remainder</span>**. 
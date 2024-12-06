>[!lemma] Proposition ([[../../../../PDFs/judson2022.pdf#page=204|Source]])
>Let $R$ be a ring with $a,b \in R$, then
>1. $a0=0a=0$
>2. $a(-b)=(-a)b=-ab$
>3. $(-a)(-b)=ab$
>
>>[!proof]-
>>1. $\,$ $$a0=a(0+0)=a0 + \underbrace{ a0 }_{ =0 }$$
>>Hence $a0=0$. The term $0a$ works accordingly.
>>
>>2. We want to show that $a(-b)+ab = 0$  $$ab + a(-b)=a(b-b)=a 0=0$$
>>3. Follows from (2)
>>$$(-a)(-b)=-(a(-b))=-(-ab)= ab \tag*{$\square$}$$

>[!def] Definition Subring ([[../../../../PDFs/judson2022.pdf#page=205|Source 1]], [[../../../../PDFs/dummit2003.pdf#page=242|Source 2]])
>Let $R$ be a ring. Then $S$ is a **<span style="color:#38ffa9">subring</span>** if
>1. $S \subset R$
>2. $S$ is a [[1 - Algebraic Structures#^2c4055|ring]] under the inherited operations from $R$
>
>>[!example]
>>1. $\mathbb{Z}$ is a subring of $\mathbb{Q}$
>>2. $\mathbb{Q}$ is a subring of $\mathbb{R}$
>>3. $2\mathbb{Z}$ is a subring of $\mathbb{Z}$

>[!lemma] Proposition
> Let $R$ be a ring and $S$ a subset of $R$. Then $S$ is a **<span style="color:#3884ff">subring</span>** of $R$ if and only if the following conditions are satisfied:
> 1. $S \neq \emptyset$
> 2. $rs \in S$ for all $r,s \in S$
> 3. $r-s \in S$ for all $r,s \in S$


## Integral Domains

>[!def] Definition Zero Divisor ([[../../../../PDFs/judson2022.pdf#page=205|Source]])
>Let $R$ be a [[1 - Algebraic Structures#^4a5286|commutative ring]] and $r \in R$ with $r \neq 0$. The element $r$ is called **<span style="color:#38ffa9">zero divisor</span>** if there is some $s \in R$ with $s \neq 0$, such that
>$$rs =0$$

>[!remark] Recall
> A ring is an [[1 - Algebraic Structures#^f48d09|integral domain]] if it has no **<span style="color:#e9ffad">zero divisors</span>**.

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

>[!lemma] Corollary ([[../../../../PDFs/dummit2003.pdf|Source]])
>Any finite integral Domain is a field.
>>[!proof]-
>> Let $D$ be a finite integral domain and let $a \neq 0$ in $D$. We define the map
>> $$\phi_{a}: x \mapsto ax$$
>> for $x \in D$. We can observe by cancellation law for $x_{1},x_{2} \in D$
>> $$\begin{align}
>> x_{1}a = x_{2}a \implies x_{1} = x_{2}
>>\end{align}$$
>>therefore $\phi_{a}$ is *injective*. By the simple fact that $D$ is finite it is also *surjective*. Therefore, there must exist some $b \in D$ such that
>>$$ab = 1$$
>>Since $a$ was arbitrary, $D$ must hold all units and therefore is a field.

## Ring Homomorphisms and Ideals

>[!def] Definition Ring Homomorphism ([[../../../../PDFs/judson2022.pdf#page=207|Source 1]], [[../../../../PDFs/dummit2003.pdf#page=253|Source 2]])
> Let $R,S$ be [[#^2c4055|rings]], then a **~={green}ring homomorphism=~** is a map $\phi:R\to S$ satisfying
> $$\begin{align}
> \phi(a+b) &= \phi(a)+\phi(b) \\
> \phi(ab)&= \phi(a)\phi(b)
>\end{align}$$
>for all $a,b \in R$. If $\phi$ is a bijection, then $\phi$ is called an **isomorphism of rings**

^c3d051

>[!def] Definition Kernel of a Ring ([[../../../../PDFs/judson2022.pdf#page=207|Source 1]], [[../../../../PDFs/dummit2003.pdf#page=253|Source 2]])
> Let $R,S$ be [[1 - Algebraic Structures#^2c4055|rings]] and $\phi:R\to S$ a [[3 - Rings#^c3d051|ring homomorphism]]. We define the **~={green}kernel of a ring homomorphism=~** to be the set
> $$\text{ker }\phi=\{ r \in R \mid \phi(r)=0 \}$$

>[!def] Definition Isomorphism ([[../../../../PDFs/dummit2003.pdf#page=253|Source]])
>A bijective ring homomorphism is called an **<span style="color:#38ffa9">isomorphism</span>**. Let $R,S$ be to *isomorphic* rings, then we denote them being isomorphic with
>$$R \simeq S$$

>[!example] Examples
>1. $\phi: \mathbb{Z} \to \mathbb{Z}_{2}$ is a [[#^c3d051|ring homomorphism]] with $\text{ker } \phi =2\mathbb{Z}$
>
>>[!example]- Because...
>>Holds under addition
>>$$\begin{align}
>> \phi(a+b) &\equiv (a+b) \text{ mod } 2  &\;\;(\text{mod } 2)\\
>>   &\equiv(a \text{ mod } 2) + (b \text{ mod } 2) &\;\;(\text{mod } 2)\\
>>   &\equiv \phi(a) + \phi(b)&\;\;(\text{mod } 2)
>>\end{align}$$
>>Holds under multiplication
>>$$\begin{align}
>> \phi (a \cdot b) &\equiv (a \cdot b) \text{ mod } 2  &\;\;(\text{mod } 2)\\
>> &\equiv (a \text{ mod } 2)  \cdot (b \text{ mod } 2) &\;\;(\text{mod } 2) \\
>> &\equiv \phi(a) \cdot \phi(b) &\;\;(\text{mod } 2)
>>\end{align}$$
>>The kernel is justified because for any $a \in 2\mathbb{Z}$ we have
>>$$a \equiv 0 \;\;(\text{mod } 2)$$
>>thus $a \in \text{ker } \phi$.
>
>2. $\phi_{n}: \mathbb{Z} \to \mathbb{Z}$ with $\phi_{n}: k \mapsto nk$ is not a [[#^c3d051|ring homomorphism]]
>
>>[!example]- Because...
>>For $a,b \in \mathbb{Z}$
>>$$\begin{align}
>> \phi(a \cdot b) &= nab \\
>> \phi (a) \cdot \phi (b) &= n^2ab
>>\end{align}$$
>
>3. $\phi: \mathbb{Q}[x]\to \mathbb{Q}$ with $\phi: p(x) \mapsto p(0)$ is a [[#^c3d051|ring homomorphism]]
>
>>[!example]- Because...
>>Holds under addition, for $p,q \in \mathbb{Q}[x]$
>>$$\begin{align}
>> \phi(p + q) &= (p + q)(0) \\
>> &= p(0) + q(0) \\
>> &= \phi(p) + \phi(q)
>>\end{align}$$
>>Note, we can treat $(p+q)$ because we are only evaluating the constant terms
>>
>>Holds under multiplication
>>$$\begin{align}
>>\phi(p \cdot q) &= (p \cdot q)(0) \\
>> &= p(0) \cdot q(0) \\
>> &= \phi(p) \cdot \phi(q)
>>\end{align}$$

>[!lemma] Proposition Ring Properties of Ring Homomorphisms ([[../../../../PDFs/dummit2003.pdf#page=254|Source]])
>Let $\phi:R\to S$ be a [[#^c3d051|ring homomorphism]].
>1. The image of $\phi$ is a subring of $S$.
>2. The kernel of $\phi$ is a subring of $R$. Furthermore, if $\alpha \in \text{ker }\phi$ then $r\alpha$ and $\alpha r$ are elements of $\text{ker }\phi$ for every $r \in R$
>
>>[!proof]-
>>1. Let $\text{im }\phi$ denote the image of $\phi$ and
>>$$\begin{align}
>>s_{1} &= \phi(r_{1}) \in \text{im }\phi &&r_{1} \in R \\
>>s_{2} &= \phi(r_{2}) \in \text{im }\phi &&r_{2} \in R
>>\end{align}$$
>>Then we only need to check first that is closed under subtraction (which ensures additive group structure) and multiplication. 
>>$$\phi(r_{1}-r_{2})=s_{1}-s_{2} \in \text{im }\phi$$
>>Since the ring is closed under subtraction we see that the image of the map must also be closed under subtraction. The same argument can be applied for the multiplication, i.e.
>>$$\phi(r_{1}\cdot r_{2})= s_{1}\cdot s_{2} \in \text{im }\phi$$
>>
>>2. Let $\alpha, \beta \in \text{ker }\phi \subseteq R$, then clearly
>>$$\phi(\alpha)=\phi(\beta)=0$$
>>Since $\phi$ is [[#^c3d051|ring homomorphism]] we have
>>$$\begin{alignat}{2}
>>\phi(a-b)&=\phi(a)-\phi(b)&&=0 \\
>>\phi(a \cdot b)&= \phi(a) \cdot \phi(b)&&=0
>>\end{alignat}$$
>>Therefore $\text{ker }\phi$ retains the ring structure inherited by $R$. Further, note for $r \in R$
>>$$\begin{alignat}{2}
>> \phi(r \alpha) &=\phi(r)\phi(\alpha)&&= \phi(r)\cdot0 = 0 \\
>> \phi(\alpha r) &=\phi(\alpha)\phi(r) &&= 0\cdot\phi(r)=0
>>\end{alignat}$$
>>we see multiplication is closed under the elements of $R$ in the kernel of $\phi$, thus $r\alpha, \alpha r \in \text{ker }\phi$. $$\tag*{$\square$}$$
>
>>[!remark] 
>>Point 2. shows that the kernel of a ring homomorphism is an [[4 - Ideals and Ideals on Polynomials#^2baf0e|ideal]] of $R$

^0d99e8

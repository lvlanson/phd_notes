## Basic Algebraic Structures (from Groups to Fields)

>[!def] Definition Basic Algebraic Structures (Group/Abelian Group) ([[../../../../PDFs/judson2022.pdf#page=50|Source]])
>Suppose $\circ$ is an arbitrary binary operation on the set $G \neq \emptyset$. We say that $(G, \circ)$ a **<u>group</u>**, if $G$ holds the following conditions under the operation $\circ$
>1. $G$ is **associative**: $\forall a,b,c \in G$:
> $$(a \circ b)\circ c = a\circ (b \circ c)$$
> 2. $G$ has exactly one **neutral/identity element**: $\exists! e \in G$, s.t. $\forall a \in G:$
>  $$a \circ e = e \circ a = a$$
>  3. $G$ has exactly one **inverse element** with respect to some element: $\forall a \in G: \exists! a^{-1} \in G$, s.t.
>   $$a \circ a^{-1} = a^{-1} \circ a = e$$
> ---
>If additionally the following holds
> 
>4. $G$ is **commutative**: $\forall a, b \in G$:
> $$a \circ b = b \circ a$$
> 
> we denote $(G, \circ)$ a  **<u>commutative/Abelian group</u>**
>

^0b2e62

>[!def] Definition Ring ([[../../../../PDFs/judson2022.pdf#page=194|Source]])
>Let $G$ is a non-empty set closed under the binary operations $(G,+)$ and $(G\setminus \{ 0 \}, \;\cdot\;)$ with $0$ being the neutral element in $(G,+)$. We say that $(G,+, \cdot)$ a **ring** if 
>1. $(G,+)$ is an [[#^0b2e62|Abelian group]]
>2. $(G,\;\cdot\;)$ holds the [[#^0b2e62|association property]]: $\forall a,b,c \in G$:$$a(bc)=(ab)c$$
>3. $(G,+,\;\cdot\;)$ holds the **Distribution Property**: $\forall a,b,c\in G$:$$a \cdot (b+c)=ab+ac$$

^2c4055

>[!def] Definition Ring with Identity
>Let $(G,+,\cdot)$ is a [[#^2c4055|Ring]]. We say that $(G,+,\;\cdot\;)$ a **ring with identity** if
>- $(G\setminus \{ 0 \},\;\cdot\;)$ has a [[#^0b2e62|neutral Element]], where $0$ is the neutral element with respect to $(G,+)$

^1a1069

>[!def] Definition Commutative Ring ([[../../../../PDFs/judson2022.pdf#page=194|Source]])
>Let $(G,+,\cdot)$ is a [[#^2c4055|Ring]]. We say that $(G,+,\;\cdot\;)$ a **commutative/Abelian ring** if it holds
>1. $(G\setminus \{ 0 \},\;\cdot\;)$ is [[#^0b2e62|Abelian]], where $0$ is the neutral element with respect to $(G,+)$

^4a5286

>[!def] Definition Integral Domain ([[../../../../PDFs/judson2022.pdf#page=194|Source]])
>Let $(G,+,\;\cdot\;)$ is a [[#^4a5286|commutative ring]]. We say that $(G,+,\;\cdot\;)$ is an **integral domain** if 
>- $\forall a,b \in G$ with $ab = 0$, then either $a=0$ or $b=0$

^f48d09

>[!def] Definition Division Ring ([[../../../../PDFs/judson2022.pdf#page=194|Source]])
>Let $(G,+,\;\cdot\;)$ is a [[#^1a1069|ring with identity]]. We say that $(G,+,\;\cdot\;)$ is a **division ring** if 
>- $(G\setminus \{ 0 \}, \;\cdot\;)$ has a [[#^0b2e62|neutral element]], where $0$ is the neutral element with respect to $(G,+)$

^d1eb27

>[!def] Definition Field ([[../../../../PDFs/judson2022.pdf#page=194|Source]])
>>[!def] Version 1
>>Let $(G,+,\;\cdot\;)$ is a [[#^d1eb27|division ring]]. We say that $(G,+,\;\cdot\;)$ is a **field** if
>>- $(G\setminus \{ 0 \}, \;\cdot\;)$ is [[#^0b2e62|commutative/Abelian]], where $0$ is the neutral element with respect to $(G,+)$
>
>>[!def] Version 2
>>We say that $(G,+,\;\cdot\;)$ is a **field** if the following holds
>>1. $(G,+)$ is a [[#^0b2e62|commutative/Abelian group]]
>>2. $(G\setminus \{ 0 \}, \;\cdot\;)$ is a [[#^0b2e62|commutative/Abelian group]] , where $0$ is the neutral element with respect to $(G,+)$
>>3. $(G,+,\;\cdot\;)$ is **distributive**: $\forall a,b,c \in G$:$$a(b+c)=ab+ac$$

^a17f1c

>[!remark] Remark on the Relationship of Basic Algebraic Structures
>|                    | Abelian $(G,+)$    | Associative $(G,\;\cdot\;)$ | Neutral Element  $(G,\;\cdot\;)$ | Inverse Element  $(G,\;\cdot\;)$ | Commutative  $(G,\;\cdot\;)$ | Distributive $(G,+,\;\cdot\;)$ |
>| ------------------ | ------------------ | --------------------------- | -------------------------------- | -------------------------------- | ---------------------------- | ------------------------------ |
>| Ring               | <center>x</center> | <center>x</center>          |                                  |                                  |                              | <center>x</center>             |
>| Ring with Identity | <center>x</center> | <center>x</center>          | <center>x</center>               |                                  |                              | <center>x</center>             |
>| Commutative Ring   | <center>x</center> | <center>x</center>          |                                  |                                  | <center>x</center>           | <center>x</center>             |
>| Integral Domain    | <center>x</center> | <center>x</center>          |                                  |                                  | <center>x</center>           | <center>x</center>             |
>| Division Ring      | <center>x</center> | <center>x</center>          | <center>x</center>               | <center>x</center>               |                              | <center>x</center>             |
>| Field              | <center>x</center> | <center>x</center>          | <center>x</center>               | <center>x</center>               |           <center>x</center>                   | <center>x</center>             |
><br>
>
>![[Figures/relationship.png|center|400]]
><center>Figure: Relationship of Algebraic Structures</center>


## Ring Homomorphisms and Ideals

^37f31d

>[!def] Definition Ring Homomorphism ([[../../../../PDFs/judson2022.pdf#page=207|Source]])
> Let $R,S$ be [[#^2c4055|rings]], then a **~={green}ring homomorphism=~** is a map $\phi:R\to S$ satisfying
> $$\begin{align}
> \phi(a+b) &= \phi(a)+\phi(b) \\
> \phi(ab)&= \phi(a)\phi(b)
>\end{align}$$
>for all $a,b \in R$. If $\phi$ is a bijection, then $\phi$ is called an **isomorphism of rings**

^c3d051

>[!def] Definition Kernel of a Ring ([[../../../../PDFs/judson2022.pdf#page=207|Source]])
> Let $R,S$ be [[#^2c4055|rings]] and $\phi:R\to S$ a [[#^37f31d|ring homomorphism]]. We define the **~={green}kernel of a ring homomorphism=~** to be the set
> $$\text{ker }\phi=\{ r \in R \mid \phi(r)=0 \}$$



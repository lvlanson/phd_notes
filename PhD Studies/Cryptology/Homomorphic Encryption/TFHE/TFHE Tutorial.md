# Definitions
## Torus and $\mathbb{Z}$-Module

>[!def] Definition Real Torus
>Let $$\begin{align}
> \mathbb{T} &= \mathbb{R}/\mathbb{Z} \\
> &= [0,1) 
>\end{align}$$
>denote the **<span style="color:#38ffa9">Real Torus</span>**. 
>>[!remark]
>>One can think of the real torus as any element for $x \in \mathbb{R}$ to be
>>$$(x \text{ mod } 1) \in \mathbb{T}$$

^eae3a4

>[!def] Definition Group Action
>Let $G$ be a group with identity element, and $X$ a set. Then a (left) group action $\alpha$ of $G$ on $X$ is a mapping
>$$\alpha: G \times X \to X$$
>satisfying 
>$$\begin{align}
>\alpha(e,x) &= x \tag{identity} \\
>\alpha(g, \alpha(h,x)) &= \alpha(gh,x)
>\end{align}$$
>for $g,h \in G$ and $e$ being the identity in $G$.

^8df96c

>[!def] Definition $R$-Module
>Let $R$ denote a ring and $1$ its multiplicative identity. A (left) $R$-module $M$ consists of
>- an Abelian group $(M,+)$
>- an operation $\cdot: R \times M \to M$
>
>such that $\forall r,s \in R$ and $\forall x,y \in M$
>$$\begin{aligned}
> &&1. &&r \cdot (x+y) ) &= r \cdot x + r \cdot y \\
> &&2. &&(r+s)\cdot x &= r \cdot x + s \cdot x \\
> &&3. &&(rs) \cdot x &= r \cdot ( s \cdot x) \\
> &&4. && 1 \cdot x &= x
>\end{aligned}$$
>The operation $\cdot$ is called the *scalar multiplication*.

^40612a

>[!property] Properties of the Real Torus
>1. The [[#^eae3a4 | real torus]] forms an Abelian group $(\mathbb{T}, +)$ with $$\begin{align}
> e &= 0 \tag{identity Element}\\ 
> a + (-a) &= 1 = 0 \tag{inverse Element}
>\end{align}$$
>and associativity
>>[!remark]
>>The real torus $\mathbb{T}$ is **not** a ring, because $0 \sim 1$ in the torus.
>2. There is the [[#^8df96c|group action]] $$\cdot : \mathbb{Z} \times \mathbb{T} \to \mathbb{T}$$
>where for any $a \in \mathbb{Z}, t \in \mathbb{T}$ we have
>$$a \cdot t \in \mathbb{T}$$
>
>3. The real torus $\mathbb{T}$ is endowed with a $\mathbb{Z}$-[[#^40612a| module]]. Define for $k \in \mathbb{Z}$ and $t \in \mathbb{T}$ $$k \cdot t = \underbrace{t + \dots + t}_{k \text{- times}}$$
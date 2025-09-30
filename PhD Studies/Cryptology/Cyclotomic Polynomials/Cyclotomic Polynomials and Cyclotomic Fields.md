## 1. Cyclic Groups

See [[../../../Lehre/Kryptologie/7 - Algebraische und Zahlentheoretische Grundlagen (2)#^1a82a3 | definitions of cyclical groups]]

>[!proposition] Proposition ([[../../../PDFs/judson2022.pdf#page=60|Source]])
>Let $G$ be a cyclic group of order $n$ and suppose that $a$ is a generator for $G$. Then
>$$a^k = e \iff n \;|\; k$$
>>[!proof]-
>> 1. $\implies$
>> First, we know by the division algorithm that for $k$ there exists some quotient $q \in \mathbb{Z}$ and some remainder $0 \leq r < n$ such that $k = nq + r$. Therefore, we can write
>> $$\begin{align}
>> a^k &= a^{nq+r} \\
>> &=(\underbrace{ a^{n} }_{ =e })^q a^r \\
>> &= a^r
>>\end{align}$$
>>The only valid $r$ such that $a^r = e$ is $r=0$, which verifies that $n \;|\; k$
>>2. $\Longleftarrow$
>> By premise we know that $n \;|\; k \implies \exists q \in \mathbb{Z} : nq =k$, hence
>> $$\begin{align}
>> a^k = a^{nq} = (a^n)^q = e
>>\end{align}$$
>>$$\tag*{$\square$}$$

^7c0c47

>[!Theorem] Theorem ([[../../../PDFs/judson2022.pdf#page=60|Source]])
>Let $G$ be a cyclic group of order $n$ and suppose that $a \in G$ is a generator of the group. If $b=a^k$, then the order of $b$ is $\frac{n}{d}$ with $d=\text{gcd}(k,n)$.
>>[!proof]-
>>Note by the preceding [[#^7c0c47|proposition]], we know that iff $n \;|\; mk$ we have $a^{mk} = e$ for some $m \in \mathbb{Z}$. Defining $$d = \text{gcd}(k,n)$$
>>with that we can state
>>$$n \;|\; mk \iff \frac{n}{d} \;\Bigg| \frac{k}{d}m\;$$
>> Since $d$ is the greatest common divisor, $\text{gcd}\left( \frac{n}{d}, \frac{k}{d} \right) = 1$. Therefore, $\frac{n}{d}$ must divide $m$. This finally concludes to the smallest $m$ being $$m= \frac{n}{d}$$
>> which is in conclusion the order of $b$.

^3c8356

>[!Corollary] Corollary ([[../../../PDFs/judson2022.pdf#page=60|Source]])
>The generators of $\mathbb{Z}_{n}$ are the integers $r$ such that $1 \leq r < n$ and $\text{gcd}(r,n)= 1$
>>[!proof]-
>>This is an immediate result of the preceding [[#^3c8356|theorem]].

## 2. Roots of Unity

>[!def] Definition $n$-th Root of Unity
>For $n \geq 1$ the $n$-th root of unity satisfies
>$$z^n = 1$$
>and is characterized as
>$$\begin{align}
>\zeta_{n}^k &= \exp\left( \frac{2k\pi i}{n} \right)  \\
>&= \cos\left( \frac{2k\pi}{n} \right) + i \sin\left( \frac{2k\pi}{n} \right)
>\end{align}$$
>with $k \in \{ 0,1,2,\dots ,n-1 \}$. The set of all $n$-th roots of unity is denoted as
>$$\mu_{n} = \{ \zeta_{n}^k  \; | \; 0 \leq k < n\}$$

^f01099

>[!def] Definition Primitive $n$-th Root of Unity
> An $n$-th root of unity is said to be **<span style="color:#38ffa9">primitive</span>** if it is not an $m$-th root of unity with $1 \leq m <n$, that is if
> $$z^n = 1 \text{ and } z^m \neq 1 \text{ for } m \in\{ 1,2,3,\dots, n-1 \}$$

>[!example] Example for Roots of Unity vs Primitive Roots of Unity
>Let $n = 6$. The $6$-th roots of unity are given as
>$$\begin{align}
> \zeta_{6}^0 &= \exp\left( \frac{2\cdot0 \cdot \pi i}{6} \right) = 1 \\
>\zeta_{6}^1 &= \exp\left( \frac{2\cdot 1 \cdot \pi i}{6} \right)   \\
>\zeta_{6}^2&= \exp\left( \frac{2\cdot 2 \cdot \pi i}{6} \right)  \\
>\zeta_{6}^3&= \exp\left( \frac{2\cdot 3 \cdot \pi i}{6} \right) = -1 \\
>\zeta_{6}^4&= \exp\left( \frac{2\cdot 4 \cdot \pi i}{6} \right)  \\
>\zeta_{6}^5&= \exp\left( \frac{2\cdot 5 \cdot \pi i}{6} \right)  \\
>\end{align}$$
>![[../../../Pasted image 20250803160053.png| center |  500]]
>Now we check which of those roots of unity are **<span style="color:#f7b8ff">primitive</span>**. 
>Note that
>$$\begin{align}
> \left(\zeta_{6}^0\right)^m = 1\end{align}$$
> for any $m \in \mathbb{N}$, hence why $0$ is excluded from the definition. For the other examples we can find that
> $$\begin{align}
> \left(\zeta_{6}^2\right)^3 &= \exp\left( \frac{\boldsymbol{3} \cdot 2\cdot 2 \cdot \pi i}{6} \right) \\
> &= 1 \tag{Not Primitive Root}\\
> \left(\zeta_{6}^3\right)^4 &= \exp\left( \frac{\boldsymbol{2} \cdot 2\cdot 3 \cdot \pi i}{6} \right)  \\
> &= 1 \tag{Not Primitive Root}\\
> \left(\zeta_{6}^4\right)^3 &= \exp\left( \frac{\boldsymbol{3} \cdot 2\cdot 4 \cdot \pi i}{6} \right)  \\ 
> &= \exp\left( {4 \cdot \pi i} \right) \\
> &= \exp\left( {2 \cdot \pi i} \right) \cdot \exp\left( {2 \cdot \pi i} \right) \\
> &= 1 \tag{Not Primitive Root}\\
>\end{align}$$
> For $\zeta_{6}^1$ and $\zeta_{6}^5$ we can't find any $1 \leq m < n$ such that
> $$\left(\zeta_{6}^1\right)^m = 1 \text{ or } \left(\zeta_{6}^5\right)^m = 1$$
> which is why they are $n$-th primitive roots of unity.

>[!theorem] Theorem $n$-th Roots of Unity is a Multiplicative Group
> Let $n \in \mathbb{N}$, then the $n$-th roots of unity form a group under multiplication
>>[!proof]-
>>1. <u>Closure of Multiplication</u>
>>Let $\exp\left( \frac{2\pi i}{n}k \right), \exp\left( \frac{2\pi i}{n}j \right)$ denote primitive $n$-th roots of unity. We want to show that
>>$$\exp\left( \frac{2\pi i}{n}k \right) \cdot \exp\left( \frac{2\pi i}{n}j \right) = \exp\left( \frac{2\pi i}{n}(k+j) \right)$$
>>**always** yields an $n$-th root of unity. By the division algorithm, we know that we decompose any integer in a quotient $q \in \mathbb{Z}$ and some remainder $0 \leq r < n$ such that for our case we have
>>$$j+k = n \cdot q + r$$
>>Hence, we get
>>$$\begin{align}
>> \exp\left( \frac{2\pi i}{n}(k+j) \right) &= \exp\left( \frac{2\pi i}{n}(nq +r) \right) \\
>> &= \underbrace{ \exp\left( 2\pi iq \right) }_{ = 1^q } \exp\left( \frac{2\pi ir}{n}\right) \\
>> &= \exp\left( \frac{2\pi ir}{n}\right)
>>\end{align}$$
>>2. <u>Associativity</u>
>>Let $\exp\left( \frac{2\pi i}{n}k \right), \exp\left( \frac{2\pi i}{n}j \right), \exp\left( \frac{2\pi i}{n}l \right)$ denote primitive $n$-th roots of unity, then
>>$$\begin{align}
>> \left(\exp\left( \frac{2\pi i}{n}k \right) \cdot \exp\left( \frac{2\pi i}{n}j \right)\right) \cdot \exp\left( \frac{2\pi i}{n}l \right) &=  \exp\left( \frac{2\pi i}{n}(k+j) \right) \cdot \exp\left( \frac{2\pi i}{n}l \right)  \\
>> &=\exp\left( \frac{2\pi i}{n}(k+j + l) \right) \\
>> &= \exp\left( \frac{2\pi i}{n}k \right) \cdot \exp\left( \frac{2\pi i}{n}(j+l) \right) \\
>> &= \exp\left( \frac{2\pi i}{n}k \right) \cdot \left(\exp\left( \frac{2\pi i}{n}j \right) \cdot \exp\left( \frac{2\pi i}{n}l \right)\right) 
>>\end{align}$$
>>3. <u>Identity Element</u>
>>Since $$\exp\left( \frac{2\pi i}{n} \cdot 0 \right) = 1$$ is an $n$-th root of unity, it acts as a neutral element since
>>$$\exp\left( \frac{2\pi i}{n} \cdot 0 \right) \exp\left( \frac{2\pi i}{n} \cdot k \right) = \exp\left( \frac{2\pi i}{n} \cdot k \right)$$
>>4. <u> Inverse Element</u>
>>Note that for any $n$-th root of unity $\exp \left( \frac{2\pi i}{n} k\right)$ there also exists some $n$-th root of unity $\exp \left( \frac{2\pi i}{n} (n-k)\right)$.  We have that
>>$$\begin{align}
>> \exp \left( \frac{2\pi i}{n} k\right) \cdot \exp \left( \frac{2\pi i}{n} (n-k)\right) &=  \exp \left( \frac{2\pi i}{n} n\right)  \\
&= 1
>>\end{align}$$
>>Hence, there always exists a multiplicative inverse for any $n$-th root of unity.
>>
>>This concludes to the $n$-th roots of unity, forming a multiplicative group. $$\tag*{$\square$}$$

>[!def] Definition Order of an Element in a Group
>Let $G$ be a group and $g \in G$. Then the order of $g$ is defined to be the integer $n$ which satisfies
>$$g^n= e$$
>with $e$ being the identity in $G$.

>[!def] Definition 2 Primitive $n$-th Root of Unity
>An $n$-th root of unity is said to be **<span style="color:#38ffa9">primitive</span>** if its order is $n$.

>[!Theorem] Group Isomorphism of $\mathbb{Z}_{n}$ and $n$-th Roots of Unity
>The function $$\psi: \mathbb{Z}_{n} \to \mu_{n}$$
>given by $$\psi(k) = \exp\left( \frac{2\pi i}{n}k \right)$$ 
>is a group isomorphism, i.e.
>$$(\mathbb{Z}_{n},+) \simeq (\mu_{n}, \;\cdot\;)$$
>>[!proof]-
>>1. <u>Well Definedness</u>
>> We first verify that $\psi$ is well-defined on equivalency classes, i.e.
>>$$j \equiv k \;\;(\text{mod } n) \implies \psi(j) = \psi(k)$$
>>for any $j,k \in \mathbb{Z}_{n}$. We know that
>>$$\begin{aligned}
>>  j \equiv k \;\;(\text{mod } n) &\iff n \;|\; j-k \\
>>  &\overset{\exists q \in \mathbb{Z}}{\iff} n q = j-k \\ 
>>  &\iff j = nq + k
>>\end{aligned}$$
>>using that result we verify that indeed $\psi(j)= \psi(k)$
>> $$\begin{align}
>> && \exp\left( \frac{2\pi i}{n}j \right) &= \exp\left( \frac{2\pi i}{n}k \right)  \\
>>&& \exp\left( \frac{2\pi i}{n} ( nq + k)\right) &= \exp\left( \frac{2\pi i}{n}k \right)  \\
>>&& \underbrace{ \exp\left( 2\pi i q \right) }_{ = 1 } \exp\left( \frac{2\pi i}{n} k\right) &= \exp\left( \frac{2\pi i}{n}k \right) \\
>>\end{align}
>>$$
>>2. <u>Bijectivity</u>
>>Let $\exp\left( \frac{2\pi i}{n}k \right)$ be an $n$-th root of unity. Then for any $k \in \mathbb{Z}_{n}$ we have $$\psi(k) = \exp\left( \frac{2\pi i}{n}k \right)$$
>>which shows that the mapping is **surjective**. <br>
>>Now, let $j,k \in \mathbb{Z}_{n}$. Suppose that $\phi(k)= \phi(j)$, then
>>$$\exp\left( \frac{2\pi i}{n}k \right) = \exp\left( \frac{2\pi i}{n}j \right) \implies j \equiv k \;\;(\text{mod }  n)$$
>>thus $\psi$ is **injective** and in conclusion is **bijective**.
>>
>>3. <u>Group Homomorphism</u>
>>Finally, we verify that $\psi$ preserves the group operation. For $j,k \in \mathbb{Z}_{n}$
>>$$\begin{aligned}
>>& \psi(j+k) &&= \psi(j)\psi(k)  \\
>>\iff& \exp\left( \frac{2\pi i}{n}(j+k) \right) &&= \exp\left( \frac{2\pi i}{n}j \right) \exp\left( \frac{2\pi i}{n}k \right)
>>\end{aligned}$$
>>which is a true statement. Hence, $\psi$ is a **group isomorphism**. $$\tag*{$\square$}$$

>[!theorem] 
>Let $n \in \mathbb{N}$. The primitive $n$-th roots of unity are
>$$\left\{  \exp\left( \frac{2\pi i}{n}k \right) \;|\; 1 \leq k \leq n, \text{ggT}(k,n) = 1  \right\}$$
>>[!proof]-
>> Note by the [[#^7c0c47|proposition]] some element $k \in \mathbb{Z}_{n}$ has order $n$ if and only if $\text{gcd}(k,n)=1$. Since $(\mathbb{Z}_{n},+)$ is isomorphic to $(\mu_{n}, \;\cdot\;)$, this can also be stated for roots of unity, i.e. some root of unity has order $n$ if and only if $\text{gcd}(k,n)=1$. If it has order $n$ then it is also a primitive $n$-th root of unity. This concludes the proof. $$\tag*{$\square$}$$

## 3.

>[!def] Definition Algebraic Numbers ([[../../../PDFs/Mukherjee.pdf#page=26|Source]])
>A number $\alpha \in \mathbb{C}$ is algebraic if it satisfies a polynomial equation
>$$x^n + a_{n-1}x^{n-1}+\dots+a_{1}x+a_{0} = 0$$
>where $a_{i} \in \mathbb{Q}$ for all $i \in \{ 0,1,2,\dots,n-1 \}$

>[!def] Definition Algebraic Integer ([[../../../PDFs/Mukherjee.pdf#page=26|Source]])
>A number $\alpha \in \mathbb{C}$ is an algebraic integer if it satisfies a polynomial equation
>$$x^n + a_{n-1}x^{n-1}+ \dots + a_{1}x+x_{0} = 0$$
>where $a_{i} \in \mathbb{Z}$ for all $i \in \{ 0,1,2,\dots,n-1 \}$

>[!def] Definition Cyclotomic Field ([[../../../PDFs/Mukherjee.pdf#page=27|Source]])
> If $K$ is a subfield of $\mathbb{C}$ such that $K=\mathbb{Q}(\alpha)$ for some [[#^f01099 | root of unity]] $\omega$, then $K$ is called a cyclotomic field.

>[!def] Definition Cyclotomic Polynomial
>The $n$-th **<span style="color:#38ffa9">cyclotomic polynomial</span>** is defined as
>$$\begin{align}
> \Phi_{n}(x) &= \prod_{\substack{1 \leq k < n \\ \text{gcd}(k,n)=1}} \left(x-e^{2\pi ik/n}\right)  \\
&= \prod_{\substack{1 \leq k < n \\ \text{gcd}(k,n)=1} } \left(x-\zeta_{n}^k\right)
>\end{align}$$
>which is **<span style="color:#38ffa9">irreducible</span>**, so it is the minimal polynomial of $\zeta_{n}$ over $\mathbb{Q}$.
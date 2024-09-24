## Fundamentals

>[!def] Definition Space of $m$-times differentiable $L$-periodic Functions ([[../../../PDFs/salgado2022.pdf#page=884|Source]])
> Let $m \in \mathbb{N}_{0}$ and $L>0$, then the set of $m$-times differentiable $L$-periodic Functions over the complex Numbers $\mathbb{C}$ is defined as
> $$C_{p}^m(0,L;\mathbb{C})=\{ f \in C^m(\mathbb{R},\mathbb{C}) \mid f(x+nL)=f(x), \forall n \in \mathbb{Z}, \forall x \in \mathbb{R} \}$$
> where $C^m(\mathbb{R},\mathbb{C})$ denotes the set of $m$-times differentiable functions mapping from $\mathbb{R}$ to $\mathbb{C}$.

>[!def] Definition Nodal Set ([[../../../PDFs/salgado2022.pdf#page=232|Source]])
> Let $[a,b] \subset \mathbb{R}$ be a compact interval. $X$ is called a **nodal set** of size $n+1 \in \mathbb{N}$ in $[a,b]$ if and only if $X=\{ x_{i} \}_{i=0}^n \subset [a,b]$ is a set of distinct elements. The elements of $X$, i.e. $x_{i}$, are called **nodes**.

^0f4f22

>[!def] Definition Trigonometric Polynomial ([[../../../PDFs/salgado2022.pdf#page=321|Source]])
> Let $n \in \mathbb{N}_{0}$. The function
> $$p_{n}(x)= \sum_{j=-n}^n c_{j} \exp(2\pi i j x)$$
> where $c_{j} \in \mathbb{C}$ and $j \in \{ -n, \dots, n \}$ is called a **trigonometric polynomial** of degree at most $n$. 
> 
> The set of all such polynomials is labeled $\mathbb{T}_{n}(0,1)$ or just $\mathbb{T}_{n}$ when the period is understood, i.e.
> $$\mathbb{T}_{n} = \left\{  p(x) = \sum_{j=-n}^n c_{j} \exp(2\pi i j x) \;\Bigg\vert\; \exists c_{j} \in \mathbb{C}, j \in \{ -n,n \} \right\}$$
> 
> Under the usual function operations, this is a vector space over the field of the complex numbers.

^ddb0ce

>[!def] Definition Trigonometric Interpolation ([[../../../PDFs/salgado2022.pdf#page=372|Source]])
> Let $f \in C_{p}(0,1; \mathbb{C})$ and $n \in \mathbb{N}$. Suppose that $X=\{ x_{j} \}_{j=0}^{n-1}$ is a uniformly spaced [[#^0f4f22|nodal set]]:
> $$x_{j} =  \frac{j}{n} \tag*{$j \in \{ 0,\dots,n-1 \}$}$$
> Further, denote $K = \left\lceil  \dfrac{n}{2}  \right\rceil$. The function $q \in \mathbb{T}_{k}(0,1)$ is called a **trigonometric interpolating polynomial of $f$ subordinate to $X$** if and only if $\forall j \in \{ 0,\dots,n-1 \}$:
> $$q(x_{j})=f(x_{j})$$

>[!def] Definition Grid Functions ([[../../../PDFs/salgado2022.pdf#page=373|Source]])
>Let $n \in \mathbb{N}$ and denote
>$$\mathcal{V}(\mathbb{C})= \{ w \mid w: \mathbb{Z} \to \mathbb{C} \}$$
>as the **set of grid functions**. 
>>[!remark]
>>Grid functions will further be denoted as
>>$$w_{i}= w(i) \tag*{$i \in \mathbb{Z}$}$$
>
>The subspace of $n$**-periodic grid functions** is defined as
>$$\mathcal{V}_{n,p}(\mathbb{C})= \{ w \in \mathcal{V}(\mathbb{C}) \mid w_{i+mn} = w_{i} \}$$

^4780e3


>[!def] Definition Periodic Grid Delta Function ([[../../../PDFs/salgado2022.pdf#page=374|Source]])
> Let $n \in \mathbb{N}$. The **periodic grid delta function**, denoted $\delta^{n,p} \in \mathcal{V}(\mathbb{C})$, is defined via
> $$\delta_{j}^{n,p}=\begin{cases}
> 1, &\exists m \in \mathbb{Z} \text{ such that } j=mn \\
> 0, &\forall m \in \mathbb{Z} \text{ such that } j\neq mn \\
>\end{cases} \tag*{$\forall j \in \mathbb{Z}$}
>$$
^periodicdelta

>[!lemma] Proposition Convolution with Delta Functions([[../../../PDFs/salgado2022.pdf#page=374|Source]])
>Let $n \in \mathbb{N}$ and $\delta_{j}^{n,p} \in \mathcal{V}_{n,p}(\mathbb{C})$. Furthermore, for any $u \in \mathcal{V}_{n,p}(\mathbb{C})$ it follows that
>$$\sum_{j=0}^{n-1}u_{j}\delta_{j-k}^{n,p} = u_{k} \tag*{$\forall k \in \mathbb{Z}$}$$ 
>>[!proof]-
>>We first note
>>$$\delta_{j-k}^{n,p} = 1 \iff j-k = nm \iff j \equiv k \;\;(\text{mod } n)$$
>>Hence, any integer $k$ which is equivalent to $j$ yields $\delta_{j-k}^{n,p} = 1$.  Without loss of generality we restrict $k\geq 0$.
>>
>><u> Case 1:</u> $k<n$
>>
>>The only number equivalent integer to $k$ with respect to modulus $n$ is $k$ itself, by definition of residue classes. We conclude
>>$$k \equiv k \;\;(\text{mod } n)\implies \delta_{0}^{n,p} = 1 \implies \sum_{j=0}^{n-1}u_{j}\delta_{j-k}^{n,p} = u_{k} $$
>>Since $0 = nm$ solves for $m=0$ for any $n \in \mathbb{N}$.
>>
>><u> Case 2:</u> $k\geq n$
>>
>>First we make a change of variables and denote $t \geq n$
>>$$t = n \cdot m + k $$
>>for some $m \in \mathbb{Z}$. Clearly,
>>$$n \cdot m + k \equiv k \;\;(\text{mod } n) $$
>>Therefore, we get
>>$$\begin{align}
>> t = n \cdot m + k &\implies n \cdot m + k \equiv k \;\;(\text{mod } n)  \\
>> &\implies \delta_{j-t}^{n,p} = 1 \\
>> &\implies \sum_{j=0}^{n-1}u_{j}\delta_{j-t}^{n,p} = u_{k} \\
>> &\implies \sum_{j=0}^{n-1}u_{j}\delta_{j-k}^{n,p} = u_{k} 
>>\end{align} $$
>>$$\tag*{$\square$}$$

^6e050a

>[!def] Definition Roots of Unity ([[../../../PDFs/salgado2022.pdf#page=374|Source]])
>Let $n \in \mathbb{N}$. Suppose that $X = \left\{  x_{j} = \frac{j}{n}  \right\}_{j=0}^{n-1}$ is the standard uniformly spaced [[#^0f4f22|nodal set]]. The grid function
>$$\omega_{n,k}= \exp(2\pi i x_{k}) \tag*{$k \in \mathbb{Z}$}$$
>is called the **n-th root of unity**. 
> ---
>The **$n$-th root of unity grid function** as a whole is denoted as $\omega_{n} \in \mathcal{V}(\mathbb{C})$.
>
>>[!pic]
>>![[figures/roots_of_unity.png|center|600]]
>><center>Figure: n-th roots of unity with n=12</center>

>[!property] Properties of n-th roots $\omega_{n}$ ([[../../../PDFs/salgado2022.pdf#page=374|Source]])
>Let $n \in \mathbb{N}$. 
>1. Let $\omega_{n} \in \mathcal{V}_{n,p}(\mathbb{C})$ and
>$$\omega_{n,k}^n = 1 \tag*{$\forall k  \in \mathbb{Z}$}$$
>where the superscript is an exponent.
>2. The functions $\omega_{n}^j \in \mathcal{V}(\mathbb{C}), j \in \mathbb{Z}$ that are defined by
> $$\omega_{n,k}^j = \exp(2\pi i j x_{k}) \tag*{$k \in \mathbb{Z}$}$$
> are periodic, i.e.
> $$\omega_{n,k+mn}^j= \omega_{n,k}^j \tag*{$\forall j,k,m \in \mathbb{Z}$}$$
> 3. $$\Big(\omega_{n,k}^j\Big)^n = 1 \tag*{$\forall j,k \in \mathbb{Z}$}$$
>
>>[!proof]-
>> 1. <br>$$\begin{align}
>> \omega_{n,k}^n &= \exp(2\pi i x_{k})^n \\
>> &= \exp(2\pi i x_{k} n) \\
>> &= \exp\left( 2\pi i \frac{k}{\cancel{ n }}\cancel{ n } \right) \\
>> &= \exp\left( 2\pi i \right)^k \\
>> &= 1^k \\
>> &= 1\tag*{$\square$}
>>\end{align}$$
>>where we used [[../Complex Analysis/Fundamental Properties#^45ef91| the identity]] $e^{2\pi i}=1$
>>2. <br>$$\begin{align}
>> \omega^j_{n,k+mn} &= \exp(2\pi i x_{k+mn})^j \\
>> &= \exp\left( 2\pi i j\frac{k+mn}{n} \right) \\
>> &= \exp\left( 2\pi i j\frac{k}{n} \right) \exp\left( 2\pi i j \frac{m\cancel{ n }}{\cancel{ n }} \right) \\
>> &= \exp\left( 2\pi i x_{k} \right)^j \cdot 1 \\
>> &= \omega^j_{n,k} \tag*{$\square$}\\
>>\end{align}$$
>>3. <br>$$\begin{align}
>> \Big(\omega_{n,k}^j\Big)^n &= \omega_{n,k}^{jn} \\
>> &=  \Big(\underbrace{ \omega_{n,k}^n }_{ =1 }\Big)^j \tag*{by (1)}\\
>> &= 1
>>\end{align}$$

## The Discrete Fourier Transform

>[!def] Definition Discrete Fourier Transform (DFT) ([[../../../PDFs/salgado2022.pdf#page=375|Source]])
>Let $n \in \mathbb{N}$. For all $u \in \mathcal{V}_{n,p}(\mathbb{C})$ and all $k \in \mathbb{Z}$ we define
>$$\mathcal{F}_{n}[u]_{k} = \widehat{u}_{k}= \frac{1}{n} \sum_{l=0}^{n-1} u_{l} \exp\left( -2\pi i k \frac{l}{n} \right)$$
>The grid function $\widehat{u}\in \mathcal{V}(\mathbb{C})$ is called the **Discrete Fourier Transform** (DFT) of $u$ and we write $\widehat{u}= \mathcal{F}_{n}[u]$.
>>[!algo] Python Implementation
>>```python
>>import numpy as np
>>
>>def F_n(Y):
>>    n = len(Y)
>>    Y_hat = []
>>    for k in range(len(Y)):
>> 	   summands = [y_l*np.exp(-2*np.pi*1j*k*l/n) for l, y_l in enumerate(Y)]
>>        transformed_k = sum(summands) / n
>>        Y_hat.append(transformed_k)
>>    return Y_hat
>>```

^db3d1d

>[!lemma] Proposition Periodicity of DFTs ([[../../../PDFs/salgado2022.pdf#page=375|Source]])
>Let $n \in \mathbb{N}$. For all $u \in \mathcal{V}_{n,p}(\mathbb{C})$, we have $\widehat{u} \in \mathcal{V}_{n,p}(\mathbb{C})$, i.e., the DFT is a periodic grid function.
>>[!proof]-
>>We want to show that
>>$$\widehat{u}_{k}= \widehat{u}_{k+mn}$$
>>Hence,
>>$$\begin{align}
>> \widehat{u}_{k+mn} &= \frac{1}{n} \sum_{l=0}^{n-1} u_{l}\exp\left( -2\pi i \frac{l}{n}(k+mn) \right) \\
>> &= \frac{1}{n} \sum_{l=0}^{n-1} u_{l}\exp\left( -2\pi i \frac{l}{n}k \right) \exp\left( -2\pi i \frac{l}{\cancel{ n }}m\cancel{ n } \right) \\
>> &= \frac{1}{n} \sum_{l=0}^{n-1} u_{l}\exp\left( -2\pi i \frac{l}{n}k \right) \exp\left( -2\pi i \right)^{lm} \\
>> &= \frac{1}{n} \sum_{l=0}^{n-1} u_{l}\exp\left( -2\pi i \frac{l}{n}k \right) \cdot 1 \\
>> &= \frac{1}{n} \sum_{l=0}^{n-1} u_{l}\exp\left( -2\pi i \frac{l}{n}k \right)   \\
>> &= \widehat{u}_{k} \tag*{$\square$}
>>\end{align}$$

>[!lemma] Proposition Periodic Grid Delta of $n$-th Roots ([[../../../PDFs/salgado2022.pdf#page=376|Source]])
> Let $n \in \mathbb{N}$. For all $k \in \mathbb{Z}$ [[#^periodicdelta|we have]]
> $$\delta_{k}^{n,p}= \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right)$$
>
>>[!proof]-
>>1. $k \neq mn$<br>
>>First we assume $k \neq mn$ for any $m \in \mathbb{Z}$. We will now establish an identity, which we will use to show, that the [[#^periodicdelta|periodic grid delta function]] must be $1$ given $k \neq mn$. We multiply the [[#^periodicdelta|periodic grid delta function]] with $\exp\left( 2\pi i \dfrac{k}{n} \right)$ and get
>>$$\begin{align}
>> \exp\left( 2\pi i \dfrac{k}{n} \right)\frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) &=  \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{k(l+1)}{n} \right) \\
>> &= \frac{1}{n}\sum_{l=1}^{n}\exp\left( 2\pi i  \frac{kl}{n} \right) \\
>> &= \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) \tag{Periodicity}
>>\end{align}$$
>>We work with this identity
>>$$\begin{align}
>> \exp\left( 2\pi i \dfrac{k}{n} \right)\frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) &= \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) \qquad&&\Big\vert  -\frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right)  \\
>> \exp\left( 2\pi i \dfrac{k}{n} \right)\frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) - \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) &= 0 \\
>> \left( \exp\left( 2\pi i \dfrac{k}{n} \right) - 1 \right)\frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) &= 0
>>\end{align}$$
>>By assumption of $k \neq mn$ the factor $\left( \exp\left( 2\pi i \dfrac{k}{n} \right) - 1 \right)$ can't become $0$. Therefore, the sum must be $0$, hence
>>$$k \neq mn \implies \delta_{k}^{n,p}= \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) = 0$$
>>2. $k = mn$<br>
>>This case is a lot easier to show, since
>>$$\begin{align}
>> \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{kl}{n} \right) &= \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i  \frac{m\cancel{ n }l}{\cancel{ n }} \right) \\
>> &= \frac{1}{n}\sum_{l=0}^{n-1}\exp\left( 2\pi i \right)^{ml} \\
>> &= \frac{1}{n}\sum_{l=0}^{n-1}1 \\
>> &= \frac{1}{n}n \\
>> &= 1
>>\end{align}$$
>>which establishes the proposition. $$\tag*{$\square$}$$

^c71a31

>[!theorem] Theorem DFT is a Bijection ([[../../../PDFs/salgado2022.pdf#page=376|Source]])
>Let $n \in \mathbb{N}$. The [[#^db3d1d|DFT]] mapping $$\begin{align}
> \mathcal{F}_{n}[u]&= \widehat{u} \\
> \mathcal{F}_{n}: \mathcal{V}(\mathbb{C}) &\to \mathcal{V}(\mathbb{C})
>\end{align}$$ 
>is a **linear bijection**.
>>[!proof]-
>>1. <u>Linearity:</u><br>
>>Let $u,v \in \mathcal{V}(\mathbb{C})$ and $\alpha \in \mathbb{C}$
>>$$\begin{align}
>> \mathcal{F}_{n}[u+v] &= \frac{1}{n} \sum_{l=0}^{n-1} (u_{l}+v_{l}) \exp\left( -2\pi i k \frac{l}{n} \right) \\
>>  &= \frac{1}{n} \sum_{l=0}^{n-1} u_{l}\exp\left( -2\pi i k \frac{l}{n} \right)+v_{l}\exp\left( -2\pi i k \frac{l}{n} \right)\\
>>  &= \frac{1}{n} \sum_{l=0}^{n-1} u_{l}\exp\left( -2\pi i k \frac{l}{n} \right)+\frac{1}{n}\sum_{l=0}^{n-1}v_{l}\exp\left( -2\pi i k \frac{l}{n} \right) \\
>>  &= \mathcal{F}_{n}[u]+\mathcal{F}_{n}[v] \tag*{$\checkmark$} \\[1em]
>>  \mathcal{F}_{n}[\alpha u] &= \frac{1}{n} \sum_{l=0}^{n-1} \alpha u_{l}\exp\left( -2\pi i k \frac{l}{n} \right) \\
>> &= \alpha \frac{1}{n} \sum_{l=0}^{n-1} u_{l}\exp\left( -2\pi i k \frac{l}{n} \right) \\
>> &= \alpha \mathcal{F}_{n}[u] \tag*{$\checkmark$}
>>\end{align}$$
>>2. <u>Injectivity:</u> 
>> Let $u,v \in \mathcal{V}_{n,p}(\mathbb{C})$ with $u \neq v$ and assume $\mathcal{F}_{n}[u] = \mathcal{F}_{n}[v]$. Hence, $\forall k \in \mathbb{Z}$ we get
>> $$\begin{align}
>> \frac{1}{n}\sum_{l=0}^{n-1}u_{l}\exp\left( -2\pi i\frac{kl}{n} \right) &= \frac{1}{n}\sum_{l=0}^{n-1}v_{l}\exp\left( -2\pi i\frac{kl}{n} \right)  \\
>> \frac{1}{n}\sum_{l=0}^{n-1}u_{l}\exp\left( -2\pi i\frac{kl}{n} \right) - \frac{1}{n}\sum_{l=0}^{n-1}v_{l}\exp\left( -2\pi i\frac{kl}{n} \right) &= 0 \\
>> \frac{1}{n}\sum_{l=0}^{n-1}(u_{l} - v_{l})\exp\left( -2\pi i\frac{kl}{n} \right) &= 0
>>\end{align}$$
>>Since any $k$ gives this identity, we can iterate over all $k$ and therefore multiply both sides with $\sum_{l=0}^{n-1}\exp\left( 2\pi i \frac{kl}{n} \right)$ such that for any $j \in \mathbb{Z}$
>>$$\begin{align}
>> 0 &=\frac{1}{n}\sum_{k=0}^{n-1}\exp\left( 2\pi i \frac{jk}{n} \right) \sum_{l=0}^{n-1}(u_{l} - v_{l})\exp\left( -2\pi i\frac{kl}{n} \right)  \\
>> &=\frac{1}{n} \sum_{l=0}^{n-1}(u_{l} - v_{l})\sum_{k=0}^{n-1}\exp\left( 2\pi i \frac{(j-l)k}{n} \right) \\
>> &= \frac{1}{n} \sum_{l=0}^{n-1}(u_{l} - v_{l}) \delta_{j-l}^{n,p} \\
>> &= \frac{1}{n} \sum_{l=0}^{n-1}(u_{l} - v_{l}) \delta_{l-j}^{n,p} \tag{1}\\
>> &= u_{j}-w_{j} \tag{2}
>>\end{align}$$
>>where in $(1)$ we made use of the fact that $j \equiv l \;\;(\text{mod } n)$ and in $(2)$ [[#^6e050a|convolution property]] of periodic grid delta functions. Hence, all $u_{j}=w_{j}$ which contradicts the assumption that they are different. Therefore, $\mathcal{F}_{n}$ is injective. $$\tag*{$\checkmark$}$$
>>
>>3. <u>Surjectivity:</u><br>
>> We want to show, that for an arbitrary $v \in \mathcal{V}_{n,p}(\mathbb{C})$ we can find some $w \in \mathcal{V}_{n,p}(\mathbb{C})$ such that $$\widehat{w}=\mathcal{F}_{n}[w]=v$$ If there is such a $w$, it would be of the form
>> $$w_{k} = \sum_{l=0}^{n-1}v_{l}\exp\left( 2\pi i \frac{kl}{n} \right)\tag{1}$$
>> for all $k \in \mathbb{Z}$. When mapping $w$, we get
>> $$\begin{align}
>> \widehat{w}_{j} = \mathcal{F}_{n}[w]_{j}&= \frac{1}{n}\sum_{k=0}^{n-1}w_{k}\exp\left( -2\pi i \frac{kj}{n} \right) \\
>> &= \frac{1}{n}\sum_{k=0}^{n-1}\sum_{l=0}^{n-1}v_{l}\exp\left( 2\pi i \frac{kl}{n} \right)\exp\left( -2\pi i \frac{kj}{n} \right) \tag*{from (1)} \\
>> &= \frac{1}{n}\sum_{k=0}^{n-1}\sum_{l=0}^{n-1}v_{l}\exp\left( 2\pi i \frac{k(l-j)}{n} \right) \\
>> &= \sum_{l=0}^{n-1}v_{l}\frac{1}{n}\sum_{k=0}^{n-1}\exp\left( 2\pi i \frac{k(l-j)}{n} \right) \\ 
>> &= \sum_{l=0}^{n-1}v_{l}\delta_{l-j}^{n,p}\\  
>> &= v_{j}
>>\end{align}$$
>>using again the [[#^6e050a|convolution property]] of periodic grid delta functions. Therefore, for any arbitrary $v \in \mathcal{V}_{n,p}(\mathbb{C})$ we can find some $w \in\mathcal{V}_{n,p}(\mathbb{C})$ such that
>>$$\mathcal{F}_{n}[w]=v \tag*{$\checkmark$}$$
>>
>>This establishes the theorem $$\tag*{$\square$}$$

^7594db

>[!def] Definition Inverse Discrete Fourier Transform (IDFT)([[../../../PDFs/salgado2022.pdf#page=377|Source]])
> The **Inverse Discrete Fourier Transform (IDFT)** is defined via
> $$\mathcal{F}_{n}^{-1}[w]_{k} = \sum_{l=0}^{n-1}w_{l}\exp\left( 2\pi i \frac{kl}{n} \right) \tag*{$\forall w \in \mathcal{V}_{n,p}(\mathbb{C})$}$$ 
>
>>[!algo] Python Implementation
>>```python
>>def F_n_inv(Y_hat):
>>    n = len(Y_hat)
>>    Y = []
>>    for k in range(len(Y_hat)):
>>        summands = [y_l * np.exp(2*np.pi*1j*k*l/n) for l, y_l in enumerate(Y_hat)]
>>        transformed_k =sum (summands)
>>        Y.append(transformed_k)
>>
>>    return Y
>>    ```
^a15a86

>[!remark] Remark on the Bijectivity of the IDFT 
> From the [[#^7594db| bijection theorem of the DFT]] the bijectivity of the [[#^a15a86|IDFT]] follows immediately. For some $w \in \mathcal{V}_{n,p}(\mathbb{C})$ 
>$$w = \mathcal{F}_{n}\Big[\mathcal{F}_{n}^{-1}[w]\Big] = \mathcal{F}_{n}^{-1}\Big[\mathcal{F}_{n}[w]\Big]$$

>[!theorem] Theorem Discrete Parseval's Identity ([[../../../PDFs/salgado2022.pdf#page=377|Source]])
>Let $n \in \mathbb{N}$. Suppose $w \in \mathcal{V}_{n,p}(\mathbb{C})$ and $\widehat{w} \in \mathcal{V}_{n,p}(\mathbb{C})$ is its [[#^db3d1d|DFT]], then
>$$\frac{1}{n}\sum_{k=0}^{n-1}w_{k}\overline{w_{k}} = \sum_{k=0}^{n-1}\widehat{w_{k}}\overline{\widehat{w}_{k}}$$
>>[!proof]-
>> First we denote the Fourier coefficients
>> $$\begin{align}
>> \widehat{w_{k}} = \mathcal{F}_{n}[w_{k}] &= \frac{1}{n}\sum_{j=0}^{n-1}w_{j}\exp\left( -2\pi i \frac{jk}{n} \right) \\
>> \overline{\widehat{w_{k}}} = \overline{\mathcal{F}_{n}[w_{k}]} &= \overline{\frac{1}{n}\sum_{l=0}^{n-1} w_{l }\exp\left( -2\pi i \frac{lk}{n} \right)} \\
>> &=\frac{1}{n}\sum_{l=0}^{n-1}\overline{w_{l}}\exp\left( 2\pi i \frac{lk}{n} \right)
>>\end{align}$$
>>We first give the product
>>$$\begin{align}
>> \widehat{w_{k}}\overline{\widehat{w}_{k}} &= \frac{1}{n}\sum_{j=0}^{n-1}w_{j}\exp\left( -2\pi i \frac{jk}{n} \right)\frac{1}{n}\sum_{l=0}^{n-1}\overline{w_{l}}\exp\left( 2\pi i \frac{lk}{n} \right) \\
>> &=\frac{1}{n^2} \sum_{j=0}^{n-1}w_{j}\sum_{l=0}^{n-1}\overline{w_{l}}\exp\left( 2\pi i \frac{(l-j)k}{n} \right) \\
>>\end{align}$$
>>We insert this to the complete expression
>>$$\begin{align}  
>> \sum_{k=0}^{n-1}\widehat{w_{k}}\overline{\widehat{w}_{k}} &= \sum_{k=0}^{n-1} \frac{1}{n^2} \sum_{j=0}^{n-1}w_{j}\sum_{l=0}^{n-1}\overline{w_{l}}\exp\left( 2\pi i \frac{(l-j)k}{n} \right) \\
>> &= \frac{1}{n^2}  \sum_{j=0}^{n-1}w_{j}\sum_{l=0}^{n-1}\overline{w_{l}}\sum_{k=0}^{n-1}\exp\left( 2\pi i \frac{(l-j)k}{n} \right) \\
>> &=\frac{1}{n^2} \sum_{j=0}^{n-1}w_{j}\sum_{l=0}^{n-1}\overline{w_{l}}   \cdot n \cdot \delta_{l-j}^{n,p}   \\
>> &=\frac{n}{n^2} \sum_{j=0}^{n-1}w_{j}\sum_{l=0}^{n-1}\overline{w_{l}}  \delta_{l-j}^{n,p} \tag{1}  \\
>> &= \frac{1}{n} \sum_{j=0}^{n-1}w_{j} \overline{w_{j}}
>>\end{align}$$
>> where at $(1)$ we used the [[#^6e050a|convolution property]]. This establishes the theorem. $$\tag*{$\square$}$$

>[!def] Definition Discrete Convolution ([[../../../PDFs/salgado2022.pdf#page=378|Source]])
>Let $n \in \mathbb{N}$ and $u,v \in \mathcal{V}_{n,p}(\mathbb{C})$. Then for all $k \in \mathbb{Z}$ 
>$$[u \star v]_{k}^{n,p}=\frac{1}{n}\sum_{j=0}^{n-1}u_{k-j}v_{j}$$
>The operator $$[\;\cdot\; \star \; \cdot \;]^{n,p}: \mathcal{V}_{n,p}(\mathbb{C})\times \mathcal{V}_{n,p}(\mathbb{C}) \to \mathcal{V}_{n,p}(\mathbb{C})$$ is called the **discrete periodic convolution**.

^4c1849

>[!property] Properties of Discrete Convolution ([[../../../PDFs/salgado2022.pdf#page=378|Source]])
>Let $n \in \mathbb{N}$ and $u,v \in \mathcal{V}_{n,p}(\mathbb{C})$ arbitrary.
>1.  $[u \star v]_{k}^{n,p} \in \mathcal{V}_{n,p}(\mathbb{C})$
>2. The discrete convolution is commutative $[u \star v]_{k}^{n,p} = [v \star u]_{k}^{n,p}$
>3. $\mathcal{F}_{n}\Big[[u \star v]_{k}^{n,p}\Big] = \mathcal{F}_{n}[u]\mathcal{F}_{n}[v]$
>
>>[!proof]-
>>1. To show that the [[#^4c1849|discrete convolution]] maps into the space of [[#^4780e3|periodic grid functions]] we have to show that the mapping preserves periodicity.
>>$$\begin{align}
>> [u \star v]_{k+p}^{n,p} &= \frac{1}{n}\sum_{j=0}^{n-1}u_{k+p-j}v_{j}  \\
>> &= \frac{1}{n}\sum_{j=0}^{n-1}u_{k-j}v_{j} \tag{1}\\
>> &= [u \star v]_{k}^{n,p}
>>\end{align}$$
>>where we used in equation $(1)$ that $u_{k}\in \mathcal{V}_{n,p}$ is periodic by [[#^4780e3|definition]]. $$\tag*{$\checkmark$}$$ 
>>2. First we define
>>$$\begin{align}
>> j' = k-j \iff j = k-j' 
>>\end{align}$$
>> We substitute and get
>>$$\begin{align}
>> [u \star v]_{k}^{n,p} &= \sum_{j=0}^{n-1}u_{k-j}v_{j} \\
>>  &= \sum_{j'=0}^{n-1}u_{k}v_{k-j'} \\
>> &= [v \star u]_{k}^{n,p} \tag*{$\checkmark$}
>>\end{align}$$
>>3. Let $m \in \mathbb{Z}$ be arbitrary $$\begin{align}
>> \mathcal{F}_{n}\Big[[u \star v]_{k}^{n,p}\Big]_{m} &= \frac{1}{n}\sum_{k=0}^{n-1}[u \star v]_{k}^{n,p} \exp\left( -2\pi i \frac{km}{n} \right) \\
>> &= \frac{1}{n}\sum_{k=0}^{n-1} \frac{1}{n}\sum_{j=0}^{n-1} u_{k-j}v_{j} \exp\left( -2\pi i \frac{km}{n} \right) \\
>> &= \frac{1}{n^2}\sum_{j=0}^{n-1}v_{j}\sum_{k=0}^{n-1}u_{k-j} \exp\left( -2\pi i \frac{km}{n} \right) \\
>>\end{align}$$
>>We make a change of variable, i.e. 
>>$$l = k-j \iff k = l+j$$
>>We substitute and continue 
>>$$\begin{align}
>> \phantom{\mathcal{F}_{n}\Big[[u \star v]_{k}^{n,p}\Big]_{m}} &= \frac{1}{n^2}\sum_{j=0}^{n-1}v_{j}\sum_{l=0}^{n-1}u_{l} \exp\left( -2\pi i \frac{(l+j)m}{n} \right)  \\
>> &= \frac{1}{n}\sum_{j=0}^{n-1} v_{j} \exp\left( -2\pi i \frac{jm}{n} \right)  \frac{1}{n}\sum_{l=0}^{n-1}u_{l} \exp\left( -2\pi i \frac{lm}{n} \right)  \\
>> &= \mathcal{F}_{n}[v]_{m} \mathcal{F}_{n}[u]_{m} \tag*{$\checkmark$}
>>\end{align}$$
>>
>>This establishes the properties. $$\tag*{$\square$}$$

>[!def] Definition Singular Periodic Grid Delta Function ([[../../../PDFs/salgado2022.pdf#page=378|Source]])
>Let $n \in \mathbb{N}$. The **singular periodic grid delta function**, denoted $\widetilde{\delta}^{n,p} \in \mathcal{V}_{n,c}(\mathbb{C})$, is defined via
>$$\widetilde{\delta}^{n,p} = n \delta^{n,p}$$

>[!lemma] Proposition Convolution with Singular Periodic Grid Delta Functions ([[../../../PDFs/salgado2022.pdf#page=378|Source]])
> Let $n \in \mathbb{N}$ and $u \in \mathcal{V}_{n,p}(\mathbb{C})$ arbitrary.
> Then $$[u \star \widetilde{\delta}^{n,p}]^{n,p}=u$$
>>[!proof]-
>>$\forall k \in \mathbb{Z}$
>>$$\begin{align}
>> [u \star \widetilde{\delta}^{n,p}]_{k}^{n,p} &= \frac{1}{n}\sum_{j=0}^{n-1}u_{k-j}n\delta_{j}^{n,p} \\
>> &= u_{k} \tag*{$\square$}
>>\end{align}$$

>[!def] Definition Periodic Grid Projection Operator ([[../../../PDFs/salgado2022.pdf#page=378|Source]])
>Let $n \in \mathbb{N}$. The **periodic grid projection operator** $$\mathcal{G}_{n,p}[f]: C_{p}(0,1; \mathbb{C})\to \mathcal{V}_{n,p}(\mathbb{C})$$ is defined as follows: $\forall f\in C_{p}(0,1;\mathbb{C}), \mathcal{G}_{n,p}[f] \in \mathcal{V}_{n,p}(\mathbb{C})$ is the grid function
>$$\mathcal{G}_{n,p}[f]_{j}= f\left( \frac{j}{n} \right) \tag*{$\forall j \in \mathbb{Z}$}$$

^4e828d

>[!def] Definition DFT of Continuous Functions ([[../../../PDFs/salgado2022.pdf#page=378|Source]])
>Let $n \in \mathbb{N}$ and $f \in C_{p}(0,1;\mathbb{C})$. For $j \in \mathbb{Z}$, the numbers
>$$\begin{align}
> \widehat{f}_{n,j} &= \frac{1}{n}\sum_{l=0}^{n-1} \mathcal{G}_{n,p}[f]_{l}\exp\left( -2\pi i \frac{jl}{n} \right) \\
> &=\frac{1}{n}\sum_{l=0}^{n-1} f\left( \frac{l}{n} \right)\exp\left( -2\pi i \frac{jl}{n} \right)
>\end{align}$$
>are called the **discrete Fourier coefficients of** $f$. The grid function
>$$\mathcal{F}_{n}\Big[\mathcal{G}_{n,p}[f]\Big] \in \mathcal{V}_{n,p}(\mathbb{C})$$
>is called the **Discrete Fourier Transform** of $f$.

^e44f1c

## Existence and Uniqueness of the Interpolant

>[!theorem] Theorem Existence and Uniqueness of the Interpolant ([[../../../PDFs/salgado2022.pdf#page=379|Source]])
>Let $f \in C_{p}(0,1;\mathbb{C})$ and $n \in \mathbb{N}$. Suppose that
>$$\begin{align}
> X&= \{ x_{j} \}_{j=0}^{n-1} \\
> x_{j}&= \frac{j}{n} \tag*{$j \in \{ 0,\dots,n-1 \}$}
>\end{align}$$
>is a uniformly spaced nodal set. Let $K= \left\lceil  \frac{n}{2}  \right\rceil$. For any $n \in \mathbb{N}$ there exists a unique [[#^ddb0ce|trigonometric polynomial]] $q \in \mathbb{T}_{K}$ which interpolates $f$ at the nodes $X$. The [[#^ddb0ce|trigonometric polynomial]] has the form
>
>If $n$ is odd:
>$$q(x) = \sum_{j=-K}^K c_{j} \exp(2\pi i j x)$$ 
>If $n$ is even:
>$$\begin{align}
>q(x) &=\frac{c_{k}}{2}(\exp(2\pi iKx) +\exp(-2\pi iKx)) + \sum_{j=-K+1}^{K-1} c_{j} \exp(2\pi ijx)  \\
> &= \sum_{j=-K+1}^{K}c_{j}\exp(2\pi ijx)
>\end{align}$$
>>[!proof]-
>> We make use of the [[#^4e828d|periodic grid projection operator]] and set
>> $$F = \mathcal{G}_{n,p}[f] \in \mathcal{V}_{n,p}(\mathbb{C})$$
>> Therefore, by definition
>> $$F_{l}=f\left(x_{l}\right)=f\left( \frac{l}{n} \right)$$
>> If $n$ is odd, we have
>> $$F_{l}=q(x_{l})= \sum_{j=-K}^K c_{j} \exp(2\pi ijx_{l}) \tag*{$\forall l \in \{ 0,\dots,n-1 \}$}$$
>> If $n$ is even, we have
>> $$\begin{align}
>> F_{l} = q(x_{l}) &= \frac{c_{k}}{2}(\exp(2\pi iKx_{l}) +\exp(-2\pi iKx_{l})) + \sum_{j=-K+1}^{K-1} c_{j} \exp(2\pi ijx_{l})  \\
>> &= c_{k} \exp(2\pi i K x_{l} )+ \sum_{j=-K+1}^{K-1} c_{j} \exp(2\pi ijx_{l}) \tag{1} \\
>> &=  \sum_{j=-K+1}^{K} c_{j} \exp(2\pi ijx_{l})
>>\end{align}$$
>> where in $(1)$ we made use of the fact that $\exp(2\pi iKx_{l}) = \exp(-2\pi iKx_{l})$ because $K$ is a multiple of $n$. 
>> 
>> Now we will view $c_{j}$ as discrete values from a [[#^4780e3|grid function]] and extend it to be periodic, i.e.
>> $$c \in V_{n,p}\in(\mathbb{C})$$
>> This allows us to shift the summation indices for
>> $$\begin{align}
>> K &= 2n + 1 \tag{$n$ is odd} \\
>> K &= 2n  \tag{$n$ is even} \\
>>\end{align}$$
>>and can therefore rewrite
>>$$f\left( \frac{l}{n} \right) = F_{l} = \sum_{j=0}^{n-1}c_{j}\exp(2\pi ijx_{kl}) \tag*{$l \in \{ 0,\dots,n-1 \}$}$$
>>Using the [[#^db3d1d|definition of the DFT]] and using its [[#^7594db|bijectivity property]] we can determine $c_{j}$ with
>>$$c_{j} = \widehat{f}_{n,j}=\frac{1}{n}\sum_{l=0}^{n-1} f\left( \frac{l}{n} \right) \exp(-2\pi i j x_{l})\tag*{$j \in \{ 0,\dots,n-1 \}$}$$
>>$$\tag*{$\square$}$$
>
>>[!algo] Python Implementation
>>```python
>>import numpy as np
>>
>>def trig_interpolation(Y_hat, delta_x, depth=1000):
>>    """
>>    Creates a trigonometric polynomial given, that Y_hat includes the *discrete Fourier coefficients*.
>>    
>>    Parameters
>>    ----------
>>    Y_hat: List[float]
>>        includes the Fourier coefficients with the following structure
>>        
>>        generally:
>>            Y_hat[0]      - zero frequency term
>>            Y_hat[1:n/2]  - positive frequency terms
>>            Y_hat[n/2+1:] - negative frequency terms
>>            
>>        if `n` is odd:
>>            Y_hat[n/2] - represents the Nyquist frequency, which is half of the upper frequency range
>>            
>>    delta_x: float
>>        describes the equidistant spacing distance
>>        
>>    depth: int
>>        describes the resolution on how the interpolation produces values
>>        
>>    Returns
>>    -------
>>    x_int: numpy.array
>>        x values with size depth
>>        
>>    y_intp: numpy.aray
>>        y values for the trigonometric polynomial q(x), such that for any x_i in x_int we have y_i = q(x_i)
>>            
>>    """
>>    n = len(Y_hat)
>>    x_range = n * delta_x
>>
>>    get_summand = lambda c_j, l, x: c_j * np.exp(2 * np.pi * 1j * l * x / x_range )
>>
>>    x_intp = [(i / depth) * x_range for i in range(depth)]                     
>>    y_intp = []
>>    K = n // 2                                                       # Fix K for the odd/even cases
>>    if n%2==0:
>>        # np.roll rearranges array such that positives are first and negatives concluding
>>        Y_hat = np.roll( Y_hat, K - 1 )                              
>>        for x in x_intp:
>>            y_intp.append(sum([get_summand(c_j,l,x) for l,c_j in zip(range(-K+1,K+1), Y_hat)]))
>>    else:
>>        # np.roll rearranges array such that zero frequency is first, positives following and negatives concluding
>>        Y_hat = np.roll( Y_hat, K )                                  # Rotate
>>        for x in x_intp:
>>            y_intp.append(sum([get_summand(c_j,l,x) for l,c_j in zip(range(-K,K+1), Y_hat)]))
>>    return x_intp, y_intp


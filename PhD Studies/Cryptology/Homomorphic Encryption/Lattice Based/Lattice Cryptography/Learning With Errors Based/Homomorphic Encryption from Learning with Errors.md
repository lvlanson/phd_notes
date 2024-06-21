
---
### Introduction to the Algorithm

>[!def] Definition Ciphertext ([[../../../../../../PDFs/gentry2013.pdf#page=4|Source]])
>Let $\mathbf{C} \in \mathbb{Z}_{q}^{N\times N}$ where $q$ is the modulus and $N$ the dimensionality parameter. The matrix $\mathbf{C}$ is the ciphertext with $c_{ij}$ being "small", i.e. $c_{ij}\ll q$.

>[!def] Definition Secret Key ([[../../../../../../PDFs/gentry2013.pdf#page=4|Source]])
>The secret key is the vector $\mathbf{v} \in \mathbb{Z}_{q}^N$ where at least one $v_{i} \in \mathbb{Z}$ is "big".

>[!def] Definition Plaintext ([[../../../../../../PDFs/gentry2013.pdf#page=4|Source]])
>The plaintext is the scalar $\mu \in \mathbb{Z}_{q}$ which should be a "small" integer

>[!def] Defintion Encryption ([[../../../../../../PDFs/gentry2013.pdf#page=4|Source]])
>The encryption is a function for some plaintext $\mu$ which solves the following expression
>$$\text{Enc}(\mu): \mathbf{C}\cdot \mathbf{v} = \mu \cdot \mathbf{v}  +\mathbf{e}$$
>where $\mathbf{e} \in \mathbb{Z}^N_{q}$ being a "small" error vector

^541d3f

>[!def] Definition Decryption ([[../../../../../../PDFs/gentry2013.pdf#page=4|Source]])
> We calculate 
> $$x \leftarrow \langle \, \mathbf{c_{i}} \,,\, \mathbf{v} \,\rangle = \mu \cdot v_{i}+e_{i}$$
> with $\mathbf{c}_{i}$ being the $i$-th row vector of $\mathbf{C}$ and we output
> $$\mu =\left\lfloor \frac{x}{v_{i}} \right\rceil $$

>[!remark] Remark ([[../../../../../../PDFs/gentry2013.pdf#page=4|Source]])
>The secret key $\mathbf{v}$ is an **approximate eigenvector** of $\mathbf{C}$ and the message $\mu$ acts as **eigenvalue** with respect to $\mathbf{C}\mathbf{v}$.

>[!property] Property Homomorphic Operations ([[../../../../../../PDFs/gentry2013.pdf#page=5|Source]])
> Denote for two different plaintexts $\mu_{1}, \mu_{2} \in \mathbb{Z}_{q}$
> $$\begin{align}
> \text{Enc}(\mu_{1}) &= \mathbf{C}_{1} \\
> \text{Enc}(\mu_{2}) &= \mathbf{C}_{2}
>\end{align}$$
> <u> Addition:</u>
> 
>Denote $\mathbf{C}^+ =\mathbf{C}_{1}+\mathbf{C}_{2}$. For [[#^541d3f|encryption]] we get
>$$\begin{align}
> \mathbf{C}^+ \mathbf{v} = (\mathbf{C}_{1} +\mathbf{C}_{2})\cdot \mathbf{v} &= (\mu_{1}\mathbf{v}+\mathbf{e}_{1})+(\mu_{2}\mathbf{v}+\mathbf{e_{2}}) \\
> &=\underbrace{ \mu_{1}\mu_{2} }_{ =\mu^+ }\cdot \mathbf{v} + \underbrace{ \mathbf{e}_{1}+\mathbf{e}_{2} }_{ =\mathbf{e}^+ } \\
> &= \mu^+\mathbf{v}+\mathbf{e}^+
>\end{align}$$
>
><u>Multiplication:</u>
>
>Denote $\mathbf{C}^\times = \mathbf{C_{1}} \cdot \mathbf{C_{2}}$. For [[#^541d3f|encryption]] we get
>$$\begin{align}
> \mathbf{C}^\times \mathbf{v} &= (\mathbf{C}_{1} \cdot \mathbf{C}_{2})\cdot \mathbf{v}  \\
> &= \mathbf{C}_{1} \cdot(\underbrace{ \mathbf{C}_{2} \cdot \mathbf{v} }_{ =\mu_{2}\mathbf{v} +\mathbf{e}_{2} }) \\
> &=\mathbf{C_{1}} \cdot (\mu_{2}\mathbf{v}+\mathbf{e}_{2}) \\
> &= \mu_{2}\underbrace{ \mathbf{C}_{1}\mathbf{v} }_{ =\mu_{1}\mathbf{v}+\mathbf{e}_{1} }+ \mathbf{C}_{1}\mathbf{e}_{2} \\
> &= \mu_{2}(\mu_{1}\mathbf{v}+\mathbf{e}_{1})+\mathbf{C}_{1}\mathbf{e}_{2} \\
> &= \underbrace{ \mu_{1}\mu_{2} }_{ = \mu^\times}\mathbf{v} + \underbrace{ \underbrace{ \mu_{2} \mathbf{e}_{1} }_{ \substack{\text{small}\\\text{term}} } +\underbrace{ \mathbf{C}_{1}\mathbf{e}_{2} }_{ \substack{\text{small}\\\text{term}}  } }_{ =\mathbf{e}^\times } \\
> &=\mu^\times \mathbf{v} + \mathbf{e}^\times
>\end{align}$$
>>[!remark]
>>The terms $\mu_{2}\mathbf{e}_{1}$ and $\mathbf{C}_{1}\mathbf{e}_{2}$ are likely to be small by construction, since $\mu_{2}, \mathbf{C}_{1}, \mathbf{e}_{1}$ and $\mathbf{e}_{2}$ are small, therefore it can be considered as the **error term** of the homomorphic multiplication.

>[!remark] Remark on Security
> - the approximation of the eigenvector is the intrinsic security mechanism. The properties of the homomorphism would prevail in an exact version, but lose its security property.
> - the choice of terms like the error being "small" is the condition for the homomorphism to hold
> - this mechanism is phrased **learning with errors (LWE)** 

>[!tip] Proposition on Error Bounds ([[../../../../../../PDFs/gentry2013.pdf#page=6|Source]])
> Let parameters $\mathbf{C}_{1}, \mathbf{C}_{2} \in \mathbb{Z}_{q}^{N\times N}$ be at most $B$-Bounded, i.e.
> $$\begin{align}
> \lvert \mu_{i} \rvert &\leq B \\
> \lvert\lvert \mathbf{c}_{i} \rvert\rvert & \leq B \\
> \lvert\lvert \mathbf{e}_{i} \rvert\rvert & \leq B   
>\end{align}$$
>Then we can bound the resulting error from circuit evaluations by
>
><u> Addition:</u>
>$$\mathbf{C}_{1}+\mathbf{C}_{2} = \mathbf{C}^+ \implies \mathbf{C}^+ \text{ is } 2B\text{-bounded} $$
>
><u> Multiplication:</u>
>$$\mathbf{C}_{1} \cdot \mathbf{C}_{2} = \mathbf{C}^\times \implies \mathbf{C}^\times \text{ is } (N+1)B^2\text{-bounded}$$

---
### Preliminaries

>[!def] Definition Learning from Parity with Error 
>Let $n \geq 1$ and $0<\varepsilon< \frac{1}{2}$, find an unknown $\mathbf{s} \in \mathbb{Z}_{2}^n$ such that the list of equations with errors
>$$\begin{align}
> \left\langle \mathbf{s}\,,\,\mathbf{a}_{1} \right\rangle &\approx_{\varepsilon} b_{1} \;\;(\text{mod } 2) \\
> \left\langle \mathbf{s}\,,\,\mathbf{a}_{2} \right\rangle &\approx_{\varepsilon} b_{2} \;\;(\text{mod } 2) \\
> &\vdots
>\end{align}$$
>where the $\mathbf{a}_{i}$s are chosen independently from the uniform distribution on $\mathbb{Z}_{2}^n$ and each equation is correct independently with probability $1-\varepsilon$
>
>>[!remark]- Remark on the Term Parity
>>Parity is a function on the bitstream of a string $s = (0+1)^n$ of the following form
>>$$\text{parity}(s)=\begin{cases}
>>0 & \text{ if number of } 1\text{'s is even} \\
>>1 & \text{ if number of }1\text{'s is odd}
>>\end{cases}$$
>
>>[!remark]- Remark on Hardness of the Problem
>>There is no algorithm which solves this problem in $\text{poly}(n)$ time even for small $\varepsilon$.
>
>>[!example]- Algorithmic Example (Useful)
>>1. Let $\mathbf{s} \in \mathbb{Z}_{2}^n$ be a randomly chosen secret by Alice. 
>>2. A request algorithm is introduced:
>>	1. Alice chooses some $\mathbf{a} \in \mathbb{Z}_{2}^n$
>>	2. Alice generates a noisy parity response $$b=\left\langle \mathbf{s}\,,\, \mathbf{a} \right\rangle + \begin{cases}
>> 0 &\text{with probability } 1-\varepsilon \\
>> 1 &\text{with probability } \varepsilon
>> \end{cases}$$
>> 	where $\varepsilon$ represents the noise or error
>> 	1. Alice sends $\mathbf{a}$ and $b$ to Bob
>>3. Bob's goal is to determine the secret vector $\mathbf{s}$ by querying Alice multiple times using the request algorithm. Each query provides a new pair $(\mathbf{a},b)$.


>[!def] Definition Learning with Errors (LWE) ([[../../../../../../PDFs/gentry2013.pdf#page=8|Source]])
>For security parameter $\lambda$, let 
>- $n=n(\lambda)$ be an integer dimension
>- $q=q(\lambda)\leq 2$ be an integer
>- $\chi=\chi(\lambda)$ be a distribution over $\mathbb{Z}$
>
>The **LWE$_{n,q,\chi}$** problem *is to distinguish* the following two distributions:
>1. One samples $(\mathbf{a}_{i}, b_{i})$ uniformly from $\mathbb{Z}_{q}^{n+1}$, i.e. $\mathbf{a}_{i} \in \mathbb{Z}_{q}^n$ and $b_{i} \in \mathbb{Z}_{q}$
>2. One first draws $\mathbf{s} \leftarrow \mathbb{Z}^n_{q}$ uniformly and then samples $(\mathbf{a}_{i}, b_{i}) \in \mathbb{Z}^{n+1}_{q}$, i.e. $\mathbf{a}_{i} \in \mathbb{Z}_{q}^n$ and $b_{i} \in \mathbb{Z}_{q}$, by 
>	- sampling $\mathbf{a}_{i} \leftarrow \mathbb{Z}_{q}^n$ uniformly
>	- $e_{i} \leftarrow \chi$
>	- setting $b_{i} = \left\langle \mathbf{a}_{i}\,,\, \mathbf{s} \right\rangle + e_{i}$
>
>The LWE$_{n,q,\chi}$ assumption is that the LWE$_{n,q,\chi}$ problem is infeasible.

>[!remark]
>>[!remark]- Remark on LWE Generally ([[../../../../../../PDFs/sabani2024.pdf#page=13|Source]])
>> The LWE problem asks to solve the discrete linear equation
>> $$\mathbf{b} =\mathbf{A}\mathbf{s}+ \mathbf{e} \text{ mod }q$$
>> given $(\mathbf{A},\mathbf{b})$ and finding the secret vector $\mathbf{s}$. The entries $e_{i} \in \mathbf{e}$ denote the discrete rounding error, such that
>> $$\begin{align}
>> \left\langle \mathbf{a}_{i}\,,\, \mathbf{s} \right\rangle \approx_{e_{i}} b_{i}
>>\end{align}$$ 
>
>>[!remark]- Remark on Security of LWE ([[../../../../../../PDFs/sabani2024.pdf#page=14|Source]])
>>The security of LWE is based on the hardness of **shortest integer problem (SIP)** for [[../Lattice Based/Lattice Cryptography/Elementary Definitions|lattices]].
>
>>[!remark]- Remark on Error $\mathbf{e}=\mathbf{0}$ ([[../../../../../../PDFs/regev2024.pdf#page=2|Source]])
>>If we consider $\mathbf{e}=\mathbf{0}$, then the problem collapses to the simple linear equation which can be solved by Gaussian elimination and can be solved for $\mathcal{O}(n)$ equations in $\text{poly}(n)$ time.
>>
>>Given $\mathbf{e}\neq \mathbf{0}$ the problem becomes untractable

>[!def] Definition Real Modulus ([[../../../../../../PDFs/regev2024.pdf#page=12|Source]])
>Let $x,y \in \mathbb{R}^+$
>$$x \text{ mod } y := x - \left\lfloor  \frac{x}{y}  \right\rfloor y $$

>[!def] Definition Closest Integer ([[../../../../../../PDFs/regev2024.pdf#page=12|Source]])
> Let $x \in \mathbb{R}$, the closest integer to $x$ is defined as
> $$\lfloor  x  \rceil \in \mathbb{Z} $$

>[!def] Definition Cyclic Group $\mathbb{Z}_{p}$ ([[../../../../../../PDFs/regev2024.pdf#page=12|Source]])
> The cyclic group $\mathbb{Z}_{p}$ with $p \in\mathbb{Z}$ over addition is given as
> $$\mathbb{Z}_{p} = \{ 0,1,\dots,p-1 \}$$

>[!def] Definition Negligible Functions ([[../../../../../../PDFs/regev2024.pdf#page=12|Source]])
>Let $n$ be some number. A function $f$ is called *negligible* if for any constant $c>0$
>$$\lim_{ n \to \infty } n^cf(n)=0 \qquad $$

>[!def] Definition Gaussian Function ([[../../../../../../PDFs/regev2024.pdf#page=13|Source]])
>Let $\mathbf{x} \in \mathbb{R}$ and the scaling factor $s>0$, the Gaussian function is given by
>$$\rho_{s}(\mathbf{x}):= \exp\left( -\pi \left\lvert \left\lvert  \frac{\mathbf{x}}{s}  \right\rvert \right\rvert^2   \right)$$
>
>>[!remark]
>>The normal distribution with mean $\mu=0$ and variance $\sigma^2$ as distribution on $\mathbb{R}$ is given by the density function
>>$$\frac{1}{\sqrt{ 2\pi }\sigma}\exp\left( -\frac{1}{2}\left( \frac{x}{\sigma} \right)^2 \right)$$ 

^cd948a

>[!def] Definition Probability Density Function based on the Gaussian Function ([[../../../../../../PDFs/regev2024.pdf#page=13|Source]])
>Note
>$$\int _{\mathbf{x}\in\mathbb{R}^n}\rho_{s}(\mathbf{x}) \, dx = s^n$$
>The $n$-dimensional Probability Density Function (PDF) is given by
>$$\nu_{s}:= \frac{\rho_{s}}{s^n}$$

>[!def] Definition Lattice Smoothed Gaussian ([[../../../../../../PDFs/regev2024.pdf#page=17|Source]])
>Let $L$ be an $n$-dimensional lattice and $\epsilon>0$. The smoothing parameter $n_{\epsilon}(L)$ with respect to lattice $L$ is the smallest $s$ such that
>$$\rho_{1/s}(L^*\setminus \{ \mathbf{0} \})\leq \epsilon$$
>
>>[!remark]
>> $p_{1/s}$ is a continuous and strictly decreasing function of $s$ and
>>  $$\begin{align}
>> \lim_{ s \to 0 } \rho_{1/s}(L^*\setminus \{ \mathbf{0} \})  &= \infty\\
>> \lim_{ s \to \infty } \rho_{1/s}(L^*\setminus \{ \mathbf{0} \})  &= 0\\
>>\end{align}$$

>[!def] Definition Discrete Gaussian Probability Distribution ([[../../../../../../PDFs/regev2024.pdf#page=14|Source]])
>Let $A$ be a countable set and $s>0$. The discrete Gaussian probability distribution $D_{A,s}$ is defined as
>$$\forall \mathbf{x} \in A, D_{A,s}(\mathbf{x}):= \frac{\rho_{s}(\mathbf{x})}{\rho_{s}(A)}$$
>where $\rho_{s}$ is the [[#^cd948a|Gaussian function]]
>>[!pic] Illustration ([[../../../../../../PDFs/regev2024.pdf#page=7|Source]])
>> ![[../../Figures/discrete_gaussian.png]]
---
### Encryption Scheme

>[!algo] Algorithm Key Generation $\text{KeyGen}$ ([[../../../../../../PDFs/gentry2013.pdf#page=10|Source 1]]), ([[../../../../../../PDFs/sabani2024.pdf#page=15|Source 2]]), ([[../../../../../../PDFs/regev2024.pdf#page=31|Source 3]])
>Let $\lambda, L \in \mathbb{Z}$ with $\lambda$ being the security parameter and $L$ being the circuit complexity parameter.
>1. $\text{Setup}(\lambda, L)$:
>	- lattice dimension parameter $n=n(\lambda,L)$
>	- choose a prime number $q \in \mathbb{Z}$ with $n^2\leq q\leq 2n^2$
>	- error distribution $\chi=\Psi_{\alpha(n)}$
>	- number of equations $m=(1+\epsilon)(n+1) \log q$ where $\epsilon>0$ is a smoothing parameter related to the Gaussian distribution and the dual lattice
>
>
>
>>[!remark] Remark on Notation
>> 1. Setup
>> 	- $q$ is chosen in a magnitude with respect to its binary representation, such that it complies with the predefined security $\lambda$ and circuit complexity $L$ constraints. The same can be said similarly for other parameters.
>> 	- the error distribution $\chi$ is usually chosen as some fitting discrete Gaussian ([[../../../../../../PDFs/sabani2024.pdf#page=3|Source 1 - Definition 3-6]], [[../../../../../../PDFs/sabani2024.pdf#page=14|Source 2 - Theorem 4]], [[../../../../../../PDFs/regev2024.pdf#page=6|Source 3]])
>> 	- security 

>[!remark]
>This algorithm is based on the *approximate eigenvector* method.

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
>>[!remark]
>>- $\mu$ represents the eigenvalue, while $\mathbf{v}$ is the approximate eigenvector and $\mathbf{e}$ some error sampled from some distribution $\chi$

^541d3f

>[!def] Definition Decryption ([[../../../../../../PDFs/gentry2013.pdf#page=4|Source]])
> We calculate 
> $$x \leftarrow \langle \, \mathbf{c_{i}} \,,\, \mathbf{v} \,\rangle = \mu \cdot v_{i}+e_{i}$$
> with $\mathbf{c}_{i}$ being the $i$-th row vector of $\mathbf{C}$ and we output
> $$\mu =\left\lfloor \frac{x}{v_{i}} \right\rceil $$
> 
>>[!remark] Remark
>>Let $x \in \mathbb{R}$, then $\left\lfloor x \right\rceil$ denotes the closest integer to $x$.

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

### Encryption Scheme

>[!algo] Algorithm Key Generation $\text{KeyGen}$ ([[../../../../../../PDFs/gentry2013.pdf#page=10|Source]])
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
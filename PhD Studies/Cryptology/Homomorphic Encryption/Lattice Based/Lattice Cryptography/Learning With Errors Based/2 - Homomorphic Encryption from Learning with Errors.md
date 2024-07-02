
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

>[!def] Definition Encryption ([[../../../../../../PDFs/gentry2013.pdf#page=4|Source]])
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

>[!def] Definition Algorithm Functions ([[../../../../../../PDFs/gentry2013.pdf|Source 1]], [[../../../../../../PDFs/brakerski2012.pdf#page=10|Source 2]])
>Let $l = \lfloor \log_{2} q \rfloor +1$
>1. **PowersOfTwo** 
>Let $\mathbf{b} \in \mathbb{Z}_{q}^n$ and $l \in \mathbb{Z}$, then $$\text{PowersOfTwo}(\mathbf{b}):=\Big(\mathbf{b}, 2 \cdot \mathbf{b}, \dots, 2^{l-1}\cdot \mathbf{b}\Big)$$
>
>2. **BitDecomp**
> For $\mathbf{a} \in \mathbb{Z}^n$ let $\mathbf{w}_{i}\in\{ 0,1 \}^n$ such that $$\mathbf{x}= \sum_{i=0}^{l-1} 2^i \cdot \mathbf{w}_{i} \;\;(\text{mod } q)$$
>and outputting the determined coefficients $\mathbf{w}_{i}$ with $0 \leq i \leq l-1$
>$$\text{BitDecomp}(\mathbf{a}) := (\mathbf{w}_{0}, \dots, \mathbf{w}_{l-1})$$
>
>
>1. **Flatten**  
> Let $\mathbf{b} \in \mathbb{Z}^n$, then $$\text{Flatten}(\mathbf{b}):= \text{BitDecomp}\Big(\text{BitDecomp}^{-1}(\mathbf{b})\Big)$$
>>[!lemma]
>>Let $q \in \mathbb{Z}$ and $\mathbf{x}, \mathbf{y} \in \mathbb{Z}^n$, it holds that
>>$$\left\langle \mathbf{x}\,,\,\mathbf{y} \right\rangle = \left\langle \text{BitDecomp}(\mathbf{x})\,,\, \text{PowersOfTwo}(\mathbf{y}) \right\rangle \;\;(\text{mod } q)  $$
>>>[!proof]
>>>$$\begin{alignat}{2}
>>> \left\langle \mathbf{x}\,,\,\mathbf{y} \right\rangle &= \sum_{i=0}^n x_{i}y_{i} &&\;\;(\text{mod } q) \\
>>> &= \sum_{i=0}^n \sum_{j=0}^l (w_{j,i} \cdot 2^j) y_{i} &&\;\;(\text{mod } q) \\
>>> &=\sum_{i=0}^n \sum_{j=0}^l w_{j,i} (2^j \cdot y_{i}) &&\;\;(\text{mod } q) \\
>>> &=\sum_{j=0}^l \underbrace{ \mathbf{w}_{j} }_{ \in \mathbb{Z}^n } (2^j \underbrace{ \mathbf{y} }_{  \in \mathbb{Z}^n }) &&\;\;(\text{mod } q) \\
>>> &=\sum_{j=0}^l \text{BitDecomp}(\mathbf{x}^T[j]) \cdot \text{PowersOfTwo}(\mathbf{y}_{j}) &&\;\;(\text{mod } q) \\
>>> &= \left\langle \text{BitDecomp}(\mathbf{x})\,,\, \text{PowersOfTwo}(\mathbf{y}) \right\rangle &&\;\;(\text{mod } q)
>>>\end{alignat}$$


>[!algo] Algorithm Key Generation $\text{KeyGen}$ ([[../../../../../../PDFs/gentry2013.pdf#page=10|Source]])
>Let $\lambda, L \in \mathbb{Z}$ with $\lambda$ being the security parameter and $L$ being the circuit complexity parameter.
>1. $\text{Setup}(\lambda, L)$: 
>	- lattice dimension parameter: $n=n(\lambda,L)$
>	- choose a prime number: $q \in \mathbb{Z}$ with $n^2\leq q\leq 2n^2$
>	- error distribution:  $\chi=\Psi_{\alpha(n)}$
>	- number of equations $m=(1+\epsilon)(n+1) \log q$ where $\epsilon>0$ is a smoothing parameter related to the Gaussian distribution and the dual lattice, where $m$ is rounded to the next integer
>
>		-> output paramaters $\text{params} = (n,q,\chi,m)$
>	- denote $l = \lfloor \log q \rfloor + 1$
>	- denote $N = (n+1) \cdot l$
>
>1. $\text{SecretKeyGen}(\text{params})$:
> 	- sample uniformly: $\mathbf{t} \leftarrow \mathbb{Z}_{q}^n$
> 	
> 		-> output secret key $\text{sk} = \mathbf{s} \leftarrow (1,-t_{1},\dots,t_{n})$
> 
>3. $\text{PublicKeyGen}(\text{params,sk})$:
>	- sample uniformly: $\mathbf{B} \leftarrow \mathbb{Z}_{q}^{m \times n}$
>	- sample: $\mathbf{e} \leftarrow \chi^m$
>	- set: $\mathbf{b}=\mathbf{B}\cdot \mathbf{t}+\mathbf{e}$
>	- set: $A=\text{concatenate}(\mathbf{b}, \mathbf{B}) \in \mathbb{Z}^{m+1\times n}$
>	- note: $\mathbf{A} \cdot \mathbf{s}  = \mathbf{e}$
>
>		-> output public key $\text{pk} = \mathbf{A}$
>
>Output: $\text{KeyGen} \to (\text{pk}=\mathbf{A}, \text{sk} = \mathbf{s})$
>>[!proof]- Proof $\mathbf{A} \cdot \mathbf{s} = \mathbf{e}$
>>$$\begin{align}
>> \mathbf{A} \cdot \mathbf{s} &= \underbrace{ [\mathbf{b}, \mathbf{B}] }_{ =\mathbf{A} } \cdot (1, -t_{1}, \dots, t_{n}) \\
>> &= [\underbrace{ (\mathbf{B}\cdot \mathbf{t}+\mathbf{e}) }_{ =\mathbf{b} }, \mathbf{B}] \cdot (1, -t_{1}, \dots, t_{n})  \\
>> &= (\mathbf{B} \cdot \mathbf{t} +\mathbf{e}) \cdot 1 - \mathbf{B}[1]t_{1} -\ldots- \mathbf{B}[n]t_{n} \\
>> &= \mathbf{B} \cdot \mathbf{t}  + \Big(- \mathbf{B}[1]t_{1} -\ldots- \mathbf{B}[n]t_{n}\Big) +\mathbf{e} \\
>> &= \Big(\mathbf{B[1]} t_{1} +\ldots+\mathbf{B}[n]t_{n}\Big)+\Big(-\mathbf{B}[1]t_{1} -\ldots- \mathbf{B}[n]t_{n}\Big) +\mathbf{e}  \\
>> &= \mathbf{e} 
>>\end{align}$$
>>where $\mathbf{D}[k]$ is the $k$-th column vector of matrix $\mathbf{D}$ and $[\mathbf{b},\mathbf{B}]$ is the concatenation of vector $\mathbf{b} \in \mathbb{Z}_{q}^n$ and matrix $\mathbf{B} \in \mathbb{Z}_{q}^{m \times n}$
>
>>[!remark]- Remark on Notation
>> 1. $\text{Setup}$
>> 	- the parameters are chosen in their binary representation, such that they comply with the predefined security $\lambda$ and circuit complexity $L$ constraints. 
>> 	- the error distribution $\chi$ is usually chosen as some fitted discrete Gaussian ([[../../../../../../PDFs/sabani2024.pdf#page=3|Source 1 - Definition 3-6]], [[../../../../../../PDFs/sabani2024.pdf#page=14|Source 2 - Theorem 4]], [[../../../../../../PDFs/regev2024.pdf#page=6|Source 3]])
>> 
>> <div> </div>
>> 
>> 3. $\text{PublicKeyGen}$
>> 	- $\text{concatenate}(\mathbf{A},\mathbf{B})$ for matrices (vectors) $\mathbf{A} \in \mathbb{Z}^{\alpha \times k  }$ and $\mathbf{B} \in \mathbb{Z}^{\beta \times k}$ creates a matrix $\mathbf{C} \in \mathbb{Z}^{ \alpha+\beta \times k}$ such that for entries $\mathbf{a}_{i} \in \mathbf{A}$ and $\mathbf{b}_{i} \in \mathbf{B}$ we get $\mathbf{C} = [\mathbf{a}_{1}, \dots, \mathbf{a}_{\alpha}, \mathbf{b}_{1}, \dots, \mathbf{b}_{\beta}]$ 
>> 	
>
>>[!remark]- Remark on Plaintext Space
>>This setup is given under the assumption that each message $\mu_{i} \in \{ 0,1 \}$. The author gives additional procedural steps to consider messages with a wider range of values

>[!algo] Algorithm Encryption and Decryption ([[../../../../../../PDFs/gentry2013.pdf#page=10|Source]])
>4. $\text{Enc}(\text{params, pk})$:
>	- $\mu \in \mathbb{Z}_{q}$ denotes the plaintext
>	- sample uniformly $\mathbf{R} \leftarrow \{ 0,1 \}^{N \times m}$
>	- output:
>	$$C = \text{Flatten}\Big(\mu \cdot \mathbf{I}_{N} + \text{BitDecomp}(\mathbf{R}\cdot \mathbf{A})\Big) \in \mathbb{Z}_{q}^{N \times N}$$

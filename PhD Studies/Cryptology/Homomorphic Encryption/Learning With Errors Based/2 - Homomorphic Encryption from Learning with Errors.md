
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
> 
>The encryption is a function for some plaintext $\mu$ which solves the following expression
>$$\text{Enc}(\mu): \mathbf{C}\cdot \mathbf{v} = \mu \cdot \mathbf{v}  +\mathbf{e}$$
>where $\mathbf{e} \in \mathbb{Z}^N_{q}$ being a "small" error vector
>
>Parameter:
> - input: $\mu$ - plaintext
> - output: $C$ - ciphertext
>
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
>Let $l =  \lceil \log_{2} q\rceil -1$
>1. **PowersOfTwo** 
>Let $\mathbf{b} \in \mathbb{Z}_{q}^n$ and $l \in \mathbb{Z}$, then $$\begin{align}
> \text{PowersOfTwo}(\mathbf{b}):&=\Big(\mathbf{b}, 2 \cdot \mathbf{b}, \dots, 2^{l-1}\cdot \mathbf{b}\Big) \in \mathbb{Z}_{q}^{l\times n} \tag{Matrix Notation} \\
> \text{PowersOfTwo}(\mathbf{b}):&=\Big(b_{1},2b_{1}, \dots 2^{l-1}b_{1},\dots, b_{k},2b_{k},\dots 2^{l-1}b_{k}, \dots, 2^{l-1}b_{n}\Big) \in \mathbb{Z}_{q}^{l \cdot n} \tag{Vector Notation}
>\end{align}$$ 
>
>2. **BitDecomp**
> For $\mathbf{a} \in \mathbb{Z}^n$ let $\mathbf{w}_{i}\in\{ 0,1 \}^n$ such that $$\mathbf{a}= \sum_{i=0}^{l-1} 2^i \cdot \mathbf{w}_{i} \;\;(\text{mod } q)$$
>and outputting the determined coefficients $\mathbf{w}_{i}$ with $0 \leq i \leq l-1$
>$$\text{BitDecomp}(\mathbf{a}) := (\mathbf{w}_{0}, \dots, \mathbf{w}_{l-1})$$
>
>
>1. **Flatten**  
> Let $\mathbf{b} \in \mathbb{Z}^n$, then $$\text{Flatten}(\mathbf{b}):= \text{BitDecomp}\Big(\text{BitDecomp}^{-1}(\mathbf{b})\Big)$$
> 
> >[!remark]- Remark on $\text{Flatten}$ on Matrices
> >If $\text{Flatten}$ receives a matrix $\mathbf{C} \in \mathbb{Z}^{m \times n}$ we get
> >$$\text{Flatten}(\mathbf{C}) = \text{Concat}(\text{Flatten}(\mathbf{c}_{1}), \dots, \text{Flatten}(\mathbf{c}_{m}))$$ where $\mathbf{c}_{i} \in \mathbb{Z}^n$ are the column vectors of $\mathbf{C}$.
> 
>>[!remark]- Remark on the meaning of $\text{Flatten}$
>>Note, that if we have some **binary depth** $l$ and some modulus $q$, then for some $\mathbf{b} \in \mathbb{Z}^n$ with at least one coefficient $b_{i}\geq q$
>>$$\text{Flatten}(\mathbf{b}) \neq \mathbf{b}$$
>>Flatten **normalizes the binary representation** given we consider $\mathbf{b}$ as a binary representation with coefficients from $\mathbb{Z}$ over modulus $q$.
>>
>>>[!example]- Example for Binary Normalization of $\text{Flatten}$
>>>Let $$\mathbf{a} = \begin{pmatrix}
>>> 1  \\ 2 \\ 3 \\ 4 \\ 5 \\ 6
>>>\end{pmatrix} \in \mathbb{Z}^6_{8}$$
>>>with $$\begin{align}
>>> l&=\lceil \log_{2}8 \rceil -1 =3 \\
>>> q &= 8 \\
>>> n &= 6 \\
>>> k &= 2
>>>\end{align}$$
>>> For easier comprehensibility we rewrite $\mathbf{a} \in \mathbb{Z}^n$ as the matrix $\mathbf{a} \in \mathbb{Z}^{l \times k}$, i.e.
>>> $$\mathbf{a} = \begin{pmatrix}
 1 & 2 & 3  \\
>>> 4 & 5 & 6
>>>\end{pmatrix}$$
>>> Applying $\text{BitDecomp}^{-1}$ on $\mathbf{a}$ gives
>>> $$\begin{alignat}{2}
>>> \text{BitDecomp}^{-1}(\mathbf{a}) &= \begin{pmatrix}
>>>1 \cdot 2^0 &+& 2 \cdot 2^1 &+& 3 \cdot 2^2 \\
>>>4 \cdot 2^0 &+& 5 \cdot 2^1 &+& 6 \cdot 2^2 
>>>\end{pmatrix} \;\;&&(\text{mod } 8) \\
>>> &= \begin{pmatrix}
>>> 7  \\
>>> 38
>>>\end{pmatrix} \;\;&&(\text{mod } 8) \\
>>> &= \begin{pmatrix}
>>> 7  \\
>>> 6
>>>\end{pmatrix} = \mathbf{a}' \;\;&&(\text{mod } 8)
>>>\end{alignat}$$
>>> Passing the resulting vector to $\text{BitDecomp}$ gives the binary representation of the coefficients of the given vector
>>> $$\begin{align}
>>> \text{BitDecomp}(\mathbf{a}') &= \begin{pmatrix}
>>> 1 & 1 & 1 \\
>>> 1 & 1 & 0
>>>\end{pmatrix}
>>>\end{align}$$
>>>We can rearrange this vector back from $l \times k$ to $n$ dimensionality, and have
>>>$$\text{Flatten}(\mathbf{a}) = \begin{pmatrix}
>>> 1 \\ 1 \\ 1 \\ 1 \\ 1 \\ 0
>>>\end{pmatrix}$$
>>
>>**Flatten helps to bound homomorphic multiplication results**

>[!lemma]
>Let $q \in \mathbb{Z}$ and $\mathbf{x}, \mathbf{y} \in \mathbb{Z}^n$, it holds that
>$$\left\langle \mathbf{x}\,,\,\mathbf{y} \right\rangle = \left\langle \text{BitDecomp}(\mathbf{x})\,,\, \text{PowersOfTwo}(\mathbf{y}) \right\rangle \;\;(\text{mod } q)  $$
>>[!proof]-
>>$$\begin{alignat}{2}
>> \left\langle \mathbf{x}\,,\,\mathbf{y} \right\rangle &= \sum_{i=0}^n x_{i}y_{i} &&\;\;(\text{mod } q) \\
>> &= \sum_{i=0}^n \sum_{j=0}^l (w_{j,i} \cdot 2^j) y_{i} &&\;\;(\text{mod } q) \\
>> &=\sum_{i=0}^n \sum_{j=0}^l w_{j,i} (2^j \cdot y_{i}) &&\;\;(\text{mod } q) \\
>> &=\sum_{j=0}^l \underbrace{ \mathbf{w}_{j} }_{ \in \mathbb{Z}^n } (2^j \underbrace{ \mathbf{y} }_{  \in \mathbb{Z}^n }) &&\;\;(\text{mod } q) \\
>> &=\sum_{j=0}^l \text{BitDecomp}(\mathbf{x}^T[j]) \cdot \text{PowersOfTwo}(\mathbf{y}_{j}) &&\;\;(\text{mod } q) \\
>> &= \left\langle \text{BitDecomp}(\mathbf{x})\,,\, \text{PowersOfTwo}(\mathbf{y}) \right\rangle &&\;\;(\text{mod } q)\\ 
>>\end{alignat}$$
>>$$\tag*{$\square$}$$

^b9de48

>[!lemma]
>Let $\mathbf{a} \in \mathbb{Z}^n, \mathbf{b} \in \mathbb{Z}_{q}^n$ and $l=\lfloor \log q \rfloor +1$
>$$\begin{align}
> \left\langle \mathbf{a}\,,\, \text{PowersOfTwo}(\mathbf{b})\right\rangle &= \left\langle \text{BitDecomp}^{-1}(\mathbf{a})\,,\, \mathbf{b} \right\rangle \tag{1} \\
> &=\left\langle \text{Flatten}(\mathbf{a})\,,\, \text{PowersOfTwo}(\mathbf{b})\right\rangle   \tag{2}
>\end{align}$$
>>[!proof]-
>>We first show the identity $(1)$. Note that $\text{BitDecomp}^{-1}$ does not necessarily only accept  $\{ 0,1 \}^n$ as domain, but rather $\mathbb{Z}^n$ as a whole. We get
>>$$\begin{alignat}{2}
>> \left\langle \mathbf{a}\,,\, \text{PowersOfTwo}(\mathbf{b})\right\rangle &= \sum_{i=0}^{n-1} a_{i}2^i\mathbf{b} \;\;&&(\text{mod } q) \\
>> &= \mathbf{b}\sum_{i=0}^{n-1}2^ia_{i} \;\;&&(\text{mod } q) \tag{3}\\
>> &= \left\langle \text{BitDecomp}^{-1}(\mathbf{a})\,,\, \mathbf{b} \right\rangle \;\;&&(\text{mod } q) 
>>\end{alignat}$$
>>which shows the first identity. Before continuing the proof for the last part of the identity, we want to note what $\text{BitDecomp}^{-1}$ does on $\mathbb{Z}^n$. 
>>
>>Naturally, $\text{BitDecomp}^{-1}$ acts on the binary numbers whose alphabet is $\{ 0,1 \}$ such that a set of $a_{i} \in \{ 0,1 \}$, with $0 \leq i \leq l-1$ being the bit-depth, composes a positive integer with $\sum_{i=0}^{l-1} 2^ia_{i} = b$. The ordered $a_{i}$ are therefore the binary representation of $b$. Now consider we extend the alphabet of the binary numbers to $\mathbb{Z}$, then each $a_{i} \in \mathbb{Z}$ represents the magnitude of $2^i$ at the $i$-th position. $\text{BitDecomp}^{-1}$ therefore returns the decimal representation of given the coefficients $a_{i}$ over each $2^i$ 
>>
>>If we pass this back to $\text{BitDecomp}$ we yield a **normalized binary representation** of $a$ which is stable in the dot-product of the given identity. See the example of $\text{Flatten}$ on the **binary normalization** above.
>>
>>We will now continue on equation $(3)$, now consider the coefficients $\widehat{a}_{i} \in \{ 0,1 \}$ to be the **binary normalized** coefficients over modulus $q$, so we get
>>$$\begin{alignat}{2}
>>\mathbf{b} \sum_{i=0}^{n-1}2^ia_{i}&= \mathbf{b} \sum_{i=0}^{n-1}2^i\widehat{a}_{i} \;\;&&(\text{mod } q) \\
>> &=  \sum_{i=0}^{n-1}\widehat{a}_{i}2^i\mathbf{b} \;\;&&(\text{mod } q) \\ 
>> &= \left\langle \text{Flatten}(\mathbf{a})\,,\, \text{PowersOfTwo}(\mathbf{b})\right\rangle  \;\;&&(\text{mod } q)
>>\end{alignat}$$
>>which establishes the identity. $$\tag*{$\square$}$$

^2b31c8


>[!algo] Algorithm Key Generation $\text{KeyGen}$ ([[../../../../../../PDFs/gentry2013.pdf#page=10|Source]])
>Let $\lambda, L \in \mathbb{Z}$ with $\lambda$ being the security parameter and $L$ being the circuit complexity parameter.
>1. $\text{Setup}(\lambda, L)$: 
>	- set: $n=n(\lambda,L)$  <span class="right-float"> (lattice dimension parameter)</span>
>	- choose: prime number: $q \in \mathbb{Z}$ 
>		- with $n^2\leq q\leq 2n^2$
>	- choose:  $\chi=\Psi_{\alpha(n)}$ <span class="right-float"> (error distribution)</span>
>	- set $m=(1+\epsilon)(n+1) \log q$ <span class="right-float">(number of equations)</span>
>		- where $\epsilon>0$ is a smoothing parameter related to the Gaussian distribution and the dual lattice
>		- where $m$ is rounded to the next integer
>	- denote: $l = \lfloor \log q \rfloor + 1$ <span class="right-float">(bit-depth)</span>
>	- denote: $N = (n+1) \cdot l$ <span class="right-float">(???)</span>
>
>	 -> **output** parameters: 
>	 $$\text{params} = (n,q,\chi,m)$$
>1. $\text{SecretKeyGen}(\text{params})$:
> 	- sample uniformly: $\mathbf{t} \leftarrow \mathbb{Z}_{q}^n$
> 	- set: $\mathbf{s} \leftarrow (1,-t_{1},\dots,t_{n}) \in \mathbb{Z}_{q}^{n+1}$
> 	- set: $\mathbf{v} \leftarrow \text{PowersOfTwo}(\mathbf{s}) \in \mathbb{Z}_{q}^{(n+1)\cdot l} = \mathbb{Z}_{q}^{N}$
> 	
> 		-> **output** secret key: 
> 		$$\text{sk} =  \mathbf{s} $$
> 	
>1. $\text{PublicKeyGen}(\text{params, sk}, \mathbf{t})$:
>	- sample uniformly: $\mathbf{B} \leftarrow \mathbb{Z}_{q}^{m \times n}$
>	- sample: $\mathbf{e} \leftarrow \chi^m$
>	- set: $\mathbf{b}=\mathbf{B}\cdot \mathbf{t}+\mathbf{e}$
>	- set: $\mathbf{A}=\text{concatenate}(\mathbf{b}, \mathbf{B}) \in \mathbb{Z}^{m\times n+1}$
>	- note: $\mathbf{A} \cdot \mathbf{s}  = \mathbf{e}$  <span class="right-float">(secret denoising)</span>
>
>		-> **output** public key: 
>		$$\text{pk} =  \mathbf{A} $$
>
>
><u>Output:</u> $$\text{KeyGen} \to (\text{pk}= \mathbf{A} , \text{sk} = \mathbf{s})$$
>>[!proof]- Proof $\mathbf{A} \cdot \mathbf{s} = \mathbf{e}$
>>$$\begin{align}
>> \mathbf{A} \cdot \mathbf{s} &= \underbrace{ [\mathbf{b}, \mathbf{B}] }_{ =\mathbf{A} } \cdot (1, -t_{1}, \dots, t_{n}) \\
>> &= [\underbrace{ (\mathbf{B}\cdot \mathbf{t}+\mathbf{e}) }_{ =\mathbf{b} }, \mathbf{B}] \cdot (1, -t_{1}, \dots, t_{n})  \\
>> &= (\mathbf{B} \cdot \mathbf{t} +\mathbf{e}) \cdot 1 - \mathbf{B}[1]t_{1} -\ldots- \mathbf{B}[n]t_{n} \\
>> &= \mathbf{B} \cdot \mathbf{t}  + \Big(- \mathbf{B}[1]t_{1} -\ldots- \mathbf{B}[n]t_{n}\Big) +\mathbf{e} \\
>> &= \underbrace{ \Big(\mathbf{B[1]} t_{1} +\ldots+\mathbf{B}[n]t_{n}\Big)+\Big(-\mathbf{B}[1]t_{1} -\ldots- \mathbf{B}[n]t_{n}\Big) }_{ =0 } +\mathbf{e}  \\
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

^12d9e0

>[!algo] Algorithm Encryption and Decryption ([[../../../../../../PDFs/gentry2013.pdf#page=10|Source]])
>4. $\text{Enc}(\text{params, pk})$:
>	- $\mu \in \mathbb{Z}_{q}$ denotes the plaintext
>	- sample uniformly $\mathbf{R} \leftarrow \{ 0,1 \}^{N \times m}$
>	- output:
>	$$\mathbf{C} = \text{Flatten}\Big(\mu \cdot \mathbf{I}_{N} + \text{BitDecomp}(\mathbf{R}\cdot \mathbf{A})\Big) \in \mathbb{Z}_{q}^{N \times N}$$
>5. $\text{Dec}(\text{params, sk}, \mathbf{C})$:
> 	- denote: $\mathbf{c}_{i} \in \mathbb{Z}_{q}^N$ - $i$-th row of $\mathbf{C}$
> 	- recall: $\mathbf{v}= \text{PowersOfTwo}(\mathbf{s}) \in \mathbb{Z}_{q}^{N}$
> 	- compute: $x_{i} = \left\langle \mathbf{c}_{i}\,,\, \mathbf{v}\right\rangle$
> 	- output:
> $$\mu' = \left\lfloor \frac{x_{i}}{vi} \right\rceil  $$


>[!proof] Proof of Correctness (Short)
> Denote $\mathbf{C}$ the cipher computed by 
> $$\mathbf{C} = \text{Flatten}\Big(\mu \cdot \mathbf{I}_{N} + \text{BitDecomp}(\mathbf{R}\cdot \mathbf{A})\Big) \in \mathbb{Z}_{q}^{N \times N}$$
> Note that a flattened vector is stable under the dot-product seen in [[#^2b31c8|this lemma]] and matrix multiplication with a vector is simply having multiple dot-products. Hence we can drop the flatten operation when computing the scalar product and get for some $\mathbf{c}_{i}$.
> $$\begin{align}
> \mathbf{C}\cdot \mathbf{v}&= \Big(\mu \cdot \mathbf{I}_{N} + \text{BitDecomp}(\mathbf{R}\cdot \mathbf{A})\Big)\mathbf{v} \\
> &= \mu \cdot \underbrace{ \mathbf{I}_{N} \cdot \mathbf{v} }_{ =\mathbf{v} } + \text{BitDecomp}(\mathbf{R}\cdot \mathbf{A})\cdot \text{PowersOfTwo}(\mathbf{s})
>\end{align}$$
>Now applying the [[#^b9de48 | other lemma]] with the fact that $\mathbf{A}\cdot \mathbf{s} = \mathbf{e}$ (see proof [[#^12d9e0|algorithm key generation]])
>$$\begin{align}
> \mathbf{C}\cdot \mathbf{v} &= \mu \cdot \mathbf{v} + \mathbf{R}\cdot \underbrace{ \mathbf{A} \cdot \mathbf{s} }_{ =\mathbf{e} } \\
> &= \mu \cdot \mathbf{v} + \mathbf{R} \cdot \mathbf{e}
>\end{align}$$
>Further note, that the matrix $\mathbf{R}$ consists of zeros and ones, such that $\mathbf{e}$ is bounded by the error distribution, which is small ($<\frac{1}{2})$, and rounding will result into
>$$\mathbf{C}\cdot \mathbf{v} \approx \mu \cdot \mathbf{v}$$
>which establishes the correct encryption $$\tag*{$\square$}$$

>[!question] Open Questions
> - how does the [[1 - Learning With Errors Introduction#^ab0e75|periodic normal distribution]] $\chi$ work exactly? 
> - Gentry specifically highlights on [[../../../../../../PDFs/gentry2013.pdf#page=5| page 5]]
>> The secret key vis a $N$-dimensional vector over $\mathbb{Z}_{q}$ with at least one "big" coefficient $v_{i}$.
>   
>    ongoing he describes [[../../../../../../PDFs/gentry2013.pdf#page=10| page 10]] that the $v_i \in (q/4, q/2]$ this ensures that the error does not grow outside of $q/2$ such that the plaintext $\mu'$ can be recovered.
>	- is the $i$ fixed from here on?
>	-  is the $i$ chosen such that $v_i \in (q/4, q/2]$?
>- how to choose security parameter $\lambda$ correctly and how many operations does it guarantee?
>- how is leveled homomorphism achieved, bootstrapping?


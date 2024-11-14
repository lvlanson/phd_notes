>[!source] 
>Internetsource: [BFV](https://inferati.com/blog/fhe-schemes-bfv)
>Paper: [[../../../../../PDFs/Fan2012.pdf|Fan2012]]


>[!remark] 
> - introduced 2012
> - considered second generation FHE schemes based on [[../Standard LWE/1 - Learning With Errors Introduction|LWE]]/RLWE schemes (Ring Learning with Errors)

>[!remark] Remark on Notation
>Messages and ciphers which are represented as **<span style="color:#e9ffad">plain integers</span>** are written in **<span style="color:#e9ffad">lower case letters</span>**, i.e. $c,m \in \mathbb{Z}$. If they are encoded as **<span style="color:#e9ffad">polynomials</span>** from some polynomial space $\mathcal{F}$ they are written in **<span style="color:#e9ffad">upper case letters</span>**.

---
## 1 - Basic Definitions

>[!def] Definition Plain- and Ciphertext Spaces
>Denote **<span style="color:#38ffa9">$\mathcal{P}$ the plaintext space</span>** and **<span style="color:#38ffa9"> $\mathcal{C}$ the ciphertext space</span>**.  We define plaintext space as $$\mathcal{P}=R_{t}= \mathbb{Z}_{t}[x]/(x^n+1)$$
>with $(x^n+1)$ being a *cyclotomic polynomial*, $n \in \mathbb{N}$ and $t >1$. The ciphertext space is defined as
>$$\mathcal{C}= R_{q} \times R_{q}$$ and
>$$R_{q}= \mathbb{Z}_{q}[x]/(x^n+1)$$
>with  $(x^n+1)$ being a *cyclotomic polynomial* again, $n \in \mathbb{N}$ and $q \gg t$. We call
>- $t > 1$ the **<span style="color:#38ffa9">plaintext coefficient</span>**
>- $q \in \mathbb{N}$ the **<span style="color:#38ffa9">ciphertext coefficient</span>**
>
> ---
>
> **<span style="color:#38ffa9">The space parameters are given as</span>**
> $$(t,q,n)$$
> 
> ---
>
>>[!remark]- Remark on the Degree of the Polynomials
>>The [[../../../../Mathematic Basics/Abstract Algebra/Judson/3 - Polynomial Rings#^a2163f|degree]] of the polynomials in $f \in R_{t}$ and $f  \in R_{q}$ is bounded by $$\text{deg }f < n$$
>
>>[!remark]- Remark on the Choice of the Plaintext and Ciphertext coefficients
>> The coefficients $t,q \in \mathbb{Z}$ are chosen such that
>> $$t \ll q \tag{much smaller}$$
>> Hence, the plaintext space is much smaller than the ciphertext space. Therefore, there are many equivalent encryptions $C_{1},C_{2} \in \mathcal{C}$ such that $$\text{Dec}(C_{1})=Dec(C_{2})=M \in \mathcal{P}$$
>
>>[!remark]- Remark on Space Sizes with Respect to the Space Coefficients
>>$$\begin{align}
>> \lvert R_{t} \rvert &= t^n \tag{Plaintext Space Size}\\
>> \lvert R_{q} \rvert &= q^n  \tag{Ciphertext Space Size}
>>\end{align}$$

>[!def] Definition Symmetric Residue System
>We define the **<span style="color:#38ffa9">residue ring $\mathbb{Z}_{a}$</span>** as the set of coefficients symmetric around $0$ with respect to $\text{mod }a$, i.e.
>$$\mathbb{Z}_{a}= \left\{  \left\lceil  -\frac{a}{2}  \right\rceil, \dots, \left\lfloor  \frac{a-1}{2}  \right\rfloor    \right\}$$ 

>[!def] Definition Error Distribution $\chi$ ([[../../../../../PDFs/Fan2012.pdf#page=3|Source]])
>The error distribution $\chi$ is based on the **<span style="color:#38ffa9">discrete Gaussian distribution $D_{\mathbb{Z, \sigma}}$</span>** with $$D_{\mathbb{Z},\sigma}= \exp\left( \frac{-\pi \lvert x \rvert^2}{\sigma^2}  \right)$$ Given the cyclotomic polynomial $f(x)=x^d+1$ with $d$ being a power of $2$, sampling from $\chi$ is the same as sampling from $D_{\mathbb{Z}, \sigma}^d$. For some chosen error-rate we call the distribution **<span style="color:#38ffa9">$B$-bounded</span>** such that
>$$B = k \cdot \sigma$$
>
>>[!remark] Recall
>>$$P_{x \leftarrow \mathcal{N}(0, \sigma^2)}\big[\lvert x \rvert > k \cdot \sigma \big] = \text{erf}\left( \frac{k}{\sqrt{ 2 }} \right)$$
>>![[Figures/errors_gaussian.png|center|800]]
>
>>[!remark] Remark Sampling based on Non-Cyclotomic Irreducible Polynomials
>> 1. Generally $\chi \neq D^d_{\mathbb{Z}, \sigma}$ if we choose non-cyclotomic irreducible polynomial
>> 2. Given $f$ is a cyclotomic polynomial, but not of the suggested form, sampling is a little more involved

>[!algo] Encryption Scheme ([[../../../../../PDFs/Fan2012.pdf#page=4|Source]])
>
>>[!schlüsselerzeugung] Key Generation  
>> 
>> ---
>> 
>>**<span style="color:#f7b8ff"> <u>Secret Key</u>: </span>**
>> Sample $$\boldsymbol{s} \leftarrow R_{2}$$
>> **<span style="color:#f7b8ff">Output</span>**
>> $$sk = (\boldsymbol{s})$$
>> 
>> ---
>> 
>> **<span style="color:#f7b8ff"><u>Public Key</u>:</span>**
>> Sample
>> $$\begin{align}
>> \boldsymbol{a}&\leftarrow R_{q} \\
>> \boldsymbol{e}&\leftarrow \chi
>>\end{align}$$
>> Compute
>> $$\begin{align}
>> \boldsymbol{p}_{0} &= [-(\boldsymbol{a}\cdot \boldsymbol{s}+ \boldsymbol{e})]_{q} \\
>> \boldsymbol{p}_{1}&= \boldsymbol{a}
>>\end{align}$$
>>**<span style="color:#f7b8ff">Output</span>**
>>$$pk = (\boldsymbol{p}_{0}, \boldsymbol{p}_{1})$$
>>
>>---
>
>>[!verschlüsselung] Encryption/Decryption 
>>---
>> **<span style="color:#f7b8ff"><u>Encryption</u>:</span>**
>> Consider the input 
>> - $\boldsymbol{m}\in R_{t}$ denote the *message* to be encrypted
>> - $pk=(\boldsymbol{p}_{0}, \boldsymbol{p}_{1})$ denote the *public key*
>> 
>> Sample
>> $$\begin{align}
>> \boldsymbol{u}, \boldsymbol{e}_{1}, \boldsymbol{e}_{2} \leftarrow \chi
>>\end{align}$$
>> 
>> Compute
>> $$\begin{align} \\
>> \Delta &= \left\lfloor  \frac{q}{t}  \right\rfloor \\
>> \boldsymbol{c}_{0} &= [\boldsymbol{p}_{0} \cdot \boldsymbol{u} + \boldsymbol{e}_{1} + \Delta \cdot m]_{q} \\
>> \boldsymbol{c}_{1} &= [\boldsymbol{p}_{1} \cdot \boldsymbol{u} + \boldsymbol{e}_{2}]_{q}
>>\end{align}$$
>>**<span style="color:#f7b8ff">Output</span>**
>>$$ct = (\boldsymbol{c}_{0}, \boldsymbol{c}_{1})$$
>>
>>---
>>
>>**<span style="color:#f7b8ff"><u>Decryption</u>:</span>**
>>Consider the input
>>- $sk = (\boldsymbol{s})$ denote the *secret key*
>>- $ct = (\boldsymbol{c}_{0}, \boldsymbol{c}_{1})$ denote the *cipher text*
>>
>>Compute
>>$$\boldsymbol{m} = \left[ \left\lfloor \frac{t \cdot [\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}]_{q}}{q} \right\rceil  \right]_{t}$$
>
>>[!proof] Proof of Correct Encryption
>>$$\begin{align}
>> \boldsymbol{m} &= \left[ \left\lfloor \frac{t \cdot [\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}]_{q}}{q} \right\rceil  \right]_{t}
>>\end{align}$$
>>First compute 
>>$$\begin{align}
>> [{\color{#38ffa9}\boldsymbol{c}_{0}}+ {\color{#38B4ff}\boldsymbol{c}_{1}} \boldsymbol{s}]_{q}&= [{\color{#38ffa9}\boldsymbol{p}_{0} \boldsymbol{u}+ \boldsymbol{e_{1}}+ \Delta \boldsymbol{m}} + ({\color{#38B4ff}\boldsymbol{p}_{1}\boldsymbol{u}+\boldsymbol{e}_{2}})\boldsymbol{s}]_{q} \\
>> &= [\underbrace{ -(\boldsymbol{a} \boldsymbol{s}+ \boldsymbol{e}) }_{ =\boldsymbol{p}_{0} }  \boldsymbol{u}+ \boldsymbol{e}_{1} + \Delta \boldsymbol{m} + (\boldsymbol{a}\boldsymbol{u}+ \boldsymbol{e}_{2})\cdot \boldsymbol{s}]_{q} \\
>> &= [\cancel{ -\boldsymbol{aus} }- \boldsymbol{u}\boldsymbol{e} + \boldsymbol{e}_{1} + \Delta \boldsymbol{m} + \cancel{ \boldsymbol{as}\boldsymbol{u} } + \boldsymbol{se}_{2}]_{q} \\
>> &= [\Delta \boldsymbol{m} + \underbrace{ \boldsymbol{e}_{1} + \boldsymbol{se}_{2} - \boldsymbol{ue} }_{ = \boldsymbol{v}}]_{q} \\
>> &= [\Delta \boldsymbol{m} + \boldsymbol{v}]_{q}
>>\end{align}$$
>>where $\boldsymbol{v}$ is the accumulated error-term. 
>>>[!note] Note on the Magnitude of the Error Term
>>>$$\begin{alignat}{2}
>>> \lvert\lvert -\boldsymbol{eu} \rvert\rvert_{\infty} &\leq B \qquad && \boldsymbol{e} \in_{R} \chi_{B}, \;\boldsymbol{u} \in_{R} R_{2} = \mathbb{Z}_{2}[x]/(x^n+1) \\
>>> \lvert\lvert \boldsymbol{e}_{1} \rvert\rvert_{\infty} &\leq  1 && \boldsymbol{e}_{1} \in_{R} \chi_{B} \\
>>> \lvert\lvert \boldsymbol{se}_{2} \rvert\rvert_{\infty} &\leq B && \boldsymbol{e}_{2} \in_{R} \chi_{B}, \; \boldsymbol{s} \in_{R}R_{2}= \mathbb{Z}_{2}[x]/(x^n+1) 
>>>\end{alignat}$$
>>>Therefore it must follow
>>>$$\lvert\lvert \boldsymbol{e}_{1}+\boldsymbol{se}_{2} - \boldsymbol{eu}\rvert\rvert_{\infty} \leq 2B+1 $$
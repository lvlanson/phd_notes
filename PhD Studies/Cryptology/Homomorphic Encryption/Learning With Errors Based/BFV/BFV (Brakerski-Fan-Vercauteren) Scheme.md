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
>with $(x^n+1)$ being a *cyclomatic polynomial*, $n \in \mathbb{N}$ and $t \in \mathbb{N}$. The ciphertext space is defined as
>$$\mathcal{C}= R_{q} \times R_{q}$$ and
>$$R_{q}= \mathbb{Z}_{q}[x]/(x^n+1)$$
>with  $(x^n+1)$ being a *cyclomatic polynomial* again, $n \in \mathbb{N}$ and $q \in \mathbb{N}$. We call
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
>The error distribution $\chi$ is based on the **<span style="color:#38ffa9">discrete Gaussian distribution $D_{\mathbb{Z, \sigma}}$</span>**. Given the cyclomatic polynomial $f(x)=x^d+1$ with $d$ being a power of $2$, sampling from $\chi$ is the same as sampling from $D_{\mathbb{Z}, \sigma}^d$.
>
>>[!remark] Recall
>>$$P_{x \leftarrow \mathcal{N}(0, \sigma^2)}\big[\lvert x \rvert > k \cdot \sigma \big] = \text{erf}\left( \frac{k}{\sqrt{ 2 }} \right)$$
>>![[Figures/errors_gaussian.png|center|800]]



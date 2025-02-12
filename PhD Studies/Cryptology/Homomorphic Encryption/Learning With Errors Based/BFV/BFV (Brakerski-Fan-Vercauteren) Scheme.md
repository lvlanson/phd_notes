>[!source] 
>Internetsource: [BFV](https://inferati.com/blog/fhe-schemes-bfv)
>Paper: [[../../../../../PDFs/Fan2012.pdf|Fan2012]]


>[!remark] 
> - introduced 2012
> - considered second generation FHE schemes based on [[../Standard LWE/1 - Learning With Errors Introduction|LWE]]/RLWE schemes (Ring Learning with Errors)

>[!remark] Remark on Notation
>Messages and ciphers which are represented as **<span style="color:#e9ffad">plain integers</span>** are written in **<span style="color:#e9ffad">lower case letters</span>**, i.e. $c,m \in \mathbb{Z}$. If they are encoded as **<span style="color:#e9ffad">polynomials</span>** from some polynomial space $\mathcal{F}$ they are written in **<span style="color:#e9ffad">upper case letters</span>**.

---
## 0 - Preliminaries
>[!theorem] Theorem Infinity Norm on Products of Polynomials in Polynomial Rings with Respect to Cyclotomic Reduction
> Let $\boldsymbol{f}, \boldsymbol{g}$ be polynomials in $R = \mathbb{Z}[x]/(x^n+1)$ where $(x^n+1)$ is a cyclotomic polynomial. Define the infinity norm
> $$\lvert\lvert \boldsymbol{g} \rvert\rvert_{\infty} := {\text{max}}\;\left\{  a_{i} \;\Bigg\vert\; \boldsymbol{g}=\sum_{i=0}^{n-1} a_{i}x^i  \right\} $$
> Then the infinity norm of the products of polynomials in $R$ is given as
> $$\lvert\lvert \boldsymbol{f} \cdot \boldsymbol{g} \rvert\rvert_{\infty} \leq  \delta_{R}\lvert\lvert \boldsymbol{f} \rvert\rvert_{\infty} \cdot \lvert\lvert \boldsymbol{g} \rvert\rvert_{\infty}  $$
> where $\delta_{R}$ is the **<span style="color:#38ffa9">ring expansion factor</span>** or also **<span style="color:#38ffa9">fudge factor</span>** with respect to $R$. 
>
>In worst-case we have
>$$\delta_{R} = n$$
>>[!proof]- Proof is omitted, but comments can be found
>> There are different ways on how to show, that $\delta_{R} = n$ in worst case. Peikert suggests in [[../../../../../PDFs/Peikert2016.pdf#page=30|his survey 4.3.3]] using a canonical embedding $\phi:R\to \mathbb{C}^n$
>> from algebraic number theory, where each ring element $\boldsymbol{z} \in R$ maps to some vector in $\mathbb{C}^n$, where the norm can be estimated more precisely over the roots of the polynomial. 

^79979b

## 1 - Basic Definitions

>[!def] Definition Plain- and Ciphertext Spaces
>Denote **<span style="color:#38ffa9">$\mathcal{P}$ the plaintext space</span>** and **<span style="color:#38ffa9"> $\mathcal{C}$ the ciphertext space</span>**.  We define plaintext space as $$\mathcal{P}=R_{t}= \mathbb{Z}_{t}[x]/(x^n+1)$$
>with $(x^n+1)$ being a *cyclotomic polynomial*, $n \in \mathbb{N}$ and $t >1$. The ciphertext space is defined as
>$$\mathcal{C}= R_{q} \times R_{q}$$ and
>$$R_{q}= \mathbb{Z}_{q}[x]/(x^n+1)$$
>with  $(x^n+1)$ being a *cyclotomic polynomial* again, $n \in \mathbb{N}$ and $t \ll q$. We call
>- $t > 1$ the **<span style="color:#38ffa9">plaintext coefficient</span>**
>- $q \in \mathbb{N}$ the **<span style="color:#38ffa9">ciphertext coefficient</span>**
>
> ---
>
> **<span style="color:#38ffa9">The space-parameters are given as</span>**
> $$(t,q,n)$$
> 
> ---
>
>>[!remark] Remark on the Degree of the Polynomials
>>The [[../../../../Mathematic Basics/Abstract Algebra/Judson and Dummit/7 - Polynomial Rings#^a2163f|degree]] of the polynomials in $\boldsymbol{f} \in R_{t}$ and $\boldsymbol{f}  \in R_{q}$ is bounded by $$\text{deg }\boldsymbol{f} < n$$
>
>>[!remark] Remark on the Choice of the Plaintext and Ciphertext coefficients
>> The coefficients $t,q \in \mathbb{Z}$ are chosen such that
>> $$t \ll q \tag{much smaller}$$
>> Hence, the plaintext space is much smaller than the ciphertext space. Therefore, there are many equivalent encryptions $C_{1},C_{2} \in \mathcal{C}$ such that $$\text{Dec}(C_{1})=Dec(C_{2})=M \in \mathcal{P}$$
>
>>[!remark] Remark on Space Sizes with Respect to the Space Coefficients
>>$$\begin{align}
>> \lvert R_{t} \rvert &= t^n \tag{Plaintext Space Size}\\
>> \lvert R_{q} \rvert &= q^n  \tag{Ciphertext Space Size}
>>\end{align}$$

^593a3a

>[!def] Definition Symmetric Residue System
>We define the **<span style="color:#38ffa9">residue ring $\mathbb{Z}_{a}$</span>** as the set of coefficients symmetric around $0$ with respect to $\text{mod }a$, i.e.
>$$\mathbb{Z}_{a}= \left\{  \left\lceil  -\frac{a}{2}  \right\rceil, \dots, \left\lfloor  \frac{a-1}{2}  \right\rfloor    \right\}$$ 

>[!def] Definition Error Distribution $\chi$ ([[../../../../../PDFs/Fan2012.pdf#page=3|Source]])
>The error distribution $\chi$ is based on the **<span style="color:#38ffa9">discrete Gaussian distribution $D_{\mathbb{Z, \sigma}}$</span>** with $$D_{\mathbb{Z},\sigma}= \exp\left( \frac{-\pi \lvert x \rvert^2}{\sigma^2}  \right)$$ Given the cyclotomic polynomial $f(x)=x^n+1$ with $d$ being a power of $2$, sampling from $\chi$ is the same as sampling from $D_{\mathbb{Z}, \sigma}^n$. For some chosen error-rate we call the distribution **<span style="color:#38ffa9">$B$-bounded</span>** such that
>$$B = k \cdot \sigma$$
>
>>[!important]
>>When we sample from $\chi$ in this encryption scheme, we sample the coefficients in $\mathbb{Z}_{s}[x]/(x^n+1)$ with these being at most $B$, i.e. for some polynomial $\boldsymbol{g} \in \mathbb{Z}_{s}[x]/(x^n+1)$
>>$$g(x) = a_{0}+ a_{1}x+\dots+a_{n-1}x^{n-1}$$
>>the coefficients are bounded with
>>$$0 \leq a_{i} \leq B$$
>>with probability 
>>$$P_{x \leftarrow \mathcal{N}(0, \sigma^2)}\Big[0 \leq a_{i} \leq B\Big] = 1-\text{erf}\left( \frac{k}{\sqrt{ 2 }} \right)$$
>
>>[!remark] Recall
>>$$P_{x \leftarrow \mathcal{N}(0, \sigma^2)}\big[\lvert x \rvert > k \cdot \sigma \big] = \text{erf}\left( \frac{k}{\sqrt{ 2 }} \right)$$
>>![[Figures/errors_gaussian.png|center|800]]
>>
>> Fix the error tolerance with $\varepsilon$. We can determine $k$ according to the error-tolerance with
>> $$\beta(\varepsilon):= \min\left\{ \;\; \beta \;\; \Bigg\vert \;\text{erf}\left( \frac{\beta}{\sqrt{ 2 }}  \right) < \varepsilon \right\}$$
>> then $k = \beta(\varepsilon)$ and samples are then $B=k \cdot \sigma$-bounded.
>> 
>>>[!example]
>>>Let $\varepsilon=2^{-64}$ then $\beta(\varepsilon)>9.2$
>
>>[!remark] Remark Sampling based on Non-Cyclotomic Irreducible Polynomials
>> 1. Generally $\chi \neq D^d_{\mathbb{Z}, \sigma}$ if we choose non-cyclotomic irreducible polynomial
>> 2. Given $f$ is a cyclotomic polynomial, but not of the suggested form, sampling is a little more involved

>[!algo] Encryption Scheme ([[../../../../../PDFs/Fan2012.pdf#page=4|Source]])
>
>>[!schlüsselerzeugung] Key Generation  
>> 
>>**<span style="color:#f7b8ff"> <u>Secret Key</u>: </span>** `SecretKeyGen(λ) -> sk`
>>
>>  **<span style="color:#f7b8ff">Input</span>** 
>> - $\lambda$ is the security parameter
>>
>> **<span style="color:#f7b8ff">Procedure</span>**
>> 
>> Sample $$\boldsymbol{s} \leftarrow R_{2}$$
>> **<span style="color:#f7b8ff">Output</span>**
>> $$sk = (\boldsymbol{s})$$
>> 
>> ---
>> 
>> **<span style="color:#f7b8ff"><u>Public Key</u>:</span>** `PublicKeyGen(sk) -> pk`
>> 
>> **<span style="color:#f7b8ff">Input</span>** 
>> 
>> - Secret Key $sk$
>> 
>> **<span style="color:#f7b8ff">Procedure</span>**
>> 
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
>> ---
>> 
>> **<span style="color:#f7b8ff"> <u>Evaluation Key</u>: </span>**([[../../../../../PDFs/Fan2012.pdf#page=8|Source]])
>>
>>There are 2 versions suggested. 
>>
>> <u>Version 1</u> `EvaluationKeyGen(sk, T) -> rlk`
>> 
>> <u>Version 2 </u>`EvaluationKeyGen(sk, p) -> rlk`
>>
>> **<span style="color:#f7b8ff">Output</span>**
>> $$rlk =$$
>
>>[!verschlüsselung] Encryption/Decryption 
>>
>> **<span style="color:#f7b8ff"><u>Encryption</u>:</span>**`Encrypt(pk, m) -> ct`
>> 
>> **<span style="color:#f7b8ff">Input</span>** 
>> - $\boldsymbol{m}\in R_{t}$ denotes the *message* to be encrypted
>> - $pk=(\boldsymbol{p}_{0}, \boldsymbol{p}_{1})$ denotes the *public key*
>> 
>> **<span style="color:#f7b8ff">Procedure</span>** 
>> 
>> Sample
>> $$\begin{align}
>> \boldsymbol{u} &\leftarrow R_{2}  \\ 
>> \boldsymbol{e}_{1}, \boldsymbol{e}_{2} &\leftarrow \chi
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
>>**<span style="color:#f7b8ff"><u>Decryption</u>:</span>** `Decrypt(sk, ct) -> m`
>>
>> **<span style="color:#f7b8ff">Input</span>** 
>>- $sk = (\boldsymbol{s})$ denotes the *secret key*
>>- $ct = (\boldsymbol{c}_{0}, \boldsymbol{c}_{1})$ denotes the *cipher text*
>>
>> **<span style="color:#f7b8ff">Procedure</span>** 
>>
>>Compute
>>$$\boldsymbol{m} = \left[ \left\lfloor \frac{t \cdot [\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}]_{q}}{q} \right\rceil  \right]_{t}$$
>>
>> **<span style="color:#f7b8ff">Output</span>** 
>> $$\boldsymbol{m}$$
>>
>
>>[!proof] Proof of Correct Encryption
>>$$\begin{align}
>> \boldsymbol{m} &= \left[ \left\lfloor \frac{t \cdot {\color{#f7b8ff}[\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}]_{q}}}{q} \right\rceil  \right]_{t}
>>\end{align}$$
>>First **<span style="color:#f7b8ff">compute</span>** 
>>$$\begin{align}
>> [{\color{#38ffa9}\boldsymbol{c}_{0}}+ {\color{#38B4ff}\boldsymbol{c}_{1}} \boldsymbol{s}]_{q}&= [{\color{#38ffa9}\boldsymbol{p}_{0} \boldsymbol{u}+ \boldsymbol{e_{1}}+ \Delta \boldsymbol{m}} + ({\color{#38B4ff}\boldsymbol{p}_{1}\boldsymbol{u}+\boldsymbol{e}_{2}})\boldsymbol{s}]_{q} \\
>> &= [\underbrace{ -(\boldsymbol{a} \boldsymbol{s}+ \boldsymbol{e}) }_{ =\boldsymbol{p}_{0} }  \boldsymbol{u}+ \boldsymbol{e}_{1} + \Delta \boldsymbol{m} + (\boldsymbol{a}\boldsymbol{u}+ \boldsymbol{e}_{2})\cdot \boldsymbol{s}]_{q} \\
>> &= [\cancel{ -\boldsymbol{aus} }- \boldsymbol{u}\boldsymbol{e} + \boldsymbol{e}_{1} + \Delta \boldsymbol{m} + \cancel{ \boldsymbol{as}\boldsymbol{u} } + \boldsymbol{se}_{2}]_{q} \\
>> &= [\Delta \boldsymbol{m} + \underbrace{ \boldsymbol{e}_{1} + \boldsymbol{se}_{2} - \boldsymbol{ue} }_{ = \boldsymbol{v}}]_{q} \\
>> &= [\Delta \boldsymbol{m} + \boldsymbol{v}]_{q}
>>\end{align}$$
>>where $\boldsymbol{v}$ is the **<span style="color:#f7b8ff"> accumulated error-term</span>**. 
>>
>>>[!note] Note on the Magnitude of the Error Term
>>>We use [[#^79979b| the theorem for the norm of the products in rings]] and have
>>>$$\begin{alignat}{2}
>>> \lvert\lvert -\boldsymbol{eu} \rvert\rvert_{\infty} &\leq \delta_{R}B \qquad && \boldsymbol{e} \in_{R} \chi, \;\boldsymbol{u} \in_{R} R_{2} = \mathbb{Z}_{2}[x]/(x^n+1) \\
>>> \lvert\lvert \boldsymbol{e}_{1} \rvert\rvert_{\infty} &\leq  B && \boldsymbol{e}_{1} \in_{R} \chi \\
>>> \lvert\lvert \boldsymbol{se}_{2} \rvert\rvert_{\infty} &\leq \delta_{R}B && \boldsymbol{e}_{2} \in_{R} \chi, \; \boldsymbol{s} \in_{R}R_{2}= \mathbb{Z}_{2}[x]/(x^n+1) 
>>>\end{alignat}$$
>>>Therefore it must follow
>>>$$\begin{align}
>> \lvert\lvert \boldsymbol{e}_{1}+\boldsymbol{se}_{2} - \boldsymbol{eu}\rvert\rvert_{\infty} &\leq \lvert\lvert \boldsymbol{e}_{1} \rvert\rvert+\lvert\lvert \boldsymbol{se}_{2} \rvert\rvert +\lvert\lvert -\boldsymbol{e}\boldsymbol{u} \rvert\rvert    \\
>> & \leq B + \delta_{R}B +\delta_{R}B  \\
>> &= B(2\delta_{R}+1)
>>\end{align} $$ 
>>
>>Expanding $[\;\cdot\;]_{q}$ with some residue $\boldsymbol{r} \in R_{q}$ gives
>>$$\begin{align}
>> \phantom{[{\color{#38ffa9}\boldsymbol{c}_{0}}+ {\color{#38B4ff}\boldsymbol{c}_{1}} \boldsymbol{s}]_{q}}&= \Delta \boldsymbol{m}+ \boldsymbol{v} + q\boldsymbol{r} \qquad\qquad\qquad\qquad\qquad\qquad\;\tag{1}
>>\end{align}$$
>>We **<span style="color:#f7b8ff">continue with</span>** 
>>$$\boldsymbol{m} = \left[ \left\lfloor {\color{#f7b8ff}\frac{t \cdot [\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}]_{q}}{q}} \right\rceil  \right]_{t}$$
>>and calculate  
>>$$\begin{align} 
>> \frac{t \cdot [\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}]_{q}}{q} &= \frac{t \cdot (\Delta \boldsymbol{m}+ \boldsymbol{v} + \boldsymbol{r}q )}{q} \\
>> &=  \frac{t}{q}\Delta \boldsymbol{m}+ \frac{t}{q}\boldsymbol{v} + t\boldsymbol{r}  \\
>>\end{align}$$
>>Note, we defined [[#^593a3a| the parameters]] $t \ll q$, such that $\frac{t}{q}$ is close to zero and $\left\lfloor \frac{q}{t} \right\rfloor=\Delta$ is some large integer. By rounding we are losing some information $\varepsilon$ on $\frac{q}{t}$. Further, we note that $\left\lfloor  \frac{q}{t}  \right\rfloor \leq \frac{q}{t}$, obviously. Hence, we define
>>$$\frac{q}{t}-\Delta= \varepsilon \iff \Delta=\frac{q}{t}-\varepsilon$$
>>with $0 \leq\varepsilon \ll 1$. So we substitute $\Delta$
>>$$\begin{align}
>> \frac{t}{q}\Delta \boldsymbol{m}+ \frac{t}{q}\boldsymbol{v} + t\boldsymbol{r} &=\frac{t}{q}\left( \frac{q}{t}-\varepsilon \right)\boldsymbol{m} + \frac{t}{q}\boldsymbol{v} + t\boldsymbol{r} \\
>> &= \boldsymbol{m} - \frac{t}{q}\varepsilon \boldsymbol{m} + \frac{t}{q}\boldsymbol{v} + t\boldsymbol{r} \\
>> &= \boldsymbol{m}  + \frac{t}{q}(\boldsymbol{v}-\varepsilon \boldsymbol{m}) + t\boldsymbol{r}
>>\end{align}$$
>>For the **<span style="color:#f7b8ff">rounding process</span>** in 
>>$$\boldsymbol{m} = \left[ {\color{#f7b8ff}\left\lfloor \frac{t \cdot [\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}]_{q}}{q} \right\rceil}  \right]_{t}$$
>>we need to consider the norm
>>$$\frac{t}{q} \cdot\lvert\lvert \boldsymbol{v}-\varepsilon \boldsymbol{m} \rvert\rvert_{\infty} $$
>>and require 
>>$$\frac{t}{q} \cdot\lvert\lvert \boldsymbol{v}-\varepsilon \boldsymbol{m} \rvert\rvert_{\infty} < \frac{1}{2}$$
>>for the rounding process to have the term vanish. We note, $\boldsymbol{m} \in R_{t}$ and $0 \leq \varepsilon \ll 1$. We have $$\begin{align}
>> \lvert\lvert \boldsymbol{v} + (- \varepsilon \boldsymbol{m}) \rvert\rvert_{\infty} \leq \lvert\lvert \boldsymbol{v} \rvert\rvert_{\infty}  + \lvert\lvert -\varepsilon \boldsymbol{m} \rvert\rvert_{\infty} &\leq \lvert\lvert \boldsymbol{v} \rvert\rvert_{\infty}  +t \\
>>\end{align}$$
>>By estimating the norm, we get.
>>$$\begin{align}
>> \frac{t}{q} \cdot \lvert\lvert \boldsymbol{v}- \varepsilon \boldsymbol{m} \rvert\rvert_{\infty} &< \frac{1}{2} \\
>>   \lvert\lvert \boldsymbol{v}- \varepsilon \boldsymbol{m} \rvert\rvert_{\infty} &< \frac{1}{2} \cdot \frac{q}{t} \\ 
>> \lvert\lvert \boldsymbol{v} \rvert\rvert_{\infty}  +t &< \frac{1}{2} \cdot \frac{q}{t} 
>>\end{align}$$
>>We denote $r_{t}(q) + \left\lfloor  \frac{q}{t}  \right\rfloor = \frac{q}{t}$ the residue from the flooring function. With $\Delta=\frac{q}{t}$ we continue 
>>$$\begin{align}
>> \lvert\lvert \boldsymbol{v} \rvert\rvert_{\infty}  +t &< \frac{1}{2} \cdot \frac{q}{t}  \\
>> \lvert\lvert \boldsymbol{v} \rvert\rvert_{\infty}   &< \frac{1}{2} \cdot \Delta+\underbrace{ r_{t}(q)-t }_{ <0 } < \frac{\Delta}{2}
>>\end{align}$$
>>**<span style="color:#f7b8ff">which establishes the parameter choice with respect to the error</span>**, hence
>>$$\lvert\lvert \boldsymbol{v} \rvert\rvert_{\infty}< B(2\delta_{R}+1) <\frac{\Delta}{2}$$
>>
>>Therefore, rounding should give
>>$$\begin{align}
>> \boldsymbol{m}&= [\boldsymbol{m}+t\boldsymbol{r}]_{t} \\
>> &=\boldsymbol{m}
>>\end{align}$$
>>after taking $\text{mod } t$.
>
>>[!homomorphic] Homomorphic Operations
>>
>>**<span style="color:#f7b8ff"><u>Addition:</u></span>** `Add(ct_1, ct_2) -> ct_3`
>>
>>**<span style="color:#f7b8ff">Input</span>**
>> 
>> $$\begin{align}
>> ct &= (\boldsymbol{c}_{0}, \boldsymbol{c}_{1}) \tag{= ct\_1}\\
>> ct' &= (\boldsymbol{c}_{0}', \boldsymbol{c}_{1}') \tag{= ct\_2}
>>\end{align}$$
>>
>>**<span style="color:#f7b8ff">Procedure</span>**
>>
>>The addition is defined as
>>$$ct'' =ct + ct' = \Big([\boldsymbol{c}_{0}+\boldsymbol{c}_{0}']_{q}, [\boldsymbol{c}_{1} + \boldsymbol{c}_{1}']_{q}\Big)$$
>>
>>**<span style="color:#f7b8ff">Output</span>**
>>
>> $$ct'' \tag{= ct\_3}$$
>>
>>**<span style="color:#f7b8ff"><u>Multiplication:</u></span>** `Mul(ct_1, ct_2, rlk) -> ct_3`
>> 
>>**<span style="color:#f7b8ff">Input</span>**
>>$$\begin{align}
>> ct &= (\boldsymbol{c}_{0}, \boldsymbol{c}_{1}) \tag{= ct\_1}\\
>> ct' &= (\boldsymbol{c}_{0}', \boldsymbol{c}_{1}') \tag{= ct\_2} \\
>> rlk &= \Big[\Big([-(\boldsymbol{a}_{i} \cdot \boldsymbol{s}+ \boldsymbol{e}_{i})+T^i \cdot \boldsymbol{s}^2]_{q}, \boldsymbol{a}_{i}\Big)\Big]_{i=0}^l\tag{Version 1} \\
>> rlk &= \Big(\big[-(\boldsymbol{a} \cdot \boldsymbol{s} +  p \cdot \boldsymbol{s}^2)\big]_{p \cdot q}, \boldsymbol{a}\Big)\tag{Version 2}
>>\end{align}$$
>>
>>**<span style="color:#f7b8ff">Procedure</span>**
>>
>>$$\begin{align}
>> \widehat{\boldsymbol{c}}_{0} &= \left[ \left\lfloor \frac{t \cdot(\boldsymbol{c}_{0} \cdot \boldsymbol{c}_{0}')}{q} \right\rceil \right]_{q} \\
>> \widehat{\boldsymbol{c}}_{1} &= \left[ \left\lfloor \frac{t \cdot(\boldsymbol{c}_{0} \cdot \boldsymbol{c}_{1}'  + \boldsymbol{c}_{1} \cdot \boldsymbol{c}_{0}')}{q} \right\rceil \right]_{q} \\
>> \widehat{\boldsymbol{c}}_{2} &= \left[ \left\lfloor \frac{t \cdot(\boldsymbol{c}_{1} \cdot \boldsymbol{c}_{1}')}{q} \right\rceil \right]_{q}
>>\end{align}$$
>>Now the $3$ cipher artifacts need to be relinearized with $\widehat{ct}=(\widehat{\boldsymbol{c}}_{0}, \widehat{\boldsymbol{c}}_{1}, \widehat{\boldsymbol{c}}_{2})$ and
>>$$ct'' = (\boldsymbol{c}_{0}'', \boldsymbol{c}_{1}'') = \text{Relin}(\widehat{ct}, rlk)$$
>>
>>**<span style="color:#f7b8ff">Output</span>**
>>$$ct'' = (\boldsymbol{c}_{0}'', \boldsymbol{c}_{1}'') \tag{= ct\_3}$$
>>
>>>[!abstract] Deriving the Multiplication Formula
>>>
>>>We will use the evaluation of the ciphertext to motivate the multiplication of ciphertexts
>>>$$\begin{align}
>>>\boldsymbol{m}_{i} = \left[ \left\lfloor \frac{t \cdot [{\color{#f7b8ff}\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}}]_{q}}{q} \right\rceil  \right]_{t} =  \left[ \left\lfloor \frac{t \cdot [{\color{#f7b8ff}ct_{i}(\boldsymbol{s})}]_{q}}{q} \right\rceil  \right]_{t}
>>>\end{align}$$
>>>Hence
>>>$$[ct_{i}(\boldsymbol{s})]_{q}= [\boldsymbol{c}_{0}+ \boldsymbol{c}_{1} \cdot \boldsymbol{s}]_{q} = \Delta \boldsymbol{m}+ \boldsymbol{v} + \boldsymbol{r}q$$
>>>as we showed in the correctness proof in equation $(1)$. Now, note that if we multiply two ciphers evaluated at $\boldsymbol{s}$ we get
>>>$$\begin{align}
>>> (ct_{1} \cdot ct_{2})(\boldsymbol{s}) &= ({\color{#38ffa9}\Delta \boldsymbol{m}_{1}}+ {\color{#e9ffad}\boldsymbol{v}_{1}} + {\color{#f7b8ff}\boldsymbol{r}_{1}q})(\Delta \boldsymbol{m}_{2}+ \boldsymbol{v}_{2} + \boldsymbol{r}_{2}q) \\
>>> &= {\color{#38ffa9}\Delta^2\boldsymbol{m}_{1}\boldsymbol{m}_{2} + \Delta \boldsymbol{m}_{1}\boldsymbol{v}_{2} + \Delta q\boldsymbol{m}_{1}\boldsymbol{r}_{2}} + { \color{#e9ffad}\Delta \boldsymbol{m}_{2}\boldsymbol{v}_{1} + \boldsymbol{v}_{1}\boldsymbol{v}_{2} + q\boldsymbol{v_{1}}\boldsymbol{v_{2}}} \; + {\color{#f7b8ff} \Delta q\boldsymbol{m}_{2}\boldsymbol{r}_{1}+q\boldsymbol{r}_{1}\boldsymbol{v}_{2} + q^2\boldsymbol{r}_{1}\boldsymbol{r}_{2}} \\
>>> &= \Delta^2\boldsymbol{m}_{1}\boldsymbol{m}_{2} + \Delta(\boldsymbol{m}_{1}\boldsymbol{v}_{2}+\boldsymbol{m}_{2}\boldsymbol{v}_{1}) + q(\boldsymbol{v}_{1}\boldsymbol{r}_{2}+ \boldsymbol{v}_{2}\boldsymbol{r}_{1}) + \Delta q(\boldsymbol{m}_{1}\boldsymbol{r}_{2}+\boldsymbol{m}_{2}\boldsymbol{r}_{1})+ \boldsymbol{v}_{1}\boldsymbol{v}_{2} + q^2\boldsymbol{r}_{1}\boldsymbol{r}_{2}
>>>\end{align}$$
>>> Note, in the last line we wish to eliminate a factor of $\Delta$, i.e. multiply by $\frac{1}{\Delta}$, such that we yield the form which one would expect when encrypting $[\boldsymbol{m}_{1} \cdot \boldsymbol{m}_{2}]_{t}$. The last term $q^2\boldsymbol{r}_{1}\boldsymbol{r}_{2}$ would cause great noise if we can't reduce the square from $q^2$. Since $\Delta= \left\lfloor  \frac{q}{t}  \right\rfloor$ and $\frac{q}{t}$ are very close, we multiply with $\left( \frac{q}{t} \right)^{-1}$ instead. 
>>>
>>> We will use the following facts
>>> $$\begin{align}
>>> \boldsymbol{m}_{1} \cdot \boldsymbol{m}_{2} &= [\boldsymbol{m}_{1} \cdot \boldsymbol{m}_{2}]_{t} + t \boldsymbol{r}_{m} \tag{2} \\
>>> \boldsymbol{v}_{1} \cdot \boldsymbol{v}_{2} &= [\boldsymbol{v}_{1} \cdot \boldsymbol{v}_{2}]_{\Delta} + \Delta \boldsymbol{r}_{v} \tag{3} \\
>>> t \cdot \Delta &= q - r_{t}(q) \tag{4}
>>> \end{align}$$
>>> Where $(2)$ and $(3)$ are just the reduction of the product with respect to some modulus and $\boldsymbol{r}$ being the remainder polynomial from the reduction $[\cdot]_{(\,\cdot\,)}$. Fact $(4)$ is due to $\Delta= \left\lfloor  \frac{q}{t}  \right\rfloor=\frac{q}{t} -r_{t}(q)$ with $0 \leq r_t(q) \ll 1$ being very small. We now reduce the raw cipher-product as suggested by multiplying with $\left( \frac{q}{t} \right)^{-1}$
>>> $$\begin{align}
>>> \frac{t(ct_{1} \cdot ct_{2})(\boldsymbol{s})}{q} &= \underbrace{ \frac{t}{q}\Delta^2\boldsymbol{m}_{1}\boldsymbol{m}_{2} }_{ (a) } + \underbrace{ \frac{t}{q}\Delta(\boldsymbol{m}_{1}\boldsymbol{v}_{2}+\boldsymbol{m}_{2}\boldsymbol{v}_{1}) }_{ (b) } + \underbrace{ \frac{t}{q}q(\boldsymbol{v}_{1}\boldsymbol{r}_{2}+ \boldsymbol{v}_{2}\boldsymbol{r}_{1}) }_{ (c) } \\ \\
&\,+ \underbrace{ \frac{t}{q}\Delta q(\boldsymbol{m}_{1}\boldsymbol{r}_{2}+\boldsymbol{m}_{2}\boldsymbol{r}_{1}) }_{ (d) }+\underbrace{ \frac{t}{q}\boldsymbol{v}_{1}\boldsymbol{v}_{2} }_{ (e) } + \underbrace{ \frac{t}{q} q^2\boldsymbol{r}_{1}\boldsymbol{r}_{2} }_{ (f) }
>>>\end{align}$$
>>> We will now discuss how each term simplifies. Note, all these terms are embedded in $\text{mod } q$, i.e. $[\cdot]_q$
>>> 
>>> $(a)$
>>> First we make use of fact $(4)$
>>> $$\Delta = \frac{q-r_{t}(q)}{t}$$
>>> Hence, we have
>>> $$\begin{align}
>>> \frac{t}{q}\Delta^2\boldsymbol{m}_{1}\boldsymbol{m}_{2} &= \frac{t}{q} \left( \frac{q-r_{t}(q)}{t} \right)^2 \boldsymbol{m}_{1}\boldsymbol{m}_{2} \\
>>> &= \frac{\cancel{ t }}{q} \frac{(q-r_{t}(q))^2}{t^{\cancel{ 2 }}} \boldsymbol{m}_{1}\boldsymbol{m}_{2} \\
>>> &= \frac{(q-r_{t}(q))^2}{qt} \boldsymbol{m}_{1}\boldsymbol{m}_{2} \\
>>>\end{align}$$
>>>We continue with fact $(1)$
>>>$$\begin{align}
>>> \phantom{\frac{t}{q}\Delta^2\boldsymbol{m}_{1}\boldsymbol{m}_{2}} &= \frac{(q-r_{t}(q))^2}{qt} \Big([\boldsymbol{m}_{1}\boldsymbol{m}_{2}]_{t}+t\boldsymbol{r}_{m}\Big) \\
>>> &= \frac{(q-r_{t}(q))^2}{qt}[\boldsymbol{m}_{1}\boldsymbol{m}_{2}]_{t}+ \frac{(q-r_{t}(q))^2}{qt}t\boldsymbol{r}_{m} \\
>>>\end{align}$$
>>>Now we consider being under modulus $q$ we observe
>>>$$\begin{align}
>>> \frac{(q-r_{t}(q))^2}{qt} &= \frac{q^2}{qt} - \frac{2qr_{t}(q)}{qt} + \frac{r_{t}^2(q)}{q} \\
>>> &=\frac{q}{t} - \frac{2r_{t}(q)}{t} + \frac{r^{2}_{t}(q)}{q}
>>>\end{align}$$
>>>
>>> 
>>> $$\begin{align}
>>> (ct_{1} \cdot ct_{2})(\boldsymbol{s})&= (\boldsymbol{c_{0}}+\boldsymbol{c}_{1}\boldsymbol{s})(\boldsymbol{c_{0}}'+\boldsymbol{c}_{1}'\boldsymbol{s}) \\
>>> &= \underbrace{ \boldsymbol{c}_{0}\boldsymbol{c}_{0}' }_{ =\widehat{\boldsymbol{c}}_{0} } + \underbrace{ \boldsymbol{c}_{0}\boldsymbol{c}_{1}' }_{ =\widehat{\boldsymbol{c}}_{1} }\boldsymbol{s} + \underbrace{ \boldsymbol{c}_{1}\boldsymbol{c}_{1}' }_{ =\widehat{\boldsymbol{c}}_{2} } \boldsymbol{s}^2 \\
>>> &= \widehat{\boldsymbol{c}}_{0} + \widehat{\boldsymbol{c}}_{1}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{s}^2
>>>\end{align}$$
>>>which is a degree $2$ polynomial in $\boldsymbol{s}$.
>>
>>**<span style="color:#f7b8ff"><u>Relinearization:</u></span>** `Relin(hat_ct, rlk) -> ct_3`
>>
>>**<span style="color:#f7b8ff">Input</span>**
>> $$\begin{align}
>> \widehat{ct}&= (\widehat{\boldsymbol{c}}_{0}, \widehat{\boldsymbol{c}}_{1}, \widehat{\boldsymbol{c}}_{2}) \tag{From Multiplication} \\
>> rlk &= \Big[\Big([-(\boldsymbol{a}_{i} \cdot \boldsymbol{s}+ \boldsymbol{e}_{i})+T^i \cdot \boldsymbol{s}^2]_{q}, \boldsymbol{a}_{i}\Big)\Big]_{i=0}^l\tag{Version 1} \\
>> rlk &= \Big(\big[-(\boldsymbol{a} \cdot \boldsymbol{s} +  p \cdot \boldsymbol{s}^2)\big]_{p \cdot q}, \boldsymbol{a}\Big)\tag{Version 2}
>>\end{align}$$

I will provide you an estimate which deviates some from the author's estimation, but which is pretty close. Maybe this might be a good continuation point, or possibly there might be a typo in the paper as well. 

First of all, assume we have the following expression and wish to simplify it
$$\left[\left\lfloor  \frac{\left[a\right]_{pq}}{p}  \right\rceil \right]_{q}\tag{1}$$
for arbitrary $a,p \in \mathbb{Z}$.  WSeeing your question, I can see where things go wrong. Your assumption $\big[[\,\cdot\,]_{pq}\big]_q = [\,\cdot\,]_q$ holds true for the integers, but it fails on the rationals (MAYBE ADD SOME MORE INSIGHT HERE).e focus for now on the enumerator 
$$\frac{a \text{ mod } pq}{p}$$
which will be some element of the residue class $a$ with respect to $pq$ and can therefore be written as
$$a \text{ mod } pq = a +rpq$$
for some residue $r \in \mathbb{Z}$. Hence, we rewrite the given expression in $(1)$ as
$$\begin{align}
\left[\left\lfloor  \frac{\left[a\right]_{pq}}{p}  \right\rceil \right]_{q} &= \left[\left\lfloor \frac{a +rpq}{p}  \right\rceil \right]_{q}\\
&= \left[\left\lfloor \frac{a}{p} + rq  \right\rceil\right]_{q} \\
&= \left[\left\lfloor \frac{a}{p}   \right\rceil + rq\right]_{q} \\
&= \left[\left\lfloor \frac{a}{p}   \right\rceil \right]_{q} \tag{2}
\end{align}$$
Now, we continue to think about how to remove the rounding function from the expression by finding a suitable substitution. Thinking about how we can express $a$ with respect to the divisor $p$ in the division algorithm gives for some $k \in \mathbb{Z}$
$$a = pk +r'$$
with $\left\lceil  -\frac{p}{2}  \right\rceil  \leq r' < \left\lfloor  \frac{p}{2}  \right\rfloor$ where we reside in the symmetric residue system as you mentioned in your post. Note,
$$r' = a \text{ mod } p$$
Removing the residue yields an integer, such that we can remove the rounding to the closest integer, i.e.
$$a = pk +r' \iff a - \text{ mod } p = pk$$
with $pk \in \mathbb{Z}$. We can therefore now legally remove the rounding to the closest integer by substituting into equation $(2)$
$$\begin{align}
\left[\left\lfloor \frac{a}{p}   \right\rceil \right]_{q} &= \left[ \frac{a - a \text{ mod } p}{p} \right]_{q} \tag{3}
\end{align}$$
We will use this fact as template for the next computations on the ciphers. It is noteworthy, though we will work with polynomials, the computations we will work accordingly, because the rounding and modulus is concerned with the coefficients of the polynomials, which are integers/rationals. First, we consider
$$\begin{align}
\boldsymbol{c}_{2,0} &= \left[ \left\lfloor \frac{\widehat{\boldsymbol{c}}_{2} \cdot \texttt{rlk}[0]}{p} \right\rceil \right]_{q} \\
            &= \left[ \left\lfloor \frac{\widehat{\boldsymbol{c}}_{2} \cdot \big[- (\boldsymbol{a}\boldsymbol{s}+\boldsymbol{e})+p\boldsymbol{s}^2\big]_{pq}}{p} \right\rceil \right]_{q} \\
&=  \left[ \left\lfloor \frac{\widehat{\boldsymbol{c}}_{2} \cdot \big(- (\boldsymbol{a}\boldsymbol{s}+\boldsymbol{e})+p\boldsymbol{s}^2\big)}{p} \right\rceil \right]_{q}  \tag*{using (2)} \\
&= \left[ \left\lfloor \frac{ - (\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})+\widehat{\boldsymbol{c}}_{2}p\boldsymbol{s}^2}{p} \right\rceil \right]_{q} \\
&= \left[ -\left\lfloor \frac{  \widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e}}{p} \right\rceil +\widehat{\boldsymbol{c}}_{2}\boldsymbol{s}^2\right]_{q} \\
&= \left[  \frac{ - \Big((\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})-\big((\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})\text{ mod }p\big)\Big)}{p}  +\widehat{\boldsymbol{c}}_{2}\boldsymbol{s}^2\right]_{q} \tag*{using (3)}
\end{align}$$
and 
$$\begin{align}
\boldsymbol{c}_{2,1} &= \left[ \left\lfloor\frac{\widehat{\boldsymbol{c}}_{2} \cdot \texttt{rlk}[1]}{p}  \right\rceil \right]_{q} \\ 
            &= \left[ \left\lfloor \frac{\widehat{\boldsymbol{c}}_{2}  \boldsymbol{a}}{p} \right\rceil \right]_{q} \\
&= \left[  \frac{\widehat{\boldsymbol{c}}_{2}  \boldsymbol{a}-(\widehat{\boldsymbol{c}}_{2}  \boldsymbol{a} \text{ mod }p)}{p}  \right]_{q} \tag*{using (3)}
\end{align}$$
Using the definitions for the updated ciphers (note, you have a typo in your question, where you used $\widehat{\boldsymbol{c}}_2$ falsely in the updates), i.e.
$$\begin{align}
\boldsymbol{c}_{0}' &= \big[\widehat{\boldsymbol{c}}_0 + \boldsymbol{c}_{2,0}\big]_q \\
        \boldsymbol{c}_{1}' &= \big[\widehat{\boldsymbol{c}}_1 + \boldsymbol{c}_{2,1}\big]_q 
\end{align}$$
For the relinearized cipher we have without considering the $[\,\cdot\,]_{q}$ operator, since all elements are $\text{ mod }q$ and will be embedded in $\text{ mod } q$
$$\begin{align}
\boldsymbol{c}_{0}' + \boldsymbol{c}_{1}'\boldsymbol{s} &= \widehat{\boldsymbol{c}}_0 + \boldsymbol{c}_{2,0} + \big(\widehat{\boldsymbol{c}}_1 + \boldsymbol{c}_{2,1}\big)\boldsymbol{s} \\
&= \widehat{\boldsymbol{c}}_0 +  \frac{ - \Big((\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})-\big((\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})\text{ mod }p\big)\Big)}{p}  +\widehat{\boldsymbol{c}}_{2}\boldsymbol{s}^2 + \widehat{\boldsymbol{c}}_1\boldsymbol{s} + \left( \frac{\widehat{\boldsymbol{c}}_{2}  \boldsymbol{a}-(\widehat{\boldsymbol{c}}_{2}  \boldsymbol{a} \text{ mod }p)}{p}\right)\boldsymbol{s}  \\
&=\widehat{\boldsymbol{c}}_0 + \widehat{\boldsymbol{c}}_1\boldsymbol{s} + \widehat{\boldsymbol{c}}_{2}\boldsymbol{s}^2 + \frac{\cancel{ -\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s} }-\widehat{\boldsymbol{c}}_{2}\boldsymbol{e}+\big((\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})\text{ mod }p\big) + \cancel{ \widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s} }-(\widehat{\boldsymbol{c}}_{2}  \boldsymbol{a} \text{ mod }p)\boldsymbol{s}}{p} \\
&=\widehat{\boldsymbol{c}}_0 + \widehat{\boldsymbol{c}}_1\boldsymbol{s} + \widehat{\boldsymbol{c}}_{2}\boldsymbol{s}^2 - \underbrace{ \frac{-\widehat{\boldsymbol{c}}_{2}\boldsymbol{e}}{p} + \frac{(\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})\text{ mod }p}{p} - \frac{(\widehat{\boldsymbol{c}}_{2}  \boldsymbol{a} \text{ mod }p)\boldsymbol{s}}{p} }_{ \text{relinearisation error} }
\end{align}$$
We can now estimate the induced error. Note, when we $\text{ mod }p$ we get symmetric residues as already pointed out earlier, hence $\lvert\lvert [a]_{p} \rvert\rvert_{\infty}=\frac{p}{2}$
$$\begin{align}
\left\lvert \left\lvert  -  \frac{-\widehat{\boldsymbol{c}}_{2}\boldsymbol{e}}{p}  \right\rvert \right\rvert_{\infty} &=  \frac{\delta_{R}\cdot q \cdot B}{2p} \tag{4a}\\
\left\lvert \left\lvert  \frac{(\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})\text{ mod }p}{p}  \right\rvert \right\rvert_{\infty} &= \frac{\frac{p}{2}}{p}  \\
&= \frac{1}{2} \tag{4b} \\
\left\lvert \left\lvert  \frac{(\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\text{ mod }p)\boldsymbol{s}}{p}  \right\rvert \right\rvert_{\infty} &= \frac{\lvert\lvert s \rvert\rvert_{\infty}\delta_{R} }{2}  \tag{4c}
\end{align}$$
In $(4a)$ the cipher is sampled from $R_{q}$ with zero-symmetric coefficients. In $(4b)$ and $(4c)$ we need to consider polynomials bounded by the $\text{ mod }p$ operation, where the coefficients are again zero-symmetric with respect to $p$. Only in $(4c)$ we need to further consider that this reduced polynomial needs to be multiplied with $\boldsymbol{s}$ which induces the ring expansion factor $\delta_{R}$. Combining these terms, we get
$$\begin{align}
\left\lvert \left\lvert  \frac{-\widehat{\boldsymbol{c}}_{2}\boldsymbol{e}}{p} + \frac{(\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})\text{ mod }p}{p} - \frac{(\widehat{\boldsymbol{c}}_{2}  \boldsymbol{a} \text{ mod }p)\boldsymbol{s}}{p}  \right\rvert \right\rvert & \leq  \left\lvert \left\lvert  -  \frac{-\widehat{\boldsymbol{c}}_{2}\boldsymbol{e}}{p}  \right\rvert \right\rvert_{\infty}+ \left\lvert \left\lvert  \frac{(\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\boldsymbol{s}+\widehat{\boldsymbol{c}}_{2}\boldsymbol{e})\text{ mod }p}{p}  \right\rvert \right\rvert_{\infty} + \left\lvert \left\lvert  \frac{(\widehat{\boldsymbol{c}}_{2}\boldsymbol{a}\text{ mod }p)\boldsymbol{s}}{p}  \right\rvert \right\rvert_{\infty}  \\
&= \frac{\delta_{R}\cdot q \cdot B}{2p} + \frac{1}{2} +  \frac{\lvert\lvert s \rvert\rvert_{\infty}\delta_{R} }{2} \\
&= \frac{\delta_{R}\cdot q \cdot B}{2p} + \frac{1+\lvert\lvert s \rvert\rvert_{\infty}\delta_{R}}{2}
\end{align}$$
This is quite close to the bounds given by the authors. Though, it is not exactly the same term, you can see what how to apply the logic for these terms. 

Hope this helps.
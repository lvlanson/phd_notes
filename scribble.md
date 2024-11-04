# LWE
#### Preliminaries
Let $q \in \mathbb{N}$. Denote the integers modulo $q$ as $\mathbb{Z}_q:=\mathbb{Z}/q\mathbb{Z}$. For convenience, we set
$$q=2^{32}$$
We will use the **symmetric residue elements**, i.e.
$$\mathbb{Z}/q\mathbb{Z} = [-2^{31}, 2^{31})$$

#### LWE  Definitions
Let 
- $\boldsymbol{s} \in \mathbb{Z}_{q}^n$ be a vector of length $n$ with elements in $\mathbb{Z}_{q}$ **(Secret Vector)**
- $\boldsymbol{a}_{1},\dots, \boldsymbol{a}_{m} \in \mathbb{Z}_{q}^m$ be **random vectors**
- $e_{1}, \dots, e_{m} \in \mathbb{Z}_{q}$ be **noise** drawn from some distribution $\chi$ 
- $b_{i}=\boldsymbol{a}_{i}^T \boldsymbol{s} + e_{i}$ be the **noisy dot-product**

The general problem of LWE can be formulated as

---
Given  $m$ random vectors $\boldsymbol{a}_{1}, \dots, \boldsymbol{a}_{m}$ and the noisy dot products $b_{1}, \dots, \boldsymbol{b}_{m}$, is it possible to efficiently learn the secret vector $\boldsymbol{s}$?

---

#### The Noise Distribution
To create the errors, we draw real numbers from a **Gaussian distribution** $\mathcal{N}(0, \sigma)$ with $\sigma \ll 1$, such that
$$-\frac{1}{2} \leq x_{i} < \frac{1}{2}$$
Then
$$e = \left\lfloor  x \cdot \frac{q}{2}  \right\rfloor $$
The given distribution is denoted as $\mathcal{N}_{q}(0, \sigma)$. 

#### Typical Values
$$\begin{align}
q &= 2^{32} \\
n &= 500 \\
\sigma &= 2^{-20}
\end{align}$$

#### Building the Encryption Scheme
- Keygeneration:
	$$\boldsymbol{s} \in_{R} \{ 0,1 \}^n \subset \mathbb{Z}_{q}^n$$
	where $\in_{R}$ denotes random selection
- Encryption Function $$\text{Enc}_{\boldsymbol{s}}(m):=(\boldsymbol{a}, \boldsymbol{a}^T \boldsymbol{s} + m + e) \in \mathbb{Z}_{q}^n \times \mathbb{Z}_{q}$$
- Decryption Function $$\begin{align}
\text{Dec}_{\boldsymbol{s}}(\boldsymbol{a},b) &= b - \boldsymbol{a}^T \boldsymbol{s} \\
&= (\boldsymbol{a}^T\boldsymbol{s}+m+e) - \boldsymbol{a}^T \boldsymbol{s} \\
&= m+e
\end{align}$$
where we still need to remove the error by some method later described
	
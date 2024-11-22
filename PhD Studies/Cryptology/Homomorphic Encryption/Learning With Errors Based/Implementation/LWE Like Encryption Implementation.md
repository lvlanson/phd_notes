### Preliminaries

>[!summary] LWE Summary
>#### **<span style="color:#52dcda">Preliminaries</span>**
>Let $q \in \mathbb{N}$. Denote the integers modulo $q$ as $\mathbb{Z}_q:=\mathbb{Z}/q\mathbb{Z}$. For convenience, we set
>$$q=2^{32}$$
>We will use the **symmetric residue elements**, i.e.
>$$\mathbb{Z}/q\mathbb{Z} = [-2^{31}, 2^{31})$$
>
>>[!remark]- Security Assumption
>>Let 
>>- $\boldsymbol{s} \in \mathbb{Z}_{q}^n$ be a vector of length $n$ with elements in $\mathbb{Z}_{q}$ **(Secret Vector)**
>>- $(\boldsymbol{a}_{1},\dots, \boldsymbol{a}_{m})^T = \boldsymbol{A} \subset \mathbb{Z}_{q}^{m \times n}$ be **random vectors**
>>- $(e_{1}, \dots, e_{n})^T = \boldsymbol{e} \in \mathbb{Z}_{q}^n$ be **noise** drawn from some distribution $\chi$ 
>>- $b_{i}=\boldsymbol{a}_{i}^T \boldsymbol{s} + e_{i}$ be the **noisy dot-product**
>>
>>The general problem of LWE can be formulated as
>>$$\boldsymbol{b} = \boldsymbol{A}\boldsymbol{s} + \boldsymbol{e}$$
>>
>>---
>>Given  $n$ random vectors $\boldsymbol{a}_{1}, \dots, \boldsymbol{a}_{n}$ and the noisy dot products $b_{1}, \dots, b_{n}$, is it possible to efficiently learn the secret vector $\boldsymbol{s}$?
>>
>>---
>
>#### **<span style="color:#52dcda">LWE Definitions</span>**
>
>Let 
>- $m \in \mathbb{Z}_q = \mathcal{M}$ denote the message
>- $\mathcal{M}$ denote the message/plaintext space
>- $\boldsymbol{s} \in \mathbb{Z}_{q}^n$ be a random uniformly sampled vector of length $n$ with elements in $\mathbb{Z}_{q}$ **(Secret Vector)**
>- $\boldsymbol{a} = \boldsymbol{A} \subset \mathbb{Z}_{q}^{n}$ be **uniformly sampled random vector**
>- $(e_{1}, \dots, e_{n})^T = \boldsymbol{e} \in \mathbb{Z}_{q}^n$ be **noise** sampled from the Gaussian distrubtiuon $\mathcal{N}(0, \sigma)$ 
>- $C \in \mathcal{C}$ denote the ciphertext
>- $\mathcal{C}$ denote the ciphertext space
>
>
>#### **<span style="color:#52dcda">The Noise Distribution / Error Sampling</span>**
>To create the errors, we sample real numbers from a **Gaussian distribution** $\mathcal{N}(0, \sigma)$ with $\sigma \ll 1$, such that for a sampled $x_i \in_R \mathcal{N}(0, \sigma)$
>$$-\frac{1}{2} \leq x_{i} < \frac{1}{2}$$
>Then scaling the sample by $q$ we yield an error in $\mathbb{Z}_q$
>$$e = \left\lfloor  x_i \cdot \frac{q}{2}  \right\rfloor $$
>The given distribution is denoted as $\mathcal{N}_{q}(0, \sigma)$. 
>
>#### **<span style="color:#52dcda">Typical Values</span>**
>$$\begin{align}
>q &= 2^{32} \\
>n &= 500 \\
>\sigma &= 2^{-20}
>\end{align}$$
>
>#### **<span style="color:#52dcda">Building the Encryption Scheme</span>**
>- Keygeneration:
>	$$\boldsymbol{s} \in_{R} \{ 0,1 \}^n \subset \mathbb{Z}_{q}^n$$
>	where $\in_{R}$ denotes random selection
>- Encryption Function $$\text{Enc}_{\boldsymbol{s}}(m):=(\boldsymbol{a}, \boldsymbol{a}^T \boldsymbol{s} + m + e) \in \mathbb{Z}_{q}^n \times \mathbb{Z}_{q}$$
>- Decryption Function $$\begin{align}
>\text{Dec}_{\boldsymbol{s}}(\boldsymbol{a},b) &= b - \boldsymbol{a}^T \boldsymbol{s} \\
>&= (\boldsymbol{a}^T\boldsymbol{s}+m+e) - \boldsymbol{a}^T \boldsymbol{s} \\
>&= m+e
>\end{align}$$
>where we still need to remove the error by some method later described


### Implementing LWE

>[!algo] Algorithm Random Sampling Functions
>```python
>from typing import Optional
>import numpy as np
>
>INT32_MIN = np.iinfo(np.int32).min
>INT32_MAX = np.iinfo(np.int32).max
>
>def uniform_sample_int32(size: int) -> np.ndarray:
>    return np.random.randint(
>        low=INT32_MIN,
>        high=INT32_MAX + 1,
>        size=size,
>        dtype=np.int32,
>    )
>
>
>def gaussian_sample_int32(std: float, size: Optional[float]) -> np.ndarray:
>    return np.int32(INT32_MAX * np.random.normal(loc=0.0, scale=std, size=size))
>
>print(INT32_MIN)
>print(INT32_MAX)
>print(uniform_sample_int32(1))
>print(gaussian_sample_int32(0.01, 1))
>```

>[!remark] Implementation Preparation
>#### **<span style="color:#e9ffad">LweConfig</span>**
>```python
>LweConfig.dimension: int
>```
>refers to the dimensionality $n$ in the secret key $\boldsymbol{n} \in_R \{0,1\}^n \subset \mathbb{Z}^n_q$ 
>
>```python
>LweConfig.noise_std: float
>```
>refers to the standard deviation used for the normal distribution $\mathcal{N}_q(0,\sigma)$
>
>#### **<span style="color:#e9ffad">LwePlaintext</span>**
>```python
>LwePlaintext.message: np.int32
>``` 
>refers to the plaintext message to be encrypted
>
>#### **<span style="color:#e9ffad">LweCiphertext</span>**
>```python
>LweCiphertext.config: LweConfig
>```
>refers to the configuration of the LWE instance given above
>
>```python
>LweCiphertext.a: np.ndarray
>LWECiphertext.b: np.int32
>```
>refers to the ciphertext $C = (\boldsymbol{a}, b) \in C$ where 
>$$\begin{align}
>\boldsymbol{a} &\in_R \mathbb{Z}_q^n \\
>b &= \boldsymbol{a}^T \boldsymbol{s} + m + e
>\end{align}$$
>#### **<span style="color:#e9ffad">LweEncryptionKey</span>**
>```Python
>LweEncryptionKey.config: LweConfig
>```
>refers to the configuration of the LWE instance given above
>```python
>LweEncryptionKey.key: nd.array
>```
>refers to the uniformly randomly sampled key $\boldsymbol{s} \in_{R} \{ 0,1 \}^n \subset \mathbb{Z}_{q}^n$
>#### **<span style="color:#e9ffad">Encryption/Decryption Functions</span>**
>```python
>lwe_encrypt(plaintext: LwePlaintext, key: LweEncryptionKey) -> LweCiphertext:
>lwe_decrypt(ciphertext: LweCiphertext, key: LweEncryptionKey) -> LwePlaintext:
>```

>[!algo] Algorithm Datastructures
>```python
>import dataclasses
>import numpy as np
>
>@dataclasses.dataclass
>class LweConfig:
>    # Size of the LWE encryption key.
>    dimension: int
>
>    # Standard deviation of the encryption noise.
>    noise_std: float
>
>@dataclasses.dataclass
>class LwePlaintext:
>    message: np.int32
>
>
>@dataclasses.dataclass
>class LweCiphertext:
>    config: LweConfig
>    a: np.ndarray  # An int32 array of size config.dimension
>    b: np.int32
>
>
>@dataclasses.dataclass
>class LweEncryptionKey:
>    config: LweConfig
>    key: np.ndarray  # An int32 array of size config.dimension
>
>
>def generate_lwe_key(config: LweConfig) -> LweEncryptionKey:
>    return LweEncryptionKey(
>        config=config,
>        key=np.random.randint(
>            low=0, high=2, size=(config.dimension,), dtype=np.int32
>        ),
>    )
>
>
>def lwe_encrypt(
>    plaintext: LwePlaintext, key: LweEncryptionKey
>) -> LweCiphertext:
>    a = uniform_sample_int32(size=key.config.dimension)
>    noise = gaussian_sample_int32(std=key.config.noise_std, size=None)
>
>    # b = (a, key) + message + noise
>    b = np.add(np.dot(a, key.key), plaintext.message, dtype=np.int32)
>    b = np.add(b, noise, dtype=np.int32)
>
>    return LweCiphertext(config=key.config, a=a, b=b)
>
>
>def lwe_decrypt(
>    ciphertext: LweCiphertext, key: LweEncryptionKey
>) -> LwePlaintext:
>    return LwePlaintext(
>        np.subtract(ciphertext.b, np.dot(ciphertext.a, key.key), dtype=np.int32)
>    )
>    
>def lwe_encrypt(
>    plaintext: LwePlaintext, key: LweEncryptionKey
>) -> LweCiphertext:
>    a = utils.uniform_sample_int32(size=key.config.dimension)
>    noise = utils.gaussian_sample_int32(std=key.config.noise_std, size=None)
>
>    # b = (a, key) + message + noise
>    b = np.add(np.dot(a, key.key), plaintext.message, dtype=np.int32)
>    b = np.add(b, noise, dtype=np.int32)
>
>    return LweCiphertext(config=key.config, a=a, b=b)
>
>def lwe_decrypt(
>    ciphertext: LweCiphertext, key: LweEncryptionKey
>) -> LwePlaintext:
>    return LwePlaintext(
>        np.subtract(ciphertext.b, np.dot(ciphertext.a, key.key), dtype=np.int32)
>    )
>    ```

>[!remark] Implementation Message Encoding and Encryption/Decryption
>Consider the message space $\mathcal{M}=\mathbb{Z}_{8}=[-4,4)$. Our objective is to encode messages $m \in \mathbb{Z}_{8}$ such that when we put noise on it and evaluate circuits, that we can recover $m$ without the noise, i.e.
>$$m = \lfloor m+e \rceil $$
>conditioned on $\lvert e \rvert < \frac{1}{2}$. For this matter we **scale** the message space to $\mathbb{Z}_{q}$ with $q=2^{32}$ such that we yield the interval $[-2^{31},2^{31})$. We note that $8 = 2^3$, which means that we can use a scaling factor $\Delta=2^{29}$ to scale up the message space. Figure 1 is illustrating how the coefficients $i \in [-4,4) = \mathbb{Z}_{8}$ are scaled by $\Delta$, i.e.
>$$\begin{alignat}{2}
> &\text{Encode}:\mathbb{Z}_{8} &&\to \mathbb{Z}_{2^{32}} \\
> &\text{Encode}: m &&\mapsto 2^{29} \cdot m&
>\end{alignat}$$
>
>![[Figures/message_space.png|center|400]]
><center>Figure 1: Message Space with Errors</center>
>
>Note that Figure 1 illustrates with the bold purple curve around $3 \cdot 2^{29}$ where the arrow is allowed such that the decoding will yield back our original message. This illustration highlights why the noise must be bounded by $\lvert e \rvert < \frac{1}{2}\Delta$. Hence, decoding is given as
>$$\begin{alignat}{2}
>&\text{Decode}: \mathbb{Z}_{2^{32}} &&\to \mathbb{Z}_{8} \\
>&\text{Decode}: 2^{29} m+e &&\mapsto \lfloor 2^{29} m+e \rceil \tag{Example}\\
>&\text{Decode}: \Delta m+e &&\mapsto \lfloor \Delta m+e \rceil \tag{General}
>\end{alignat}$$

>[!algo] Encoding/Decoding Functions
>```python
>def encode(i: int) -> np.int32:
>    """Encode an integer in [-4, 4) as an int32"""
>    return np.multiply(i, 1 << 29, dtype=np.int32)
>
>def decode(i: np.int32) -> int:
>    """Decode an int32 to an integer in the range [-4, 4) mod 8"""
>    d = int(np.rint(i / (1 << 29)))
>    return ((d + 4) % 8) - 4
>
>def lwe_encode(i: int) -> LwePlaintext:
>    """Encode an integer in [-4,4) as an LWE plaintext."""
>    return LwePlaintext(encode(i))
>
>def lwe_decode(plaintext: LwePlaintext) -> int:
>    """Decode an LWE plaintext to an integer in [-4,4) mod 8."""
>    return decode(plaintext.message)
> ```

>[!remark] Instantiating an LWE Configuration

>[!algo] Algorithm Instantiation and Key Generation
>```python
># Lattice Estimator https://github.com/malb/lattice-estimator
>
>LWE_CONFIG = LweConfig(dimension=1024, noise_std=2**(-24))
>
># Generate an LWE key.
>key = generate_lwe_key(LWE_CONFIG)
>```

>[!summary] Homomorphic Addition
>Denote the encryption function with secret key $\boldsymbol{s} \in \mathbb{Z}_{q}^n$ as
>$$\begin{alignat}{2}
> &\text{LWE}_{\boldsymbol{s}}: (m, \boldsymbol{s}) &&\mapsto C \\
> &\text{LWE}_{\boldsymbol{s}}: \mathcal{M} \times \mathbb{Z}_{q} &&\to \mathcal{C}
>\end{alignat}$$
>we define the **<span style="color:#52dcda">homomorphic addition</span>** in LWE as
>$$\begin{alignat}{2}
>&\oplus: \Big((\boldsymbol{a}_{1}, b_{1}), (\boldsymbol{a}_{2}, b_{2})\Big)&&\mapsto (\boldsymbol{a}_{1} + \boldsymbol{a}_{2}, b_{1} + b_{2}) \\
>&\oplus:\text{LWE}_{\boldsymbol{s}} \times \text{LWE}_{\boldsymbol{s}} &&\to \text{LWE}_{\boldsymbol{s}} 
>\end{alignat}$$
>where we have the homomorphism for $m_{1}, m_{2} \in \mathcal{M}$
>$$\underbrace{ \text{LWE}_{\boldsymbol{s}}(m_{1}) }_{ =C_{1} } \oplus \underbrace{ \text{LWE}_{\boldsymbol{s}}(m_{2}) }_{ =C_{2} } = \underbrace{ \text{LWE}_{\boldsymbol{s}}(m_{1}+m_{2}) }_{ =C_{3} }$$
>>[!proof]
>>Let $\text{Dec}_{\boldsymbol{s}}$ denote the **decryption** function with secret key $\boldsymbol{s} \in \mathbb{Z}_{q}$.
>>$$\begin{align}
>> \text{Dec}_{\boldsymbol{s}}(C_{3})&= \text{Dec}_{\boldsymbol{s}}\Big((\boldsymbol{a}_{1}+\boldsymbol{a}_{2}, b_{1} + b_{2})\Big) \\
>> &= (b_{1}+b_{2}) - (\boldsymbol{a}_{1}+\boldsymbol{a}_{2})^T\boldsymbol{s} \\
>> &= (b_{1} -  \boldsymbol{a}_{1}^T\boldsymbol{s}) + (b_{2} - \boldsymbol{a}_{2}^T\boldsymbol{s}) \\
>> &= \text{Dec}_{\boldsymbol{s}}(C_{1}) + \text{Dec}_{\boldsymbol{s}}(C_{2}) \\
>> &= (m_{1}+e_{1}) + (m_{2}+ e_{2}) \\
>> &= (m_{1}+m_{2}) +  e_{3} \tag*{$\square$}
>>\end{align}$$
>
>>[!note]
>>Encryption only works correctly if
>>$$\lvert e_{1} + e_{2}\rvert < \frac{1}{2}\Delta$$
>
>>[!remark] Remark: Subtraction follows accordingly


>[!algo] Algorithm Homomorphic Addition and Subtraction
>```python
>def lwe_add(
>    ciphertext_left: LweCiphertext,
>    ciphertext_right: LweCiphertext) -> LweCiphertext:
>    """Homomorphic addition evaluation.
>
>       If ciphertext_left is an encryption of m_left and ciphertext_right is
>       an encryption of m_right then return an encryption of
>       m_left + m_right.
>    """
>    return LweCiphertext(
>        ciphertext_left.config,
>        np.add(ciphertext_left.a, ciphertext_right.a, dtype=np.int32),
>        np.add(ciphertext_left.b, ciphertext_right.b, dtype=np.int32))
>
>def lwe_subtract(
>    ciphertext_left: LweCiphertext,
>    ciphertext_right: LweCiphertext) -> LweCiphertext:
>    """Homomorphic subtraction evaluation.
>
>       If ciphertext_left is an encryption of m_left and ciphertext_right is
>       an encryption of m_right then return an encryption of
>       m_left - m_right.
>    """
>    return LweCiphertext(
>        ciphertext_left.config,
>        np.subtract(ciphertext_left.a, ciphertext_right.a, dtype=np.int32),
>        np.subtract(ciphertext_left.b, ciphertext_right.b, dtype=np.int32))
>```

>[!summary] Homomorphic Multiplication By Plaintext

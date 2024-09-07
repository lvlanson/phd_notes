
>[!note] Note: Interesting Facts
>>[!abstract] Quelle: ([[../../../../PDFs/marcolla2022.pdf|marcolla2022]])
>> - firstly described by Rivest, Adleman and Dertouzos in 1978 when asymmetric encryption was firstly introduced ([[../../../../PDFs/rivest1978a.pdf|rivest1978a]])
>> - firstly achieved by Gentry in 2009 ([[../../../../PDFs/gentry2009.pdf|gentry2009]])
>> - Applications:
>> 	- machine learning
>> 	- cloud computing
>> - there have been **homomorphic Encryption with limited number/type of operations**:
>> 	- RSA
>> 	- Goldwasser und Micali
>> 	- El Gamal
>> 	- Benaloh
>> 	- Naccache and Stern
>> 	- Paillier and Boneh
>> 	- Goh and Nissim (arbitrary number additions -> one multiplication -> arbitrary number additions)
>> - the paper of [[../../../../PDFs/armknecht2015a.pdf|armknecht2015a]] gives a good summary of the terminology defined in a comprehensive manner


### 1 - Terminology and Classification of Homomorphic Encryption Schemes 

#### 1.1 Terminology

>[!def] Definition Circuit ([[../../../../PDFs/armknecht2015a.pdf#page=10|Source]])
>A circuit $C \in \mathcal{C}$ is a boolean representation of a function $f \in \mathcal{F}$

^0b9560


>[!def] Definition $\mathcal{C}$-Evaluation Scheme ([[../../../../PDFs/armknecht2015a.pdf#page=10|Source]])
> Let $\mathcal{C}$ be a set of [[#^0b9560|circuits]]. A $\mathcal{C}$-Evaluation scheme for $\mathcal{C}$ is a tuple of probabilistic polynomial-time algorithms $(\text{Gen, Enc, Eval, Dec})$ such that:
> - $\text{Gen}(1^\lambda, \alpha)$: 
> 	- key generation algorithm, where $\lambda \in \mathbb{N}$ is the security parameter and $\alpha \in \mathcal{A}$ the auxiliary parameter 
> 	- output is the triple key pair $(sk,pk,evk)$.
> 	- $sk \in \mathcal{K}_{sk}$ is the secret key
> 	- $pk \in \mathcal{K}_{pk}$ is the public key
> 	- $evk \in \mathcal{K}_{evk}$ is the evaluation key
> 		- the secret key and evaluation key can be the same, depending on the scheme
> - $\text{Enc}(pk,m)$: 
> 	- encryption algorithm with encryption key $pk \in \mathcal{K}_{p}$ and plaintext $m \in \mathcal{P}$. 
> 	- output is the ciphertext $c \in \mathcal{C}$ 
> - $\text{Eval}(evk, C, c_{1}, \dots, c_{n})$:
> 	- evaluation algorithm with inputs $evk \in \mathcal{K}_{evk}$ evaluation key, $C \in \mathcal{C}$ a circuit and a mix of ciphertexts and evaluation results $c_{1},\dots,c_{n} \in \mathcal{Z}^*$
> 		- $\mathcal{Z}$ denotes the space of ciphertexts and evaluation outputs, with $\mathcal{X}$ being the ciphertext space and $\mathcal{Y}$ the space of evaluation outputs
> 		- $\mathcal{Z}^*$ denotes the space of arbitrary length tuples of elements in $\mathcal{Z}$
> 	- output is an evaluation $c_{i} \in \mathcal{Y}$
> - $\text{Dec}(sk, c)$:
> 	- decryption algorithm with input decryption key $sk \in \mathcal{K}_{sk}$ and ciphertext or evaluation output $c \in \mathcal{Z}$
> 
> In summary:
> $$\begin{alignat}{2}
> \text{Gen}&: \mathbb{N} \times \mathcal{A}&&\to \mathcal{K}_{p} \times\mathcal{K}_{s}\times\mathcal{K}_{e} \\
> \text{Enc}&: \mathcal{K}_{p} \times \mathcal{P}&&\to \mathcal{X} \\
> \text{Dec}&: \mathcal{K}_{s} \times \mathcal{Z}&&\to \mathcal{P} \\
> \text{Eval}&: \mathcal{K}_{e} \times \mathcal{C} \times \mathcal{Z}^* &&\to \mathcal{Y}
>\end{alignat}$$
>with $\mathcal{Z} = \mathcal{X} \cup \mathcal{Y}$

>[!def] Definition Correct Decryption ([[../../../../PDFs/armknecht2015a.pdf#page=12|Source]])
>A $\mathcal{C}$-evaluation scheme $(\text{Gen, Enc, Dec, Eval})$ is said to **correctly decrypt** if $\forall m \in \mathcal{P}$
>$$P\Big(\text{Dec}\big(sk, \text{Enc}(pk,m)\big)=m\Big) = 1$$

^00ba5e

>[!def] Definition Correct Evaluation ([[../../../../PDFs/armknecht2015a.pdf#page=12|Source]])
>A $\mathcal{C}$-evaluation scheme $(\text{Gen, Enc, Dec, Eval})$ correctly evaluates all circuits in $\mathcal{C}$ if for all $\forall c_{i} \in \mathcal{X}$, $\forall C \in \mathcal{C}$ and some [[../Learning With Errors Based/1 - Learning With Errors Introduction#^548cd0|negligible function]] $\varepsilon$
>$$P\Big(\text{Dec}\big(sk, \text{Eval}(evk, C, c_{1}, \dots, c_{n})=C(m_{1}, \dots, m_{n})\big)\Big)= 1- \varepsilon(\lambda)$$

^b78a8d

>[!remark] Remark: Correctness of $\mathcal{C}$-evalutation schemes
>A $\mathcal{C}$-evalutation scheme $(\text{Gen, Enc, Dec, Eval})$ is correct if its [[#^00ba5e|Decryption]] and [[#^b78a8d|Evaluation]] is correct.

>[!def] Definition Compactness ([[../../../../PDFs/armknecht2015a.pdf#page=12|Source]])
> A $\mathcal{C}$-evalutation scheme $(\text{Gen, Enc, Dec, Eval})$ is said to be compact if there is a polynomial $p$, such that for any key-triple $(sk,pk,evk)$, any circuit $C \in \mathcal{C}$ and all ciphertexts $c_{i} \in \mathcal{X}$, **the size of the output** $\text{Eval}(evk, C, c_{1}, \dots, c_{n})$ is not more than $p(\lambda)$ bits, independent of the size of the circuits.
> 
>>[!remark]
>>The ciphertext does not grow much through homomorphic operations and is only dependent on the security parameter $\lambda$.

>[!def] Definition Circuit Privacy ([[../../../../PDFs/armknecht2015a.pdf#page=13|Source]])
>
> A $\mathcal{C}$-evalutation scheme $(\text{Gen, Enc, Dec, Eval})$ is called **perfectly, statistically, computationally circuit private** if for any key-triple $(sk,pk,evk)$ for all circuits $C \in \mathcal{C}$ and all $c_{i} \in X$, the two distributions on $\mathcal{Z} = \mathcal{X} \cup \mathcal{Y}$
> $$D_{1} = \text{Eval}(evk, C, c_{1},\dots,c_{n})$$
> and
> $$D_{2}= \text{Enc}\Big(pk, C(m_{1},\dots,m_{n}) \Big)$$
> both taken over randomness of each algorithm, are *perfectly, statistically or computationally indistinguishable*, respectively.
>>[!remark]
>> Note, $D_{1}$ is a distribution over the ciphertext space and $D_{2}$ is a distribution over the plaintext space. Circuit privacy implies that these spaces are statistically indistinguishable when circuits are calculated over ciphertexts and plaintexts.

#### 1.2 Classification of Homomorphic Encryption Schemes

>[!def] Definition Somewhat Homomorphic Encryption Scheme ([[../../../../PDFs/armknecht2015a.pdf#page=14|Source]])
>A $\mathcal{C}$-evalutation scheme $(\text{Gen, Enc, Dec, Eval})$ that has correct decryption and correct evaluation is called **somewhat homomorphic encryption scheme (SHE)**
>>[!remark]
>>- SHEs don't need to be compact, hence ciphertexts can grow substantialy
>>- SHEs don't need to cover all operations, hence circuits can have limited sets of operations

>[!def] Definition Levelled Homomorphic Encryption Scheme ([[../../../../PDFs/armknecht2015a.pdf#page=14|Source]])
> A $\mathcal{C}$-evalutation scheme $(\text{Gen, Enc, Dec, Eval})$ is called a **levelled homomorphic scheme** if it takes an auxiliary input $\alpha=d$ to the function $\text{Gen}$ which specifies the **maximum depth of circuits** that can be evaluated. Further requirements are **correctness, compactness** and that **the length of the evaluation output does not depend on** $d$.

^5f3338

>[!def] Definition Fully Homomorphic Encryption Scheme ([[../../../../PDFs/armknecht2015a.pdf#page=14|Source]])
>  A **fully homomorphic** encryption scheme is a $\mathcal{C}$-evalutation scheme $(\text{Gen, Enc, Dec, Eval})$ that is compact, correct and where $\mathcal{C}$ is the **set of all circuits**.
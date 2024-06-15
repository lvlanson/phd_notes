>[!def] Definition Homomorphism ([[../../../../PDFs/nita2023.pdf#page=38|Source]])
>A function $f: A \to B$ is referred to as **homomorphism** if 
>$$f(x_{1} \circ x_{2})= f(x_{1})*f(x_{2}) \tag*{$\forall x_{1}, x_{2} \in A$}$$
>where $\circ$ is a binary operation on $A$, $*$ is a binary operation on $B$ and $A,B$ are algebraic structures of the same signature (groups, rings, fields). 

>[!def] Definition Homomorphic Encryption Scheme ([[../../../../PDFs/nita2023.pdf#page=38|Source]])
>A **homomorphic encryption scheme** $\mathcal{E}$ consists of a tuple of four probabilistic polynomial-time algorithms $$\mathcal{E} = (\text{KeyGeneration, Encryption, Decryption, Evaluation})$$ with
>- $\text{KeyGeneration}(\lambda, 1^\tau)\to(k_{s}, k_{p})$: 
>	- $\lambda$ - security parameter
>	- $\tau$ - functionality parameter
>	- $k_{s}$ - secret/private key
>	- $k_{p}$ - public key
>- $\text{Encryption}(m, k_{p})\to c$:
>	- $m \in \{ 0,1 \}$ - plain bit message 
>	- $k_{p}$ - public key
>	- $c \in \{ 0,1 \}$ - cipher text
>- $\text{Decryption}(c, k_{s}) \to m$:
>	- $c \in \{ 0,1 \}$ - cipher text
>	- $k_{s}$ - secret key
>	- $m \in \{ 0,1 \}$ - plain bit message
>- $\text{Evaluate}(k_{p}, \pi, \mathbf{v}) \to \mathbf{v}'$
>	- $k_{p}$ - public key
>	- $\pi$ - circuit
>	- $\mathbf{v}$ - vector of encrypted texts $\mathbf{v}=(v_{1}, v_{2}, \dots, v_{z})$ where $\pi$ has $z$ **entrance bits**
>	- $\mathbf{v}'$ - vector of encrypted texts $\mathbf{v}'=(v_{1}', v_{2}', \dots, v_{t}')$ where $\pi$ has $t$ **exit bits**

>[!terminology]
> - Fresh Ciphertexts - produced by the $\text{Encryption}$ algorithm
> - Evaluated Ciphertexts - produced by the $\text{Evaluation}$ algorithm
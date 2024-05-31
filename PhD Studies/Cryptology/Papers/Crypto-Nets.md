![[../../../References/@xie2014|@xie2014]]

>[!terminology] 
> - Circuit - describes the algorithmic computation steps to perform encryption and decryption. Therefore it is considered to have different elements such as _input nodes, logic gates and output nodes_. This is a consequence of the research of [[../../../PDFs/rivest1978.pdf|rivest1978]] who has considered solutions in hardware design and homomorphic encryption.

>[!def] Definition Homomorphic Encryption Scheme
>A homomorphic encryption scheme consists of the following parts:
>- $k$ - key
>- $E$ and $E_k$ - encryption function with and without key $k$ (algorithm)
>- $D$ and $D_k$ - decryption function with and without key $k$ (algorithm)
>- $\bigoplus$ - addition (algorithm)
>- $\bigotimes$ - multiplication (algorithm)
>
>Let $m_{1},m_{2} \in \mathbb{Z}$ be messages, then the algorithms have the following properties
>1. given $c_1=E_{k}(m_{1})$, it is computationally infeasible to compute $m_{1}$ without the private key $k$  
>2. it holds $$m_{1}=D_{k}(E_{k}(m_{1}))$$
>3. it holds $$m_{1} + m_{2} = D_{k}(E_{k}(m_{1}) \oplus E_{k}(m_{2}))$$
>4. it holds $$m_{1} \cdot m_{2} = D_{k}(E_{k}(m_{1}) \otimes E_{k}(m_{2}))$$
>
>>[!note]
>>The operations $\oplus, \otimes$ do not use the key $k$ to establish the identity.

>[!remark]
>RSA and El Gamal encryption schemes are _Partial Homomorphic Encryption_ (PHE) schemes
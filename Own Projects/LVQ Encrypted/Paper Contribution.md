Since FHE encryption schemes fundamentally only allow addition and multiplication operations and LVQ requires additional operations such as a \textit{less than} $LT$ and an \textit{equality} relational function $EQ$, we have to methods on how to compute these functions in encrypted space with the supported FHE operations. Such functions can be constructed using Lagrange's interpolation lemma, where we can represent these functions by a polynomial yielding the expected outputs. The behavior of the \textit{equality} function can be given as for some $a,b \in S = [0,p-1]$, where $S$ is a totally ordered set 
$$EQ_{S}(a,b)=\begin{cases}
1 & \text{ if } a = b \\
0 & \text{ if } a \neq b
\end{cases}$$
a realization of $LT$ is given by \cite[LQ-EQ]. Let $a,b \in S$ evaluated over $\mathbb{F}_{p}$ being a finite field over the prime number $p$, then 
$$EQ_{S}(a,b)\equiv1-(a-b)^{p-1} \;\;(\text{mod } p)$$
The \textit{less than} can be characterized as
$$LT_{S}(a,b)=\begin{cases}
1 & \text{ if } a < b \\
0 & \text{ if } a \geq b
\end{cases}$$
The authors of \cite[LQ-EQ] give a computationally optimized interpolation. We get the polynomial
$$Q_{LT_{S}}(X,Y)=$$


So to perform comparison in encrypted space we bound some integer $a \in \mathbb{Z}$ by a prime number $a < p$ and encode $a \in \mathbb{Z}_p$ as a polynomial $\mathbb{Z}_{p}[X]$. The encoding will be accomplished using a digitwise $2$-adic representation of $a$ as a polynomial. To compare polynomials embedded in $\mathbb{Z}_{p}[X]$, which can be encrypted by some polynomial based FHE, we compare the digitwise representation, such that some digit $a_{i}<b_{i}$ for some polynomial representation of $b \in \mathbb{Z}_{p}$.
---
aliases:
- eigenvector
- eigenvectors
- eigenvalue
- eigenvalues
---
>[!source]
![[../../../References/@kwak2004|Linear Algebra Book]]

>[!def] Definition Eigenvectors and Eigenvalues ([[../../../PDFs/kwak2004.pdf#page=213|Source]])
> Let $A$ be a $n \times n$ square matrix. A nonzero vector $\mathbf{x}$ in the $n$-space $\mathbb{R}^n$ is called an <u>eigenvector</u> (or <u>characteristic vector</u>) of $A$ if there is a scalar $\lambda$ in $\mathbb{R}$ such that 
> $$A\mathbf{x} = \lambda\mathbf{x}$$
> The scalar $\lambda$ is called an <u>eigenvalue</u> (or <u>characteristic value</u>) of $A$, and we say $\mathbf{x}$ belongs to $\lambda$.

>[!note]
>The subspace $W$ spanned by $\mathbf{x}$ is invariant under the linear transformation $A: \mathbb{R}^n \rightarrow \mathbb{R}^n$.
>```tikz
>\begin{document}
>\begin{tikzpicture}[>=stealth, scale=1.5]
>\draw[draw=none] (0,-5) rectangle (3,10); %create a bounding box to reserve space
>\begin{pgflowlevelscope}{\pgftransformscale{2}}
>% Draw grid
>\draw[step=1, gray, thin] (-2,-2) grid (4,4);
>
>% Draw axes
>\draw[->, thick] (-2.2,0) -- (4.2,0) node[right] {$x_1$};
>\draw[->, thick] (0,-2.2) -- (0,4.2) node[above] {$x_2$};
>\draw[->, thick] (0, 0) -- (1,2) node[above, xshift=-1em] {$\mathbf{x}$};
>\draw[dotted,thick] (-1,-2) --node[above, xshift=3em, yshift=7em]{$W$} (2,4);
>\node[text centered, text width=0.22\textwidth, fill=white, draw=black](r) at (3,3.5){$\mathbf{x}$ is eigenvector, s.t. $A\mathbf{x} = \lambda\mathbf{x}$};
>% Label axes ticks
>\foreach \x in {-2,-1,1,2,3,4}
>    \draw (\x,0.1) -- (\x,-0.1) node[below] {$\x$};
>\foreach \y in {-2,-1,1,2,3,4}
>    \draw (0.1,\y) -- (-0.1,\y) node[left] {$\y$};
>\end{pgflowlevelscope}
>\end{tikzpicture}
>\end{document}
>```

>[!note]
> The eigenvectors and eigenvalues can be determined solving the homogeneous system of 
> $$(\lambda I -A)\mathbf{x} = \mathbf{0}$$
> Solving the <u>characteristic equation</u> 
> $$ \det (\lambda I -A)= \mathbf{0}$$
> yields the <u>characteristic polynomial</u> of degree $n$. Each eigenvalue $\lambda$ is a root of the characteristic polynomial.

>[!theorem] Theorem ([[../../../PDFs/kwak2004.pdf#page=214|Source]])
>For any square matrix $A$, the following statements are equivalent
>1) $\lambda$ is an eigenvalue of $A$
>2) $\det(\lambda I - A) = 0$
>3) $\lambda I - A$ is singular
>4) the homogeneous system $(\lambda I - A)\mathbf{x} = \mathbf{0}$ has a nontrivial solution

>[!lemma] Lemma ([[../../../PDFs/kwak2004.pdf#page=217|Source]])
> 1) If $A$ is a triangular matrix, then the diagonal entries are exactly the eigenvalues of $A$.
> 2) if $A$ and $B$ are square matrices similar to each other, then they have the same characteristic polynomial.
>
>>[!proof]
>>1)
>>The upper triangular matrix can be given as
>>$$A = \begin{pmatrix}a_{11} &a_{12} & \ldots & a_{1n}\\ 
>>					    0 &a_{22}   &\ldots & a_{2n}\\ 
>>					    \vdots & \vdots & \ddots & \vdots \\
>>					    0 & 0 & \ldots & a_{nn}\end{pmatrix}$$
>>Then the characteristic equation can be given as 
>>$$\begin{align}\det (\lambda I - A) &= \begin{pmatrix}\lambda - a_{11} &-a_{12} & \ldots & -a_{1n}\\ 
>>					    0 &\lambda - a_{22}   &\ldots & -a_{2n}\\ 
>>					    \vdots & \vdots & \ddots & \vdots \\
>>					    0 & 0 & \ldots & \lambda - a_{nn}\end{pmatrix}\\
>>					    &=(\lambda - a_{11}) \dots(\lambda - a_{nn}) \\
>>					    &= 0\end{align}$$
>>
>> 2) Since there exists a nonsingular matrix $Q$ such that $B=Q^{-1}AQ$
>> $$\begin{align} \det (\lambda I - B) &= \det\left(Q^{-1}(\lambda I)Q - Q^{-1}AQ\right) \\
>> &=\det\left(Q^{-1}(\lambda I - A)Q \right) \\
>> &=\det Q^{-1} \det\left(\lambda I - A) \right)\det Q \\
>> &=\det\left(\lambda I - A) \right)\end{align}$$
>>>[!note]-
>>>Used properties
>>>1) $\det(AB) = \det(A)\det(B)$
>>>2) $\det(A)\det(A^{-1}) = 1$

>[!observation]
> Let $\mathbf{x}$ be an eigenvector to $B$ with eigenvalue $\lambda$, i.e. $B\mathbf{x}=\lambda \mathbf{x}$ and $Q$ a non-singular matrix with same dimensions as $B$. 
> $$\begin{align}B &= Q^{-1}AQ \\
> QB &= AQ \\
> QB\mathbf{x} &= AQ\mathbf{x} \\
> Q\lambda\mathbf{x} &= AQ\mathbf{x} \\
> \lambda Q\mathbf{x} &= AQ\mathbf{x} 
> \end{align}$$
> Hence, $Q \mathbf{x}$ must be an eigenvector of $A$.

>[!Theorem] Theorem ([[../../../PDFs/kwak2004.pdf#page=217|Source]])
>1) $\det A = \lambda_1 \lambda_2 \dots \lambda_n$
>2) $\text{tr}(A) = \lambda_1 + \lambda_2 + \dots + \lambda_n$
>
>>[!proof]
>>1. The eigenvalues $\lambda_1, \ldots, \lambda_n$ are the roots to the characteristic polynomial
>> $$\det(\lambda I - A) = (\lambda - \lambda_1)(\lambda - \lambda_2) \dots (\lambda - \lambda_n)$$
>> Setting $\lambda=0$ yields
>> $$\begin{align}
>> (-1)^n\det A &= (-1)^n \lambda_1 \lambda_2 \dots \lambda_n \\
>> \det A &= \lambda_1 \lambda_2 \dots \lambda_n
>> \end{align}$$
>> 2. $\;$ 
>> $$ \begin{align}
>>  \det( A - \lambda I) &= \det \begin{pmatrix} a_{11} - \lambda & a_{12} & \ldots & a_{1n}\\ 
>>					    a_{21} &a_{22} - \lambda  &\ldots & a_{2n}\\ 
>>					    \vdots & \vdots & \ddots & \vdots \\
>>					    a_{n1} & a_{n2} & \ldots & a_{nn} - \lambda \end{pmatrix}\\
>>					    &=(\lambda_1 - \lambda) \dots(\lambda_n - \lambda) \\
>>					    &= (-1)^n\left(\lambda^n + c_1\lambda^{(n-1)} + c_2\lambda^{(n-2)} + \dots + c_n\right)
>>	\end{align}
>>  $$
>> Note $c_1 = \text{Tr}(A) = \sum_{i=1}^n a_{nn}$ because in $\det A$ we multiply $\lambda^{n-1}$ with 
>> (FINISH THIS PROOF)


### Diagonalization of Matrices

>[!def] Definition Diagonalizable Matrices ([[../../../PDFs/kwak2004.pdf#page=219|Source]])
> A square matrix $A$ is said to be **diagonizable** if there exists an invertible matrix $Q$ such that 
> $$Q^{-1}AQ$$
> is a diagonal matrix, i.e. $A$ is similar to a diagonal matrix

^3b9ec0

>[!theorem] Diagonalization Theorem I ([[../../../PDFs/kwak2004.pdf#page=220|Source]])
>Let $A$ be a $n \times n$ matrix. Then $A$ is diagonizable if and only if $A$ has $n$ linearly independent eigenvectors.
>>[!proof]-
>>> $A$ diagonizable $\implies$ $A$ has $n$ linearly independent eigenvectors
>>
>>Suppose $A$ is diagonizable, by the [[#^3b9ec0| diagonalization definition]] we know
>>$$\begin{align}
Q^{-1}AQ &= \begin{bmatrix}
>> \lambda_{1} &0 &\dots &0 \\
>> 0 &\lambda_{2} & \dots & 0 \\
>> \vdots & \vdots & \ddots & \vdots \\ 
>> 0 & 0 & \dots & \lambda_{n} \\
>>\end{bmatrix} \\
>>&= D 
>>\end{align}$$
>>This is equivalent to
>>$$AQ = QD$$
>>Note
>>$$\begin{align}
>> AQ = [A\mathbf{x}_{1}, A\mathbf{x}_{2}, \dots, A\mathbf{x}_{n}] \\
>> QD = [\lambda_{1}\mathbf{x}_{1}, \lambda\mathbf{x}_{2}, \dots, \lambda\mathbf{x}_{n}]
>>\end{align}$$
>>implies that
>>$$A\mathbf{x}_{i} = \lambda_{i}\mathbf{x}_{i}$$
>>for $i = 1, \dots, n$. Further note, since $Q$ is invertible, their column vectors are nonzero and linearly independent
>>>[!note]
>>>1. If $Q$ had a zero column vector the definition of the inverse would not hold $$Q^{-1}Q = QQ^{-1} = I$$
>>>2. Since the inverse exist, then $Q$ must be a bijection. This is only possible if the column vectors are linearly independent
>>
>>Hence, the $\mathbf{x}_{i}$ are linearly independent eigenvectors of $A$.
>>>$A$ diagonizable $\Longleftarrow$ $A$ has $n$ linearly independent eigenvectors
>> Assuming $A$ has $n$ linearly eigenvectors $\mathbf{x}_{1}\dots \mathbf{x}_{n}$ with eigenvalues $\lambda_{1},\dots, \lambda_{n}$ such that
>> $$A \mathbf{x}_{i}= \lambda_{i}\mathbf{x}_{i}$$
>> We can define
>> $$Q = [\mathbf{x}_{1}, \dots, \mathbf{x}_{n}]$$
>> and therefore construct 
>> $$AQ = QD$$
>> with $D$ being the diagonal matrix of the eigenvalues of $A$. Since the column vectors are assumed to be linearly independent, we are allowed to write
>> $$Q^{-1}AQ=A$$

^a0a687

>[!theorem] Diagonalization Theorem II  ([[../../../PDFs/kwak2004.pdf#page=223|Source]])
>If an $n \times n$ matrix $A$ has $n$ distinct eigenvalues, then $A$ is diagonalizable.
>>[!remark]
>>The proof follows from the fact, that if we have $n$ distinct eigenvalues, we also have $n$ distinct eigenvectors which form a basis for $\mathbb{R}^n$ and therefore is a bijection and lastly therefore is invertible

^431403

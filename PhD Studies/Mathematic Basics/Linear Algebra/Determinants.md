---
aliases: 
- determinants
- determinant
---

>[!def] Properties of Determinants
> A real-valued function $f: M_{n\times n}(\mathbb{R}) \rightarrow \mathbb{R}$  of all $n \times n$ square matrices is called a <u>determinant</u> if it satisfies
> 1) $f(I_{n}) = 1$ with $I_n$ being the $n \times n$ identity matrix
> 2) If two rows are interchanged, the sign of $f$ changes
> 3) $f$ is linear in the first row, i.e.
> $$f\left(\begin{matrix}k \mathbf{r}_1 + l \hat{\mathbf{r}}_1 \\ \mathbf{r}_2 \\ \vdots \\ \mathbf{r}_n\end{matrix} \right) = kf\left(\begin{matrix}\mathbf{r}_1 \\ \mathbf{r}_2 \\ \vdots \\ \mathbf{r}_n\end{matrix}\right) + lf\left(\begin{matrix}\hat{\mathbf{r}}_1 \\ \mathbf{r}_2 \\ \vdots \\ \mathbf{r}_n\end{matrix}\right)$$
>>[!note]-
>>$f$ is linear in every row


>[!note] Deriving the formula for $2\times 2$ matrices
> Let $A = \begin{pmatrix}a & b \\ c & d \end{pmatrix}$
> $$\begin{alignat}{1} 
> \det A &= \begin{vmatrix}a & b \\ c & d \end{vmatrix} & \\
> &= \begin{vmatrix}a & 0 \\ c & d \end{vmatrix} + \begin{vmatrix}0 & b \\ c & d \end{vmatrix}  \tag{3 - Linearity} \\
> &=\underbrace{\cancel{\begin{vmatrix}a & 0 \\ c & 0 \end{vmatrix}}}_{=0} + \begin{vmatrix}a & 0 \\ 0 & d \end{vmatrix} + \underbrace{\cancel{\begin{vmatrix}0 & b \\ 0 & d \end{vmatrix}}}_{=0} + \begin{vmatrix}0 & b \\ c & 0 \end{vmatrix}  \tag{3 - Linearity} \\
> &= \begin{vmatrix}a & 0 \\ 0 & d \end{vmatrix} + \begin{vmatrix}0 & b \\ c & 0 \end{vmatrix} \\
> &= \begin{vmatrix}a & 0 \\ 0 & d \end{vmatrix} - \begin{vmatrix}c & 0 \\ 0 & b \end{vmatrix} \tag{2 - Row Change} \\
> &= ad\begin{vmatrix}1 & 0 \\ 0 & 1 \end{vmatrix} -bc \begin{vmatrix}1 & 0 \\ 0 & 1 \end{vmatrix} \tag{3 - Linearity} \\
> &= ad -bc \tag{1 - Identity} 
> \end{alignat}$$

>[!note] Deriving the formula for $3\times 3$ matrices
> Let $A = \begin{pmatrix}a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{pmatrix}$
> $$\begin{alignat}{2}
> \det A = &\begin{vmatrix}a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33}\end{vmatrix} \\
> \\
> = &\begin{vmatrix}a_{11} & 0 & 0 \\ 0 & a_{22} & 0 \\ 0 & 0 & a_{33} \end{vmatrix} + \begin{vmatrix}0 & a_{12} & 0 \\ 0 & 0 & a_{23} \\ a_{31} & 0 & 0 \end{vmatrix} +\begin{vmatrix}0 & 0 & a_{13} \\ a_{21} & 0 & 0 \\ 0 & a_{32} & 0 \end{vmatrix} \\
> + &\begin{vmatrix}0 & 0 & a_{13} \\ 0 & a_{22} & 0 \\ a_{31} & 0 & 0 \end{vmatrix}
> + \begin{vmatrix}a_{11} & 0 & 0 \\ 0 & 0 & a_{23} \\ 0 & a_{32} & 0 \end{vmatrix}
> + \begin{vmatrix}0 & a_{12} & 0 \\ a_{21} & 0 & 0 \\ 0 & 0 & a_{33} \end{vmatrix} \\
> \\
> =& \begin{vmatrix}a_{11} & 0 & 0 \\ 0 & a_{22} & 0 \\ 0 & 0 & a_{33} \end{vmatrix} + \begin{vmatrix}a_{31} & 0 & 0 \\ 0 & a_{12} & 0 \\ 0 & 0 & a_{23} \end{vmatrix} +\begin{vmatrix}a_{21} & 0 & 0 \\ 0 & a_{32} & 0 \\ 0 & 0 & a_{13} \end{vmatrix} \\
> - &\begin{vmatrix}a_{31} & 0 & 0\\ 0 & a_{22} & 0 \\ 0 & 0 & a_{13} \end{vmatrix}
> - \begin{vmatrix}a_{11} & 0 & 0 \\ 0 & a_{32} & 0 \\ 0 & 0 & a_{23} \end{vmatrix}
> - \begin{vmatrix}a_{21} & 0 & 0 \\ 0 & a_{12} & 0 \\ 0 & 0 & a_{33} \end{vmatrix} \\ \\
> =& a_{11}a_{22}a_{33} + a_{31}a_{12}a_{23} + a_{21}a_{32}a_{13}\\
> -& a_{31}a_{22}a_{13} - a_{11}a_{32}a_{23} - a_{21}a_{12}a_{33}
> \end{alignat}$$
> >[!Note]-
> >In line 2 linearity, in line 3 row change and in the last line the identity is used

>[!observation]
>1) Linearizing creates $n^n$ matrices, hence in the $2 \times 2$ case $2^2 = 4$ matrices and in the $3 \times 3$ case $3^3 = 27$ matrices with $n!$ non-zero terms.
>2) Each non-zero linearized term is a permutation
>3) After linearization, each term has exactly $n$ non-zero values. The non-zero determinants have their terms in **different** columns
>4) Because of the different columns the index $j$ in $a_{ij}$ is a permutation over the set $\{1,\ldots, n\}$, hence there are $$n! = n(n-1)(n-2)\dots2 \cdot 1$$
>	different non-zero terms as stated in 1). Each row and column can only be used once, hence the next choice has for every preceding choice one less choice.

>[!info]- Permutation
>The set of to be permuted is $N_n$ and the set of permutations is $S_n$.
>>[!def] Permutation
>> A <u>permutation</u> of $n$ objects is a bijective mapping from the set of $n$ objects to itself
>
>>[!example]
>> $$\sigma = \langle \sigma(1), \sigma(2), \dots, \sigma(n)\rangle = \begin{pmatrix} 1 & 2 & \ldots & n \\ \sigma(1) & \sigma(2) & \ldots & \sigma(n)\end{pmatrix}$$ 
>
>>[!def] Inversion
>> A permutation $\sigma = \langle j_1, j_2, \ldots, j_n \rangle$ is said to have an <u>inversion</u> if $j_s > j_t$ for $s<t$
>
>>[!example]
>>$$\sigma = \langle 3, 1, 5, 4, 2 \rangle$$
>> This permutation has 3 inversions
>> 1. 3 < 1, but 3 comes before 1
>> 2. 5 < 4, but 5 comes before 4
>> 3. 4 < 2, but 4 comes before 2
>
>>[!def] Sign of Permutations
>> A permutation is odd if the number of inversions is odd, otherwise it is even.
>> $$\text{sgn}(\sigma) = \begin{Bmatrix} 1 & \text{if } \sigma \text{ is an even permutation} \\ -1 & \text{ if } \sigma \text{ is an odd permutation} \end{Bmatrix} = (-1)^k$$
>> with $k$ being the number of inversions.
>
>

>[!def]
>The determinant for an arbitrary $n \times n$ matrix $A$ is given as
>$$ \det A = \sum\limits_{\sigma\in S_n} \text{sgn}(\sigma)a_{1\sigma(1)}a_{2\sigma(2)}\dots a_{n\sigma(n)} $$
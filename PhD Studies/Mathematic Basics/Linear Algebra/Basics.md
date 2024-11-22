>[!def] Definition Matrix and Vector Multiplication
>Let $\boldsymbol{A} \in \mathbb{K}^{m \times n}$
>$$\begin{align*}
>  \boldsymbol{A}\mathbf{x}=
>  \left[
>    \begin{array}{cccc}
>      a_{11} & a_{12} & \ldots & a_{1n}\\
>      a_{21} & a_{22} & \ldots & a_{2n}\\
>      \vdots & \vdots & \ddots & \vdots\\
>      a_{m1} & a_{m2} & \ldots & a_{mn}
>    \end{array}
>  \right]
>  \left[
>    \begin{array}{c}
>      x_1\\
>      x_2\\
>      \vdots\\
>      x_n
>    \end{array}
>  \right]
>  =
>  \left[
>    \begin{array}{c}
>      a_{11}x_1+a_{12}x_2 + \cdots + a_{1n} x_n\\
>      a_{21}x_1+a_{22}x_2 + \cdots + a_{2n} x_n\\
>      \vdots\\
>      a_{m1}x_1+a_{m2}x_2 + \cdots + a_{mn} x_n\\
>    \end{array}
>  \right]
>\end{align*}$$
>>[!example]
>>![[media/matrix_vector_multiplication.webm|matrix_vector_multiplication]]
>>[Source](http://matrixmultiplication.xyz)

>[!property] Inverse of Matrix Product
> Let $A,B$ be invertible, square matrices, then 
> ---
> $$(AB)^{-1}= B^{-1}A^{-1}$$
>
>---
>>[!proof]-
>>Given that $B^{-1}A^{-1}$ is the inverse of $AB$ then the product of those must yield the identity matrix $I$. We have
>>$$\begin{align}
>> (AB)(B^{-1}A^{-1}) &= A(BB^{-1})A^{-1} \tag{Associativity} \\
>> &= AIA^{-1} \tag{Inverse to Neutral} \\
>> &= AA^{-1} \tag{Neutrality} \\
>> &= I 
>>\end{align}$$
>>$$\tag*{$\square$}$$

^5457a2

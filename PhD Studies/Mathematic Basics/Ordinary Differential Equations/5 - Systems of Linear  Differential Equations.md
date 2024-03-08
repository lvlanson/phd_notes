>[!def] $n \times n$ First Order Linear Differential System ([[../../../PDFs/nagy.pdf#page=240| Source]])
>An $n \times n$ **first order linear differential system** is the equation 
>$$\mathbf{x}'(t)=A(t)\mathbf{x}(t)+ \mathbf{b}(t)$$
>where the $n \times n$ coefficient matrix $A$, the source $n$-vector and the unknown $n$-vector $\mathbf{x}$ are given in components by
>$$\begin{align}
>A(t) &= \begin{bmatrix}
a_{11}(t) &\dots & a_{1n}(t) \\
\vdots &\ddots & \vdots \\
a_{n1}(t) &\dots & a_{nn}(t)
\end{bmatrix} \\[1em]
> \mathbf{b}(t) &= \begin{bmatrix}
> b_{1}(t) \\
> \vdots \\
> b_{n}(t)
>\end{bmatrix} \\[1em]
> \mathbf{x}(t)&= \begin{bmatrix}
>x_{1}(t) \\
> \vdots \\
> x_{n}(t)
>\end{bmatrix}  
>\end{align}$$
>
>>[!remark]
>>The described system of linear differential equations is called **homogeneous** iff
>>- $\mathbf{b} = 0$ AND
>>- $A$ is constant AND
>>- $A$ is diagonalizable

>[!remark]
>1. The derivative of a vector valued function is defined as $$\mathbf{x}(t)' = \begin{bmatrix} x_{1}'(t) \\  \vdots \\ x_{n}'(t) \end{bmatrix} $$
>2. The matrix vector product  $A(t)\mathbf{x}(t)$  can be written as
>$$\begin{align}
> x'_{1}(t) &= a_{11}(t)x_{1}(t)+ \dots + a_{1n}(t)x_{n}(t)+b_{1}(t) \\
>  &\qquad\qquad\qquad\qquad \vdots \\
>x'_{n}(t) &= a_{n1}(t)x_{1}(t)+ \dots + a_{nn}(t)x_{n}(t)+b_{n}(t) 
>\end{align}$$
>3. Recall, according to the definition of [[../Linear Algebra/Eigenvectors and Eigenvalues#^3b9ec0|diagonalizable matrices]], some matrix $A$ is diagonalizable if there exists an invertible matrix $Q$ such that
>   $$Q^{-1}AQ = D$$
>   with $D$ containing the eigenvalues of $A$.

>[!example] Examples
>>[!example] Example for $n=1$
>>This is a single differential equation 
>>$$x_{1}' = a_{11}(t)x_{1}+ b_{1}(t)$$
>>which can be solved according to [[1 - First Order ODEs#^defThmSolODEVar|first order ODEs with variable coefficients]].
>
>>[!example] Example for $n=2$
>>Find the coefficient matrix, the source vector and the unknown vector for the $2 \times 2$ linear system
>>$$\begin{align}
>> x_{1}' &= a_{11}(t)x_{1}+ a_{12}(t)x_{2}+g_{1}(t)\\
>> x_{1}' &= a_{21}(t)x_{1}+ a_{22}(t)x_{2}+g_{2}(t)
>>\end{align}$$
>>>[!example] Solution
>>>$$\begin{align}
>>> A(t) &= \begin{bmatrix}
>>> a_{11}(t) & a_{12}(t) \\
>>> a_{21}(t) & a_{22}(t)
>>>\end{bmatrix} \\[1em]
>>>\mathbf{b}(t) &= \begin{bmatrix}
>>> g_{1}(t) \\
>>> g_{2}(t)
>>>\end{bmatrix} \\[1em]
>>>\mathbf{x}(t) &= \begin{bmatrix}
>>> x_{1}(t) \\
>>> x_{2}(t)
>>>\end{bmatrix}
>>>\end{align}$$
>
>>[!example]
>>Use matrix notation to write down the $2 \times 2$ system given by
>>$$\begin{align}
>> x_{1}' &= x_{1}-x_{2} \\
>> x_{2}' &= -x_{1}+x_{2}
>>\end{align}$$
>>>[!example]- Solution
>>> $$\begin{align}
>>> A &= \begin{bmatrix}
>>> 1 & -1 \\
>>> -1 & 1
>>>\end{bmatrix} \\[1em]
>>> \mathbf{b}(t) &= \begin{bmatrix}
>>> 0 \\
>>> 0
>>>\end{bmatrix}  \\[1em]
>>> \mathbf{x}(t) &= \begin{bmatrix}
>>> x_{1}(t) \\
>>> x_{2}(t)
>>>\end{bmatrix}
>>>\end{align}$$
>>> such that
>>> $$\begin{bmatrix}
>>> x_{1}' \\
>>> x_{2}'
>>>\end{bmatrix}
>>> = \begin{bmatrix}
>>> 1 & -1 \\
>>> -1 & 1
>>>\end{bmatrix}
>>>\begin{bmatrix}
>>> x_{1} \\
>>> x_{2}
>>>\end{bmatrix} \Leftrightarrow \mathbf{x}' = A\mathbf{x}$$
>
>>[!example]
>>Find the explicit expression for the linear system $$\mathbf{x}' = A\mathbf{x}+ \mathbf{b}$$
>>with 
>>$$\begin{align}
>>A &= \begin{bmatrix}
>>1 & 3 \\
>>3 & 1 
>>\end{bmatrix} \\
>> \mathbf{b}(t) &= \begin{bmatrix}
>> e^t \\
>> 2e^{3t}
>>\end{bmatrix} \\
>> \mathbf{x} &= \begin{bmatrix}
>> x_{1} \\
>> x_{2}
>>\end{bmatrix}
>>\end{align}$$
>>>[!example]- Solution
>>>$$\begin{align}
>>> x_{1}' &= x_{1}+3x_{2} + e^t \\
>>> x_{2}' &= 3x_{1}+x_{2}+2e^{3t}
>>>\end{align}$$

>[!def] Definition Initial Value Problem for Systems of Differential Equations ([[../../../PDFs/nagy.pdf#page=242| Source]])
>An **initial value problem** for an $n \times n$ linear differential system is the following:
>
>Given 
>- an $n \times n$ matrix valued function $A$
>- an $n$-vector valued function $\mathbf{b}$
>- a real constant $t_0$
>- $n$-vector $\mathbf{x}_{0}$
>
>find an $n$-vector valued function $\mathbf{x}$ solution of
>$$\mathbf{x}' = A(t)\mathbf{x} + \mathbf{b}(t) \qquad \mathbf{x}(t_{0})=\mathbf{x}_{0}$$
>>[!remark]
>> The initial condition vector $\mathbf{x}_{0}$ represents $n$ conditions, one for each component of the unknown vector $\mathbf{x}$

>[!theorem] Theorem Existence and Uniqueness of Solutions ([[../../../PDFs/nagy.pdf#page=242| Source]])
>If the function $A$ and $\mathbf{b}$ are continuous on an open interval $I \subset \mathbb{R}$, and if $\mathbf{x}_{0}$ is any constant vector and $t_{0}$ is any constant in $I$, then there exist only one function $\mathbf{x}$, defined an interval $\tilde{I} \subset I$ with $t_{0} \in \tilde{I}$, solution of the initial value problem
>$$\mathbf{x}' = A(t)\mathbf{x}+\mathbf{b}(t), \qquad \mathbf{x}(t_{0})=\mathbf{x}_{0}$$

>[!remark]
>There exists a correspondence between $n \times n$ systems of linear differential equations and $n$-th order differential equations.

>[!theorem] Theorem First Order Reduction ([[../../../PDFs/nagy.pdf#page=243| Source]])
> A function $y$ solves the second order equation
> $$
> y'' + a_{1}(t)y' + a_{0}(t)y = b(t) \tag{1}
>$$
>**iff** the function $x_{1}=y$ and $x_{2}=y'$ are solutions to the $2 \times 2$ first order differential system
>$$\begin{align}
> x_{1}' &= x_{2} \tag{2} \\ 
> x_{2}' &= -a_{0}(t)x_{1}-a_{1}(t)x_{2}+b(t) \tag{3}
>\end{align}$$
>>[!proof]
>>> $\implies$
>>
>> Given a solution of $y$ of 
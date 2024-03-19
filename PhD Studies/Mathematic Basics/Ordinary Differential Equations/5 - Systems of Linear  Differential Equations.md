>[!terminology]
>- [[#^1dd106| Superposition Principle]]
>- [[#^16a38b| Fundamental Set]]
>- [[#^16a38b| General Solution]]
>- [[#^44918f| Solution Matrix | Fundamental Matrix]]
>- [[#^44918f| Wronskian]]

^7e6f96

## 5.1 General Properties
### 5.1.1 First Order Linear Systems
>[!def] Definition $n \times n$ First Order Linear Differential System ([[../../../PDFs/nagy.pdf#page=240| Source]])
>An $n \times n$ **first order linear differential system** is the equation 
>$$\mathbf{x}'(t)=A(t)\mathbf{x}(t)+ \mathbf{b}(t)$$
>where the $n \times n$ coefficient matrix $A$, the source $n$-vector and the unknown $n$-vector $\mathbf{x}$ are given in components by
>---
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
>---
>>[!remark]
>>The described system of linear differential equations is called **homogeneous** iff
>>- $\mathbf{b} = 0$ AND
>>- $A$ is constant AND
>>- $A$ is diagonalizable

^5c0272

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

>[!example]- Examples
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
>
>---
>$$\mathbf{x}' = A(t)\mathbf{x} + \mathbf{b}(t) \qquad \mathbf{x}(t_{0})=\mathbf{x}_{0}$$
>
>---
>>[!remark]
>> The initial condition vector $\mathbf{x}_{0}$ represents $n$ conditions, one for each component of the unknown vector $\mathbf{x}$

### 5.1.2 Existence of Solutions

^c3380b

>[!theorem] Theorem Existence and Uniqueness of Solutions ([[../../../PDFs/nagy.pdf#page=242| Source]])
>If the function $A$ and $\mathbf{b}$ are continuous on an open interval $I \subset \mathbb{R}$, and if $\mathbf{x}_{0}$ is any constant vector and $t_{0}$ is any constant in $I$, then there exist only one function $\mathbf{x}$, defined an interval $\tilde{I} \subset I$ with $t_{0} \in \tilde{I}$, solution of the initial value problem
>---
>$$\mathbf{x}' = A(t)\mathbf{x}+\mathbf{b}(t), \qquad \mathbf{x}(t_{0})=\mathbf{x}_{0}$$
>
>---

^2e3cb4

>[!remark]
>There exists a correspondence between $n \times n$ systems of linear differential equations and $n$-th order differential equations.

### 5.1.3 Order Transformations

>[!theorem] Theorem First Order Reduction ([[../../../PDFs/nagy.pdf#page=243| Source]])
> A function $y$ solves the second order equation
> $$
> y'' + a_{1}(t)y' + a_{0}(t)y = b(t) \tag{1}
>$$
>**iff** the functions 
>$$\begin{align}
> x_{1}&=y \\ 
> x_{2}&=y'
>\end{align}$$ 
>are solutions to the $2 \times 2$ first order differential system
>$$\begin{align}
> x_{1}' &= x_{2} \tag{2} \\ 
> x_{2}' &= -a_{0}(t)x_{1}-a_{1}(t)x_{2}+b(t) \tag{3}
>\end{align}$$
>>[!proof]-
>>> $\implies$
>>
>> Given $y$ is a solution of equation $(1)$, we introduce
>> $$\begin{align}
>> x_{1} &= y \\
>> x_{2} &= y'
>>\end{align}$$
>>Equation $(2)$ holds because
>>$$x_{1}' = x_{2}=y'$$ 
>>Equation $(3)$ holds because $y'$ can be arranged such that
>>$$x_{2}' = y'$$
>>holds
>>$$\begin{align}
>> \underbrace{ y'' }_{ =x_{2}' } + a_{1}(t)\underbrace{ y' }_{ =x_{2} } + a_{0}(t)\underbrace{ y }_{ =x_{1} } &= b(t) \\
>> x_{2}' + a_{1}(t)x_{2}+a_{0}(t)x_{1} &= b(t) \\
>> x_{2}' &= -a_{1}(t)x_{2}-a_{0}(t)x_{1} +b(t) 
>>\end{align}$$
>>>$\Longleftarrow$
>>
>>We take equation $(2)$
>>$$\begin{alignat}{2}
>> x_{1}' &= x_{2} \qquad&&\Big\vert \frac{d}{dt} \\
>> x_{1}'' &= x_{2}'
>>\end{alignat}$$
>>We now substitute into the suggested solution equation $(3)$
>>$$\begin{align}
>> \underbrace{ x_{2}' }_{ =x_{1}'' } &= -a_{0}(t)x_{1}-a_{1}(t)\underbrace{ x_{2} }_{ =x_{1}' }+b(t) \\
>> x_{1}'' &= -a_{0}(t)x_{1}-a_{1}(t)x_{1}'+b(t)
>>\end{align}$$
>>Renaming $x_1$ to $y$ as suggested by the theorem gives the desired result
>>$$y'' = -a_{0}(t)y-a_{1}(t)y'+b(t) \tag*{$\square$}$$
>
>>[!example]
>>Express as a first order system the second order equation $$y''+2y'+2y=\sin(at)$$
>>>[!example]- Solution
>>>Using the theorem we introduce the variables
>>>$$\begin{align}
>>> x_{1} &= y \\
>>> x_{2} &= y'
>>>\end{align}$$
>>>Therefore, we have
>>>$$x_{2} = x_{1}'$$
>>>and by taking the derivative of $x_2$ we get
>>>$$\begin{align}
>>> x_{2}' = y''
>>>\end{align}$$
>>>Hence, we get
>>>$$x_{2}'+2x_{2}+x_{1}=\sin(at)$$
>>>The system of differential equations can now be stated as
>>>$$\begin{align}
>>> x_{1}' &= x_{2} \\
>>> x_{2}' &= -2x_{2}-x_{1}+\sin(at)
>>>\end{align}$$
>
>>[!remark]
>>The transformation given by the theorem can be generalized to $n \times n$ linear differential systems and $n$-th order scalar linear equations for $n \geq 2$

^fb7c74

>[!theorem] Theorem Second Order Reduction ([[../../../PDFs/nagy.pdf#page=244| Source]])
>Any $2 \times 2$ constant coefficients linear system
>$$\begin{align}
> \mathbf{x}'=A\mathbf{x}
>\end{align}$$
>with $\mathbf{x}=\begin{bmatrix} x_1 \\ x_2\end{bmatrix}$ can be written as second order equations for $x_{1}$ and $x_{2}$
>
>---
>$$\mathbf{x}''  - \mathrm{tr}(A)\mathbf{x}' + \det(A)\mathbf{x}=\mathbf{0} \tag{1}$$
>
>---
>Furthermore, the solution to the initial value problem $\mathbf{x}'=A\mathbf{x}$ with $\mathbf{x}(0)=\mathbf{x}_{0}$, also solves the initial value problem given by equation $(1)$ with initial condition
>$$\mathbf{x}(0) = \mathbf{x}_{0} \qquad \mathbf{x}'(0)=A\mathbf{x}_{0}$$
>>[!remark]-
>> Equation $(1)$ can be given as
>> $$\begin{align}
>> x_{1}'' - \mathrm{tr}(A)x_{1}' + \det(A)x_{1} &=0 \\
>> x_{2}'' - \mathrm{tr}(A)x_{2}' + \det(A)x_{2} &=0 
>>\end{align}$$
>
>>[!proof]- Proof 1 (Based on Cayley-Hamilton Theorem)
>>The following identity can be stated for any $2 \times 2$ matrix $A$
>>$$A^2 - \mathrm{tr}(A)A+\det(A)I = 0 \tag{1}$$
>>>[!note]- Note Cayley-Hamilton Theorem for $n=2$
>>> $$\begin{align}
>>> A^2 - \mathrm{tr}(A)A+\det(A)I &= 0 \\
>>> \underbrace{ \underbrace{ \begin{bmatrix}
>>> a_{11} & a_{12} \\
>>> a_{21} & a_{22}
>>>\end{bmatrix}^2 }_{ =(1) } - \underbrace{ (a_{11}+a_{22})\begin{bmatrix}
>>> a_{11} & a_{12} \\
>>> a_{21} & a_{22}
>>>\end{bmatrix} }_{ =(2) } }_{ =(4) } + \underbrace{ (a_{11}a_{22}-a_{12}a_{21})\begin{bmatrix}
>>>1 & 0 \\
>>>0 & 1
>>>\end{bmatrix} }_{ =(3) } &= 0
>>> 
>>>\end{align}$$
>>>We solve
>>>$$\begin{bmatrix}
>>> a_{11} & a_{12} \\
>>> a_{21} & a_{22}
>>>\end{bmatrix}^2 = \begin{bmatrix}
>>> a_{11}^2+a_{21}a_{12} & a_{11}a_{12} + a_{12}a_{22} \\
>>> a_{11}a_{21}+a_{21}a_{22} & a_{22}^2 + a_{21}a_{12}
>>>\end{bmatrix} \tag{1}$$
>>>and 
>>>$$(a_{11}+a_{22})\begin{bmatrix}
>>> a_{11} & a_{12} \\
>>> a_{21} & a_{22}
>>>\end{bmatrix} = \begin{bmatrix}
>>> a_{11}^2+a_{11}a_{22} & a_{12}a_{11}+a_{12}a_{22} \\
>>> a_{21}a_{11}+a_{21}a_{22} & a_{22}^2+a_{11}a_{22}
>>>\end{bmatrix} \tag{2}$$
>>>and
>>>$$(a_{11}a_{22}-a_{12}a_{21})\begin{bmatrix}
>>>1 & 0 \\
>>>0 & 1
>>>\end{bmatrix} = \begin{bmatrix}
>>>a_{11}a_{22}-a_{12}a_{21} & 0 \\
>>>0 & a_{11}a_{22}-a_{12}a_{21}
>>>\end{bmatrix} \tag{3}$$
>>>
>>>Having these results, we now combine $(1)-(2)$ as stated in the original equation.
>>>$$\begin{align}
>>>(1)-(2) &= \begin{bmatrix}
>>> a_{11}^2+a_{21}a_{12} & a_{11}a_{12} + a_{12}a_{22} \\
>>> a_{11}a_{21}+a_{21}a_{22} & a_{22}^2 + a_{21}a_{12}
>>>\end{bmatrix} - \begin{bmatrix}
>>> a_{11}^2+a_{11}a_{22} & a_{12}a_{11}+a_{12}a_{22} \\
>>> a_{21}a_{11}+a_{21}a_{22} & a_{22}^2+a_{11}a_{22}
>>>\end{bmatrix}  \\[1em]
>>> &= \begin{bmatrix}
>>> \cancel{ a_{11}^2 }+a_{21}a_{12} & \cancel{ a_{11}a_{12} } + \cancel{ a_{12}a_{22} } \\
>>> \cancel{ a_{11}a_{21} }+\cancel{ a_{21}a_{22} } & \cancel{ a_{22}^2 } + a_{21}a_{12}
>>>\end{bmatrix} - \begin{bmatrix}
>>> \cancel{ a_{11}^2 }+a_{11}a_{22} & \cancel{ a_{12}a_{11} }+\cancel{ a_{12}a_{22} } \\
>>> \cancel{ a_{21}a_{11} }+\cancel{ a_{21}a_{22} } & \cancel{ a_{22}^2 }+a_{11}a_{22}
>>>\end{bmatrix} \\[1em]
>>> &= \begin{bmatrix}
>>>a_{21}a_{12} - a_{11}a_{22} & 0 \\
>>>0 &  a_{21}a_{12} - a_{11}a_{22}
>>>\end{bmatrix} \tag{4}
>>>\end{align}$$
>>>Now we combine this result as suggested $(3)+(4)$
>>>$$\begin{align}
>>> (4)+(3) &= \begin{bmatrix}
>>>a_{21}a_{12} - a_{11}a_{22} & 0 \\
>>>0 &  a_{21}a_{12} - a_{11}a_{22}
>>>\end{bmatrix} +\begin{bmatrix}
>>>a_{11}a_{22}-a_{12}a_{21} & 0 \\
>>>0 & a_{11}a_{22}-a_{12}a_{21}
>>>\end{bmatrix} \\[1em]
>>> &= 0
>>>\end{align}$$
>>>which confirms the suggested identity
>>>$$\tag*{$\square$}$$
>>
>>Note, we have given the equation
>>$$\mathbf{x}' = A\mathbf{x}$$
>>Taking the derivative yields
>>$$\begin{align}
>> \mathbf{x}'' &= (A\mathbf{x})' \\
>> &= A\mathbf{x}'  \\
>> &= A^2\mathbf{x}\tag{$\mathbf{x}' = A\mathbf{x}$}
>>\end{align}$$
>>We can arrange equation $(1)$ to have
>>$$\begin{align}
>> A^2 - \mathrm{tr}(A)A+\det(A)I &= 0 \\ 
>> A^2 &= \mathrm{tr}(A)A -\det(A)I \qquad&&\Big\vert \cdot \mathbf{x} \\ 
>> A^2\mathbf{x} &= \mathrm{tr}(A)A\mathbf{x} -\det(A)\underbrace{ I\mathbf{x} }_{ =\mathbf{x} } \\
>> A^2\mathbf{x} &= \mathrm{tr}(A)A\mathbf{x} -\det(A)\mathbf{x}
>>\end{align}$$
>>We insert this result, rearrange and yield
>>$$\begin{align}
>> \mathbf{x}'' &= \mathrm{tr}(A)A\mathbf{x} -\det(A)\mathbf{x} \\
>> \mathbf{x}''-\mathrm{tr}(A)A\mathbf{x} +\det(A)\mathbf{x} &= 0 
>>\end{align}$$
>>We conclude by checking the initial condition claims. By [[#^2e3cb4| the existence and uniqueness theorem]] the initial condition to the system of first order differential equations is given as
>>$$\mathbf{x}(t_{0})=\mathbf{x_{0}}$$
>>Note, the second condition follows from $t=0$
>>$$\begin{align}
>> \mathbf{x}'(0) &= A\mathbf{x}(0) \\
>>   &= A\mathbf{x}_{0}
>>\end{align}$$
>>which establishes the theorem $$\tag*{$\square$}$$
>
>>[!proof]- Proof 2 (Computational)
>>First, we denote
>>$$A = \begin{bmatrix}
>>a_{11} & a_{12} \\
>> a_{21} & a_{22}
>>\end{bmatrix}$$ 
>>and can therefore state the system
>>$$\begin{align}
>> x_{1}' &= a_{11}x_{1} + a_{12}x_{2} \tag{1}\\
>> x_{2}' &= a_{21}x_{1} + a_{22}x_{2} \tag{2}
>>\end{align}$$
>>>Case: $a_{12} \neq 0$
>>
>>We reorganize equation $(1)$ as follows
>>$$\begin{alignat}{2}
>> x_{1}' &= a_{11}x_{1} + a_{12}x_{2} \qquad&&\Big\vert \frac{d}{dt} \\
>> x_{1}'' &= a_{11}x_{1}' + a_{12}x_{2}' \\
>>\end{alignat}$$
>>We insert $x_2'$ into equation $(2)$
>>$$\begin{align}
>>x_{1}'' &= a_{11}x_{1}' + a_{12}(a_{21}x_{1} + a_{22}x_{2}) \tag{3}
>>\end{align}$$
>>We rearrange equation $(1)$ for $x_2'$ to substitute into equation $(3)$. 
>>$$\begin{align}
>> x_{1}' &= a_{11}x_{1} + a_{12}x_{2} \\
>> x_{2} &= \frac{x_{1}' - a_{11}x_{1}}{a_{12}}
>>\end{align}$$
>>We insert the result into equation $(3)$
>>$$\begin{align}
>>x_{1}'' &= a_{11}x_{1}' + a_{12}\left( a_{21}x_{1} + a_{22}\frac{x_{1}' - a_{11}x_{1}}{a_{12}} \right) \\
>>x_{1}'' &= a_{11}x_{1}' + a_{12}a_{21}x_{1} + \cancel{ a_{12} }a_{22}\frac{x_{1}' - a_{11}x_{1}}{\cancel{ a_{12} }} \\
>>x_{1}'' &= a_{11}x_{1}' + a_{12}a_{21}x_{1} + a_{22}x_{1}' - a_{11}a_{22}x_{1} \\
>>x_{1}'' &= x_{1}'\underbrace{ (a_{11}+a_{22}) }_{ =\mathrm{tr}(A) } - x_{1}\underbrace{ (a_{11}a_{22}-a_{12}a_{21}) }_{ =\det(A) } \\ 
>>x_{1}'' &= x_{1}'\mathrm{tr}(A) - x_{1}\det(A) \\
>>x_{1}''-x_{1}'\mathrm{tr}(A)+x_{1}\det(A)  &=  0
>>\end{align}$$
>>By [[#^2e3cb4| the existence and uniqueness theorem]] the initial condition to the system of first order differential equations is given as
>>$$\mathbf{x}(t_{0})=\mathbf{x}_{0}$$
>>Hence with $t=0$,
>>$$x_{1}(0)= x_{0_{1}}$$
>>Note, the second condition follows from
>>$$\begin{align}
>> \mathbf{x}'(0) &= A\mathbf{x}(0) \\
>>   &= A\mathbf{x}_{0}
>>\end{align}$$
>>where the first component is calculated with
>>$$x_{0_{1}}'(0)= a_{11}x_{0_{1}}(0)+ a_{12}x_{0_{2}}$$
>>> Case: $a_{12}=0$
>>
>>$$\begin{align}
>>  x_{1}' &= a_{11}x_{1} \tag{4}\\
>> x_{2}' &= a_{21}x_{1} + a_{22}x_{2} \tag{5}
>>\end{align}$$
>>We again compute the derivative for equation $(4)$
>>$$\begin{align}
>>x_{1}' &= a_{11}x_{1} \qquad&&\Big\vert \frac{d}{dt} \\
>> x_{1}'' &= a_{11}x_{1}' \\ 
>> x_{1}''-a_{11}x_{1}' &= 0 \tag{6}
>>\end{align}$$
>>We now rewrite equation $(4)$
>>$$\begin{alignat}{2}
>> x_{1}' &= a_{11}x_{1}  \qquad&&\Big\vert -x_{1}' \\
>> a_{11}x_{1}-x_{1}'  &= 0 \qquad&&\Big\vert \cdot a_{22} \\
>> a_{22}(a_{11}x_{1}-x_{1}')  &= 0 \tag{7}
>>\end{alignat}$$
>>Setting equations $(6)$ and $(7)$ equal yields
>>$$\begin{align}
>> x_{1}''-a_{11}x_{1}' + a_{22}(a_{11}x_{1}-x_{1}') = 0 \\
>> x_{1}''-a_{11}x_{1}' - a_{22}x_{1}'+a_{11}a_{22}x_{1} = 0 \\
>> x_{1}''-x_{1}' \underbrace{ (a_{11} + a_{22}) }_{ =\mathrm{tr}(A) } +\underbrace{ a_{11}a_{22} }_{ =\det(A) }x_{1} = 0 \\
>> x_{1}''-x_{1}' \mathrm{tr}(A)  + \det(A) x_{1} = 0 \\
>>\end{align}$$
>>The initial conditions can be derived as in the previous case. For $x_2$ we can do the same analysis using $a_{21}$.
>>$$\tag*{$\square$}$$
>
>>[!example]
>>Express the $2 \times 2$ system as a single second order equation and solve
>>$$\begin{align}
>>x_{1}' &= -x_{1}+ 3x_{2} \tag{1}\\
>> x_{2}' &= x_{1}-x_{2}\tag{2}
>>\end{align}$$
>>>[!example]- Solution
>>>First we prepare some necessary computations
>>>$$\begin{alignat}{2}
>>> x_{1}' &= -x_{1} + 3x_{2} \qquad&&\Big\vert \frac{d}{dt} \\
>>> x_{1}'' &= -x_{1}' + 3x_{2}'  \tag{3}\\[2em]
>>> x_{1}' &= -x_{1} + 3x_{2} \qquad&&\Big\vert +x_{1} \\
>>> 3x_{2} &= x_{1} + x_{1}' \qquad&&\Big\vert :3  \\
>>> x_{2} &= \frac{x_{1} + x_{1}'}{3} \tag{4} \\[2em]
>>>\end{alignat}$$
>>>We now compute the 2nd order ODE using equation $(3)$
>>>$$\begin{align}
>>>x_{1}'' &= -x_{1}'+ 3\underbrace{ x_{2}' }_{ =(2) } \\
>>>x_{1}'' &= -x_{1}' + 3(x_{1}-\underbrace{ x_{2} }_{ =(4) }) \\
>>>x_{1}'' &= -x_{1}' + 3\left(  x_{1}-\frac{x_{1} + x_{1}'}{3}  \right)\\
>>>x_{1}'' &= -x_{1}' +  3x_{1}-x_{1} - x_{1}' \\
>>>x_{1}'' &= -2x_{1}' +  2x_{1} \\
>>>x_{1}''+2x_{1}'-2x_{1} &= 0 \\
>>>\end{align}$$
>>>This is a second order differential equation and can be solved using the [[2 - Second Order ODEs#^9bcb76| characteristic polynomial]] and using the [[2 - Second Order ODEs#^702f6f| appropriate theorem]]. Therefore, we have
>>>$$\begin{align}
>>> r^2+2r-2 = 0
>>>\end{align}$$
>>>This yields the solutions
>>>$$\begin{align}
>>> r_{+} &= -1 + \sqrt{ 3 } \\
>>> r_{-} &= -1 - \sqrt{ 3 }
>>>\end{align}$$
>>>According to the solution theorem, the general solution for $x_1$ can be given as
>>>$$x_{1}=c_{+}e^{(-1 + \sqrt{ 3 })t}+ c_{-}e^{(-1 - \sqrt{ 3 })t}$$
>>>Finally, since we are also interested to have solutions for $x_2$, we can use the found solution of $x_1$. Since $x_1$ is the general solution, hence both parts of the solutions are linearly independent, we can choose arbitrary constants $\tilde{c}_{\pm}$ for $x_{2}$, which by design of the system solve the requirements. Finally,
>>>$$x_{2}=\tilde{c}_{+}e^{(-1 + \sqrt{ 3 })t}+ \tilde{c}_{-}e^{(-1 - \sqrt{ 3 })t}$$
>
>>[!example] 
>> Write the first order initial value problem 
>> $$\begin{align}
>> \mathbf{x}' &= A\mathbf{x} \\
>> A &= \begin{bmatrix}
>> 1 & 2 \\
>> 3 & 4
>>\end{bmatrix} \\
>> \mathbf{x} &= \begin{bmatrix}
>> x_{1} \\
>> x_{2}
>>\end{bmatrix} \\
>> \mathbf{x}(0) &= \begin{bmatrix}
>> 5 \\ 6
>>\end{bmatrix}
>>\end{align}$$
>>as a second order initial value problem for $x_{1}$. Repeat calculations for $x_2$.
>>>[!example]- Solution
>>>We have
>>>$$\begin{align}
>>>\begin{bmatrix}
>>> x_{1}' \\ x_{2}'
>>>\end{bmatrix} &= \begin{bmatrix}
>>> 1 & 2 \\
>>> 3 & 4
>>>\end{bmatrix} \begin{bmatrix}
>>> x_{1} \\
>>> x_{2}
>>>\end{bmatrix} \\ &\Downarrow \\
>>> x_{1}' &= x_{1} + 2x_{2} \\
>>> x_{2}' &= 3x_{1} + 4x_{2}
>>>\end{align}$$
>>>The theorem states for initial conditions
>>>$$\begin{align}
>>> \mathbf{x}(\mathbf{0}) &= \mathbf{x_{0}} \\
>>> \mathbf{x}'(\mathbf{0})  &= \mathbf{A}\mathbf{x_{0}}
>>>\end{align}$$
>>>Therefore we have
>>>$$\begin{align}
>>> \mathbf{x}(\mathbf{0})&=\begin{bmatrix}
>>> x_{1}(0) \\ x_{2}(0)
>>>\end{bmatrix} =\begin{bmatrix}
>>> 5 \\ 6
>>>\end{bmatrix} \\
>>> &\Downarrow \\
>>> x_{1}(0) &= 5 \\
>>> x_{2}(0) &= 6
>>>\end{align}$$
>>>and for $\mathbf{x}'$
>>>$$\begin{align}
>>> \mathbf{x}'(\mathbf{0})&=\begin{bmatrix}
>>> x_{1}'(0) \\ x_{2}'(0)
>>>\end{bmatrix} =\begin{bmatrix}
>>> 1 & 2 \\
>>> 3 & 4
>>>\end{bmatrix}\begin{bmatrix}
>>> 5 \\ 6
>>>\end{bmatrix} = \begin{bmatrix}
>>> 17 \\ 39
>>>\end{bmatrix} \\
>>> &\Downarrow \\
>>> x_{1}'(0) &= 17 \\
>>> x_{2}'(0) &= 39 \\
>>>\end{align}$$

^93c797

### 5.1.4 Homogeneous Systems

>[!theorem] Theorem Superposition for Homogeneous Systems ([[../../../PDFs/nagy.pdf#page=244| Source]])
>If the vector functions $\mathbf{x}^{(1)}, \mathbf{x}^{(2)}$ are solutions of 
>$$\begin{align}
> \mathbf{x}^{(1)'} &= A\mathbf{x}^{(1)} \\
> \mathbf{x}^{(2)'} &= A\mathbf{x}^{(2)} 
>\end{align}$$
>then the linear combination 
>$$\begin{align}
> \mathbf{x} = a \mathbf{x}^{(1)} + b \mathbf{x}^{(2)} \qquad \forall a,b \in \mathbb{R} 
>\end{align}$$
>is also solution of 
>$$\mathbf{x}' = A\mathbf{x}$$
>>[!remark]
>>This is an extension of the [[2 - Second Order ODEs#^88d6f3|superposition principle]] of linear homogeneous second order differential equations
>
>>[!remark]
>>There are two cases of interest
>>1. $a = b= 1$:
>>$\mathbf{x}^{(1)}, \mathbf{x}^{(2)}$ are solutions $\Longrightarrow$ so is $\mathbf{x}^{(1)}+ \mathbf{x}^{(2)}$
>>2. $b=0, a$ arbitrary:
>>$\mathbf{x}^{(1)}$ is solution $\Longrightarrow$ so is $a\mathbf{x}^{(1)}$
>
>>[!proof]-
>>Suppose 
>>$$\mathbf{x}= a\mathbf{x}^{(1)} + b\mathbf{x}^{(2)}$$
>>is a solution of the differential equation. We use the [[2 - Second Order ODEs#^dec49d|linearity of the differential operator]]
>>$$\begin{align}
>> \mathbf{x}' &= \Big(a\mathbf{x}^{(1)} + b\mathbf{x}^{(2)} \Big)' \\
>>  &= a\mathbf{x}^{(1)'} + b\mathbf{x}^{(2)'} \tag{1}
>>\end{align}$$
>>Note, the solution to any linear homogeneous differential system is given as $$\mathbf{x}' = A\mathbf{x}$$ as stated in the [[#^5c0272| definition of linear systems]] with $\mathbf{b}=\mathbf{0}$.  We substitute accordingly into equation $(1)$
>>$$\begin{align}
>> \mathbf{x}' &=  aA\mathbf{x}^{(1)} + bA\mathbf{x}^{(2)} \\
>>    &= A( a\mathbf{x}^{(1)} + b\mathbf{x}^{(2)}) \\
>>    &= A\mathbf{x} \tag*{$\square$}
>>\end{align}$$
>
>>[!example]
>>Verify that 
>>$$\begin{align}
>> \mathbf{x}^{(1)} &= \begin{bmatrix}
>> 1 \\ 1
>>\end{bmatrix}e^{-2t} \\
>>\mathbf{x}^{(2)} &= \begin{bmatrix}
>> -1 \\ 1
>>\end{bmatrix}e^{4t} \\
>> \tilde{\mathbf{x}} &= \mathbf{x}^{(1)} + \mathbf{x}^{(2)}
>>\end{align}$$
>> are solutions to the homogeneous linear system
>> $$\begin{align}
>> \mathbf{x}' &= A\mathbf{x} \\ 
>> A &= \begin{bmatrix}
>> 1 & -3 \\ -3 & 1
>>\end{bmatrix} 
>>\end{align}$$
>>>[!example]- Solution
>>>First, we verify that the fundamental solutions are valid. Computing the derivatives gives
>>>$$\begin{align}
>>> \mathbf{x}^{(1)'} &= \begin{bmatrix}
>> -2 \\ -2
>>\end{bmatrix}e^{-2t} \\
>>\mathbf{x}^{(2)'} &= \begin{bmatrix}
>> -4 \\ 4
>>\end{bmatrix}e^{4t} \\
>>>\end{align}$$
>>>Now, we insert for each fundamental solution into the system and verify
>>>$$\begin{align}
>>> \mathbf{x}^{(1)'} &= A\mathbf{x}^{(1)} \\
>>> \begin{bmatrix}
>> -2 \\ -2
>>\end{bmatrix}e^{-2t} &= \begin{bmatrix}
>> 1 & -3 \\ -3 & 1
>>\end{bmatrix} \begin{bmatrix}
>> 1 \\ 1
>>\end{bmatrix}e^{-2t}  \\
>> &=\begin{bmatrix}
>> 1-3 \\ -3+1
>>\end{bmatrix}e^{-2t} \\
>> &=\begin{bmatrix}
>> -2 \\ -2
>>\end{bmatrix}e^{-2t}
>>> \end{align}$$
>>> and
>>> $$\begin{align}
>>> \mathbf{x}^{(2)'} &= A\mathbf{x}^{(2)} \\
>>> \begin{bmatrix}
>> -4 \\ 4
>>\end{bmatrix}e^{4t} &= \begin{bmatrix}
>> 1 & -3 \\ -3 & 1
>>\end{bmatrix} \begin{bmatrix}
>> -1 \\ 1
>>\end{bmatrix}e^{4t}  \\
>> &=\begin{bmatrix}
>> -1-3 \\ 3+1
>>\end{bmatrix}e^{4t} \\
>> &=\begin{bmatrix}
>> -4 \\ 4
>>\end{bmatrix}e^{-2t}
>>> \end{align}$$
>>> We now successfully verified that the fundamental solutions solve the system of differential equations. We now verify, that the general solution also solves that system
>>> $$\begin{align}
>>>\tilde{\mathbf{x}}' &= A\tilde{\mathbf{x}} \\ 
>>> \mathbf{x}^{(1)'} + \mathbf{x}^{(2)'} &= A\mathbf{x}^{(1)} + A\mathbf{x}^{(2)}\\
>>>\begin{bmatrix}
>> -2 \\ -2
>>\end{bmatrix}e^{-2t} + \begin{bmatrix}
>> -4 \\ 4
>>\end{bmatrix}e^{4t} &= \begin{bmatrix}
>> 1 & -3 \\ -3 & 1
>>\end{bmatrix} \begin{bmatrix}
>> 1 \\ 1
>>\end{bmatrix}e^{-2t} + \begin{bmatrix}
>> 1 & -3 \\ -3 & 1
>>\end{bmatrix} \begin{bmatrix}
>> -1 \\ 1
>>\end{bmatrix}e^{4t} \\
>>&= \begin{bmatrix}
>> -2 \\ -2
>>\end{bmatrix}e^{-2t} + \begin{bmatrix}
>> -4 \\ 4
>>\end{bmatrix}e^{4t}
>>>\end{align}$$

^1dd106

>[!def] Definition Linear Independence of Vector Valued Functions ([[../../../PDFs/nagy.pdf#page=247| Source]])
>A set of $n$ vector valued functions $\{ \mathbf{x}^{(1)},  \dots, \mathbf{x}^{(n)} \}$ is called **linearly dependent** on an interval $I \in \mathbb{R}$ iff for all $t \in I$ there exist constants $c_{1}, \dots, c_{n}$ not all of them zero, such that it holds
>$$c_{1}\mathbf{x}^{(1)}(t)+ \dots + c_{n}**c_{1}\mathbf{x}^{(n)}(t) = \mathbf{0}$$
>A set of $n$ vector valued functions is called **linearly independent** on $I$ iff the set is not linearly dependent.

>[!def] Definition Fundamental Set and General Solution ([[../../../PDFs/nagy.pdf#page=248| Source]])
>1. The set of functions $\{ \mathbf{x}^{(1)}, \dots, \mathbf{x}^{(n)} \}$ is a **fundamental set of solutions** of the equation $\mathbf{x}' = A\mathbf{x}$ iff the set $\{ \mathbf{x}^{(1)}, \dots, \mathbf{x}^{(n)} \}$ is linearly independent and $\mathbf{x}^{(i)'} = A\mathbf{x}^{(i)}$ for every $i = 1,\dots,n$
>2. The **general solution** of the homogeneous equation $\mathbf{x}' = A\mathbf{x}$ denotes any vector valued function $\mathbf{x}_{gen}$ that can be written as linear combination
>---
>$$\mathbf{x}_{gen}(t) = c_{1}\mathbf{x}^{(1)}(t)+ \dots + c_{n}\mathbf{x}^{(n)}(t)$$
>
>---
>where $\mathbf{x}^{(1)},\dots, \mathbf{x}^{(n)}$ are the functions in any fundamental set of solutions of $\mathbf{x}' = A\mathbf{x}$ while $c_{1},\dots,c_{n}$ are arbitrary constants

^16a38b

>[!theorem] Theorem General Solution ([[../../../PDFs/nagy.pdf#page=248| Source]])
>If $\{ \mathbf{x}^{(1)},  \dots, \mathbf{x}^{(n)} \}$ is a linearly independent set of solutions to the $n \times n$ system $$\mathbf{x}' =A\mathbf{x}$$ where $A$ is a continuous matrix valued function, then there exist unique constants $c_{1}, \dots, c_{n}$ such that every solution $\mathbf{x}$ of the differential equation $\mathbf{x}' = A\mathbf{x}$ can be written as the linear combination
>
>---
>$$\mathbf{x}_{gen}(t)= c_{1}\mathbf{x}^{(1)}(t)+ \dots + c_{n}\mathbf{x}^{(n)}(t)$$
>
>---
>>[!remark]
>> The [[#^1dd106|superposition theorem]] already implies, that given we have fundamental solutions, that these could form a general solution.
>
>>[!proof]-
>>First note, the [[#^1dd106| superposition principle]] can easily be extended to $n$ solutions for an $n \times n$ system. Hence, a general solution for an $n \times n$ system, can be given as 
>>$$\mathbf{x}_{gen}(t)= c_{1}\mathbf{x}^{(1)}(t)+ \dots + c_{n}\mathbf{x}^{(n)}(t)$$
>>Now, by [[#^2e3cb4|the uniqueness property of solutions]] for initial value problems, we can state, that we can find a single function for the general solution $\mathbf{x}_{gen}$ given some $t_{0}$. Solving means we need to solve for $\mathbf{c}=[c_{1}, \dots, c_{n}]^T$. We make a change of notation
>>$$\begin{align}
>> c_{1}\mathbf{x}^{(1)}(t)+ \dots + c_{n}\mathbf{x}^{(n)}(t) =X(t)\mathbf{c}
>>\end{align}$$
>>with 
>>$$\begin{align}
>> X(t) &= [\mathbf{x}^{(1)}(t), \dots , \mathbf{x}^{(n)}(t)]  \\
>> \mathbf{c} &= \begin{bmatrix}
>> c_{1} \\ \vdots \\ c_{n}
>>\end{bmatrix}
>>\end{align}$$
>>Hence, the general solution can be given as
>>$$\mathbf{x}(t_{0})=X(t_{0})\mathbf{c}$$
>>Note, solving for $\mathbf{c}$ requires the matrix $X(t)$ to be invertible, i.e. $\det(X) \neq 0$, which means we require the set of fundamental solutions to be linearly independent. 
>>$$\tag*{$\square$}$$
>>>[!note]
>>>Abel's Theorem for systems of equations will validate the concluding claim.
>
>>[!example]
>>Find the general solution to the differential equation and use the general solution to find the solution of the initial value problem
>> $$\begin{align}
>> \mathbf{x}' &= A\mathbf{x} \\
>> A &= \begin{bmatrix}
>> 1 & 2 \\
>> 3 & 4
>>\end{bmatrix} \\
>> \mathbf{x}(0) &= \begin{bmatrix}
>> 1 \\ 5
>>\end{bmatrix}
>>\end{align}$$
>> with solutions
>> $$\begin{align}
>> \mathbf{x}^{(1)} &= \begin{bmatrix}
>> 2 \\ 1
>>\end{bmatrix}e^{2t} \\
>> \mathbf{x}^{(2)} &= \begin{bmatrix}
>> 1 \\ 2
>>\end{bmatrix} e^{-t}
>>\end{align}$$
>>>[!example]- Solution
>>>The general solution can be given as
>>>$$\begin{align}
>>>\mathbf{x}_{gen} &= c_{1}\begin{bmatrix}
>>> 2 \\ 1
>>>\end{bmatrix}e^{2t} + c_{2} \begin{bmatrix}
>>> 1 \\ 2
>>>\end{bmatrix} e^{-t} \\ 
>>> &=\begin{bmatrix}
>>> 2 e^{2t} & e^{-t} \\
>>> e^{2t} & 2e^{-t}
>>>\end{bmatrix} \begin{bmatrix}
>>> c_{1} \\ c_{2}
>>>\end{bmatrix}
>>>\end{align}$$
>>>The inverse matrix for $t=0$ is given as
>>>>[!note]- Calculating the Inverse
>>>>We calculate the inverse of the matrix for $t=0$
>>>>$$\begin{alignat}{2}
>>>>\begin{bmatrix}
>>>> 2 & 1 \\
>>>> 1 & 2
>>>>\end{bmatrix}^{-1}  \implies  
>>>>&\left[\begin{array}{cc|cc}
>>>> 2 & 1  & 1 & 0 \\
>>>> 1 & 2 & 0 & 1
>>>>\end{array}\right] \qquad\qquad&&[\text{1. Line}] \cdot \frac{1}{2}\\
>>>>\Longleftrightarrow&\left[\begin{array}{cc|cc}
>>>> 1 & \frac{1}{2}  & \frac{1}{2} & 0 \\
>>>> 1 & 2 & 0 & 1
>>>>\end{array}\right] \qquad\qquad&&(2)=(2)-(1)\\
>>>>\Longleftrightarrow&\left[\begin{array}{cc|cc}
>>>> 1 & \frac{1}{2}  & \frac{1}{2} & 0 \\
>>>> 0 & \frac{3}{2} & -\frac{1}{2} & 1
>>>>\end{array}\right] \qquad\qquad&&[\text{2. Line}] \cdot \frac{1}{3}\\
>>>>\Longleftrightarrow&\left[\begin{array}{cc|cc}
>>>> 1 & \frac{1}{2}  & \frac{1}{2} & 0 \\
>>>> 0 & \frac{1}{2} & -\frac{1}{6} & \frac{1}{3}
>>>>\end{array}\right] \qquad\qquad&&(1)=(1)-(2)\\
>>>>\Longleftrightarrow&\left[\begin{array}{cc|cc}
>>>> 1 & 0  & \frac{2}{3} & -\frac{1}{3} \\
>>>> 0 & \frac{1}{2} & -\frac{1}{6} & \frac{1}{3}
>>>>\end{array}\right] \qquad\qquad&&[\text{2. Line}] \cdot 2\\
>>>>\Longleftrightarrow&\left[\begin{array}{cc|cc}
>>>> 1 & 0  & \frac{2}{3} & -\frac{1}{3} \\
>>>> 0 & 1 & -\frac{1}{3} & \frac{2}{3}
>>>>\end{array}\right] \qquad\qquad&&\\
>>>>X(0)^{-1}=&\begin{bmatrix} 
>>>>  \frac{2}{3} & -\frac{1}{3} \\ 
>>>> -\frac{1}{3} & \frac{2}{3}
>>>>\end{bmatrix} \\
>>>> =& \frac{1}{3} \begin{bmatrix} 
>>>>  2 & -1 \\ 
>>>> -1 & 2
>>>>\end{bmatrix} 
>>>>\end{alignat}$$
>>>$$\begin{align}
>>> X(0)^{-1} =& \frac{1}{3} \begin{bmatrix} 
>>>  2 & -1 \\ 
>>> -1 & 2
>>>\end{bmatrix} 
>>>\end{align}$$
>>> We get
>>> $$\begin{alignat}{2}
>>> \mathbf{x}(0) &= X(0)\mathbf{c} \qquad&&\Big\vert X(0)^{-1}\cdot \\
>>> X(0)^{-1}\mathbf{x}(0) &= \mathbf{c}  \\
>>> \frac{1}{3} \begin{bmatrix} 
>>>  2 & -1 \\ 
>>> -1 & 2
>>>\end{bmatrix} \begin{bmatrix}
>>> 1 \\ 5
>>>\end{bmatrix} &= \begin{bmatrix}
>>>c_{1} \\ c_{2}
>>>\end{bmatrix} \\
>>> \frac{1}{3} \begin{bmatrix}
>>> 2-5 \\ -1+10
>>>\end{bmatrix} &= \begin{bmatrix}
>>>c_{1} \\ c_{2}
>>>\end{bmatrix}\\
>>>\frac{1}{3} \begin{bmatrix}
>>> -3 \\ 9
>>>\end{bmatrix} &= \begin{bmatrix}
>>>c_{1} \\ c_{2} \\
>>>\end{bmatrix}\\
>>> \begin{bmatrix}
>>> -1 \\ 3
>>>\end{bmatrix} &= \begin{bmatrix}
>>>c_{1} \\ c_{2} \\
>>>\end{bmatrix}\\
>>>\end{alignat}$$
>>>Now we can state
>>>$$\begin{align}
>>>c_{1} &= -1 \\
>>>c_{2} &= 3
>>>\end{align}$$
>>>Then the unique solution to the initial value problem can be given as
>>>$$\mathbf{x}(t)= -\begin{bmatrix}
>>> 2 \\ 1
>>>\end{bmatrix}e^{2t}+3\begin{bmatrix}
>>> 1 \\ 2
>>>\end{bmatrix}e^{-t}$$
>>>

### 5.1.5 Wronskian and Abel's Theorem

>[!def] Definition Solution Matrix and Wronskian ([[../../../PDFs/nagy.pdf#page=250| Source]])
>1. A **solution matrix** of any set of vector function $\{ \mathbf{x}^{(1)}, \dots, \mathbf{x}^{n} \}$, solutions to a differential equation $\mathbf{x}' = A\mathbf{x}$, is the $n \times n$ matrix valued function
>$$X(t)= \left[\mathbf{x}^{(1)}(t), \dots, \mathbf{x}^{(n)}(t)\right]$$
>$X$ is called a **fundamental matrix** iff the set $\{ \mathbf{x}^{(1)},\dots,\mathbf{x}^{(n)} \}$ is a fundamental set.
>2. The **Wronskian** of the set $\{ \mathbf{x}^{(1)}, \dots, \mathbf{x}^{n} \}$ is the function $$W(t)=\det (X(t))$$

^44918f

>[!theorem] Abel's Theorem  ([[../../../PDFs/nagy.pdf#page=251| Source]])
>The Wronskian function $W = \det(X(t))$ of a solution matrix $X = \left[\mathbf{x}^{(1)}, \dots, \mathbf{x}^{(n)}\right]$ of the linear system $\mathbf{x}'=A(t)\mathbf{x}$, where $A$ is an $n \times n$ continuous matrix valued function on a domain $I \subset \mathbb{R}$, satisfies the differential equation
>$$W'(t)= \mathrm{tr}\Big(A(t)\Big)W(t)$$
>Hence $W$ is given by
>---
>$$W(t)=W(t_{0})e^{\alpha(t)}$$
>with
>$$\alpha(t)=\int _{t_{0}}^t \mathrm{tr}(A(\tau)) \, d\tau $$
>
>---
>where $t_{0}$ is any point in $I$
>>[!proof] Proof ([[../../../PDFs/nagy.pdf#page=252| omitted]])

## 5.2 Solution Formulas

>[!theorem] Theorem Homogeneous Systems ([[../../../PDFs/nagy.pdf#page=255| Source]])
>If $A$ is an $n \times n$ matrix, $t_{0} \in \mathbb{R}$ is an arbitrary constant and $\mathbf{x}_{0} \in \mathbb{R}^n$ constant, then the initial value problem for the unknown $n$-vector valued function $\mathbf{x}$ given by
>$$\mathbf{x}'=A\mathbf{x} \qquad \mathbf{x}(t_{0})=\mathbf{x}_{0}$$ 
>has a unique solution given by the formula
>
>---
>$$\mathbf{x}(t)=e^{A(t-t_{0})}\mathbf{x}_{0}$$
>
>---
>>[!remark]- Remark Matrix Exponential
>>Information about the [[A - Matrix Exponential| matrix exponential]] involves
>>- [[A - Matrix Exponential#^730bfa| the derivative of the matrix exponential]]
>> $$\frac{d}{dt}e^{At} = Ae^{At}= e^{At}A$$
>>- [[A - Matrix Exponential#^cd67f1| the inverse of the matrix exponential and its group properties]]
>>$$e^{As}e^{At} = e^{A(s+t)}$$
>
>>[!proof]-
>>We use the integrating factor method analogous to [[1 - First Order ODEs|first order ODEs]].
>>$$\begin{alignat}{2}
>> \mathbf{x}' &= A\mathbf{x} \qquad&&\\ 
>> \mathbf{x}' -A\mathbf{x} &= 0 \qquad&&\Big\vert\cdot e^{-At}  \\
>> e^{-At}\mathbf{x}' -e^{-At}A\mathbf{x} &= 0 \tag{3}
>>\end{alignat}$$
>>Note, the expression $-e^{-At}A$ can be rearranged because $A$ commutes with itself by [[A - Matrix Exponential#^6ed8d5| the properties of the matrix exponential]].
>>$$-e^{-At}A = -Ae^{-At}$$
>>Further note, this is the [[A - Matrix Exponential#^730bfa|derivative]] of $e^{-At}$, i.e.
>>$$\frac{d}{dt}e^{-At} = (e^{-At})'  = -Ae^{-At}$$
>>We insert this result into equation $(3)$
>>$$\begin{align}
>> e^{-At}\mathbf{x}' -(e^{-At})'\mathbf{x} &= 0
>>\end{align}$$
>>Note, that this expression is the result of the product rule, i.e.
>>$$(e^{-At}\mathbf{x})' = 0$$
>>We integrate both sides with respect to $t$ and get
>>$$\begin{align}
>>e^{-At}\mathbf{x} &= \mathbf{c} \\
>> \mathbf{x} &= e^{At}\mathbf{c}
>>\end{align}$$
>>We now evaluate at $t=t_{0}$ with $\mathbf{x}(t_{0})=\mathbf{x_{0}}$ and get
>>$$\begin{align}
>> \mathbf{x}_{0} &= e^{At_{0}}\mathbf{c} \\
>> e^{-At_{0}}\mathbf{x}_{0} &= \mathbf{c} 
>>\end{align}$$
>>which solves the unique value problem.
>>$$\tag*{$\square$}$$
>
>>[!example]
>>Compute the exponential function $e^{At}$ and use it to express the vector-valued function $\mathbf{x}$ solution to the initial value problem
>>$$\begin{align}
>> \mathbf{x}' &= A\mathbf{x} \\
>> A &= \begin{bmatrix}
>> 1 & 2  \\
>> 2 & 1
>>\end{bmatrix} \\
>> \mathbf{x}(0) &= \mathbf{x}_{0} =[x_{0_{1}}, x_{0_{2}}]^T 
>>\end{align}$$
>>>[!example]- Solution
>>>First, we need to think about how to solve the matrix exponential into a pure matrix form. Checking the properties of the [[A - Matrix Exponential| matrix exponential]] we find, that the exponential is easy to compute for [[A - Matrix Exponential#^5c6d39| diagonal matrices]]. We also know for full rank matrices, we can [[../Linear Algebra/Eigenvectors and Eigenvalues#^3b9ec0|decompose]] them in a diagonal matrix of eigenvalues and a matrix of corresponding eigenvectors.
>>>
>>>Hence, we compute first the eigenvalues of $A$. Therefore, we solve
>>>$$\begin{align}
>>> \det(A-\lambda I) &= \begin{vmatrix}
>>> 1-\lambda & 2 \\ 2 & 1-\lambda \\
>>>\end{vmatrix} \\
>>> &= (1-\lambda)^2-4
>>>\end{align}$$
>>>This characteristic polynomial can be solved easily with
>>>$$\begin{align}
>>> \lambda_{1} &= -1 \\
>>> \lambda_{2} &= 3
>>>\end{align}$$
>>>The eigenvectors can be found solving
>>>$$\begin{align}
>>> A\mathbf{x}&=\lambda \mathbf{x} \\
>>> (A-\lambda I)\mathbf{x} &= 0
>>>\end{align}$$
>>>for each $\lambda$
>>>>[!note]- Calculations
>>>>First we solve for $\lambda_1=-1$
>>>>$$\begin{align}
>>>> \begin{bmatrix}
>>>> 1 & 2 \\ 2 & 1
>>>>\end{bmatrix} - \begin{bmatrix}
>>>> -1 & 0 \\ 0 & -1
>>>>\end{bmatrix}\begin{bmatrix}
>>>> x_{1} \\ x_{2}
>>>>\end{bmatrix} &= 0  \\
>>>> \begin{bmatrix}
>>>> 2 & 2 \\ 2 & 2
>>>>\end{bmatrix}\begin{bmatrix}
>>>> x_{1} \\ x_{2}
>>>>\end{bmatrix}&= 0 \\
>>>> \begin{bmatrix}
>>>> 1 & 1 \\ 0 & 0
>>>>\end{bmatrix}\begin{bmatrix}
>>>> x_{1} \\ x_{2}
>>>>\end{bmatrix}&= 0 \\[1em]
>>>> \implies x_{1}+x_{2}&=0 \\
>>>> x_{1} &= -x_{2}
>>>>\end{align}$$
>>>>So we choose
>>>> $$\mathbf{x}_{1} = \begin{bmatrix}
>>>> 1 \\ -1
>>>>\end{bmatrix}$$
>>>>Now we solve for $\lambda_{2}=3$
>>>>$$\begin{align} \\
>>>> \begin{bmatrix}
>>>> 1 & 2 \\ 2 & 1
>>>>\end{bmatrix} - \begin{bmatrix}
>>>> 3 & 0 \\ 0 & 3
>>>>\end{bmatrix}\begin{bmatrix}
>>>> x_{1} \\ x_{2}
>>>>\end{bmatrix} &= 0   \\
>>>> \begin{bmatrix}
>>>> -2 & 2 \\ 2 & -2
>>>>\end{bmatrix}\begin{bmatrix}
>>>> x_{1} \\ x_{2}
>>>>\end{bmatrix} &= 0   \\
>>>> \begin{bmatrix}
>>>> -2 & 2 \\ 0 & 0
>>>>\end{bmatrix}\begin{bmatrix}
>>>> x_{1} \\ x_{2}
>>>>\end{bmatrix} &= 0  \\
>>>> \begin{bmatrix}
>>>> -1 & 1 \\ 0 & 0
>>>>\end{bmatrix}\begin{bmatrix}
>>>> x_{1} \\ x_{2}
>>>>\end{bmatrix} &= 0   \\[1em]
>>>> \implies x_{1}+x_{2}&=0 \\
>>>> x_{1} &= x_{2}
>>>>\end{align}$$
>>>>So we choose $$\mathbf{x}_{2} = \begin{bmatrix}
>>>> 1 \\ 1
>>>>\end{bmatrix}$$
>>>
>>>The eigenvectors are
>>>$$\begin{align}
>>> \mathbf{x}_{1} &= [1, -1]^T \\
>>> \mathbf{x}_{2} &= [1,1]^T
>>>\end{align}$$
>>>Therefore we can give the diagonal matrix $D$ and the matrix of eigenvectors $P$ as
>>>$$\begin{align}
>>> D &= \begin{bmatrix}
>>>   -1 & 0 \\ 0 & 3
>>>\end{bmatrix} \\
>>> P &= \begin{bmatrix}
>>> 1 & 1 \\ -1 & 1
>>>\end{bmatrix} \\
>>>\end{align}$$
>>>We also need the inverse of $P$ 
>>>>[!note]- Calculations
>>>>$$\begin{align}
>>>>\left[\begin{array}{cc|cc}
>>>> 1 & 1 & 1& 0 \\
>>>> -1 & 1 & 0 & 1
>>>>\end{array}\right]&\Longleftrightarrow \left[\begin{array}{cc|cc}
>>>> 1 & 1 & 1& 0 \\
>>>> 0 & 2 & 1 & 1
>>>>\end{array}\right] \\
>>>>&\Longleftrightarrow \left[\begin{array}{cc|cc}
>>>> 1 & 1 & 1& 0 \\
>>>> 0 & 1 & \frac{1}{2} & \frac{1}{2}
>>>>\end{array}\right] \\
>>>>&\Longleftrightarrow \left[\begin{array}{cc|cc}
>>>> 1 & 0 & \frac{1}{2}& -\frac{1}{2} \\
>>>> 0 & 1 & \frac{1}{2} & \frac{1}{2}
>>>>\end{array}\right]
>>>>\end{align}$$
>>>>The inverse therefore is
>>>>$$P^{-1} = \frac{1}{2}\begin{bmatrix}
>>>>1& -1 \\1 & 1
>>>>\end{bmatrix}$$
>>>
>>>By [[A - Matrix Exponential#^56ae16| the decomposition theorem for matrix exponentials]] we can write
>>>$$\begin{align}
>>> e^{At}&=Pe^{Dt}P^{-1} \\
>>>   &=\begin{bmatrix}
>>> 1 & 1 \\ -1 & 1
>>>\end{bmatrix} e^{Dt}\frac{1}{2}\begin{bmatrix}
>>>1& -1 \\1 & 1
>>>\end{bmatrix}
>>>\end{align}$$
>>>where $e^{Dt}$ can be written in [[A - Matrix Exponential#^5c6d39| diagonal form]]. Therefore, we have
>>>$$\begin{align}
>>> e^{At} &=\frac{1}{2}\begin{bmatrix}
>>> 1 & 1 \\ -1 & 1
>>>\end{bmatrix} \begin{bmatrix}
>>>e^{-t} & 0 \\ 0 & e^{3t}
>>>\end{bmatrix}\begin{bmatrix}
>>>1& -1 \\1 & 1
>>>\end{bmatrix} \\
>>> &= \frac{1}{2}\begin{bmatrix}
>>> e^{-t} & e^{3t} \\ -e^{-t} & e^{3t}
>>>\end{bmatrix}\begin{bmatrix}
>>>1& -1 \\1 & 1
>>>\end{bmatrix} \\
>>> &= \frac{1}{2}\begin{bmatrix}
>>> e^{-t}+e^{3t} & -e^{-t} + e^{3t} \\ -e^{-t}+e^{3t} & e^{-t}+e^{3t}
>>>\end{bmatrix}
>>>\end{align}$$

>[!theorem] Theorem Homogeneous Diagonalizable Systems ([[../../../PDFs/nagy.pdf#page=258| Source]])
>If the $n \times n$ constant matrix $A$ is diagonalizable, with a set of linearly independent eigenvectors $\{ \mathbf{v}^{(1)}, \dots, \mathbf{v}^{(n)} \}$ and corresponding eigenvalues $\{ \lambda_{1}, \dots, \lambda_{n} \}$ then the system
>$$\mathbf{x}' = A\mathbf{x}$$
>has a general solution
>---
>$$\mathbf{x}_{gen}(t)= c_{1}e^{\lambda_{1}t}\mathbf{v}^{(1)}+\dots+c_{n}e^{\lambda_{n}t}\mathbf{v}^{(n)}$$
>
>---
>Furthermore, every initial value problem 
>$$\mathbf{x}'(t)=A\mathbf{x}(t)$$
>with $\mathbf{x}(t_{0})=\mathbf{x}_{0}$ has a unique solution for every initial condition $\mathbf{x}_{0}\in \mathbb{R}^n$, where the constants $c_{1}, \dots, c_{n}$ are solutions of the algebraic linear system
>$$\mathbf{x}_{0} = c_{1}e^{\lambda_{1}t_{0}}\mathbf{v}^{(1)}+ \dots + c_{n}e^{\lambda_{1}t_{0}}\mathbf{v}^{(n)}$$
>>[!remark]
>>This theorem follows the idea of **decoupling equations**.
>>>[!example]-
>>>$$\begin{align}
>>> x_{1}' &= x_{1}-x_{2} \\
>>> x_{2}' &= -x_{1}+x_{2}
>>>\end{align}$$
>>>Adding $(1)$ and subtracting $(2)$ both equations yield
>>>$$\begin{align}
>>> (x_{1}+x_{2})' &= 0 \tag{1} \\
>>> (x_{1}-x_{2})' &= 2(x_{1}-x_{2}) \tag{2}
>>>\end{align}$$
>>>Now, lets denote $$\begin{align}
>>> y_{1}&=x_{1}+x_{2}  \tag{3}\\
>>> y_{2}&=x_{1}-x_{2} \tag{4}
>>>\end{align}$$
>>>and substitute
>>>$$\begin{align}
>>>y_{1}' &= 0 \\
>>> y_{2}' &= 2y_{2}
>>>\end{align}$$
>>>This is the **decoupled representation of the original system**. Each equation can now be solved independently.
>>>$$\begin{align}
>>> y_{1}&=c_{1} \\
>>> y_{2}&=c_{2}e^{2t}
>>>\end{align}$$
>>>Solving equations $(3)$ and ($4$) for $x_1$ and $x_2$ gives
>>>$$\begin{align}
>>> x_{1} &= \frac{1}{2}(y_{1} + y_{2})  \\
>>> x_{2} &= \frac{1}{2}(y_{1}-y_{2})
>>>\end{align}$$
>>>and we get the solutions
>>>$$\begin{align}
>>> x_{1}(t) &= \frac{1}{2}(c_{1}+c_{2}e^{2t}) \\
>>> x_{2}(t) &= \frac{1}{2}(c_{1}-c_{2}e^{2t})
>>>\end{align}$$
>
>>[!proof]- Validation Proof
>> Note, each function
>> $$\mathbf{x}^{(i)}= e^{\lambda_{i}t}\mathbf{v}^{(i)} \tag{1}$$
>> is solution of the system
>> $$\mathbf{x}^{(i)'}=A\mathbf{x}^{(i)}$$
>> We first work on equation $(1)$
>> $$\begin{alignat}{2}
>> \mathbf{x}^{(i)}&= e^{\lambda_{i}t}\mathbf{v}^{(i)} \qquad&&\Big\vert \frac{d}{dt} \\
>> \mathbf{x}^{(i)'}&= \lambda_{i}e^{\lambda_{i}t}\mathbf{v}^{(i)} \tag{2} \\
>>\end{alignat}$$
>>and
>>$$\begin{alignat}{2}
>> \mathbf{x}^{(i)} &= e^{\lambda_{i}t}\mathbf{v}^{(i)} \qquad&&\Big\vert A \cdot \\
>> A\mathbf{x}^{(i)} &= A(e^{\lambda_{i}t}\mathbf{v}^{(i)}) \\
>> A\mathbf{x}^{(i)} &= e^{\lambda_{i}t} \underbrace{ A \mathbf{v}^{(i)} }_{ =\lambda_{i}\mathbf{v}^{(i)} } \tag{Eigenvector Def} \\
>> A\mathbf{x}^{(i)} &=e^{\lambda_{i}t}\lambda_{i}\mathbf{v}^{(i)} \tag{3}
>>\end{alignat}$$
>>Note that the expressions $(2)$ and $(3)$ are equal, hence
>>$$\mathbf{x}^{(i)'}=e^{\lambda_{i}t}\lambda_{i}\mathbf{v}^{(i)}$$
>> Integrating gives
>> $$\mathbf{x}^{(i)} = c_{i}e^{\lambda_{i}t}\mathbf{v}^{(i)}$$
>>
>>Note, $A$ is a diagonalizable matrix, hence, the solution set can be given as
>>$$\{ \mathbf{x}¹, \dots, \mathbf{x}^n \} = \{ c_{1}e^{\lambda_{1}t}\mathbf{v}^{(1)}, \dots, c_{n}e^{\lambda_{n}t}\mathbf{v}^{(n)} \}$$
>>therefore, the general solution can be given the [[#^7e6f96| superposition principle]] as 
>>$$\mathbf{x}_{gen}(t)  = c_{1}e^{\lambda_{1}t}\mathbf{v}^1+\dots+c_{n}e^{\lambda_{n}t}\mathbf{v}^{(n)}$$
>>with constants $c_{i}$ being determined by solving the initial value problem at $t_{0}=0$ ($\mathbf{x}(t_{0})=\mathbf{x}_{0})$. $$\tag*{$\square$}$$
>
>>[!proof]- Constructive Proof
>>First we use the property that $A$ is diagonalizable, hence
>>$$A = PDP^{-1}$$
>>with $P$ being an invertible matrix. We take the original equation and substitute
>>$$\begin{alignat}{2}
>> \mathbf{x}' &= A\mathbf{x}  \\
>> \mathbf{x}' &= PDP^{-1}\mathbf{x}  \qquad&&\Big\vert P^{-1}\cdot  \\
>> P^{-1}\mathbf{x}' &= \underbrace{ P^{-1}P }_{ =I }DP^{-1}\mathbf{x}    \\
>>\end{alignat}$$
>>Note, A is a constant matrix, therefore, $P, P^{-1}, D$ are constant too. We continue to work the equation
>>$$\begin{align}
>> (P^{-1}\mathbf{x})' &= DP^{-1}\mathbf{x}    \\
>>\end{align}$$
>>We now define the variable $\mathbf{y} = (P^{-1}\mathbf{x})$ and get
>>$$\mathbf{y}' = D\mathbf{y}$$
>>Since the matrix $D$ is diagonal, we notice **the system is decoupled**.
>>$$\begin{align}
>> \begin{Bmatrix}
>> y_{1}' = \lambda_{1}y_{1} \\
>> \vdots \\
>> y_{n} =\lambda_{n}y_{n}
>>\end{Bmatrix} \implies \begin{Bmatrix}
>> y_{1} = c_{1}e^{\lambda_{1}t} \\
>> \vdots \\
>> y_{n} = c_{n}e^{\lambda_{n}t}
>>\end{Bmatrix} \implies \mathbf{y} = \begin{bmatrix}
>> c_{1}e^{\lambda_{1}t} \\
>> \vdots \\
>> c_{n}e^{\lambda_{n}t}
>>\end{bmatrix}
>>\end{align}$$
>>Having solved for $\mathbf{y}$ we can transform back to the $\mathbf{x}$ representation
>>$$\begin{align}
>> \mathbf{x} &= P\mathbf{y} \\
>>   &= \Big[\mathbf{v}^{(1)}, \dots, \mathbf{v}^{(1)}\Big]\begin{bmatrix}
>>c_{1}e^{\lambda_{1}t} \\
>> \vdots \\
>> c_{n}e^{\lambda_{n}t}
>>\end{bmatrix} \\
>> &= c_{1}e^{\lambda_{1}t_{0}}\mathbf{v}^{(1)}+ \dots + c_{n}e^{\lambda_{1}t_{0}}\mathbf{v}^{(n)}
>>\end{align}$$
>>Evaluating at $t_0$ automatically yields the IVP formula. $$\tag*{$\square$}$$
>
>>[!example]
>>Find the vector valued function $\mathbf{x}$ solution to the differential system
>>$$\begin{align}
>> \mathbf{x}' &= A\mathbf{x} \\
>> \mathbf{x}(0) &= \begin{bmatrix}
>> 3 \\ 2
>>\end{bmatrix} \\
>> A &= \begin{bmatrix}
>> 1 & 2 \\ 2 & 1
>>\end{bmatrix}
>>\end{align}$$
>>>[!example]- Solution
>>> We first confirm, that $A$ is diagonalizable by computing the eigenvalues and eigenvectors.
>>> $$\begin{align}
>>> \det(A- \lambda I) &= \begin{vmatrix}
>>> 1- \lambda & 2  \\
>>> 2 & 1-\lambda
>>>\end{vmatrix} \\
>>> &= (1-\lambda)^2 -4
>>>\end{align}$$
>>>It can easily be seen that the eigenvalues are
>>>$$\begin{align}
>>> \lambda_{1} &= -1 \\
>>> \lambda_{2} &= 3
>>>\end{align}$$
>>>The eigenvectors have already been computed in [[#^abe58b|the example of the previous theorem]]. We state them
>>>$$\begin{align}
>>> \mathbf{x}_{1} &= [1, -1]^T \\
>>> \mathbf{x}_{2} &= [1,1]^T
>>>\end{align}$$
>>>Now we can state the general solution
>>>$$\mathbf{x}_{gen}(t) = c_{1}e^{-t}[1, -1]^T + c_{2}e^{3t}[1,1]^T$$
>>>Inserting the initial conditions $t=0$ we get
>>>$$\begin{align}
>>> c_{1} \begin{bmatrix}
>>> 1 \\ -1
>>>\end{bmatrix} + c_{2} \begin{bmatrix}
>>>  1 \\ 1
>>>\end{bmatrix} &= \begin{bmatrix}
>>> 3 \\ 2
>>>\end{bmatrix}  \\
>>> \begin{bmatrix}
>>> 1 & 1 \\ -1 & 1
>>>\end{bmatrix} \begin{bmatrix}
>>>  c_{1}  \\ c_{2}
>>>\end{bmatrix} &= \begin{bmatrix}
>>> 3 \\ 2
>>>\end{bmatrix} \\  
>>> \begin{bmatrix}
>>>  c_{1}  \\ c_{2}
>>>\end{bmatrix} &= \frac{1}{2}\begin{bmatrix}
>>> 3 \\ 2
>>>\end{bmatrix} \begin{bmatrix}
>>>1& -1 \\1 & 1 \end{bmatrix} \\
>>> \begin{bmatrix}
>>>  c_{1}  \\ c_{2}
>>>\end{bmatrix} &= \begin{bmatrix}
>>> \frac{5}{2} \\ -\frac{1}{2}
>>>\end{bmatrix}
>>>\end{align}$$
>>>Inserting this into the _general solution_ we get
>>>$$\begin{align}
>>> \mathbf{x}(t) = \frac{1}{2}\begin{bmatrix}
>>>5e^{3t} + e^{-t} \\ 5e^{3t}-e^{-t} \end{bmatrix}
>>>\end{align}$$

^abe58b

>[!theorem] Theorem Fundamental Matrix Expression ([[../../../PDFs/nagy.pdf#page=261| Source]])
>If the $n\times n$ constant matrix $A$ is diagonalizable, with a set of linearly independent eigenvectors $\{ \mathbf{v}^{(1)}, \dots ,\mathbf{v}^{(n)} \}$ and corresponding eigenvalues $\{ \lambda_{1}, \dots , \lambda_{n} \}$, then, the initial value problem
>$$\mathbf{x}' = A\mathbf{x}$$
>with
>$$\mathbf{x}(t_{0})=\mathbf{x}_{0}$$
>has a unique solution given by
>---
>$$\mathbf{x}(t)=X(t)X(t_{0})^{-1}\mathbf{x}_{0}$$
>
>---
>where $X(t)= \big[e^{\lambda_{1}t}\mathbf{v}^{(1)},\dots,e^{\lambda_{n}t}\mathbf{v}^{(n)}\big]$ is a fundamental matrix of the system.
>>[!proof]-
>> For the system of equations
>> $$\mathbf{x}' = A\mathbf{x}$$
>> we have the solution set
>> $$\left\{\begin{matrix}
>> \mathbf{x}^{(1)} = e^{\lambda_{1}t}\mathbf{v}^{(1)}&, \\
>> \vdots&, \\
>> \mathbf{x}^{(n)} = e^{\lambda_{n}t}\mathbf{v}^{(n)}
>>\end{matrix}\right\}$$
>>Therefore the [[#^44918f| fundamental matrix]] can be given as
>>$$X(t)= \big[e^{\lambda_{1}t}\mathbf{v}^{(1)}, \dots, e^{\lambda_{n}t}\mathbf{v}^{(n)}\big]$$
>>Hence, the general solution can be given as 
>>$$\begin{align}
>> \mathbf{x}_{gen}(t)&= c_{1}e^{\lambda_{1}t}\mathbf{v}^{(1)}+\dots+c_{n}e^{\lambda_{n}t}\mathbf{v}^{(n)} \\
>> &= X(t)\mathbf{c} \tag{1}
>>\end{align}$$
>>We now insert the initial condition $t_{0}$ and solve for $c$
>>$$\begin{alignat}{2}
>> \mathbf{x}_{0} &= X(0)\mathbf{c} \qquad&&\Big\vert X^{-1}(0)\cdot \\
>> X^{-1}(0)\mathbf{x}_{0} &= \mathbf{c}
>>\end{alignat}$$
>>Substituting $c$ in equation $(1)$ gives
>>$$\begin{align}
>> \mathbf{x}_{0}(t) &=  X(0)X^{-1}(0)\mathbf{x}_{0} \tag*{$\square$}
>>\end{align}$$

^c0156d

>[!theorem] Theorem Exponential for Diagonalizable Systems ([[../../../PDFs/nagy.pdf#page=263| Source]])
> If an $n \times n$ matrix $A$ has linearly independent eigenvector $\{ \mathbf{v}_{1}^{(1)}, \dots, \mathbf{v}_{n}^{(n)} \}$ with corresponding eigenvalues $\{ \lambda_{1}, \dots, \lambda_{n} \}$, then
> ---
> $$e^{A(t-t_{0})} = X(t)X(t_{0})^{-1}$$
>
>---
>where $X(t)= \big[e^{\lambda_{1}t}\mathbf{v}^{(1)},\dots,e^{\lambda_{n}t}\mathbf{v}^{(n)}\big]$
>>[!proof]-
>>We rewrite the [[#^44918f| fundamental matrix]]
>>$$\begin{align}
>> X(t) &= \big[e^{\lambda_{1}t}\mathbf{v}^{(1)},\dots,e^{\lambda_{n}t}\mathbf{v}^{(n)}\big] \\
>> &= [\mathbf{v}^{(1)}, \dots, \mathbf{v}^{(n)}]\begin{bmatrix}
>> e^{\lambda_{1}t} &\dots& 0 \\ \vdots & \ddots & \vdots \\ 0 & \dots & e^{\lambda_{n}t}
>>\end{bmatrix} \\
>> &= [\mathbf{v}^{(1)}, \dots, \mathbf{v}^{(n)}] \mathrm{diag}\left(e^{\lambda_{1}t}, \dots, e^{\lambda_{n}t}\right)
>>\end{align}$$
>>By the [[#^740a1c| diagonalization theorem]] we can rewrite the diagonal matrix as
>>$$\begin{align}
>>\phantom{X(t)} &= [\mathbf{v}^{(1)}, \dots, \mathbf{v}^{(n)}] e^{Dt} \phantom{aaaaaaaaaaaaa} \\
>>\end{align}$$
>>with $Dt= \mathrm{diag}\left(\lambda_{1}t\dots,\lambda_{n}t \right)$. Further, we denote $P=[\mathbf{v}^{(1)}, \dots, \mathbf{v}^{(n)}]$ and get
>>$$X(t) = P e^{Dt} \phantom{aaaaaaaaaaaaaaaaaaaaaaa,}\tag{1}$$
>>We now take the inverse on both sides for $t_0$ and use the property of [[../Linear Algebra/Basics#^5457a2|the inverse of matrix products]]
>>$$\begin{align}
>> X(t_{0})^{-1} &= \big(Pe^{Dt_{0}}\big)^{-1} \phantom{aaaaaaaaaaaaaaaaaaaaaa} \\ 
>> X(t_{0})^{-1} &= e^{-Dt_{0}}P^{-1} \tag{2}
>>\end{align}$$
>>We now calculate the product $X(t)X(t_0)^{-1}$ and use the results of equation $(1)$ and $(2)$
>>$$\begin{align}
>> X(t)X(t_0)^{-1} &= P e^{Dt} e^{-Dt_{0}}P^{-1}  \phantom{aaaaaaaaaaaaaaaaaaaaaaa}\\
>> &= P e^{D(t-t_{0})} P^{-1} 
>>\end{align}$$
>>Since $A$ is diagonalizable we can make use of the [[A - Matrix Exponential#^3c5427|diagonalization property of matrix exponentials]], i.e.
>>$$\begin{align}
>> e^{A(t-t_{0})} = P e^{D(t-t_{0})} P^{-1} \phantom{aaaaaaaaaaaaaaaaaaaa} \\
>>\end{align}$$
>>We finally get the desired result
>>$$X(t)X(t_0)^{-1}=e^{A(t-t_{0})} \phantom{aaaaaaaaaaaaaaaaaaaaaaaaaaaaaa}\tag*{$\square$}$$


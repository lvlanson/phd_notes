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
>>- $\mathbf{b} = 0$ ANDl
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

^2e3cb4

>[!remark]
>There exists a correspondence between $n \times n$ systems of linear differential equations and $n$-th order differential equations.

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

>[!theorem] Theorem Second Order Reduction ([[../../../PDFs/nagy.pdf#page=244| Source]])
>Any $2 \times 2$ constant coefficients linear system
>$$\begin{align}
> \mathbf{x}'=A\mathbf{x}
>\end{align}$$
>with $\mathbf{x}=\begin{bmatrix} x_1 \\ x_2\end{bmatrix}$ can be written as second order equations for $x_{1}$ and $x_{2}$
>$$\mathbf{x}''  - \mathrm{tr}(A)\mathbf{x}' + \det(A)\mathbf{x}=\mathbf{0} \tag{1}$$
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
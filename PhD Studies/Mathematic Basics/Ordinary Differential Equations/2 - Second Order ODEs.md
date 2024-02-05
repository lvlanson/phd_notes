## 2.1 Variable Coefficients

>[!def] Definition Second Order Linear Differential Equations ([[../../../Sources/nagy.pdf#page=86 | Source]])
>A **second order linear differential equation** for the function $y$ is
>$$y'' + a_{1}(t) y' + a_{0}(t)y = b(t)$$
>where $a_{1}, a_{0}, b$ are given functions on the interval $I \subset \mathbb{R}$. The equation above 
>1. is **homogeneous** iff the source $b(t)=0$ for all $t \in\mathbb{R}$
>2. has **constant coefficients** iff $a_1$ and $a_{0}$ are constants
>3. has **variable coefficients** iff either $a_1$ or $a_{0}$ is not constant
>
>>[!example]-
>>1. second order, linear, homogeneous, constant coefficients$$y'' + 5y' +  6 = 0$$ 
>>2. second order, linear, non-homogeneous, constant coefficients$$y'' - 3y' + y = \cos(3t)$$
>>3. second order, linear, non-homogeneous, variable coefficients$$y'' + 2ty' - \ln(t)y = e^{3t}$$

>[!example]- Task Find the differential equation satisfied by the family of functions $y(t)=c_{1}e^{4t}+c_{2}e^{-4t}$
> We first solve for $c_1$
> $$\begin{alignat}{2}
> y &= c_{1}e^{4t}+c_{2}e^{-4t} \qquad&&\Big\vert \cdot e^{-4t} \\
> ye^{-4t} &= c_{1}+c_{2}e^{-8t} \qquad&&\Big\vert -c_{2}e^{-8t} \\
> c_{1} &= ye^{-4t}-c_{2}e^{-8t} \qquad&&\Big\vert -c_{2}e^{-8t} \tag{1}\\
>\end{alignat}$$
>Now we compute the derivative of $y$
>$$\begin{align}
> \frac{dy}{dt} &=y'= 4c_{1}e^{4t}-4c_{2}e^{-4t} \tag{2}
>\end{align}$$
>Inserting the expression of $c_1$ in $(1)$ into $(2)$ gives
>$$\begin{align}
> y' &= 4(ye^{-4t}-c_{2}e^{-8t})e^{4t}-4c_{2}e^{-4t} \\
> &= 4ye^{0}-4c_{2}e^{-4t}-4c_{2}e^{-4t} \\
> &= 4y - 8c_{2}e^{-4t}
>\end{align}$$
> Solving for $c_2$ we get
> $$\begin{alignat}{2}
> y' &= 4y - 8c_{2}e^{-4t} \qquad&&\Big\vert -y' + 8c_{2}e^{-4t}  \\
> 8c_{2}e^{-4t} &= 4y-y' \qquad&&\Big\vert \cdot \frac{1}{8}e^{4t} \\
> c_{2} &= \frac{1}{8}e^{4t}(4y-y') \\
>\end{alignat}$$
>Taking now the derivative $\frac{d}{dt}$ removes the last remaining constant $c_2$ and yields the differential equation of second order
>$$\begin{alignat}{2}
>0 &= \frac{1}{2}e^{4t}(4y-y')+\frac{1}{8}e^{4t}(4y'-y'') \tag{Product + Chain Rule} \qquad&&\Big\vert \cdot 8e^{-4t} \\
>0 &= 4(4y-y')+(4y'-y'')   \\
>0 &= 16y\cancel{ -4y+4y' }-y'' \\
>0 &= 16y-y''   \\
>\end{alignat}$$

>[!example]- Task Find the differential equation satisfied by the family of functions $y(t)=\frac{c_{1}}{t}+c_{2}t$
>First, we take the derivative with respect to $t$
>$$\begin{align}
> y' = -\frac{c_{1}}{t^2}+c_{2}
>\end{align}$$
>Solving for $c_2$ gives
>$$c_{2} = \frac{c_{1}}{t^2}+y'$$
>Inserting this solution into the original equation gives
>$$\begin{align}
> y &= \frac{c_{1}}{t}+ \left( \frac{c_{1}}{t^2}+y' \right)t \\
>   &= \frac{c_{1}}{t}+ \frac{c_{1}}{t}+y't \\
>   &= \frac{2c_{1}}{t}+y't \\
> y-y't  &= 2c_{1}\\ 
> yt-y't^2  &= 2c_{1} \\ 
>\end{align}$$
>Taking now again the derivative with respect to $t$ yields
>$$\begin{align}
>y+y't-2y't-y''t^2 = 0 \\
>y-y't-y''t^2 = 0 \\
>\end{align}$$

>[!example]- Task Find the differential equation satisfied by the family of functions $y(x)=c_{1}x+c_{2}x^2$
> First we take the first derivative with respect to $x$, because solving for $c_1$ will be easy then
> $$\begin{align}
> y' &= c_{1 }+2c_{2}x\\
> y'-2c_{2}x &= c_{1}\\
>\end{align}$$
>Inserting this into the first equation gives
>$$\begin{align}
> y &= (y'-2c_{2}x)x + c_{2}x^2\\
> y &= y'x-2c_{2}x^2 + c_{2}x^2\\
> y &= y'x-c_{2}x^2 \\
> c_{2}x^2 &= y'x-y \\
> c_{2} &= y'\frac{1}{x}-y\frac{1}{x^2} \\
>\end{align}$$
>We take the derivative with respect to $x$ to obtain the ODE
>$$\begin{alignat}{2}
>0 &= y'' \frac{1}{x}-y' \frac{1}{x^2}-y' \frac{1}{x^2}+y \frac{2}{x^3} \qquad&&\\
>0 &= y'' \frac{1}{x}-y' \frac{2}{x^2}+y \frac{2}{x^3} \qquad&&\Big\vert \cdot x^3\\
>0 &= y''x^2 -2y'x +2y  \qquad&& \\
>\end{alignat}$$


>[!theorem] Theorem Solutions to IVP of Second Order ODEs ([[../../../Sources/nagy.pdf#page=88 | Source]])
>If 
>- the functions $a_{0},a_{1}, b$ are continuous on a closed interval $I \subset \mathbb{R}$, 
>- the constant $t_{0} \in I$, 
>- and $y_{0}, y_{1} \in \mathbb{R}$ are arbitrary constants
>
>then there is a unique solution $y$, defined on $I$, of the initial value problem
>$$y'' + a_{1}(t)y'+ a_{0}(t)y = b(t)$$
>with $$ y(t_{0})=y_{0} \quad y'(t_{0})= y_{1}$$
>>[!proof]-
>>Fixed point argument can be extended of [[1 - First Order ODEs#^2f934e| Picard-Lindelöf's theorem]].
>
>>[!example]-
>>Find the domain of the solution to the initial value problem 
>>$$(t-1)y''-3ty'+\frac{4(t-1)}{(t-3)}y=t(t-1)$$
>>with $y(2)=1$ and $y'(2)=0$
>>>[!example] Solution
>>>We rearrange to get the form of the theorem. We have
>>>$$\begin{alignat}{2}
>>>(t-1)y''-3ty'+\frac{4(t-1)}{(t-3)}y=t(t-1) \qquad&&\Big\vert :(t-1) \\
>>>y''-3ty'+\frac{4(t-1)}{(t-3)}y=t \qquad&&
>>>\end{alignat}$$
>>>Note, since we divided by $(t-1)$, we can not allow $t=1$. Further, since $(t-3)$ is in the denominator, $t=3$ is also disallowed. Therefore, we can state the domain of the equation coefficients as
>>>$$(-\infty,1) \cup (1,3)\cup(3,\infty)$$
>>>Since $t_{0}=2 \in (1,3)$, the domain is given as $$D=(1,3)$$ 
>>>>[!Note]
>>>> We require all parameters $a_0, a_{1}, b$ to be continuous on the same interval. Only $(1,3)$ suffices this condition, hence it is the sought solution

^786ff5

>[!proposition] Notation
>We introduce a new notation. Let $L$ be a function of $y$ and $a_{0}, a_{1}$ functions of $t$, then we write
>$$L(y) = y'' + a_{1}(t)y'+ a_{0}(t)y$$
>>[!example]- Example Compute the operator $L(y)=ty''+2y' - \frac{8}{t}y$ acting on $y(t)=t^3$
>>We insert the definition of $y$ into the operator $L$, we have
>>$$\begin{align}
>> L(t^3) &= t \left( \frac{d}{dt^2} t^3 \right) + 2 \left( \frac{d}{dt} t^3 \right) - \frac{8}{t}(t^3)  \\
>>       &= t (t^3)'' + 2(t^3)' - \frac{8}{t}(t^3) \\
>>       &= 6t^2  +6t^2 - 8t^2 \\
>>       &= 4t^2
>>\end{align}$$
>
>>[!note]
>>$L$ is an **operator**, because it takes a function $y$ as input. Since we are describing $L$ as a mapping of differentials on $y$, we call $L$ a **differential operator**.

>[!def] Definition Linear Operator ([[../../../Sources/nagy.pdf#page=89 | Source]])
>An operator $L$ is a **linear operator** iff for every pair of functions $y_{1},y_{2}$ and constants $c_{1}, c_{2}$ holds
>$$L(c_{1}y_{1}+ c_{2}y_{2}) = c_{1}L(y_{1})+ c_{2}L(y_{2})$$


>[!theorem] Theorem Linear Differential Operator ([[../../../Sources/nagy.pdf#page=89 | Source]])
>The operator $L(y)=y'' + a_{1}y' + a_{0}y$, where $a_{0},a_{1}$ are continuous functions and $y$ is a twice differentiable function, **is a linear operator**
>>[!proof]-
>>$$\begin{align}
>> L(c_{1}y_{1}+c_{2}y_{2}) &= (c_{1}y_{1}+c_{2}y_{2})'' + a_{1}(c_{1}y_{1}+c_{2}y_{2}) + a_{0}(c_{1}y_{1}+c_{2}y_{2}) \\
>>              &= c_{1}y_{1}'' +c_{2}y_{2}'' + a_{1}c_{1}y_{1}'+a_{1}c_{2}y_{2}' + a_{0}c_{1}y_{1}+ a_{0}c_{2}y_{2} \\
>>              &= (c_{1}y_{1}'' + a_{1}c_{1}y_{1}' + a_{0}c_{1}y_{1}) + (c_{2}y_{2}'' + a_{1}c_{2}y_{2}' + a_{0}c_{2}y_{2}) \\
>>              &= c_{1}(y_{1}'' + a_{1}y_{1}' + a_{0}y_{1}) + c_{2}(y_{2}'' + a_{1}y_{2}' + a_{0}y_{2}) \\
>>              &= c_{1}L(y_{1}) + c_{2}L(y_{2}) \tag*{$\square$}
>>\end{align}$$

^dec49d

>[!theorem] Theorem Superposition ([[../../../Sources/nagy.pdf#page=90 | Source]])
> If $L$ is a linear operator and $y_{1}, y_{2}$ are solutions of the homogeneous equations $L(y_{1})=0$ and $L(y_{2})=0$, then for every constant $c_1, c_2$ holds
> $$L(c_{1}y_{1}+ c_{2}y_{2})=0$$
>>[!note]
>> This theorem focuses on the non-IVP. Given variable $t_{0}$, we can state there are arbitrary $c_1, c_2$ holding the superposition theorem. We further note, that fixing $t_0$ will make the pair $c_1, c_2$ unique.
>
>>[!proof]-
>> For the function $y=c_{1}y_{1}+c_{2}y_{2}$ satisfies $L(y)=0$ using [[#^dec49d|linearity]] we have
>> $$\begin{align}
>> L(y) &= L(c_{1}y_{1} + c_{2}y_{2}) \\
>>      &= c_{1}L(y_{1}) + c_{2}L(y_{2}) \\
>>      &= c_{1}0  + c_{2}0 \\
>>      &= 0 \tag*{$\square$}
>>\end{align}$$

^88d6f3


>[!remark] Remarks on Proportionality and Linear Independence
>1. $y_1, y_2$ are proportional, then there exists some constant $k$ such that
>   $$y_{1}(t)=ky_{2}(t)$$
>2. $y_1 =0$ is proportional to any $y_2$, since $y_1=0=0y_2$ due to linearity
>3. $y_{1}$ and $y_2$ are linearly independent if there exist constants $c_1, c_2 \neq 0$ such that
> $$c_{1}y_{1}+c_{2}y_{2} = 0$$
>4. Fixing $c_1=1$ in linear independence, we have the proportionality statement from 1.
>5. If two functions are proportional, then their  slopes are also proportional. We have
> $$\frac{d}{dx}(k\cdot y(x)) = k \frac{d}{dx}y(x)$$
>
>>[!example]- Example Show that $y_1(t)=\sin(t)$ and $y_{2}(t)=2\sin(t)$ are linearly independent
>>Obviously 
>>$$\begin{align}
>> 2y_{1}(t)-y_{2}(t) &= 0  \\
>> 2\sin(t)-2\sin(t) &= 0
>>\end{align}$$
>>with $c_1 = 2$ and $c_2 = -1$.
>
>>[!example]- Example Show that $y_1(t)=\sin(t)$ and $y_{2}(t)=t\sin(t)$ are linearly independent
>> Since we have in $y_2$ a continuous function $a(t)=0$ we have to find some $t \in \mathbb{R}$ such that we can't find $c_1, c_2 \neq 0$ satisfying the linear independence conditions, since the chosen $c_1, c_2$ must hold the property for any $t \in \mathbb{R}$. We choose $t = \frac{\pi}{2}$ and $t = \frac{3\pi}{2}$ and have
>> $$\begin{align}
>> c_{1} + \frac{\pi}{2} c_{2} &= 0 \tag{$t=\frac{\pi}{2}$} \\
>> c_{1} + \frac{3\pi}{2} c_{2} &= 0 \tag{$t=\frac{3\pi}{2}$} 
>>\end{align}$$
>> Here the only solution to this system of equations is $c_{1}=c_{2}=0$. Hence, $y_{1}$ and $y_{2}$ are linearly independent.

^2aec50

>[!def] Definition Fundamental and General Solution ([[../../../Sources/nagy.pdf#page=91 | Source]])
>1. The function $y_1$ and $y_2$ are **fundamental solutions** of the equation $L(y)=0$ iff $y_1, y_{2}$ are linear linearly independent and $$L(y_{1})=0, \quad L(y_{2})= 0$$
>2. The **general solution** of the homogeneous equation $L(y)=0$ is a two-parameter family of functions $y_{\text{gen}}$ given by
>   $$y_{\text{gen}}(t) = c_{1}y_{1}(t)+c_{2}y_{2}(t)$$
>   where the arbitrary constants $c_{1}, c_{2}$ are the parameters of the family and $y_{1}, y_{2}$ are fundamental solutions of $L(y)=0$
>   
>>[!example]- Example Show that $y_{1}=e^t$ and $y_{2}=e^{-2t}$ are fundamental solutions to $y''+y'-2y=0$
>>First we show, that the given solutions are actually valid
>>$$\begin{align}
>> L(y_{1}) &= L(e^t) \\
>>       &= (e^t)'' + (e^t)' - 2e^t \\
>>       &= e^t + e^t - 2e^t  \\
>>       &= 0 \\
>> L(y_{2}) &= L(e^{-2t}) \\
>>       &=  (e^{-2t})'' + (e^{-2t})' - 2e^{-2t} \\
>>       &= 4e^{-2t} -2e^{-2t} - 2e^{-2t} \\
>>       &= 0 
>>\end{align}$$
>>We verified $y_{1}, y_{2}$ to be solutions. Now we verify it being a **general solution** to the ODE, i.e. $y_1, y_2$ being linearly independent with $t \in \mathbb{R}$. If the fundamental solutions are linear dependent, then their slopes are proportional. Therefore, we take the derivative of $y_1$ and $y_2$. 
>>$$\begin{alignat}{2}
>>y_{1}' &= e^t &&= y_{1} \\
>>y_{2}' &= -2e^{-2t} &&= -2y_{2}
>>\end{alignat}$$
>>We fix $t=0$ and have
>>$$\begin{align}
>> c_{1}y_{1} -2c_{2}y_{2} &= 0 \\
>> c_{1}e^0 -2 c_{2}e^0 &= 0  \\
>> c_{1} - 2c_{2} &=0
>>\end{align}$$
>>Obviously, there is no other configuration than $c_1 = c_2 = 0$, hence $y_1$ and $y_2$ are linear independent and therefore $y_1, y_2$ are a general solution to the ODE.
>
>>[!remark]- Remark Fundamental Solutions not Unique
>>Note, fundamental solutions are not unique. The preceding example also has solutions $y_1 = \frac{2}{3}e^t + \frac{1}{3}e^{-2t}$ and $y_2 = \frac{1}{3} (e^t - e^{-2t})$

>[!theorem] Theorem General Solution to Second Order ODEs ([[../../../Sources/nagy.pdf#page=91 | Source]])
>If $y_{1}$ and $y_{2}$ are linearly independent solutions of the equation $L(y)=0$ on an interval $I \subset \mathbb{R}$, where $L(y)=y'' + a_{1}y' + a_{0}y$, and $a_{1},a_{2}$ are continuous functions on $I$, then there are unique constants $c_{1},c_{2}$ such that every solution $y$ of the differential equation $L(y)=0$ on $I$ can be written as a linear combination
>$$y(t) = c_{1}y_{1}(t) + c_{2}y_{2}(t)$$
>>[!proof]-
>>>Goal:
>>>We have to show, that any solution pair $(y_1, y_2)$ are a unique linear combination of
>>>$$L(y_{\text{gen}}) = L(c_{1}y_{1}+c_{2}y_{2}) = 0$$
>>>with 
>>>$$\begin{align}
>>> y_{\text{gen}} = c_{1}y_{1}+c_{2}y_{2} \tag{1}
>>>\end{align}$$
>>
>> We will use the following properties
>>>1. by the [[#^88d6f3|superposition theorem]] we know that given fundamental solutions $y_{1}, y_{2}$ are solutions to any $c_1, c_2$, i.e. $$L(c_{1}y_{1}+c_{2}y_{2}) = c_{1}\underbrace{ L(y_{1}) }_{ =0 }+c_{2}\underbrace{ L(y_{2}) }_{ =0 } = 0$$
>>>2. a general solution $y_{{\text{gen}}}$ is a linear combination of arbitrary $y_1$ and $y_2$ where $c_1, c_2$ are unique with respect to $y_1, y_2$. This can easily be shown by assuming there exist two linear combinations $(c_{1}, c_{2})$ and $(\hat{c}_{1}, \hat{c}_{2})$, then we'd have
>>>  $$\begin{align}
>>> y(t) = c_{1}y_{1}+c_{2}y_{2}  \\
>>> y(t) = \hat{c}_{1}y_{1} + \hat{c}_{2}y_{2}
>>>\end{align}$$
>>>Setting these equal and subtracting them yields
>>>$$(c_{1}-\hat{c}_{1})y_{1} +  (c_{2}-\hat{c}_{2})y_{2} = 0$$
>>>Hence, the only configuration solving the condition for linear independence of $y_1, y_2$ is
>>>$$\begin{align}
>>> c_{1}-\hat{c}_{1} &= 0 \\
>>> c_{2}-\hat{c}_{2} &= 0
>>>\end{align}$$
>>
>> Recall the [[#^786ff5|theorem of solutions for second order ODEs with IVP]] says for homogeneous second order equations there is a unique solutions given we have initial values $y(t_{0})=d_{1}$ and $y'(t_{0})= d_{2}$. Hence, the given parametrization of $y$ with parameters $d_1, d_2$ can identify a solution uniquely.
>> 
>> Now we approach the given problem similarly by treating $d_1, d_2$ as fundamental solutions parametrized by $c_1$ and $c_2$
>>$$\begin{align}
>> y(t_{0}) = d_{1} &= c_{1}y_{1}(t_{0}) + c_{2}y_{2}(t_{0}) \\
>> y'(t_{0}) = d_{2} &= c_{1}y'_{1}(t_{0}) + c_{2}y'_{2}(t_{0}) \\
>>\end{align}$$
>>Now we want to show, that this mapping is invertible under certain conditions, such that we can obtain the solution $(c_{1},c_{2})$ over given $y_1, y_2, y'_1, y'_2, d_1, d_2, t_0$. Since this is a system of linear equations, we can use the properties of [[../Linear Algebra/Determinants|Determinants]], where there is no solution if $\det(A) = 0$. Hence, we know that the mapping is invertible iff
>>$$\begin{align}
>>\begin{vmatrix}
>> y_{1}(t_{0}) &y_{2}(t_{0})\\ y_{1}'(t_{0}) &y_{2}'(t_{0})
>>\end{vmatrix} &= y_{1}(t_{0})y_{2}'(t_{0}) - y_{1}'(t_{0})y_{2}(t_{0}) \neq 0
>>\end{align}$$
>>This can be represented by the Wronskian function of $y_1, y_2$, i.e.
>>$$W_{12}(t)= y_{1}(t)y_{2}'(t)-y_{1}'(t)y_{2}(t)$$
>>The Wronskian function has the property, if $y_1, y_2$ are fundamental solutions of $L(y)=0$ on $I \subset \mathbb{R}$, then $W_{12}(t)\neq 0$ on $I$, which proves the theorem.
>> $$\begin{align}
>> \, \tag*{$\square$}
>>\end{align}$$
>>>[!note]
>>>The Wronskian function and its properties will be discussed following

>[!def] Definition The Wronskian Function ([[../../../Sources/nagy.pdf#page=93 | Source]])
> The **Wronskian** of the differentiable functions $y_{1}, y_{2}$ is the function
> $$W_{12}(t)=y_{1}(t)y_{2}'(t)-y_{1}'y_{2}(t)$$
> 
>>[!proposition] Notation
>>We use 
>>$$A(t) = \begin{bmatrix}
>>y_{1}(t) & y_{2}(t) \\
>>y_{1}'(t) & y_{2}'(t)
>>\end{bmatrix}$$
>>for the system of equations, hence the Wronskian can be written as
>>$$W_{12}=\det A(t) = \begin{vmatrix}
>>y_{1} & y_{2} \\
>>y_{1}' & y_{2}'
>>\end{vmatrix}$$
>
>>[!example]- Find the Wronskian of $y_{1}(t)=\sin(t)$ and $y_{2}(t)=2\sin(t)$
>>$$\begin{align}
>> W_{12} &= \begin{vmatrix}
>> \sin(t) &2\sin(t) \\
>> \cos(t) & 2\cos(t) 
>>\end{vmatrix} \\
>> &= \sin(t)2\cos(t)- 2\sin(t)\cos(t) \\
>> &= 0
>>\end{align}$$
>
>>[!example]- Find the Wronskian of $y_{1}(t)=\sin(t)$ and $y_{2}(t)=t\sin(t)$
>>$$\begin{align}
>> W_{12} &= \begin{vmatrix}
>> \sin(t) & t\sin(t) \\
>> \cos(t) & t\cos(t) + \sin (t)
>>\end{vmatrix} \\
>> &= \sin(t)(t\cos(t)+ \sin(t)) - \cos(t)t\sin(t) \\
>> &= \sin^2(t) + t\sin(t)\cos(t)-t\sin(t)\cos(t) \\
>> &= \sin^2(t)
>>\end{align}$$
>>

>[!theorem] Theorem Wronskian (I)
>If $y_{1}, y_{2}$ are linearly dependent on $I \subset \mathbb{R}$ then
>$$W_{12}=0 \;\; \text{ on }\;\; I$$
>>[!proof]-
>>Since $y_{1}, y_{2}$ are linearly independent, there exists some constant $c$ such that $$y_{1} = cy_{2}$$
>>Therefore we have for the Wronskian
>>$$\begin{align}
>> W_{12} &= y_{1}y_{2}'-y_{2}y_{1}' \\
>> &= cy_{2}y_{2}' - y_{2}(cy_{2})' \tag{Linear Independence}  \\
>> &=cy_{2}y_{2}' - cy_{2}y_{2}' \\
>> &= 0
>>\end{align}$$
>>$$\begin{align}
>>\, \tag*{$\square$}
>>\end{align}$$
>
>>[!remark]-
>>The converse is not necessarily true, we can not conclude from $W_{12}=0$ that $y_{1},y_{2}$ are linearly dependent.
>
>>[!example]- Show that the functions $y_{1}(t)=t^2$ and $y_{2}(t) = \lvert t \rvert t$ for $t \in \mathbb{R}$ are linearly independent and have Wronskian $W_{12}=0$
>>Note that
>>$$\begin{align}
>> y_{2}(t)=\begin{cases}
>> t^2&t\geq0 \\
>>  -t^2  &t<0
>>\end{cases}
>>\end{align}$$
>>Hence, we have
>>$$\begin{align}
>> c_{1}y_{1}+c_{2}y_{2} =\begin{cases}
>> c_{1}t^2 +c_{2}t^2 =0 & t \geq 0 \\
>> c_{1}t^2 -c_{2}t^2 =0 & t<0
>>\end{cases}
>>\end{align}$$ 
>>We can clearly tell, that only $c_1 = c_2 =0$ solves the above equation, hence, $y_{1}$ and $y_{2}$ are linearly independent. We now calculate the Wronskian
>>$$\begin{align}
>> W_{12} = \begin{cases}
>> \begin{vmatrix}
>>t^2 & t^2 \\
>>2t & 2t
>>\end{vmatrix} &=2t^3 - 2t^3 &=0 &&t\geq 0  \\ 
>>\begin{vmatrix}
>>t^2 & -t^2 \\
>>2t & -2t
>>\end{vmatrix} &= -2t³+2t^3 &=0  && t <0
>>\end{cases}
>>\end{align}$$
>>Hence, $W_{12} = 0$

>[!corollary] Corollary Inverse Wronskian (I) Theorem
> If the Wronskian $W_{12}(t_{0}) \neq 0$ at a point $t_{0}\in I$, then the functions $y_{1}, y_{2}$ are linearly independent.

>[!Theorem] Abel's Theorem
>If $y_{1},y_{2}$ are twice continuously differentiable solutions of $$y''+a_{1}(t)y'+a_{0}(t)y=0$$
>where $a_{0}, a_{1}$ are continuous on $I \subset \mathbb{R}$, then the Wronskian $W_{12}$ satisfies
>$$W_{12}'+a_{1}(t)W_{12} = 0$$
>Therefore, for any $t_{0} \in I$, the Wronskian $W_{12}$ is given by the expression
>$$W_{12}(t)=W_{12}(t_{0})e^{-A_{1}(t)}$$
>with $$A_{1}(t)=\int _{t_{0}}^t a_{1}(s) \, ds $$
>>[!proof]-
>> The derivative of the Wronskian is computed as
>> $$\begin{align}
>> W_{12}'&=(y_{1}y_{2}'-y_{1}'y_{2})' \\
>>     &=(y_{1}y_{2}')'-(y_{1}'-y_{2})' \\
>>     &=y_{1}'y_{2}'+y_{1}y_{2}'' - (y_{1}''y_{2} + y_{1}'y_{2}') \\
>>     &= y_{1}y_{2}'' - y_{1}''y_{2} \tag{1}
>>\end{align}$$
>>Recall by the theorem's condition we have
>>$$\begin{align}
>> 0&=y''+a_{1}(t)y'+a_{0}(t)y \\
>> y''&=-a_{1}(t)y'-a_{0}(t)y \\
>>\end{align}$$
>>Inserting this result into $(1)$ gives
>>$$\begin{align}
>>W_{12}'&=y_{1}(-a_{1}y_{2}'-a_{0}y_{2}) - (-a_{1}y_{1}'-a_{0}y_{1})y_{2}  \\
>>    &=-a_{1}y_{1}y_{2}'\cancel{ -a_{0}y_{1}y_{2} } + a_{1}y_{1}'y_{2} + \cancel{ a_{0}y_{1}y_{2} } \\
>>    &=-a_{1}\underbrace{ (y_{1}y_{2}'-y_{1}'y_{2}) }_{ =W_{12} } \\
>>    &= -a_{1}W_{12}
>>\end{align}$$
>>Hence we have
>>$$W_{12}' + a_{1}W_{12} = 0$$
>>which is a [[1 - First Order ODEs| first order ODE]] which can be solved with [[1 - First Order ODEs#^thmsolIVPvar| using the integrating factor method]], where the integrating factor $e^{-A(t)}$ can be given as
>>$$\begin{align}
>> A(t)=\int _{t_{0}}^t A(s)\, ds \tag*{$\square$}
>>\end{align}$$
>
>>[!example]- Find the Wronskian of two solutions of the equation $t^2y''-t(t+2)y' + (t+2)y = 0$ with $t>0$
>>>[!note]
>>> We do not know the fundamental solutions $y_{1},y_{2}$
>>
>>We rewrite the homogeneous differential equation to bring it in the base form for Abel's theorem
>>$$\begin{alignat}{2}
>> t^2y''-t(t+2)y' + (t+2)y &= 0 \qquad&&\Big\vert :t^2 \\
>> y'' - \frac{t+2}{t}y' + \frac{t+2}{t^2}y  &= 0 \\
>>  y''  \underbrace{- \left( 1 + \frac{2}{t} \right) }_{ =a_{1} }y'+\underbrace{ \left( \frac{1}{t}+\frac{2}{t^2} \right) }_{ =a_{0} }y &=0
>>\end{alignat}$$
>>By Abel's theorem we have the following relation
>>$$\begin{align}
>> W_{12}'+a_{1}(t)W_{12} &= 0 \\
>> W_{12}'-\left( 1 + \frac{2}{t} \right)W_{12} &= 0 \\
>>\end{align}$$
>>This is a [[1 - First Order ODEs|first order ODE]] and can be solved using [[1 - First Order ODEs#^thmsolIVPvar| using the integrating factor method]] with
>>$$\begin{align}
>> A(s) &= \int_{t_{0}}^t a(s) \, ds  \\
>>      &= -\int_{t_{0}}^t 1 + \frac{2}{s}  \, ds  \\
>>      &= -\left[s + 2\ln s\right]_{t_{0}}^t  \\
>>      &= -\Big((t +2\ln t)-(t_{0}+2\ln t_{0})\Big)  \\
>>      &= -\Big(2\ln \frac{t}{t_{0}} +t-t_{0}\Big)  \\
>>      &= -2\ln \frac{t}{t_{0}} -(t-t_{0})  \\
>>      &= \ln \frac{t_{0}^2}{t^2} -(t-t_{0})  \\
>>\end{align}$$
>>The integrating factor can therefore be given as
>>$$\begin{align}
>>e^{-A(s)} &= e^{-(\ln \frac{t_{0}^2}{t^2} -(t-t_{0}))}  \\
>>       &= e^{\ln \frac{t^2}{t_{0}^2} +(t-t_{0})} \\
>>       &= e^{\ln \frac{t^2}{t_{0}^2}} e^{(t-t_{0})} \\
>>       &= \frac{t^2}{t_{0}^2} e^{(t-t_{0})} \\
>>\end{align}$$
>>The Wronskian can be given as
>>$$\begin{align}
>> W_{12}(t)&=W_{12}(t_{0})e^{-A_{1}(t)} \\
>>       &= W_{12}(t_{0})\frac{t^2}{t_{0}^2} e^{(t-t_{0})} \\ 
>>       &= W_{12}(t_{0})\frac{t^2}{t_{0}^2} \frac{e^t}{e^{t_{0}}}  \\
>>       &= \underbrace{ \frac{W_{12}(t_{0})}{t_{0}^2e^{t_{0}}} }_{ =c }t^2e^t\\
>>       &= ct^2e^t
>>\end{align}$$

^78710b

>[!theorem] Theorem Wronskian (II)
>If $y_{1},y_{2}$ are fundamental solutions of $L(y)=0$ on $I \subset \mathbb{R}$, then $W_{12}(t) \neq 0$ on $I$.
>>[!proof] Proof is given by the inverse Corollary

>[!Corollary] Corollary Inverse Wronskian (II) Theorem 
>If $y_{1},y_{2}$ are solutions of $L(y)=0$ on $I \subset \mathbb{R}$ and there is a point $t_{1} \in I$ such that $W_{12}(t_{1})=0$, then $y_{1},y_{2}$ are linearly dependent on $I$.
>>[!proof]-
>>By the theorem's condition we know that $y_{1},y_{2}$ are solutions of $L(y)=0$ on $I \subset \mathbb{R}$. By [[#^78710b|Abel's theorem]] we know
>>$$W_{12}(t)=W_{12}(t_{0})e^{-A_{1}(t)}$$
>>for any $t_{0} \in I$. We choose $t_0$ to be $t_1$ and have by the corollary
>>$$W_{12}(t_{1})= 0$$
>>since the claim is valid for any $t_{0} \in I$ we can generalize the statement as
>>$$W_{12}(t) = 0 \quad \forall t\in I$$
>>The Wronskian vanishes identically on $I$, i.e.
>>$$y_{1}y_{2}' - y_{1}'y_{2} = 0$$
>>1. Case: $y_{1}$ or $y_{2}$ are  the zero function => $y_{1}$ and $y_{2}$ are linearly dependent :luc_check:
>>2. Case: we choose $y_1$ to be non-zero on the open neighborhood $I_{1} \subset I$ of $t_1$, such that we can write
>>$$\begin{alignat}{2}
>>y_{1}y_{2}'-y_{1}'y_{2} &= 0 \qquad&&\Big\vert :y_{1}^2 \\
>>\frac{y_{1}y_{2}'-y_{1}'y_{2}}{y_{1}^2} &= 0 \tag{Division Rule}\\
>> \left( \frac{y_{2}}{y_{1}} \right)' &= 0 \qquad&&\Big\vert \int  \, dt   \\
>> \frac{y_{2}}{y_{1}}  &= c \qquad&&\Big\vert \int  \, dt   \\
>>\end{alignat}$$
>>Hence $y_{1},y_{2}$ are proportional on the open set $I_{1}$ and by the [[#^2aec50| remark on proportionality]] we know they are linearly dependent. Hence, we have $y_{\text{gen}}=y_{2}-cy_{1}$. By the corollary, [[#^786ff5| the solution theorem]] and the [[#^dec49d| linearity]], we have
>>$$L(y) = 0 \;\;\text{ with } \;\; y(t_{1})=0, \;\; y'(t_{1})=0$$
>>therefore, $y(t)=0$ over all $t \in I$, hence $y_{1}$ and $y_{2}$ are linearly dependent.
>>$$\begin{align}
>> \, \tag*{$\square$}
>>\end{align}$$

>[!example] Exercises
>>[!example] Task
>>Find the constants $c$ and $k$ such that the function $y(t)=ct^k$ is solution of
>>$$-t^3y+t^2y+4ty=1$$
>
>>[!example] Task
>>Let $$y(t)=c_{1}t+c_{2}t^2$$
>>be the general solution of a second order linear differential equation $L(y)=0$. By eliminating the constants $c_{1}$ and $c_{2}$, find the differential equation satisfied by $y$.
>
>>[!example] Task
>>1. Verify that $y_{1}(t)=t^2$ and $y_{2}(t)=\frac{1}{t}$ are solutions of the differential equation
>> $$t²y''-2y=0$$
>> with $t>0$
>>2. Show that $y(t)=at^2+\frac{b}{t}$  is solution of the same equation for all constants $a,b \in \mathbb{R}$
>
>>[!example] Task
>>Find the longest interval where the solution $y$ of the IVP below is defined, not solving
>>1. $t^2 y'' + 6y = 2t$ with $y(1)=2$ and $y'(1)=3$
>>2. $(t-6)y'+3ty'-y=1$ with $y(3)=-1$ and $y'(3)=2$
>
>>[!example] Task
>> If the graph of $y$, solution to a second order linear differential equation $L(y(t))=0$ on the interval $[a,b]$ is tangent to the $t$-axis at any point $t_{0}\in[a,b]$, then find the solution $y$ explicitly.
>
>>[!example] Task
>>Can the function $y(t)=\sin(t^2)$ be solution on an open interval containing $t=0$ of a differential equation $$y''+a(t)y'+b(t)y=0$$
>>with continuous coefficients $a$ and $b$? Explain your answer
>
>>[!example] Task
>>Compute the Wronskian of the following functions
>>1. $f(t)=\sin(t)$ and $g(t)=\cos(t)$
>>2. $f(x)=x$ and $g(x)=xe^x$
>>3. $f(\theta)=\cos²(\theta)$ and $g(\theta)=1+\cos(2\theta)$
>
>>[!example] Task
>>Verify whether the functions $y_{1}, y_{2}$ below are a fundamental set for the differential equations given below
>>1. $y_{1}(t)=\cos(2t)$ and $y_{2}(t)=\sin(2t)$ for
>>	$$y''+4y=0$$
>>2.$y_{1}(t)=e^t$ and $y_{2}(t)=te^t$ for $$y''-2y'+y=0$$
>>3.$y_{1}(x)=x$ and $y_{2}(t)=xe^x$ for $$x^2y''-2x(x+2)y'+(x+2)y=0$$
>
>>[!example] Task
>>If the Wronskian of any two solutions of the differential equation 
>>$$y'' + p(t)y'+q(t)y=0$$
>>is constant, what does this imply about the coefficients $p$ and $q$?
>
>>[!example] Task*
>>Suppose $y_{1}$ is solution of the IVP
>>$$y_{1}''+a_{1}y_{1}'+a_{0}y_{1}=0$$
>>with
>>$$y_{1}(0)=0 \;\; \text{ and }\;\; y_{1}'(0)=5$$
>>and $y_{2}$ is solution of the IVP
>>$$y_{2}''+a_{1}y_{2}'+a_{0}y_{2}=0$$
>>with
>>$$y_{1}(0)=0 \;\; \text{ and }\;\; y_{1}'(0)=1$$
>>that is, same differential equation and same initial condition for the function, but different intial conditions for the derivatives. Then show that the functions $y_{1}$ and $y_{2}$ mus be proportional to each other, i.e.
>>$$y_{1}(t)=cy_{2}(t)$$
>>and find the proportionality factor $c$.
>>>[!note]- Hint 1
>>>[[#^786ff5 | The second order solution theorem]] states
>>>$$y'' + a_{1}y' + a_{0}y = 0$$
>>>with $y(0)=0$ and $y'(0)=0$ has a unique solution. The solution is $y(t)=0$ for all $t$.
>>
>>>[!note]- Hint 2
>>>Find what is the IVP problem for the function $$y_{c}(t) = y_{1}(t)-cy_{2}(t)$$ and fine tune $c$ to use hint 1

## 2.2 Reduction Order Methods
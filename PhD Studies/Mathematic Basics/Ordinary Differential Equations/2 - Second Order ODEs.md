## 2.1 Variable Coefficients

>[!def] Definition Second Order Linear Differential Equations ([[../../../PDFs/nagy.pdf#page=86| Source]])
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


>[!theorem] Theorem Solutions to IVP of Second Order ODEs ([[../../../PDFs/nagy.pdf#page=88| Source]])
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

>[!def] Definition Linear Operator ([[../../../PDFs/nagy.pdf#page=89| Source]])
>An operator $L$ is a **linear operator** iff for every pair of functions $y_{1},y_{2}$ and constants $c_{1}, c_{2}$ holds
>$$L(c_{1}y_{1}+ c_{2}y_{2}) = c_{1}L(y_{1})+ c_{2}L(y_{2})$$


>[!theorem] Theorem Linear Differential Operator ([[../../../PDFs/nagy.pdf#page=89| Source]])
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

>[!theorem] Theorem Superposition ([[../../../PDFs/nagy.pdf#page=90| Source]])
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

>[!def] Definition Fundamental and General Solution ([[../../../PDFs/nagy.pdf#page=91| Source]])
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

>[!theorem] Theorem General Solution to Second Order ODEs ([[../../../PDFs/nagy.pdf#page=91| Source]])
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

>[!def] Definition The Wronskian Function ([[../../../PDFs/nagy.pdf#page=93| Source]])
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

^42635c

>[!theorem] Theorem Wronskian (I) ([[../../../PDFs/nagy.pdf#page=93| Source]])
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

>[!corollary] Corollary Inverse Wronskian (I) Theorem ([[../../../PDFs/nagy.pdf#page=94| Source]])
> If the Wronskian $W_{12}(t_{0}) \neq 0$ at a point $t_{0}\in I$, then the functions $y_{1}, y_{2}$ are linearly independent.

>[!Theorem] Abel's Theorem ([[../../../PDFs/nagy.pdf#page=94| Source]])
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

>[!theorem] Theorem Wronskian (II) ([[../../../PDFs/nagy.pdf#page=95| Source]])
>If $y_{1},y_{2}$ are fundamental solutions of $L(y)=0$ on $I \subset \mathbb{R}$, then $W_{12}(t) \neq 0$ on $I$.
>>[!proof] Proof is given by the inverse Corollary

^5577c0

>[!Corollary] Corollary Inverse Wronskian (II) Theorem ([[../../../PDFs/nagy.pdf#page=95| Source]])
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

>[!example]- Exercises
>>[!example] Task
>>Let $$y(t)=c_{1}t+c_{2}t^2$$
>>be the general solution of a second order linear differential equation $L(y)=0$. By eliminating the constants $c_{1}$ and $c_{2}$, find the differential equation satisfied by $y$.
>>>[!example]- Solution
>>> First taking the derivative with respect to $t$ and finding an expression for $c_{1}$
>>> $$\begin{align}
>>> y' &= c_{1} + 2c_{2}t \\
>>> c_{1}&= 2c_{2}t - y'
>>>\end{align}$$
>>> Inserting this into the original equation gives
>>> $$\begin{align}
>>> y &= (y'-2c_{2}t)t+c_{2}t^2  \\
>>> y &= y't - c_{2}t^2 \\
>>> c_{2}t^2 &= y't - y \\
>>> c_{2} &= \frac{1}{t}y'-\frac{1}{t^2}y 
>>>\end{align}$$
>>>Taking now the derivative with respect to $t$ gives
>>>$$\begin{align}
>>> 0 = -\frac{1}{t^2}y' + \frac{1}{t}y'' - \left( -\frac{1}{t^3}y + \frac{1}{t^2}y' \right) \\
>>> 0 = \frac{1}{t^3}y -\frac{2}{t^2}y'+\frac{1}{t}y'' \qquad&&\Big\vert \cdot t^3 \\ 
>>> 0 = y -2ty'+t^2y''  
>>>\end{align}$$
>>>which is the second order differential equation
>
>>[!example] Task
>>1. Verify that $y_{1}(t)=t^2$ and $y_{2}(t)=\frac{1}{t}$ are solutions of the differential equation
>> $$t²y''-2y=0$$
>> with $t>0$
>>2. Show that $y(t)=at^2+\frac{b}{t}$  is solution of the same equation for all constants $a,b \in \mathbb{R}$
>>
>>>[!example]- Solution
>>> 1. $\,$ 
>>> Since the differential equation is of the form
>>> $$L(y) = 0$$
>>> we can apply the [[#^88d6f3 | superposition theorem]] and have 
>>> $$y_{\text{gen}} = t^2 + \frac{1}{t}$$
>>> Computing the derivatives of $y_{\text{gen}}$ yields
>>> $$\begin{align}
>>> y' &= 2t -\frac{1}{t^2} \\
>>> y'' &= 2 + \frac{2}{t^3}
>>>\end{align}$$
>>>Inserting these into the differential equation gives
>>>$$\begin{align}
>>> t²y''-2y&=0  \\
>>> t^2\left( 2 + \frac{2}{t^3} \right)-2\left( t^2 + \frac{1}{t} \right) &=0 \\
>>> 2t^2+\frac{2}{t} - 2t^2 -\frac{2}{t} &= 0 \\
>>> 0&=0
>>>\end{align}$$
>>>which confirms the solutions.
>>>2. $\,$
>>>Having $y(t)=at^2+\frac{b}{t}$ we take the first two derivatives with respect to $t$
>>>$$\begin{align}
>>> y' &= 2at - \frac{b}{t^2}  \\
>>> y'' &=2a + \frac{b}{t^3} 
>>>\end{align}$$
>>>Inserting these into the solution we get
>>>$$\begin{align}
>>> t^2\left( 2a+2 \frac{b}{t^3} \right) - 2 \left( at^2+\frac{b}{t} \right) &= 0 \\
>>> 2at^2 + \frac{2b}{t} - 2at^2 - \frac{2b}{t} &=0
>>>\end{align}$$
>>>which confirms the solution.
>
>>[!example] Task
>>Find the longest interval where the solution $y$ of the IVP below is defined, not solving
>>1. $t^2 y'' + 6y = 2t$ with $y(1)=2$ and $y'(1)=3$
>>2. $(t-6)y''+3ty'-y=1$ with $y(3)=-1$ and $y'(3)=2$
>>
>>>[!example]- Solution
>>> 1. $\,$
>>> First we rearrange for the form of [[#^786ff5 | the solution theorem for second order ODEs]]
>>> $$\begin{alignat}{2}
>>> t^2 y'' +6y &= 2t \qquad&&\Big\vert :t^2 \\
>>> y'' + \frac{6}{t^2}y &= \frac{2}{t}
>>>\end{alignat}$$
>>>We can conclude $t\neq 0 \Rightarrow t \in[-\infty, 0) \cup (0,\infty]$. Since $t_0 = 1$, we choose
>>>$$D = (0, \infty]$$
>>>2. $\,$
>>>First we rearrange for the form of [[#^786ff5 | the solution theorem for second order ODEs]]
>>> $$\begin{alignat}{2}
>>> (t-6) y'' +3ty' -y &= 1 \qquad&&\Big\vert :(t-6) \\
>>> y'' + \frac{3}{t-6}y' - \frac{1}{t-6}y &= \frac{1}{t-6}
>>>\end{alignat}$$
>>>We can conclude $t\neq 6 \Rightarrow t \in[-\infty, 6) \cup (6,\infty]$. Since $t_0 = 3$, we choose
>>>$$D = [-\infty, 6)$$
>
>>[!example] Task
>>Can the function $y(t)=\sin(t^2)$ be solution on an open interval containing $t=0$ of a differential equation $$y''+a(t)y'+b(t)y=0$$
>>with continuous coefficients $a$ and $b$? Explain your answer
>>>[!example]- Solution
>>>Looking at the derivatives
>>>$$\begin{align}
>>> y' &= 2t \cos(t^2) \\
>> y'' &= -4t^2\sin(t^2)
>>>\end{align}$$
>>>we can see that $y''$ is continuous on the open interval containing $t=0$. For $y'$ we must further consider the behavior of $a(t)$. Since we require $a(t)$ to be also continuous on the same interval containing $t=0$, we can't find a function $a(t)$ such that the combination of $a(t)y'$ would become discontinuous on such interval. The solution $y(t)=\sin(t^2)$ is continuous on  the real numbers, we can conclude that the function can be a solution.
>
>>[!example] Task
>>Compute the Wronskian of the following functions
>>1. $f(t)=\sin(t)$ and $g(t)=\cos(t)$
>>2. $f(x)=x$ and $g(x)=xe^x$
>>3. $f(\theta)=\cos²(\theta)$ and $g(\theta)=1+\cos(2\theta)$
>>
>>>[!example]- Solution
>>>1. $f(t)=\sin(t)$ and $g(t)=\cos(t)$ 
>>>$$\begin{align}
>>> W_{12} &= \begin{vmatrix}
>>>\sin(t) &\cos(t) \\
>>> \cos(t) &-\sin(t)
>>>\end{vmatrix}  \\
>>> &= -\sin^2 (t)-\cos^2(t)
>>>\end{align}$$
>>>2.  $f(x)=x$ and $g(x)=xe^x$
>>>$$\begin{align}
>>> W_{12} &= \begin{vmatrix}
>>> x &xe^x \\
>>> 1 &e^x+xe^x
>>>\end{vmatrix}   \\
>>> &=x (e^x+xe^x)-xe^x \\
>>> &=x^2e^x
>>>\end{align}$$
>>>3. $f(\theta)=\cos²(\theta)$ and $g(\theta)=1+\cos(2\theta)$
>>>$$\begin{align}
>>> W_{12} &= \begin{vmatrix}
>>> \cos^2(\theta) &1+\cos(2\theta) \\
>>> -2\sin(\theta)\cos(\theta) &-2\sin(\theta)
>>>\end{vmatrix}  \\
>>> &= -2\cos^2(\theta)\sin(\theta)+2\sin(\theta)\cos(\theta)+2\sin(\theta)\cos(\theta)\cos(2\theta) \\
>>> &= 2\cos(\theta)\sin(\theta)\Big(-\cos(\theta)+1+\cos(2\theta)\Big)
>>>\end{align}$$
>
>>[!example] Task
>>Verify whether the functions $y_{1}, y_{2}$ below are a fundamental set for the differential equations given below
>>1. $y_{1}(t)=\cos(2t)$ and $y_{2}(t)=\sin(2t)$ for
>>	$$y''+4y=0$$
>>2. $y_{1}(t)=e^t$ and $y_{2}(t)=te^t$ for $$y''-2y'+y=0$$
>>3. $y_{1}(x)=x$ and $y_{2}(t)=xe^x$ for $$x^2y''-2x(x+2)y'+(x+2)y=0$$
>>
>>>[!example]- Solution
>>>1. By the [[#^88d6f3| superposition theorem]] we can give a general solution as
>>>$$y=c_{1}y_{1}+c_{2}y_{2}$$
>>>We now compute until the second derivative
>>>$$\begin{align}
>>> y &= c_{1}\cos(2t)+c_{2}\sin(2t) \\
>>> y' &= -2c_{1}\sin(2t) + 2c_{2}\cos(2t) \\
>>> y'' &= -4c_{1}\cos(2t)-4c_{2}\sin(2t)
>>>\end{align}$$
>>>Inserting into the given ODE yields
>>>$$\begin{align}
>>> y'' + 4y &= 0 \\
>>> -4c_{1}\cos(2t)-4c_{2}\sin(2t) + 4(c_{1}\cos(2t)+c_{2}\sin(2t)) &= 0 \\
>>> 0 &=0
>>>\end{align}$$
>>>Hence, the given solutions can be verified.
>>>2. By the [[#^88d6f3| superposition theorem]] we can give a general solution as
>>>$$y=c_{1}y_{1}+c_{2}y_{2}$$
>>>We now compute until the second derivative
>>>$$\begin{align}
>>> y &= c_{1}e^t+c_{2}te^t \\
>>> y' &= c_{1}e^t + c_{2}te^t + c_{2}e^t \\
>>> y'' &= c_{1}e^t + c_{2}te^t + 2c_{2}e^t
>>>\end{align}$$
>>>Inserting into the given ODE yields
>>>$$\begin{align}
>>> 0 &= y'' -2y' + y \\
>>> 0 &= c_{1}e^t + c_{2}te^t + 2c_{2}e^t -2(c_{1}e^t + c_{2}te^t + c_{2}e^t) + c_{1}e^t+c_{2}te^t \\
>>> 0 &= 0
>>>\end{align}$$ 
>>>Hence, the given solutions can be verified.
>>>3. By the [[#^88d6f3| superposition theorem]] we can give a general solution as
>>>$$y=c_{1}y_{1}+c_{2}y_{2}$$
>>>We now compute until the second derivative
>>>$$\begin{align}
>>> y &= c_{1}x+c_{2}xe^x \\
>>> y' &= c_{1} + c_{2}xe^x + c_{2}e^x\\
>>> y'' &= c_{2}xe^x+2c_{2}e^x
>>>\end{align}$$
>>>Inserting into the given ODE yields
>>>$$\begin{align}
>>> 0 &= x^2y''-2x(x+2)y'+(x+2)y  \\
>>> 0 &= x^2 \big(c_{2}xe^x+2c_{2}e^x\big)-(2x^2+4x)\big(c_{1} + c_{2}xe^x + c_{2}e^x\big)+(x+2)\big(c_{1}x+c_{2}xe^x \big) \\
>>> 0 &= c_{2}x^3e^x+2c_{2}x^2e^x -\big(2c_{1}x^2 + 2c_{2}x^3e^x+2c_{2}x^2e^x+4c_{1}x+4c_{2}x^2e^x+4c_{2}xe^x\big) \\
>>>   &+\big(c_{1}x^2+c_{2}x^2e^x+2c_{1}x+2c_{2}xe^x\big) \\
>>> 0 &= -c_{2}x^3e^x - 3c_{2}x^2e^x -2c_{2}xe^x-2c_{1}x-c_{1}x^2 \\
>>>\end{align}$$
>>>Hence, the given solutions are not solutions to the ODE.
>
>>[!example] Task
>>If the Wronskian of any two solutions of the differential equation 
>>$$y'' + p(t)y'+q(t)y=0$$
>>is constant, what does this imply about the coefficients $p$ and $q$?
>>>[!example]- Solution
>>>By [[#^78710b|Abel's theorem]] we know that the Wronskian for two twice differentiable solutions can be expressed as
>>>$$\begin{align}
>>> W_{12}(t) &= W_{12}(t_{0})e^{-A_{1}(t)}
>>>\end{align}$$
>>>for some $t_{0} \in I$ where the parameters $p, q$ are continuous on $I$ for the given ODE. Let's denote $$W_{12}(t_{0}) = c$$ since it will be a constant after computing the Wronskian for $t_{0}$, we have
>>>$$W_{12}(t) = ce^{-A_{1}(t)}$$
>>>with $$A_{1}(t)= \int_{t_{0}}^t p(s) \, ds $$
>>>For the claim of the Wronskian being constant, we have to only deal with the variable parameter $A_{1}(t)$. To have this parameter constant, it must satisfy $$p \equiv 0$$
>>>The parameter $q(t)$ does not play a role for the given condition.
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
>>that is, same differential equation and same initial condition for the function, but different initial conditions for the derivatives. Then show that the functions $y_{1}$ and $y_{2}$ must be proportional to each other, i.e.
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

>[!def] Definition Second Order Equation ([[../../../PDFs/nagy.pdf#page=98| Source]])
> A **second order** equation in the unknown function $y$ is an equation
> $$y'' = f(t,y,y')$$
> where the function $f:\mathbb{R}^3 \to \mathbb{R}$ is given. The equation is **linear** iff the function $f$ is linear in both arguments $y$ and $y'$. 

>[!def] Definition Special Second Order Equation ([[../../../PDFs/nagy.pdf#page=98| Source]])
>A second order differential equation is **special** iff one of the following condition holds
>1. $y'' = f(t,\cancel{ y },y')$, where $y$ does not appear explicitly
>2. $y'' = f(\cancel{ t },y,y')$, where $t$ does not appear explicitly
>3. $y'' = f(\cancel{ t },y,\cancel{ y' })$, where $t$ and $y'$ do not appear explicitly

>[!theorem] Theorem Function $y$ is Missing (Case 1) ([[../../../PDFs/nagy.pdf#page=98| Source]])
>If a second order differential equation has the form
>$$y''=f(t,y')$$
>then $v=y'$ satisfies the first order equation $v'=f(t,v)$
>>[!example]- Example Find the $y$ solution of the second order nonlinear equation $y''=-2t(y')^2$ with initial conditions $y(0)=2$ and $y'(0)=-1$
>>We introduce
>>$$v=y' \text{ and } v' = y''$$
>>therefore we have
>>$$v'=-2tv^2$$
>>We separate variables according to the [[1 - First Order ODEs#^defSeparableDifferentialEquation|solution theorem for separable equations]]
>>$$\begin{alignat}{2}
>> v'&=-2tv^2 \qquad&&\Big\vert :v^2 \\
>> \frac{1}{v^2}v' &= -2t \qquad&&\Big\vert \int    \\
>> -\frac{1}{v} &= -t^2+c \\
>>\end{alignat}$$
>>Resubstitung $v=y'$ gives
>>$$\begin{align}
>> -\frac{1}{y'} = -t^2+c \tag{1}
>>\end{align}$$
>>Solving for $c$ with the initial condition $y'(0)=-1$
>>$$\begin{align}
>>1 &= 0^2+c \\
>>1 &= c
>>\end{align}$$
>>Hence we have for equation $(1)$
>>$$\begin{align}
>> -\frac{1}{y'} &= -t^2+1 \\ 
>> \frac{1}{y'} &= t^2-1 \\
>> y' &= \frac{1}{t^2-1} \\
>>\end{align}$$ 
>>Integrating gives
>>$$\begin{align}
>> y &= \int \frac{1}{t^2-1} \, dt \\ 
>> y &= \int \frac{1}{(t+1)(t-1)} \, dt \\
>>\end{align}$$
>>>[!note]- Partial Fractions
>>>By the partial fractions method we look for $a,b$ satisfying
>>>$$\begin{alignat}{2}
>>>\frac{1}{(t+1)(t-1)}&=\frac{A}{t+1}+\frac{B}{t-1} \qquad&&\Big\vert \cdot(t+1)(t-1) \\
>>>1&=\frac{A\cancel{ (t+1) }(t-1)}{\cancel{ t+1 }}+\frac{B(t+1)\cancel{ (t-1) }}{\cancel{ t-1 }} \qquad&& \\
>>>1 &= A(t-1)+B(t+1) \\
>>>1 &= At-A+Bt+B \\
>>>1 &= At+Bt - A+B \\
>>>1 &=t(A+B)-A+B
>>>\end{alignat}$$
>>>We choose $A+B = 0$ and therefore require $1 = -A+B$. We have a system of linear equations and solve
>>>$$\begin{alignat}{2}
>>> \begin{pmatrix}
>>>1 &1 \\
>>>-1 & 1
>>>\end{pmatrix} &=\begin{pmatrix}
>>> 0\\1 
>>>\end{pmatrix} \qquad&&\Big\vert (I)+(II) \\
>>> \begin{pmatrix}
>>>1 &1 \\
>>>0 & 2
>>>\end{pmatrix} &=\begin{pmatrix}
>>> 0\\1 
>>>\end{pmatrix} \qquad&&\Big\vert (II):2 \\
>>> \begin{pmatrix}
>>>1 &1 \\
>>>0 & 1
>>>\end{pmatrix} &=\begin{pmatrix}
>>> 0\\ \frac{1}{2} 
>>>\end{pmatrix} \qquad&&\\
>>>\end{alignat}$$
>>>Hence we have $$B=\frac{1}{2}$$ and
>>>$$\begin{align}
>>>A + \frac{1}{2} &= 0  \\
>>>A &= -\frac{1}{2}
>>>\end{align}$$
>>
>> The fraction under the integral can be simplified to
>> $$\begin{align}
>> \frac{1}{(t+1)(t-1)}&=\frac{-\frac{1}{2}}{(t+1)}+\frac{\frac{1}{2}}{(t-1)} \\
>> &= \frac{1}{2} \left( \frac{1}{t-1}-\frac{1}{t+1} \right)
>>\end{align}$$
>>Hence, we have
>>$$\begin{align}
>>y &= \frac{1}{2}\int \frac{1}{t-1}-\frac{1}{t+1} \, dt  \\
>>  &= \frac{1}{2}\Big(\ln \lvert t-1 \rvert  - \ln\lvert t+1 \rvert \Big) + c
>>\end{align}$$
>>We now check for the initial value given as $y(0)=2$ and solve for $c$
>>$$\begin{align}
>>2 &= \frac{1}{2}(0-0) + c \\
>> 2&= c
>>\end{align}$$
>>Hence, the solution is
>>$$y=\frac{1}{2}\Big(\ln \lvert t-1 \rvert  - \ln\lvert t+1 \rvert \Big) + 2$$

^235d4c

>[!theorem] Theorem Variable $t$ is Missing (Case 2) ([[../../../PDFs/nagy.pdf#page=99| Source]])
> If the IVP
> $$y''=f(y,y')$$
> with 
> $$y(0)=y_{0} \; \text{ and } \; y'(0)=y_{1}$$
> has an _invertible_ solution $y$, then the function
> $$w(y)=v(t(y))$$
> where $$v(t)=y'(t)$$ and $t(y)$ is the inverse of $y(t)$, satisfies the IVP
> $$w' = \frac{f(y,w)}{w}$$
> with $$w(y_{0})=y_{1}$$
> and $$w' = \frac{dw}{dy}$$
>>[!proof]-
>> The original equation is denoted as
>> $$\begin{align}
>> y'' = f(y,y') 
>>\end{align}$$
>> We now denote $v(t)=y(t)'$, hence $v(t)' = y(t)''$. Therefore, we substitute and have
>> $$v'=f(y,v) \tag{1}$$
>> Given $y$ is invertible we denote the inverse as $t(y)$. We denote $$w(y)=v(t(y)) \tag{2}$$
>>>[!note]- Notation of inverse
>>> Assume the function $f(t) = y$, then the inverse is $f^{-1}(y)=g(y) =t$. We have
>>> $$\begin{align}
>>> f(t) &= y(t) \\
>>> g(y) = f^{-1}(y) &= t(y)
>>>\end{align}$$
>>
>> By the chain rule we can find the derivative of $w$, i.e. $w'$
>> $$\begin{align}
>> w'&= \frac{dw}{dy} \\
>>   &= \frac{dv}{\cancel{ dt }} \frac{\cancel{ dt }}{dy} \\
>>   &= \frac{dv}{dy} \\ 
>>   &= \frac{v'}{y'}
>>\end{align}$$
>>Recall in equation $(1)$, we substitute and have with equation $(2)$
>>$$\begin{align}
>> \frac{f\big(y(t),v(t)\big)}{v(t)} &= \frac{f(y,w(y))}{w(y)}
>>\end{align}$$
>>Hence, we have for found
>>$$w' = \frac{f(y,w)}{w}$$
>>Finally, we verify the initial condition for $w$. Recall we want to apply the initial condition to the inverse functions with $v=y'$, we have
>>$$\begin{alignat}{3}
>> y(t=0)&=y_{0} \quad &&\Longleftrightarrow \quad t(y=y_{0})&&=0 \\
>> y'(t=0)&=y_{1} &&\Longleftrightarrow \quad v(t=0)&&=y_{1}
>>\end{alignat}$$
>>Hence, for the claim $w(y_{0})$ we have
>>$$\begin{align}
>> w(y=y_{0})&=v(\underbrace{ t(y=y_{0}) }_{ =0 }) \tag*{by (2)} \\
>>  &= v(t=0) \\
>>  &= y_{1} \tag*{$\square$}
>>\end{align}$$
>
>>[!example]- Example Find a solution $y$ to the second order equation $y''=2yy'$
>>Note we do not have any variable $t$, such that we can make use of the theorem. We make the following substitution as suggested by the theorem
>>$$\begin{align}
>> v' = 2yv
>>\end{align}$$
>>We now want to determine $w(y)$, we use the suggested definition
>>$$\begin{align}
>> w' &= \frac{dw}{dy} \\
>> &= \frac{dv}{dy} \\
>> &= \frac{dv}{\cancel{ dt }} \frac{\cancel{ dt }}{dy} \\
>> &= \frac{dv}{dy}
>>\end{align}$$
>>Inserting gives
>>$$\begin{align}
>> \frac{dv}{dy} &=\frac{2yv}{y'} \\
>> &= \frac{2y\cancel{ v }}{\cancel{ v }} \\
>> &= 2y
>>\end{align}$$
>>Integrating with respect to y gives
>>$$\begin{align}
>> w &= \int 2y \, dy \\
>>  &= y^2+c 
>>\end{align}$$
>> By definition $w(y) = v(t(y))$, hence
>> $$\begin{align}
>> v&=y^2+c  \\
>> y' &= y^2 + c
>>\end{align}$$
>>This is a [[1 - First Order ODEs#^defSeparableDifferentialEquation| separable equation]], we solve accordingly and choose $c=1$
>>$$\begin{alignat}{2}
>>y'\frac{1}{y^2+c} &= 1 \\ 
>> \int \frac{1}{y^2 + 1} \, dy &= \int 1 \, dt  \\
>> \arctan(y) &= t + c_{0} \\
>> y &= \tan(t + c_{0})
>>\end{alignat}$$
>>Choosing $c_{0}=0$ gives
>>$$ y = \tan(t)$$
>
>>[!example]- Example Find the solution $y$ to the IVP $yy''+3(y')^2=0$ with $y(0)=1$ and $y'(0)=6$
>>Again we have an ODE with missing $t$, hence we can make use of the given theorem. We denote
>>$$\begin{align}
>> v&=y' \\
>> v' &= y''
>>\end{align}$$
>>Then the ODE can be given as 
>>$$\begin{align}
>> yv'+3v^2 = 0 \tag{1}
>>\end{align}$$
>>Now we want to determine $w(t)$ again which can be found over
>>$$\begin{align}
>> \frac{dw}{dy} &= \frac{dv}{dy} \\
>>           &= \frac{dv}{\cancel{ dt }} \frac{\cancel{ dt }}{dy} \\
>>           &= \frac{dv}{dy} \\
>>           &= \frac{v'}{v} \tag{2}
>>\end{align}$$
>>Solving equation $(1)$ for $y'$ gives
>>$$\begin{align}
>> v'=-\frac{3v^2}{y}
>>\end{align}$$
>>We insert this in $w'$, i.e. equation $(2)$
>>$$\begin{align}
>> w' &= \frac{v'}{v} \\
>>    &= \frac{\left( -\frac{3v²}{y} \right)}{v} \\
>>    &= -\frac{3v^2}{vy}
>>\end{align}$$
>>Note, we defined $w(y) = v(t(y))$, so we substitute
>>$$\begin{align}
>> w' = -\frac{3w^\cancel{ 2 }}{\cancel{ w }y}
>>\end{align}$$
>>This can be solved using [[1 - First Order ODEs#^defSeparableDifferentialEquation | separation of variables]], we get
>>$$\begin{alignat}{2}
>>w' \frac{1}{w} &= -\frac{3}{y}  \qquad&&\Big\vert \int   \\
>> \int \frac{1}{w} \, dw &= -3\int  \frac{1}{y} \, dy  + c_{0} \qquad&& \\
>> \ln(w) &= -3\ln(y) + c_{0} \qquad&&\Big\vert \exp() \\
>> w &= y^{-3} \underbrace{ e^{c_{0}} }_{ =c_{1} } \qquad&&\Big\vert :3 \\
>> w &=c_{1}y^{-3} \tag{3}
>>\end{alignat}$$
>>Our initial conditions are
>>$$\begin{alignat}{2}
>> y_{0} &= y(0) &&= 1 \\
>> y_{1} &=y'(0) &&= 6
>>\end{alignat}$$
>>and we have
>>$$w(y_{0}) = y_{1} \quad \Longrightarrow \quad w(1)=6 $$
>>inserting this result into equation $(3)$
>>$$ 6 = c_{1}$$
>>Having found $c_{1}$ we have a proper form for $w(y)$
>>$$w(y)= 6y^{-3}$$
>>Resubstituting $w(y)=v(t(y))=y'$ we get
>>$$y'=6y^{-3}$$
>>This can easily be solved by [[1 - First Order ODEs#^defSeparableDifferentialEquation | separation of variables]]
>>$$\begin{align}
>>y'y^3 &= 6 \\
>> \frac{1}{4}y^4 &= 6t + c \tag{4}
>>\end{align}$$
>>He we can use the initial condition $y_0=y(0)=1$ and get
>>$$\begin{align}
>> \frac{1}{4} &= c_{2}
>>\end{align}$$
>>Inserting the result into equation $(4)$ yields the solution to the IVP
>>$$\begin{alignat}{2}
>> \frac{1}{4}y^4 &= 6t+\frac{1}{4} \qquad&&\Big\vert \cdot 4 \\
>> y^4 &= 24t+1 \qquad&&\Big\vert \sqrt[4]{  }\\
>> y &= \sqrt[4]{  24t+1} \qquad\\
>>\end{alignat}$$

>[!theorem] Theorem Conservation of Energy ([[../../../PDFs/nagy.pdf#page=101| Source]])
>>[!note]- Change of Notation
>> We adapt the notation to its physical roots, which originate from Newtonian mechanics. We write now
>> $$y'' = f(y) \quad \Longleftrightarrow \quad my''=f(y)$$
>> with 
>> - $m$ being a constant, in Newtonian mechanics it represents the mass for a particle
>> - $y$ being the particle position function dependent of time $t$
>> - $f$ being a force depending on the particle position $y$
>
>Consider 
>- a particle with positive mass $m$ 
>- position $y$ as function of time $t$
>- velocity $v = y'$
>
>where $y$ is a solution of Newton's second law of motion
>$$my''=f(y) \tag{1}$$
>with initial conditions
>$$y(t_{0})=y_{0} \quad \text{and} \quad y'(t_{0})=v_{0}$$
>where $f(y)$ is the force acting on the particle at the position $y$. 
>
>Then, the position function $y$ satisfies
>$$\frac{1}{2}mv^2 + V(y) = E_{0}$$
>where $E_{0}=\frac{1}{2}mv_{0}^2 + V(y_{0})$ is fixed by the initial conditions $v(t)=y'(t)$ is the particle velocity, and $V$ is the potential of the force $f$, that is
>$$V(y)=-\int f(y) \, dy \quad\Longleftrightarrow\quad f(y)=-\frac{dV}{dy} \tag{2}$$
>>[!remark]-
>>The term $T(v)=\frac{1}{2}mv^2$ is the kinetic energy of the particle. The term $V(y)$ is the potential energy. The theorem above says that the total mechanical energy
>>$$E=T(v)+ V(y)$$
>>remains constant during the motion of the particle. Potential energy can be interpreted as the energy "stored" in an object, like the gravitational energy stored in an object.
>
>>[!proof]-
>> We use equation $(1)$ and $(2)$ and set them equal, we have
>> $$\begin{alignat}{2}
>> my'' &= -\frac{dV}{dy} \\
>> m \frac{d^2y}{dt^2} &= -\frac{dV}{dy} \qquad&&\Big\vert \cdot y'=\frac{dy}{dt} \\
>> m \frac{d^2y}{dt^2}\frac{dy}{dt} &= -\frac{dV}{\cancel{ dy }}\frac{\cancel{ dy }}{dt} \qquad&& \\
>> \frac{d}{dt}\left( \frac{1}{2}m \left( \frac{dy}{dt} \right)^2 \right) &= -\frac{dV}{dt} \qquad&& \tag{Inverse Chain Rule}\\
>>\end{alignat}$$
>>Inserting the definition of the velocity $v(t)=\frac{dy}{dt}$ gives
>>$$\begin{alignat}{2}
>> -\frac{dV}{dt} &= \frac{d}{dt} \left( \frac{1}{2}mv^2  \right) \qquad&&\Big\vert +\frac{dV}{dt} \\
>> 0 &= \frac{d}{dt} \left( \frac{1}{2}mv^2 +V \right) \qquad&&  \\
>>\end{alignat}$$
>>Integrating with respect to $t$ yields the constant
>>$$\begin{align}
>> E(y,v) = \frac{1}{2}mv(t)^2+V(y)
>>\end{align}$$
>>which is the verifies the conservation of energy. $$\tag*{$\square$}$$
>
>>[!example] Examples Find the potential energy and write the energy conservation for the following systems
>>>[!example]- A particle attached to a spring with constant $k$, moving in one space dimension
>>> The force on a particle of mass $m$ attached to a spring with spring constant $k>0$, when displaced an amount $y$ from the equilibrium position $y=0$ is $f(y)=-ky$. Imagine the spring being squished, hence the position of $y$ is decreased by the displacement $k$. Applying Newton's law of motion we have
>>> $$\begin{align}
>>> my''=-ky
>>>\end{align}$$
>>>The potential energy is given by
>>>$$\begin{align}
>>> V(y)&= -\int f(y) \, dy \\
>>>&= -\int -ky \, dy \\
>>>&= \frac{1}{2}ky^2  \\
>>>\end{align}$$
>>>Note, we have the acceleration $v=y'$ and can therefore write by the given theorem the total mechanical energy can be given as
>>>$$E=\frac{1}{2}mv^2 + \frac{1}{2}ky^2$$
>>>with it also being the initial energy $E_0$ as the energy remains constant.
>>
>>>[!example]- A particle moving vertically close to the Earth surface, under Earth's constant gravitational acceleration. In this case the force on the particle having mass $m$ is $f(y)=mg$ with $g=9.81 \frac{m}{s^2}$
>>>Again we have the location of the particle given by
>>>$$f(y)=mg$$
>>>Hence, by the theorem we have
>>>$$\begin{alignat}{2}
>>> my''&=mg \qquad&&\Big\vert \cdot y' \\
>>> my''y' &= mgy' \\
>>> \frac{d}{dt}\left( \frac{1}{2}m(y')^2 \right) &= \frac{d}{dt}(mgy) \qquad&&\Big\vert -\frac{d}{dt}(mgy) \\
>>> \frac{d}{dt}\left( \frac{1}{2}m(y')^2 - mgy \right) &= 0 \qquad&&\Big\vert \int  \, dt  \\ 
>>>  \frac{1}{2}mv^2 - mgy &= E(y,v)\tag{$v=y'$}
>>>\end{alignat}$$
>>>>[!remark]
>>>>The gravitational Energy is constant, because $\frac{d}{dt}E(y,v)=0$.


>[!theorem] Theorem Reduction of Order ([[../../../PDFs/nagy.pdf#page=106| Source]])
>If a nonzero function $y_{1}$ is solution to 
>$$y''+a_{1}(t)y' + a_{0}(t)y = 0 \tag{1}$$
>where $a_{1},a_{0}$ are given functions, then a second solution not proportional to $y_{1}$ is
>$$y_{2}(t)=y_{1}(t)\int \frac{e^{-A_{1}(t)}}{y^2_{1}(t)} \, dt $$
>where $$A_{1}(t)=\int a_{1}(t) \, dt $$
>>[!remark] Important Remark
>> Here we assume, we have found already a solution $y_1$ and we are interested to find all solutions in the solutions space for a given _second order, linear, homogeneous, differential equation_. **We transform the problem of a second order problem to two first order problems.**
>
>>[!remark] Remark on non-proportional Solutions
>>In the theory of linear ordinary differential equations, solutions that are linearly independent are crucial because they form a basis for the solution space. Having solutions that are linearly independent ensures that you can form any solution to the differential equation as a linear combination of these solutions.
>
>>[!proof]-
>>We first rewrite $y_2$ as **linear combination of the solution** $y_1$ with $v$ being a function of $t$ and compute its derivatives
>>$$\begin{align}
>> y_{2}&= v y_{1}  \tag{2}\\
>> y_{2}' &= v'y_{1} + vy_{1}' \\
>> y_{2}'' &= v''y_{1} + v'y_{1}' + v'y_{1}' + vy_{1}'' \\
>>  &= v''y_{1}+ 2v'y_{1}' + vy_{1}''
>>\end{align}$$
>>and insert the expression into the second order derivative $(1)$, such that we yield and sort for $v$
>>$$\begin{align}
>> ( v''y_{1}+ 2v'y_{1}' + vy_{1}'') + a_{1}(v'y_{1} + vy_{1}') + a_{0}v y_{1} &= 0 \\
>> y_{1}v'' + \Big(2y_{1}'+ a_{1}y_{1}\Big)v' + \Big(y_{1}''+a_{1}y_{1}'+a_{0}y_{1}\Big)v &= 0
>>\end{align}$$
>>
>>The function $y_1$ is solution to the differential original equation
>>$$\begin{align}
>> y_{1}'' + a_{1}y_{1}' + a_{0}y_{1} &= 0 \\
>> y_{1}'' &= -a_{1}y_{1}' - a_{0}y_{1} \tag{3}
>>\end{align}$$
>>then, the equation for $v$ is given by
>>$$\begin{alignat}{2}
>> y_{1}v'' + \Big(2y_{1}'+ a_{1}y_{1}\Big)v' + \Big(\underbrace{ y_{1}'' }_{ =(2) }+a_{1}y_{1}'+a_{0}y_{1}\Big)v &= 0 \\
>> y_{1}v'' + \Big(2y_{1}'+ a_{1}y_{1}\Big)v' + \cancel{ \Big(-a_{1}y_{1}' - a_{0}y_{1}+a_{1}y_{1}'+a_{0}y_{1}\Big)v } &= 0 \\
>> y_{1}v'' + \Big(2y_{1}'+ a_{1}y_{1}\Big)v' &= 0 \qquad&&\Big\vert :y_{1} \\
>> v'' + \left( 2\frac{y_{1}'}{y_{1}}+ a_{1} \right)v' &= 0
>>\end{alignat}$$
>>Here we can make use of [[#^235d4c| Theorem Function y is missing (Case 1)]] and substitute $w=v'$ and get 
>>$$w' + \left( 2\frac{y_{1}'}{y_{1}}+ a_{1} \right)w = 0$$
>>This can be solved using the first order ODE method of [[1 - First Order ODEs#^defSeparableDifferentialEquation| separation of variables]]. We have
>>$$\begin{alignat}{2}
>> w' + \left( 2\frac{y_{1}'}{y_{1}}+ a_{1} \right)w &= 0 \qquad&&\Big\vert :w \\
>> \frac{w'}{w} + 2\frac{y_{1}'}{y_{1}}+ a_{1} &= 0 \qquad&&\Big\vert -2\frac{y_{1}'}{y_{1}}-a_{1} \\
>> \frac{w'}{w} &= -2\frac{y_{1}'}{y_{1}}-a_{1} \qquad&&\Big\vert \int  \,    \tag{Separation} \\
>> \int \frac{1}{w} \, dw &= -2 \int \frac{1}{y_{1}} \, dy_{1} -\underbrace{ \int a_{1} \, dt }_{ =A_{1} } +c   \qquad&& \\
>> \ln \lvert w \rvert &= -2\ln \lvert y_{1} \rvert  -A_{1} + c \qquad&&\Big\vert e^{(\cdot)} \\
>> w &= y_{1}^{-2}\underbrace{ e^c }_{ =w_{0} }e^{-A_{1}} \\
>> w &= w_{0}\frac{e^{-A_{1}}}{y_{1}^2} \tag{4}
>>\end{alignat}$$
>>Note, we introduced $w=v'$, therefore we still need to integrate one more time with respect to $t$
>>$$v(t) = w_{0} \int \frac{e^{-A_{1}}}{y_{1}^2} + v_{0} \, dt $$
>> Since we are trying to determine no specific solution to the given ODE, we can choose sensible integration constants $w_{0},v_{0}$, therefore, we choose
>> $$\begin{align}
>> w_{0}&=1 \\
>> v_{0}&=0
>>\end{align}$$
>>and get
>>$$v(t) = \int \frac{e^{-A_{1}}}{y_{1}^2} \, dt$$
>>Note, from equation $(2)$ we can derive
>>$$\begin{align}
>> y_{2}&= v y_{1} \\
>> v &= \frac{y_{2}}{y_{1}} 
>>\end{align}$$
>>Inserting and rearranging yields
>>$$\begin{align}
>> \frac{y_{2}}{y_{1} }&= \int \frac{e^{-A_{1}}}{y_{1}^2} \, dt \\
>> y_{2} &= y_{1}\int \frac{e^{-A_{1}}}{y_{1}^2} \, dt
>>\end{align}$$
>> Finally, we show that $y_{1},y_{2}$ are fundamental solutions, i.e. are linearly independent. We use for this [[#^5577c0| Wronskian's second theorem]]. Therefore we compute the [[#^42635c| Wronskian function]] $W_{12}$ and get
>> $$\begin{align}
>> W_{12} &= \begin{vmatrix}
>> y_{1} & vy_{1} \\
>> y_{1}' & (v'y_{1} + vy_{1}') \\
>>\end{vmatrix} \\
>> &= y_{1}(v'y_{1}+vy_{1}') - vy_{1}'y_{1}\\ 
>> &= v'y_{1}^2+\cancel{ vy_{1}'y_{1} } \cancel{ - vy_{1}'y_{1} }\\ 
>>\end{align}$$
>>Note, we computed earlier in equation $(4)$ an expression for $w = v'$, hence, we substitute for $v'$ with $w_{0}=1$ and get
>>$$\begin{align}
>> v'y_{1^2} &= \frac{e^{-A_{1}}}{\cancel{ y_{1}^2 }}\cancel{ y_{1}^2 } \\
>>  &= e^{-A_{1}}
>>\end{align}$$
>>Hence, the Wronskian can never equal to zero. By [[#^5577c0| Wronskian's second theorem]] we know that the solutions are linearly independent. This concludes the proof.
>>$$\tag*{$\square$}$$
>
>>[!proof] Constructive Proof ([[../../../PDFs/nagy.pdf#page=116| Omitted but given here]])
>
>>[!example]
>>Find a second solution $y_{2}$ linearly independent to the solution $y_{1}(t)=t$ of the differential equation
>>$$t²y''+2ty'-2y=0$$
>>>[!example]- Solution
>>>First we rearrange the given second order equation, such that we have the form of the theorem.
>>>$$\begin{align}
>>> y'' + \frac{2}{t}y' - \frac{2}{t^2}y =0
>>>\end{align}$$
>>>To find a second fundamental solution we use
>>>$$\begin{align}  
>>> y_{2}(t)&=y_{1}(t)\int \frac{e^{-A_{1}(t)}}{y^2_{1}(t)} \, dt \\
>>> A_{1}(t) &= \int a_{1}(t) \, dt 
>>>\end{align}$$
>>>We have 
>>>$$\begin{align}
>>> y_{1}(t) &= t \\
>>> a_{1}(t) &= \frac{2}{t}  \\
>>> A_{1}(t) &= \int a_{1}(t) \, dt \\
>>> &= \int \frac{2}{t} \, dt  \\
>>> &= 2 \ln \lvert t \rvert  \\
>>> &= \ln t^2 \\
>>> \int \frac{e^{-A_{1}(t)}}{y^2_{1}(t)} \, dt &= \int \frac{e^{- \ln t^2}}{t^2} \, dt \\
>>>  &= \int \frac{1}{t^2t^2} \, dt \\
>>>  &= \int \frac{1}{t^4} \, dt \\
>>>  &= -\frac{1}{3}t^{-3} +\underbrace{ c }_{ =0 }
>>>\end{align}$$
>>>We choose the integration constant to be zero, since it is sufficient to find a single fundamental solution linearly independent to $y_1$. We now solve
>>>$$\begin{align}
>>> y_{2}(t)&=y_{1}(t)\int \frac{e^{-A_{1}(t)}}{y^2_{1}(t)} \, dt \\
>>> y_{2}(t) &= t \left( -\frac{1}{3}t^{-3} \right) \\
>>> y_{2}(t) &= -\frac{1}{3}t^{-2} 
>>>\end{align}$$
>>>>[!note]- Solution Validation
>>>>$$\begin{align} \\
>>>> y_{2} &= -\frac{1}{3}t^{-2} \\
>>>> y_{2}' &= \frac{2}{3}t^{-3} \\
>>>> y_{2}'' &= -2t^{-4}
>>>>\end{align}$$
>>>>We insert into 
>>>>$$\begin{align}
>>>> t²y''+2ty'-2y&=0 \\
>>>> t^2 \cdot (-2t^{-4}) + 2t \left( -\frac{2}{3}t^{-3} \right) - 2 \left( -\frac{1}{3}t^{-2} \right) &= 0 \\
>>>> -2t^{-2} -\frac{4}{3}t^{-2}+\frac{2}{3}t^{-2} &= 0 \\
>>>> 0 &= 0
>>>>\end{align}$$
>>>>Note, linear independence should be validated too using the Wronskian function.

>[!example] Exercises
>>[!example] Task
>>Consider the differential equation
>>$$t^2y''+3ty'-3=0, \quad t>0$$
>>with initial conditions
>>$$y(1)= 3 \qquad y'(1)=\frac{3}{2}$$
>>1. Find the initial value problem satisfied by $v(t)=y'(t)$
>>2. Solve the differential equation for $v$
>>3. Find the solution $y$ of the differential equation above
>>
>>>[!example]- Solution
>>>Note, we have the case $y'' = f(t,\cancel{ y },y')$, where $y$ does not appear explicitly. We can use [[#^235d4c | the corresponding theorem]] and substitute $v = y'$ and get
>>>$$t^2v'+2tv-3=0$$
>>>This is a [[1 - First Order ODEs#^defThmSolODEVar | first order differential equation with variable coefficients]], we have
>>>$$v' = \underbrace{ -\frac{3}{t} }_{ =a(t) }v \underbrace{- \frac{3}{t^2} }_{ =b(t) }$$ 
>>>We use the solution formula
>>>$$\begin{align}
>>> v &= c_{1}e^{A(t)}+e^{A(t)}\int e^{-A(t)}b(t) \, dt  \\
>>> A(t) &= \int a(t) \, dt 
>>>\end{align}$$
>>>We get
>>>$$\begin{align}
>>> A(t) &= \int a(t) \, dt \\
>>> &=   \int -\frac{3}{t} \, dt \\
>>> &=   -3\ln \lvert t \rvert  \\
>>> &= \ln \lvert t^{-3} \rvert \\
>>> e^{A(t)} &=  t^{-3} \\
>>> e^{-A(t)} &= t^{3} \\
>>> \int e^{-A(t)}b(t) \, dt &= \int t^3\left( -\frac{3}{t^2} \right)  \, dt \\
>>>  &= -\int 3t  \, dt \\
>>>  &= \frac{3}{2}t^2   
>>>\end{align}$$
>>>We finally get for $v$
>>>$$\begin{align}
>>> v &= c_{1}t^{-3}+ t^{-3}\left( \frac{3}{2}t^2 \right) \\
>>>   &= c_{1}t^{-3}+  \frac{3}{2}t^{-1}
>>>\end{align}$$
>>>Since we defined $v= y'$ we integrate one more time to yield $y$
>>>$$\begin{align}
>>> y &= \int c_{1}t^{-3}  \, dt + \int \frac{3}{2}t^{-1} \, dt   \\
>>> &= -c_{1} \frac{1}{2}t^{-2}+\frac{3}{2}\ln \lvert t \rvert + c 
>>>\end{align}$$

## 2.3 Homogeneous Constant Coefficients Equations

>[!def] Definition Characteristic Polynomial ([[../../../PDFs/nagy.pdf#page=111| Source]])
>The **characteristic polynomial** and **characteristic equation** of the second order linear homogeneous equation with constant coefficients
>$$y''+a_{1}y'+a_{0}y = 0$$
>are given by
>$$p(r)=r^2+a_{1}r+a_{0}, \qquad p(r)=0$$

^9bcb76

>[!theorem] Theorem Solutions for the Characteristic Polynomial with Constant Coefficients ([[../../../PDFs/nagy.pdf#page=111| Source]])
>If $r_{\pm}$ are the roots of the characteristic polynomial to the second order linear homogeneous equation with constant coefficients
>$$y''+a_{1}y'+a_{0}y=0 \tag{1}$$
>and if $c_{+}, c_{-}$ are arbitrary constants, then the following statement holds true
>1. If $r_{+} \neq r_{-}$, real or complex, then the general solution of equation $(1)$ can be given by
>$$y_{gen}(t)=c_{+}e^{r_{+}t} + c_{-}e^{r_{-}t}$$
>2. If $r_{+}=r_{-}=r_{0} \in \mathbb{R}$, then the general solution of equation $(1)$ is given by
>$$y_{gen}(t)=c_{+}e^{r_{0}t} + c_{-}te^{r_{0}t}$$
>
>Furthermore, given real constants $t_{0}, y_{0}$ and $y_{1}$, there is a unique solution to the initial value problem given by equation $(1)$ and the initial conditions $y(t_{0})=y_{0}$ and $y'(t_{0})=y_{1}$.
>>[!proof]-
>>>[!remark]
>>>This proof involves guessing that functions $y(t)=e^{rt}$ must be solutions. The next proof will be constructive and won't involve guessing the solutions.
>>
>>As mentioned we guess, that $y(t)=e^{rt}$ must be solution for the given ODE, since we can cancel out the exponential function as follows. Therefore, we insert the solution in equation $(1)$ accordingly
>>$$\begin{align}
>> y''+a_{1}y'+a_{0}y&=0 \\
>> (e^{rt})''+a_{1}(e^{rt})'+a_{0}e^{rt}&=0 \\
>> r^2e^{rt}+a_{1}re^{rt}+a_{0}e^{rt}&=0 \qquad&&\Big\vert : e^{rt} \\ 
>> r^2+a_{1}r+a_{0}&=0 \tag{2}
>>\end{align}$$
>>From equation $(2)$ we understand, that we have two cases for the solutions $r_{+}, r_{-}$ as suggested by the theorem.
>>> Case $r_+ \neq r_-$
>>
>>We have the solutions
>>$$y_{+}(t) = e^{r_{+}t}\qquad y_{-}(t)=e^{r_{-}t}$$
>> which must be linearly independent, because the exponential functions have different exponents. Hence, we  can give the general solution as the linear combination
>> $$y_{gen}(t)=c_{+}e^{r_{+}t} + c_{-}e^{r_{-}t} $$
>>> Case $r_{+} = r_{-}=r_{0}$
>>
>>We now have the single solution
>>$$y_{+}(t)=e^{r_{0}t}$$
>> To find a second solution not proportional to $y_{+}$, we use the reduction of order method. Therefore, we write
>> $$\begin{align}
>> y_{-}(t) &= v(t)y_{+}(t) \\
>>  &= v(t)e^{r_{0}t}
>>\end{align}$$
>>We have to determine the first two derivatives to insert those into equation $(1)$
>>$$\begin{align}
>> y_{-} &= ve^{r_{0}t}  \\
>> y_{-}' &= v'e^{r_{0}t} + r_{0}ve^{r_{0}t} \\
>> y_{-}'' &= v''e^{r_{0}t} + 2r_{0}v'e^{r_{0}t} + r_{0}^2ve^{r_{0}t}
>>\end{align}$$
>>We insert the derivatives into equation $(1)$ and rearrange, such that we make the terms dependent on $v$.
>>$$\begin{align}
>> y_{-}''+a_{1}y_{-}'+a_{0}y_{-}&=0  \\
>> v''e^{r_{0}t} + 2r_{0}v'e^{r_{0}t} + r_{0}^2ve^{r_{0}t} + a_{1}(v'e^{r_{0}t} + r_{0}ve^{r_{0}t}) + a_{0}(ve^{r_{0}t}) &= 0 \\
>> v''e^{r_{0}t} + v'e^{r_{0}t}(2r_{0}+ a_{1}) + ve^{r_{0}t}(r^2_{0}+a_{1}r_{0}+a_{0}) &=0 \qquad&&\Big\vert : e^{r_{0}t} \\
>> v'' + v'(2r_{0}+ a_{1}) + v(r^2_{0}+a_{1}r_{0}+a_{0}) &=0 \tag{3}
>>\end{align}$$
>>Note, by equation $(2)$ we determined $r^2_{0}+a_{1}r_{0}+a_{0} = 0$ and get
>>$$v'' + v'(2r_{0}+ a_{1}) = 0$$
>>Further note, we determine the solution $r_0$ by computing
>>$$r_{0} = -\frac{a_{1}}{2}\pm \frac{1}{2}\sqrt{ a_{1}^2 -4a_{0} }$$
>>The root must be $0$, because we have a single solution to the characteristic polynomial, hence,
>>$$r_{0} = -\frac{a_{1}}{2}$$
>>We rearrange
>>$$2r_{0}+a_{1}=0$$
>>The term $v'(2r_{0}+ a_{1})$ in equation $(3)$ therefore vanishes and we have 
>>$$v'' = 0$$
>>Integrating two times gives
>>$$v = c_{1}+c_{2}t$$
>>Since we require the second solution to be proportional to $y_{1}$, we have to require $c_2 \neq 0$. We are able to choose $c_{1}= 0$ and $c_{2}= 1$ and yield
>>$$v = t$$
>>Hence, the fundamental solutions can be given as
>>$$\begin{align}
>> y_{+}(t) &= e^{r_{0}t} \\
>> y_{-}(t) &= te^{r_{0}t}
>>\end{align}$$
>>and the general solution can be given as
>>$$y_{gen}(t) = c_{+}e^{r_{0}t}+ c_{-}te^{r_{0}t}$$
>>>Unique Solutions of the Initial Value Problems for $r_+ \neq r_-$
>>
>>Given are $y(t_{0})=y_{0}$ and $y'(t_{0})=y_{1}$, so we first describe these functions with respect to the general solution
>>$$\begin{align}
>> y_{0} &=c_{+}e^{r_{+}t} + c_{-}e^{r_{-}t} \\
>> y_{1} &= r_{+}c_{+}e^{r_{+}t} + r_{-}c_{-}e^{r_{-}t}
>>\end{align}$$
>>which yields a system of equations we want to solve for $c_+$ and $c_{-}$, where we have
>>$$\begin{align}
>> c_{+} &= - \frac{r_{-}y_{0}-y_{1}}{(r_{+}-r_{-})e^{r_{+}t_{0}}} \\
>> c_{-} &= \frac{r_{+}y_{0}-y_{1}}{(r_{+}-r_{-})e^{r_{-}t_{0}}} 
>>\end{align}$$
>>>Unique Solutions of the Initial Value Problems for $r_+ = r_- = r_{0}$
>>
>>In this case we get the following equations
>>$$\begin{align}
>> y_{0} &= (c_{+} + c_{-}t_{0})e^{r_{0}t_{0}} \\
>> y_{1} &= c_{-}e^{r_{0}t_{0}} + r_{0}(c_{+}+c_{-}t_{0})e^{r_{0}t_{0}}
>>\end{align}$$
>>where we yield the following solutions
>>$$\begin{align}
>> c_{+} &= \frac{y_{0} +t_{0}(r_{0}y_{0}-y_{1})}{e^{r_{0}t_{0}}} \\
>> c_{-} &= \frac{r_{0}y_{0}-y_{0}}{e^{r_{0}t_{0}}} 
>>\end{align}$$
>>$$\tag*{$\square$}$$
>
>>[!example] 
>>Find the general solution $y_{gen}$ of the differential equation
>>$$2y''-3y'+y=0$$
>>>[!example]- Solution
>>>First, we bring the 2nd order homogeneous differential equation in the standard form, hence
>>>$$y'' -\frac{3}{2}y' + \frac{1}{2}y$$
>>>The characteristic polynomial can be given as
>>>$$\begin{align}
>>>p(r) &= r^2-\frac{3}{2}r+\frac{1}{2}
>>>\end{align}$$
>>>Solving yields
>>>$$\begin{align}
>>> r_{\pm} &= \frac{3}{4}\pm \sqrt{ \frac{9}{16}-\frac{1}{2} } \\
>>>  &= \frac{3}{4}\pm \sqrt{ \frac{1}{16} } \\ 
>>> r_{+} &= 1 \\
>> r_{-} &= \frac{1}{2}
>>>\end{align}$$
>>>We note having the case $r_{+}\neq r_{-}$, therefore the general solution can be given as
>>>$$y_{gen}= c_{+}e^{t}+c_{-}e^{(1/2)t}$$
>
>>[!example]
>> Find the solution to the initial value problem
>> $$9y''+6y'+y=0$$
>> with
>> $$y(0)=1 \qquad y'(0)=\frac{5}{3}$$
>>>[!example]- Solution
>>> First we represent the differential equation in its normalform
>>> $$y'' + \frac{2}{3}y' + \frac{1}{9}y = 0$$
>>> and get the characteristic polynomial
>>> $$r^2 + \frac{2}{3}r + \frac{1}{9} = 0$$
>>> Solving for solutions gives
>>> $$\begin{align}
>>> r_{0} &= -\frac{1}{3}
>>>\end{align}$$
>>>According to the theorem we can give the general solution as
>>>$$y_{gen}(t) = c_{+}e^{-(1/3)t} + c_{-}te^{-(1/3)t}$$
>>> Computing the derivative
>>> $$y'_{gen}(t) = -\frac{1}{3}c_{+}e^{-(1/3)t} + \left(1 -\frac{t}{3} \right)c_{-}e^{-(1/3)t}$$
>>> Inserting the initial conditions gives
>>> $$\begin{align}
>>> 1 &= c_{+}e^{0} + c_{-}te^{0} \tag*{y(0)=1} \\
>>> 1 &= c_{+} \\ \\
>>> \frac{5}{3} &= -\frac{1}{3}c_{+}e^{0} +  \left(1 -\frac{0}{3} \right)c_{-}e^{0} \tag*{y'(0)=5/3} \\
>>> \frac{5}{3} &= -\frac{1}{3}c_{+} + c_{-} 
>>>\end{align}$$
>>>We have the first solution of the system of equations and can solve therefore
>>>$$\begin{align}
>>> c_{+} &= 1 \tag{1}\\
>>> \frac{5}{3} &= -\frac{1}{3} + c_{-}  \tag{2} \\
>>> c_{-} &= 2
>>>\end{align}$$
>
>>[!example]
>> Find the solution to the initial value problem
>> $$y''+5y'+6y=0$$
>> with
>> $$y(0)=1 \qquad y'(0)=-1$$
>>>[!example]- Solution
>>> We determine the characteristic polynomial
>>> $$r^2+5r+6 = 0$$
>>> The solutions to this polynom can be given as
>>> $$\begin{align}
>>> r_{+} &= -2 \\
>>> r_{-} &=-3
>>>\end{align}$$
>>>We have the case $r_{+} \neq r_{-}$. Using the solution formula given by the theorem we can state the general solution as
>>>$$y_{gen}(t) = c_{-}e^{-3t}+c_{+}e^{-2t}$$
>>>Computing the first derivative gives
>>>$$y_{gen}'(t) = -3c_{-}e^{-3t}-2c_{+}e^{-2t}$$
>>>Inserting the initial conditions gives
>>>$$\begin{align}
>>> 1 &= c_{-}e^{0}+c_{+}e^{0} \tag*{y(0)=1}  \\
>>> 1 &= c_{-} + c_{+} \\ \\
>>> -1 &= -3c_{-}e^{0}-2c_{+}e^{0} \tag*{y'(0)=-1} \\
>>> -1 &= -3c_{-}-2c_{+}
>>>\end{align}$$
>>>This yields the system of equations
>>>$$\begin{align}
>>> 1 &= c_{-} + c_{+} \tag{1} \\
>>> 1 &= -3c_{-}-2c_{+} \tag{2}
>>>\end{align}$$
>>>which gives the solutions
>>>$$\begin{align}
>>> c_{+}&=2 \\
>>> c_{-}&= -1
>>>\end{align}$$
>>>Inserting the solutions for $c_{+}, c_{-}$ gives
>>>$$y(t) = 2e^{-2t}-e^{-3t}$$
>
>>[!example]
>>Find the general solution $y_{gen}$ of the equation
>>$$y''-2y'+6y =0 $$
>>>[!example]- Solution
>>> The characteristic polynom can be given as
>>> $$r^2-2r + 6 = 0$$
>>> Solving gives the following complex solutions
>>> $$\begin{align}
>>> r_{+} &= 1 + i\sqrt{ 5 } \\ 
>>> r_{-} &= 1 - i\sqrt{ 5 } \\ 
>>>\end{align}$$
>>>The theorem includes complex solutions, hence we state the general solution
>>>$$y_{gen}(t)=c_{+}e^{(1 + i\sqrt{ 5 })t} + c_{-}e^{(1 - i\sqrt{ 5 })t}$$

^702f6f

>[!remark]
>We now analyze how to extract real valued solutions from complex general solutions.

>[!theorem] Theorem Real Valued Fundamental Solutions ([[../../../PDFs/nagy.pdf#page=114| Source]])
>If the differential equation
>$$y'' + a_{1}y' + a_{0}y = 0$$
>where $a_{1}, a_{0}$ are real constants, has a characteristic polynomial with complex roots $r_{\pm}= \alpha \pm i\beta$ and complex valued fundamental solutions
>$$\begin{align}
> \tilde{y}_{+}(t) &= e^{(\alpha+i\beta)t}  \\
> \tilde{y}_{-}(t) &= e^{(\alpha-i\beta)t} 
>\end{align}$$ 
>then the equation also has real valued fundamental solutions given by
>$$\begin{align}
> y_{+}(t) &= e^{\alpha t}\cos(\beta t)  \\
> y_{-}(t) &= e^{\alpha t} \sin(\beta t)
>\end{align}$$
>>[!proof]-
>>First, we decompose the complex solutions using the [[../Complex Analysis/Fundamental Properties|properties of complex numbers]]
>>$$\begin{align}
>> \tilde{y}_{\pm}(t)&= e^{(\alpha \pm i \beta)t} \\
>> &= e^{\alpha t}e ^{ \pm i \beta t} \\
>> &= e^{\alpha t}(\cos \beta t \pm i \sin \beta t)
>>\end{align}$$
>>Since we have a **homogeneous differential equation** we can apply the [[#^88d6f3| superposition theorem]], which states we can compose any solution by a linear combination of $\tilde{y}_{+}$ and $\tilde{y}_{-}$ with arbitrary constants $c_1$ and $c_2$. Choosing $c_1=\frac{1}{2}$ and $c_{2}=\frac{1}{2i}$ will yield the desired result. We get
>>$$\begin{align}
>> y_{+}(t) &= \frac{1}{2}(\tilde{y}_{+}(t) + \tilde{y}_{-}(t)) \\
>>  &= \frac{1}{2}\Big(e^{\alpha t}(\cos \beta t + i \sin \beta t) + e^{\alpha t}(\cos \beta t - i \sin \beta t)\Big) \\
>>  &= \frac{1}{2}\Big(e^{\alpha t}(\cos \beta t \cancel{ + i \sin \beta t } + \cos \beta t \cancel{ - i \sin \beta t })\Big) \\ 
>> &= e^{\alpha t}\cos \beta t \\
>> y_{-}(t) &= \frac{1}{2i}(\tilde{y}_{+}(t) - \tilde{y}_{-}(t)) \\
>>  &= \frac{1}{2i}\Big(e^{\alpha t}(\cos \beta t + i \sin \beta t) - e^{\alpha t}(\cos \beta t - i \sin \beta t)\Big) \\
>>  &= \frac{1}{2i}\Big(e^{\alpha t}(\cancel{ \cos \beta t  }+ i \sin \beta t \cancel{ - \cos \beta t } + i \sin \beta t)\Big) \\
>>  &= \frac{1}{2i}\Big(2i e^{\alpha t} \sin \beta t \Big) \\
>>  &= i e^{\alpha t} \sin \beta t \tag*{$\square$} \\
>>\end{align}$$
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
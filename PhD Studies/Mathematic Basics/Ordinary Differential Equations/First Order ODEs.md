---
aliases:
- First Order ODE
- Linear First Order ODE
---

>[!Source]-
>URL: 
>PDF: [PDF](nagy.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@nagy)

>[!observation]- Introduction ([[../../../Sources/nagy.pdf#page=12|Source]])
> A differential equation is an equation, where the unknown is a function and both the function and its derivatives may appear in the equation.
>
>>[!example] Example Newton's law
>> Mass $\times$ Acceleration $=$ Force
>> $$ ma =f $$
>>
| variable                           | meaning                       |
| ---------------------------------- | ----------------------------- |
| $m$                                | particle                      |
| $a = \dfrac{d^2 \mathbf{x}}{dt^2}$ | particle acceleration         |
| $f$                                | force acting on the particle  |
| $\mathbf{x}(t)$                    | particle position at time $t$ |
>> can be rewritten as
>> $$ m \frac{d^2\mathbf{x}}{dt^2}(t) = \mathbf{f}\Big(f, \mathbf{x}(t), \frac{d\mathbf{x}}{dt}(t)\Big)$$
>> being a **Second Order Ordinary Differential Equation (ODE)** with the unknown 
>
>>[!example] Example Radioactive Decay
>>The amount $u$ of radioactive material changes in time as follows
>>$$ \frac{du}{dt}(t) = -k\,u(t)$$
>>with $k>0$ representing the radioactive properties of the material. This is a **First order ODE**
>
>>[!example] The Heat Equation
>>Temperature $T$ changes in solid material over time in three space dimensions $\mathbf{x} = (x,y,z)$
>>$$\frac{\partial T}{\partial t}(t, \mathbf{x}) = k \left(\frac{\partial^2 T}{\partial x^2}(t, \mathbf{x}) + \frac{\partial^2 T}{\partial y^2}(t, \mathbf{x}) \frac{\partial^2 T}{\partial z^2}(t, \mathbf{x})\right)$$
>>with $k>0$ being the positive constant representing thermal properties of the material. This is a **First Order Partial Differential Equation (PDE) in Time** and a **Second Order PDE in Space**. 
>

<br>

## 1 - Solving Linear Differential Equations

>[!def] Definition First Order ODE ([[../../../Sources/nagy.pdf#page=13|Source]])
>A first order ODE on the unknown $y$ is given as 
>$$ y'(t) = f(t,y(t))$$
>where $f$ is given and $y' = \dfrac{dy}{dt}$. The equation is linear iff the source function is linear on its second argument, i.e.
>$$y' = a(t)y + b(t) \tag{1}$$
> with the coefficient name convention
> 
| Name                      | Condition                |
| ------------------------- | ------------------------ |
| **Constant Coefficients** | $a, b$ both are constant |
| **Variable Coefficients** | Otherwise                |
>>[!note]- Note Different Sign Conventions
>>There are different name conventions used for equation (1) in literature, which are only a matter of taste, i.e.
>>$$ y' = -ay + b $$
>>^deffirstorderODE
>
>>[!example]- Examples (Equations)
>>>[!example] Example 1 (First Order Linear ODE)
>>>$$ y' =  2y + 3$$
>>>with the function 
>>>$$ \begin{align} f(t,y) &= 2y+3 \\ &= 2y(t) + 3 \end{align}$$
>>>and
>>>$$ \begin{align} a(t) &=2 \\ b(t) &= 3 \end{align}$$
>>
>>>[!example] Example 2 (First Order Linear ODE)
>>>$$ y' = -\frac{2}{t} y + 4t$$
>>>with the function 
>>>$$ \begin{align} f(t,y) &= -\frac{2y}{t} y + 4t \\ &= -\frac{2y(t)}{t} y + 4t \end{align}$$
>>>and
>>>$$ \begin{align} a(t) &=-\frac{2}{t} \\ b(t) &= 4t \end{align}$$
>>
>>>[!example] Example 3 (Nonlinear ODE)
>>>$$ y' = -\frac{2}{ty} +4t $$
>>>because $y$ is in the numerator and therefore not linear with respect to $f(t,y(t))$
>
>>[!example]- Examples (Tasks)
>>>[!example]- Task Show that $y(t) = e^{2t}-\frac{3}{2}$ is a solution for $y' = 2y+3$
>>>We have the ODE $y' = 2y + 3$. To verify the statement we first calculate the derivative of $y(t)$ which is
>>>$$\frac{dy}{dt}=y'=2e^{2t}$$
>>>Plugging these in, yields
>>>$$ \begin{align} 2e^{2t} &= 2\left(e^{2t} - \frac{3}{2}\right) + 3 \\
>>>&= 2e^{2t} -3 +3 \\
>>>&= 2e^{2t}\end{align}$$
>>
>>>[!example]- Task Find the differential equation $y' = f(y)$ satisfied by $y(t) = 4e^{2t} + 3$
>>>First we find the derivative of $y(t)$, i.e.
>>>$$\frac{dy}{dt}=y'=8e^{2t}$$
>>>Since $y(t)$ is the [[First Order ODEs#^deffirstorderODE|first order ODE]] it is of the form
>>>$$y' = a(t)y + b(t)$$
>>>We now rewrite $y(t)$ such that we yield $y'(t)$
>>>$$\begin{align}
>>>y &= 4e^{2t} +3 \\ 
>>>y - 3 &= 4e^{2t} \\
>>>2(y-3) &= 8e^{2t} \\
>>>2y-6&= y'
>>>\end{align}$$
>>>Hence we have
>>>$$ y' = a(t)y + b(t)$$
>>>with $a(t)=2$ and $b(t)=-6$ 

>[!theorem] Theorem Solutions of First Order ODEs with Constant Coefficients ([[../../../Sources/nagy.pdf#page=14|Source]])
> The linear differential equation 
> $$y'=ay+b \tag{1}$$
> with $a\neq0$, $b$ constants, has infinitely many solutions,
> $$y(t) = ce^{at}- \frac{b}a \tag{2}$$
> with $c \in \mathbb{R}$
>>[!note]-
>>1. equation $(2)$ is called the **general solution** of the differential equation $(1)$
>>2. the theorem states there are infinitely many solutions, one solution for each constant $c$
>>3. the constant $c$ is related to the vanishing constants in the first derivative, i.e. the integration constant $c$
>
>>[!proof]-
>> First, let's use the notation $y' = \dfrac{dy}{dt}$. Then we have
>> $$\begin{alignat}{2} 
>> \frac{dy}{dt} &= ay+b \qquad\qquad &&\Big|\cdot a^{-1} \\
>> \frac{1}{a}\frac{dy}{dt} &= y+\frac{b}{a} &&\Big| \cdot a\, dt\,\frac{1}{y+\frac{b}{a}} \\
>> \frac{1}{y+\frac{b}{a}} \,dy  &= a \, dt &&\Big| \int\\
>> \int \frac{1}{y+\frac{b}{a}} \,dy &= \int a \, dt \\
>> \ln\left(\left|y + \frac{b}{a}\right|\right) &= at + c_0 &&\Big|\;e^{(\,.\,)} \\
>> y +\frac{b}{a} &=e^{at+c_0} &&\Big|-\frac{b}{a} \\
>> y &=e^{at} \underbrace{e^{c_0}}_{=c} - \frac{b}{a} \\
>> y&=ce^{at} -\frac{b}{a} \tag*{$\square$}
>> \end{alignat}$$
>> with $c$ being the constant resulting from integration and $c = e^{c_0}$. Note, for integrating $\frac{1}{y + \frac{b}a}$ we use [[../Calculus/Differentiation Statements#^dernatlog| the derivative of the natural logarithm]]. Since the logarithm is not defined on negative values, we have to take the absolute value of the integrating term.
>> 
>
>>[!example]- Task Find all solutions to the constant coefficient equation $y'=2y+3$
>>$$\begin{align} \frac{dy}{dt} &= 2y + 3 \\ 
>>\frac{dy}{2dt} &= y + \frac{3}{2} \\
>>\frac{1}{y+\frac{3}{2}}\; dy&= 2\; dt \\
>>\int \frac{1}{y+\frac32} \; dy &= \int 2 \; dt \\
>>\ln\left(y+\frac32\right) &= 2t +c_0\\
>>y + \frac32&=e^{2t} e^{c_0}\\
>>y &= ce^{2t}-\frac32
>>\end{align}$$
>
>>[!proof]- Proof using Integrating Factor Method
>> First recall the product rule for derivatives, i.e. let $f(x) = f$, $\,u(x) = u$ be two functions, then
>> $$ \begin{align} \frac{d f \cdot u}{dx} &= \left(\frac{df}{dx}\right)u + \left(\frac{du}{dx}\right)f \\
>> &= f'u + fu'\end{align}$$
>> We introduce an **integrating factor** which is a function of $t$, i.e. $\mu(t)$. We want to choose $\mu(t)$ in a way, that for
>> $$ \begin{alignat}{2}
>> \frac{dy}{dt} &= ya +b \qquad \Big| -ya\\
>> \frac{dy}{dt} + (-a)y &= b 
>> \end{alignat}
>> $$
>> we can multiply the left-hand side by the integrating factor and yield the derivative of the product-rule, which is given by the right hand-side. Therefore, we are looking for $\mu(t)$ satisfying
>> $$
>> \begin{alignat}{1}
>> \left(\frac{dy}{dt}\right)\mu + (-a)y\mu &= \frac{d \mu y}{dt} \tag{3}
>> \end{alignat}$$
>> Note, we can consider $a,b$ to be functions of $t$, i.e. $a(t), b(t)$. 
>> To find $\mu(t)$ we use the product rule
>> $$\begin{align} 
>> 	\frac{d\mu y}{dt} &= \left(\frac{d \mu}{dt}\right) y +\left(\frac{dy}{dt}\right) \mu \tag{4}
>> \end{align} $$
>> Comparing $(3)$ and $(4)$ and setting them equal yields
>> $$\begin{alignat}{2}
>> 	\left(\frac{dy}{dt}\right)\mu + (-a)y\mu &= \left(\frac{d \mu}{dt}\right) y +\left(\frac{dy}{dt}\right) \mu \qquad && \Big|-\left(\frac{dy}{dt}\right) \mu \\
>> 	-ay\mu &= \left(\frac{d \mu}{dt}\right) y &&\Big| \cdot y^{-1}\\
>> 	-a\mu &=\frac{d \mu}{dt} &&\Big|\cdot dt, \cdot \mu^{-1} \\
>> 	-a\, dt &=\frac{d \mu}{\mu} &&\Big|\int \\
>> 	\int -a\, dt &= \int \frac{1}{\mu} \, d \mu \\
>> 	\int -a\, dt &=\ln|\mu| &&\Big|\;e^{( \, . \, )} \\
>> 	e^{\int -a\, dt} &=\mu 	\tag{5}
>> \end{alignat}$$
>> Thereby we found an expression for $\mu$ which is our **integrating factor**. Note, the constant of integration cancels out when we multiply with $\mu$ on both sides of our first order ODE.
>> $$\begin{alignat}{2} 
>> \frac{dy}{dt} &= ay + b \qquad&&\Big| -ay \\
>> \frac{dy}{dt} - ay &= b &&\Big| \cdot \mu \\
>> \frac{dy}{dt}\mu - ay \mu &= b\mu  &&\Big| \text{ inserting } \mu = e^{\int a\, dt}\\
>> \underbrace{\frac{d}{dt} ye^{\int -a\, dt}}_{=f'u} - \underbrace{ya e^{\int -a\, dt}}_{=fu'} &= b e^{\int -a\, dt}  &&\Big| \int (\, . )\,dt\\
>> \underbrace{\frac{d}{dt} ye^{\int -a\, dt}}_{=f'u} - \underbrace{ya e^{\int -a\, dt}}_{=fu'} &= b e^{\int -a\, dt}  &&\Big| \int (\, . )\,dt\\
>> \int \frac{d}{dt}\left[ye^{\int -a\, dt}\right] \, dt  &= \int b e^{\int -a\, dt}  \, dt\\
>> y e^{\int -a\, dt}  - c&= \int b e^{\int -a\, dt} \, dt  \qquad &&\Big| \;\cdot  + c \\
>> y e^{\int -a\, dt} &= c + \int b e^{\int -a\, dt} \, dt  \qquad &&\Big| \;\cdot  e^{-\int -a\, dt} \\
>> y&=ce^{\int a\, dt} + e^{\int a\, dt}  \int b e^{\int -a\, dt} \, dt \tag{6}
>> \end{alignat}$$
>> Assuming $a = a(t)$ and $b=b(t)$ are functions, then equation $(6)$ is the solution. Next we assume $a,b$ are constants again, then we have
>> $$ \begin{align} 
>> \int -a\, dt &= -ta + c\\
>> \int a\, dt &= ta + c\\
>> \int b e^{\int -a\, dt} \, dt &= \int b e^{-ta + c} \, dt \\
>> &= \frac{b}{a}e^{-ta + c} + c
>> \end{align}$$
>> Setting the constant of the integration $c_0=0$, we have
>> $$\begin{align} y&=ce^{\int a\, dt} + e^{\int a\, dt}  \int b e^{\int -a\, dt} \, dt  \\
>>  &=c_1e^{ta + c_0} + e^{ta + c_0}  \left(-\frac{b}{a}e^{-ta+c_0}+c_1\right)  \\
>>  &=c_1e^{ta + c_0} -\frac{b}{a}e^{2c_0}+ c_1e^{ta + c_0}  \\
>>  &=2c_1e^{ta + c_0} -\frac{b}{a}e^{2c_0} \\
>>  &=ce^{ta} -\frac{b}{a} \tag*{$\square$}\\
>> \end{align}$$
>
>>[!Example]- Task Find all solutions to the constant coefficient equation $y'=2y+3$
>>Let $\mu = e^{\int -2 \, dt} = e^{-2t}$
>>$$\begin{alignat}{2} 
>> \frac{dy}{dt} &= 2y + 3 \qquad &&\Big|-2y \\
>> \frac{dy}{dt} - 2y &= 3  &&\Big| \cdot \mu \\
>> \frac{d}{dt}y e^{-2t} - 2y e^{-2t} &= 3 e^{-2t}  &&\Big| \int ( \, . ) \,dt\\
>> \int \frac{d}{dt} \left[ye^{-2t}\right] \, dt &= \int 3 e^{-2t} \, dt  \\
>> ye^{-2t} + c_0&=  -\frac{3}{2} e^{-2t} +c_1 \qquad &&\Big|-c_0 \\
>> ye^{-2t} &=  -\frac{3}{2} e^{-2t} +c \qquad &&\Big| \cdot e^{2t} \\
>> y &=  -\frac{3}{2} +ce^{2t}
>>\end{alignat}$$
>>
>
>^thmsolvefoode

<br>

## 2 - Initial Value Problem

>[!def] Definition Initial Value Problem ([[../../../Sources/nagy.pdf#page=18|Source]])
> The initial value problem (IVP) is to find all solutions $y$ to 
> $$ y' = ay+b $$
> that satisfy the initial condition 
> $$ y(t_0) = y_0 \tag{Initial Condition}$$
> where $a,b,t_0, y_0$ are given constants.
>>[!note]
>>The differential equation has a unique solution with respect to the initial condition.
>

>[!theorem] Theorem Solutions of IVPs  ([[../../../Sources/nagy.pdf#page=18|Source]])
> Given the constants $a,b,t_0,y_0 \in \mathbb{R}$, with $a \neq 0$, the initial value problem 
> $$ y' = ay + b, \qquad  y(t_0) = y_0,$$
> has the unique solution
> $$ y(t) = \left(y_0 + \frac{b}{a}\right)e^{a(t-t_0)} - \frac{b}{a}$$
>>[!proof]-
>>First we use the results of the [[First Order ODEs#^thmsolvefoode|Theorem for solveability of first order ODEs]], i.e.
>> $$y(t) = ce^{at} - \frac{b}a$$
>> and solve $y_0 = y(t_0)$ for $c$
>> $$\begin{align}
>> 	y_0 &= ce^{at_0} -\frac{b}{a} \\
>> 	y_0 + \frac{b}{a} &= ce^{at_0} \\
>> 	\left(y_0 + \frac{b}{a}\right)e^{-at_0} &= c \\
>> \end{align}$$
>> Using this result for the integration constant yields
>> $$\begin{align}
>> y(t)&=ce^{at} - \frac{b}a \\
>> &= \left(y_0 + \frac{b}{a}\right)e^{-at_0}e^{at} - \frac{b}a \\
>> &= \left(y_0 + \frac{b}{a}\right)e^{a(t-t_0)} - \frac{b}a \tag*{$\square$}
>>\end{align}$$
>^thmsolivp
>
>>[!example]- Task Find the unique solution of the initial value problem $y'=2y + 3$ with $y(0) = 1$
>>Solutions for $y$ can be given as 
>>$$ \begin{align}
>>y=ce^{2t} - \frac{3}{2} \tag{1}
>>\end{align}$$
>>Determining the value for the integrating constant $c$ gives
>>$$\begin{align} 
>>y(0)&= ce^{0}-\frac32 \\
>>1 &= c - \frac32 \\
>>c &= \frac52
>>\end{align}$$
>>Inserting the result into $(1)$ gives
>>$$\begin{equation}y = \frac52 e^{2t}-\frac32\end{equation}$$
>
>>[!example]- Task Find the unique solution of the initial value problem $y'=-3y + 1$ with $y(0) = 1$
>>Solutions for $y$ can be given as 
>>$$ \begin{align}
>>y=ce^{-3t} - \frac{1}{3} \tag{1}
>>\end{align}$$
>>Determining the value for the integrating constant $c$ gives
>>$$\begin{align} 
>>y(0)&= ce^{0}-\frac13 \\
>>1 &= c - \frac13 \\
>>c &= \frac23
>>\end{align}$$
>>Inserting the result into $(1)$ gives
>>$$ y=\frac23e^{-3t} + \frac13$$

>[!example]- Exercises
>>[!example]- Task Find the differential equation of the form $y' = f(y)$ satisfied by the function $y(t) = 8e^{5t} - \frac25$
>>$$\begin{align} y(t) &= 8e^{5t} - \frac25 \\
>>\frac{dy}{dt} = y' &= 40e^{5t} 
>>\end{align}$$
>>Inserting this result in the standard form gives
>>$$\begin{alignat}{2}
>>y'&=ay+b \\
>>40e^{5t} &= a(8e^5t - \frac25) + b \qquad &&\Big|\text{ clearly } a=5  \\ 
>>40e^{5t} &= 40e^5t - \frac{10}5 + b \qquad &&\Big|\text{ clearly } b=2  \\
>>40e^{5t} &= 40e^{5t}
>>\end{alignat}$$
>>Hence the solution is
>>$$ y' = 5y + 2$$
>
>
>>[!example]- Task Find all solutions of $y$ of $y' = 3y$
>> We identify $a=3$ and $b=0$. Using theorem [[First Order ODEs#^thmsolvefoode|Theorem for ODE solving]] we have
>> $$ y =  ce^{3t} $$
>
>>[!example] Task Follow the steps below to find all solutions of $y' = -4y + 2$
>>1. Find the integrating factor $\mu$
>>2. Write the equations as a total derivative of a function $\psi$, that is $y'=-4y+2 \Leftrightarrow \psi'=0$
>>3. Integrate the equation for $\psi$
>>4. Compute $y$ using part (3)
>>>[!example]- Solution
>>>Following the procedure from the proof using the [[First Order ODEs#^thmsolvefoode| integrating factors method]].
>>>1. First, we put the equation into the form, that we can compare it to the product rule. Let $\mu(t) = \mu$ denote the integrating factor
>>> $$\begin{align}
>>> 	\frac{dy}{dt} &= -4y +2\\
>>> 	\frac{dy}{dt} +4y &= 2\\
>>> 	\left(\frac{dy}{dt}\right)\mu +4y\mu &= 2\mu \tag{1}\\
>>> \end{align}$$
>>> Recall the product rule
>>> $$\begin{align}
>>> \frac{d}{dt}\left[y\mu\right] = \left(\frac{dy}{dt}\right)\mu + \left(\frac{d\mu}{dt}\right)y \tag{2}
>>> \end{align}$$
>>> We want to choose $\mu$ such that the right hand-side of $(1)$ is giving the product rule, i.e. $(2)$. Therefor, we set $(1)$ LHS $=(2)$ RHS
>>>  $$\begin{alignat}{2}
>>> \left(\frac{dy}{dt}\right)\mu +4y\mu &= \left(\frac{dy}{dt}\right)\mu + \left(\frac{d\mu}{dt}\right)y  \qquad &&\Big| - \left(\frac{dy}{dt}\right)\mu \\
>>> 4y\mu &= \left(\frac{d\mu}{dt}\right)y   &&\Big| :y \\
>>> 4\mu &= \frac{d\mu}{dt}   
>>> \end{alignat}$$
>>> This can easily be solved for $a=4, b=0$ with $\mu = ce^{4t} = e^{4t}$ where we choose for convenience $c=1$. Therefore, we yield the following equation from (1) and the found expression for $\mu$
>>> $$ \begin{align} 
>>> \left(\frac{dy}{dt}\right)e^{4t} +4ye^{4t} &= 2e^{4t} \\
>>> \frac{d}{dt} \left[e^{4t}y\right] &=2e^{4t} \tag{3}
>>> \end{align}$$
>>> 2. To find the expression for the total derivative, we first put the right hand-side in an equivalent derivative form and rearrange to get $\psi(y,t)=0$. First we assert
>>> $$ \frac{d}{dt} \frac{1}{2}e^{4t} = 2e^{4t}$$
>>> Substituting this result in $(3)$, rearranging gives
>>> $$ \begin{alignat}{2} 
>>> \frac{d}{dt} \left[e^{4t}y\right] &=\frac{d}{dt} \frac{1}{2}e^{4t} \qquad&&\Big| - \frac{d}{dt} \frac{1}{2}e^{4t}  \\
>>> \frac{d}{dt} \left[e^{4t}y-\frac{1}{2}e^{4t}\right] &=0 \\
>>> \end{alignat}
>>> $$
>>> 3. Integrating gives
>>> $$ \begin{alignat}{2}
>>> \frac{d}{dt} \left[y-\frac{1}{2}\right]e^{4t} &=0 \qquad&&\Big|\int \\
>>> \left[y-\frac{1}{2}\right]e^{4t} &=c 
>>> \end{alignat}$$
>>> 4. Computing $y$ gives
>>>  $$ \begin{alignat}{2}
>>> \left[y-\frac{1}{2}\right]e^{4t} &=c \qquad\qquad\qquad&&\Big| \cdot e^{-4t},\; +\frac12 \\
>>> y &= ce^{-4t}+\frac12
>>> \end{alignat}$$
>
>>[!example]- Task Find all solutions of $y'=2y+5$
>> We identify $a=2$ and $b=5$. Using theorem [[First Order ODEs#^thmsolvefoode|Theorem for ODE solving]] we have
>> $$ y =  ce^{2t} -\frac52 $$
>
>>[!example]- Task Find all solutions of the IVP $y'=-4y+2$, $y(0)=5$
>> Using the [[First Order ODEs#^thmsolivp|Theorem for solving IVP with constant coefficients]] we can identify 
>> $$\begin{align} 
>>  t_0 &= 0 \\
>>  y_0 &= 5 \\
>>  a &= -4 \\
>>  b &= 2 \\
>> \end{align}$$
>> Hence, we have
>>$$\begin{align} 
>> y(t) &= \left(5+ \frac{2}{-4}\right) e^{-4t} - \frac{2}{-4} \\
>> y(t) &= \frac{9}{2} e^{-4t}+ \frac{1}{2} \\
>>\end{align}$$
>
>>[!example]- Task Find the solution of the IVP $\frac{dy}{dt}(t)=3y(t)-2$, $y(1)=1$
>> Using the [[First Order ODEs#^thmsolivp|Theorem for solving IVP with constant coefficients]] we can identify 
>> $$\begin{align} 
>>  t_0 &= 1 \\
>>  y_0 &= 1 \\
>>  a &= 3 \\
>>  b &= -2 \\
>> \end{align}$$
>> Hence, we have
>>$$\begin{align} 
>> y(t) &= \left(1+ \frac{-2}{3}\right) e^{3t-3} - \frac{-2}{3} \\
>> y(t) &= \frac{1}{3} e^{3t-3} + \frac{2}{3} \\
>>\end{align}$$
>
>>[!example] Task
>>Express the differential equation $y'=6y+1$ as a total derivative of a potential function $\psi(t,y)$, that is, find $\psi$ satisfying 
>>$$ y'=6y+1 \Leftrightarrow \psi'=0$$
>>Integrate the equation for the potential function $\psi$ to find all solutions of $y$.
>>>[!example]- Solution
>>>We first determine the integrating factor $\mu(t)$ to apply the product rule. 
>>>$$\begin{align} 
>>>\frac{dy}{dt} - 6y &= 1 \\
>>>\frac{dy}{dt} \mu - 6y\mu &= \mu \tag{1}
>>>\end{align}$$
>>> Settings the LHS equal to the product rule
>>> $$\begin{align} 
>>>\frac{dy}{dt}\mu - 6y\mu &= \left(\frac{d\mu}{dt}\right)y + \left(\frac{dy}{dt}\right)\mu\\
>>> - 6\mu y &= \left(\frac{d\mu}{dt}\right)y\\
>>> - 6\mu &= \frac{d\mu}{dt} \\
>>>\end{align}$$
>>>According to the [[First Order ODEs#^thmsolvefoode| theorem for solving this]], we get the following result 
>>>$$\mu = e^{-6t}$$
>>> Further we determine the potential function by inserting $\mu$ into $(1)$. Recall, the LHS is constructed to be the product-rule.
>>> $$ \begin{align}
>>> 	\frac{dy}{dt} e^{-6t} - 6y e^{-6t} &= e^{-6t} \\
>>> 	\frac{d}{dt} \left[ye^{-6t}\right]  &= e^{-6t} \\
>>> 	\frac{d}{dt} \left[ye^{-6t}\right]  &= \frac{d}{dt} \frac{1}{-6}e^{-6t} \\
>>> 	\frac{d}{dt} \left[ye^{-6t} + \frac{1}{6}e^{-6t}\right]  &= 0  \\
>>> \end{align}
>>> $$
>>> Hence, we have found the potential function $\psi(y,t) = ye^{-6t} + \frac{1}{6}e^{-6t}$. Integrating yields a solution for $y$.
>>> $$ \begin{align}
>>> 	\frac{d}{dt} \left[ye^{-6t} + \frac{1}{6}e^{-6t}\right]  &= 0 \\
>>> 	ye^{-6t} + \frac{1}{6}e^{-6t} &= c \\
>>> 	\left(y + \frac{1}{6}\right)e^{-6t} &= c \\
>>> 	y + \frac{1}{6} &= ce^{6t} \\
>>> 	y  &= ce^{6t} - \frac{1}{6} \\
>>> \end{align}
>>> $$
>
>>[!example]- Task Find the solution of the IVP $y'=6y+1$, $y(0) = 1$
>> $$\begin{align} 
>>  t_0 &= 0 \\
>>  y_0 &= 1 \\
>>  a &= -6 \\
>>  b &= 1 \\
>> \end{align}$$
>> Hence, we have
>>$$\begin{align} 
>> y(t) &= \left(1+ \frac{1}{6}\right) e^{6t} - \frac{1}{6} \\
>> y(t) &= \frac{7}{6} e^{6t}- \frac{1}{6} \\
>>\end{align}$$
>
>>[!example] Task Follow the steps below to find all solutions of $y'=-3y+5$, $y(0)=1$
>>1. Find an integrating factor $\mu$ for the differential equation.
>>2. Write the differential equation as a total derivative of a potential function $\psi$.
>>3. Use the potential function to find the general solution of the differential equation
>>4. Find the solution of the initial value problem above.
>>>[!example]- Solution
>>>1. We first determine the integrating factor $\mu(t)$ to apply the product rule. 
>>>$$\begin{align} 
>>>\frac{dy}{dt} + 3y &= 5 \\
>>>\frac{dy}{dt} \mu + 3y\mu &= 5\mu \tag{1}
>>>\end{align}$$
>>> Settings the LHS equal to the product rule
>>> 
>>> $$\begin{align} 
>>>\frac{dy}{dt}\mu + 3y\mu &= \left(\frac{d\mu}{dt}\right)y + \left(\frac{dy}{dt}\right)\mu\\
>>> 3\mu y &= \left(\frac{d\mu}{dt}\right)y\\
>>> 3\mu &= \frac{d\mu}{dt} \\
>>>\end{align}$$
>>>According to the [[First Order ODEs#^thmsolvefoode| theorem for solving this]], we get the following result 
>>>$$\mu = e^{3t}$$
>>>
>>>2. Further, we determine the potential function by inserting $\mu$ into $(1)$. Recall, the LHS is constructed to be the product-rule.
>>> $$ \begin{align}
>>> 	\frac{dy}{dt} e^{3t} + 3y e^{3t} &= 5e^{3t} \\
>>> 	\frac{d}{dt} \left[ye^{3t}\right]  &= 5e^{3t} \\
>>> 	\frac{d}{dt} \left[ye^{3t}\right]  &= \frac{d}{dt} \frac{5}{3}e^{3t} \\
>>> 	\frac{d}{dt} \left[ye^{3t} - \frac{5}{3}e^{3t}\right]  &= 0  \\
>>> \end{align}
>>> $$
>>> Hence, we have found the potential function $\psi(y,t) = ye^{3t} - \frac{5}{3}e^{3t}$. 
>>> 3. Integrating yields a solution for $y$.
>>> $$ \begin{align}
>>> 	\frac{d}{dt} \left[ye^{3t} - \frac{5}{3}e^{3t}\right]  &= 0 \\
>>> 	ye^{3t} - \frac{5}{3}e^{3t} &= c \\
>>> 	\left(y - \frac{5}{3}\right)e^{3t} &= c \\
>>> 	y - \frac{5}{3} &= ce^{-3t} \\
>>> 	y  &= ce^{-3t} + \frac{5}{3} \tag{2}\\
>>> \end{align}
>>> $$
>>> 4.  Solving for $c$ with $t=0$ and $y(0) = 1$ yields
>>> $$ \begin{align} 
>>> y(0)  &= ce^{0} + \frac{5}{3} \\
>>> 1  &= c + \frac{5}{3} \\
>>> -\frac{2}{3}  &= c \\
>>> \end{align}$$
>>> Inserting this into $(2)$ gives the solution for the IVP, hence we have
>>> $$ y(t) = -\frac{2}{3}e^{-3t} + \frac{5}{3}$$

<br>

## 3 - Linear Variable Coefficient Equations

>[!theorem] Theorem Solutions to First Order ODEs with Variable Coefficients ([[../../../Sources/nagy.pdf#page=23|Source]])
>If the functions $a,b$ are continuous, then
>$$ y' = a(t)y + b(t)$$
>has infinitely many solutions given by
>$$ \begin{equation}y(t) = ce^{A(t)}+e^{A(t)} \int e^{-A(t)} b(t) \, dt \tag{General Solution}\end{equation}$$
>where $A(t) = \int a(t) \, dt$ being the **integrating factor** and $c \in \mathbb{R}$
>>[!proof] Proof: See [[First Order ODEs#^thmsolvefoode| Proof for constant coefficients Integrating Factor Method]]
>
>>[!example]- Task Find all solutions $y$ for the differential equation $y'=\frac3ty+t^5$ with $t>0$
>>First compute $\mu(t)$ following the form of the product rule as previously already shown. Note, that the parameters $a,b$ are functions of $t$, i.e. $a(t) = \frac3t$ and $b(t) = t^5$.
>>$$\begin{alignat}{2} 
>>\frac{dy}{dt} &= \frac3ty + t^5 \qquad &&\Big|-\frac3ty \\
>>\frac{dy}{dt} -\frac3ty  &= t^5 \qquad &&\Big|\cdot \mu \\
>>\left(\frac{dy}{dt}\right)\mu -\frac3ty\mu  &= t^5\mu  \tag{1} \\
>>\end{alignat}$$
>>Setting the LHS of $(1)$ equal to the product rule, yields
>>$$\begin{alignat}{2} 
>>\left(\frac{dy}{dt}\right)\mu -\frac3ty\mu  &= \left(\frac{dy}{dt}\right)\mu + \left(\frac{d\mu}{dt}\right)y \qquad &&\Big|-\left(\frac{dy}{dt}\right)\mu, \;\cdot y^{-1}   \\
>>-\frac3t\mu  &= \frac{d}{dt}\mu \qquad &&\Big|\cdot \mu^{-1}\ \cdot dt \\
>>-\frac3t dt  &= \frac{1}{\mu} d\mu \qquad &&\Big|\int(\,. )\, dt\\
>>\int-\frac3t dt  &= \int \frac{1}{\mu} d\mu\qquad \\
>>-3 \ln |t| + c_0 &= \ln|\mu| \qquad &&\Big|e^{(\,.\,)}\\
>>e^{\ln |t|^{-3}}(\pm e^{c_0}) &= \mu &&\Big|\text{ choosing } c_0 = 0\\
>>\pm t^{-3}  &= \mu \\
>>\end{alignat}$$
>>Now we can apply the product rule for $(1)$ and then insert the result for $\mu$ found in $(2)$
>>$$\begin{alignat}{2} 
>>\left(\frac{dy}{dt}\right)\mu -\frac3ty\mu  &= t^5\mu \qquad  \\
>>\frac{d}{dt}\left[\mu y\right]  &= t^5\mu \qquad &&\Big|-t^5\mu\\ 
>>\frac{d}{dt}\left[t^{-3} y\right]  -t^5t^{-3}&= 0 \qquad &&\Big|\;\mu = t^{-3} \\ 
>>\frac{d}{dt}\left[t^{-3} y\right]  -t^2&= 0 \qquad &&\Big|\int(\,.)\, dt \\ 
>>t^{-3}y + c_0  - \int t^2&= c_1 \qquad &&\\ 
>>t^{-3}y + c_0  - \left(\frac13 t^3 + c_2\right) &= c_1 \qquad &&\Big|c_0 - c_2 = c_3\\ 
>>t^{-3}y   &= c + \frac13 t^3 \qquad &&\Big| \cdot t^{3}\\ 
>>y   &= ct^{3} + \frac13 t^6 \qquad &&\\ 
>>\end{alignat}$$
>
>>[!example]- Task Find all solutions $y$ for the differential equation $ty'=-2y+4t^2$ with $t>0$
>>First we determine the **integration factor** $\mu(t)$ by identifying it over the product rule
>>$$\begin{alignat}{2}
>>	t\frac{dy}{dt} &= -2y + 4t^2 \qquad &&\Big|\cdot t^{-1} \\ 
>>	\frac{dy}{dt} &= -\frac2t y + 4t \qquad &&\Big|+\frac2t y \\ 
>>	\frac{dy}{dt} +\frac2t y &=  4t \qquad &&\Big|\cdot \mu \\ 
>>	\frac{dy}{dt} \mu +\frac2t y \mu &=  4t\mu \tag{1}\\ 
>>\end{alignat}$$
>>Now we use the LHS on the product rule
>>$$\begin{alignat}{2}
>>	\frac{dy}{dt} \mu +\frac2t y \mu &= \left(\frac{dy}{dt}\right)\mu + \left(\frac{d\mu}{dt}\right)y \qquad &&\Big|-\left(\frac{dy}{dt}\right)\mu, \;\cdot y^{-1}   \\ \\ 
>>	\frac2t \mu &=\frac{d\mu}{dt} \qquad &&\Big|\cdot dt, \; \cdot \mu^{-1} \\ 
>>	\frac2t dt &= \frac{1}{\mu} d\mu   \qquad &&\Big|\int(\,.)\, dt \ \\ 
>>	2\ln |t| +c_0&= \ln|\mu| +c_1   \qquad &&\Big|c_0 - c_1 = c_3 \\ 
>>	\ln t^2 +c_3&= \ln|\mu|   \qquad &&\Big|e^{(\,.\,)} \\ 
>>	t^2 e^{c_3}&= \mu   \qquad &&\Big| \text{ choosing } c_3 = 0 \\ 
>>	\pm t^2 &= \mu   \\ 
>>\end{alignat}$$
>>Using this result in $(1)$ gives
>>$$\begin{alignat}{2} 
>>	\frac{dy}{dt} \mu +\frac2t y \mu &=  4t\mu \\ 
>>	\frac{d}{dt} \left[ \mu y\right] &= 4t\mu \qquad &&\Big|\;\mu = t^2\\
>>	\frac{d}{dt} \left[ t^2 y\right] &= 4t^3 \\ 
>>	\frac{d}{dt} \left[ t^2 y\right] &= \frac{d}{dt} \left[t^4\right] \qquad &&\Big| - \frac{d}{dt} \left[t^4\right]\\ 
>>	\frac{d}{dt} \left[ t^2y -t^4\right] &= 0 \qquad &&\Big| \int (\, . ) \;dt\\ 
>>	t^2y -t^4 &= c \qquad &&\Big| +t^4\\ 
>>	t^2y &= c + t^4 \qquad &&\Big| \cdot ta^{-2}\\ 
>>	y &= ct^{-2} + t^2 \\ 
>>\end{alignat}$$
>^defThmSolODEVar

>[!def] Definition Initial Value Problem for Variable Coefficients ([[../../../Sources/nagy.pdf#page=25|Source]])
>The **initial value problem (IVP)** is to find all solutions $y$ of
>$$ y' = a(t) y + b(t)$$
>that satisfy the initial condition
>$$\begin{equation} y(t_0) = y_0 \tag{Initial Condition}\end{equation}$$
>where $a,b$ are given functions and $t_0, y_0$ are given constants.
>>[!note]
>>The IVP has a unique solution.
>^defIVPvar

>[!theorem] Theorem Solutions of IVP with Variable Coefficients ([[../../../Sources/nagy.pdf#page=26|Source]])
> Given continuous functions $a,b$ with domain $(t_1, t_2)$ and constants $t_0 \in (t_1, t_2)$ and $y_0 \in \mathbb{R}$, the IVP
> $$ y' = a(t)y + b(t), \qquad y(t_0) = y_0 $$
> has the unique solution $y$ on the domain $(t_1, t_2)$, given by
> $$ y(t) = y_0e^{A(t)} + e^{A(t)}\int_{t_0}^t e^{-A(s)}b(s) \, ds$$
> where the function $A(t) = \int_{t_0}^t a(s) \, ds$ is a particular antiderivative of function $a$.
>>[!proof]-
>> First we use the results of the [[First Order ODEs#^defThmSolODEVar| Theorem Solving First Order ODEs with Variable Coefficients]]. 
>> $$ \begin{equation}y(t) = ce^{A(t)}+e^{A(t)} \int e^{-A(t)} b(t) \, dt \tag{1}\end{equation}$$
>>where $A(t) = \int a(t) \, dt$. Setting 
>>$$\begin{align} y(t_0) &= y_0 \\ K(t) &= \int e^{-A(t)} b(t) \, dt \end{align}$$ 
>>and rearranging for $c$ gives
>>$$\begin{alignat}{2}
>>  y_0 &= ce^{A(t_0)} + e^{A(t_0)} K(t_0) &&\qquad \Big\vert -e^{A(t_0)} K(t_0)\\
>>   y_0 - e^{A(t_0)} K(t_0) &= ce^{A(t_0)}  &&\qquad \Big\vert \cdot e^{-A(t_0)}\\
>>   y_0e^{-A(t_0)} -  K(t_0) &= c  &&\qquad 
>>\end{alignat} $$
>>Substituting $c$ this back into $(1)$ gives
>>$$\begin{alignat}{2}
>>  y(t) &= \left(y_0e^{-A(t_0)} -  K(t_0)\right)e^{A(t)}+e^{A(t)} K(t) \\
>>  &= y_0e^{A(t)-A(t_0)} - e^{A(t)}K(t_0) +e^{A(t)} K(t) \\
>>  &= y_0e^{A(t)-A(t_0)} + e^{A(t)}\left(K(t) - K(t_0)\right) \tag{2}\\
>>\end{alignat} $$
>>Further, we notice $A(t_0) = \int_{t_0}^{t_0}a(s) \,ds$ is vanishing due to its integration limits. Therefore, we define 
>>$$\begin{align}
>> \widehat{A}(t) &= A(t) - \underbrace{A(t_0)}_{=0} \\
>> &= A(t) \tag{3}
>>\end{align}$$
>>Next, we specify $K(t)$. Since we are interested in finding an **initial value**, we have to turn the indefinite integral in $K(t)$ in to a definite one. Since we are inspecting the initial value of $t_0$ with respect to $t$, we define the integral on the range of $[t_0, t]$, hence, we have
>>$$\begin{align}
>>\widehat{K}(t) &= K_{t_0}^{t}(t) - K_{t_0}^{t_0}(t) \\
>>&= K_{t_0}^{t}(t) - K_{t_0}^{t_0}(t) \\
>>&=  \int_{t_0}^t e^{-A(t)} b(t) - \underbrace{\int_{t_0}^{t_0} e^{-A(t)} b(t)}_{=0} \\
>>&= \int_{t_0}^t e^{-A(t)} b(t) \tag{4}
>>\end{align}$$
>> We insert the findings of $(3)$ and $(4)$ into $(2)$. Further notice, we can add $A(t_0)=0$ as we need
>> $$\begin{align}
>> y_0e^{A(t)-A(t_0)} + e^{A(t)}\left(K(t) - K(t_0)\right) &= y_0e^{\widehat{A}(t)} +  e^{A(t)} \int_{t_0}^t e^{-A(t)} b(t) \\
>>  &= y_0e^{\widehat{A}(t)} +  e^{A(t) - A(t_0)} \int_{t_0}^t e^{-(A(t) - A(t_0))} b(t) \\
>>  &= y_0e^{\widehat{A}(t)} +  e^{\widehat{A}(t)} \int_{t_0}^t e^{-\widehat{A}(t)} b(t) \\
>>\end{align}$$
>>Changing the naming of $\widehat{A}(t)$ to $A(t)$ yields the theorem to be proven, i.e.
>>$$ y(t) = y_0e^{A(t)} + e^{A(t)}\int_{t_0}^t e^{-A(s)}b(s) \, ds$$
>> 
>
>>[!example]- Task Find the function $y$ solution of the IVP $ty' + 2y = 4t^2$ with $t>0$ and $y(1) = 2$
>>We use the result of the [[First Order ODEs#^thmsolivp| theorem solution for IVP with variable coefficients]]. First we rearrange the formula
>>$$\begin{align}
>>ty' +2y &= 4t^2 \qquad \Big\vert-2y, \; \cdot t^{-1} \\
>>y' &= -\frac{2}{t}y + 4t \qquad \\
>>\end{align}$$
>>Next we specify the terms of the formula with respect to the given parameters
>>$$\begin{align} 
>>A(t) &=  \int_{t_0}^{t}a(s) \,ds  \\
>>     &=  \int_{1}^{t}-\frac{2}s \,ds \\ 
>>     &=  -2\int_{1}^{t}\frac{1}s \,ds \\ 
>>     &=  -2\Bigg( \ln |s|\Bigg\vert^t_{1}\Bigg) \,\\ 
>>     &=  -2\Bigg( \ln |t| - \underbrace{\ln 1}_{=0}\Bigg) \\ 
>>     &=  -2\ln |t|  \\ 
>>     &=  \ln |t|^{-2}  \\
>> 				    \\
>>      \int_{t_0}^t e^{-A(s)}b(s) \, ds &= \int_{1}^t e^{-\ln s^{-2}} 4s \, ds \\
>> 								      &= \int_{1}^t e^{\ln s^{2}} 4s \, ds \\
>> 								      &= \int_{1}^t s^{2} 4s \, ds \\ 
>> 								      &= \int_{1}^t 4s^3 \, ds \\ 
>> 								      &= s^4 \Bigg\vert_1^t  \\ 
>> 								      &= t^4 - 1 \\ 
>>\end{align}$$
>>Now we insert the results into the formula
>>$$\begin{align}
>>	y(t) &= y_0e^{A(t)} + e^{A(t)}\int_{t_0}^t e^{-A(s)}b(s) \, ds \\
>>	&= 2e^{\ln |t|^{-2}} + e^{\ln |t|^{-2}}\left(t^4 - 1 \right) \\
>>	&= 2t^{-2} + t^{-2}\left(t^4 - 1 \right) \\
>>	&= 2t^{-2} + t^{2} - t^{-2}\\
>>	&= \frac{1}{t^2} + t^{2} \\
>>\end{align}$$
>
>^thmsolIVPvar
>


>[!remark]- Remark Recovering Constant Coefficient Form
> We can get the [[First Order ODEs#^thmsolivp|constant coefficient form]] back by assuming $a(t), b(t)$ being constant. First, we reduce $A(t)$ to be constant with
> $$
> \begin{align}
> 	A(t) &= \int_{t_0}^t a \, ds \\
> 	     &=  sa \; \Bigg\vert_{t_0}^t \\
> 	     &=  ta - t_0a  \\
> 	     &=  a(t - t_0)  \\
> \end{align}
> $$
> Next we insert this result into the solution equation
> $$ 
> \begin{align} 
> 	y(t) &= y_0e^{A(t)} + e^{A(t)}\int_{t_0}^t e^{-A(s)}b(s) \; ds \\
> 	     &= y_0e^{a(t - t_0)} + e^{a(t - t_0)}\int_{t_0}^t e^{-a(t - t_0)}b \; ds \tag{1}\\
> \end{align}
> $$
> Now we solve the definite integral using the [[../Calculus/Integration#^thmSubstitutionRuleDef|substitution method]]. We identify the form of the given definition in the substitution method and apply the method
> $$
> \begin{align}
> 	\int_{t_0}^t e^{-a(s-t_0)}b \; ds &= \int_a^b f\Big(g(s)\Big)g'(s) \,ds \\
> 	g(s) &=  s-t_0 \\
> 	g'(s) &= 1 \\
> 	f(g(s)) &= e^{-ag(s)}b\\  
> 	&= e^{-a(s-t_0)}b \\
> 	g(a)=g(t_0)&= t_0-t_0 \\
> 	&= 0 \\
> 	g(b) =g(t) &=t - t_0
> \end{align}
> $$
> Which captures the inner form of the integral. Applying the method with $g(s) = u= s-t_0$ yields
> $$\begin{align}
>	\int_a^b f(g(x))g'(x) \;dx &= \int_{g(a)}^{g(b)}f(u) \; du \tag{Substitution Rule} \\
>	\int_{t_0}^t e^{-a(t - t_0)}b\; ds &= \int_{0}^{t - t_0} e^{-au}b \; du \tag{Applying the Rule} \\
>									  &= b \int_{0}^{t - t_0} e^{-au} \; du  \\
>									  &= b \Bigg(-\frac{1}{a}e^{-au} \Bigg\vert_{0}^{t - t_0}\Bigg)   \\
>									  &= b \Bigg(-\frac{1}{a}e^{-a(t - t_0)} - \left(-\frac{1}{a}e^{0}\right) \Bigg)   \\
>									  &= -\frac{b}{a}e^{-a(t - t_0)} + \frac{b}{a}     \\
>\end{align}$$
>Inserting this result into $(1)$ gives 
>$$ \begin{align}
>	y_0e^{a(t - t_0)} + e^{a(t - t_0)}\left(-\frac{b}{a}e^{-a(t - t_0)} + \frac{b}{a}\right)  &=y_0e^{a(t - t_0)} - \frac{b}{a}e^0 + e^{a(t - t_0)}\frac{b}{a} \\
>	&=\left(y_0 + \frac{b}{a}\right)e^{a(t - t_0)} - \frac{b}{a} \tag*{$\square$}
>\end{align}$$
>which concludes this remark.

## 3.1 - The Bernoulli Equation

>[!def] Definition Bernoulli Equation ([[../../../Sources/nagy.pdf#page=27|Source]])
>The **Bernoulli equation** is
>$$\begin{align} 
>y' = p(t)y + q(t)y^n
>\end{align}$$
>where $p,q$ are given functions and $n \in \mathbb{R}$.
>^defBernoulli

>[!remark]- Remark Regarding $n$ in the Bernoulli equation
> - $n \neq 0, 1$ => Bernoulli equation is **non-linear**
> - $n = 2$ => Bernoulli equation is **logistic equation**

>[!theorem] Theorem Solutions for the Bernoulli equation  ([[../../../Sources/nagy.pdf#page=26|Source]])
>The function $y$ is a solution of the Bernoulli equation iff the function 
>$$ \nu = \frac{1}{y^{n-1}}$$
>is solution of the linear differential equation
>$$ \nu' = -(n-1)p(t)\nu - (n-1)q(t)$$
>>[!note]-
>>The non-linear representation of the Bernoulli equation is linearized in its representation, such that it can be solved using methods of linear ODEs.
>
>>[!proof]-
>>We take the Bernoulli equation and divide by $y^n$
>>$$\begin{align} 
>>	y' &= p(t)y + q(t)y^n \\
>>	\frac{y'}{y^n} &= \frac{p(t)}{y^{n-1}} + q(t) \tag{1}\\
>>\end{align}$$
>>Now we set $\nu = y^{-(n-1)} \;(2)$ and determine $\nu'=\frac{d\nu}{dt}$
>>$$\begin{align}
>>	\frac{d\nu}{dt} &= \frac{d}{dt} \left(y^{-(n-1)} \right) \\
>>					&= -(n-1)y^{-n} \frac{dy}{dt} \tag{chain rule}
>>\end{align}$$
>>We continue to rearrange to have the expression of the LHS of $(1)$
>>$$\begin{align} 
>>\nu' &=-(n-1)y^{-n}y' \qquad\Big|: (-(n-1)) \\
>>\frac{\nu'}{-(n-1)} &=\frac{y'}{y^{n}} \qquad\Big|: (-(n-1)) \tag{3}\\
>>\end{align}$$
>>
>>Now we set the LHS $(1)$ = RHS $(3)$ with  $\nu = y^{-(n-1)}$ from $(2)$
>>$$\begin{alignat}{2}
>>\frac{\nu'}{-(n-1)}&= p(t)\nu + q(t) \qquad &&\Big|\cdot (-(n-1)) \\
>>\nu' &= -(n-1)p(t)\nu - (n-1)q(t) \qquad&& \tag*{$\square$}
>>\end{alignat}$$
>
>>[!example]- Task Find every nonzero solution of the differential equation $y' = y+2y⁵$
>>Note, this is a Bernoulli equation with $n=5$. We use the procedure shown in the proof.
>>$$\begin{alignat}{2} 
>>y' &= y+2y⁵ \qquad &&\Big|:y⁵ \\
>>\frac{y'}{y^5} &= y^{-4}+2  \tag{1}\\
>>\end{alignat}$$
>>We now set $\nu = y^{-4} \;\;(2)$ and have 
>>$$ \begin{alignat}{2} 
>>	\nu' &= -4y^{-5} y' \qquad &&\Big|\cdot -4^{-1} \\
>>	-\frac{\nu'}{4} &= \frac{y'}{y^5} &&\tag{3}
>>\end{alignat}$$ 
>>Setting $(1) = (3)$ 
>>$$\begin{alignat}{2}
>>	-\frac{\nu'}{4} &= \nu+2 \qquad &&\Big|\cdot (-4) \\
>>	\nu' &= -4\nu-8 \qquad 
>>\end{alignat}$$
>>This equation can now be solved using the [[First Order ODEs#^thmsolvefoode|solution for first order ODEs with constant coefficients]] which is
>>$$y(t) = ce^{at} - \frac{b}{a} $$
>>We identify
>>$$\begin{align}
>>	a &= -4\\
>>	b &= -8
>>\end{align}$$
>>We find
>>$$ \begin{equation} \nu = ce^{-4t} - 2 \tag{4}\end{equation}$$
>>Substituting $(4)$ back into $(2)$ yields
>>$$\begin{alignat}{2}
>>	y^{-4} &= \nu \\ 
>>	y^{-4} &= ce^{-4t} - 2 \qquad&&\Big|( \,. )^{-1/4}\\ 
>>	y &= \frac1{\left(ce^{-4t} - 2\right)^{1/4}} 
>>\end{alignat}$$ 
>
>>[!example]- Task Given any constants $a_0, b_0$ find every solution of the differential equation $y'= a_0y +b_0y^3$
>> The given equation is a Bernoulli equation with $n=3$. Therefore, we use the procedure of the proof
>> $$\begin{alignat}{2}
>> y' &= ay + by^3 \qquad &&\Big| \cdot y^{-3}\\
>> \frac{y'}{y^{-3}} &= ay^{-2} + b  \tag{1} 
>> \end{alignat}$$
>> We define $\nu=\frac{1}{y^2} \;\;(2)$ 
>> $$\begin{alignat}{2}
>> \frac{d \nu}{dt} &= \frac{d}{dt} \frac{1}{y^2} \\
>>  &= -2y{-3} \frac{dy}{dt} \\
>>  \nu' &= -2 \frac{ y'}{y{3}} \tag{3}
>>\end{alignat}$$
>>We insert the result $(3)$ into $(1)$ 
>>$$\begin{alignat}{2}
>> -\frac{\nu'}{2} &= \frac{a}{y^2} + b \qquad&&\Big\vert \cdot (-2) \\
>> \nu' &= -2a \nu - 2b 
>>\end{alignat}$$
>>Solving this using [[First Order ODEs#^thmsolvefoode|first order ODE with constant coefficients solution]] gives
>>$$\begin{alignat}{2}
>> \nu &= ce^{-2t} - \frac{b}{a}
>>\end{alignat}$$
>>Now inserting the result into $(2)$ yields
>>$$\begin{alignat}{2}
>> \nu &= \frac{1}{y^2} \\
>> ce^{-2t} - \frac{b}{a} &= \frac{1}{y^2}  \qquad&&\Big\vert (\,.)^{-2}\\
>> y &= \pm\frac{1}{\sqrt{   ce^{-2t} - \frac{b}{a}}}   
>>\end{alignat}$$
>
>>[!example]- Task Find every solution of the equation $ty'=3y+t^5y^{1/3}$
>>Note this equation is a Bernoulli equation with $n=\frac{1}{3}$. We use the results from the theorem. Rearranging the equation gives 
>>$$\begin{align}
>> y' &= \frac{3}{t}y + t^4 y^{1/3} \\ 
>> \frac{y'}{y^{1/3}} &= \frac{3}{t}y^{2/3} + t^4 
>>\end{align} $$
>>Setting $\nu$ and its derivative according to the theorem
>>$$\begin{align}
>> \nu &= \frac{1}{y^{n-1}} \\
>> \nu &= \frac{1}{y^{-2/3}} \\
>> &= y^{2/3} \tag{1} \\
>> \nu' &= \frac{2}{3} \frac{y'}{y^{1/3}} \\
>> \nu' \frac{3}{2} &= \frac{y'}{y^{1/3}} 
>>\end{align}$$
>>Using the results
>>$$\begin{align}
>> \nu' \frac{3}{2} &= \frac{3}{t}y^{2/3} + t^4 \\
>> \nu' &= \frac{2}{t}\nu + \frac{2}{3}t^4 \\
>>\end{align}$$
>>This equation represents an ODE with variable coefficients with $a(t) = \frac{2}{t}$ and $b(t)=\frac{2}{3}t^4$. Following the [[First Order ODEs#^defThmSolODEVar|solution theorem]] we have
>> $$\begin{align}
>> y(t)&=ce^{A(t)} + e^{A(t)} \int  e^{-A(t)} b(t) \, dt 
>>\end{align}$$
>>
>>with $$A(t) = \int  a(t)\, dt$$ 
>>We solve $A(t)$
>>$$\begin{align}
>>A(t) &= \int \frac{2}{t} \, dt \\
>> &= 2 \int  \frac{1}{t} \, dt \\
>> &= 2 \ln{|t|} +c_{0}\\ 
>> &= \ln{t^2} + c_{0} 
>>\end{align}$$
>>Then we have with $c_{0}=0$
>>$$\begin{align}
>> e^{-A(t)} &= e^{-\ln t^2} \\
>> &= t^{-2} \\
>>\int  e^{-A(t)} b(t) \, dt &= \int   t^{-2} \frac{2}{3}t^4 \, dt\\
>> &= \int   \frac{2}{3}t^2 \, dt\\
>> &= \frac{2}{9}t^3 + c_{1}\\
>>\end{align}$$
>>Finally with $c_1=0$
>>$$\begin{align}
>> \nu(t) = t^2 + \frac{2}{9}t^5
>>\end{align}$$
>>Inserting this result into $(1)$
>>$$\begin{alignat}{2}
>> \nu &= y^{2/3} \\
>>  t^2 + \frac{2}{9}t^5 &= y^{2/3} \qquad&&\Big\vert (\,.)^{3/2}\\
>>  y&= \pm \left(t^2 + \frac{2}{9}t^5\right)^{3/2}
>>\end{alignat}$$

^c27f79

>[!example]- Exercises
>>[!example]- Find all solutions of $y' = 4ty$
>> Given is a first order [[First Order ODEs#^defThmSolODEVar|ODE with variable coefficients]] with $a(t)=4t$ and $b(t)=0$. We therefore use the solution theorem.
>> $$\begin{align}
>> y &= ce^{A(t)} + e^{A(t)} \int  e^{-A(t)} b(t) \, dt \\
>> A(t)&= \int  a(t) \, dt \\ 
>> &= \int  4t dt \\   
>> &= 2t^2 + \underbrace{ c_{0} }_{ =0 }   \\ 
>> y &= ce^{2t^2} + e^{2t^2} \cdot 0\\
>> y &= ce^{2t^2}\\
>>\end{align}$$
>
>>[!example]- Find the general solution of $y' = -y + e^{-2t}$
>>Given is a first order [[First Order ODEs#^defThmSolODEVar|ODE with variable coefficients]] with $a(t)=-1$ and $b(t)=e^{-2t}$. We therefore use the solution theorem.
>>$$\begin{align}
>> y &= ce^{A(t)} + e^{A(t)} \int  e^{-A(t)} b(t) \, dt \\
>> A(t)&= \int  a(t) \, dt \\ 
>> &= \int  -1 dt \\   
>> &= -t + \underbrace{ c_{0} }_{ =0 }   \\  
>> \int  e^{-A(t)} b(t) \, dt &= \int  e^t e^{-2t} \, dt \\
>> &= \int  e^{-t} \, dt \\
>> &= -e^{-t} \\
>> y &= ce^{-t} + e^{-t} \cdot \left(-e^{-t}\right)\\
>> y &= ce^{-t} -e^{-2t}\\
>>\end{align}$$
>
>>[!example]- Find the solution of $y$ to the IVP $y' = y + 2te^{2t}, \quad y(0)=0$ 
>>Given is a first order [[First Order ODEs#^thmsolIVPvar| ODE IVP problem with variable coefficients]] with 
>>$$\begin{align}
>> a(t)  & = 1 \\ 
>> b(t)  & = 2te^{2t}  \\ 
>> t_{0} &= 0 \\
>> y_{0} &= y(0) = 0 \\
>>\end{align}$$
>> We use the formula of the theorem, i.e.
>> $$\begin{align}
>> y(t) &= y_0e^{A(t)} + e^{A(t)}\int_{t_0}^t e^{-A(s)}b(s) \, ds \tag{1}\\
>> A(t) &= \int _{t_{0}}^t a(s) \, ds 
>>\end{align}$$
>>Hence, we solve
>>$$\begin{align}
>> A(t)  & = \int _{0}^t 1\, ds \\
>>       & = s \Big\vert_{0}^t \\ 
>>       & = t \\
>> \int_{t_0}^t e^{-A(s)}b(s) \, ds &= \int_{0}^t e^{-s}2se^{2s} \, ds \\
>>       &= \int_{0}^t 2se^{s} \, ds \\ \\
>>\end{align}$$
>>For this we use [[../Calculus/Integration#^thmIntByParts| integration by parts]]
>>$$\begin{align}
>> \int  u \, dv = uv - \int  v \, du 
>>\end{align}$$
>>We choose
>>$$\begin{align} \\
>> u &= 2s \\ 
>> dv &= e^{s}\\
>>\end{align}$$
>> and determine
>> $$\begin{align} \\
>> du &= 2\\ 
>> v &= e^s \\ \\
>> \int 2se^{s} \, ds &= 2se^s - \int 2e^s \, ds \\
>>   &= 2se^s - 2e^s + c  \\
>>\end{align}$$
>>Evaluating the integral between $t_0 = 0$ and $t$ gives
>>$$\begin{align}
>> \left[2se^s- 2e^2\right]_0^t &= 2se^t - 2e^t +2
>>\end{align}$$
>>Plugging the found terms into $(1)$ gives
>>$$\begin{align} \\
>> y &= 0 + e^t \left(2se^t - 2e^t + 2\right) \\
>> y &= 2e^t \left(se^t - e^t + 1\right) \\
>>\end{align}$$
>
>>[!example]- Find the solution of $y$ to the IVP $ty' +2y = \frac{\sin(t)}{t} \quad y\left(\frac{\pi}{2}\right)=\frac{2}{\pi}$ for $t>0$ ❌
>> First reorder the task to identify the problem properly
>> $$\begin{alignat}{2}
>>  ty' + 2y & = \frac{\sin(t)}{t} \qquad&&\Big\vert -2y\\
>>  ty' & = \frac{\sin(t)}{t} - 2y\qquad&&\Big\vert \cdot t^{-1}\\
>>  y' & = \frac{\sin(t)}{t^2} - \frac{2}{t}y\\
>>\end{alignat}$$
>>This can be identified as an [[First Order ODEs#^thmsolIVPvar| ODE IVP problem with variable coefficients]] with
>>$$\begin{align}
>>  a(t) &= -\frac{2}{t} \\
>>  b(t) &= \frac{\sin(t)}{t}  \\
>> t_{0} &= \frac{\pi}{2}\\ 
>> y_{0} &= \frac{2}{\pi}
>>\end{align}$$
>>We use the solution equation 
>>$$\begin{align}
>> y(t) &= y_0e^{A(t)} + e^{A(t)}\int_{t_0}^t e^{-A(s)}b(s) \, ds \tag{1}\\
>> A(t) &= \int _{t_{0}}^t a(t) \, dt 
>>\end{align}$$
>>and solve 
>>$$\begin{align}
>> A(t) &= \int _{\pi / 2}^t -\frac{2}{s}\, dt \\
>>      &= -2\int _{\pi / 2}^t \frac{1}{s}\, dt \\ 
>>      &= -2 \left(\ln |s| \right) \Big\vert_{\pi / 2}^{t} \\
>>      &= -2 \left(\ln |t| - \ln |\pi / 2| \right) \\
>>      &= -2 \left(\ln  \frac{2|t|}{\pi}\right) \\
>>      &=  \ln \left[\left(|t| \frac{2}{\pi}\right)^{-2}\right] \\
>>\int_{t_0}^t e^{-A(s)}b(s) \, ds&= \int_{\pi / 2}^t e^{-\ln \Big[\big(|s| {\pi}/{2}\big)^{-2}\Big]} \frac{\sin s}{s}\, ds \\ \\
>> &= \int_{\pi / 2}^t \left(s \frac{\pi}{2}\right)^{2} \frac{\sin s}{s} \, ds  \\
>> &=\frac{\pi^2}{4} \int_{\pi / 2}^t s^2 \frac{\sin s}{s} \, ds \\
>> &=\frac{\pi^2}{4} \int_{\pi / 2}^t  s \sin (s)\, ds 
>>\end{align}$$
>>The integral can be solved using integration by parts and use the results from [[../Calculus/Integration#^thmIntByParts|example 1 from the integration by parts theorem]]. We have
>>$$\int  x \sin (x) \, dx = -x\cos x + \sin x + c$$
>>Hence
>>$$\begin{align}
>> \frac{\pi^2}{4} \int_{\pi /2}^t  s \sin (s)\, ds &=  \frac{\pi^2}{4} \Big[-s\cos s + \sin s \Big]_{\pi / 2}^{t}\\
>>  &=  \frac{\pi^2}{4} \left( -t\cos t + \sin t - \left( -\frac{\pi}{2} \cos \frac{\pi}{2} + \sin \frac{\pi}{2} \right) \right) \\
>>  &=  \frac{\pi^2}{4} \left( -t\cos t + \sin t - 1 \right)
>>\end{align}$$
>
>>[!example]- Find all solutions $y$ to the ODE $\dfrac{y'}{(t^2+1)y} = 4t$
>> First we reformulate the given equation to solve
>> $$\begin{alignat}{2}
>> \dfrac{y'}{(t^2+1)y} &= 4t \qquad&&\Big\vert \cdot (t²+1)y\\
>> y' &= (4t^4+4t)y \\
>>\end{alignat}$$
>> Given is a first order [[First Order ODEs#^defThmSolODEVar|ODE with variable coefficients]] with $a(t)=4t^4+4t$ and $b(t)=0$. First we solve
>> $$\begin{align}
>> A(t)&= \int  4t^3 \, dt + \int  4t \, dt \\ 
>> &= t^4 + 2t^2 + \underbrace{ c }_{ =0 }
>>\end{align}$$
>>Now we plug into the solution formula and get
>> $$\begin{align}
>> y&= ce^{t^4+2t^2}+e^{t^4+2t^2}\int e^{-(t^4+2t^2)} \cdot 0 \, dt \\
>> y&= ce^{t^4+2t^2} 
>>\end{align}
>> $$
>
>>[!example]- Find all solutions $y$ to the ODE $ty' +ny = t^2$ with $n$ a positive integer
>> First we rearrange the formula
>>$$\begin{alignat}{2}
>> ty' +ny&=t^2  \qquad&&\Big\vert -ny\\
>> ty' &=t^2 -ny  \qquad&&\Big\vert \cdot t^{-1}\\
>> y' &=t -\frac{n}{t} y  \\
>>\end{alignat}$$
>>Given is a first order [[First Order ODEs#^defThmSolODEVar|ODE with variable coefficients]] with $a(t)=-\frac{n}{t}$ and $b(t)=t$. First we solve
>>$$\begin{align}
>> A(t) &=  \int - \frac{n}{t} \, dt \\
>>      &=  -n \int  \frac{1}{t} \, dt \\
>>      &=  -n \ln t + \underbrace{ c }_{ =0 }\\
>>      &=  \ln t^{-n} \\ \\
>> \int e^{-\ln t^{-n}} t \, dt &= \int  t^n t \, dt \\  
>>      &= \int  t^{n+1} \, dt \\  
>>      &=  \frac{1}{n+2}t^{n+2} + \underbrace{ c }_{ =0 }\\  
>>\end{align}$$
>>Now we plug into the solution formula and get
>>$$\begin{align}
>> y &= ce^{A(t)} + e^{A(t)}\int e^{-A(t)}b(t) \, dt \\
>>   &= ce^{\ln t^{-n}} + e^{\ln t^{-n}}\frac{1}{n+2}t^{n+2}  \\
>>   &= \frac{c}{t^{n}} + \frac{1}{t^{n}}\frac{1}{n+2}t^{n+2}  \\
>>   &= \frac{c}{t^{n}} + \frac{1}{n+2}t^{2}  \\
>>\end{align}
>>
>>$$
>
>>[!example]- Find the solutions to the IVP $2ty - y' = 02$ with $y(0)=3$
>> Rearranging we have 
>> $$ y' = 2ty$$
>> which is a [[First Order ODEs#^thmsolIVPvar | First Order ODE IVP with variable coefficients]] with 
>> $$\begin{align}
>> a(t) &= 2t \\
>> b(t) &= 0 \\
>> y_{0} &= y(0)= 3  \\
>> t_{0}  &= 0
>>\end{align}$$
>>Using the solution formula we get
>>$$\begin{align}
>>  y &= y_{0}^{A(t)} + \underbrace{ e^{A(t)} \int_{t_{0}}^t e^{-A(s)}b(s)  \, ds }_{ =0 } 
>>\end{align}$$
>>Solving $A(t)$ yields
>>$$\begin{align}
>> A(t) &= \int _{t_{0}}^t a(s) \, ds \\
>> A(t) &= \int _{0}^t 2t \, ds  \\
>> A(t) &= \left[ t^2\right]_{0}^t  \\
>> A(t) &= t^2  \\
>>\end{align}$$
>>which solves to
>>$$ y=3e^{2t} $$
>
>>[!example]- Find all solutions of the equation $y' = y - 2\sin(t)$
>> We have a [[First Order ODEs#^defThmSolODEVar| First Order ODE with variable coefficients]] with 
>> $$\begin{align}
>> a(t) &= 1 \\
>> b(t) &= -2\sin(t) \\
>>\end{align}$$
>>We use the solution formula
>>$$\begin{align}
>> y &= ce^{A(t)} + e^{A(t)} \int e^{-A(t)} b(t) \, dt 
>>\end{align}$$
>>First we find $$\begin{align}
>> A(t) &= \int a(t) \, dt \\
>> &= \int 1 \, dt \\  
>> &= t \\  
>>\end{align}$$
>>Then solving the integral yields the following problem
>>$$\begin{align}
>> \int  e^{-t} -2\sin(t)\, dt &=  -2 \int e^{-t}\sin(t) \, dt 
>>\end{align}$$
>>We use the [[../Calculus/Integration#^thmSubstitutionRuleIndef|substitution rule]] to solve the integral $\int u\,dv = uv - \int v\, du$
>>$$\begin{align}
>> -2 \int \underbrace{ e^{-t} }_{ =dv }\underbrace{ \sin(t) }_{ =u } \, dt &= -2 \left(-e^{-t}\sin(t) -\int -e^{-t} \cos(t) \, dt \right)
>>\end{align}$$
>>Again we have to use the [[../Calculus/Integration#^thmSubstitutionRuleIndef|substitution rule]] for the next integral
>>$$\begin{align}
>> \phantom{-2 \int \underbrace{ e^{-t} }_{ =dv }\underbrace{ \sin(t) }_{ =u } \, dt }&= -2\left(-e^{-t}\sin(t) +\int \underbrace{ e^{-t} }_{ =dv } \underbrace{ \cos(t) }_{ =u } \, dt \right)\\ 
>> &= -2\left(-e^{-t}\sin(t) + \underbrace{ \Big(-e^{-t} \cos(t)\Big) }_{ =uv }-\int -e^{-t}  (-\sin(t)) \, dt \right) \\
>> &= -2\left(-e^{-t}\sin(t) -e^{-t} \cos(t)- \int e^{-t}  \sin(t) \, dt \right) \\
>> &= -2\left(-e^{-t}\sin(t) -e^{-t} \cos(t)\right) -2 \int e^{-t}  \sin(t) \, dt  \\
>>\end{align}$$ 
>>Now we bring the integral to one side and remove the factor, hence 
>>$$\begin{alignat}{2}
>> -2 \int \underbrace{ e^{-t} }_{ =dv }\underbrace{ \sin(t) }_{ =u } \, dt &= -2\left(-e^{-t}\sin(t) -e^{-t} \cos(t)\right) +2 \int e^{-t}  \sin(t) \, dt  \qquad&&\Big\vert - 2 \int e^{-t}  \sin(t) \, dt\\
>> -4 \int \underbrace{ e^{-t} }_{ =dv }\underbrace{ \sin(t) }_{ =u } \, dt &= -2\left(-e^{-t}\sin(t) -e^{-t} \cos(t)\right)  \qquad&&\Big\vert :(-4)\\
>> \int \underbrace{ e^{-t} }_{ =dv }\underbrace{ \sin(t) }_{ =u } \, dt &= \frac{1}{2}\left(-e^{-t}\sin(t) -e^{-t} \cos(t)\right)  \\
>> 
>>\end{alignat}$$
>>Inserting the found terms into the solution formula yields
>>$$ y= c^{t}- \frac{1}{2} \sin t - \frac{1}{2}\cos t$$ 
>
>>[!example]- Find the solution to the IVP $ty' = 2y + 4t³ \cos(4t)$ with $y\left(\frac{\pi}{8}\right)=0$ ❔
>> Rearranging the equation to
>> $$ y' = \frac{2}{t}y +4 t^2 \cos (4t)$$
>> This is an first order ODE with variable coefficients with
>> $$\begin{align}
>> a(t)&= \frac{2}{t} \\ 
>> b(t) &= 4t^2 \cos (4t)  \\
>> t_{0} &= \frac{\pi}{8}  \\
>> y_{0} &= y(t_{0}) = 0
>>\end{align}$$
>> Using the solution formula
>> $$ y = y_{0} e^{A(t)} + e^{A(t)} \int _{t_{0}}^t e^{-A(s)}b(s) \, ds $$
>> we first solve
>> $$\begin{align}
>> A(t) &= \int_{t_{0}}^t a(s)  \, ds \\ 
>>  &= \int_{{\pi}/{8}}^t \frac{2}{s}  \, ds \\ 
>>  &= 2\int_{{\pi}/{8}}^t \frac{1}{s}  \, ds \\ 
>>  &= 2\left[\ln s \right]_{{\pi}/{8}}^t   \\
>>  &= 2\left[\ln t - \ln \frac{\pi}{8}\right]   \\
>>  &= 2\ln\left( t  \frac{8}{\pi}\right)   \\
>>  &= \ln\left( t  \frac{8}{\pi}\right)^2   \\
>>\end{align}$$ 
>>Now we solve the integral of the solution formula
>>$$\begin{align}
>> \int _{t_{0}}^t e^{-A(s)}b(s) \, ds &= \int _{{\pi}/{8}}^t e^{\ln\left( s  \frac{8}{\pi}\right)^{-2}}4s^2 \cos (4s) \, ds \\
>>  &= \int _{{\pi}/{8}}^t \left(\frac{\pi}{8s}\right)^2 4s^2 \cos (4s) \, ds \\
>>  &= \left(\frac{\pi}{8}\right)^2\int _{{\pi}/{8}}^t \cancel{\frac{1}{s^2}} 4\cancel{s^2} \cos (4s) \, ds \\
>>  &= \left(\frac{\pi}{8}\right)^2\int _{{\pi}/{8}}^t 4 \cos (4s) \, ds \\
>>  &= \left(\frac{\pi}{8}\right)^2 \Big[\sin (4s)\Big]_{{\pi}/{8}}^t \\
>>  &= \left(\frac{\pi}{8}\right)^2 \Big[\sin (4t) - 0\Big] \\
>>  &= \left(\frac{\pi}{8}\right)^2 \sin (4t)\\
>>\end{align}$$
>>Now we have
>>$$\begin{align}
>>y &= y_{0} e^{A(t)} + e^{A(t)} \int _{t_{0}}^t e^{-A(s)}b(s) \, ds \\  
>>  &= 0 \cdot e^{\ln\left( 8t/{\pi}\right)^2} + e^{\ln\left( 8t/{\pi}\right)^2} \left(\left(\frac{\pi}{8}\right)^2 \sin (4t)\right)   \\
>>  &= t^2\cancel{\left(\frac{8}{\pi}\right)^2} \cancel{\left(\frac{\pi}{8}\right)^2} \sin (4t)  \\
>>  &= t^2\sin (4t)  \\
>>\end{align}$$
>
>>[!example]- Find all solutions of the equation $y' + ty = ty²$ ❔
>> We rearrange 
>> $$\begin{alignat}{2}
>> y' + ty &= ty² \qquad&&\Big\vert -ty\\
>> y' &= ty² -ty \\
>>\end{alignat}$$
>> This is a [[First Order ODEs#^defBernoulli|Bernoulli equation]] with $n=2$, $p(t)=-t$ and $q(t)=t$. We solve using the $\nu$ [[First Order ODEs#^c27f79 | linearization formula]]. Therefore,
>>$$\begin{align}
>> \nu' &= -(n-1) p(t)\nu - (n-1)q(t)  \\
>> &=t\nu-t 
>>\end{align}$$
>>This now is a [[First Order ODEs#^defThmSolODEVar|first order ODE with variable coefficients]]. Solving gives
>>$$\begin{align}
>> \nu &= ce^{A(t)} + e^{A(t)}\int e^{-A(t)}b(t) \, dt \\
>>  &= ce^{\frac{1}{2}t^2} + e^{\frac{1}{2}t^2}\int e^{-\frac{1}{2}t^2}t \, dt \\
>>\end{align}$$
>>Solving the integral $\int e^{-\frac{1}{2}t^2}t \, dt$ using the [[../Calculus/Integration#^thmSubstitutionRuleIndef | substitution rule]]
>>$$\begin{alignat}{2}
>> u &= -\frac{1}{2}t^2 \\ 
>> du &= -t\, dt \qquad&&\Big\vert :(-t)\\
>> -\frac{1}{t}du &= dt \\
>> \int e^{-\frac{1}{2}t^2}t \, dt &= \int -e^{u} \, du \tag{Substitution}\\
>>  &= -e^{u} + c\\
>>  &= -e^{-\frac{1}{2}t^2}+ \underbrace{ c }_{ =0 } \tag{Resubstitution}\\
>>\end{alignat}$$
>>Solving $\nu$
>>$$\begin{align}
>> \nu &= ce^{\frac{1}{2}t^2} - \underbrace{ e^{\frac{1}{2}t^2}e^{-\frac{1}{2}t^2} }_{ =1 }\\
>>   &= ce^{\frac{1}{2}t^2} - 1\\
>>\end{align}$$
>>Resubstituting it with respect to $y$ gives
>>$$ \begin{alignat}{2}
>> \nu &= \frac{1}{y^{n-1}} \\
>> ce^{\frac{1}{2}t^2} - 1 &= \frac{1}{y} \qquad&&\Big\vert \;(\,.)^{-1}\\
>> \frac{1}{ce^{\frac{1}{2}t^2} - 1} &= y
>>\end{alignat}$$
>
>>[!example] Find all solutions of the equation $y'= -xy + 6x\sqrt{ y }$
>
>>[!example] Find all solutions of the equation $y' = y + \frac{3}{y^2}$ with $y(0)=1$
>
>>[!example] Find all solutions of $y' = ay + by^n$ with $a\neq 0$ and $b,n\in \mathbb{R}$ constants with $n\neq0,1$

## 4 - Separable Equations

>[!def] Definition Separable Differential Equation ([[../../../Sources/nagy.pdf#page=32|Source]]) 
>A **separable** differential equation for the function $y$ is 
>$$ h(y) y' = g(t)$$
>where $h, g$ are given functions
>>[!note]-
>>- LHS depends explicitly on $y$, while
>>- RHS depends explicitly on $t$
>
>>[!note]
>>If an equation is separable, it can be easily solved by integrating both sides with respect to $t$
>
>
>>[!example]- Examples Identifying Separable Equations
>>>[!example]
>>>$$ \begin{align}
>>> y' &= \frac{t^2}{1-y^2} \\
>>> (1-y^2)y' &= t^2 \\
>>>\end{align}$$
>>>with
>>>$$\begin{align}
>>> g(t) &= t^2 \\
>>> h(y) &= 1 - y^2
>>>\end{align}$$
>>
>>>[!example]
>>>The equation $y'=e^y + \cos(t)$ is not separable.
>
>>[!example]- Example Find all solutions $y$ to the differential equation $-\frac{y'}{y^2} = \cos (2t)$
>>Note the differential equation is separable. Note
>>$$\begin{align}
>> h(y) &= -\frac{1}{y^2} \\ 
>> g(t) &= \cos (2t)
>>\end{align}$$ 
>>Therefore, we can solve by integration
>>$$\begin{alignat}{2}
>> -\frac{y'}{y^2} &= \cos (2t) \qquad&&\Big\vert \int  \, dt \\
>> \int -\frac{y'}{y^2}  \,dt  &= \int \cos (2t)  \, dt \tag{1}\\
>>\end{alignat}$$
>>Using the [[../Calculus/Integration#^thmSubstitutionRuleIndef | substitution rule]] with 
>>$$\begin{align}
>> u &= y  \\
>> &= g(t)\\
>> \frac{du}{dt} &= y' \\
>> {du} &= y' {dt}\\
>> f(u) &= -\frac{1}{u^2}
>>\end{align}$$ 
>>we have for $u=y$
>>$$\begin{align}
>>\int f(g(t))g'(t) \, dt &= \int f(u) \, du  \\
>>                        &= \int -\frac{1}{u^2} \, du  \\
>>                        &= \frac{1}{u} +c  \\
>>\end{align}$$
>>Substituting back yields
>>$$ \begin{align}
>>\int -\frac{y'}{y^2}  \,dt  &= \frac{1}{y} + c \tag{2}
>>\end{align}$$
>>We use again the substitution rule for solving the RHS of $(1)$, i.e. $\int \cos (2t)  \, dt$ 
>>$$ \begin{align}
>> u &= 2t \\
>>  &= g(t) \\
>> f(u) &= \cos(u) \\
>> \frac{du}{dt} &= 2 \\ 
>> du &= 2dt \\ 
>> \frac{1}{2} du &= dt\\
>>\end{align}$$
>>Hence, we have for $u=g(t)$
>>$$\begin{align}
>>\int \underbrace{ \cos(2t) }_{ =f(u) } \,\underbrace{  dt }_{ \frac{1}{2} du } &= \int \cos(u) \frac{1}{2}du  \\
>>                        &= \frac{1}{2}\int \cos (u) \, du  \\
>>                        &= \frac{1}{2} \sin (u) + c \\
>>\end{align}$$
>>Resubstituting $u=2t$ solves the RHS
>>$$\begin{equation}
>>\int \cos (2t)  \, dt = \frac{1}{2} \sin (u) + c \tag{3}
>>\end{equation} $$
>>Using the results from $(2)$ and $(3)$ gives
>>$$\begin{alignat}{2}
>> \frac{1}{y} &= \frac{1}{2}\sin (2t) + c \qquad&&\Big\vert (\,.)^{-1}\\
>> {y} &= \frac{2}{\sin (2t) + 2c} \\
>>\end{alignat} $$
>^defSeparableDifferentialEquation

>[!Theorem] Theorem Solutions to Separable Equations ([[../../../Sources/nagy.pdf#page=33|Source]]) 
>If $h,g$ are continuous with $h\neq 0$, then
>$$ h(y)y' = g(t)$$
>has infinitely many solutions $y$ satisfying the algebraic equation
>$$ H(y(t)) = G(t)+c$$
>where $c \in \mathbb{R}$ is arbitrary, $H$ and $G$ are antiderivatives of $h$ and $g$.
>>[!proof]-
>>$$\begin{alignat}{2}
>> h(y)y' &= g(t) \qquad&&\Big\vert \int (\,.) \, dt \\
>> \int h(y)y' \, dt  &= \int g(t) \, dt + c  \\
>>\end{alignat}$$
>>Using the [[../Calculus/Integration#^thmSubstitutionRuleDef| substitution rule]] for LHS we have
>>$$\begin{align}
>> u &= y(t) \\ 
>> du & = y'(t) dt \\
>> \int h(\underbrace{ y }_{ =u })\underbrace{ y' \, dt  }_{ = du }&= \int h(u)\, du   \\
>>&= \int h(y)\, dy \tag{Resubstitution} 
>>\end{align}$$
>>Hence, we have
>>$$\begin{align}
>>	\int h(y)y \, dy &= \int g(t) \, dt + c
>>\end{align}$$
>>We denote
>>$$\begin{align}
>> H(y) = \int h(y) \, dy \tag{Antiderivative of $h$} \\
>> G(t) = \int  g(t) \, dt \tag{Antiderivative of $g$} 
>>\end{align}$$
>>Hence we have
>>$$\begin{align}
>> H(y) = G(t) + c \tag*{$\square$}
>>\end{align}$$
>
>>[!Example]- Example Find all solutions $y$ to the differential equation $y' = \frac{t^2}{1-y^2}$
>>First we bring the equation into its separated form
>>$$\begin{alignat}{2}
>> y' &= \frac{t^2}{1-y^2} \qquad&&\Big\vert \cdot (1-y^2)\\
>> y'(1-y^2) &= t^2
>>\end{alignat} $$
>>Now we can apply the theorem
>>$$\begin{align}
>> h(y) &= 1-y^2 \\  
>> g(t) &= t^2 
>>\end{align}$$
>>We determine the antiderivatives
>>$$\begin{align}
>> H(y) &= \int 1-y^2 \, dy  \\
>> &= y-\frac{1}{3}y^3 \\
>> G(t) &= \int  t^2 \, dt \\
>> &= \frac{1}{3}t^3 
>>\end{align}$$
>>The solution to the given differential equation is
>>$$\begin{align}
>>y-\frac{1}{3}y^3 = \frac{1}{3}t ³ + c
>>\end{align}$$

^017e13

>[!def] Definition Implicit and Explicit Form ([[../../../Sources/nagy.pdf#page=35|Source]]) 
> A function $y$ is a solution in <u>**implicit form**</u> of the equation $h(y)y'=g(t)$ iff the function $y$ is solution of the algebraic equation $$H(y(t)) = G(t) + c$$ where $H$ and $G$ are any antiderivatives of $h$ and $g$. In the case that function $H$ is invertible, the solution $y$ above is given in <u>**explicit form**</u> iff is written as 
> $$y(t) = H^{-1}\big(G(t) + c\big)$$ 
> 
>>[!note]
>>In the case that $H$ is not invertible or $H^{-1}$ is difficult to compute, we leave the solution $y$ in implicit form.
>^defImplicitExplicit

## 4.1 - Euler Homogeneous Equations

>[!def] Definition Euler Homogeneous Differential Equation ([[../../../Sources/nagy.pdf#page=37|Source]]) 
>An **Euler homogenous** differential equation has the form
>$$\begin{align}
> y'(t) = F\left( \frac{y(t)}{t} \right)
>\end{align}$$

>[!lemma]  Scale Invariance and Homogeneous Functions
>1. **Scale Invariance** 
>  Any function $F$ of $t, y$ that depends only on the quotient $\frac{y}{t}$ is scale invariant. This means that $F$ does not change when we do the transformation $y \mapsto cy$ and $t \mapsto ct$,
>  $$F\left(\frac{cy}{ct}\right) = F\left( \frac{y}{t} \right)$$
>  For this reason the differential equations above are also called **scale invariant equations**.
>>[!example] Example Show that the functions $f_1$ and $f_2$ are scale invariant functions
>>$$\begin{align}
>> f_{1}(t,y)&= \frac{y}{t} \tag{1}\\
>> f_{2}(t,y)&= \frac{t^3+t^2y+ty^2+y^3}{t^3+ty^2}\tag{2}
>>\end{align}$$
>>>[!example]- Solution
>>>1. $\,$ $$\begin{align}
>>> f_{1}(ct,cy)&= \frac{cy}{ct}  \\
>>> &= \frac{c}{t} \\
>>> &= f_{1}(t,y)
>>>\end{align}$$
>>>Hence, $f_1$ is scale invariant
>>>1. $\,$ $$\begin{align}
>>> f_{2}(ct, cy) &=  \frac{(ct)^3+(ct)^2(cy)+(ct)(cy)^2+(cy)^3}{(ct)^3+(ct)(cy)^2} \\
>> &=  \frac{c³t^3+c³t^2y+c³ty^2+c³y^3}{c³t^3+c³ty^2}\\
>> &=  \frac{\cancel{ c^3 }(t^3+t^2y+ty^2+y^3)}{\cancel{ c^3 }(t^3+ty^2)}\\
>> &=  f_{2}(ct, cy)
>>>\end{align}$$
>>>Hence, $f_2$ is scale invariant
>  <br>
>2. **Homogeneous Functions**
>    Scale invariant functions are a particular case of **homogeneous functions of degree $n$**, which are functions $f$ satisfying $$f(ct, cy)=c^n f(y,t)$$
>    Scale invariant functions are the case $n=0$. Note that the exponents of each summand of $y$ and $t$ sum up to $n$.
>>[!example] Example Show that functions $f_1$ and $f_2$ are homogeneous and find their degree
>>$$\begin{align}
>> f_1(ct,cy) &= c^4t^4c^2y^2 + ctc^5y^5 + c^3t^3c^3y^3 \tag{1} \\
>> f_{2}(ct,cy) &= c^2t^2c^2y^2 + ctc^3y^3 \tag{2}
>>\end{align}$$
>>>[!example]- Solution
>>>1. $\,$ $$\begin{align}
>>>f_1(ct,cy) &= c^4t^4c^2y^2 + ctc^5y^5 + c^3t^3c^3y^3  \\
>>> &= c^6t^4y^2 + c^6ty^5 + c^6t^3y^3 \\
>>> &= c^6(t^4y^2 + ty^5 + t^3y^3) \\
>>> &= c^6f_{1}(t,y)
>>>\end{align}$$
>>> Hence, $f_1$ is a **homogeneous differential equation** of degree 6.
>>>2. $\,$ $$\begin{align}
>>>f_{2}(ct,cy) &= c^2t^2c^2y^2 + ctc^3y^3 \\ 
>>> &= c^44(t^2y^2+ty^3) \\
>>> &=c^4 f_{2}(t,y) 
>>>\end{align}$$
>>> Hence, $f_2$ is a **homogeneous differential equation** of degree 4.
>>
>    
>>[!note]- Note Physics Example
>>An example of a homogeneous function is the energy of a thermodynamical system, such as a gas in a bottle. The energy, $E$, of a fixed amount of gas is a function of the gas entropy, $S$, and the gas volume, $V$. Such energy is a homogeneous function of degree one, $$E(cS, cV) = cE(S,V)$$ for all $c\in\mathbb{R}$
>
>^remScaleInvarianceHomogenousFunctions

>[!Theorem] Theorem Identification of Euler Homogeneous Differential Equations ([[../../../Sources/nagy.pdf#page=39|Source]]) 
> If the functions $N, M$ of $t,y$ are homogeneous of the same degree, then the differential equation
> $$ N(t,y)y'(t) + M(t,y) = 0 $$
>is **Euler homogeneous**.
>>[!proof]-
>> We rewrite the equation as
>> $$\begin{align}
>> y'(t) = - \frac{M(t,y)}{N(t,y)}
>>\end{align}$$
>>It can easily be shown, that $f(t,y) = - \frac{M(t,y)}{N(t,y)}$ is scale invariant.
>>>[!proof]- Proof $f(t,y)$ being scale invariant
>>>$$\begin{align}
>>> f(ct,cy) &= - \frac{M(ct,cy)}{N(ct,cy)} \\
>>>  &= - \frac{\cancel{ c^n }M(t,y)}{\cancel{ c^n }N(t,y)} \\
>>>  &= - \frac{M(t,y)}{N(t,y)} \\
>>>  &= f(t,y) \\
>>>\end{align}$$
>>>because both $M$ and $N$ are homogeneous of degree $n$
>>
>>Now we try to find a function $F$ such that we can write
>>$$y'(t) = F\left( \frac{y}{t} \right)$$
>>Therefore, we set $c=1/t^n$ and use the property of the homogeneous equation. We have
>>$$\begin{align}
>> y'(t) &= - \frac{M(t,y)}{N(t,y)} \underbrace{ \frac{1/t^n}{1/t^n} }_{ =c^n/c^n }  \\
>> &=  - \frac{M(t/t,y/t)}{N(t/t,y/t)} \\
>> &=  - \frac{M(1,y/t)}{N(1,y/t)} \\ \\
>>\end{align}$$
>>Now we can formulate
>>$$ \begin{align}F\left( \frac{y}{t} \right) &= - \frac{M(1,y/t)}{N(1,y/t)} \tag*{$\square$}\end{align}$$
>
>>[!example]- Example Show that $(t-y)y'-2y+3t+\frac{y^2}{t} =0$ is an Euler homogeneous equation.
>> We first rearrange 
>> $$\begin{align}
>> (t-y)y'-2y+3t+\frac{y^2}{t} = 0 \\
>> (t-y)y' = 2y-3t-\frac{y^2}{t} \\
>> y' = \frac{2y-3t-\frac{y^2}{t}}{(t-y)} \\
>>\end{align}$$
>>We note that $f(t,y) = \frac{2y-3t-{y^2}/{t}}{(t-y)}$ is a homogeneous differential equation of degree 1, i.e.
>>$$\begin{align}
>> f(ct,cy) &= \frac{2cy-3ct-{\frac{c^{\cancel{ 2 }}y^2}{\cancel{ c }t}}}{(ct-cy)} \\
>>  &= \frac{\cancel{ c }\left(2y-3t-{\frac{y^2}{t}}\right)}{\cancel{ c }(t-y)} \\
>>  &= f(t,y) \\
>>\end{align}$$
>>Now we rewrite the equation in the form $y'=F(\frac{y}{t})$. Since the numerator and denominator are both of degree $n=1$, we multiply the fraction with $\frac{1/t}{1/t}$
>>$$\begin{align}
>> y' &= \frac{2y-3t-\frac{y^2}{t}}{(t-y)} \frac{\frac{1}{t}}{\frac{1}{t}}\\
>>    &= \frac{2\frac{y}{t}-3-\frac{y^2}{t^2}}{\left( 1-\frac{y}{t} \right)}
>>\end{align}$$
>>We have found
>>$$F\left( \frac{y}{t} \right) = \frac{2\frac{y}{t}-3-\frac{y^2}{t^2}}{\left( 1-\frac{y}{t} \right)}$$
>
>>[!example]- Example Determine whether the equation $(1-y^3)y'=t^2$ is Euler homogeneous.
>> First we determine a proper form for $f(t,y)$
>> $$\begin{align}
>> (1-y^3)y' &= t^2 \\
>> y' &= \frac{t^2}{1-y^3} \\
>> &= f(t,y) 
>>\end{align}$$
>>We now check the condition for homogeneity  
>>$$\begin{align}
>> f(ct, cy) &= \frac{c^2 t^2}{1-c^3y^3} \\
>> &\neq f(t,y)
>>\end{align}$$
>>Hence, the equation is not homogeneous.
>
>^thmIdentificationEulerHomogeneous

>[!theorem] Theorem Solutions to Euler Homogeneous Differential Equations ([[../../../Sources/nagy.pdf#page=40|Source]]) 
> The Euler homogeneous equation 
> $$ y' = F\left( \frac{y}{t} \right)$$
> for the function $y$ determines a separable equation for $$\begin{align}
>\nu = \frac{y}{t} \tag{Change of Functions}
>\end{align}$$  given by 
> $$\frac{\nu'}{(F(\nu)-\nu)}=\frac{1}{t}$$
>>[!proof]-
>> First we denote $\nu = \frac{y}{t}$ and
>> $$y' = F(\nu)$$
>> Now  we use the identity $y = t\nu$ to find a replacement for $y'$
>>>[!note]- Note on the identity $y = t\nu$
>>>Since $\nu = \frac{y}{t}$, we have
>>>$$\begin{align}
>>> y &= t\nu \\
>>> y &= \cancel{ t } \frac{y}{\cancel{ t }} \\ 
>>> y &= y
>>>\end{align}$$
>>
>>$$\begin{alignat}{2}
>> y(t) &= t\nu(t) \qquad&&\Big\vert \frac{d}{dt}\\
>> y' &= \nu + \nu't \qquad&& \tag{Product Rule} \\
>> &= F(\nu) \tag{By Definition}
>>\end{alignat}$$
>>Rearranging gives
>>$$\begin{alignat}{2}
>> F(\nu) &= \nu + t\nu' \qquad&&\Big\vert -\nu; \;\;:\nu'\\
>> \frac{F(\nu)-\nu}{\nu'} &= t \qquad&&\Big\vert\, (\,.)^{-1}\\
>> \frac{\nu'}{F(\nu)-\nu} &= \frac{1}{t} \tag*{$\square$}\\
>>\end{alignat}$$
>
>>[!example]- Example Find all solutions $y$ of the differential equation $y'= \frac{t^2 + 3y^2}{2ty}$
>>First we verify that the given equation is a Euler homogeneous for $f(t,y) = \frac{t^2 + 3y^2}{2ty}$
>>$$\begin{align}
>>f(ct,cy) &= \frac{c^2t^2 + 3c^2y^2}{2ctcy} \\
>> &= \frac{\cancel{ c^2 }(t^2 + 3y^2)}{\cancel{ c² }(2ty)} \\
>> &= f(t,y)
>>\end{align}$$
>>Knowing that its a Euler homogeneous of degree $n=2$ we just multiply the fraction with $\frac{1/t^2}{1/t^2}$ to find $F(\frac{y}{t})$
>>$$\begin{align}
>> F\left( \frac{y}{t} \right) &= \frac{t^2 + 3y^2}{2ty} \frac{\frac{1}{t^2}}{\frac{1}{t^2}} \\
>>  &= \frac{1 + 3(\frac{y}{t})^2}{2\frac{y}{t}} \\
>>\end{align}$$
>>Denote $\nu(t) = \frac{y(t)}{t}$ (change of functions), hence we have
>>$$\begin{align}
>> y' = \frac{1+3\nu}{2\nu^2} \tag{1}
>>\end{align}$$
>>Now we substitute $y'$. Note 
>>$$\begin{align}
>> y &= \nu t \\ 
>> y' &= \nu't + \nu 
>>\end{align}$$
>>We substitute into $(1)$
>>$$\begin{alignat}{2}
>> \nu't + \nu &= \frac{1+3\nu^2}{2\nu} \qquad&&\Big\vert -\nu\\
>> v't&= \frac{1+3\nu^2}{2\nu} - \frac{2\nu^2}{2\nu} \\
>> v't&= \frac{1+\nu^2}{2\nu} \qquad&&\Big\vert :t \\
>> v'&= \frac{1+\nu^2}{2t\nu} \\
>> v'&= \frac{1}{t}\left(\frac{1+\nu^2}{2\nu}\right)
>>\end{alignat}$$
>>which is a [[First Order ODEs#^defSeparableDifferentialEquation | separable equation]], rearranging we have
>>$$\begin{align}
>> \left( \frac{2\nu}{1 + \nu^2} \right)\nu' = \frac{1}{t} 
>>\end{align}$$
>>We solve by integrating on both sides. First we apply the  [[../Calculus/Integration#^thmSubstitutionRuleIndef | substitution rule]] to the LHS. We have
>>$$\begin{align}
>> u &= 1+\nu^2(t) \tag{2}\\
>> du &= 2\nu(t) \nu'(t) \;dt \\
>>  \int \frac{2\nu}{1+\nu^2} \nu' \, dt  &= \int \frac{1}{u} \, du \tag{Substitution}\\
>>\end{align}$$
>>Hence, we have by integrating on both sides
>>$$ \begin{alignat}{2}
>> \int \frac{1}{u}  \, du  &= \int \frac{1}{t} \, dt  + c \qquad&&  \\\\
>>      \ln(u)&= \ln t + c \qquad&&\Big\vert \,e^{(\,.\,)} \\
>>      u&= e^{\ln t + c}  \\
>>      u&= t \underbrace{ e^{c}  }_{ =c_{1} } \\
>>      u&= c_{1}t  \\
>>\end{alignat}$$ 
>>Plugging the solution for $u$ into $(2)$ yields
>>$$\begin{alignat}{2}
>> 1+\nu^2 &= c_{1}t  \qquad&&\Big\vert -1 \\
>> \nu^2 &=c_{1}t -1 \qquad&&\Big\vert \sqrt{ (\,.) } \\
>> \nu &=\pm\sqrt{c_{1}t -1 } 
>>\end{alignat}$$
>>Substituting back for $nu = \frac{y}{t}$ we have
>>$$\begin{alignat}{2}
>> \frac{y}{t} &=\pm\sqrt{c_{1}t -1 } \qquad&&\Big\vert \cdot t \\
>> y &=\pm t\sqrt{c_{1}t -1 }  \\
>>\end{alignat}$$
>
>>[!example]- Example Find all solutions $y$ of the differential equation $y' = \frac{t(y+1)+(y+1)^2}{t^2}$
>> First we show that the given function is a homogeneous function $f(t,y) = \frac{t(y+1)+(y+1)^2}{t^2}$. Therefore, we set $u = y+1 \;\;(1)$.
>>>[!note]
>>>Substituting $u=y+1$ is valid, since 
>>>$$\begin{align}
>>> \frac{du}{dt} &=\frac{d}{dt}(y+1) \\
>>> u' &= y' \\
>>>\end{align}$$
>>
>>Substituting yields
>>$$ \begin{align}
>>u' = \frac{tu+u^2}{t^2} \tag{2}
>>\end{align}$$
>>Now we check the conditions of homogeneity
>> $$\begin{align}
>> f(ct,cu) &= \frac{(ct)(cu)+c^2u^2}{c^2t^2} \\
>>          &= \frac{\cancel{ c^2 }(tu+u^2)}{\cancel{ c^2 }t^2} \\ 
>>          &= f(t,u) 
>>\end{align}$$
>>We introduce $\nu=\frac{u}{t}\;\;(3)$ with
>>$$\begin{align}
>> u &= \nu t  \\
>> u' &= \nu't + \nu
>>\end{align}$$
>>We set the found expression equal to $(2)$
>>$$\begin{alignat}{2}
>> \nu't + \nu &= \frac{t(\nu t)+(\nu t)^2}{t^2} \qquad&&\Big\vert -\nu \\
>> \nu't  &= \frac{t^2\nu+\nu^2t^2}{t^2} -\frac{t^2\nu}{t^2}\qquad&& \\
>> \nu't  &= \frac{\nu^2\cancel{ t^2 }}{\cancel{ t^2 }} \qquad&&\Big\vert :\nu'\\
>> t  &= \frac{\nu^2}{\nu'} \qquad&&\Big\vert \;(\,.)^{-1} \\
>> \frac{1}{t} &= v' \frac{1}{\nu^{2}}
>>\end{alignat}$$
>>This represents a [[First Order ODEs#^defSeparableDifferentialEquation | separable equation]]. We integrate on both sides accordingly
>>$$\begin{alignat}{2}
>> \int  \frac{1}{t} \, dt &= \int \frac{1}{\nu^2} \, d\nu  \\
>> \ln t + c&= -\frac{1}{\nu} \qquad&&\Big\vert \,(\,.)^{-1} \\  
>> \frac{1}{\ln t + c}&= -\nu \qquad&&\Big\vert \cdot (-1) \\  
>> -\frac{1}{\ln t + c}&= \nu \\  
>>\end{alignat}$$
>>Resubstituting into $(3)$ and $(1)$ gives
>>$$\begin{alignat}{2}
>> \nu &= \frac{u}{t} \tag{Substituting (3)} \\
>> -\frac{1}{\ln t + c}&= \frac{y+1}{t} \qquad&&\Big\vert \cdot t \tag{Substituting (1)} \\
>> -\frac{t}{\ln t + c}&= y+1 \qquad&&\Big\vert -1 \\
>> -\frac{t}{\ln t + c}-1&= y  \\
>>\end{alignat}$$
>

>[!example]- Exercises
>>[!example] Find all solution $y$ to the ODE $y' = \frac{t^2}{y}$. Express the solutions in explicit form.
>>Rearranging the equation gives
>>$$\begin{align}
>> y'y = t^2
>>\end{align}$$
>>which is a [[First Order ODEs#^defSeparableDifferentialEquation | separable equation]]. We integrate both sides and have
>>$$\begin{align}
>> \int y \, dy &= \int t^2 \, dt \\
>> \frac{1}{2}y^2 &= \frac{1}{3}t^3 + c \tag{Explicit Form}\\
>> y  &= \pm\sqrt{ \frac{2}{3}t ³ + 2c } \tag{Implicit Form}
>>\end{align}$$
>
>>[!example] Find every solution $y$ of the ODE $3t^2+4y^3y'-1+y'=0$. Leave the solution in implicit form.
>> We rearrange
>> $$\begin{alignat}{2}
>> 3t^2+4y^3y'-1+y'&=0 \qquad&&\Big\vert -3t²+1 \\
>> 4y^3y'+y'&=1 - 3t^2 \qquad&&\\
>> y'\underbrace{ (4y^3+1) }_{ h(y) }&=\underbrace{ 1 - 3t^2 }_{ g(t) } \qquad&&\\
>>\end{alignat}$$
>>which is a [[First Order ODEs#^defSeparableDifferentialEquation | separable equation]]. We integrate both sides and have
>>$$\begin{alignat}{2}
>>\int 4y^3 + 1 \, dy &= \int 1-3t^2 \, dt  +c \\
>>y^4 + y &= t-t^3  +c \tag{Implicit Form}\\
>>\end{alignat}$$
>
>>[!example] Find the solution $y$ to the IVP $y'=t^2y^2$ with $y(0)=1$
>>First we separate variables and solve by integrating both sides
>>$$\begin{alignat}{2}
>> y' &= t^2y^2 \qquad&&\Big\vert :y^2 \\
>> y'y^{-2} &= t^2 \qquad&& \\
>> \int y^{-2} \, dy &= \int t^2 \, dt  +c\qquad&& \\
>> -\frac{1}{y}  &= \frac{1}{3}t^3  +c \qquad&&\Big\vert \cdot(-1); \; (\,.)^{-1} \\
>> y &= -\frac{1}{\frac{1}{3}t^3 +c}
>>\end{alignat}$$
>>Now solving $y(0)=1$ for $c$
>>$$\begin{alignat}{2}
>>1 &= -\frac{1}{\frac{1}{3}0^3 +c} \qquad&& \\
>>1 &= -\frac{1}{c} \qquad&&\Big\vert \cdot(-1); \; (\,.)^{-1} \\
>>-1 &= c \qquad&& \\
>>\end{alignat}$$
>>For the IVP we have
>>$$\begin{align}
>> y &= -\frac{1}{\frac{1}{3}t^3 -1} \\
>> y &= -\frac{3}{t^3 -3} \\
>> y &= \frac{3}{3-t^3} \\
>>\end{align}$$
>
>>[!example] Find every solution $y$ of the ODE $ty + \sqrt{ 1+t^2 }\;y'=0$
>> We rearrange
>> $$\begin{alignat}{2}
>> ty + \sqrt{ 1+t^2 }\;y'&=0 \qquad&&\Big\vert -ty \\
>> \sqrt{ 1+t^2 }\;y'&=-ty \qquad&&\Big\vert :\sqrt{ 1+t^2 } \\
>> y'&=\frac{-t}{\sqrt{ 1+t^2 }}y \qquad&&\\
>>\end{alignat}$$
>>Which is an [[First Order ODEs#^defThmSolODEVar|first order ODE with variable coefficients]] with $a(t)=\frac{-t}{\sqrt{ 1+t^2 }}$ and $b(t)=0$. We use the solution formula
>>$$\begin{align}
>> y=ce^{A(t)} + \underbrace{ e^{A(t)} \int e^{-A(t)}b(t) \, dt }_{ =0 }
>>\end{align}$$
>>with
>>$$A(t) = \int a(t) \, dt $$
>>We solve $A(t)$ and rewrite therefore
>>$$\begin{alignat}{2}
>> \int \frac{-t}{\sqrt{ 1+t^2 }} \, dt  &=\int -t \left(1+t^2\right)^{-1/2} \, dt \\
>>\end{alignat}$$
>>Here we use the [[../Calculus/Integration#^thmSubstitutionRuleIndef|substitution method]] with $u=1+t^2$. We write
>>$$\begin{alignat}{2}
>> du &= 2t \; dt \qquad&&\Big\vert :(-2) \\
>> -\frac{1}{2}du &= -t \; dt \qquad&&\\
>>\end{alignat}$$
>>We substitute now
>>$$\begin{align}
>> \int -t \left(1+t^2\right)^{-1/2} \, dt  &=\int  -\frac{1}{2}u^{-1/2}\, du \\
>>  &=-\frac{1}{2}\int  u^{-1/2}\, du \\
>>  &=-\frac{1}{2} \left(2u^{1/2}\right) + c\\
>>  &=-(1+t^2)^{1/2} + c \tag{Resubstituting}\\
>>  &=-\sqrt{ 1+t^2 } + \underbrace{ c }_{ =0 } \tag*{$=A(t)$}\\
>>\end{align}$$
>>We now insert the found expression into the solution formula
>>$$\begin{align}
>>y = ce^{-\sqrt{ 1+t^2 }}
>>\end{align}$$
>
>>[!example] Find every solution $y$ of the Euler homogeneous equation $y' = \frac{y+t}{t}$
>
>>[!example] Find all solutions $y$ to the ODE $y' = \frac{t^2+y^2}{ty}$
>
>>[!example] Find the explicit solution to the IVP $(t^2+2ty)y' = y^2$ with $y(1)=1$
>
>>[!example] Prove that if $y' = f(t,y)$ is an Euler homogeneous equation and $y_1(t)$ is solution, then $y(t) = \frac{1}{k}y_{1}(kt)$ is also a solution for every non-zero $k \in \mathbb{R}$
>
>>[!example] Find the explicit solution of the IVP $y' = \frac{4t-6t^2}{y}$ with $y(0)= -3$

## 5 - Exact Differential Equations

>[!remark] Terminology
>
| Term                             | Meaning                                                                                                                                                                                                     |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Potential Function $\psi$        | the total derivative of a function                                                                                                                                                                          |
| Integrating Factor               | Is a function to transform a semi-exact equation into an exact equation                                                                                                                                     |
| Exact Differential Equation      | it is a potential function, i.e. a total derivative of a function                                                                                                                                           |
| Semi-Exact Differential Equation | is a function, which is not exact yet, but can be transformed to be exact by multiplying with an integrating factor                                                                                         |
| Total Derivative                 | Taking the derivative of a **multivariate function** with respect to all of the dependent variables                                                                                                         |
| Total $t$-Derivative             | Taking the derivative of a **multivariate function** with respect to $t$ where all dependent variables not only directly depend on $t$, but also have indirect dependencies through other variables on $t$. | 


>[!remark]-
>Linear differential equations are special case of semi-exact equations. 

>[!def] Definition Exact Equation ([[../../../Sources/nagy.pdf#page=44|Source]]) 
>An **exact** differential equation for $y$ is
>$$N(t,y)y' + M(t,y) = 0$$
>where the functions $N$ and $M$ satisfy
>$$\partial_{t}N(t,y) = \partial_{y} M(t,y)$$
>>[!note]- Note on Notation
>>$$\begin{align}
>> \partial_{t}N &= \frac{\partial N}{\partial t}  \\
>> \partial_{y}N &= \frac{\partial M}{\partial y}
>>\end{align}$$
>
>>[!example]- Example Separable Equations being exact
>> Recall [[First Order ODEs#^defSeparableDifferentialEquation | separable equations]] and their [[First Order ODEs#^017e13|solutions]]. Therefore, let 
>> $$h(y)y'(t) = g(t)$$
>> We rewrite the equation such that we have the **exact** form, i.e.
>> $$h(y)y'(t)-g(t) = 0$$
>> Now we denote
>> $$\begin{align}
>> N(t,y) &= h(y) \\
>> M(t,y) &= g(t)
>>\end{align} $$
>>Determining the partial derivatives and selecting the deriving variable properly gives
>>$$\begin{align}
>> \partial_t N(t,y) &= 0  \\
>> \partial_{y} M(t,y) &= 0
>>\end{align}$$
>>Clearly, we have
>>$$ \partial_t N(t,y) = \partial_{y} M(t,y)$$
>>Therefore, separable equations are exact equations.
>
>>[!example]- Example Linear Differential Equations being not exact
>>Recall [[First Order ODEs#^defThmSolODEVar| Linear Differential Equations with variable coefficients]]. We denote them with
>>$$ y'(t) = a(t)y(t)+b(t)\qquad a(t)\neq 0$$
>>We rewrite again to gain the **exact** form
>>$$ y' - a(t)y - b(t) = 0$$
>>We denote
>>$$\begin{align}
>> N(t,y) &= 1  \\
>> M(t,y) &= a(t)y - b(t)
>>\end{align}$$
>> Checking the conditions gives
>> $$\begin{align}
>> \partial_{t} N(t,y) &= 0 \\
>> \partial_{y} M(t,y) &= -a(t)
>>\end{align}$$
>>Hence, we from $\partial_{t} N(t,y) \neq \partial_{y} M(t,y)$ we can conclude linear differential equations are not exact differential equations.
>
>>[!example]- Example Non-separable Differential Equations being exact
>>Let $$2tyy' + 2t + y^2 = 0$$
>>We denote
>>$$\begin{align}
>> N(t,y) &= 2ty  \\
>> M(t,y) &= 2t+y^2
>>\end{align}$$
>>Determining the partial derivatives gives
>>$$\begin{align}
>> \partial_{t} N(t,y)&=2y \\
>> \partial_{y}M(t,y)&=2y
>>\end{align}$$
>>Since the partial derivatives match, we can conclude the given example is an exact equation.
>
>>[!example]- Example Show whether $\sin(t)y'+t^2e^yy'-y'=-y\cos(t)-2te^y$ is exact or not.
>>First, we rearrange to correctly identify the necessary terms
>>$$\begin{alignat}{2}
>> \sin(t)y'+t^2e^yy'-y'&=-y\cos(t)-2te^y \\
>> y'\big(\sin(t)+t^2e^y-1\big)&=-y\cos(t)-2te^y \qquad&&\Big\vert +y\cos (t)+2te^y\\
>> y'\underbrace{ \big(\sin(t)+t^2e^y-1\big) }_{ =N(t,y) } +\underbrace{ \big(- y\cos(t)-2te^y\big) }_{ =M(t,y) }&=0
>>\end{alignat}$$
>>Computing the partial derivatives will show if the equation is **exact**.
>>$$\begin{align}
>> \partial_{t}N(t,y) &= \cos (t) + 2te^y
>> \partial_{y}M(t,y) &= \cos (t) + 2te^y
>>\end{align}$$
>>Hence, the equation is **exact**.


>[!theorem] Theorem Poincaré's Lemma ([[../../../Sources/nagy.pdf#page=46|Source]]) 
> Let $N,M$ denote continuously differentiable functions on $t,y$. We have
> $$\begin{alignat}{2}
>\partial_{t}N(t,y) = \partial_{y}M(t,y) \Longleftrightarrow &\exists\psi\in C^2  \\
>& \psi: (t,y) \mapsto \psi(t,y) \\
>& \text{such that}\\
>& \partial_{y}\psi(t,y) = N(t,y) \\
>& \partial_{t} \psi(t,y) = M(t,y))
>\end{alignat}$$
>with $C^2$ being the space of twice continuously differentiable functions.
>>[!proof]- 
>>>$(\Rightarrow)$
>>> omitted, but is given in [[../../../Sources/rudin1976.pdf|Principles of Mathematical Analysis by Rudin]]
>>
>>>$(\Leftarrow)$
>>> Assume that $\psi$ is a **potential function** satisfying
>>> $$\begin{align}
>>> N &= \partial_{y}\psi  \\
>>> M &= \partial_{t}\psi \\
>>>\end{align}$$
>>>$\psi$ is twice differentiable, hence we can further differentiate $N$ and $M$. Therefore, we write
>>>$$\begin{align}
>>>\partial_{t} N = \partial_{t}\partial_{y}\psi = \partial_{y}\partial_{t}\psi = \partial_{y}M \tag*{$\square$}
>>>\end{align}$$

^0207e0


>[!theorem] Theorem Solving Exact Equations ([[../../../Sources/nagy.pdf#page=45|Source]]) 
> If the differential equation
> $$\begin{align}
>N(t,y)y' + M(t,y) = 0\tag{1}
>\end{align}$$
> is **exact**, then it can be written as
> $$\frac{d\psi}{dt}(t,y(t))=0$$
> where $\psi$ is called a **potential function** and satisfies
> $$N = \partial_{y} \psi, \quad M= \partial_{t}\psi$$
> Therefore, the solutions of the exact equation are given in [[First Order ODEs#^defImplicitExplicit |implicit form]] as
> $$\psi(t,y(t)) = c, \quad c\in \mathbb{R}$$
>>[!proof]-
>> Note that equation $(1)$ is an [[First Order ODEs#^7959bc|exact equation]]. Hence, the condition of [[First Order ODEs#^0207e0 | Poincaré's Lemma]] hold. Therefore, we can state
>> $$\begin{align}
>> N &= \partial_{y} \psi \\M &= \partial_{t}\psi
>>\end{align}$$
>>We can rewrite $(1)$ with
>>$$\begin{alignat}{2}
>> 0 &= N(t,y)y' &&+ M(t,y) \\
>>   &= \Big(\partial_{y}\psi(t,y)\Big) y' &&+ \partial_{t}\psi(t,y) \tag{2}\\
>>   &= \frac{d}{dt} \psi(t, y(t)) \tag{3}
>>\end{alignat}$$
>>Note, equation $(2)$ is the form of the _chain rule_ applied on equation $(3)$, i.e. $\frac{d}{dx}f(g(x))= \frac{df}{dg} \frac{dg}{dx}$, since one variable is a function of $t$ itself, i.e. $y(t)$.  Hence, $(3)$ is a total $t$-derivative and is therefore simple to integrate.
>>$$ \begin{align}
>> \int \frac{d}{dt} \psi(t, y(t)) \, dt  &= \int 0 \, dt \\
>> \psi(t,y(t)) &= c \tag*{$\square$}
>>\end{align}$$
>
>>[!remark] Remark Background and Geometrical Interpretation of Exact Equations
>> Exact equations come up frequently in physics and engineering. We denote $\psi(x,y)$ as the potential function being dependent on $x$ and $y$. The naming of the potential function with respect to physics and engineering suggests the it being connected to calculation of some energy or electrical potentials. See the following example
>> $$ \psi(x,y) = x^2 + y^2$$
>> ```tik
>>\usepackage{pgfplots}
>>\pgfplotsset{compat=1.16}
>>
>>\begin{document}
>>\begin{tikzpicture}
>>\begin{axis}[colormap/viridis]
>>\addplot3[
>>	surf,
>>	samples=18,
>>	domain=-3:3
>>]
>>{x^2 + y^2};
>>\end{axis}
>>\end{tikzpicture}
>>
>>\end{document}
>> ```
>> <div align="center">Figure 1 Plot of the potential function</div>
>> 
>> Taking the total derivative of the potential function gives
>> $$\begin{align}
>> \frac{d\,\psi(x,y)}{d x} &= \frac{\partial \psi}{\partial x} dx + \frac{\partial \, \psi}{\partial y}dy  \\
>> &= \partial_{x} dx + \partial_{y} dy
>>\end{align}$$
>
>>[!example]- Example Find all solutions $y$ to the differential equation $2tyy'+2t+y^2=0$
>> First we verify that the given equation is **exact**. We have
>> $$\begin{align}
>> \underbrace{ 2ty }_{ N(t,y) }y'+\underbrace{2t+y^2 }_{ M(t,y) }&=0  \\ \\
>> \partial_{t}N&=2y \\
>> \partial_{y}M&= 2y
>>\end{align}$$
>>We can assert the given equation to be **exact**. By [[First Order ODEs#^0207e0 | Poincaré's Lemma]] we know there exists the potential function $\psi$  satisfying
>>$$\begin{align}
>> \partial_{y} \psi(t,y) &=N(t,y) \tag{1}\\
>> \partial_{t} \psi(t,y) &= M(t,y)\tag{2}
>>\end{align}$$
>>We now determine the potential function $\psi$ by integrating equation $(1)$ with respect to $y$ and keeping $t$ constant. Hence, we have
>>$$\begin{align}
>>\psi(t,y) &= \int 2ty \, dy \\
>> &= ty^2 + g(t) \tag{3}
>>\end{align}$$
>>>[!note] 
>>>We integrated with respect to $y$. Clearly, $y$ is a function of $t$. Hence the value of $y$ is dependent of $t$. Therefore, we also allow the integration constant to be dependent of $t$. Therefore, we choose it to be the function $g(t)$.
>>
>>We use the found expression for the potential function and insert it into equation $(2)$.
>>$$\begin{align}
>> \partial_{t} \psi(t,y) &= \partial_{t} \Big(ty^2 + g(t)\Big)  \\
>> &=y^2 + g'(t) \tag{4}
>>\end{align}$$
>>>[!note]
>>>We treat $y$ as constant, even though it is also a function of $t$. In $(3)$ we already considered the change of rate of change with respect to $y$, that is why we strictly only consider $t$ and $g(t)$ since it is a constants expression with respect to $t$.
>> 
>> We now set the found expressions for $\partial_{t}\psi(t,y)$ from equation $(2)$ and $(4)$ equal
>> $$\begin{alignat}{2}
>> y^2 + g'(t) &= 2t+y^2 \qquad&&\Big\vert -y^2 \\
>> g'(t) &= 2t
>>\end{alignat}$$
>>Integrating $g'(t)$ yields the missing parameter for equation $(3)$.
>>$$g(t) = t^2 $$
>>Inserting the solution for $g(t)$ into $(3)$.
>>$$\begin{align}
>> \psi(t,y) = ty^2 + t^2
>>\end{align}$$
>>Applying the solution the solution theorem gives
>>$$ty^2 + t^2 = c$$
>
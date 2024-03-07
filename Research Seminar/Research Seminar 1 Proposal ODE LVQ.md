## 1. Introduction to Linear Ordinary Differential Equations

>[!Question] Question: What is a Linear Ordinary Differential Equation (ODE)?
>A linear ODE is an equation of the form
>$$y^{(n)} =\sum_{i=0}^{n-1} a_{i}y^{(i)}$$
>where $y^{(i)}$ is the $i$-th derivative of the function real/complex valued function $y(t)$ and $a_i$ are either constants or functions of $t$. In this definition $n$ gives the order of the ODE.
>
>In an ODE the variable of interest is the unknown function $y$.

>[!example] Example Linear First Order ODE 
>ODE: $y'=2y+3$
>Solution: $y = ce^{2t}-\frac32$
>>[!Calculation]- Calculation (Separation of Variables)
>>$$\begin{align} \frac{dy}{dt} &= 2y + 3 \\ 
>>\frac{dy}{2dt} &= y + \frac{3}{2} \\
>>\frac{1}{y+\frac{3}{2}}\; dy&= 2\; dt \\
>>\int \frac{1}{y+\frac32} \; dy &= \int 2 \; dt \\
>>\ln\left(y+\frac32\right) &= 2t +c_0\\
>>y + \frac32&=e^{2t} e^{c_0}\\
>>y &= ce^{2t}-\frac32
>>\end{align}$$
>
>Note, solving an ODE yields an integration constant $c$. Any choice of $c$ will be a solution to the ODE.
>
>![[ODE_example_1.png | center | 500 ]]
>$$\text{Figure: Direction Field of ODE with solutions at } y_{0}=(-20, -15, -10, -5, 0, 5, 10, 15) \text{ with } y_{0} = y(0)$$


>[!remark]
>The solution for a first order ODE characterizes infinitely many functions, dependent on the choice of the integration constant $c$.

>[!theorem] Hypothesis: ODE LVQ Fundamental Principle
>1. Let an ODE represent a prototype in an LVQ learning scheme
>2. Let an (for now) arbitrary function represent a data point in the LVQ learning scheme
>
>**Main Idea:**
>As previously remarked, an ODE **represents a set of functions <u>prototyped</u> by the ODE**. What if we can develop a learning scheme, such that
>* an ODE will be learned discriminating functions

>[!Warning] Issues
> 1. How to initialize prototypes?
> 2. Given an ODE, how to determine which function out of the set of functions described by the ODE fits best to a datapoint (function)?
> 3. Time series data more often than not is a set of discrete points. How should we get an ODE from such a set of discrete data points?
> 4. How to compare an ODE (prototype) to another function (data point)? (Metric)
> 5. Given we solved the first issues, how to formulate an update rule?

## 2. Road to ODE LVQ

### Issue 1 Prototype Inititialization
>[!theorem]  Initialization of Prototypes
> 1. Choose an arbitrary datapoint for a given class.
> 2. An ODE can be calculated given there is a function suitable for calculating its ODE

>[!example] Example: Determining the ODE for a function $y(t)=\frac{c_{1}}{t}+c_{2}t$
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

### Issue 2 Function Choice in ODE

>[!def] Definition Initial Value Problem ([[../PDFs/nagy.pdf#page=18|Source]])
> The initial value problem (IVP) is to find all solutions $y$ to 
> $$ y' = ay+b $$
> that satisfy the initial condition 
> $$ y(t_0) = y_0 \tag{Initial Condition}$$
> where $a,b,t_0, y_0$ are given constants.
>>[!note]
>>The differential equation has a unique solution with respect to the initial condition.

Similarly for second order ODEs etc.
>[!theorem] Theorem Solutions to IVP of Second Order ODEs ([[../PDFs/nagy.pdf#page=88| Source]])
>If 
>- the functions $a_{0},a_{1}, b$ are continuous on a closed interval $I \subset \mathbb{R}$, 
>- the constant $t_{0} \in I$, 
>- and $y_{0}, y_{1} \in \mathbb{R}$ are arbitrary constants
>
>then there is a unique solution $y$, defined on $I$, of the initial value problem
>$$y'' + a_{1}(t)y'+ a_{0}(t)y = b(t)$$
>with $$ y(t_{0})=y_{0} \quad y'(t_{0})= y_{1}$$

>[!remark] Remarks
>1. Even if we would construct ODEs of higher orders, we could still find a matching function in the higher order ODE by utilizing the initial value problem.
>2. Alex suggested that there might be other ways to pick a matching ODE, so this can still be changed if needed (needs more research)
>3. This method for now allows a straight forward approach to pick a function from the ODE

### Issue 3 Discrete Data

![[Figures/rs_1_fig_1.png|center|1000]]
$$\text{Figure: How to find an ODE representing the sequence of discrete points}$$

>[!remark] Discussion: Many possibilities
>1. Interpolation (Spline)
>2. Possibly using Laplace transform and treat it as piecewise continuous functions (not confirmed yet)
>3. Dirac Delta Expansion with Fourier Transform
>4. <u>My Approach:</u> Discrete Fourier Transform (DFT)

>[!properties] Properties of Sine and Cosine Functions
> The derivatives/anti-derivatives of $\sin$ and $cos$ behave nicely, i.e.
> $$\begin{align}
> \frac{d}{dt} \sin(ct) &= c \cos(ct) \\
> \frac{d}{dt} \cos(ct) &= -c \sin(ct)
>\end{align}$$
>>[!note]
>>The notion _nice behavior_ means $\sin$ and $\cos$ are very predictable in their derivatives/antiderivatives. The arguments inside the function stay constant and, the derivatives switch between $\sin$ and $\cos$.

>[!example] Example Step Function
>Let's approximate the step function the step function 
>$$f(x) = \begin{cases}
1 & \text{ if } 0 \leq x < \pi \\
-1 & \text{ if } \pi \leq x < 2\pi
\end{cases}$$
> by a partial Fourier sum $FS_{N}[f]_{t}$ with accuracy $N=2$, we get
> $$y = \frac{4}{\pi}\left( \sin(x)+ \frac{1}{3}\sin(3x) + \frac{1}{5}\sin(5x)+ \frac{1}{7}\sin(7x) + \frac{1}{9}\sin(9x) \right)$$
> We will omit the factor $\frac{4}{\pi}$ for simplification purposes
> $$y =  \sin(x)+ \frac{1}{3}\sin(3x) $$
> ![[Figures/rs_1_fig_2.png]]
> $$\text{Figure: partial sum in green, step function in orange}$$
> Lets determine an ODE from the approximation and parameterize the first coefficient. Hence,
> $$y = \underbrace{ c_{1} \sin(x) }_{ \substack{\text{ first}\\ \text{ coefficient}} }+ \frac{1}{3}\sin(3x) + \frac{1}{5}\sin(5x) + \frac{1}{7}\sin(7x) + \frac{1}{9}\sin(9x) \tag{1}$$
> We determine the first derivative
> $$y' = c_{1} \cos(x)+ \cos(3x)+ \cos(5x)+\cos(7x)+ \cos(9x)$$
> We solve for $c_{1}$
> $$c_{1} = \frac{y' - \cos(3x)-\cos(5x)-\cos(7x)-\cos(9x)}{\cos (x)}$$
> Inserting $c_{1}$ into equation $(1)$ gives
> $$\begin{align}
> y &= \frac{(y' - \cos(3x)-\cos(5x)- \cos(7x)-\cos(9x))\sin (x)}{\cos (x)}+ \frac{1}{3}\sin(3x) + \frac{1}{5}\sin(5x)+ \frac{1}{7}\sin(7x) + \frac{1}{9}\sin(9x) \\
> &=\frac{y'\sin(x)}{\cos(x)} -\frac{\sin(x)(\cos(3x)+ \cos(5x)+\cos(7x)+\cos(9x))}{\cos(x)} + \frac{1}{3}\sin(3x) + \frac{1}{5}\sin(5x)+ \frac{1}{7}\sin(7x) + \frac{1}{9}\sin(9x)
>\end{align} $$
> We now need to solve for $y'$ to yield the ODE, the solution is
> $$\begin{align}
> y' = \cos(3x)+\cos(5x)+\cos(7x)+\cos(9x) - \frac{\cos(x)}{\sin(x)}\left(\frac{1}{3}\sin(3x) + \frac{1}{5}\sin(5x)+\frac{1}{7}\sin(7x) + \frac{1}{9}\sin(9x) - y\right)
>\end{align}$$
>![[Figures/rs_1_fig_3.png]]
>$$\text{ODE with dependence on }\sin(x)$$
>If we solve for the $4$-th coefficient ($\frac{1}{7}\sin(7x)$), we get
>$$y' = \cos(x)+\cos(3x)+\cos(5x)+\cos(9x) - \frac{7\cos(7x)}{\sin(x)}\left(\sin(x)+\frac{1}{3}\sin(3x) + \frac{1}{5}\sin(5x)+ \frac{1}{9}\sin(9x) - y\right)$$
>![[Figures/rs_1_fig_4.png]]
>$$\text{ODE with dependence on } \frac{1}{7}\sin(7x)$$

>[!Observation]
>Dependent on which frequency term we use, the ODE 

>[!question] Questions
> 1. Which parameter should be chosen to define the ODE, and could it be beneficial to use higher order ODEs? 
> 2. How many should be chosen?
> 3. How would many parameters affect the construction?

### Issue 4 + 5 Comparing ODE to Function (Metric) and updating prototype

>[!observation] Idea
>1. Find function with _initial value problem_ (IVP)
>2. Compare IVP determined function with data point function 
>	* using Dynamic Timewarping
>	* using distance on $L^2[a,b]$ norm
>	* using distance based on maximums norm
>3. ???
>	 * update IVP function $u^*$-> determine ODE -> update prototype with ODE from $u^*$

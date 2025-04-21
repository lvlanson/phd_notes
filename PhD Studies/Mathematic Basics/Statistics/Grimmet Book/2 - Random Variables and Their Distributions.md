## 2.1 Random Variables
### Examples
A coin toss game, where we count the heads
>Let 
>- $X: \Omega \to \mathbb{R}$ be a random variable
>- $\Omega$ be the space of two coin tosses
>	- $\Omega = \{ HH, HT, TH, TT \}$
>- $X$ count the number of heads, i.e.
>$$\begin{align}
>X(HH) &= 2 \\
>X(HT) = X(TH)&= 1 \\
>X(TT) &= 0
>\end{align}$$

A coin toss game, where a gambler bets $1€$ on head and gambles cumulatively

>Let 
>- $W: \Omega \to \mathbb{R}$ be a random variable
>- $\Omega$ be the space of two coin tosses
>	- $\Omega = \{ HH, HT, TH, TT \}$
>- $X$ count the number of heads, i.e.
>$$\begin{align}
>W(HH) &= 4 \\
>X(HT) = X(TH) = X(TT) &= 1 \\
>\end{align}$$

Note, the gambler loses everything if only one tails appears.

![[Figures/2-distribution_function.png|center]]
<center> Visualization <span class="math display"> F_X </span> with Respect to Random Variable <span class="math display">X</span> </center>

>[!def] Definition Random Variable
> **<span style="color:#38ffa9">A random variable</span>** is a function $X: \Omega \to \mathbb{R}$ with the property that $\{ \omega \in \Omega : X(\omega)\leq x \} \in \mathcal{F}$ for each $x \in \mathbb{R}$. Such a function is said to be $\mathcal{F}$-measurable. ($\mathcal{F}$ is a $\sigma$-field)
>>[!example]
>>Consider the random variable $X$ from above
>> $$\begin{align}
>> A(1) &= \{ \omega \in \Omega : X(\omega) \leq 1 \} \\
>> &= \{ HT, TH, TT \}
>>\end{align}$$ 
>>where
>>$$A(x) = \{ \omega \in \Omega:X(\omega )\leq x \}$$

>[!def] Definition Distribution Function
>The **<span style="color:#38ffa9">distribution function</span>** of a random variable $X$ is the function $F: \mathbb{R} \to [0,1]$ given by 
>$$F(x) = \mathbb{P}(X \leq x)$$

### Examples Continued
$$\begin{align}
F_{X}(x) &= \begin{cases}
0 & \text{if } x < 0 \\
\frac{1}{4} & \text{if } 0 \leq x < 1 \\
\frac{3}{4} & \text{if } 1 \leq x < 2  \\
1 & \text{if } 2 \geq x
\end{cases} \\
F_{W}(x) &= \begin{cases}
0  & \text{if }x < 0 \\
\frac{3}{4} & \text{if } 0 \leq x < 4 \\
1 & \text{if } 4 \geq x
\end{cases}
\end{align}$$

>[!lemma] Lemma Properties of the Distribution Function
>A **<span style="color:#3884ff">distribution function</span>** $F$ has the following properties:
>1. $\lim_{ x \to -\infty } F(x) = 0$ and $\lim_{ x \to \infty } = 1$
>2. $x < y \implies F(x) < F(y)$
>3. $F$ is right-continous, that is, $F(x+h) \to F(x)$ as $h \searrow 0$
> 
>>[!proof]-
>>   
>>  (1) 
>>  Let $$B_{n} = \{ \omega \in \Omega : X(\omega ) \leq -n \}$$ be the event evaluating to at most $-n$. Now, recognize that $$B_{1}, B_{2},\dots$$ is a decreasing sequence where $$\begin{align}
>> \lim_{ n \to \infty } B_{n} &= \emptyset \\
>> \implies \lim_{ n \to \infty } \mathbb{P}(B_{n}) &= 0 
>>\end{align}$$
>>By constructing an increasing sequence $C_n$ one can prove also the other limit.
>>  (2)
>>  Let $$\begin{align}
>> A(x) &= \{ \omega \in \Omega : X(\omega) \leq x \}  \\
>> A(x,y) &= \{ \omega \in \Omega : x < X(\omega) \leq y \}
>>\end{align}$$
>>Denote $$A(x) \cup A(x,y) = A(y)$$
>>and note
>>$$A(x) \cap A(x,y) = \emptyset \implies \mathbb{P}(A(x))+\mathbb{P}(A(x,y)) = \mathbb{P}(A(y))$$
>>By definition we can conclude
>>$$F(y) = F(x) + \mathbb{P}(x < X \leq y) \geq F(x)$$

Note, for the preceding lemma, we have
$$\text{lemma} \iff \text{distribution function}$$

>[!lemma]
>Let $F$ be the distribution function of $X$. Then
>1. $\mathbb{P}(X > x) = 1-F(x)$
>2. $\mathbb{P}(x < X \leq y) = F(y)-F(x)$
>3. $\mathbb{P}(X=x) = F(x)-\lim_{ y \uparrow x }F(y)$
>
>>[!proof]-
>> (1) 
>> $$\begin{align}
>> \mathbb{P}(X>x) &= 1 - \mathbb{P}(X \leq x)  \\
>> &= 1 - F(x) \tag*{$\square$}
>>\end{align}$$
>>(2)
>>$$\begin{align}
>> \mathbb{P}(x <X \leq y) &= \mathbb{P}(Y \leq y) - \mathbb{P}(X \leq x) \\
>> &= F(y) -F(x) \tag*{$\square$}
>>\end{align}$$
>>(3)
>>Note, that we can use (2)
>>$$F(x)-\lim_{ y \uparrow x }F(y) = \lim_{ y \uparrow x } \mathbb{P}(y < X \leq x)$$
>>Define $y= x- \frac{1}{n}$ and denote
>>$$B_{n} = \left\{  \omega \in \Omega : x - \frac{1}{n} <X(\omega ) \leq x  \right\}$$
>>and note that 
>>$$\mathbb{P}(y < X \leq x) = \mathbb{P}(B_{n})$$
>>Observe that
>>$$\begin{align}
>> \lim_{ n \to \infty } B_{n}&= \{ \omega \in \Omega : x < X(\omega ) \leq x\} \\
>> &= \{ \omega \in \Omega: X(\omega)= x \}
>>\end{align} $$
>>Hence,
>>$$\begin{align}
>> \lim_{ y \uparrow x } \mathbb{P}(y < X \leq x) &= \lim_{ n \to \infty } \mathbb{P}(B_{n}) \\
>> &= \mathbb{P}(X=x) \tag*{$\square$}
>>\end{align}$$

## 2.2 The Law of Averages

- consider the probability of event $A$ to be the average of a repeated experiment, such that $$ \mathbb{P}(A)= \lim_{ N \to \infty } \frac{N(A)}{N}$$

>[!theorem] Theorem (Bernoulli, 1692)
>Let $S_n=\sum_{i=1}^{n} \mathbb{1}_{A_{i}}$ be the sum of indicator functions of the events $A_{1},A_{2},\dots,A_{n} \in \mathcal{F}$. The indicator function is defined as $\omega \in \Omega$
>$$\mathbb{1}_{A_{i}}(\omega) = \begin{cases}
1 &\text{if } \omega \in A \\
0 &\text{if } \omega \in \overline{A}
\end{cases}$$
> It is the case, that $n^{-1}S_{n}$ converges to $p$ as $n \to \infty$ in the sense that, for all $\varepsilon > 0$
>$$\mathbb{P}(p- \varepsilon \leq n^{-1} S_{n} \leq p + \varepsilon) \underset{n \to \infty}{\longrightarrow} 1$$

## 2.3 Discrete and Continuous Variables

>[!def] Definition Discrete Random Variable
>The Random variable $X$ is called **<span style="color:#38ffa9">discrete</span>** if it takes values in some countable subset $\{ x_{1},x_{2},\dots \}$, only, of $\mathbb{R}$. The discrete random variable $X$ has **<span style="color:#38ffa9">(probability) mass function</span>**
>$$f : \mathbb{R} \to [0,1]$$
>given by 
>$$f(x)= \mathbb{P}(X=x)$$

>[!def] Definition Continuous Random Variable
>The random variable $X$ is called **<span style="color:#38ffa9">continuous</span>** if its distribution function can be expressed as $$F(x) = \int _{-\infty}^{x} f(u) \, du \tag*{$x \in \mathbb{R}$}$$
>for some integrable function 
>$$f : \mathbb{R} \to [0,\infty)$$
>called the **<span style="color:#38ffa9">(probability) density function</span>** of $X$.


## 2.5 Random Vectors

>[!def] Definition Joint Distribution Function
> The **<span style="color:#38ffa9">joint distribution function</span>** of a random vector $$\boldsymbol{X}=(X_{1}, X_{2}, \dots, X_{n})$$ on the probability space $(\Omega, \mathcal{F}, \mathbb{P})$ is the function $$F_{\boldsymbol{X}}: \mathbb{R}^n \to [0,1]$$ given by
> $$F_{\boldsymbol{X}}(\boldsymbol{x}) = \mathbb{P}(\boldsymbol{X}\leq \boldsymbol{x})$$
> for $\boldsymbol{x}\in\mathbb{R}^n$.

>[!lemma] 
> The joint distribution function $F_{X,Y}$ of the random vector $(X,Y)$ has the following properties:
> 1. $$\lim_{ x,y \to -\infty } F_{X,Y}(x,y)=0 \quad \lim_{ x,y \to \infty } F_{X,Y}(x,y)=1$$
> 2. $$(x_{1},y_{1})\leq(x_{2},y_{2}) \implies F(x_{1},y_{1}) \leq F(x_{2},y_{2})$$
> 3. $F_{X,Y}$ is continuous from above, in that $$F_{X,Y}(x+u, y+v) \underset{u,v \searrow 0}\longrightarrow F_{X,Y}(x,y)$$


>[!note] 
>1. $$\lim_{ y \to \infty } F_{X,Y}(x,y) = F_{X}(x) = \mathbb{P}(X \leq x) $$
>2. $$\lim_{ x \to \infty } F_{X,Y}(x,y) = F_{Y}(y) = \mathbb{P}(Y \leq y) $$

>[!remark]
>The functions $F_{X}$ and $F_{Y}$ are called the **<span style="color:#e9ffad">marginal distribution functions</span>** of $F_{X,Y}$.

>[!def] Definition Jointly Discrete Random Variable
>The random variables $X$ and $Y$ on the probability space $(\Omega, \mathcal{F}, \mathbb{P})$ are called
**<span style="color:#38ffa9">(jointly) discrete</span>** if the vector $(X, Y)$ takes values in some countable subset of $\mathbb{R}^2$  only. The **<span style="color:#38ffa9">jointly discrete random variables </span>** $X, Y$ have joint (probability) mass function 
>$$f : \mathbb{R}^2 \to [0, 1]$$ given by $$f (x, y) = \mathbb{P}(X = x, Y = y)$$

>[!def] Definition Jointly Continuous Random Variable
>The random variables $X$ and $Y$ on the probability space $(\Omega, \mathcal{F}, \mathbb{P})$ are called **<span style="color:#38ffa9">(jointly) continuous</span>** if their joint distribution function can be expressed as 
>$$F_{X,Y}(x, y) = \int _{u= -\infty}^x \int _{v=-\infty}^y f(u,v) \, du \, dv \tag*{$x,y \in \mathbb{R}$} $$
>for some integrable function $$f : \mathbb{R}^2 \to [0, \infty)$$ called the **<span style="color:#38ffa9">joint (probability) density function</span>** of the pair $(X, Y)$.


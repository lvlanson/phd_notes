## 3.1 Probability Mass Functions

>[!def] Definition Probability Mass Function
>The **<span style="color:#38ffa9">(probability) mass function</span>** of a discrete random variable $X$ is the function 
>$$f: \mathbb{R}\to [0, 1]$$ 
>given by 
>$$f(x) = \mathbb{P}(X = x)$$

The distribution and mass functions are related by

$$F(x) = \sum_{i: x_{i} \leq x} f(x_{i}) \qquad f(x)= F(x)- \lim_{ y \uparrow x } F(y)$$ 

>[!lemma]
>The probability mass function $f:\mathbb{R} \to[0,1]$ satisfies:
>1. the set of $x$ such that $f(x)\neq 0$ is countable
>2. $\sum_{i} = 1$, where $x_{1},x_{2},\dots$ are the values of $x$ such that $f(x) \neq 0$


## 3.2 Independence

>[!def] Definition Independence
>Discrete variables $X$ and $Y$ are independent if the events ${X = x}$ and ${Y = y}$ are independent for all $x$ and $y$.

### Example 

>A coin is tossed once and heads turns up with probability $p = 1 - q$. Let $X$ and $Y$ be the numbers of heads and tails respectively. It is no surprise that $X$ and $Y$ are not independent. After all, $$\begin{align}
> \mathbb{P}(X=Y=1)&=0 \\
> \mathbb{P}(X = 1)\mathbb{P}(Y = 1) &= p(l - p)
>\end{align}$$

>[!theorem] Theorem
>If $X$ and $Y$ are independent and $g,h: \mathbb{R} \to \mathbb{R}$, then $g(X)$ and $h(Y)$ are independent also.

## 3.3 Expectation
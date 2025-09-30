Let 
- $\boldsymbol{x} \in X$ denote data points
- $\boldsymbol{w} \in W$ denote prototypes
- $\{ c(\boldsymbol{w}_{i}) \}_{i=1}^N$ denote the labels of the prototypes
	- where $c: \mathbb{R}^n \to C$ maps data points/prototypes to a class in $C$

>[!def] Definition Winning Prototype
>The winning prototype of the **Winner-Takes-All (WTA)** competition is defined as
>$$\boldsymbol{w}_{s} = \min_{\boldsymbol{w} \in W} \{ d(\boldsymbol{\boldsymbol{x, \boldsymbol{w}}}) \}$$
>with $d: \mathbb{R}^n \times \mathbb{R}^n \to[0, \infty)$ being a differentiable dissimilarity measure.

>[!def] Definition Approximation of the Classification Error
>Let 
>- $d^+ = d(\boldsymbol{x}, \boldsymbol{w}^+)$ denotes the distance of the best matching prototype $\boldsymbol{w}^+$ with $c(\boldsymbol{x})=c(\boldsymbol{w}^+)$
>- $d^- = d(\boldsymbol{x}, \boldsymbol{w}^-)$ denotes the distance of the best non-matching prototype $\boldsymbol{w}^-$ with $c(\boldsymbol{x})\neq c(\boldsymbol{w}^-)$
>
>then the **<span style="color:#38ffa9">approximation of the classification error</span>** is defined as
>$$\mu(\boldsymbol{x}) = \frac{d^+-d^-}{d^+ + d^-}$$

^98b74e

>[!remark] 
> The [[#^98b74e| definition of the Approximation of the Classification Error]] can also be considered as classifier function which
> - returns negative values if the classification is correct
> - returns positive values if the classification is incorrect

>[!def] Definition Cost Function GLVQ
>Let
>$$E_{GLVQ}(X,W) = \frac{1}{|X|}\sum_{\boldsymbol{x \in X}}E_{local}(\boldsymbol{x}, W)$$
>denote the **<span style="color:#38ffa9">cost function</span>** of GLVQ with the **<span style="color:#38ffa9">local error</span>**
>$$E_{local}=f\big(\mu(\boldsymbol{x})\big)$$
>where $f$ is usually either
>$$\begin{align}
> \sigma(\boldsymbol{x})&= \frac{1}{1+\exp\left( -\boldsymbol{x} \right)} \tag{sigmoid function}\\
> id(\boldsymbol{x}) &= \boldsymbol{x} \tag{identity function}
>\end{align}$$


>[!theorem] Theorem Gradient of GLVQ
> The gradient of GLVQ with respect to the **<span style="color:#38ffa9">local error</span>** is given as 
> $$\begin{align}
> \Delta \boldsymbol{w}^{+} &= \frac{\partial f}{\partial \mu} \cdot 4  \frac{d^-}{(d^+ + d^-)^2} (\boldsymbol{x}-\boldsymbol{w}^+) \\
> \Delta \boldsymbol{w}^{-} &= \frac{\partial f}{\partial \mu} \cdot 4 \frac{d^+}{(d^+ + d^-)^2}(\boldsymbol{x}-\boldsymbol{w}^-) 
>\end{align} $$
>>[!proof]
>> We have to take the partial derivative
>> $$\begin{align}
>>  \frac{\partial E_{local}}{\partial \boldsymbol{w}^{\pm}} &= \frac{\partial f}{\partial \mu} \frac{\partial \mu}{\partial d^{\pm}} \frac{\partial d^{\pm}}{\partial \boldsymbol{w}^{\pm}} \\ 
>>\end{align}$$
>>Since we consider $f$ being unknown at this point of time and we assume the **<span style="color:#38ffa9">squared Euclidean distance</span>** is used, we will only consider the other two partial derivatives.
>>$$\begin{align}
>> \frac{\partial \mu}{\partial d^{+}}&= \frac{\partial \frac{ d^+ - d^-}{ d^+ + d^-}}{\partial d^+}  \\
>>  &= \frac{\overbrace{ (d^++d^-) }^{ u'v } - \overbrace{ (d^+ - d^-) }^{ uv'  }}{\underbrace{ (d^+ + d^-)^2 }_{ v^2 }} \\
>> &= \frac{2d^-}{(d^+ + d^-)^2} \\ 
>> \frac{\partial \mu}{\partial d^{-}} &= \frac{2d^+}{(d^+ + d^-)^2} \\
>> \frac{\partial d^{+}}{\partial \boldsymbol{w}^{\pm}} &=  \frac{\partial d(\boldsymbol{w}^\pm, \boldsymbol{x})^2}{\partial \boldsymbol{w}^\pm} \\
>> &= \frac{\partial d(\boldsymbol{w}^\pm, \boldsymbol{x})^2}{\partial \boldsymbol{w}^\pm} \\
>> &= \frac{\partial \lvert\lvert \boldsymbol{w}^\pm - \boldsymbol{x} \rvert\rvert ^2}{\partial \boldsymbol{w}^\pm} \\
>> &= \frac{\partial {\boldsymbol{w}^\pm}^2 - 2\boldsymbol{w}^\pm\boldsymbol{x}+\boldsymbol{x}^2}{\partial \boldsymbol{w}^\pm} \\ 
>> &= 2\boldsymbol{w}^\pm - 2\boldsymbol{x} \\
>> &= 2(\boldsymbol{x}-2\boldsymbol{w}^\pm)
>>\end{align}$$
>>Hence we get
>> $$\begin{align}
>> \frac{\partial E_{local}}{\partial \boldsymbol{w}^{+}} &= \frac{\partial f}{\partial \mu}  \cdot \frac{2d^-}{(d^+ + d^-)^2} \cdot 2(\boldsymbol{x}-\boldsymbol{w}^+) \\
>> &= \frac{\partial f}{\partial \mu} \cdot 4 \frac{d^-}{(d^+ + d^-)^2}(\boldsymbol{x}-\boldsymbol{w}^-)  \\
>> \frac{\partial E_{local}}{\partial \boldsymbol{w}^{-}} &= \frac{\partial f}{\partial \mu} \cdot  4 \frac{d^+}{(d^+ + d^-)^2}(\boldsymbol{x}-\boldsymbol{w}^-)  \tag*{$\square$}
>>\end{align}$$

>[!remark] Remark Sigmoid as Activation Function
>
> Assume $f(\boldsymbol{x})= \sigma(\boldsymbol{x}) = \frac{1}{1+e^{-\boldsymbol{x}}}$ then 
> $$\begin{align}
> \frac{\partial \sigma(\mu)}{\partial \mu} &= \frac{\partial \frac{1}{1+e^{-\boldsymbol{\mu}}}}{\partial \mu}  \\
>   &=  \sigma(\mu) \cdot(1-\sigma(\mu))
>\end{align}$$
>and we get as gradient
>$$\begin{align}
>\Delta \boldsymbol{w}^{+} &= \sigma(\mu) \cdot(1-\sigma(\mu)) \cdot 4  \frac{d^-}{(d^+ + d^-)^2} (\boldsymbol{x}-\boldsymbol{w}^+) \\
>\Delta \boldsymbol{w}^{-} &= \sigma(\mu) \cdot(1-\sigma(\mu)) \cdot 4 \frac{d^+}{(d^+ + d^-)^2}(\boldsymbol{x}-\boldsymbol{w}^-) 
>\end{align}$$

>[!def] Definition Update Rule
>Given some label data point $(\boldsymbol{x}, y)$ and respective prototypes $\boldsymbol{w}^+, \boldsymbol{w}^-$
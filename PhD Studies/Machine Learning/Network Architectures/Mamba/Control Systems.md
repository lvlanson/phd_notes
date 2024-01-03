---
aliases:
- Control Systems
---

>[!source]-
>URL: 
>PDF: [PDF](brogan1991.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@brogan1991)

>[!terminology]-
>
>- Control Theory ([[../../../../Sources/brogan1991.pdf#page=21|Source]])
>> Control Theory is more often concerned with physical applications. A control system is considered to be any system which exists for the purpose of regulating or controlling the flow of energy, information, money, or other quantities in some desired fashion. In more general terms, a control system is an interconnection of many components or functional units in such a way as to produce a desired result. 
>- Control System ([[../../../../Sources/brogan1991.pdf#page=21|Source]])
>> - An open-loop control system chooses a control $\mathbf{u}(t)$ based on the goals of the systems and all available a priori knowledge about the system. The input is in no way influenced by the system's output $\mathbf{y}(t)$. If unexpected disturbances act upon an open-loop system, or if its behavior is not completely understood, then the output will not behave precisely as expected.
>> ![[figures/open_loop_control_system.png]]
>> <br>
>> - A closed-loop/feedback control system the control $\mathbf{u}(t)$ is modified by in some way by information about the behavior of the system output. A feedback system is often better able to cope with unexpected behavior.
>>![[figures/closed_loop_control_system.png]]
>

>[!variables]  ([[../../../../Sources/brogan1991.pdf#page=94|Source]])
>- $\mathcal{T}$ interval of time points $[t_a, t_b]$ with $t_a \leq t_b$
>- $\Sigma \subseteq \mathbb{R}$ is the state space
>- $x_i(t) \in \Sigma$ state variable $x_i$ at time $t \in \mathcal{T}$
>- $\mathbf{y}: \mathcal{T}^m \rightarrow \mathcal{Y}^m \subseteq \mathbb{F}^m$ **output** variable, i.e. $y_i(t) \in \mathbb{F}$
>- $\mathbf{u}: \mathcal{T}^r \rightarrow \mathcal{U}^r \subseteq \mathbb{F}^r$ is the **input or control** variable, i.e. $u_i(t) \in \mathbb{F}$
>- $\mathbf{u}_{[t_0, t_1]}$ describes the input interval $\left[\mathbf{u}(t_0), \mathbf{u}(t_1)\right]$

>[!Note]  State ([[../../../../Sources/brogan1991.pdf#page=93|Source]])
>A state is a complete summary of a system's state at a particular point in time $t_i$ for $i\geq0$ with respect to some initial point of time $t_0$. The variables $x_i \in \mathbb{F}$ are called the *state variables*. A system can be described by a finite number of states which can be given as a *state vector* $\mathbf{x} = (x_1, \ldots, x_n)^T$.

>[!def] Definition Time Interval  ([[../../../../Sources/brogan1991.pdf#page=94|Source]])
>Let $\mathcal{T}$ denote the time interval $[t_a, t_b]$. 
>If the time interval is 
>- continuous => $[t_a, t_b] \subseteq \mathbb{R}$
>- discrete => $[t_a, t_b] \subseteq \mathbb{Z}$

>[!def] Definition State Variables ([[../../../../Sources/brogan1991.pdf#page=95|Source]])
>The state variables $\mathbf{x} \in \mathbb{F}^n$ of a system consist of a minimum set of parameters which completely summarize the system's status in the following sense. If at any time $t_0 \in \mathcal{T}$ the values of the state variables $x_i(t_0)$ are known, then the output $\mathbf{y}(t_1)$ and the values $x_i(t_1)$ can be uniquely determined for any time $t_1 \in \mathcal{T}, t_1 > t_0$ provided $\mathbf{u}_{[t_0, t_1]}$ is known.

>[!def] Definition System State ([[../../../../Sources/brogan1991.pdf#page=95|Source]])
> The state at any time $t_0$ is a set of the minimum number of parameters $x_i(t_0)$ which allows a unique output segment $\mathbf{y}_{[t_0, t]}$ to be associated with each input segment $\mathbf{u}[t_0, t]$ for every $t_0 \in \mathcal{T}$ and for all $t > t_0, t\in \mathcal{T}$.

>[!def] Definition State Mapping ([[../../../../Sources/brogan1991.pdf#page=96|Source]])
>Let $\mathbf{g}$ be the system mapping with
>$$ \mathbf{g}: \mathcal{T}\times \mathcal{T}\times \Sigma \times \mathcal{U} \rightarrow \Sigma$$
>$$\mathbf{x}(t_1) = \mathbf{g}\Big(t_0, t_1, \mathbf{x}(t_0), \mathbf{u}_{[t_0, t_1]}\Big)$$

>[!def] Definition System Mapping ([[../../../../Sources/brogan1991.pdf#page=96|Source]])
> Since $\mathbf{y}(t_1)$ is uniquely determined, there exists a mapping
> $$ \mathbf{h}: \mathcal{T} \times \Sigma \times \mathcal{U}^r \rightarrow \mathcal{Y}^m $$
> $$ \mathbf{y}(t_1) = \mathbf{h}\Big(t_1, \mathbf{x}(t_1), \mathbf{u}(t_1)\Big)$$


>[!note]
>- the mapping $\mathbf{h}$ has no memory
>- $\mathbf{y}$ depend only on the instantaneous values $\mathbf{x}(t_1), \mathbf{u}(t_1)$ and $t_1$.
>- the mapping $\mathbf{g}$ is *non-anticipative* (causal)
>- => the state and output $t_1$ are not dependent on inputs occurring after $t_1$ 

>[!def] Definition Dynamical System ([[../../../../Sources/brogan1991.pdf#page=96|Source]])
> The model of a physical system is called a *dynamical system* if a set of times $\mathcal{T}$, spaces $\mathcal{U}, \Sigma, \mathcal{Y}$ and mappings $\mathbf{g}, \mathbf{h}$ can be associated with it. The mappings $\mathbf{g}, \mathbf{h}$ must have the following properties
> 1. For any $t_0, t_1 \in \mathcal{T}$ $$\begin{align}\mathbf{x}(t_0) = \mathbf{g}\big(t_0, t_0, \mathbf{x}(t_0), \mathbf{u}_{[t_0, t_1]}\big)\tag{Idenitity Property}\end{align}$$
> 2. If $\mathbf{u} \in \mathcal{U}$ and $\mathbf{v} \in \mathcal{V}$ with $\mathbf{u} = \mathbf{v}$ over some segment $[t_0, t_1]$, then 
>  $$\begin{equation}\mathbf{g}\Big(t_0,t_1, \mathbf{x}(t_0), \mathbf{u}_{[t_0, t_1]}\Big) = \mathbf{g}\Big(t_0,t_1, \mathbf{x}(t_0), \mathbf{v}_{[t_0, t_1]}\Big)\tag{State Transition Property}\end{equation}$$
>  3. If $t_0, t_1, t_2 \in \mathcal{T}$ and $t_0 < t_1 < t_2$, then
>  $$\begin{align} \mathbf{x}(t_2) &= \mathbf{g}\Big(t_0, t_2, \mathbf{x}(t_0), \mathbf{u}_{[t_0, t_2]}\Big)\\
>  &= \mathbf{g}\Big(t_1, t_2, \mathbf{x}(t_1), \mathbf{u}_{[t_1, t_2]}\Big) \\
>  &= \mathbf{g}\Big(t_1, t_2, \mathbf{g}\big(t_0, t_1, \mathbf{x}(t_0), \mathbf{u}_{[t_0, t_2]}\big), \mathbf{u}_{[t_0, t_2]}\Big) \tag{Semigroup Property}
>  \end{align}$$
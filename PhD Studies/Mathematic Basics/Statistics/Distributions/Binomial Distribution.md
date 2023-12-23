---
aliases:
- Binomial Distribution
---

>[!source]
>Page 47
>PDF: [PDF](grimmett1986.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@grimmett1986)

>[!introduction]
>The binomial distribution acts on a **binary random variable** and is an extension of the [[Binomial Distribution]], where an experiment is repeated $n$ times.

>[!def]
>The probability mass function $f: \mathbb{R} \rightarrow [0,1]$ is given as
>$$\begin{align} f(x;n,p) &= \binom{n}{x}p^x q^{n-x}\end{align}$$
>with 
>
| Variable | Meaning                                     |
| -------- | ------------------------------------------- |
| $x$      | number of times $p$ occurs                  |
| $p$      | probability that $x$ occurs, i.e. $f(x)=p$  |
| $n$      | number of times the experiment is performed |
>and $f(x) = 0$ if $x < 0$

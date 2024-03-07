>[!Source]
>Page 113
>PDF: [PDF](../../../PDFs/bishop2006.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@bishop2006)

>[!notation]
| Variable                                                 | Meaning                                                   |
| -------------------------------------------------------- | --------------------------------------------------------- |
| $f(\mathbf{x})$     | probability distribution for random variable $\mathbf{x}$ |
| $f_B(\mathbf{x;p})$                                      | Bernoulli distribution with $f(\mathbf{x})=p$ |
| $\set{\mathbf{x}_1, \mathbf{x}_2, \ldots, \mathbf{x}_N}$ | finite set of observations                                  |

>[!def] Definition Bernoulli Distribution
> See [[../../Mathematic Basics/Statistics/Distributions/Bernoulli Distribution|Bernoulli Distribution]]
>>The distribution can be given as
>>$$ f_B(\mathbf{x};p) = p^\mathbf{x}(1-p)^{\mathbf{1}-\mathbf{x}}$$

>[!Derivation]
>$$ \begin{align}f_B(\mathbf{x};p) &= p^\mathbf{x}(1-p)^{\mathbf{1}-\mathbf{x}} \\ 
>								&= \exp\Big[\text{ln}\left(p^\mathbf{x}(1-p)^{\mathbf{1}-\mathbf{x}}\right)\Big] \tag*{exponentional of logarithm}\\ 
>								&= \exp\Big[\text{ln}\left(p^\mathbf{x}\right) + \text{ ln}\left((1-p)^{\mathbf{1}-\mathbf{x}}\right)\Big] \tag*{logarithm law}\\
>								&= \exp\Big[\mathbf{x}\text{ ln}(p) + (\mathbf{1}-\mathbf{x})\text{ ln}(1-p)\Big] \tag*{logarithm law}\\
>								&=\exp\Big[\mathbf{x}\text{ ln}(p) + \text{ ln}(1-p) - \mathbf{x}\text{ ln}(1-p)\Big] \\
>								&=\exp\Bigg[\mathbf{x}\text{ ln}(p) + \text{ ln}(1-p) + \mathbf{x}\text{ ln}\left(\frac{1}{1-p}\right)\Bigg] \tag*{logarithm law}\\
>								&=\exp\Bigg[\text{ ln}(1-p) + \mathbf{x}\text{ ln}\left(\frac{p}{1-p}\right)\Bigg] \tag*{logarithm law} \\
>								&=(1-p)\exp\Bigg[\mathbf{x}\text{ ln}\left(\frac{p}{1-p}\right)\Bigg] \tag*{exponential of logarithm}
>								\end{align}$$

>[!def] Definition Exponential Family of Distributions
>The exponential family of distributions over $\mathbf{x}$ given parameters $\eta$ is given as
>$$f(\mathbf{x}; \eta) = h(\mathbf{x})g(\mathbf{\eta}) \exp\left[\mathbf{\eta}^T \mathbf{u}(\mathbf{x})\right]$$
>with
>
| Parameter                | Meaning                                                                                                                                                                               |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $\mathbf{\eta}$          | natural parameters of the probability distribution like in $f_B(\mathbf{x}) = p$ <br>the parameter $p$ is a natural parameter of the Bernoulli distribution, i.e. $f_B(\mathbf{x};p)$ |
| $g(\mathbf{\eta})$       | normalization parameter, i.e. $g(\mathbf{\eta})\int h(\mathbf{x}) \exp\left[\mathbf{\eta}^T \mathbf{u}(\mathbf{x})\right] \text{d}\mathbf{x}=1$                                       |
| $h(\mathbf{x})$          | function of observations $\mathbf{x}$                                                                                                                                                 |
| $\mathbf{u}(\mathbf{x})$ | statistics of the distribution                                                                                                                                                                                      |

>[!observation]
> We can identify the parameters of the _exponential family of distributions_ from the reformulated Bernoulli distribution $f_B$
> $$f(\mathbf{x}; \eta) = h(\mathbf{x})g(\mathbf{\eta}) \exp\left[\mathbf{\eta}^T \mathbf{u}(\mathbf{x})\right]$$
>
| Parameter                | Identification                           |
| ------------------------ | ---------------------------------------- |
| $\eta$                   | $= \text{ln}\left(\frac{p}{1-p}\right)$ |
| $\mathbf{u}(\mathbf{x})$ | $= \mathbf{x}$                           |
| $h(\mathbf{x})$          | $= 1$                                    |
| $g(\eta)$                | $= \sigma(-\eta)$                        | 
>
>_Note $\sigma$ will be defined next_

>[!Derivation] 
> We reformulate the observation of the natural parameters $\eta$ as a mapping $\sigma: \eta \mapsto \sigma(\eta)$
> $$\begin{align}
> 	\eta &= \text{ ln}\left(\frac{p}{1-p}\right) \tag*{| $\exp(\;)$} \\
> 	\exp(\eta) &= \frac{p}{1-p} \tag*{| $(\;)^{-1}$} \\
> 	\frac1{\exp(\eta)} &= \frac{1}{p} - 1 \\
> 	\frac1{\exp(\eta)} +1 &= \frac{1}{p} \\
> 	\frac{1 + \exp(\eta)}{\exp(\eta)} &= \frac{1}{p} \tag*{| $(\;)^{-1}$} \\
> 	\frac{\exp(\eta)}{1 + \exp(\eta)} &= p \\
> 	\frac{\exp(\eta) \cdot \exp{(-\eta})}{(1 + \exp(\eta))\cdot\exp{(-\eta})} &= p \\
> 	\frac{1}{1 + \exp(-\eta)} &= p \\
> \end{align}$$
> We identify
> $$\sigma(\eta) = \frac{1}{1 + \exp(-\eta)} $$

>[!Property]
>$$ \begin{align} \sigma(-\eta) = 1 - \sigma(\eta)\end{align}$$
>>[!proof]
>>It must hold $\sigma(-\eta) + \sigma(\eta) =1$
>>$$ \begin{align} 1  &= \sigma(-\eta) + \sigma(\eta)  \\
>>					&=  \frac{1}{1 + \exp(\eta)} + \frac{1}{1 + \exp(-\eta)} \\
>>					&= \frac{1}{1 + \exp(\eta)} + \frac{\exp{(\eta)}}{(1 + \exp(-\eta))\cdot \exp{(\eta)}} \\
>>					&= \frac{1}{1 + \exp(\eta)} + \frac{\exp{(\eta)}}{1 + \exp(\eta)} \\
>>					&= \frac{1 + \exp(\eta)}{1 + \exp(\eta)} \\
>>					&= 1 \tag*{$\square$}
>>					\end{align} $$
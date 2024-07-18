>[!important] xLSTM Objectives
> 1. LSTM **<u>struggle to revise</u>** stored information
> 2. Cell states are of the form of scalars which <u>**limits memory**</u> of cells greatly
> 3. LSTM are <u>**not parallelizable**</u> 

>[!algo] Architecture xLSTM
>xLSTM is a stacked architecture composed arbitrarily out of
>- sLSTM blocks
>- mLSTM blocks
>
>with skip connections
>![[Figures/xLSTM_stacked_blocks.png]]


## sLSTM (scalar LSTM)

>[!algo] Architecture sLSTM ([[../../../../PDFs/beck2024.pdf|Source]])
> Denote at time $t$ for input $\mathbf{x} \in \mathbf{R}^n$ with LSTM hidden dimensionality $1$
> 
>| States                     | Gates                 | Weights |
>| -------------------------- | --------------------- | ------- |
>| $c_t \in \mathbb{R}$ - cell state         | $z_{t}\in \mathbb{R}$ - cell input  | $\mathbf{w}_{z,i,f,o}\in \mathbb{R}^n$ - input weights for respective gates        |
>| $h_{t}\in \mathbb{R}$ - hidden state     | $f_{t}\in \mathbb{R}$ - forget gate |  $r_{z,i,f,o}\in \mathbb{R}$ - cell weights for respective gates       |
>| $n_{t}\in \mathbb{R}$ - normalizer state | $i_{t}\in \mathbb{R}$ - input gate  |  $b_{z,i,f,o}\in \mathbb{R}$ - biases for respective gates       |
>| $m_{t}\in \mathbb{R}$ - stabilizer state | $o_{t}\in \mathbb{R}$ - output gate |  $\phi$ - activation function, usually $\tanh$       |
> 
> ![[Figures/sLSTM_raw.png|center|700]]
> <center> Figure: sLSTM without stabilization but with introduced exponential "activation functions" </center>
> 
>>[!note]- Note on Hidden Dimensionality
>>If the hidden dimensionality $d$ is greater than $1$ all scalars turn into vectors and the input weight $\mathbf{w}$ becomes a matrix $\mathbf{W} \in \mathbb{R}^{n \times d}$ and the cell weight becomes a matrix too $\mathbf{R} \in \mathbb{R}^{n \times d}$.
>
>>[!note] Note: exponential function is used as activation function
>
>>[!danger] The exponential function can blow up, stabilization and normalization is needed!
>
>![[Figures/sLSTM_stabilized.png]]
><center> Figure: sLSTM with stabilization to prevent overflow produced by the exponential "activation functions".</center>
>
>>[!remark] Remark on the Need of the Exponential Gate
>>Note, the exponential "activation function" is used instead of the sigmoid activation function (or $\tanh$ respectively).
>>
>>![[Figures/sLSTM_exponential_vs_sigmoid.png]]
>><center> Figure: The sigmoid function in green and the exponential function in orange </center>
>>
>> We want to emphasize on the fact, that the sigmoid function converges to one as we approach $\infty$. This means in consequence, $\forall a,b \in \mathbb{R}_{0}^+$ with $a<b$ and any arbitrary positive constant $\gamma \in \mathbb{R}^+$ we get
>> $$\Big\lvert \;\sigma([a,b]) \;\Big\rvert> \Big\lvert \;\sigma([a+\gamma, b+\gamma])\; \Big\rvert  $$
>> while
>> $$\Big\lvert\; \exp([a,b]) \;\Big\rvert < \Big\lvert\; \exp([a+\gamma, b+\gamma])\; \Big\rvert $$
>> where $\lvert \cdot \rvert$ denotes the length of the interval.
>>
>>Conceptually, this means weights at time $t$ can be learned such that input-weights $\mathbf{w}_{i}$ can increase the "input-incentive" for higher-valued mappings produced by the weight vectors. This is established by the fact that the difference between two higher values is greater using the exponential function, while the difference becomes increasingly small using the sigmoid function, as illustrated earlier.
>>
>>Therefore, if an input is very interesting for our learning task, it can **revise storage decisions** by overriding previously learned information with values which resemble the importance.
>
>>[!remark] Remark on Memory Mixing
>>Usually not single scalars are passed through an LSTM network, but instead a collection of scalars in the form of a vector are passed, such that all states are represented as vectors, i.e. $\mathbf{c,h,f,i,z,o} \in \mathbb{R}^d$ and bias $\mathbf{b} \in \mathbb{R}^d$. Hence, the recurrent weight $r_{t}$ is then represented as a **matrix** $\mathbf{R}_{t} \in \mathbb{R}^{d \times d}$.
>>
>>The states $h_{t}$, respectively $\mathbf{h}_{t}$, are responsible for the output of the single LSTM recurrent cells. They can also be referred as the memory of some LSTM cell at time $t$. **Memory Mixing** is referred as the ability to share memory across different context entries in the hidden state $\mathbf{h}_{t}$. This means, by calculating $\mathbf{R}\mathbf{h}_{t-1}$, we mix all memory entries with each other. This is similar to full-fledged [[../Attention/Sparse Attention#^2d06b4|attention]].
>>
>> sLSTM introduces an improvement in memory mixing inspired by transformers and [[../Attention/Sparse Attention|sparse attention]], especially [[../Attention/Sparse Attention#^62e8a4|sparse block attention]], where the region of interest is focussed on the blockdiagonal of the recurrent matrix $\mathbf{R}_{t}$. These blocks are simply called **heads**. The hidden embedding vector $\mathbf{h}_{t}$ is therefore interpreted as some input sequence on which attention can be performed on. By defining some amount of **recurrent heads**, the granularity of the blockdiagonal is defined with $d_{head}=\dfrac{d}{\text{head}_{\text{num}}}$, where greater $d_{head}$ imply more memory mixing and thus more computation.
>> 
>> ![[Figures/sLSTM_memory_mixing_heads.png]]
>> 
>> Therefore, the authors mention that memory mixing within a 

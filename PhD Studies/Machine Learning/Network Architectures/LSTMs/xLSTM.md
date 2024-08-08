>[!source]
>Source: [[../../../../PDFs/beck2024.pdf|beck2024]]

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
>![[Figures/xLSTM_stacked_blocks.png|center|400]]
><center>Figure: Stacked xLSTM network consisting of sLSTM and mLSTM blocks </center>


## sLSTM (Scalar LSTM)

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
> ![[Figures/sLSTM_raw.png|center]]
> <center> Figure: sLSTM without stabilization but with introduced exponential "activation functions" </center>
>
><u>Scalar Version</u>
> $$\begin{alignat}{3}
> c_{t} &= f_{t}c_{t-1} + i_{t}z_{t} \qquad \tag{cell state} \\ 
> n_{t} &= f_{t}n_{t-1}+i_{t} \tag{normalizer state} \\
> h_{t} &= o_{t}\widetilde{h}_{t} && \widetilde{h}_{t} &&= \frac{c_{t}}{n_{t}} \tag{hidden state}\\
> z_{t} &= \phi(\widetilde{z}_{t}) && \widetilde{z}_{t}&&= \mathbf{w}_{z}^T\mathbf{x}_{t} + r_{z}h_{t-1}+b_{z} \tag{cell input}\\
> i_{t} &= \exp(\widetilde{i}_{t}) && \widetilde{i}_{t}&&= \mathbf{w}_{i}^T\mathbf{x}_{t} + r_{i}h_{t-1}+b_{i} \tag{input gate}\\
> f_{t}&= \sigma(\widetilde{f}_{t}) \text{ OR }\exp(\widetilde{f}_{t})\qquad && \widetilde{f}_{t}&&= \mathbf{w}_{f}^T\mathbf{x}_{t} + r_{f}h_{t-1}+b_{f} \tag{forget gate} \\
> o_{t} &= \sigma(\widetilde{o}_{t}) && \widetilde{o}_{t}&&= \mathbf{w}_{o}^T\mathbf{x}_{t} + r_{o}h_{t-1}+b_{o} \tag{output gate} \\ 
> m_{t} &= \underset{}{\text{max}}\Big(\log(f_{t})+m_{t-1}, \log(i_{t})\Big) \tag{stabilizer gate}\\
> i^\prime_{t} &= \exp\Big(\log(i_{t})-m_{t}\Big) = \exp(\widetilde{i}_{t}-m_{t}) \tag{stabil. input gate} \\
> f'_{t} &= \exp(\log(f_{t})+m_{t-1}-m_{t}) \tag{stabil. forget gate}
>\end{alignat}$$
> 
><u>Multi-Scalar/Vector Version</u> 
> 
> $$\begin{alignat}{3}
> \mathbf{c}_{t} &= \mathbf{f}_{t}\odot\mathbf{c}_{t-1} + \mathbf{i}_{t}\odot\mathbf{z}_{t} \qquad \tag{cell state} \\ 
> \mathbf{n}_{t} &= \mathbf{f}_{t}\odot n_{t-1}+\mathbf{i}_{t} \tag{normalizer state} \\
> \mathbf{h}_{t} &= \mathbf{o}_{t}\odot\widetilde{\mathbf{h}}_{t} && \widetilde{\mathbf{h}}_{t} &&= \mathbf{c}_{t}\odot \mathbf{n}_{t}^{-1} \tag{hidden state}\\
> \mathbf{z}_{t} &= \phi(\widetilde{\mathbf{z}}_{t}) && \widetilde{\mathbf{z}}_{t}&&= \mathbf{W}_{z}\mathbf{x}_{t} + \mathbf{R}_{z}\mathbf{h}_{t-1}+\mathbf{b}_{z} \tag{cell input}\\
> \mathbf{i}_{t} &= \exp(\widetilde{\mathbf{i}}_{t}) && \widetilde{\mathbf{i}}_{t}&&= \mathbf{W}_{i}\mathbf{x}_{t} + \mathbf{R}_{i}\mathbf{h}_{t-1}+\mathbf{b}_{i} \tag{input gate}\\
> \mathbf{f}_{t}&= \sigma(\widetilde{\mathbf{f}}_{t}) \text{ OR }\exp(\widetilde{\mathbf{f}}_{t})\qquad && \widetilde{\mathbf{f}}_{t}&&= \mathbf{W}_{f}\mathbf{x}_{t} + \mathbf{R}_{f}\mathbf{h}_{t-1}+\mathbf{b}_{f} \tag{forget gate} \\
> \mathbf{o}_{t} &= \sigma(\widetilde{\mathbf{o}}_{t}) && \widetilde{\mathbf{o}}_{t}&&= \mathbf{W}_{o}\mathbf{x}_{t} + \mathbf{R}_{o}\mathbf{h}_{t-1}+\mathbf{b}_{o} \tag{output gate} \\ 
> \mathbf{m}_{t} &= \underset{}{\text{max}}\Big(\log(\mathbf{f}_{t})+\mathbf{m}_{t-1}, \log(\mathbf{i}_{t})\Big) \tag{stabilizer gate}\\
> \mathbf{i}^\prime_{t} &= \exp\Big(\log(\mathbf{i}_{t})-\mathbf{m}_{t}\Big) = \exp(\widetilde{\mathbf{i}}_{t}-\mathbf{m}_{t}) \tag{stabil. input gate} \\
> \mathbf{f}'_{t} &= \exp(\log(\mathbf{f}_{t})+\mathbf{m}_{t-1}-\mathbf{m}_{t}) \tag{stabil. forget gate}
>\end{alignat}$$
> 
>>[!note] Note on Hidden Dimensionality
>>If the hidden dimensionality $d$ is greater than $1$ all scalars turn into vectors and the input weight $\mathbf{w}$ becomes a matrix $\mathbf{W} \in \mathbb{R}^{n \times d}$ and the cell weight becomes a matrix too $\mathbf{R} \in \mathbb{R}^{n \times d}$. The entries of the state vectors are treated as a collection of scalars, this can easily be seen since all operations are done elementwise, see Hadamard-product and vector addition.
>
>>[!note] Note: exponential function is used as activation function
>
>>[!danger] The exponential function can blow up, stabilization and normalization is needed!
>
>![[Figures/sLSTM_stabilized.png]]
><center> Figure: sLSTM with stabilization to prevent overflow produced by the exponential "activation functions".</center>

>[!remark] Remark on the Need of the Exponential Gate
>Note, the exponential "activation function" is used instead of the sigmoid activation function (or $\tanh$ respectively).
>
>![[Figures/sLSTM_exponential_vs_sigmoid.png|center|450]]
><center> Figure: The sigmoid function in green and the exponential function in orange </center>
>
> We want to emphasize on the fact, that the sigmoid function converges to one as we approach $\infty$. This means in consequence, $\forall a,b \in \mathbb{R}_{0}^+$ with $a<b$ and any arbitrary positive constant $\gamma \in \mathbb{R}^+$ we get
> $$\Big\lvert \;\sigma([a,b]) \;\Big\rvert> \Big\lvert \;\sigma([a+\gamma, b+\gamma])\; \Big\rvert  $$
> while
> $$\Big\lvert\; \exp([a,b]) \;\Big\rvert < \Big\lvert\; \exp([a+\gamma, b+\gamma])\; \Big\rvert $$
> where $\lvert \cdot \rvert$ denotes the length of the interval.
>
>Conceptually, this means weights at time $t$ can be learned such that input-weights $\mathbf{w}_{i}$ can increase the "input-incentive" for higher-valued mappings produced by the weight vectors. This is established by the fact that the difference between two higher values is greater using the exponential function, while the difference becomes increasingly small using the sigmoid function, as illustrated earlier.
>
>Therefore, if an input is very interesting for our learning task, it can **revise storage decisions** by overriding previously learned information with values which resemble the importance.

>[!remark] Remark on Memory Mixing
>Usually not single scalars are passed through an LSTM network, but instead a collection of scalars in the form of a vector are passed, such that all states are represented as vectors, i.e. $\mathbf{c,h,f,i,z,o} \in \mathbb{R}^d$ and bias $\mathbf{b} \in \mathbb{R}^d$. Hence, the recurrent weight $r_{t}$ is then represented as a **matrix** $\mathbf{R}_{t} \in \mathbb{R}^{d \times d}$.
>
>The states $h_{t}$, respectively $\mathbf{h}_{t}$, are responsible for the output of the single LSTM recurrent cells. They can also be referred as the memory of some LSTM cell at time $t$. **Memory Mixing** is referred as the ability to share memory across different context entries in the hidden state $\mathbf{h}_{t}$. This means, by calculating $\mathbf{R}\mathbf{h}_{t-1}$, we mix all memory entries with each other. This is similar to full-fledged [[../Attention/Sparse Attention#^2d06b4|attention]].
>
> sLSTM introduces an improvement in memory mixing inspired by transformers and [[../Attention/Sparse Attention|sparse attention]], especially [[../Attention/Sparse Attention#^62e8a4|sparse block attention]], where the region of interest is focussed on the blockdiagonal of the recurrent matrix $\mathbf{R}_{t}$. These blocks are simply called **heads**. The hidden embedding vector $\mathbf{h}_{t}$ is therefore interpreted as some input sequence on which attention can be performed on. By defining some amount of **recurrent heads**, the granularity of the blockdiagonal is defined with $d_{head}=\dfrac{d}{\text{head}_{\text{num}}}$, where greater $d_{head}$ imply more memory mixing and thus more computation.
> 
> ![[Figures/sLSTM_memory_mixing_heads.png|center|400]]
> <center> Figure: Recurrent matrix weight for standard LSTM on the <b>left</b> and blockdiagonal recurrent matrix for sLSTM on the <b>right</b> </center>
> 
> **The new memory mixing saves memory consumption by optimizing the learning strategy.**

>[!remark] Remark on Computation
>Since sLSTM still uses recurrency, it lacks the ability to be parallized.

## mLSTM (Memory LSTM)

>[!algo] Architecture
>$$\begin{alignat}{2}
> \mathbf{C}_{t} &= f_{t} \mathbf{C}_{t-1} + i_{t}\mathbf{v}_{t}\mathbf{k}_{t}^T \qquad\tag{cell state} \\
> \mathbf{n}_{t} &= f_{t}\mathbf{n}_{t-1} + i_{t}\mathbf{k}_{t} \tag{normalizer state} \\
> \mathbf{h}_{t} &= \mathbf{o}_{t} \odot \widetilde{\mathbf{h}}_{t} & \widetilde{\mathbf{h}}_{t} &= \frac{\mathbf{C}_{t}\mathbf{q}_{t}}{\underset{}{\text{max}}\Big(\Big\vert \mathbf{n}_{t}^T\mathbf{q}_{t}\Big\vert, 1\Big)\;} \tag{hidden state} \\
> \mathbf{q}_{t} &=\mathbf{W}_{q}\mathbf{x}_{t} + \mathbf{b}_{q} \tag{query input} \\
> \mathbf{k}_{t} &= \frac{1}{\sqrt{ d }}\mathbf{W}_{k} \mathbf{x}_{t} +\mathbf{b}_{k} \tag{key input} \\
> \mathbf{v}_{t} &= \mathbf{W}_{v}\mathbf{x}_{t} +\mathbf{b}_{v} \tag{value input}\\
> i_{t} &= \exp(\widetilde{i}_{t}) & \widetilde{i} &= \mathbf{w}_{i}^T \mathbf{x}_{t} + b_{i} \tag{input gate}\\
> f_{t} &= \sigma(\widetilde{f}_{t}) \text{ OR } \exp(\widetilde{f}_{t}) &\widetilde{f}_{t}&=\mathbf{w}_{f}^T \mathbf{x}_{t}+b_{f} \tag{forget gate}\\
> \mathbf{o}_{t} &= \sigma(\widetilde{\mathbf{o}}_{t}) &\widetilde{\mathbf{o}}_{t} &= \mathbf{W}_{\mathbf{o}}\mathbf{x}_{t} +\mathbf{b}_{\mathbf{o}} \tag{output gate}
>\end{alignat}$$

>[!remark] Remark on the Cell States
><u>Correlation Matrix and Memory</u>
>
> The cell state resembles a correlation matrix and is of the form of an [[../Associative Memory/Associative Memory Terminology|associative memory]], especially [[../Associative Memory/Correlation Matrix Memories|correlation matrix memories (CMM)]]. The correlation matrix is an extension of the scalar memory and upgraded to an associative memory.
> 
> According to [[../../../../PDFs/anderson1977.pdf|anderson1977]] the correlation matrix is of the form
>>[!def]- Definition Correlation Matrix $\mathbf{A}$ according to Anderson 1977
>>Let $\mathbf{f}_{i},\mathbf{g}_{i}\in\mathbb{R}^n$ denote two patterns and give the $i$-th association $(\mathbf{f}_{i}, \mathbf{g}_{i})$. Further, assume $\lvert\lvert f \rvert\rvert = 1.$ Then the correlation matrix over the two patterns can be given as
>>$$\begin{align}
>> \mathbf{A}_{1} &= \mathbf{f}_{1}\mathbf{g}_{1}^T \\
>> \mathbf{A}_{i} &= \mathbf{A}_{i-1} + \mathbf{f}_{i}\mathbf{g}_{i}^T
>>\end{align}$$
>>where a pattern can be retrieved for a query $\mathbf{g}_{i}$
>>$$\mathbf{A}\mathbf{f}_{i} =\mathbf{g}_{i}$$
>
><u>Memory Creation </u>
>
>The memory $\mathbf{C}_{t}$ at time step $t$ is the sum of the by the forget gate scaled previous memory $\mathbf{C}_{t-1}$ and the input scaled new correlation $\mathbf{v}_{t}\mathbf{k}_{t}^T$ created by some value and key vectors $\mathbf{v}, \mathbf{k} \in \mathbb{R}^n$. Value and key vectors are learned over the input sequence by weight matrices $\mathbf{W}_{q},\mathbf{W}_{k}$.
>
><u>Output Creation</u>
>
>For generating the output a query retrieves over time stored information from the correlation matrix by calculating
>$$\mathbf{C}_{t}\mathbf{q}_{t}$$
>expecting a similar output as designed by [[../../../../PDFs/anderson1977.pdf|anderson1977]] and [[../../../../PDFs/kohonen1972.pdf|kohonen1972]] (see above). The retrieved information is inversely scaled by the dotproduct of the query and normalizer vectors $\mathbf{n}_{t}^T\mathbf{q}_{t}$ but at most $1$, i.e.
>$$\widetilde{\mathbf{h}}_{t} = \frac{\mathbf{C}_{t}\mathbf{q}_{t}}{\underset{}{\text{max}}\Big(\Big\vert \mathbf{n}_{t}^T\mathbf{q}_{t}\Big\vert, 1\Big)\;}$$
> This dot-product is a cumulative, scaled dot-product of key and query vectors $\mathbf{k}$ and $\mathbf{q}$ scaled by the input and forget gate, i.e.
>$$\mathbf{n}_{t} = f_{t}\mathbf{n}_{t-1} + i_{t}\mathbf{k}_{t}$$
>The output is a element-wise product with the output-gate and the hidden state
>$$\mathbf{h}_{t} = \mathbf{o}_{t} \odot \widetilde{\mathbf{h}}_{t}$$

>[!remark] Remark on Recursion and Parallel Computation
> The algorithm can be run in full parallel. Note, that **the input and forget gate** can be computed without recursive information $\mathbf{h}_{t-1}$ contrary to sLSTM and vanilla LSTM.
> $$\begin{align}
> i_{t} &= \exp(\widetilde{i}_{t}) & \widetilde{i} &= \mathbf{w}_{i}^T \mathbf{x}_{t} + b_{i} \tag{input gate}\\
> f_{t} &= \sigma(\widetilde{f}_{t}) \text{ OR } \exp(\widetilde{f}_{t}) &\widetilde{f}_{t}&=\mathbf{w}_{f}^T \mathbf{x}_{t}+b_{f} \tag{forget gate}\\
>\end{align}$$
>All input and forget gates can therefore be computed immediately
>$$\begin{align} \\
> \mathbf{F}_{ij} &= \begin{cases}
> 0 & \text{ for } j > i \\
> 1 & \text{ for } j = i  \\
> \prod_{k=j+1}^i \sigma(\widetilde{f}_{k}) & \text{ for } j \leq i
>\end{cases} \\[1em]
> \mathbf{F} &= \begin{pmatrix}
> 1 & 0 & 0 & 0 & \dots & 0 & 0 \\
> \sigma(\widetilde{f}_{2}) & 1 & 0 & 0 & \dots & 0 & 0 \\
> \sum_{k=2}^3\sigma(\widetilde{f}_{i}) & \sigma(\widetilde{f}_{3}) & 1 & 0 & \dots & 0 & 0 \\
> \sum_{k=2}^4\sigma(\widetilde{f}_{i}) & \sum_{k=3}^4\sigma(\widetilde{f}_{i}) & \sigma(\widetilde{f}_{4}) & 1 & \dots & 0 & 0 \\
> \vdots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
> \sum_{k=2}^{T-1}\sigma(\widetilde{f}_{i}) & \sum_{k=3}^{T-1}\sigma(\widetilde{f}_{i}) & \sum_{k=4}^{T-1}\sigma(\widetilde{f}_{i}) & \sum_{k=5}^{T-1}\sigma(\widetilde{f}_{i}) & \dots & 1 & 0 \\
> \sum_{k=2}^{T}\sigma(\widetilde{f}_{i}) & \sum_{k=3}^{T}\sigma(\widetilde{f}_{i}) & \sum_{k=4}^{T}\sigma(\widetilde{f}_{i}) & \sum_{k=5}^{T}\sigma(\widetilde{f}_{i}) & \dots & \sigma(\widetilde{f}_{T}) & 1 \\
>\end{pmatrix} \\[1em]
> \mathbf{\widetilde{I}}_{ij} &= \begin{cases}
> 0 & \text{ for } j > i \\
> i_{j} & \text{ for } j \leq i
>\end{cases}  \tag{error in paper?}\\[1em]
>\mathbf{\widetilde{I}} &= \begin{pmatrix}
> \widetilde{i}_{1} & 0 & 0 & \dots & 0 \\
> \widetilde{i}_{1} & \widetilde{i}_{2} &0& \dots & 0 \\
> \widetilde{i}_{1} & \widetilde{i}_{2} & \widetilde{i}_{3}& \dots & 0 \\
>\vdots & \vdots & \vdots & \ddots & \vdots \\
>\widetilde{i}_{1} & \widetilde{i}_{2} & \widetilde{i}_{3}& \dots & \widetilde{i}_{T}
>\end{pmatrix}
>\end{align}$$
>
>The unstabilized gate activation can be calculated as
>$$\begin{align}
> \mathbf{D} &= \mathbf{F} \odot \exp(\mathbf{\widetilde{I}})
>\end{align}$$
>and the stabilized gate activation (overflow protection)
>$$\begin{align}
> \mathbf{D} &= \log(\mathbf{F}) \odot \mathbf{\widetilde{I}}
>\end{align}$$
>where the logarithm and exponential are performed element-wise. 
>
>---
>Unclear paper description of $\underset{}{\text{max}}(\mathbf{C})\;$, if this operation yields a matrix, then what does $\exp(-\underset{}{\text{max}}\;\mathbf{\widetilde{D}})$ yield?
>$$\mathbf{C} = \frac{\mathbf{\widetilde{C}}'}{\underset{}{\text{max}}\left( \left\lvert  \sum_{j=1}^T \mathbf{\widetilde{C}}_{ij}  \right\rvert, \exp(-\underset{}{\text{max}}\;\mathbf{\widetilde{D}})  \right)\;}$$
>
>---

>[!tip] Experiments
><center> xLSTM[a:b] <=> <b>a</b> layers of mLSTM and <b>b</b> layers of sLSTM blocks </center>
>
>>[!tip] Experiment Language Task with State Tracking
>> ![[Figures/experiment_1.png|center]]
>
>>[!tip] Experiment Associative Recall
>>
>>>[!example] Task Associative Recall
>>>In an *Associative Recall* experiment a model receives a corrupted pattern and is expected to return the fully recovered pattern. 
>>
>>![[Figures/experiment_2.png|center]]
>>
>>The *KV Pair* distinction is concerned with different *Key-Value pairs* where key is a corrupted pattern and value the expected recovered pattern.  
>
>>[!tip] Experiment Next Token Prediction
>>![[Figures/experiment_4.png|center]]
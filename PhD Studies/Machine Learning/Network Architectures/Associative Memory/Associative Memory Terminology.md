>[!source]
>Source: [[../../../../PDFs/gritsenko2017.pdf|gritsenko2017]]
>Source: [[../../../../PDFs/prasad2012.pdf|prasad2012]]

>[!observation] Observation: Hebb's Learning
>---
><center>Neurons that fire together, wire together.</center>
>
>---
><p align="right" style="font-family:cursive"><i>Donalb E. Hebb</i></p>
>
>>[!tip] Brain's Architecture
>>- nerve cells are densely interconnected by **excitatory connections**
>>=> **Neural Network**
>>
>>![[Figures/neural_network_biological.png|center|200]]
>><center> Figure: Illustrative Neural Network </center>
>
>>[!tip] Neuronal Mechanics
>>- each **<u>neuron's membrane potential**</u> is determined by the sum of the output of other neurons weighted by the connection strength 
>>- neurons become **<u>active</u>** if their membrane potential exceeds a threshold
>>- more **<u>simultaneous activity</u>** between neurons strengthens their connection **(Hebb's rule)**
>>=> **cell assemblies are organized** (neurons sharing strong connections)
>>	- if a sufficient collection of neurons of a cell assembly is being activated, the whole assembly will be activated
>>
>>---
>><center>Cell assemblies may be regarded as <b><u>memorized representations</u></b> of items encoded by the distributed patterns of active neurons.</center>
>>
>>---
>
>>[!tip] Biological Interpretation
>>Assembly activation may be regarded as **<u>pattern completion</u>** or **<u>associative information retrieval</u>** of similar patterns stored by the cell assemblies from noisy or incomplete inputs.
>>
>>Memory is not stored as in specific locations but rather is associated with a collection of neurons.

>[!def] Definition Associative Memory/Content-Adressable Memory (CAN)
>A content-addressable memory is a type of memory that allows for the recall of data based on the degree of similarity between the input pattern and the patterns stored in memory. 
>
>Let $(A_{i}, B_{i})$ denote a programmed memory where $B_{i}$ is called **association of**  of some pattern $A_{i}$. A matrix $\mathbf{W}$ encodes the given associations $(A_{i},B_{i})^Q_{i-1}$. 
>>[!remark]
>>It refers to a memory organization in which the memory is accessed by
>>its content as opposed to an explicit address like in the traditional computer memory system. Therefore, this type of memory allows the recall of information based on partial knowledge of its contents. 



>[!def] Definition Auto-Associative Memory
> Let $(A_{i},B_{i})$ denote a programmed memory for which a matrix $\mathbf{W}$ encodes the given associations, then the model is an **auto-associative** memory if $A_{i} = B_{i}$.
>>[!remark]- Remark on the Association Matrix $\mathbf{W}$
>>As a consequence $\mathbf{W} \in \mathbb{R}^{n \times n}$ is a quadratic matrix, since both patterns are of the same dimensionality.

>[!def] Definition Hetero-Associative Memory
> Let $(A_{i},B_{i})$ denote a programmed memory for which a matrix $\mathbf{W}$ encodes the given associations, then the model is an **auto-associative** memory if $A_{i}$ and $B_{i}$ are of different spaces.
>>[!remark]- Remark on the Association Matrix $\mathbf{W}$
>>As a consequence $\mathbf{W} \in \mathbb{R}^{n \times n}$ is likely a non-quadratic matrix, since both patterns are of different space.
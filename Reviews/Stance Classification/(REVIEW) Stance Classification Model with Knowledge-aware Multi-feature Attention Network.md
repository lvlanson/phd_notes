# 1 - Introduction

![[../../Excalidraw/(REVIEW) Stance Classification Model with Knowledge-aware Multi-feature Attention Network 2023-12-04 16.29.58.excalidraw|1100]]

>[!example]
> 1. `I will fight for the unborn!` 
> **Target**: \[Legalization of Abortion] <-> **Stance**: \[AGAINST] 
> 2. `The government has given no explanation of why the law was changed macedonia hrctte`
> **Target**: \[Legalization of Abortion] <-> **Stance**: \[AGAINST] 
> 3. `It very simple let women choose repealthe8th notacriminal`
> **Target**: \[Legalization of Abortion] <-> **Stance**: \[FAVOR] 


- <u>Topic:</u> Opinion Mining -> rumor detection, community detection, election prediction etc.
- <u>Problem:</u> Feature Extraction, i.e. labeling
- <u>Past Efforts:</u> There have been models (CNN/RNN), with unsatisfactory success
- <u>Recent Efforts:</u> Further some attention based models have been utilized, improved performance but also with unsatisfactory success
- <u>Ansatz:</u> Creating a model which utilizes feature extraction on the targets to correlate the text to the target
	1. knowledge extractor → training to extract knowledge from the text with respect to the target
	2. stance classifier → multi-feature attention network 


### Comments
- This paper proposes a hypothesis \[p. 2, 43.5 left]

# 2 - Related Work

>[!source]
>###### SemEval-2016
>dataset to detect stance of tweets
>-> established twitter as main platform for stance classification


# 3 - Methodology

>[!def]
> Let $Text = [\mathbf{w}_1,\mathbf{w}_2, \ldots, \mathbf{w}_n]$ and $Target = [\mathbf{t}_1, \mathbf{t}_2, \ldots, \mathbf{t}_m]$ with $\mathbf{w}_i, \mathbf{t}_i$ being tokens of words.
>
>_<u>Note:</u> What  $\mathbf{w}_i, \mathbf{t}_i$ mathematically are is not mentioned. This could be an indirect consequence of the use of BERT,  but a clearer description would still be helpful._

>[!def]
> **Learning Stance Features**
> $$TO=BERT(Text) =[T0O,T1O,…,TnO]$$
> **Learning Sentiment Features**
> $$TS=S_BERT(Text) =[T0S,T1S,…,TnS]$$
> **Learning Target Features**
> $$TT=T_BERT(Text) =[T0T,T1T,…,TnT]$$
> with any $T^{(O/S/T)}_i$ being the last hidden state in $BERT$ with respect to word $\mathbf{w}_i$ 

>[!def]
> **Vocabulary**
> $$\begin{align} 
> \text{Voc} &= \text{TF\_IDF}(\set{Text_i \;|\; 0  \leq i \leq N_{\text{train}}})\
> &= \set{w_j \; | \; 0 \leq j \leq L}
> \end{align}$$
> with
>  - $N_{\text{train}}$  the number of training samples 
>  - $L$ the number of words in $\text{Voc}$
>  
>_(Keyword Extraction???)_
>
>**Stance distributed Vocabulary**
> $$\begin{align} \text{Voc}_{SK} = \{w_i \; | \; &0 \leq i \leq L_{SK}, \\
> &n_{i,0} + n_{i,1} + n_{i,2} \geq N, \\
> &max(p_{i,0},p_{i,1},p_{i,2}) \geq P \}\end{align}$$
> with 
> - $L_{SK}$ the number of words in $Voc_{SK}$
> - $n_{i,s}$  being the number a word $w_i$ is appears regarding stance $s$ 
> - 
>
>>[!note]
>>TF-IDF (Frequency-Inverse Document Frequency)
>>Das allgemeine Ziel von TF-IDF ist es, statistisch zu messen, wie wichtig ein Wort in einer Sammlung von Dokumenten ist
>>$$TF\_IDF = TF \cdot IDF$$
>>with 
>>$$\begin{align}
>>\delta(w_1, w_2) &= \begin{cases}1 &\text{ if } w_1 = w_2 \\
>>						 0 &\text{ else } \end{cases} \\
>>\gamma(w, D) &= \begin{cases}1 &\text{ if } w \in D \\
>>							 0 &\text{ else } \end{cases} \\
>>TF(w) &= \frac{\sum_{w_i \in D} \delta(w, w_i)}{|D|} \\
>>IDF(w) &= \log\left(\frac{\sum_{D_i \in C} \gamma(w, D_i)}{|C|}\right)
>>\end{align}$$
>>and $C = \set{D_i}_{i=1}^{|C|}$ being the corpus, $D$ being the documents and $w \in V$ being a word from the vocabulary $V$.
>> $\delta$ returns the number of times a word $w$ occurs in a Document $D$ and 
>> $\gamma$ returns the number of times a word $w$ appears at least one time over all Documents $D \in C$ 

>[!algo]
> **Preprocessing**
> 1. $$\text{target\_classification\_label} = \begin{cases} 1 &\text{ if stance\_label is not None} \\ 0 &\text{ else}\end{cases}$$

>[!Quote]- Quotes - What is BERT?
>##### What is BERT?
>>(...) BERT is designed to pretrain deep bidirectional representations from unlabeled text by jointly conditioning on both left and right context in all layers. As a result, the pre-trained BERT model can be finetuned with just one additional output layer to create state-of-the-art models for a wide range of tasks, such as question answering and language inference, without substantial taskspecific architecture modifications.
>>	-  [[../../Literature/@devlin2019|@devlin2019]]
>
>>BERT’s model architecture is a multi-layer bidirectional Transformer encoder based on the original implementation described in Vaswani et al. (2017)(...).
>
> ![[BERT.png]]

>[!KRITIK]
>  - (p.5 left 1-8) 
> 	- What  $\mathbf{w}_i, \mathbf{t}_i$ mathematically are is not mentioned. This could be an indirect consequence of the use of BERT, but a clearer description would still be helpful. 
> - (p.5 right 37-38)
> 	- What is TF_IDF -> Frequency-Inverse Document Frequency
> 	- How does TF_IDF extract the vocabulary? It should return a weight, not a word
> 
>> Initially, TF_IDF was employed to extract the vocabulary from the training dataset.
>
>    while
>>  Term frequency, $\text{tf}(t,d)$, is the relative frequency of term $t$ within document $d$. ([more here](https://en.wikipedia.org/wiki/Tf%E2%80%93idf))
> - Probably the **keywords** were extracted, but still imprecise description and **imprecise** formula 
> - (p.6 left 41-48)
> 	- description not clear
> - (p.6 right 37-40)
> 	- what is $SKE$ (acronym)?
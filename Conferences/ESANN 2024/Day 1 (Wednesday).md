# 1st Session
### <u>Informed Machine Learning for Complex Data (Overview)</u>

- complex data: images, text, sequences, trees, graphs
- different aspects of domain-specific integration (data, technically (engineering aspects of development), environmentally (energy consumption training), physically, ethically informed)

### <u>Informed Machine Learning: Excess Risk and Generalization</u>

- Tradeoff between maximizing/optimizing certain objectives (easy to formulate) and plausibility+trustworthiness 
- physical knowledge can help to extrapolate knowledge (damped oscillator using physically informed loss)
- there is a tradeoff between errors, the more you information you add regarding the different aspects of learning
	- information, approximation, estimation, optimizer quality
- conclusion: adding information knowledge is not always helpful (computational complexity)
	- sometimes it is better to point the model into the correct direction 
- **<span style="color:#38ffa9">increasing provided information increases approximation error</span>**
### **<span style="color:#f7b8ff"><u>Enchancing Echo State Networks with Gradient-based Explainability Methods</u></span>** 🧠

- explainable AI for time series classification
- echo state networks are used here as neural network
- **<span style="color:#38ffa9">INTERESTING</span>**
	- Gradient 
	- Gradient$\times$Input 
	- **<span style="color:#38ffa9">Gradient SHAP</span>**
- **<span style="color:#f7b8ff">when there is a lot of noise, weight gradient with these techniques to improve performance</span>**
- explainable AI techniques are only used to improve accuracy

### <u>Generalizing Convolution to Point Clouds</u> 💤

- voxel grid ($d$ dimensional boxes - regular) vs point cloud (points - irregular)
- standard convolution can't be applied to point clouds because of the irregular structure
- using offsets to "map" grid from standard convolution to point clouds? (using $k$-nearest neighbor)

### <u></u><u>Towards the Application of Backpropagation-Free Graph Convolutional Networks on Huge Datasets</u>

- Gated Neural Network 
	- training each neuron independently exploiting global error signal
- did not understand properly
- using prototype based approach to reduce computational complexity?

---
# 2nd Session

### **<span style="color:#38ffa9"><u>Machine Learning in distributed, federated and non-stationary environments - recent trends</u></span>** 🧠

- federated learning
	- Advantages:
		- "privacy preservation"
		- efficient resource utilization
		- access to diverse and heterogeneous data and information
	- Disadvantages:
		- non-iid data distributions (label skewness, data quantity skewness, covariate shift)
		- communication cost
	- Advancements:
		- aggregation techniques
		- multi-modal considerations (different model types)
		- fairness (client selection, contribution evaluation)
	- Topics
		- homomorphic encryption
		- differential privacy
		- secure multi-party computation
- non-stationary environments
	- concept drift (changes in data distribution)
	- real time adaption (incremental learning)
	- data scarcity/imbalance

### <u>Sparse Uncertanty-Informed Sampling from Federated Streaming Data</u>

did not really understand where the talk was going, single key-points seemed plausible, but the big picture is not clear

- federated learning:
	- production environment with IoT devices is considered

### <u>On the Fine Structure of Drifting Features</u>

- concept drift: change in distribution of the data
- chain of functions (machinery) change the time series
- this chain can be an a-cyclic graph
- it is difficult to detect which function/machine is causing this in a-cyclic settings
- each machine is interpreted as function, estimating the function can help to determine which function is responsible
- the drift causing feature can be computed using **common feature selection methods**

### <u>Federated Learning with Hyperspherical Prototypical Regularization</u>

- exchanging the whole model across all participants
- each party can have different class distributions which result in exchange and aggregation into worse space segmentation
- FedHP fixes prototypes on a unit-sphere (anchor-points, parametric prototypes)
- FedProto vanilla method
- FedHP new method - does not improve an accuracy, but on communication cost

---
# 3rd Session

### <u>Continual Learning of Deep NeuralNetworks in the Age of Big Data</u> ❓
❓❓❓❓❓❓

### <u>Sequential Continual Pre-Training for Neural Machine Translation</u>

- pretraining language models with masking and shuffling
- drawbacks:
	- lots of computational time is necessary
	- catastrophic forgetting
- incremental pre-training 

---

### <u>Joint Entropy Search for Multi-objective Bayesian Optimization with Constraints und Multiple Fidelities</u>

### <u>Convergence analysis of an inexact gradient method on smooth convex functions</u>


# Session 1

### <u>Trust in Artificial Intelligence: Beyond Interpretability</u> 🧠

- Hybrid system between GMLVQ and Encoder-Decoder Architecture with convolutions
- doing GMLVQ in latent space
- decode eigenvectors with decoder
- lower computational cost in GMLVQ due to Encoder
- less interpretability, goal of project is bringing back interpretability
	- decoding eigenvectors seems to give the difference of prototypes

### <u>ProtoNCD: Prototypical Parts of Interpretable Novel Class Discovery</u>

- taking images and segment them in patches (using CNN)
- classify segments of image
- use classifications to make overall classification AND/OR clustering of unlabeled data 
- new combinations of patch-classes form new prototypes?

### <u>Evaluating the Quality of Saliency Maps for Distilled Convolutional Neural Networks</u>

- model compression
	- pruning and knowledge distillation
		- pruning is removing weights
		- knowledge distillation is having a teacher network and teaching a smaller student network
			- using softmax output of teacher in loss function of student to improve generalization
			- this takes into account, that a more complex model can better emphasize similarity between data points (a dog can be also a cat up to some degree)
	- potential problems
		- robustness
		- spurious correlations
		- biases
- using saliency maps to find out importance of possible importantness
	- masking important parts by confidence and try to correlate with predictions
- coherence of saliency maps
	- check if saliencies are in agreement with domain knowledge

---

# Session 4

### **<span style="color:#38ffa9"><u>Reservoir Memory Networks (RNN type)</u></span>** 🧠

- look paper up
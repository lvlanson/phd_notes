---
aliases:
- pytorch module
- nn.Module
---
>[!attention]
>Run the code below first for importing necessary libraries!
>```python
>from torch import nn
>```


### Structure
```python
class SOMETHING(nn.module):

def __init__(self, *args, **kwargs):
	super().__init__()
	#DEFINE LAYERS HERE

def forward(self, model_input) -> torch.Tensor:
	#DEFINE COMPUTATION HERE
	return #SOLUTION
```

### Example: Linear Regression
```python
class LinearRegressionModel(nn.Module): 
    def __init__(self):
        super().__init__() 
        self.weights = nn.Parameter(torch.randn(1, dtype=torch.float), 
                                    requires_grad=True) 
        self.bias = nn.Parameter(torch.randn(1, dtype=torch.float), 
                                 requires_grad=True) 
                                
    def forward(self, x: torch.Tensor) -> torch.Tensor: 
        return self.weights * x + self.bias 
```
>[!note]
>`nn.Parameter` creates a Tensor meant for training in modules [Doc](https://pytorch.org/docs/stable/generated/torch.nn.parameter.Parameter.html)
>`requires_grad` defines the parameter to be updated
> `forward` defines the computation of the model
> `torch.randn` creates a random scalar of type `torch.float` see [[../Basics/PyTorch Basic Functions#Random Tensor|randn]]
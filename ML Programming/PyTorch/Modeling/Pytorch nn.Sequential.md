---
aliases:
- pytorch sequential
- nn.Sequential
---
>[!attention]
>Run the code below first for importing necessary libraries!
>```python
>from torch import nn
>```

### Structure
```python
some_model = nn.Sequential(
	LAYER_1()
	LAYER_2()
	...
)
```

### Example: Linear Regression
```python
linear_regression = nn.Sequential(
	nn.Linear(in_features=1, out_features=1)
)
```

### Example: Feedforward Network

```
ffn = nn.Sequential
```
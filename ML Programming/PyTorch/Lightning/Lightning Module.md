---
aliases:
- Lightning Module
---

The lightning module defines the __training, test and validation steps__
```python
import lightning as L
L.LightningModule
```

>[!Super Basic Training module]
>```python
>import lighnting as L
>
>class CustomModule(L.LightningModule):
>
>	def __init__(self, *args, **kwargs):
>		super().__init__()
>		# define all necessary variables here
>		self.model = MyTorchModel(*args, **kwargs) #passing some arguments
>
>	def forward(self, x):
>		# inference logic here
>		return self.model(x)
>
>	def configure_optimizers(self):
>		optimizer = SomeOptimizer(self.parameters(), learning_rate)
>
>	def training_step(self, batch, batch_idx):
>		x, y = batch
>		# some processing steps here and possible logging
>		y_hat = self(x)
>		loss = myLossFunction(y, y_hat)
>		return loss 
>``` 
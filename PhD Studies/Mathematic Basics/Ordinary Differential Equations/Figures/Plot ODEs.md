```python
import matplotlib.pyplot as plt
import numpy as np
from scipy.integrate import odeint


# Define the differential equation y'=df
def df(x,y):
	return 2*y + 3

def plot_df(df, size=(12,9), 
			x_grid=(0.0, 4.0, 20), 
			y_grid=(0.0, 4.0, 20), 
			show_solution=False,
			y_0=0,
            path=None):
	# df: function df(x,y)
	# size: (int, int)
	# x_grid and y_grid for mesh
	
	# figure output size
    fig = plt.figure(figsize=size)
    ax = fig.add_subplot(111)
	
	# mesh grid 
    minx, maxx,	xsteps = x_grid
    miny, maxy, ysteps = y_grid
    x,y = np.meshgrid(np.linspace(minx,maxx, xsteps), np.linspace(miny, maxy, ysteps))
	
	# direction values for the vectors
    u = x-x+1
    v = 1*df(x,y)

	# normalize vectors, such that they are same size
    r = np.power(np.add(np.power(u,2), np.power(v,2)),0.5)

    # find solutions to IVP
    plt.quiver(x,y,u/r,v/r, angles="xy", headwidth=4.2, width=0.002)
    if show_solution:
        solution_steps = 101
        t = np.linspace(minx, maxx, solution_steps)
        if type(y_0) == int:
             sol = odeint(df, y_0, t, tfirst=True)
             plt.plot(t, sol)
        else:
             for y_k in y_0:
                  sol = odeint(df, y_0, t, tfirst=True)
                  plt.plot(t, sol)
		
    if path:
         plt.savefig(path, bbox_inches='tight')
    plt.show()
	
plot_df(df, x_grid=(0.0, 2.0, 20), y_grid=(-1000, 1000, 10), show_solution=True, y_0=range(-20, 20, 5), path="example_1")
```
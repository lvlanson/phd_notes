# Dataset

>[!remark] Classes
>1. Wave functions (sine, cosine)
> ![[Figures/sine_cosine.png|400]]
> 2. rectangle or hard clipped/saturated wave functions
> ![[Figures/hard_clipped_sine.png|400]]
> 
>>[!code]
>>```python 
>>import numpy as np
>>import matplotlib.pyplot as plt 
>>
>>def get_wave(periods: float, freq:float, xshift: float, yshift: float, ystretch: float, res: int = 1_000):
>>    '''
>>    Creates a trigonometric wave function. Given the parameters 
>>        periods  = 1
>>        freq     = 1
>>        xshift   = 0
>>        yshift   = 0
>>        ystretch = 1
>>    one would get a vanilla sine function.
>>    
>>    
>>    Parameters
>>    ----------
>>    periods: float
>>        the amount of periods the wave function should have
>>        
>>    freq: float
>>        the amount of periods within 2*np.pi, freq has to be strictly positive
>>
>>    xshift: float
>>        the shift of the vanilla wave function across the x-axis
>>        
>>    yshift: float
>>        the shift of the vanilla wave function across the y-axis
>>        
>>    ystretch: float
>>        the stretch factor across y-axis of a vanilla sine-wave with [-1,1] range, applying
>>        some factor y_s gives [-y_s, y_s] range
>>        
>>    res: float, optional
>>        determines at what resolution the timeseries is being built 
>>
>>    '''
>>    if freq <= 0:
>>        raise Exception("freq must be strictly positive")
>>    
>>    # create arguments for the sine function where
>>    #   xshift  - shifts the points along the x-axis
>>    #   periods - determines how often a periods is being produced
>>    #   res     - determines how many points are being produced over the
>>    #             given parameters
>>    points = np.linspace(0 + xshift, periods * 2* np.pi + xshift, res, endpoint=False)
>>    
>>    # compute the sine values stretching them with `ystretch` and shift them with `yshift`
>>    y = np.sin(points) * ystretch + yshift 
>>    
>>    # computing the arguments range, such that the are scaled correctly
>>    x = (np.arange(0,res)/res)*2*np.pi*periods/freq
>>    return np.asarray((x,y))
>>
>>def get_rect(periods: float, freq:float, xshift: float, yshift: float, ystretch: float, saturation_factor: float, res: float = 1000):
>>    '''
>>    Creates a trigonometric wave function. Contrary to the `get_wave` function it will "saturate"
>>    the wave function, such that it hard-clips it at some factor `sat_fac` 0 <= sat_fac <= 1. Creates a trigonometric wave function. Given the parameters 
>>        periods = 1
>>        xshift = 0
>>        yshift = 0
>>        ystretch = 1
>>    one would get a vanilla sine function.
>>    
>>    
>>    Parameters
>>    ----------
>>    periods: float
>>       gives the amount of periods the wave function should have
>>        
>>    freq: float
>>        the amount of periods within 2*np.pi
>>
>>    xshift: float
>>        the shift of the vanilla wave function across the x-axis
>>        
>>    yshift: float
>>        the shift of the vanilla wave function across the y-axis
>>        
>>    ystretch: float
>>        the stretch factor across y-axis of a vanilla sine-wave with [-1,1] range, applying
>>        some factor y_s gives [-y_s, y_s] range
>>        
>>    saturation_factor: float
>>        the factor how much a sine function is being hard clipped creating a rectangle-similar function, the factor is supposed to be in the range [0,1] where 0 is no saturation at all and 1 clipping completely creating a straight line
 >>       
 >>   res: float, optional
 >>       determines at what resolution the timeseries is being built 
 >>   '''
 >>   if saturation_factor > 1 or saturation_factor < 0:
 >>       raise Exception("saturation_factor is supposed to be in the range [0,1]")
 >>   data = get_wave(periods, freq, xshift, yshift, ystretch, res)
 >>   
>>    # determine max and min points of the wave
>>    max_pt = np.max(data[1])
>>    min_pt = np.min(data[1])
>>    
>>    # determine wave vertical length
>>    v_length = np.abs(max_pt - min_pt)
>>    
>>    # determine hard-clip points relative to max and min points
>>    sat_max_pt = (min_pt + max_pt)/2 + v_length*saturation_factor
>>    sat_min_pt = (min_pt + max_pt)/2 - v_length*saturation_factor
>>    
>>    # mask out the points outside of the clipping range
>>    mask_top = data[1] <= sat_max_pt
>>    mask_bottom = data[1] >= sat_min_pt
>>    clipped = np.where(mask_top, data[1], sat_max_pt)
>>    clipped = np.where(mask_bottom, clipped, sat_min_pt)
>>
>>    # reassign wave and output
>>    data[1] = clipped
>>    return data
>>```
>
>>[!pic] Results from Code
>>## 1. Saturated/Clipped Sine Function
>>![[Figures/function_saturated_rect.png|400]]
>>```
>>x,y = get_rect(periods=4, 
>>               freq=3,
>>               xshift=3, 
>>               yshift=4, 
>>               ystretch=3,
>>               res=10000,
>>               saturation_factor=0.2)
>>```
>>## 2. Rectangle Function (Almost)
>>![[Figures/function_almost_rect.png|400]]
>>```
>>x,y = get_rect(periods=4, 
>>               freq=3,
>>               xshift=3, 
>>               yshift=4, 
>>               ystretch=3,
>>               res=10000,
>>               saturation_factor=0.001)
>>```
>>## 3. Sine Function
>>![[Figures/function_sine.png|400]]
>>```
>>x,y = get_wave(periods=4, 
>>               freq=3,
>>               xshift=3, 
>>               yshift=4, 
>>               ystretch=3,
>>               res=10000)
>>```

>[!remark] Dataset Creation
>>[!code]
>>```python
>>def create_dataset(n: int, seed: int=1337, res: int=10_000): 
>>    """
>>    Creates a dataset of vanilla sine waves and clipped sine waves which we will refer to rectangle functions,
>>    though they are not precisely rectangle functions 
>>    
>>    Parameters
>>    ----------
>>    n: int
>>        number of samples generated for each class, which are
>>        0 - sine waves
>>        1 - rectangle waves
>>        
>>    seed: int
>>        random seed
>>    
>>    res: int
>>        number of samples created
>>    """
>>    np.random.seed(seed)
>>    waves = []
>>    rects = []
>>    for _ in range(n):
>>        periods  = np.random.randint(1_000)/100
>>        xshift   = np.random.randint(1_000)/100
>>        yshift   = np.random.randint(1_000)/100
>>        freq     = np.random.randint(1, 1_000)/800
>>        ystretch = np.random.randint(1_000)/100
>>        wave     = get_wave(periods=periods, 
>>                            xshift=xshift, 
>>                            yshift=yshift, 
>>                            freq=freq, 
>>                            ystretch=ystretch,
>>                            res=res)
>>        waves.append(wave)
>>
>>    for _ in range(n):
>> 	   periods  = np.random.randint(1_000)/100
>>        xshift   = np.random.randint(1_000)/100
>>        yshift   = np.random.randint(1_000)/100
>>        freq     = np.random.randint(1, 1_000)/800
>>        ystretch = np.random.randint(1_000)/100
>>        sat      = np.random.randint(400)/1_000
>>        rect   = get_rect(periods=periods,
>>                          xshift=xshift, 
>>                          yshift=yshift, 
>>                          freq=freq, 
>>                          ystretch=ystretch,
>>                          saturation_factor=sat,
>>                          res=res)
>>        rects.append(rect) 
>>    return waves, rects
>>    
>>
>>data = create_dataset(100)
>>```
>
>>[!pic] Plots
>>```python 
>>sample = 50  
>>
>>x=data[1][sample][0]
>>y=data[1][sample][1]
>>
>>plt.figure(figsize=(20,8))
>>plt.plot(x,y)
>>```
>>sample = 50 (rectangle)
>>![[Figures/dataset_rect_50.png|800]]
>>sample = 33 (rectangle)
>>![[Figures/dataset_rect_33.png|800]]
>>sample = 15 (rectangle)
>>![[Figures/dataset_rect_15.png|800]]
>>sample = 50 (wave)
>>![[Figures/dataset_sin_50.png|800]]
>>sample = 33 (wave)
>>![[Figures/dataset_rect_33 1.png|800]]


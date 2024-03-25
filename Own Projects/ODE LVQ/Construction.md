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
>>def create_wave_function(rng, xshift, yshift, freq, ystretch):
>>    data = []
>>    for x in range(rng): 
>>        pt = ystretch*np.sin(x*freq + xshift) + yshift
>>        data.append(pt)
>>    data = np.asarray([np.asarray(range(rng)), np.asarray(data)])
>>    return data
>>
>>def create_rect_function(rng, xshift, yshift, freq, ystretch, saturation_factor):
>>    data = create_wave_function(rng, xshift, yshift, freq, ystretch)
>>    max_pt = np.max(data[1])
>>    min_pt = np.min(data[1])
>>    sat_max_pt = max_pt - max_pt*saturation_factor
>>    sat_min_pt = max_pt*saturation_factor + min_pt
>>    mask_top = np.abs(data[1]) <= sat_max_pt
>>    mask_bottom = np.abs(data[1]) >= sat_min_pt
>>    saturated = np.where(mask_top, data[1], sat_max_pt)
>>    saturated = np.where(mask_bottom, saturated, sat_min_pt)
>>    data[1] = saturated
>>    return data
>>```
>
>>[!pic] Results from Code
>>## 1. Saturated/Clipped Sine Function
>>![[Figures/Pasted image 20240324174714.png|300]]
>>with 
>>```
>>data = create_rect_function(rng=range(100), 
>>                            xshift=2, 
>>                            yshift=1, 
>>                            freq=0.1, 
>>                            ystretch=1,
>>                            saturation_factor=0.3) 
>>```
>>## 2. Rectangle Function (Almost)
>>![[Figures/Pasted image 20240324175002.png|300]]
>>```
>>data = create_rect_function(rng=range(100), 
>>                            xshift=2, 
>>                            yshift=1, 
>>                            freq=0.1, 
>>                            ystretch=1,
>>                            saturation_factor=0.5) 
>>```
>>## 3. Sine Function
>>![[Figures/Pasted image 20240324175134.png|300]]
>>```
>>data = create_rect_function(rng=range(100), 
>>                            xshift=2, 
>>                            yshift=1, 
>>                            freq=0.1, 
>>                            ystretch=1,
>>                            saturation_factor=0.5) 
>>```

>[!remark] Dataset Creation
>>[!code]
>>```python
>>def create_dataset(n, seed=1337, rng=100):
>>    # n: number of series per dataset
>>    np.random.seed(seed)
>>    waves = [] 
>>    rects = [] 
>>    for _ in range(n):
>>        xshift   = np.random.randint(1_000)/100
>>        yshift   = np.random.randint(1_000)/100
>>        freq     = np.random.randint(1_000)/500
>>        ystretch = np.random.randint(1_000)/100
>>        wave     = create_wave_function(rng=rng, 
>>                                        xshift=xshift, 
>>                                        yshift=yshift, 
>>                                        freq=freq, 
>>                                        ystretch=ystretch)
>>        waves.append(wave)
>>
>>    for _ in range(n):
>>        xshift   = np.random.randint(1_000)/100
>>        yshift   = np.random.randint(1_000)/100
>>        freq     = np.random.randint(1_000)/500
>>        ystretch = np.random.randint(1_000)/100
>>        sat      = np.random.randint(800)/1_000 + 0.1
>>        rect   = create_rect_function(rng=rng, 
>>                                      xshift=xshift, 
>>                                      yshift=yshift, 
>>                                      freq=freq, 
>>                                      ystretch=ystretch,
>>                                      saturation_factor=sat)
>>        rects.append(rect)
>>    return waves, rects
>>    
>>
>>data = create_dataset(100)
>>
>>sample = 20
>>
>>x=data[1][sample][0]
>>y=data[1][sample][1]
>>
>>plt.plot(x,y) 
>>```
>
>>[!pic] Plots
>>```python 
>>sample = 55
>>
>>x=data[1][sample][0]
>>y=data[1][sample][1]
>>
>>plt.figure(figsize=(20,8))
>>plt.plot(x,y)
>>```
>>n = 50 (rectangle)
>>![[Figures/Pasted image 20240324185054.png]]
>>n = 33 (rectangle)
>>![[Figures/Pasted image 20240324185152.png]]
>>n = 50 (wave)
>>![[../../Pasted image 20240324185253.png]]
>>n = 33 (wave)
>>![[../../Pasted image 20240324185307.png]]
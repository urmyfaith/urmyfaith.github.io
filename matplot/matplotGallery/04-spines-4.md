# plot sin 04
* 坐标轴居中
---

## code 

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import numpy as np
import matplotlib
import matplotlib.pyplot as plt

# Data to be represented
X = np.linspace(-np.pi,+np.pi,256)
Y = np.sin(X)

# Actual plotting
fig = plt.figure(figsize=(8,6), dpi=72,facecolor="white")
axes = plt.subplot(111)
axes.plot(X,Y, color = 'blue', linewidth=2, linestyle="-")
axes.set_xlim(X.min(),X.max())
axes.set_ylim(1.01*Y.min(),1.01*Y.max())

axes.spines['right'].set_color('none')
axes.spines['top'].set_color('none')
axes.xaxis.set_ticks_position('bottom')
axes.spines['bottom'].set_position(('data',0))
axes.yaxis.set_ticks_position('left')
axes.spines['left'].set_position(('data',0))

plt.show()

```
---

## Keypoints
**axes.spines['bottom'].set_position(('data',0))**  
X轴居中

** axes.spines['left'].set_position(('data',0))**
Y轴居中

---
## Result

![plot-sin-04](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/plot-sin-04.png)

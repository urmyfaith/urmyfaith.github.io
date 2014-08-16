#plot sin 03

1. 数据区域边界线的位置

---
# Code

``` python

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
axes.set_ylim(1.01*Y.min(), 1.01*Y.max())

axes.spines['right'].set_color('none')
axes.spines['top'].set_color('none')

axes.xaxis.set_ticks_position('bottom') 
axes.spines['bottom'].set_position(('data',0))
axes.yaxis.set_ticks_position('left')
axes.spines['left'].set_position(('data',X.min()))

plt.show()

```
---
## Keypoints:

> axes.xaxis.set_ticks_position('bottom') 

x轴位置:底部

>   axes.spines['bottom'].set_position(('data',0))

数据区域编辑线(左,上,右,下)

下: (X轴)数据值为0的地方(y=0)

> axes.spines['left'].set_position(('data',X.min()))

左: (Y轴)数据值为X最小的地方

![spines-set-position](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/spines-set-position.png)

---

## Result
![plot-sin-03](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/plot-sin-03.png)


# draw sin 02

1. 设置数据区域的边界线颜色
2. 设置坐标轴的位置
---
## code

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
    axes.set_ylim(1.01*Y.min(),1.01*Y.max())
    
    
    #spines
    axes.spines['left'].set_color('yellow')
    axes.spines['top'].set_color('red')
    axes.spines['right'].set_color('blue')
    axes.spines['bottom'].set_color('green')
    
                
    #axes.xaxis.set_ticks_position('bottom')
    axes.xaxis.set_ticks_position('top')
    
    #axes.yaxis.set_ticks_position('left')
    axes.yaxis.set_ticks_position('right')
   
    plt.show()

```
---

## Keypoints:

### 设置数据区域的边界线颜色

> axes.spines['left'].set_color('yellow')

**spines** :  the-line-noting-the-data-area-boundaries

四个边界线:左,上,右,下

### 设置坐标轴位置

> #axes.yaxis.set_ticks_position('left')

x轴的位置:上,下
y轴的位置:左,右.

## result
![plot_sin](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/plot-sin-02.png)


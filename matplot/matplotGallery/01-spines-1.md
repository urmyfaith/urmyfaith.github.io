# draw sin 

## Steps

1. 导入包
2. 生成X轴,Y轴的数据点
3. 设置输出图大小,像素,前景色
4. 指定线宽,线型,绘制曲线
5. 设置坐标轴范围
6. 显示图形.

## Code

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
fig = plt.figure(figsize=(8,6), dpi=72, facecolor="white")
axes = plt.subplot(111)
axes.plot(X,Y, color = 'blue', linewidth=2, linestyle="-")
axes.set_xlim(X.min(),X.max())

plt.show()


```

----

## Detail

> X = np.linspace(-np.pi,+np.pi,256)

> Y = np.sin(X)

生成X,Y轴的数据点,X轴是256个数据点,Y也是256个数据点.

> fig = plt.figure(figsize=(8,6), dpi=72, facecolor="white")

设置输出图形的窗口大小,像素,前景色

![matplotlib_pylot_figure](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/matplotlib-pylot-figure.png)

>  axes.plot(X,Y, color = 'blue', linewidth=2, linestyle="-")

指定线宽,线型,绘制曲线

## Result

![plot_sin](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/plot_sin.png)
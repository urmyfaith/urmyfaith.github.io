# plot sin示意图(隐藏刻度,自定义刻度)

* 隐藏坐标轴刻度
* 自定义坐标轴刻度
---

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
fig = plt.figure(figsize=(8,6), dpi=72,facecolor="white")
axes = plt.subplot(111)
axes.plot(X,Y, color = 'blue', linewidth=2, linestyle="-")
axes.set_xlim(1.1*X.min(),1.1*X.max())
axes.set_ylim(1.1*Y.min(),1.1*Y.max())

axes.spines['right'].set_color('none')
axes.spines['top'].set_color('none')
axes.spines['bottom'].set_position(('data',0))
axes.spines['left'].set_position(('data',0))
axes.set_xticks([])
axes.set_yticks([])

plt.show()

```

## Keypoints
**axes.set_xticks([])**
**axes.set_yticks([])**
设置X,Y坐标轴点刻度为空
![set_xticks](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/set-xticks.png)

## Result
![set-xticks-01.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/set-xticks-01.png)

## More
自定义刻度
```python 
 axes.set_xticks([-3,-2,-1,0,1,2,3])
```
![set-xticks-02.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/set-xticks-02.png)

---
自定义刻度
```python
axes.set_xticks([0., .5*np.pi, np.pi, 1.5*np.pi, 2*np.pi])
```
![set-xticks-03.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/set-xticks-03.png)

---
自定义刻度
```python
axes.set_xticks([0., .5*np.pi, np.pi)
axes.set_xticklabels(["0", r"$\frac{1}{2}\pi$",r"$\pi$"])
```
![set-xticks-04.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/set-xticks-04.png)

---
隐藏坐标轴
```python
axes.set_xticks([])
axes.set_yticks([])
axes.spines['right'].set_color('none')
axes.spines['top'].set_color('none')
axes.spines['bottom'].set_color('none')
axes.spines['left'].set_color('none')
```
![set-xticks-05.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/set-xticks-05.png)



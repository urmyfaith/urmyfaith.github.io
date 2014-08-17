# style 

1. 绘制y=1
2. 不同线宽

---

## y=1

###code 

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import numpy as np
import matplotlib
import matplotlib.pyplot as plt

#Data
Y=np.linspace(0,1,12)
X=np.ones(Y.size)

#figure
fig = plt.figure(figsize=(8,6), dpi=72, facecolor='white')
axes = plt.subplot(111)

#plot 
axes.plot( (1+0)*X, Y, linewidth=0.25, color='blue')

plt.show()
 
```
###Keypoints

> axes.plot( (1+0)*X, Y, linewidth=0.25, color='blue')

X=[ 1.  1.  1.  1.  1.  1.  1.  1.  1.  1.  1.  1.]

Y=[ 0.          0.09090909  0.18181818  0.27272727  0.36363636  0.45454545
  0.54545455  0.63636364  0.72727273  0.81818182  0.90909091  1.        ]

###Result
![style-01.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/style-01.png)

----

## 不同线宽

### code

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import numpy as np
import matplotlib
import matplotlib.pyplot as plt

# Data to be represented
Y = np.linspace(0,1,12)
print Y

X = np.ones(Y.size)
print X

W = [0.25,0.50,0.75,1,2,3,4,5,6,7,8]  #linewidth 
print W

# Actual plotting
fig = plt.figure(figsize=(8,6), dpi=72, facecolor='white')
axes = plt.subplot(111)

for i,w in enumerate(W):
    axes.plot( (1+i)*X, Y, linewidth=w, color='blue')

# X,Y axes lable
axes.set_xlim(0,len(W)+1)
axes.set_yticks([])
axes.set_xticks(np.arange(1,len(W)+1))
axes.set_xticklabels(['%.2f' % w for w in W])

plt.show()

```
### Keypoints
 
> ```python
for i,w in enumerate(W):
    axes.plot( (1+i)*X, Y, linewidth=w, color='blue')
```

![enumerate-help.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/enumerate-help.png)

绘制12条直线,X=1,...X=12

### Result

![style-02.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/style-02.png)

隐藏Y轴刻度,替换X轴标签后的图形

![style-03.png](https://raw.githubusercontent.com/urmyfaith/urmyfaith.github.io/master/matplot/matplotGallery/images/style-03.png)

----







title: python-matplotlib后端设置
date: 2015-12-21 21:46:23
tags:
---

###### OS：openSuSE Leap-42.1

```python
import matplotlib.ptplot as plt
```


　　在使用python-matplotlib模块的时候遇到了一个问题，plt.show()函数无法正常输出图像。在网上找到解决方案为修改matplotlib的配置文件，原为Agg，将其backend设置为其他即可，如Qt4Agg，TkAgg。设为Qt4Agg没有问题，输出正常。


　　之后因为需要将图像的输出设为动态交互式的，而将plt.show()改为plt.draw()。注意，使用draw()而非show()是因为后者生成的窗口无法调用close()主动关闭，而前者可以。若使用plt.draw()则需要打开interactive开关，即plt.ion()。但这时又出现了无法输出图像的问题，在网上找了很久没能解决，最后尝试着再次修改了backend为TkAgg，问题成功解决。
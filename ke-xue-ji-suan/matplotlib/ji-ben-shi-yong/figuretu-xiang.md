## 简单的线条 {#简单的线条}

matplotlib 的 figure 就是一个 单独的 figure 小窗口, 小窗口里面还可以有更多的小图片.

使用`import`导入模块`matplotlib.pyplot`，并简写成`plt`使用`import`导入模块`numpy`，并简写成`np`

```
import matplotlib.pyplot as plt
import numpy as np
```

使用`np.linspace`定义x：范围是\(-3,3\);个数是50. 仿真一维数据组\(`x`,`y1`\)表示曲线1. 仿真一维数据组\(`x`,`y2`\)表示曲线2.

```
x = np.linspace(-3, 3, 50)
y1 = 2*x + 1
y2 = x**2
```

使用`plt.figure`定义一个图像窗口. 使用`plt.plot`画\(`x`,`y1`\)曲线.

```
plt.figure()
plt.plot(x, y1)
plt.show()
```

[![](https://morvanzhou.github.io/static/results/plt/2_2_1.png "figure 图像")](https://morvanzhou.github.io/static/results/plt/2_2_1.png)

使用`plt.figure`定义一个图像窗口：编号为3；大小为\(8, 5\). 使用`plt.plot`画\(`x`,`y2`\)曲线. 使用`plt.plot`画\(`x`,`y1`\)曲线，曲线的颜色属性\(`color`\)为红色;曲线的宽度\(`linewidth`\)为1.0；曲线的类型\(`linestyle`\)为虚线. 使用`plt.show`显示图像.

```
plt.figure(num=3, figsize=(8, 5),)
plt.plot(x, y2)
plt.plot(x, y1, color='red', linewidth=1.0, linestyle='--')
plt.show()
```

[![](https://morvanzhou.github.io/static/results/plt/2_2_2.png "figure 图像")](https://morvanzhou.github.io/static/results/plt/2_2_2.png)


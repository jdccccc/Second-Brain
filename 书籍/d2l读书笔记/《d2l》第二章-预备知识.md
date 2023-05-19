#深度学习 #d2l

深度学习需要使用数据，学会存储、操作、预处理数据。
数据是一种表，可以使用线性代数的方法来处理表格数据。
调整参数需要微积分知识。
推断时需要用到概率语言。

# 数据操作

张量Tensor——N维数组
[[d2l-zh-pytorch-anno#^bfntccc5lzm|深度学习框架又比Numpy的ndarray多一些重要功能：首先，GPU很好地支持加速计算，而NumPy仅支持CPU计算；其次，张量类支持自动微分]]

## 入门

```Python
import torch

x = torch.arange(12) #创建行向量
x.shape() #查看张量各维的尺寸
x.numel() #查看张量总共的元素数量
```
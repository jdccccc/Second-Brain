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
X = x.reshape(3,4)#把张量x从形状为(12,)的行向量转换为形状为(3,4)的矩阵
X = x.reshape(-1,4)#通过-1来调用自动计算出维度的功能,最多省略1个维度

#全0、全1、其他常量，或者从特定分布中随机采样的数字来初始化矩阵
torch.zeros((2,3,4))
torch.ones((2,3,4))
torch.randn(3,4)#每个元素都从均值为0、标准差为1的标准高斯分布（正态分布）中随机采样

#提供包含数值的Python列表（或嵌套列表），来为所需张量中的每个元素赋予确定值
torch.tensor([[2, 1, 4, 3], [1, 2, 3, 4], [4, 3, 2, 1]])
```

## 运算符
对于将两个数组作为输入的函数，**按元素运算**将二元运算符应用于两个数组中的每对位置对应的元素。
$$
F:\mathbb{R}^{d},\mathbb{R}^{d}\to \mathbb{R}^{d}
$$

```python
>>> x = torch.tensor([1.0, 2, 4, 8]) #tensor初试化时有一个元素是浮点数，tensor中所有其他元素都是浮点数
>>> y = torch.tensor([2, 2, 2, 2])
>>> x+y
tensor([ 3.,  4.,  6., 10.])
>>> x = torch.tensor([1, 2, 4, 8]) 
>>> x+y
tensor([ 3,  4,  6, 10])
>>> torch.exp(x)
tensor([2.7183e+00, 7.3891e+00, 5.4598e+01, 2.9810e+03])
```


把多个张量**连结（concatenate）** 在一起
```python
X = torch.arange(12, dtype=torch.float32).reshape((3,4)) 
Y = torch.tensor([[2.0, 1, 4, 3], [1, 2, 3, 4], [4, 3, 2, 1]]) torch.cat((X, Y), dim=0), torch.cat((X, Y), dim=1)
```
第一个输出张量的轴-0⻓ 度（6）是两个输入张量轴-0⻓度的总和（3 + 3）；第二个输出张量的轴-1⻓度（8）是两个输入张量轴-1⻓度 的总和（4 + 4）。
```python
(tensor([[ 0., 1., 2., 3.], [ 4., 5., 6., 7.], [ 8., 9., 10., 11.], [ 2., 1., 4., 3.], [ 1., 2., 3., 4.], [ 4., 3., 2., 1.]]), tensor([[ 0., 1., 2., 3., 2., 1., 4., 3.], [ 4., 5., 6., 7., 1., 2., 3., 4.], [ 8., 9., 10., 11., 4., 3., 2., 1.]]))
```


通过**逻辑运算符**构建二元张量
```python
>>> x == y
tensor([False,  True, False, False])
```

对张量中的**所有元素进行求和**，会产生一个单元素张量
```python
>>> x.sum()
tensor(15)
```

## 广播机制

在某些情况下，即使形状不同， 我们仍然可以通过调用 **广播机制（broadcasting mechanism）** 来执行按元素操作。这种机制的工作方式如 下： 
1. 通过适当复制元素来扩展一个或两个数组，以便在转换之后，两个张量具有相同的形状； 
2. 对生成的数组执行按元素操作。

```python
>>> a = torch.arange(3).reshape((3, 1)) 
>>> b = torch.arange(2).reshape((1, 2)) 
>>> a, b
(tensor([[0],
        [1],
        [2]]), tensor([[0, 1]]))
>>> a+b #矩阵a将复制列，矩阵b将复制行，然后再按元素相加
tensor([[0, 1],
        [1, 2],
        [2, 3]])
```

## 索引和切片
张量中的元素可以通过索引访问，与任何Python数组一样：第一个元素的索引是0，**最后一个元素索引是-1**。

```python
x[-1], x[1:3] #用[-1]选择最后一个元素，用[1:3]选择第二个和第三个元素
x[1,2] = 9 #过指定索引来将元素写入矩阵

#[0:2, :]访问第1行和第2行,其中“:”代表沿轴1（列）的所有元素
x[0:2, :] = 12 #为多个元素赋值相同的值
```

## 节省内存
Python的id()函数给我们提供了内存中引用对象的确切地址。运行Y = Y + X后，我们会发现id(Y)指向另一个位置。这是因为Python首先计算Y + X，为结果分配新的内存，然后使Y指向内存中的这个新位置。

```python
>>> import torch
>>> X = torch.ones(1,2,3)
>>> Y = torch.ones(1,2,3)
>>> id(Y)
139997579952832
>>> Y = X+Y
>>> id(Y)
139997579952992
```

这可能是不可取的，原因有两个： 
1. 首先，我们不想总是**不必要地分配内存**。在机器学习中，我们可能有数百兆的参数，并且在一秒内多次 更新所有参数。通常情况下，我们希望原地执行这些更新； 
2. 如果我们不原地更新，其他引用仍然会指向旧的内存位置，这样我们的某些代码可能会**无意中引用旧的参数**。

**执行原地操作**：使用**切片表示法**或者**自增运算符**将操作的结果分配给先前分配的数组。
```python
>>> id(Y)
139997579952992
>>> Y[:]=X+Y
>>> id(Y)
139997579952992
>>> Y += X
>>> id(Y)
139997579952992
```

## 转换为其他Python对象
torch张量和numpy数组转换后共享它们的底层内存，就地操作更改一个张量也会同时更改另一个张量。

```python
>>> import torch
>>> A = torch.ones((2,3,4))
>>> B = A.numpy()
>>> C = torch.tensor(B)
>>> type(A),type(B)
(<class 'torch.Tensor'>, <class 'numpy.ndarray'>)
```


将大小为1的张量转换为Python标量，可以调用**item函数**或Python的内置函数
```python
>>> a = torch.tensor([3.5])
>>> a
tensor([3.5000])
>>> float(a)
3.5
>>> int(a)
3
>>> a.item()
3.5
```

# 数据预处理
在Python中常用的数据分析工具中，我们通常使用pandas软件包。
## 读取数据集
首先创建一个人工数据集，并存储在CSV（逗号分隔值）文件./data/house_tiny.csv中。
将数据集按行写入CSV文件中：

```python
import os 
os.makedirs(os.path.join('.', 'data'), exist_ok=True) 
data_file = os.path.join('.', 'data', 'house_tiny.csv') 
with open(data_file, 'w') as f: 
	f.write('NumRooms,Alley,Price\n') # 列名 
	f.write('NA,Pave,127500\n') # 每行表示一个数据样本 
	f.write('2,NA,106000\n') 
	f.write('4,NA,178100\n') 
	f.write('NA,NA,140000\n')
```

- [[如何使用Python的import语句？]]
- [[如何使用python os模块]]
- [[如何使用python的open函数？]]
- [[如何使用python的file对象？]]
- [[如何使用python的with...as语句？]]

要从创建的CSV文件中加载原始数据集，我们导入pandas包并调用read_csv函数。该数据集有四行三列。其中每行描述了房间数量（“NumRooms”）、巷子类型（“Alley”）和房屋价格（“Price”）。 

 ```python
 import pandas as pd 
 data = pd.read_csv(data_file) 
 print(data)
 ```

```python
   NumRooms Alley   Price
0       NaN  Pave  127500
1       2.0   NaN  106000
2       4.0   NaN  178100
3       NaN   NaN  140000
```

## 处理缺失值
“NaN”项代表缺失值。
为了处理缺失的数据，典型的方法包括插值法和删除法，
- 插值法用一个替代值弥补缺失值
- 删除法则直接忽略缺失值

通过位置索引iloc，我们将data分成inputs和outputs，其中前者为data的前两列，而后者为data的最后一列。 
对于inputs中缺少的数值，我们用同一列的均值替换“NaN”项。
```python
inputs, outputs = data.iloc[:, 0:2], data.iloc[:, 2] 
inputs = inputs.fillna(inputs.mean())
print(inputs)
```

[[如何使用python pandas模块？]]

对于inputs中的类别值或离散值，我们将“NaN”视为一个类别。
由于“巷子类型”（“Alley”）列只接受两种类型的类别值“Pave”和“NaN”，pandas可以自动将此列转换为两列“Alley_Pave”和“Alley_nan”。
巷子类型为“Pave”的行会将“Alley_Pave”的值设置为1，“Alley_nan”的值设置为0。
缺少巷子类型的行会将“Alley_Pave”和“Alley_nan”分别设置为0和1。
```python
inputs = pd.get_dummies(inputs, dummy_na=True) 
print(inputs)
```

```python
   NumRooms  Alley_Pave  Alley_nan
0       3.0           1          0
1       2.0           0          1
2       4.0           0          1
3       3.0           0          1
```

## 转换为张量格式

```python
>>>import torch 
>>>X, y = torch.tensor(inputs.values), torch.tensor(outputs.values) 
>>>X, y 

(tensor([[3., 1., 0.], 
		 [2., 0., 1.], 
		 [4., 0., 1.], 
		 [3., 0., 1.]], dtype=torch.float64), 
 tensor([127500, 106000, 178100, 140000]))
```
# 线性代数
## 标量

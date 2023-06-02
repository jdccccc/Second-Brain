#python #pandas

# 简单的常用函数
- 通过位置选择数据  
	`data.iloc[row_index, column_index]`
- 将缺失值替换为指定的值
	`data.fillna(0)`
- 计算每列的平均值  
	`mean = data.mean()`

# 较复杂的函数
## get_dummies
**get_dummies**是 pandas 实现**one hot encode**的方式。

one-hot的基本思想：将离散型特征的每一种取值都看成一种状态，若你的这一特征中有N个不相同的取值，那么我们就可以将该特征抽象成N种不同的状态，one-hot编码保证了每一个取值只会使得一种状态处于“激活态”，也就是说这N种状态中只有一个状态位值为1，其他状态位都是0。
`pd.get_dummies( data, prefix=None, prefix_sep='\_', dummy_na=False, columns=None, sparse=False, drop_first=False, dtype=None)`

```python
data = pd.DataFrame({'A': ['a', 'b', 'a'], 'B': ['b', 'a', 'c'],
                   'C': [1, 2, 3]})
print(data)
>>>
   A  B  C
0  a  b  1
1  b  a  2
2  a  c  3

print(pd.get_dummies(data))
>>>
   C  A_a  A_b  B_a  B_b  B_c
0  1    1    0    0    1    0
1  2    0    1    1    0    0
2  3    1    0    0    0    1
```

- data : array-like, Series, or DataFrame
	输入的数据
- prefix : string, list of strings, or dict of strings, default None
	get_dummies转换后，列名的前缀
- columns : list-like, default None
	指定需要实现类别转换的列名
- dummy_na : bool, default False
增加一列表示空缺值，如果False就忽略空缺值
- drop_first : bool, default False
获得k中的k-1个类别值，去除第一个
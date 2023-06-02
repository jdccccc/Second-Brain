#python #import
import 语句用来导入其他 python 文件（称为模块 module），使用该模块里定义的类、方法或者变量，从而达到代码复用的目的。

[[Python 中 import 的用法]]

# 简单情形

1. `import module_name`。即 import 后直接接模块名。在这种情况下，Python 会在两个地方寻找这个模块
	1. 第一是 sys.path（通过运行代码`import sys; print(sys.path)`查看），os 这个模块所在的目录就在列表 sys.path 中，一般安装的 Python 库的目录都可以在 sys.path 中找到（前提是要将 Python 的安装目录添加到电脑的环境变量），所以对于安装好的库，我们直接 import 即可。
	2. 第二个地方就是运行文件所在的目录，

2.  `from package_name import module_name`。一般把模块组成的集合称为包（package）。包是一个文件夹，模块是py文件，包文件夹中包含一些py文件（模块）。与第一种写法类似，Python 会在 sys.path 和运行文件目录这两个地方寻找包，然后导入包中名为 module_name 的模块。

*   `import moudle_name as alias`。有些 module_name 比较长，之后写它时较为麻烦，或者 module_name 会出现名字冲突，可以用 as 来给它改名，如`import numpy as np`。
*   `from module_name import function_name, variable_name, class_name`。上面导入的都是整个模块，有时候我们只想使用模块中的某些函数、某些变量、某些类，用这种写法就可以了。使用逗号可以导入模块中的多个元素。
*   有时候导入的元素很多，可以使用反斜杠来换行，官方推荐使用括号。


# 绝对导入和相对导入

python3的import使用**绝对导入**，即导入 sys.path 中的包和运行文件所在目录下的包。导入自己写的文件，如果是**非运行入口文件，则需要相对导入**。

比如
```
Tree
|____ m1.py
|____ m2.py
|____ Branch
     |____m3.py
     |____m4.py
```
m1中from Branch import m3，m3中import m4，运行m1则会报错。
m1中from Branch import m3，m3中import m2，运行m1不会报错。

对于非运行入口文件 m3.py，其导入 m4.py 需要使用相对导入：
```python
from . import m4
def printSelf():
	print('In m3')
```

相对导入的写法：

*   `from . import module_name`。导入和自己同目录下的模块。
*   `from .package_name import module_name`。导入和自己同目录的包的模块。
*   `from .. import module_name`。导入上级目录的模块。
*   `from ..package_name import module_name`。导入位于上级目录下的包的模块。
*   每多一个点就多往上一层目录。



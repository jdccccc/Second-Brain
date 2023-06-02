#python #os #module

`os`就是“operating system”的缩写，顾名思义，`os`模块提供的就是各种 Python 程序与操作系统进行交互的接口。

# os.name
该属性宽泛地指明了当前 Python 运行所在的环境，实际上是导入的操作系统相关模块的名称。这个名称也决定了模块中**哪些功能是可用**的，哪些是没有相应实现的。

目前有效名称为以下三个：`posix`，`nt`，`java`。

其中`posix`是 Portable Operating System Interface of UNIX（可移植操作系统接口）的缩写。Linux 和 Mac OS 均会返回该值；`nt`全称应为“Microsoft Windows NT”，大体可以等同于 Windows 操作系统，因此 Windows 环境下会返回该值；`java`则是 Java 虚拟机环境下的返回值。

# os.path()
这个模块是`os`模块根据系统类型从另一个模块导入的，并非直接由`os`模块实现，比如`os.name`值为`nt`，则在`os`模块中执行`import ntpath as path`；如果`os.name`值为`posix`，则导入`posixpath`。

使用该模块要注意一个很重要的特性：`os.path`中的函数基本上是纯粹的字符串操作。换句话说，传入该模块函数的参数甚至不需要是一个有效路径，该模块也不会试图访问这个路径，而仅仅是按照“路径”的通用格式对字符串进行处理。

该模块的作用是让我们在实现相同功能的时候不必考虑具体的系统，尤其是不需要过多关注文件系统分隔符的问题。

## os.path.join()
可以将多个传入路径组合为一个路径。实际上是将传入的几个字符串**用系统的分隔符**连接起来，组合成一个新的字符串，所以一般的用法是将第一个参数作为父目录，之后每一个参数即使下一级目录，从而组合成一个新的符合逻辑的路径。

但如果传入路径中存在一个“绝对路径”格式的字符串，且这个字符串不是函数的第一个参数，那么其他在这个参数之前的所有参数都会被丢弃，余下的参数再进行组合。更准确地说，只有最后一个“绝对路径”及其之后的参数才会体现在返回结果中。

```python
>>> os.path.join("just", "do", "python", "dot", "com")
'just\\do\\python\\dot\\com'
>>> 
>>> os.path.join("just", "do", "d:/", "python", "dot", "com")
'd:/python\\dot\\com'
>>> 
>>> os.path.join("just", "do", "d:/", "python", "dot", "g:/", "com")
'g:/com'
```

# os.makedirs()
函数`os.makedirs()`执行的是递归创建，若有必要，会分别新建指定路径经过的中间路径，直到最后创建出末端的“叶子路径”。

`os.makedirs(name, mode=0o777, exist_ok=False)`
参数说明
- name：你想创建的目录名
- mode：要为目录设置的权限数字模式，默认的模式为 0o777 (八进制)。
- exist_ok：是否在目录存在时触发异常。如果exist_ok为False（默认值），则在目标目录已存在的情况下触发FileExistsError异常；如果exist_ok为True，则在目标目录已存在的情况下不会触发FileExistsError异常。
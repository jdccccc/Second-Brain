#python #with-as

# With语句是什么？

有一些任务，可能**事先需要设置，事后做清理工作**。对于这种场景，Python的with语句提供了一种非常方便的处理方式。一个很好的例子是文件处理，你需要获取一个文件句柄，从文件中读取数据，然后关闭文件句柄。  
[[如何使用python的file对象？]]
如果不用with语句，代码如下：

```python
file = open("/tmp/foo.txt")  
data = file.read()  
file.close()
```

这里有两个问题。一是可能忘记关闭文件句柄；二是文件读取数据发生异常，没有进行任何处理。下面是处理异常的加强版本：

```python
file = open ("/tmp/foo.txt")
try:
	data = file.read()
finally:
	file.close()
```

虽然这段代码运行良好，但是太冗长了。这时候就是with一展身手的时候了。除了有更优雅的语法，with还可以很好的处理上下文环境产生的异常。下面是with版本的代码：

```python
with open("/tmp/foo.txt") as file:
	data = file.read()
```

# with如何工作?

基本思想是with所求值的对象必须有一个__enter__()方法，一个__exit__()方法。

紧跟with后面的语句被求值后，返回对象的__enter__()方法被调用，这个方法的返回值将被赋值给as后面的变量。当with后面的代码块全部被执行完之后，将调用前面返回对象的__exit__()方法。

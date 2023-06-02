Python 用了快两年了吧，其中有些东西一直是稀里糊涂地用，import 便是我一直没有明白的东西。曾经有过三次解决它的机会，我都因得过且过、一拖再拖而没能化敌为友。今天下午，它又给了我一次机会，我想我还是从了它的心愿吧。

故事是从这篇台湾同胞的博客（[Python 的 Import 陷阱](https://link.zhihu.com/?target=https%3A//medium.com/pyladies-taiwan/python-%25E7%259A%2584-import-%25E9%2599%25B7%25E9%2598%25B1-3538e74f57e3)）开始的，然后又跳到了 Python 社区的 PEP 328 提案（[PEP 328 -- Imports: Multi-Line and Absolute/Relative](https://link.zhihu.com/?target=https%3A//www.python.org/dev/peps/pep-0328/%23id1)），再结合过去的经验以及一些测试，我想我大概懂了吧。下面是我的总结，希望内容能够言简意赅、易于理解。

import 语句有什么用？import 语句用来导入其他 python 文件（称为模块 module），使用该模块里定义的类、方法或者变量，从而达到代码复用的目的。为了方便说明，我们用实例来说明 import 的用法，读者朋友可以跟着尝试（尝试时建议使用 python3，python2 和 python3 在 import 的表现有差异，之后会提到）。

将要建立文件的结构为：

```
Tree
|____ m1.py
|____ m2.py
|____ Branch
     |____m3.py
     |____m4.py
```

首先，先建立一个文件夹 Tree 作为工作目录，并在其内建立两个文件 m1.py 和 m2.py，在 m1.py 写入代码：

```
import os
import m2
m2.printSelf()
```

在 m2.py 写入代码：

```
def printSelf():
	print('In m2')
```

打开命令行，进入到 Tree 目录下，敲下`python m1.py`运行，发现没有报错，且打印出`In m2`，说明这样使用 import 没有问题。由此我们总结出 import 语句的第一种用法。

*   `import module_name`。即 import 后直接接模块名。在这种情况下，Python 会在两个地方寻找这个模块，第一是 sys.path（通过运行代码`import sys; print(sys.path)`查看），os 这个模块所在的目录就在列表 sys.path 中，一般安装的 Python 库的目录都可以在 sys.path 中找到（前提是要将 Python 的安装目录添加到电脑的环境变量），所以对于安装好的库，我们直接 import 即可。第二个地方就是运行文件（这里是 m1.py）所在的目录，因为 m2.py 和运行文件在同一目录下，所以上述写法没有问题。

用上述方法导入原有的 sys.path 中的库没有问题。但是，最好不要用上述方法导入同目录下的文件！因为这可能会出错。演示这个错误需要用到 import 语句的第二种写法，所以先来学一学 import 的第二种写法。在 Tree 目录下新建一个目录 Branch，在 Branch 中新建文件 m3.py，m3.py 的内容如下：

```
def printSelf():
	print('In m3')
```

如何在 m1 中导入 m3.py 呢，请看更改后的 m1.py：

```
from Branch import m3
m3.printSelf()
```

总结 import 语句的第二种用法：

*   `from package_name import module_name`。一般把模块组成的集合称为包（package）。与第一种写法类似，Python 会在 sys.path 和运行文件目录这两个地方寻找包，然后导入包中名为 module_name 的模块。

现在我们来说明为什么不要用 import 的第一种写法来导入同目录下的文件。在 Branch 目录下新建 m4.py 文件，m4.py 的内容如下：

```
def printSelf():
	print('In m4')
```

然后我们在 m3.py 中直接导入 m4，m3.py 变为：

```
import m4
def printSelf():
	print('In m3')
```

这时候运行 m1.py 就会报错了，说没法导入 m4 模块。为什么呢？我们来看一下导入流程：m1 使用`from Branch import m3`导入 m3，然后在 m3.py 中用`import m4`导入 m4。看出问题了吗？m4.py 和 m1.py 不在同一目录，怎么能直接使用`import m4`导入 m4 呢。（读者可以试试直接在 Tree 目录下新建另一个 m4.py 文件，你会发现再运行 m1.py 就不会出错了，只不过导入的是第二个 m4.py 了）

面对上面的错误，使用 python2 运行 m1.py 就不会报错，因为在 python2 中，上面提到的 import 的两种写法都属于相对导入，而在 python3 中，却属于绝对导入。话说到了这里，就要牵扯到 import 中最关键的部分了——相对导入和绝对导入。

我们还是谈论 python3 的 import 用法。上面提到的两种写法属于绝对导入，即用于导入 sys.path 中的包和运行文件所在目录下的包。对于 sys.path 中的包，这种写法毫无问题；导入自己写的文件，如果是非运行入口文件（上面的 m1.py 是运行入口文件，可以使用绝对导入），则需要相对导入。

比如对于非运行入口文件 m3.py，其导入 m4.py 需要使用相对导入：

```
from . import m4
def printSelf():
	print('In m3')
```

这时候再运行 m1.py 就 ok 了。列举一下相对导入的写法：

*   `from . import module_name`。导入和自己同目录下的模块。
*   `from .package_name import module_name`。导入和自己同目录的包的模块。
*   `from .. import module_name`。导入上级目录的模块。
*   `from ..package_name import module_name`。导入位于上级目录下的包的模块。
*   当然还可以有更多的`.`，每多一个点就多往上一层目录。

不知道你有没有留神上面的一句话——“上面的 m1.py 是运行入口文件，可以使用绝对导入”，这句话是没问题的，也和我平时的做法一致。那么，运行入口文件可不可以使用相对导入呢？比如 m1.py 内容改成：

```
from .Branch import m3
m3.printSelf()
```

答案是可以，但不能用`python m1.py`命令，而是需要进入到 Tree 所在的目录，使用`python -m Tree.m1`来运行。为什么？关于前者，PEP 328 提案中的一段文字好像给出了原因：

Relative imports use a module's _name_ attribute to determine that module's position in the package hierarchy. If the module's name does not contain any package information (e.g. it is set to '__main__') then relative imports are resolved as if the module were a top level module, regardless of where the module is actually located on the file system.

我不太懂，但是又有一点明白。我们应该见过下面一段代码：

```
if __name__ == '__main__':
	main()
```

意思是如果运行了当前文件，则__name__变量会置为__main__，然后会执行 main 函数，如果当前文件是被其他文件作为模块导入的话，则__name__为模块名，不等于__main__，就不会执行 main 函数。比如对于上述更改后的 m1.py，执行`python m1.py`命令后，会报如下错误：

Traceback (most recent call last): File "m1.py", line 1, in from .Branch import m3 ModuleNotFoundError: No module named '__main__.Branch';'__main__' is not a package

据此我猜测执行`python m1.py`命令后，当前目录所代表的包'.'变成了__main__。

那为什么`python -m Tree.m1`就可以呢？那位台湾老师给出了解释：

执行指令中的 - m 是为了让 Python 预先 import 你要的 package 或 module 给你，然后再执行 script。

即不把 m1.py 当作运行入口文件，而是也把它当作被导入的模块，这就和非运行入口文件有一样的表现了。

注意，在 Tree 目录下运行`python -m m1`是不可以的，会报 ImportError: attempted relative import with no known parent package 的错误。因为 m1.py 中的`from .Branch import m3`中的`.` ，解释器并不知道是哪一个 package。使用`python -m Tree.m1`，解释器就知道`.`对应的是 Tree 这个 package。

那反过来，如果 m1.py 使用绝对导入（`from Branch import m3`），能使用`python -m m1`运行吗？我试了一下，如果当前目录是 Tree 就可以。如果在其他目录下运行，比如在 Tree 所在的目录（使用`python -m Tree.m1`运行），就不可以。这可能还是与绝对导入相关。

（之前看到了一个大型项目，其运行入口文件有一大堆的相对导入，我还傻乎乎地用 python 直接运行它。之后看到他给的样例运行命令是带了 - m 参数的。现在才恍然大悟。）

理解 import 的难点差不多就这样了。下面说一说 import 的其他简单但实用的用法。

*   `import moudle_name as alias`。有些 module_name 比较长，之后写它时较为麻烦，或者 module_name 会出现名字冲突，可以用 as 来给它改名，如`import numpy as np`。
*   `from module_name import function_name, variable_name, class_name`。上面导入的都是整个模块，有时候我们只想使用模块中的某些函数、某些变量、某些类，用这种写法就可以了。使用逗号可以导入模块中的多个元素。
*   有时候导入的元素很多，可以使用反斜杠来换行，官方推荐使用括号。

```
from Tkinter import Tk, Frame, Button, Entry, Canvas, Text, \
    LEFT, DISABLED, NORMAL, RIDGE, END	# 反斜杠换行
from Tkinter import (Tk, Frame, Button, Entry, Canvas, Text,
    LEFT, DISABLED, NORMAL, RIDGE, END)	# 括号换行（推荐）
```

说到这感觉 import 的核心已经说完了。再跟着上面的博客说一说使用 import 可能碰到的问题吧。

问题 1 描述：ValueError: attempted relative import beyond top-level package。直面问题的第一步是去了解熟悉它，最好是能复现它，将错误暴露在阳光之下。仍然是上面四个文件，稍作修改，四个文件如下：

```
# m1.py
from Branch import m3
m3.printSelf()
# m2.py
def printSelf():
	print('module2')
# m3.py
from .. import m2 # 复现的关键在这 #
print(__name__)
def printSelf():
	print('In m3')
# m4.py
def printSelf():
	print('In m4')
```

运行`python m1.py`，就会出现该问题。问题何在？我猜测，运行 m1.py 后，m1 代表的模块就是顶层模块（参见上面 PEP 328 的引用），而 m3.py 中尝试导入的 m2 模块所在的包（即 Tree 目录代表的包）比 m1 的层级更高，所以会报出这样的错误。怎么解决呢？将 m1.py 的所有导入改为相对导入，然后进入 m1.py 的上层目录，运行`python -m Tree.m1`即可。

对于使用 import 出现的其他问题，碰到了再接着更新。
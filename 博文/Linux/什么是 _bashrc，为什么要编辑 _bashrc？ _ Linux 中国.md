你的 home 目录下藏着很多隐藏文件。如果你在运行 macOS 或者主流的 Linux 发行版的话，你就会在靠近隐藏文件列表的上方看见一个名为 `.bashrc` 的文件。那么什么是 `.bashrc`，编辑 `.bashrc` 又有什么用呢？

![](https://pic1.zhimg.com/v2-bea1dfe0b7057bb03b99fd53183030d0_r.jpg)

如果你运行一个基于 Unix 或者类 Unix 的操作系统，bash 很有可能是作为默认终端被安装的。虽然存在很多[不同的 shell](https://link.zhihu.com/?target=https%3A//www.maketecheasier.com/alternative-linux-shells/)，bash 却是最常见或许也是最主流的。如果你不明白那意味着什么，bash 是一个能解释你输入进终端程序的东西，并且基于你的输入来运行命令。它在一定程度上支持使用脚本来定制功能，这时候就要用到 `.bashrc` 了。

为了加载你的配置，bash 在每次启动时都会加载 `.bashrc` 文件的内容。每个用户的 home 目录都有这个 shell 脚本。它用来存储并加载你的终端配置和环境变量。

终端配置可以包含很多不同的东西。最常见的，`.bashrc` 文件包含用户想要用的别名。别名允许用户通过更短的名字或替代的名字来指向命令，对于经常在终端下工作的人来说这可是一个省时利器。

![](https://pic4.zhimg.com/v2-082554d01df346007d123beedcab46cb_r.jpg)

你可以在任何终端文本编辑器上编辑 `.bashrc`。在接下来的例子中我们将使用 `nano`。

要使用 `nano` 来编辑 `.bashrc`，在终端中调用以下命令：

```
nano ~/.bashrc
```

如果你之前从没有编辑过 `.bashrc` 的话，你也许会发现它是空的。这没关系！如果不是的话，你可以随意在任一行添加你的配置。

你对 bashrc 所做的任何修改将在下一次启动终端时生效。如果你想立刻生效的话，运行下面的命令：

```
source ~/.bashrc
```

你可以添加到任何 `.bashrc` 的位置，随意使用命令（通过 `#`）来组织你的代码。

编辑 `.bashrc` 需要遵循 [bash 脚本格式](https://link.zhihu.com/?target=http%3A//tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)。如果你不知道如何用 bash 编写脚本的话，有很多在线资料可供查阅。这是一本相当全面的[介绍指南](https://link.zhihu.com/?target=https%3A//www.digitalocean.com/community/tutorials/an-introduction-to-useful-bash-aliases-and-functions)，包含一些我们没能在这里提及的 bashrc 的方面。

**相关**： [如何在 Linux 启动时以 root 权限运行 bash 脚本](https://link.zhihu.com/?target=https%3A//www.maketecheasier.com/run-bash-script-as-root-during-startup-linux/)

有一些有用的小技巧能使你的终端体验将更高效，也更用户友好。

## **为什么我要编辑 bashrc ？**

## `Bash 提示符`

bash 提示符允许你自定义你的终端，并让它在你运行命令时显示提示。自定义的 bash 提示符着实能提高你在终端的工作效率。

看看这些即[有用](https://link.zhihu.com/?target=https%3A//www.maketecheasier.com/8-useful-and-interesting-bash-prompts/)又[有趣](https://link.zhihu.com/?target=https%3A//www.maketecheasier.com/more-useful-and-interesting-bash-prompts/)的 bash 提示符，你可以把它们添加到你的 `.bashrc` 里。

## `别名`

![](https://pic1.zhimg.com/v2-c10ab92309fc726553dfd1f772e14750_r.jpg)

别名允许你使用简写的代码来执行你想要的某种格式的某个命令。让我们用 `ls` 命令来举个例子吧。`ls`命令默认显示你目录里的内容。这挺有用的，不过显示目录的更多信息，或者显示目录下的隐藏内容，往往更加有用。因此，有个常见的别名就是 `ll`，用来运行 `ls -lha` 或者其他类似的命令。这样就能显示文件的大部分信息，找出隐藏的文件，并能以 “能被人类阅读” 的单位显示文件大小，而不是用 “块” 作为单位。

你需要按照下面这样的格式书写别名：

```
alias ll = "ls -lha"
```

左边输入你想设置的别名，右边引号里是要执行的命令。你可以用这种方法来创建命令的短版本，防止出现常见的拼写错误，或者让一个命令总是带上你想要的参数来运行。你也可以用你喜欢的缩写来规避讨厌或容易忘记的语法。这是一些[常见的别名的用法](https://link.zhihu.com/?target=https%3A//www.maketecheasier.com/install-software-in-various-linux-distros/%23aliases)，你可以添加到你的 `.bashrc` 里。

## `函数`

![](https://pic1.zhimg.com/v2-be50f2a7100a3be5b973331fede3fa3c_r.jpg)

除了缩短命令名，你也可以用 bash 函数组合多个命令到一个操作。这些命令可以很复杂，但是它们大多遵循这种语法：

```
function_name () {
 command_1
 command_2
}
```

下面的命令组合了 `mkdir` 和 `cd` 命令。输入 `md folder_name` 可以在你的工作目录创建一个名为 “folder_name” 的目录并立刻导航进入。

```
md () {
  mkdir -p $1
  cd $1 
}
```

如你所见，函数中的 `$1` 代表第一个参数，就是你在函数名后紧跟着输入的文本。

## **总结**

不像某些自定义终端的方法，变动 bashrc 是非常直接且低风险的。即使你一不小心全搞砸了，你也可以随时删掉 bashrc 文件然后重新来一遍。试试看吧，你会惊叹于你提高的生产力的。

via: [https://www.maketecheasier.com/what-is-bashrc/](https://link.zhihu.com/?target=https%3A//www.maketecheasier.com/what-is-bashrc/)

作者：[Alexander Fox](https://link.zhihu.com/?target=https%3A//www.maketecheasier.com/author/alexfox/) 译者：[heart4lor](https://link.zhihu.com/?target=https%3A//github.com/heart4lor) 校对：[wxy](https://link.zhihu.com/?target=https%3A//github.com/wxy)

本文由 [LCTT](https://link.zhihu.com/?target=https%3A//github.com/LCTT/TranslateProject) 原创编译，[Linux 中国](https://link.zhihu.com/?target=https%3A//linux.cn/) 荣誉推出
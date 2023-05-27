#shell #LInux

# shell prompt是什么？
[[linux 中 prompt 是什么 - 常见问题 - PHP 中文网]]

prompt是Linux shell 的终端提示符，提示用户进行命令输入。

一般格式为
```bash
[启动shell的用户名@主机名 ~] $
```
$代表普通用户，#代表超级用户
~代表用户主目录，会根据当前所在工作目录变化成对应路径

shell使用PS1和PS2两个环境变量来控制提示符格式，默认使用PS1指定的提示符格式，当输入一个命令后还需要输入附加信息（由shell判断）则shell使用PS2指定的提示符格式。 ^1279f4

PS1和PS2是可以重新定义的，详情请见源博文文档。

# shell 如何识别command line？
[[shell 传递参数方法.pdf]]

在shell prompt后面输入文本，按下enter键，则在enter键和shell prompt之间输入的字符文本就是一条command line（命令行），每个command line的charactor（字符）分为两种：
- literal（字面意义）——普通文字，无特殊功能
- meta（元）——具有特殊功能的保留字

常见的literal有英文字母和数字
常见的meta有IFS（Internal Field Seperator）和CR（Carriage Return）
- IFS由space、enter、tab之一组成，用来划分word，shell命令行按word处理
- CR由enter产生，CR用来结束一条命令行
还有一些常用的meta
- =：设定变量
- $：做变量或运算替换
- ()：将其内的命令置于nested subshell执行，或用于运算或命令替换
[[如何使用shell中的括号？]]

其他常用的meta详见源博文

如果需要将command line中的元功能关闭，需要用到quoting处理（常称为引号处理）：
- soft quote双引号：双引号内大部分meta都关闭，除了$、单引号、反斜线、\`,关闭空格、双引号的meta功能。
- hard quote单引号：单引号内所有meta全部关闭。
- escape反斜线：只有跟在反斜线后的单一meta被关闭
[[shell 中三种引号的用法及区别_shell 双引号里面写 $ 和直接 $ 的区别_Cloud-Future 的博客 - CSDN 博客|如何在shell中使用三种引号？]]

猜测shell执行过程：首先接收每次enter键之前的命令行，然后对于其中的元字符执行对应的元功能，接着分割出word，最后将所有非\$0参数传给\$0对应的程序并执行该程序。
花括号表示soft quoting，关闭了其中的空格和双引号的meta功能。

# export语句语法
Linux export 命令用于设置或显示环境变量。

在 shell 中执行程序时，shell 会提供一组环境变量。export 可新增，修改或删除环境变量，供后续执行的程序使用。export 的效力仅限于该次登陆操作。

语法如下：
`export [-fnp][变量名称]=[变量设置值]`


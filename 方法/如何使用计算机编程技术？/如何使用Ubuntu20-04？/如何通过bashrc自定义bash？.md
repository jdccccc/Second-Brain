#bash #shell #LInux 

>[[什么是 _bashrc，为什么要编辑 _bashrc？ _ Linux 中国]]
# 什么是.bashrc?

.bashrc文件通常指得是bash的配置源文件，可以帮助bash配置别名、路径等，详见引用博文。
bash打开后提示符指向的用户名的主目录下的.bashrc文件就是当前用户的bash窗口的源文件。
bash会在每次启动的时候加载对应的.bashrc文件的内容，bashrc本身也是shell脚本。

使用`source ~/.bashrc`能够使本次bash运行过程中更改后的bashrc文件的配置立即生效。


# 如何设置PATH(路径)？
>[[如何在 Bash Shell Linux 中设置路径？_cunjiu9486 的博客 - CSDN 博客]]
## 什么是PATH？
每次bash中执行一条命令，都将会用首位参数的值和当前工作目录和PATH指定的目录下的文件进行比对，如果一致，则执行该文件代表的程序，并将命令中后续参数传入该程序中进行执行。

## 添加PATH

打印PATH
```bash
loverain@loverain-VirtualBox:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```
PATH的格式是在每个用于搜索二进制文件和库文件的路径之间加上冒号，最后一个路径的后面不需要冒号

想要为当前用户添加新的PATH需要在~/.bashrc文件中添加语句
```
$PATH = 此处写上需要添加的路径:$PATH
```

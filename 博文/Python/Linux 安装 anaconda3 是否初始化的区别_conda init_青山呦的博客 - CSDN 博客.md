Linux 安装 anaconda3 提示是否希望安装程序通过运行 [conda](https://so.csdn.net/so/search?q=conda&spm=1001.2101.3001.7020) init 来初始化 Anaconda3?  
Do you wish the installer to initialize Anaconda3 by running conda init?

官方建议的是选 yes，那么选择 yes 和 no 有什么区别呢？  
1、选择 yes：  
选择 yes 的话，bashrc 文件中会添加以下内容，这样在打开终端时自动执行 conda activate root 命令，这样在终端输入 python 的时候默认是 python3（CentOS7 及 7 以下默认装的是 python2）。  

![](attachments/20200415003547156.png)

  
这样的话，启动虚拟机 shell 命令前面出现 (base) 字样，默认 python3（当然，conda deactivate 这个命令又可以回去）  

![](attachments/20200415003639889.png)

  
2、选择 no：  
选择 no 的话，在安装完 [anaconda](https://so.csdn.net/so/search?q=anaconda&spm=1001.2101.3001.7020) 后需手动添加环境变量：  

![](attachments/20200415004209382.jpg.png)

  
以下是选择 no 的终端 shell 命令格式：  

![](attachments/20200415004420944.png)

这里，终端输入 python，就会选择 python2，当然可以通过以下命令切换到 python3:  
conda activate root

不过，有的小伙伴会问，如果我安装过程选择了 no，但是安装完还想初始化，该怎么操作？可以通过以下命令来实现：  
source /usr/local/src/anaconda3/bin/activate  
conda init  
以实际安装目录为准。  
执行完这两个命令，bashrc 中也会添加上面那些内容。

ps: 以下是官网的建议:  

![](attachments/20200415004834674.png)
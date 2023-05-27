#ubuntu #anaconda #方法 
# 安装

## 九曲栏杆课程中的安装方法
![[LEC02-深度学习入门-实验课#Ubuntu20.04下Anaconda的安装]]


## 气泡水博客安装方法

在按no之前的方式是一致的，主要是no之后激活conda命令的方式不同
![[Ubuntu 20_04 安装 Anaconda3 及简单使用_ubuntu20_04 安装 anaconda_气泡水、的博客 - CSDN 博客#修改环境变量]]

## 两种方式激活conda命令的深刻理解
这里通过研究几种方式的区别来作出更深刻的理解。

### conda shell.bash hook + conda init
分析`eval "$( /home/Loverain/anaconda3/bin/conda shell.bash hook)"`

[[如何使用shell？]]
猜测shell执行过程：首先接收每次enter键之前的命令行，然后对于其中的元字符执行对应的元功能，接着分割出word，最后将所有非\$0参数传给\$0对应的程序并执行该程序。
花括号表示soft quoting，关闭了其中的空格和双引号的meta功能。


[[【Linux】eval 命令的使用_eval linux_seven_0-0 的博客 - CSDN 博客|如何使用eval命令？]]
eval命令扫描两遍其后的参数，第一遍参数中间接引用的变量，第二遍执行替换后的文本代表的命令。

![[Pasted image 20230502180332.png]]
eval 会将其接受到的所有参数字符串中间加一个空格，然后作为命令（cmd）放入到当前shell执行

`$()`元功能是执行括号之间的命令cmd执行后的结果对其进行替换。
![[Pasted image 20230502183359.png]]


`eval "$( /home/Loverain/anaconda3/bin/conda shell.bash hook)"`
此处的指令中没有变量可以替换，在双引号的元功能执行后eval被传入一个参数（空格元功能被取消）。
```bash
$( /home/Loverain/anaconda3/bin/conda shell.bash hook)
```
等同于shell直接执行上面这条指令。
然后shell执行\$()的元功能，执行括号中间的语句

```shell
/home/Loverain/anaconda3/bin/conda shell.bash hook
```
并将其输出填回\$(···)所在的位置，由于这条语句没有执行结果，故而相当于该参数被抹除。

这条括号中间的语句使得当前shell直接能够使用conda（命令）并且进入base模式。
然后执行`conda init`对于`.bashrc`文件进行修改，使得每次进入shell时都执行上述括号中指令。
![[Pasted image 20230502190227.png]]
[[Linux 安装 anaconda3 是否初始化的区别_conda init_青山呦的博客 - CSDN 博客]]

### 修改环境变量

![[如何通过bashrc自定义bash？#添加PATH]]

![[如何使用shell？#export语句语法]]

export语法也可添加环境变量，比如PATH，但是只在当前登录页面生效。
```bash
export PATH="/home/LoveRain/anaconda3/bin:$PATH"
```
表示每次登录时都会引入conda所在的目录作为路径环境变量。

## 三种消除base的方法的深刻理解
### 更改changeps1配置
在condarc中令changeps1等于false，含义是不改变提示符，则进入base模式后提示符不改变，也就不会出现base字样。
![[如何使用shell？#^1279f4]]

### conda deactivate base
[[conda 与 pip 及 conda 的一些常用操作]]
conda是环境管理工具和包管理工具，base是conda默认安装的python环境，加装了包括numpy在内的很多包，可以快速进入开发阶段。
```bash
conda activate base #进入base环境
conda deactivate #退出当前环境
```

## conda config --set auto_activate_base False

conda config --set 命令 对于conda进行设置，这里的设置是取消自动进入base模式的选项。


# 使用
>[[Ubuntu 20_04 安装 Anaconda3 及简单使用_ubuntu20_04 安装 anaconda_气泡水、的博客 - CSDN 博客#5、常用命令]]

>[[conda 与 pip 及 conda 的一些常用操作#conda 的基本命令：]]

```bash
conda activate env_name
conda deactive
```
![[如何在anaconda中建立虚拟环境？]]
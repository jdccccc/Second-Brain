## conda 与 pip 之间的区别：

conda 是包管理器同时也是环境管理器，而 pip 是 python 的管理器。conda 不仅仅可用于 python 语言，也可以用于 R 语言等，而 pip 只能用于 python 语言，conda 的强大之处在于对不同项目的环境管理。

## conda 与 pip 之间的联系：

两个都可以用于 python 包的安装，但两者并不冲突，在使用过程中，pip 搜索源的包数量比 conda 更多，往往会出现 conda 找不到的包但可以使用 pip 安装，**因此，可以使用 conda 先建立虚拟环境，在虚拟环境中使用 conda 或 pip 安装包，从而实现环境隔离以及包资源的最大化**。

## conda 中 base 环境的作用：

base 环境是安装好 anaconda 之后就已经建立的默认环境，包含很多数据分析之类的包，如 numpy，但是由于环境隔离，base 环境仍然与其他环境互不影响，**base 环境可在不需要单独环境的情况下快速进行项目**。

## 能否在已有环境的基础上建立环境：

不同的项目之间的依赖不一样，似乎并没有这样的方法 (要是有知道的大佬可以告知一下），但是我们可以在最初建立环境时使用如下命令，即安装一个 anaconda 的包，这个包包含很多基础的包，如 numpy 等，可以省去我们很多的安装操作：

```
conda create -n env_1 python=3.4.0 anaconda
```

## conda 的基本命令：

1.  查看 conda 基础信息：

```
% conda版本 %
conda -V
% 基本信息 %
conda info
% conda当前环境安装的所有的包 % 
conda list
% 查看当前存在的虚拟环境 %
conda env list 或 conda info -e
% 更新conda %
conda update conda
```

2. conda 添加 pypi 源

```
% 添加源 %
conda config --add channels 源地址
% 删除源 %
conda config --remove channels 源地址
% 源中搜索时显示通道地址 %
conda config --set show_channel_urls yes
% 恢复默认源 %
conda config --remove-key channels
```

3. conda - 环境

```
% 创建环境 %
conda create -n env_name python=x.x.x
% 激活环境 %
conda activate env_name
% 在虚拟环境中安装其他包 %
conda install -n env_name [package]
% 关闭当前虚拟环境，返回默认环境 %
conda deactivate env_name
% 删除环境 %
conda remove -n env_name --all
% 删除环境中的某个包
conda remove --name env_name [package]
% false即取消"退出时自动激活conda的base环境" %
conda config --set auto_activate_base false
```

4. conda 安装 cuda 和 cudnn

```
% 安装cuda %
conda install cudatoolkit=版本号 -c 地址
% 安装cudnn %
conda isntall cudnn=版本号 -c 地址
```
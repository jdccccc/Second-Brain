在安装了 anaconda 之后，conda install 和 pip install 的安装路径默认是一致的，因此不存在什么问题。但是由于不同的项目对于包的版本有着不同的要求，因此采用虚拟环境来避免包依赖之间的冲突。

1.  **检查当前 python 环境依赖冲突**
    
    `python -m pip check`
    
    ![](attachments/v2-98474604e05cd84480a9ff3e22f1332f_b.jpg)
    
    伴随着虚拟环境的使用，之前我们对于 pip 和 conda 的理解就需要进一步加深了。比如我们有两个虚拟环境 base 和 test， 并且此时我们希望在 test 环境中安装包，而且 conda 找不到这个包，只能使用 pip 安装。 这就需要我们对于 pip 和 conda 的安装机制有进一步的认识
    
2.  **进一步认识 conda**
    
    `conda info`
    
    ![](attachments/v2-774239ed43e442899b28f410903b504a_b.jpg.png)
    
    可以看到
    
    1.  当前激活的虚拟环境为 base，也就是最开始安装的 anaconda
        
    2.  这里的 shell level 表示的是当前环境的层数 (套娃), 比如我们此时执行指令 `conda activate test`, 激活 test 环境, 那么 shell level 会变为 2。
        
        ![](attachments/v2-c76c1d03c0f634a6481fbbb140ec2b5b_b.jpg)
        
        因此一般情况下，我们想要切换环境时，最好是先退出当前环境，再激活到想要使用的环境，避免套娃出现问题。
        
        `conda deactivate` 退出当前环境
        
        `conda activate env_name` 切换到想要使用的环境
        
    3.  虚拟环境的目录有三个，默认新创建的虚拟环境会被放在 Anaconda 安装目录里面的 envs 文件夹下面。
        
3.  **包管理**
    
    我们知道，conda 有专门的指令在指定 虚拟环境中安装指定的 package
    
    `conda install -n your_env_name [package]`
    
    一般情况下这就已经满足我们的日常使用了，但是我在安装 `snntoolbox` 的时候, 由于不支持 conda 安装，同时和 base 环境下的 tensorflow 的依赖库版本会有冲突。 因此遇到了这样的问题**在 test 环境下使用 pip 安装包， 该包是否被安装在 test 环境中**。
    
    我们使用 `pip -V` 指令来查看**当前使用的 pip 的路径**
    
    ![](attachments/v2-7555f73abf2de297f848f9b5c1332f3a_b.jpg.png)
    
    可以看到, 在不同的环境下, 所使用的 pip 的路径是不同的, 因此我们大胆猜想，小心求证：**只要切换了虚拟环境，使用 pip 安装 package 就只会装在该虚拟环境中，不会污染其他虚拟环境的包 (Anaconda 其实也是一种虚拟环境 - base)**
    
    我们以 [snntoolbox](https://link.zhihu.com/?target=https%3A//snntoolbox.readthedocs.io/en/latest/guide/installation.html) 为例 (目前不支持 conda 安装), 在 test 环境下安装 `snntoolbox`
    
    `pip install snntoolbox`
    
    ![](attachments/v2-a5c53aca1e630a309bb3b2b90f6150c1_b.jpg.png)
    
    因此, 我们可以得出结论，不同虚拟环境都有自己的 pip。只要记得切换虚拟环境, 我们就可以直接使用 pip 来安张 package, 不会污染其他的虚拟环境
    

## conda 常用命令

1.  更新 conda
    
    `conda update conda`
    
2.  查看安装的包
    
    `conda list`
    
3.  创建虚拟环境
    
    `conda create -n env_name python=x.x`
    
    安装环境默认路径在 Anaconda 目录下的 envs 里面
    
4.  查看虚拟环境
    
    `conda env list`
    
    `conda info -e`
    
5.  激活虚拟环境
    
    `conda activate env_name`
    
6.  在指定虚拟环境中安装 package
    
    `conda install -n env_name [package]`
    
7.  退出虚拟环境
    
    `conda deactivate`
    
8.  删除虚拟环境
    
    `conda remove -n env_name --all`
    
9.  删除环境中的某个包
    
    `conda remove --name env_name package_name`
    

本文使用 [Zhihu On VSCode](https://zhuanlan.zhihu.com/p/106057556) 创作并发布
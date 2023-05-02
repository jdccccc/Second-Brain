[[如何在ubuntu20-04上使用anaconda？#使用]]
[[LEC02-深度学习入门-实验课#Ubuntu20.04下Anaconda的安装]]


>[[d2l-zh-pytorch-anno#^njhiapei13|我们需要配置一个环境来运行Python、Jupyter Notebook、相关库以及运行本书所需的代码，以快速入⻔并获得动手学习经验。]]

[[如何将pdf整合到obsidian笔记系统中？]]

```bash
conda info -e #查看当前存在哪些环境
conda list #查看安装了哪些包
conda create -n d2l python=X.X -y #创建新的py环境
conda activate d2l #激活d2l环境
pip install torch==1.12.0  
pip install torchvision==0.13.0
pip install d2l==0.17.6
```

由于各种开发环境之间的包依赖问题，最好采用虚拟环境的方式来进行py开发。
[[如何在anaconda中建立虚拟环境？]]


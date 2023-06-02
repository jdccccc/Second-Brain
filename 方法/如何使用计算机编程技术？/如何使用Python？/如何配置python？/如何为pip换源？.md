#pip #python

[[PIP 更换国内安装源_pip 换源_SoloLinux 的博客 - CSDN 博客]]
**永久修改：**   
**linux:**   
修改 ~/.pip/pip.conf (没有就创建一个)， 内容如下：

```
[global]index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```

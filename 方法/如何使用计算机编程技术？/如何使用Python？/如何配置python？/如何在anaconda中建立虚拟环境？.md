#ubuntu  #anaconda 

不同虚拟环境中使用pip进行安装的python包都是相互隔离的。[[python 包管理之 conda 与 pip]]

```bash
conda create -n newenv_name python=X.X #建立新环境
pip -V #查看pip包安装位置位置

```

![[Pasted image 20230502224524.png]]
不同的虚拟环境的pip的的安装位置是不同的。

- pip install包安装位置：`pip -V`显示的位置
- conda install包安装位置：和pip的一致
- conda list显示包位置：当前环境的包的位置
	![[Pasted image 20230502230755.png]]
	如果不在任何环境中，默认显示base的包的位置
	![[Pasted image 20230502230926.png]]
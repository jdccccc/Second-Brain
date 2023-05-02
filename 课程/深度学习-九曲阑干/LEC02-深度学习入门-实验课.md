> [[d2l-zh-pytorch.pdf]]

# Ubuntu20.04下Anaconda的安装

1. Ubuntu20.04 [[如何在VirtualBox上安装Ubuntu20-04？]] 上安装Anaconda[[如何在ubuntu20-04上使用anaconda？]] （需要一定的Linux基础[[Linux常用shell命令]]）
	1. wget命令
	2. 最新版本的上一个版本
	
	![[Pasted image 20230429200125.png]]
	![[Pasted image 20230429200300.png]]
	![[Pasted image 20230429200021.png]]


2. 使用chmod +x为anaconda安装包添加可执行文件权限
	![[Pasted image 20230429200349.png]]	
 
3. 启动安装程序，一路点击yes
	如果shell自动填写no
	![[Pasted image 20230429202329.png]]
	则手动输入提示的指令激活conda命令
	![[Pasted image 20230429202356.png]]

	![[Linux 系统终端出现（base）怎么解决？]]
	这种方式只能在一个终端窗口中生效
	
	![[终端命令行前出现 (base) 怎么办？_终端前面出现 base_Cyber One-Punch Man 的博客 - CSDN 博客]]
	这种方式可以永久生效

	还有一种方式是在.condarc的最后一行加上`changeps1: False`,也能够生效。

	猜测：第一种方式告诉我，base是conda的一种模式，第二种方式告诉我，conda在.bashrc中加入了自动开启base模式的一条命令，使得每次打开shell时都会自动进入base模式，第三种方式应该是在base模式下不显示base字样，我目前不选择第三种方式，这样的方式可能会让我无法分辨base模式和正常模式

	还有一种方式是输入`source .bashrc`使得.bashrc文件生效激活conda命令，但不需要输入之前提示中的命令，我没有尝试，仅提供一种可能性。

4. 为anaconda换源
	使用`conda info`查看channel包管理工具的源
	![[Pasted image 20230501164138.png]]
	在清华镜像网站中找到需要拷贝到.condarc中的文本片段，进行拷贝
	![[Pasted image 20230501164656.png]]

# Pytorch的安装

1. 进入Pytorch的官网，在get started栏目中找到对应版本的安装命令，复制到终端运行
	![[Pasted image 20230501165816.png]]

2. 检查python、pytorch的版本
	![[Pasted image 20230501170630.png]]

# 数据集的训练

## 代码下载数据集

```python
import torch 
import torchvision
from PIL import Image
import numpy #处理任意维数组的py库
train_data = torchvision.datasets.MNIST( './data',
			train = True,
			download = True,
			transform = torchvision.transforms.ToTensor())
			
test_data = torchvision.datasets.MNIST( './data',
			train=False,
			download= True,
			transform = torchvision.transforms.ToTensor()) 
#torch.Tensor是存储和变换数据的主要工具。Tensor表示张量，0维张量是标量，1维张量是向量，2维张量是矩阵。张量可以看成是多维数组。

def main():
	print(len(train_data), len(test_data))
	img, label = train_data[1]
	np_img = img.numpy()
	re_img = np_img.reshape(28, 28)
	ary = numpy.uint8(numpy.around(re_img))
	#show
	print(ary)
	print("****************************") 
	print("Label is:" , label)

	#normalization to bmp
	ary *= 255 ;

	#convert array to image
	pil_img = Image. fromarray(ary, mode= 'L')
	pil_img.save(" ./tmp.png" );

main();
```



## 1、[Anaconda](https://so.csdn.net/so/search?q=Anaconda&spm=1001.2101.3001.7020) 安装包下载

（1）[官网下载](https://www.anaconda.com/products/individual#download-section)，下载速度较慢  
（2）[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)

## 2、安装 Anaconda

（1）进入文件下载目录

```
cd ~/software
```

（2）运行安装包

```
bash Anaconda3-2020.07-Linux-x86_64.sh
```

（3）回车键，进入注册信息页面  

![](attachments/20200904144027122.png)

  
（4）按 q 跳过阅读，yes  

![](attachments/20200904144138422.png)

  
（5）默认安装在用户目录下，直接回车即可安装；若想自定义安装目录，直接输入安装目录，回车即可。  

![](attachments/20200904144244232.png)

  
（6）Do you wish the installer to initialize Anaconda3 by running [conda](https://so.csdn.net/so/search?q=conda&spm=1001.2101.3001.7020) init ? 输入 no，回车  

![](attachments/20200904144527327.png)

  
（7）看到下面的提示信息说明安装完成。  

![](attachments/20200904144627768.png)

## 修改环境变量

将 Anaconda 添加到用户环境变量中

```
vim ~/.bashrc
```

添加下面内容

```
export PATH="/home/ssj/anaconda3/bin:$PATH"
```

source 一下

```
source ~/.bashrc
```

## 4、检查是否安装成功

查看版本  

![](attachments/20200904150151937.png)

输入 python3，发现是 Anaconda 安装的版本  

![](attachments/20200904150136583.png)

## 5、常用命令

```
#创建虚拟环境
conda create -n your_env_name python=X.X（3.6、3.7等）
 
#激活虚拟环境
source activate your_env_name(虚拟环境名称)
 
#退出虚拟环境
source deactivate your_env_name(虚拟环境名称)
 
#删除虚拟环境
conda remove -n your_env_name(虚拟环境名称) --all
 
#查看安装了哪些包
conda list
 
#安装包
conda install package_name(包名)
conda install scrapy==1.3 # 安装指定版本的包
conda install -n 环境名 包名 # 在conda指定的某个环境中安装包
 
#查看当前存在哪些虚拟环境
conda env list 
#或 
conda info -e
#或
conda info --envs
 
#检查更新当前conda
conda update conda
 
#更新anaconda
conda update anaconda
 
#更新所有库
conda update --all
 
#更新python
conda update python
```
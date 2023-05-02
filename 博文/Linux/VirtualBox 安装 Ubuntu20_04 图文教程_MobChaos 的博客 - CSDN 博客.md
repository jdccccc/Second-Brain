# Virtual Box 安装虚拟机

## 一、下载安装 Virtual Box

### 1. 下载 Virtual Box

VirtualBox 的官方下载网址：[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

![](attachments/c1c0d3b8e7d74152b6d85f2cf871c16a.png)

### 2. 安装 Virtual Box

双击 Virtual Box 安装程序进入安装欢迎界面，如下图所示：

![](attachments/9a9245c9901c40c7815e9f4b9fa76e87.png)

单击 `下一步` 按钮后进入下一安装界面，在此界面中，可以选择要安装的功能和磁盘存储位置 ，如下图所示：

![](attachments/2cccce3eb704416880e2b06f14012d81.png)

单击`下一步`按钮后进入下一安装界面，如下图所示：

![](attachments/21703c49f88b45719b70276c0f430fc1.png)

单击`下一步`按钮后进入下一安装界面，如下图所示：

![](attachments/b7ef9a4bbf4c494ea5b7418e4b2634cf.png)

单击`是`按钮后进入下一安装界面，如下图所示：

![](attachments/65683c0d771442d9bc8bc40d9979a614.png)

单击`安装`按钮后等待安装，安装完成后进入完成界面，点击`完成`按钮完成安装，如下图所示：

![](attachments/0ad64979b6ae4f53ac623edc37c9a765.png)

重启电脑，完成 Virtual Box 安装

## 二、Virtual Box [安装 Ubuntu](https://so.csdn.net/so/search?q=%E5%AE%89%E8%A3%85Ubuntu&spm=1001.2101.3001.7020)

### 1. 下载 [Ubuntu 镜像](https://so.csdn.net/so/search?q=Ubuntu%E9%95%9C%E5%83%8F&spm=1001.2101.3001.7020)

Ubuntu 镜像官方下载网址：[https://cn.ubuntu.com/download/desktop](https://cn.ubuntu.com/download/desktop)

![](attachments/2eaa7621705e4840a9fa920dc5f29fd2.png)

### 2. Virtual Box 创建虚拟机

打开 Virtual Box，单击`新建`按钮，出现`新建虚拟电脑`对话框，在对话框中自定义名称和存储路径，类型选择 Linux，版本按照自己下载的镜像选择 32 位或 64 位，如下图所示：

![](attachments/d05911ae4929438abfd27604eeaae1f7.png)

单击`下一步`按钮，根据自己的需要和计算机内存情况分配大小，如下图所示：

![](attachments/22ac7d23617441abb120a1670a766e70.png)

单击`下一步`按钮，在虚拟硬盘界面选择现在创建虚拟硬盘，如下图所示：

![](attachments/a74442d9b0a442c4823c42abf513ff2f.png)

单击`创建`按钮，在虚拟硬盘文件类型界面选择`VDI`，如下图所示：  

![](attachments/633017cf5e864ada9df328c22e5afe0e.png)

单击`下一步`按钮，在存储在物理硬盘上界面选择动态分配，如下图所示：

![](attachments/4830bb6320fb4bc3b24d19aa6378b23a.png)

单击`下一步`按钮，在文件位置和大小界面设置文件位置，并根据需要设置虚拟硬盘大小，如下图所示：

![](attachments/7e72b109c6554e36b336d8f20f7dca5b.png)

单击`创建`按钮，虚拟机创建成功，可以单击`设置`按钮，选择`系统`选项中的`处理器`选项设置处理器数量，如下图所示：

![](attachments/ba166bf88371408bb56088f3d6eb1f21.png)

### 3. Virtual Box 安装 Ubuntu

选择刚刚创建的虚拟机，单击`设置`按钮，在菜单栏里依次`选择存储` → `没有光盘` → `没有光盘图标` → `选择一个虚拟光盘文件选项`，进入虚拟光盘选择界面，如下图所示：

![](attachments/b99fc01fe5c64792b62a7abc4acbc64d.png)

单击`注册`按钮，在弹出的`文件对话框`中选择 Ubuntu 的 iso 镜像文件，如下图所示：

![](attachments/240905f8a4e1487f962b060d66a49c4f.png)

单击`打开`按钮后，回到虚拟光盘选择界面，选择刚刚注册的虚拟光盘，如下图所示：

![](attachments/669f88af8eb04e20b345c7c24c69c543.png)

单击`选择`后，再单击`OK`按钮，完成虚拟光盘的设置，如下图所示：

![](attachments/ee77181d5d2d4f128128d5060f46ff17.png)

单击`启动`按钮启动虚拟机，开始安装 Ubuntu，如下图所示：  

![](attachments/67c42c2101364780a8583c9d8d34b26d.png)

进入`欢迎`界面，选择 Ubuntu 系统语言为`中文（简体）`，然后单击`安装Ubuntu`按钮进行安装，如图所示：  

![](attachments/b2861d5991d64a4eb4056c827b12b2ed.png)

进入`键盘布局`界面，默认设置即可，单击`继续`按钮（**如果没有看到`继续`按钮，这是由于计算机的分辨率问题导致的，遇到这种情形时，可以按住键盘的`Win`键移动鼠标拖动界面，其他版本的 Ubuntu 可能是`Alt`键** ），如图所示：

![](attachments/0a1cacfabbc44edfa65a755dfc556643.png)

进入`更新和其他软件`界面，选择`最小安装`并勾选`为图形或无线硬件，以及其他媒体格式安装第三方软件`，然后单击`继续`按钮，如图所示：

![](attachments/51670b14205b4d03897b4ed859a1f389.png)

进入`安装类型`界面，默认选中`清除整个磁盘并安装 Ubuntu`，然后单击 `现在安装` 按钮，如图所示：

![](attachments/97a2da1ddf3e4a21a447ef0f04d7da5e.png)

在弹出的`将改动写入磁盘吗？` 对话框中，单击 `继续` 按钮，如图所示：

![](attachments/7cd2bff12e014605a23a022d558a9930.png)

进入`你在什么地方？`界面，默认`Shanghai`即可，单击`继续`按钮，进入`你是谁？`界面，设置姓名，计算机名，选择一个用户名并设置账号密码 ，然后单击`继续`按钮，如图所示：  

![](attachments/899fb7f924494e0994a41184b846a28b.png)

  

![](attachments/fed42136d3f448539314bb15cfde2cc5.png)

接下来就开始安装 Ubuntu，等待安装，Ubuntu 系统安装完成后，需要重新启动，在 `安装完成` 对话框中单击 `现在重启` 按钮，如图所示 ：

![](attachments/388f720063b94d8c946610f3c3c08e94.png)

至此，Ubuntu 就安装完成了

## 三、Virtual Box 配置 Ubuntu

### 1. 安装增强功能

单击虚拟菜单栏的`设备`选项，选择`安装增强功能`，如下图所示：

![](attachments/da6c120bd14243b999c85d292a74f1ff.png)

在弹出的对话框中，单击`运行`按钮，认证密码，等待安装，安装完成后按回车键退出，如下图所示：

![](attachments/927943d60e354bb48e5a6165c215b41f.png)

  

![](attachments/4c9cda1901e744b49817b146a6bfed16.png)

在虚拟机菜单栏中，单击`设备`选项，选择`共享粘贴板` -> `双向`，设置共享粘贴板，如下图所示：

![](attachments/2158fc21d3c648eabd40b8ac3409dac5.png)

在虚拟机菜单栏中，单击`设备`选项，选择共享文件夹，设置共享文件夹，在弹出的对话框中设置 windows 共享文件夹路径和共享文件夹名称，勾选`固定分配`，如下图所示：

![](attachments/e35c65705ccd4c48915aa3dbf0963022.png)

![](attachments/19cdf4bdf8a94dd5b7ab1db51937fd00.png)

按下`crtl+alt+t`快捷键打开终端，输入以下指令：

```
cd /mnt
sudo mkdir share
sudo mount -t vboxsf VirtualBox_Share /mnt/share # VirtualBox_Share为自己的共享文件夹名称
```

而后输入`sudo gedit /etc/fstab`，打开的编辑器最后一行添加如下语句`VirtualBox_Share /mnt/share vboxsf rw,gid=1000,uid=1000,auto 0 0`，其中 VirtualBox_Share 为自己的共享文件夹名称，然后单击`保存`按钮，如下图所示：

![](attachments/f6f506ef0da146c387d6925577a22d32.png)

至此，增强功能安装完毕

### 2. 更换 “源” 服务器

打开左下角的`开始`菜单，选择`全部`，点击`软件和更新`图标，如下图所示：

![](attachments/761a0773a35643018db32378d7d248a1.png)

打开`下载至`的下拉框，选择`其他站点`，如下图所示：

![](attachments/14ee0da98bce48ecbb46f9fa627de628.png)

在弹出的`选择下载服务器`的对话框中，单击`选择最佳服务器`按钮，一段时间后单击`选择服务器`按钮，如下图所示：

![](attachments/46af231f4b4c499a9e9fb538568be2dd.png)

单击`关闭`按钮后弹出对话框，选择`重新载入`按钮，如下图所示：

![](attachments/569d3fd19a7645c683174f835ed57f0a.png)

至此，完成源服务器的更新

### 3. 更新系统

打开左下角的`开始`菜单，选择`全部`，点击`软件更新器`图标，而后更新系统，更新完成后重启电脑，如下图所示：

![](attachments/3ad834100dcb4325a8477a3b19d0e1cb.png)

### 4. 完善语言

打开左下角的`开始`菜单，选择`全部`，点击`设置`图标，如下图所示：

![](attachments/b5968a2153d14cebac65a935f35e9a1f.png)

在`设置`界面，选择`区域和语言` -> `管理已安装的语言` -> `安装`，安装完成后不用重启，只用重新登录即可，如下图所示：

![](attachments/d09697b52e5b434183e21bd8d435fb19.png)

## 四、其他注意事项

### 1. 无法安装 64 位虚拟机问题

需要进入`BIOS`开启 CPU 虚拟化才能安装 64 位虚拟机，联想 Y7000 操作过程是开机时狂按`F2`键进入`BIOS`界面，而后进入`Configuration`选项，将`Intel Virtual Technology`设为 Enable，最后按 F10 保存并离开，如下图所示：

![](attachments/712121b6f1f94d37bc53966f012db2f1.png.jpg)

### 2. 安装 Ubuntu 过程分辨率问题

安装过程，Ubuntu20.04 可以按住键盘的`Win`键拖动键盘，其他版本的 Ubuntu 可能是`Alt`键

### 3. Ubuntu 分辨率问题

安装完增强功能重启后，放大按两次`右ctrl+c`应该就可以了

### 4. Virtual Box 6.1.30 和 Ubuntu 20.04.03 下载

链接：[https://pan.baidu.com/s/1EneZaEbgP_q7LTzmoAcOXQ](https://pan.baidu.com/s/1EneZaEbgP_q7LTzmoAcOXQ)  
提取码：agvq
1. 在BIOS中让Intel Virtualization Enable使能
2. 确认虚拟化功能已经开启，在windows下的任务管理器的性能的CPU界面，看到虚拟化已启动
3. 安装VMware，并且找到认证码。（VM有两种版本，Player和Pro，player简陋一些）
4. 下载Ubuntu18.04的镜像（目前较稳定版）
5. 在VMware中新建第4步下载的Ubuntu虚拟机
	- 命名可以改成便于识别的名字
	- 最大磁盘容量大小改成80G
	- 选择存储为单个文件，加快运行速度
	- 在自定义硬件中打开处理器的虚拟化引擎的Intel（ARM） Vt-x/EPT功能
	- 网络适配器使用NAT模式
6. 勾选自动开启虚拟机的按钮，完成设置后开始自动安装
7. 关闭Ubuntu的自动更新功能（软件和ubuntu版本）
8. 设置中切换到华为云源，然后reload
9. 更改时区到中国上海
10. Ubuntu下配置samba
	1. `sudo apt install samba`
	2. /etc/samba/ 下`sudo chmod a+w smb.conf`
	3. 在smb.conf末尾加上
	```samba
	[atom]
	   path = /home/atom
	   guest ok = yes
	   read only = no
	```
	4. 在/etc/samba下重启服务`service smbd restart`
	5. 安装网络工具`sudo apt install net-tools`
	6. `ifconfig`查看当前IP地址
11. windows的文件界面中的网络一栏下输入`\\<刚刚查到的ubuntu虚拟机的Ip地址>`
12. 在Ubuntu下的/home/atom中将Document文件夹的权限改为所有人可读可写
13. 在VMware的虚拟网络编辑器中找到Ubuntu虚拟机对应的设置界面，打开DHCP设置，将刷新时间尽量延长，防止ubuntu虚拟机的IP地址映射频繁变动
14. 另外一种解决频繁IP变动的方法：
		在smb.conf的workgroup下再缩进加上`NetBIOS name = <主机名>`
15. 在ubuntu下安装git`sudo apt install git`
16. 配置git
	```shell
	jdc@ubuntu:~$ git config --global user.name "lvrain"
	jdc@ubuntu:~$ git config --global user.email "2019743214@qq.com"
	jdc@ubuntu:~$ git config --global credential.helper store
	```
17. 安装码云
```shell
wget https://gitee.com/oschina/repo/raw/fork_flow/repo-py3
sudo cp repo-py3 /usr/local/bin/repo
sudo chmod a+x /usr/local/bin/repo
sudo apt install python-pip3
pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
```
18. 详见[OpenHarmony入门文档][https://gitee.com/openharmony/docs/blob/master/zh-cn/device-dev/quick-start/quickstart-lite-env-setup.md#%E5%87%86%E5%A4%87%E5%B7%A5%E4%BD%9C]

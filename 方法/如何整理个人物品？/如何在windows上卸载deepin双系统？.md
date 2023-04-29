#Windows #存储清理 #电脑使用方法 #文件系统 #方法 

1. 打开win10下的磁盘管理工具，按Windows键+X键就可以在弹出来的菜单中找到磁盘管理
	打开后找到当时安装deepin的分区，在哪个分区右击删除卷即可

2. 刚才已经删除了deepin的系统文件，但是还有grub引导程序没有删除（这时如果重启会出现grub界面，如果你已经重启进入grub界面，并没有进入Windows选项很简单，进入BIOS将Windows设置为第一启动项，保存重启后即可进入Windows）。

	在win下，下载磁盘工具[_DiskGenius_](http://www.baidu.com/link?url=s5PYJLycb3kGgwtyoa_0QxEWg45kT3IMCafVnfJs7xCuuM8HHKPo2ubmt0O-qqdo)
	[下载地址](http://www.diskgenius.cn/download.php)

	存在Boot、deepin、Microsoft三个文件夹，将Boot、deepin删除即可，删除方式为，在软件的右边，进入到EFI下，选择彻底删除

3. 上一步中删除了deepin的引导文件，但是这个时候进入BIOS发现还是有deepin的启动项，在百度上搜索下载EasyUefi，下载安装好后，打开它，如图选择管理EFI启动项。
	下图为删除完成后的状态。
	![[Pasted image 20230418134345.png]]
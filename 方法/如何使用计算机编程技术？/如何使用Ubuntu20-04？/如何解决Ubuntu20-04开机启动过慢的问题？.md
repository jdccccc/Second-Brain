#ubuntu #开机过慢

```shell
# 查看开机时间
systemd-analyze time


# 查看具体占用多时间的程序
systemd-analyze blame

# 禁用速度过慢的启动服务#
sudo systemctl disable xxx.service
```

如果是在虚拟机virtualBox上运行Ubuntu，启动过慢的原因可能是增强程序没有正确安装[[如何正确安装VirtualBox增强功能？]]
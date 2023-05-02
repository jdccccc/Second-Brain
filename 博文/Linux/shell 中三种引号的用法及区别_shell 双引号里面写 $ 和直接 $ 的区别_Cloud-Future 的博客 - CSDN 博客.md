Linux Shell 中有三种引号，分别为双引号（""）、单引号 (' ') 以及反引号(\`)。

其中双引号对字符串中出现的 $、''、\` 和 \\ 进行替换；单引号不进行替换，将字符串中所有字符作为普通字符输出，而反引号中字符串作为 shell 命令执行，并返回执行结果。具体含义如下：

*   双引号（""）：在双引号中，除了 $,'', \` 和 \\ 以外所有的字符都解释成字符本身。
*   单引号（''）：在单引号中所有的字符包括特殊字符（$,'',\` 和\\）都将解释成字符本身而成为普通字符。
*   反引号（\`）：在反引号中的字符串将解释成 shell 命令来执行。

举例：

```
root@gyb-ubuntu:~# echo "$PATH"
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```

可以看到在双引号中，$ 被作为特殊字符处理，PATH 被解释为变量。

```
root@gyb-ubuntu:~# echo '$PATH'
$PATH
```

在单引号中，特殊字符也失去了特殊意义作为普通字符输出。

```
root@gyb-ubuntu:~# echo ls
ls
```

ls 是一个 shell 命令，直接 echo ls shell 会将 ls 作为普通字符输出。如果我们加上反引号就不一样了，

```
root@gyb-ubuntu:~# echo `ls`
99.sh cloud_curr_design cloud_curr_design.tar.gz exefile for.sh gyb_virsh httpd-2.2.31 qemu_help readfile.sh switch.sh temp temp10.sh temp1.sh temp2.sh temp3.sh temp4.sh temp5.sh temp6.sh temp7.sh temp8.sh temp9.sh te.sh test9.sh ubuntu1204Server.img ubuntu1204Server.xml ubuntuGuest.xml ubuntu-server.img win7.img
```

加上反引号之后，shell 将 ls 作为命令执行，并将结果返回。
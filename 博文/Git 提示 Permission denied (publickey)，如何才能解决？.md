首先确认下你的 Linux/Mac/Wins 当前用户对于 git 工程所在的本地文件夹, 是否具有 777 权限, 没有的话, 先设置一下.

因为即使你把 root 用户的 ssh 加到 GitHub 后, 操作系统的子账户并不能具有 ssh 的权限.

如果具有 777 权限, 可以进行下面的检查:

下面的方案前提是你对文件夹有 777 权限.

## **电脑只有一个 git 环境**

如果你的电脑只有一个 git 环境，那么极大多数情况是由于 GitHub 账号没有设置 ssh 公钥信息所致。 前往 GitHub 网站的 "account settings"

依次点击 "Setting -> SSH Keys"->"New SSH key"

Title 处填写 “id_rsa.pub” 或其他任意信息。 key 处原样拷贝下面命令的打印 `~/.ssh/id_rsa.pub` 文件的内容：

```
cat ~/.ssh/id_rsa.pub      # 控制台上输出内容
pbcopy < ~/.ssh/id_rsa.pub # 自动拷贝到粘贴板
```

如没有则按下述方法生成：

```
ssh-keygen -t rsa
```

输入文件名的地方输入可以输入自定义文件名，默认是 id_rsa，然后一路回车......

注意如果自定义文件名的话，需要加一个 config 文件，下文有介绍。

最后，输入

```
ssh -T git@github.com
```

如果没有报错，

再尝试输出就应该有了

```
cat ~/.ssh/id_rsa.pub      # 控制台上输出内容
pbcopy < ~/.ssh/id_rsa.pub # 自动拷贝到粘贴板
```

或者说设置了 sshkey 还是 permission denied 怎么回事?

回到如下命令，检查当前配置的 SSH 对应的 git 账号；

```
ssh -T git@github.com
```

然后用如下命令 (id_rsa 对应目标账户的私钥) 命令，制定目标 Git 账号

```
ssh-add -K ~/.ssh/id_rsa
```

## **电脑有多个 git 环境**

如果尝试了上面的方法还是不行，那么可能你用了多个密钥，你在新建秘钥的时候使用了自定义的名称，比如 github_rsa，你需要再配置一个 config 文件

```
cd ~/.ssh/
vi config
```

输入以下内容:

```
Host github
    User git 
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/github_rsa
    ServerAliveInterval 300
    ServerAliveCountMax 10
```

ESC+:wq 保存退出

重新尝试以下命令即可搞定:

注意⚠️：@ 符号前后的参数要与上面 User 和 HostName 对应上，一般公司内部的代码仓库都是自定义的，注意修改上面的参数然后再匹配下面的进行测试：

```
ssh -T git@github.com

ssh-add -K ~/.ssh/github_rsa
```
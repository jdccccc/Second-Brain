# Git使用入门——远程仓库
## 空白远程仓库创建、推送与修改
1. 首先在github上创建一个空白repository
2. 将本地的仓库与之关联，输入命令
    ```bash
    #根据github官网上的提示，建立一个远程推送的映射
    #这里起名叫做origin，https是远程仓库的推送地址
    $git remote add origin git@github.com:jdccccc/NOTES.git

    #将工作目录所在的版本库推送到origin对应的远程仓库的master分支上
    #-u表示将本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时可以简化命令
    $git push -u origin master

    #之后本地作了版本之后可以不加-u就推送版本库
    $git push origin master
    ```
    >注：此步骤若遇到访问失败问题，见本文ssh连接部分解决
3. 更改远程仓库的映射
    ```bash
    #remote -v查看映射信息
    $git remote -v

    #根据名字删除
    $git remote rm origin
    ```

## SSH连接
1. 点击进入github中的`setting`标签中
2. 点击进入`SSH and GPG keys`选项
3. 点击右侧的`New SSH key`选项
4. 向Key输入本机的SSH公钥串，Title窗口中输入合适的名称
    生成本机SSH公钥方法：
    1. shell中输入ssh-keygen
    2. 选择存储的位置（默认为用户目录下的.ssh/id_rsa.pub）
    3. 进入id_rsa.pub文件并复制全部内容即公钥到Key窗口中。


## 从远程库克隆
```bash
#通过ssh进行克隆，可以在github仓库网页上找到ssh连接串
$git clone git@github.com:example.com
```
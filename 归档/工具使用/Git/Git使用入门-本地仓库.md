# Git使用入门——本地
## Git安装
- windows官网下载安装程序，默认安装
- Linux下命令行用对应的软件源安装，或者源码安装
>由于每个系统下安装方法都有差异，请自行搜索相应系统安装方法，本教程在Linux环境下完成测试。

安装完成后，测试Git是否可以使用，在shell（windows下cmd）中输入
```bash
$git --version
```
如果有显示`git version xxxxx`，xxxx表示版本号，则表示安装成功

接下来进行全局设置，设置机器的名字和Email地址
```bash
$git config --global user.name "[Your Name]"
$git config --global user.email "[email@example.com]"
```

## Git本地版本库管理
### 工作区、版本库
### 创建、添加、删除文件
版本库（repository），即一个文件目录，可以被Git掌控管理。
1. 创建版本库空目录
    ```bash
    $mkdir test #在shell当前所在工作目录下创建一个空目录 
    $cd test    #进入test目录（工作目录改为test）
    ```
2. 初始化版本库
    ```bash
    $git init
    ```
    >初始化完成后工作目录下多出一个.git文件（隐藏文件），说明当前目录已经建立了版本库。
3. 添加文件到版本库
    Git仅能跟踪文本文件，不能跟踪二进制文件的具体改动。
    此处我们以向test版本库创建并添加一个README.md文件为例。
    ```bash
    #当前工作目录是刚刚创建的版本库test所在目录
    #touch命令向当前工作目录下创建一个新文件，是对于当前工作目录的一种修改。
    #同理，rm文件也是一种修改。
    $touch README.md

    #git add将README.md文件添加到暂存区
    $git add README.md
    
    #git commit将暂存区中的文件提交到仓库中去（即版本库）
    #-m 后的字符串表示这一次提交相关的信息描述
    #$git commit -m "<message>"
    $git commit -m "first commit"
    ```
4. 从版本库中删除文件
    ```bash
    $rm README.md
    $git rm README.md
    $git commit -m "delete"
    ```

### 版本更替
1. 更新版本
    ```bash
    #status可以查看当前暂存区的状况，包括是否修改文件，是否新建或删除文件
    $git status
    #diff查看<file>更改内容
    #$git diff <file>
    $git diff README.md

    #再次使用add命令可以将指定文件放入暂存区
    #$git add <file1> [file2,...]
    $git add README.md

    #使用commit将暂存区中的文件装入仓库
    #$git commit -m "<message>"
    $git commit -m "something has changed"
    ```

2. 回退版本
    ```bash
    $git log    #查看提交的版本日志
    $git log --pretty=oneline   #精简的提交版本日志

    #HEAD表示当前版本，HEAD^表示上一个版本
    #HEAD^^表示上上一个版本，HEAD~100表示前第100个版本
    $git reset --hard HEAD^#回到上一个版本

    #$git reset --hard commit_id 回到确定版本号的版本
    $git reset --hard 1094abd

    #reflog可以查看命令历史，用于确定回到未来的哪个版本
    $git reflog    
    ```


3. 撤销修改
    ```bash
    $git checkout -- README.md
    #将暂存区的修改撤销掉，重新放回工作区
    $git reset HEAD README.md
    ```


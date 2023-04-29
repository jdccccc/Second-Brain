#git  #github #方法 

# 创建新仓库

- 创建新文件夹，打开

- 执行

  ```bash
  git init
  ```

- 创建成功




# 检出仓库

执行如下命令以创建一个本地仓库的克隆版本

```bash
git clone /path/to/repository
```

如果是远端服务器上的仓库，你的命令会是这个样子

```bash
git clone username@host:/path/to/repository
```



# 工作流

你的本地仓库由git维护的三棵“树”组成。

- 第一个是你的`工作目录`——它持有实际文件
- 第二个是`暂存区`——它像个缓存区域，临时保存你的改动
- 最后是`HEAD`——它指向你最后一次提交的结果

![image-20220530211138602](attachments/image-20220530211138602.png)



# 提交和添加

你可以提出更改（把它们添加到暂存区），使用如下命令：
`git add <filename>`
`git add *`

>[[github 报错：The file will have its original line endings in your working directory_大扬哥啦啦啦的博客 - CSDN 博客]]

使用如下命令以实际提交改动：
`git commit -m "代码提交信息"`
现在，你的改动已经提交到了 **HEAD**，但是还没到你的远端仓库。

>[[解决使用 Git 时报错 bash： $'-302-226git'： command not found]]


# 推送改动

你的改动现在已经在本地仓库的 **HEAD** 中了。执行如下命令以将这些改动提交到远端仓库：
`git push origin master`
可以把 *master* 换成你想要推送的任何分支。

如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加：
`git remote add origin <server>`
`<server>` 例如`git@github.com:jdccccc/Second-Brain.git`
如此你就能够将你的改动推送到所添加的服务器上去了。

```bash
git remote -v
```
可以查看所有的远程仓库。


> 此时可能会产生错误
>
> “git@github.com: Permission denied (publickey).
>
> 解决方案见下一个条目



# SSH Keys配置

1. 验证邮箱是否与Github注册时输入的是否一致<img src="https://cdn.jsdelivr.net/gh/jdccccc/PictureBed/img/202205302129853.png" alt="image-20220530212953813" style="zoom: 200%;" />
	```bash
	git config --global --list
 ```
 
2. 生成一个.ssh文件夹，密钥存储在其中

   ```bash
   ssh-keygen -t rsa -C 
   ```

   ssh-keygen -t rsa -C “这里换上你的邮箱”，一路回车，在出现选择时输入Y，再一路回车直到生成密钥，命令执行完成后会提示生成位置。
   ![[Pasted image 20230429170440.png]]

3. 到git仓库，添加密钥![image-20220530213602990](attachments/image-20220530213602990.png)

   不是上图所在的项目设置，而是下图所示的帐号设置

   ![image-20220530213840199](attachments/image-20220530213840199.png)

​  ![image-20220530214235336](attachments/image-20220530214235336.png)				

![image-20220530214323095](attachments/image-20220530214323095.png)

- title中输入sshKey的名称
- Key中输入pub文件的内容

使用`ssh -T git@github.com`命令查看ssh是否认证成功。


4. 再次使用push查看是否能够推送项目内容

>[[Git 提示 Permission denied (publickey)，如何才能解决？]]


# 更新与合并

1. 更新修改（**git fetch** 命令用于从远程获取代码库。）

   ```bash
   git fetch origin
   ```

2. 查看分支

   ```bash
   git branch -a
   ```

3. 合并

   ```bash
   git merge origin/master
   ```

4. 初学者可以选择强行覆盖，这样以本地为准

   ```bash
   git push origin master -f
   ```

   

# 分支

分支是用来将特性开发绝缘开来的。在你创建仓库的时候，*master* 是“默认的”分支。在其他分支上进行开发，完成后再将它们合并到主分支上。

![image-20220530215500378](attachments/image-20220530215500378.png)

创建一个叫做“feature_x”的分支，并切换过去：
`git checkout -b feature_x`
切换回主分支：
`git checkout master`
再把新建的分支删掉：
`git branch -d feature_x`
除非你将分支推送到远端仓库，不然该分支就是 *不为他人所见的*：
`git push origin <branch>`

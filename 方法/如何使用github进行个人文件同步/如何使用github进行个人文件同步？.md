#git #github #方法 #电脑使用方法 

使用github云端管理个人文件，比如obsidian笔记文件等等，仅需要实现github的上传和下拉即可。

了解git的基本操作。[[如何使用git上传和更新库？]]

```bash
git add * #将更改添加到暂存区中
git commit -m "update" #head指向最新一次更改
git push origin master [-f] #向github推送
git fetch origin #从github拉取
```
如果有需要的话，需要更改git默认的master分支（反对奴隶制的原因）为github默认的main分支。
```bash
git checkout -b main #创建main分支并切换
git branch -d master #删除master分支
git push origin main #推送main分支给远程仓库
```



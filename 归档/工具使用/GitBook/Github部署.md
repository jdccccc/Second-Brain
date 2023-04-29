# GitHub部署

[参考文档](http://ypeng.me/%E7%94%A8gitbook%E7%BB%84%E7%BB%87%E6%96%87%E6%A1%A3%E5%B9%B6%E5%B1%95%E7%A4%BA%E5%88%B0github%E7%9A%84pages%E4%B8%AD)

我将gitbook部署到username.github.io仓库的master分支上，与参考链接不同

可以直接访问username.github.io访问

```sh
gitbook build . docs
git checkout master
git add .
git commit -m "update"
git push -u Blog +master
```

可以写一个脚本launch.sh

```sh
chmod 764 launch.sh
```

```sh
gitbook build . docs
git config user.email "1704690357@qq.com"#请改成自己的邮箱
git config user.name "jdccccc"			 #请改成自己的用户名
git add .
git commit -m "update"
```

推送需要单独发送

```sh
git push -u Blog master
```


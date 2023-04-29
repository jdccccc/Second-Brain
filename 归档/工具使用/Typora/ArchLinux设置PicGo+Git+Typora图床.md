## ArchLinux设置PicGo+Git+Typora图床

## ArchLinux 截图

`参考`

https://zhuanlan.zhihu.com/p/88325211

使用Flameshot

```
sudo pacman -S flameshot
```

## 安装

https://zhuanlan.zhihu.com/p/358939060

``` bash
yay -S picgo-appimage
```

## 获取token

https://www.jianshu.com/p/4a29945ad69c

- 在github上新创建一个仓库充当图床
- 在github上生成一个Token

## 配置PicGo

https://www.jianshu.com/p/4a29945ad69c

进入图床配置中的Github配置

- 设定仓库名：按照 `用户名/图床仓库名` 的格式填写

- 设定分支名：`master`

- 设定Token：填写之前在GitHub生成的Token

- 指定存储路径：填写想要储存的路径，如 `BlogImg/`，这样就会在仓库下创建一个名为`BlogImg` 的文件夹，图片将会储存在此文件夹中

- 设定自定义域名：图片上传后，PicGo 会按照 `自定义域名+储存路径+上传的图片名` 的方式生成访问链接，并放到粘贴板上

  因为我们要使用 jsDelivr 加速访问，所以自定义域名可以设置为 `https://cdn.jsdelivr.net/gh/用户名/图床仓库名`，上传完毕后，就可以通过 `https://cdn.jsdelivr.net/gh/用户名/图床仓库名/储存路径/上传的图片名` 加速访问我们的图片了。

- 打开`时间戳重命名`

  上传图片时，如果多次上传同一张图片的话，文件名会一样，导致文件已存在而报错，在上传图片时使用时间戳不会因为文件名重复而报错。

## 配置Typora

!!!记得安装xclip

```bash
yay -S xclip
```
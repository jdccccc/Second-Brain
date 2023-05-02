## 问题描述：

git add：添加至暂存区，但并未提交至服务器。git add . 是表示把当前目录下的所有更新添加至暂存区。有时在终端操作这个会提示：

```
warning: LF will be replaced by CRLF in ball_pool/assets/Main.js.
The file will have its original line endings in your working directory
```

## 原因：

这是因为文件中换行符的差别导致的。这个提示的意思是说：会把 windows 格式（CRLF（也就是回车换行））转换成 Unix 格式（LF），这些是转换文件格式的警告，不影响使用。

git 默认支持 LF。windows commit 代码时 git 会把 CRLF 转 LF，update 代码时 LF 换 CRLF。

## 解决方法：

**注：  . 为文件路径名**

```
git rm -r --cached .
git config core.autocrlf false
git add .
git commit -m ''
 
git push
```
#python #file对象

file 对象使用 open 函数来创建。

# Python File write() 方法
## 概述

**write()** 方法用于向文件中写入指定字符串。

**在文件关闭前或缓冲区刷新前，字符串内容存储在缓冲区中，这时你在文件中是看不到写入的内容的。**

如果文件打开模式带 b，那写入文件内容时，str (参数)要用 encode 方法转为 bytes 形式，否则报错：TypeError: a bytes-like object is required, not 'str'。

## 语法

write() 方法语法如下：

`fileObject.write( [ str ])`

## 参数

- **str** -- 要写入文件的字符串。
    

## 返回值

返回的是写入的字符长度。
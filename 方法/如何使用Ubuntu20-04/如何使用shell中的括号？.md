#shell #LInux 
>[shell 中各种括号的作用|菜鸟教程 (runoob.com)](https://www.runoob.com/w3cnote/linux-shell-brackets-features.html)

# 单小括号 ()

-   **命令组**。括号中的命令将会新开一个子shell顺序执行，所以括号中的变量不能够被脚本余下的部分使用。括号中多个命令之间用分号隔开，最后一个命令可以没有分号，各命令和括号之间不必有空格。
-   **命令替换**。等同于\`cmd\`，shell扫描一遍命令行，发现了\$(cmd)结构，便将\$(cmd)中的cmd执行一次，得到其标准输出，再将此输出放到原来命令。有些shell不支持，如tcsh。
-   **用于初始化数组**。如：array=(a b c d)
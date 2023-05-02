prompt 是指终端提示符（Shell 提示符），是在 linux 操作系统中，提示进行命令输入的一种工作提示符。对于普通用户，Base shell 默认的提示符是美元符号 “$”；对于超级用户（root 用户），Bash Shell 默认的提示符是井号 “#”；该符号表示 Shell 等待输入命令。

本教程操作环境：centos8 系统、Dell G3 电脑。  

prompt 是指终端提示符，是在 linux 操作系统中，提示进行命令输入的一种工作提示符。

启动终端模拟包或者从 Linux 控制台登录后，便可以看到 Shell 提示符。提示符是通往 Shell 的大门，是输入 Shell 命令的地方。

对于普通用户，Base shell 默认的提示符是美元符号`$`；对于超级用户（root 用户），Bash Shell 默认的提示符是井号`#`。该符号表示 Shell 等待输入命令。

不同的 Linux 发行版使用的提示符格式不同。例如在 CentOS 中，默认的提示符格式为：

```
[mozhiyan@localhost ~]$
```


这种格式包含了以下三个方面的信息：

*   启动 Shell 的用户名，也即 mozhiyan；
    
*   本地主机名称，也即 localhost；
    
*   当前目录，波浪号~ 是主目录的简写表示法。
    

# shell如何控制提示符格式?
Shell 通过 PS1 和 PS2 两个环境变量来控制提示符格式：

*   PS1 控制最外层命令行的提示符格式。
    
*   PS2 控制第二层命令行的提示符格式。
    

在 Shell 中初次输入命令，使用的是 PS1 指定的提示符格式；如果输入一个命令后还需要输入附加信息，Shell 就使用 PS2 指定的提示符格式。请看下面的例子：

```
[mozhiyan@localhost ~]$ echo "PHP中文网"
PHP中文网
[mozhiyan@localhost ~]$ echo "https://www.php.cn/"
https://www.php.cn/
[mozhiyan@localhost ~]$ echo "
> yan
> chang
> sheng
> "
yan
chang
sheng
[mozhiyan@localhost ~]$
```

echo 是一个输出命令，可以用来输出数字、变量、字符串等；本例中，我们使用 echo 来输出字符串。

字符串是一组由 "" 包围起来的字符序列，echo 将第一个" 作为字符串的开端，将第二个 " 作为字符串的结尾。此处的字符串就可以看做 echo 命令的附加信息。

本例中，前两次使用 echo 命令时都是在后面紧跟字符串，一行之内输入了完整的附加信息。第三次使用 echo 时，将字符串分成多行，echo 遇到第一个 "认为是不完整的附加信息，所以会继续等待用户输入，直到遇见第二个"。输入的附加信息就是第二层命令，所以使用 > 作为提示符。

要显示提示符的当前格式，可以使用 echo 输出 PS1 和 PS2：

```
[mozhiyan@localhost ~]$ echo $PS1
[\u@\h \W]\$
[mozhiyan@localhost ~]$ echo $PS2
>
[mozhiyan@localhost ~]$
```

Shell 使用以 \\ 为前导的特殊字符来表示命令提示符中包含的要素，这使得 PS1 和 PS2 的格式看起来可能有点奇怪。下表展示了可以在 PS1 和 PS2 中使用的特殊字符。

<table><caption>Bash shell 提示符可以包含的要素</caption><tbody><tr><th>字符</th><th>描述</th></tr><tr><td>\a</td><td>铃声字符</td></tr><tr><td>\d</td><td>格式为 “日 月 年” 的日期</td></tr><tr><td>\e</td><td>ASCII 转义字符</td></tr><tr><td>\h</td><td>本地主机名</td></tr><tr><td>\H</td><td>完全合格的限定域主机名</td></tr><tr><td>\j</td><td>shell 当前管理的作业数</td></tr><tr><td>\1</td><td>shell 终端设备名的基本名称</td></tr><tr><td>\n</td><td>ASCII 换行字符</td></tr><tr><td>\r</td><td>ASCII 回车</td></tr><tr><td>\s</td><td>shell 的名称</td></tr><tr><td>\t</td><td>格式为 “小时: 分钟: 秒” 的 24 小时制的当前时间</td></tr><tr><td>\T</td><td>格式为 “小时: 分钟: 秒” 的 12 小时制的当前时间</td></tr><tr><td>\@</td><td>格式为 am/pm 的 12 小时制的当前时间</td></tr><tr><td>\u</td><td>当前用户的用户名</td></tr><tr><td>\v</td><td>bash shell 的版本</td></tr><tr><td>\V</td><td>bash shell 的发布级别</td></tr><tr><td>\w</td><td>当前工作目录</td></tr><tr><td>\W</td><td>当前工作目录的基本名称</td></tr><tr><td>\!</td><td>该命令的 bash shell 历史数</td></tr><tr><td>\#</td><td>该命令的命令数量</td></tr><tr><td>\$</td><td>如果是普通用户，则为美元符号<code>$</code>；如果超级用户（root 用户），则为井号<code>#</code>。</td></tr><tr><td>\nnn</td><td>对应于八进制值 nnn 的字符</td></tr><tr><td>\\</td><td>斜杠</td></tr><tr><td>\[</td><td>控制码序列的开头</td></tr><tr><td>\]</td><td>控制码序列的结尾</td></tr></tbody></table>

注意，所有的特殊字符均以反斜杠\\ 开头，目的是与普通字符区分开来。您可以在命令提示符中使用以上任何特殊字符的组合。

我们可以通过修改 PS1 变量来修改提示符格式，例如：

```
[mozhiyan@localhost ~]$ PS1="[\t][\u]\$ "
[17:27:34][mozhiyan]$
```


新的 Shell 提示符现在可以显示当前的时间和用户名。不过这个新定义的 PS1 变量只在当前 Shell 会话期间有效，再次启动 Shell 时将重新使用默认的提示符格式。


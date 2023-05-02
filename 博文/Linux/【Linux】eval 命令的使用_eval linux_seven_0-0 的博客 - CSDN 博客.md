eval 可以读取一连串的参数，然后按照参数特性来执行。参数数目不限，彼此之间用分号隔开。  
eval 会对后面的命令进行两遍扫描，如果第一遍扫描后，命令是个普通命令，则执行此命令；如果命令中含有变量的间接引用，则保证间接引用的语义。也就是说，eval 命令将会首先扫描命令行进行所有的置换，然后再执行该命令。因此，eval 命令适用于那些一次扫描无法实现其功能的变量。  
eval 执行以下两个步骤：  
第一步，执行变量替换，类似与 C 语言的宏替代；  
第二步，执行替换后的命令串。  
下面来看几个例子：  
**1、执行含有带字符串的命令**  
我们可以新建一个文件 test 将字符串”HelloWorld！“写入文件中，把 cat test 赋值给变量 WORD, 如果我们 echo WORD 并不能的到 test 中的内容；然而 eval WORD 则能显示文件中的内容，因为 eval 命令对后面的命令进行了两次扫描，第一次将 WORD 替换为 cat test，第二次执行 cat test。  

![](https://img-blog.csdn.net/20170325174624243?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGVyX18wXzA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  
这些需要进行两次扫描的变量有时被称为复杂变量。不过这些变量本身并不复杂。eval 命令不仅可以回显复杂变量，也可以用于回显简单变量。  
**2、回显简单变量**  

![](https://img-blog.csdn.net/20170325174811866?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGVyX18wXzA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  
**3、eval 命令还可以获取传给 shell 的最后一个参数**  
如果我们知道参数个数，我们想要查看最后一个参数的内容可以使用 echo 直接显示，如输入 first last 两个参数我们可以用 echo $2 来查看最后一个参数；  
但是，如果我们不知道参数个数还想查看最后一个参数内容该怎么办呢？这是我们就想到使用`#`为传给 shell 脚本的参数个数，但是上例中 echo `#` 后显示的其实是参数个数，而使用 eval echo `#` 才显示最后一个参数的内容。

![](https://img-blog.csdn.net/20170325175053789?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGVyX18wXzA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

**4、条件筛选**

在 file 文件中写入两列数据，第一列对应 KEY 、第二列为 VALUE，使用 eval 命令将 KEY 与 VALUE 的值对应起来，从文件中读取

![](https://img-blog.csdn.net/20170325175825386?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGVyX18wXzA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

**注意：**  
1、eval 不能获得函数处理结果。  
2、eval 嵌套无意义，在其他语言中可以通过 eval(eval(“code”)) ，来执行（执行动态生成的 code 的返回），而由于 shell 中 eval 将后面的 eval 命令简单当作命令字符串执行，失去了嵌套作用，嵌套被命令替换取代。
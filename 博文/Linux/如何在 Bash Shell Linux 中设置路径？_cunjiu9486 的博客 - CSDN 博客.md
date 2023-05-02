[Linux](https://so.csdn.net/so/search?q=Linux&spm=1001.2101.3001.7020) bash shell provides a lot of information into running applications. `PATH` is one of the most important ones which is used to locate binary files and libraries. In some situations, we may need to edit, add or remove some paths and locations from the bash PATH variable. In this tutorial, we will differently use cases about these operations.

Linux bash shell 为运行的应用程序提供了大量信息。 `PATH`是最重要的`PATH`之一，用于查找二进制文件和库。 在某些情况下，我们可能需要编辑，添加或删除 bash PATH 变量中的某些路径和位置。 在本教程中，我们将对这些操作使用不同的用例。

# 打印当前 PATH 变量 (Print Current PATH Variable)

We will start printing the current `PATH` variable. This will print currently available paths in the `PATH` variable.

我们将开始打印当前的`PATH`变量。 这将在`PATH`变量中打印当前可用的路径。

```
$ echo $PATH
```

![](attachments/3c67cf96369ae58ae58e6f44a4edd1a4.png)

Print Current PATH Variable

打印当前 PATH 变量

# PATH 变量语法 (PATH Variable Syntax)

As we can see in previous example paths are stored in a single line and delimited with `:` . Each entry is a separate path to search binaries and libraries.

正如我们在前面的示例中看到的那样，路径存储在一行中，并以`:`分隔。 每个条目都是搜索二进制文件和库的单独路径。

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bi
```

# 添加新路径 (Add New Path)

Now we need to add a new path to the `PATH` variable. We will put a delimiter which is `:` and then put the new path we want to add. In this example, we will add `/home/ismail/bin` as new path.

现在，我们需要向`PATH`变量添加新路径。 我们将放置一个定界符`:` ，然后放置我们要添加的新路径。 在此示例中，我们将添加`/home/ismail/bin`作为新路径。

```
$ PATH=$PATH:/home/ismail/bin
```

![](attachments/6c0baea5a98c392061a3d362f924a1de.png)

Add New Path

添加新路径

# 删除现有路径 (Remove Existing Path)

In order to remove the existing path, we should copy the PATH variable value and then remove the path we want to remove. Then set the new PATH variable.

为了删除现有路径，我们应该复制 PATH 变量值，然后删除要删除的路径。 然后设置新的 PATH 变量。

# 导出 PATH 变量 (Export PATH Variable)

Newly created PATH variable will be available for the current shell sessions. If we need to make this available for all other sessions we should export PATH variable to all other sessions with  `export` command like below.

新创建的 PATH 变量将可用于当前的 Shell 会话。 如果我们需要将此设置用于所有其他会话，则应使用如下所示的`export`命令将 PATH 变量导出到所有其他会话。

```
$ export PATH
```

# 使 PATH 变量永久存在 (Make PATH Variable Persistent)

Even we export our PATH variable this will not make our variable persistent after a reboot all newly added paths will be removed. In order to make the PATH variable persistent, we should add it to `.bashrc` file which will read before a shell start for the current user.

即使我们导出 PATH 变量，重启后所有新添加的路径也将被删除，这也不会使变量持久化。 为了使 PATH 变量具有持久性，我们应该将其添加到`.bashrc`文件中，该文件将在 shell 启动之前为当前用户读取。

![](attachments/dde93cc84133f44149be7b377a7baf6d.png)

Make PATH Variable Persistent

使 PATH 变量永久存在

# 使 PATH 变量永久且对所有用户可用 (Make PATH Variable Persistent and Available For All Users)

In the previous example, the PATH variable will be available for only the current user. If we need to make it available for all other system users we should change the system-wide file `/etc/profile` with a text editor. In order to change `profile`file, we need root privileges.

在前面的示例中，PATH 变量仅对当前用户可用。 如果需要使它可用于所有其他系统用户，则应使用文本编辑器更改系统范围的文件`/etc/profile` 。 为了更改`profile`文件，我们需要 root 特权。

![](attachments/d35792966dc64a300b34f4c258c5bc52.png)

Make PATH Variable Persistent and Available For All Users

使 PATH 变量永久且对所有用户可用

翻译自: [https://www.poftut.com/set-path-bash-shell-linux/](https://www.poftut.com/set-path-bash-shell-linux/)
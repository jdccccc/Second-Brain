在你一通猛如虎的操作之后，突然发现终端每一行命令前面都出现了 (base)
出现 (base) 的原因可能是因为 auto_activate_base 被设置为 True  
你可以在终端中使用以下命令进行检查  
`conda config --show | grep auto_activate_base`

若为 True，你可以通过以下命令将其设置为 False：  
`conda config --set auto_activate_base False`

之后关闭并重启终端，每个命令行前面惹眼的 (base) 就消失了
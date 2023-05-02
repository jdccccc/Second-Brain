https://www.cnblogs.com/saamcheung1i/p/17072794.html

# saamcheung1i


### 问题/需求：

1.  网页剪藏内容保存到本地/icloud云盘。
2.  保存文件格式便于迁移，可跨应用。
3.  网页中的图片能够快捷的保存到本地，避免图片链接失效。

### 如何解决：

**环境**：mac os 12.1-
**应用**：Obsidian 1.1.9、Cubox 7.2.6-
**Obsidian插件**(解决图片保存问题)：Local images、Clear Unused Images

**方案**：使用Cubox实现多端网页剪藏，通过Cubox自定义URL动作及Obsidian URI保存到Obsidian。

#### Cubox自定义URL动作配置方式如下：

Cubox在`文章菜单` - `更多`中，编辑快捷动作

在`动作URL`中添加以下内容：

```URL
obsidian://new?vault=库的名字&name=[card_title]&content=[content_markdown]   

```

> 关于obsidian URI其他操作可参考官方文档：[Using obsidian URI](https://help.obsidian.md/Advanced+topics/Using+obsidian+URI)-
> 另外需要注意确保 `valus` 已正确进行 URI 编码。 例如，正斜杠字符 **`/`** 必须编码为 **`％2F`**，空格字符必须编码为 **`％20`**。这特别重要，因为编码不正确的 “保留字符” 可能会破坏 URI的解释。

配置好动作后，在文章菜单页面-更多中使用该动作，即可同步文章到obsidian

### 图片保存问题

1.  文章MD同步到Obsidian后，图片链接为网络链接，并未保存到本地。下载图片到本地需要用到Obsidian的插件Local images。在第三方插件市场安装启用后，command+p输入`local images`，会跳出两个命令，down load images locally 和 down load images locally for all your notes，第一个是下载当前md文件的图片，第二个是obsidian当前库所有md文件的图片。图片下载后会存放在配置路径的文件夹下。 ^7f0f43
2.  图片保存到本地后，删除md文件或图片链接，图片文件不会同步删除。清理无效的图片可以使用Obsidian的插件Clear Unused Images。 ^62ed89

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=ff80808187c21d840187c6e31c722d30)
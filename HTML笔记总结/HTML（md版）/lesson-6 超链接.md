# lesson-6 超链接

#超链接（a标记）

超链接分为两类

- 外部链接   点击后跳到其他网站。url地址需要用绝对地址。
- 内部链接 同一个网站内不同HTML界面的链接关系。url地址可以用相对地址（同级目录“./”,上一级“../”）。   **网站里的相对路径不能跨盘符。**（为什么？）

超链接标记\<a>....\</a>

## 基本链接

**基本语法：**

```html
<a href="url" title=""  target="self|blank"></a>


href
-- 跳外部网页用绝对url
-- 跳本网站界面用相对url

title
提示信息（鼠标划到链接时的提示信息）

target 属性的两个值
-- self 在当前窗口打开链接界面
-- blank 在新窗口打开
```

> **注**：**链接也可以指向其他html资源：如文档，视频，音频等。**
>
> ```html
> 		<ul>
> 			<li><a href="mailto://E-mail地址[?subject=邮件主题[&参数=参数值]]">点我发邮件</a></li>
> 			<li><a href="mov.mp4">点我看视频</a></li>
> 			<li><a href="我的梦.mp3">点我听音乐</a></li>
> 			<li><a href="lesson-9  html5介绍.pdf">点我下载文件</a></li>
> 		</ul
> ```
>
> ![mark](http://qiniu.wind-zhou.com/blog/201107/02H3CjbibA.png?imageslim)

## 电子邮件链接

基本语法：

```html
<a href="mailto://E-mail地址[?subject=邮件主题[&参数=参数值]]">点我发送邮件</a>
```

**语法说明：**

![mark](http://qiniu.wind-zhou.com/blog/201030/fHia8BBCJf.png?imageslim)

**邮件参数**：

| 参数    | 说明         |
| ------- | ------------ |
| subject | 电子邮件主题 |
| cc      | 抄送         |
| body    | 邮件内容     |

```html
<a href="mailto:zhouzheng5210@163.com?subject=聚会信息"& cc=zhouzheng5210@gmail.com& body=多喝热水>点我发送邮件</a>
```

## 书签链接（锚）

可以跳转到文章的指定位置（**用于导航**）

书签跳转需要两步走：

1. 给目标位置打锚点
2. 在超链接标签中指定锚点

**基本语法**：

如何打锚点？

```html
<a name="书签名称">链接内容</a>
```

如何链接锚点？（分为两种情况）

- 在同一页面跳跃

```html
<a href="#书签名称" target="窗口名称">链接标题</a>
```

- 在不同页面跳跃

```html
<a href="url地址#书签名称 " target="窗口名称">链接标题</a>
```

实战练习：

![mark](http://qiniu.wind-zhou.com/blog/201030/51d412CD32.png?imageslim)


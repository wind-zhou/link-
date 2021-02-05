# LINK 65班第一次测试汇总

## 一、档案类型声明的作用是什么?常见的文档类型声明有哪些?

**doctype的作用**：文档类型声明，用来声明使用什么风格的html或xhtml。doctype告诉浏览器怎样去处理这个文档，并且让验证器知道按照什么的标准去检查代码语法。

**常见的文档类型声明：**

- HTML4.01**文档过渡定义类型**
- HTML4.01**文档严格定义类型**
- HTML4.01**文档框架定义类型**
- XHTML1.0**文档过渡定义类型**
- XHTML1.0**文档严格定义类型**
- XHTML1.0**文档框架定义类型**
- XHTML1.1**文档严格定义类型**

## 二、什么是语义化 ?h5语义化的标记有哪些？

**语义化**：简单来说，就是用人们更容易理解的名字去给标签命名。

这样主要有两方面好处：

1. 可以增强程序的可读性，方便程序员看懂程序，有利于生产中项目的交接以及后期代码的维护。
2. 可以让搜索引擎更容易识别网页的内容，能够帮助所搜引擎SEO，加快对数据的识别和处理

**常见的h5语义化标签（目前学过的）**

![mark](http://qiniu.wind-zhou.com/blog/201109/A0G20hk1l8.png?imageslim)

\<title>：页面主体内容

\<h->：h1~h6，分级标题

\<ul>：无序列表

\<ol>：有序列表

\<address>:地址

\<header>：页眉通常包括网站标志、主导航、全站链接以及搜索框

\<nav>：标记导航，仅对文档中重要的链接群使用。

\<article>：定义外部的内容，其中的内容独立于文档的其余部分

\<section>：定义文档中的节（section、区段）。比如章节、页眉、页脚或文档中的其他部分

\<aside>：定义其所处内容之外的内容。如侧栏、文章的一组链接、广告、友情链接、相关产品列表

\<footer>：页脚，只有当父级是body时，才是整个页面的页脚

\<strong>：和 em 标签一样，用于强调文本，但它强调的程度更强一些

\<em>：将其中的文本表示为强调的内容，表现为斜体

\<blockquote>：定义块引用，块引用拥有它们自己的空间

\<time>：datetime属性遵循特定格式，如果忽略此属性，文本内容必须是合法的日期或者时间格式

\<del>：移除的内容

[详解HTML5常用的语义化标签](https://www.jb51.net/html5/695341.html)

## 三、h5和h4的区别

html5与html4的区别
1）doctype声明
2）meta声明
3）添加了新的标签，淘汰了一些旧的标签

**以下是W3C官方给出的回答！**

HTML5 中的一些有趣的新特性：

- 用于绘画的 canvas 元素
- 用于媒介回放的 video 和 audio 元素
- 对本地离线存储的更好的支持
- 新的特殊内容元素，比如 article、footer、header、nav、section
- 新的表单控件，比如 calendar、date、time、email、url、search

## 四、h5新增的布局元素

- \<article> 用于指定页面上独立、完整的一片文章或区域。

- \<section> 对页面元素进行分块（UI版嵌套在article里面） **section侧重于文章分块，article侧重**

  **于整片文章。**

- \<nav> 用于定义导航

- \<aside> 用于定义当前页面的附属信息。（即网页的侧边栏）

- \<header> 用于定义article元素文章头部信息

- \<footer> 用于定义脚注部分（包含文章的版权作者等）

## 五、h5表单新增控件

新增的控件主要就是指新增的不同type类型的input控件

新增的那十三个：

color、date、datetime、datetime-local、time、month、week、url、search、range、number、tel、email

##六、h5新增的语义化文本元素？

**这是什么鬼？** 

## 七、 实现以下效果

![mark](http://qiniu.wind-zhou.com/blog/201109/4d6IcgC1mG.png?imageslim)

**源码：**

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<form>
			
			<table>
				<caption><b>成员注册</b></caption>
				<tr >
					<td align="right">*用户名称</td>
					<td><input type="text" name="username" required="required"></td>
				</tr>
				<tr >
					<td align="right">*真实姓名</td>
					<td> <input type="text" name="name2" required="required"></td>
				</tr>
				<tr >
					<td align="right">出生时间</td>
					<td> <input type="date" name="time"></td>
				</tr>
				<tr >
					<td align="right">性别</td>
					<td><input type="radio" name="sex" value="man">男
					<input type="radio" name="sex" value="women">女</td>
				</tr>
				<tr >
					<td align="right">*登录密码</td>
					<td><input type="password" name="pwd"  required="required"/>
					</td>
				</tr>
				<tr >
					<td align="right">*确认密码</td>
					<td><input type="password" name="pwd2"  required="required"/></td>
				</tr>
				<tr >
					<td align="right">*Email</td>
					<td><input type="email" name="mail" required="required"></td>
				</tr>
				<tr >
					<td align="right">电话</td>
					<td><input type="tel" name="tel"></td>
				</tr>
				<tr >
					<td align="right">其他联系方方式</td>
					<td ><input type="tel" name="tel2"></td>
				</tr>
				<tr >
					<td align="right">个人简介</td>
					<td><textarea >
						这个家伙很懒，什么都没有留下！
					</textarea></td>
				</tr>
				<tr >
					<td align="right"></td>
					<td><input type="submit" value="确定"></td>
				</tr>
			</table>
		</form>
	</body>
</html>

```




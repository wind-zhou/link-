# lesson-1 HTML

**不谋全局者，不足谋一域！**

##  网站的概述

**网站工作原理：**

![mark](http://qiniu.wind-zhou.com/blog/20201022/CdYB0TvBeCFg.png?imageslim)

**网站的构成**：

- 结构层（支撑网页框架，主要用HTML实现）
- 表现层（美化网页，用CSS实现）
- 动作层（实现交互，用JavaScript实现）

>扩展阅读：（我发现他们没什么鸟关系，但就贴在这里吧）
>
># [三层架构与MVC](https://www.cnblogs.com/wind-zhou/p/12943709.html)

## 网页设计相关概念

**万维网：**WWW（world wide web）一种基于超文本（可以理解为多媒体，视频，图片，文字等）的信息检索服务工具。

注：万维网不等于互联网，只是互联网提供的服务之一。可以理解为一种规则。

一个机构：**W3C**，用于管理www并制定协议等。

**超链接**：Hyper Link是特殊的文字标识，指向了www中的资源。

>扩展（推荐阅读）：
>
>[全面了解浏览器（内核）发展史](https://www.jianshu.com/p/db1b230e3415)
>
>[浏览器和搜索引擎有什么区别？](https://www.zhihu.com/question/356013328)
>
>[搜索引擎分类和基础架构概述](https://www.cnblogs.com/maybe2030/p/4778107.html)

**统一资源定位符（URL）**：用于描述互联网上资源的位置和访问方式。

​		URL的基本语法结构：scheme://host.domin:post/path/filename

![mark](http://qiniu.wind-zhou.com/blog/20201022/LHehWfUCDxaS.png?imageslim)

​		`http与https的区别：https是加密过的http协议。`

>推荐阅读：[关于HTTP协议，一篇就够了](https://www.cnblogs.com/wind-zhou/p/12918684.html)

## HTML

超文本**标记**语言（Hypertext Makeup Language）----属于标记语言，没有逻辑。

最新的版本已经到了**HTML5**。

**几点常识：**

XML(可扩展标记语言，主要**用于存数据**，HTML是用来展示数据的)。曾经和html4.0结合出来了一个xhtml（可扩展超文本语言，兼具了xml的语法和html4.0的功能）。

**HTML5使用方向**：网站，公众号，html5场景，混合式app？，html5游戏。

**HTML兼容性**：移动端全部支持；PC端一部分支持。

## HTML、XML和XHTML的联系与区别

此文章主要为大家介绍了HTML、XML和XHTML的联系与区别，具有一定的参考价值，学习觉得挺不错的，分享给大家。

![img](https://ss1.baidu.com/6ONXsjip0QIZ8tyhnq/it/u=2008860661,2651557802&fm=173&app=25&f=JPEG?w=640&h=670&s=48A0BA5396073FE9429DF34B030080F0)



​		**HTML(HyperText Markup Language)，超文本标记语言**。“超文本”就是指页面内可以包含图片、链接，甚至音乐、程序等非文字元素，“标记”是指用特定的标记符号来标记要显示的内容的各个部分。超文本标记语言是标准通用标记语言下的一个应用，也是一种规范，一种标准，**它被设计用来显示数据**。HTML文本就是我们通常所说的网页，扩展名可以是html或htm。

　　**XML(Extensible Markup Language)，可扩展标记语言**。XML是标准通用标记语言的子集，是一种用于标记电子文件使其具有结构性的标记语言，**它被设计用来传输和存储数据**，是**对超文本标记语言的补充**。可扩展标记语言是一种元标记语言，即定义了用于定义其他特定领域有关语义的、**结构化的标记语言**，**这些标记语言将文档分成许多部件并对这些部件加以标识。**它能够更精确地声明内容，方便跨越多种平台的更有意义的搜索结果。它提供了一种描述结构数据的格式，**简化了网络中数据交换和表示，使得代码、数据和表示分离，**并作为数据交换的标准格式，因此它常被称为智能数据文档，文件扩展名为xml。　

　　　**XHTML(Extensible HyperText Markup Language)，可扩展超文本标记语言**。XHTML基于可扩展标记语言（XML）。XHTML就是一个扮演着类似HTML的角色的可扩展标记语言（XML），所以，本质上说，**XHTML是一个过渡技术，结合了部分XML的强大功能及大多数HTML的简单特性**。**XHTML 1.0是一种在HTML 4.0基础上优化和改进的的新语言**，目的是基于XML应用。XHTML是一种增强了的HTML,**XHTML 是更严谨更纯净的 HTML** 版本。它的可扩展性和灵活性将适应未来网络应用更多的需求。XML虽然数据转换能力强大，完全可以替代HTML，但面对成千上万已有的基于HTML语言设计的网站，直接采用XML还为时过早。因此，在HTML4.0的基础上，用XML的规则对其进行扩展，得到了XHTML。所以，建立XHTML的目的就是实现HTML向XML的过渡。XHTML 于2000年的1月26日成为 W3C （World Wide Web Consortium ，万维网联盟），文件扩展名为xhtml.。

总结：HTML、XML和XHTML都是标准通用标记语言的一个子集。HTML被设计用来显示数据，其焦点是数据的外观；XML被设计用来传输和存储数据，其焦点是数据的内容；XHTML是更严格更纯净的 HTML 版本，是作为一种 XML 应用被重新定义的 HTML，设计的目的是为了取代HTML以适应未来网络更多的需求。它们都可以用来开发网页，但就目前来看，网页开发中HTML还是占绝对的主流，现在最新版本HTML5也备受推崇。可拓展标记语言XML广泛运用于各种应用程序中数据的存储（例如各种配置文件）和应用程序间的数据传输，可以说是一项必须掌握的技术。至于可扩展超文本标记语言XHTML，在2009年W3C已经宣布停止了对XHTML2的开发，转而大力支持HTML5。

>转载自：
>
>[HTML、XML和XHTML的联系与区别](https://baijiahao.baidu.com/s?id=1596336010202648529&wfr=spider&for=pc)
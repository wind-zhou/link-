# lesson-1 jquery简介

## 从“JavaScript”到“JavaScript库”

“jQuery、Prototype、Mootools、YUI、Dojo、Ext.js……”在平常的学习中，我们或多或少都听过以上这些名词。其实，这些都来自 JavaScript 库。那么问题就来了：“JavaScript 库又是什么呢？本来已经有 JavaScript 了，为什么还会出现这玩意儿？”

我们都知道，JavaScript 是一门很烦琐的编程语言，不仅语法复杂，还会出现各种兼容问题。举个简单的例子，如果我们使用 JavaScript 来实现动画效果（如滑动、过渡等），那么代码量会非常大，而且还得对各个浏览器作兼容处理。因此，为了减少工作量，我们常常会把 JavaScript 中经常用到的一些功能或特效封装成一个“代码库”，这样在实际开发中只需要调用一些简单的函数就能直接使用这些功能或特效了。

对于“JavaScript”和“JavaScript库”的关系，可以这样去理解。如果经常用到某一个特效，我们可以把这个特效封装成一个函数。这样以后需要用到这个特效时，我们只需要调用这个函数就可以了。我们把常用的功能或特效都像上面那样封装成一个个函数，这些函数放在一起就成了一个“JavaScript 库”。也就是说：jQuery、Prototype、Mootools 等，本身都是用 JavaScript 来写的。（这句话应该很好理解。）

打个比方，我们把“JavaScript”看成是“原料”，则“JavaScript 库”可以看成是用原料做成的“半成品”，而程序用到的功能或特效就是“成品”。如果想要得到一件成品，你可以直接用原料做，也可以用半成品做。不过用原料来做，工序肯定更多，时间也更长。而使用半成品来做，则可以省去很多工序，时间也会缩短很多。

实际上，我们即将学到的 jQuery 就是众多 JavaScript 库中非常好用的半成品，也是用得非常频繁的半成品。

## 关于jQuery

jQuery，也就是 **JavaScript** 和**查询（Query）**的组合，即辅助 JavaScript 开发的一个库。

jQuery 是全球十分流行的 JavaScript 库。在世界访问量前 10000 的网站中，超过 55% 的网站在使用 jQuery。



![jQuery](http://c.biancheng.net/uploads/allimg/200605/11-200605111R52X.jpg)


从前文我们可以知道，jQuery 本身就是用 JavaScript 来写的，它只是把 JavaScript 中最常用的功能封装起来，以方便开发者快速开发。遥想当年，jQuery 的创始人 John Resig 就是受够了 JavaScript 的各种缺点，所以才开发了 jQuery。

**jQuery 具有很多优点，主要包括以下几点。**

- 代码简洁。
- 完美兼容。
- 轻量级。
- 强大的选择器。
- 完善的Ajax。
- 丰富的插件。
- 链式操作
- 隐形迭代


“简洁与高效”是 jQuery 最大的特点。有一句话说得好：“每多学一点知识，就少写一行代码。”实际上 jQuery 的理念亦是如此：“Write less,do more.”

【解惑】

1.在三大框架（Vue、React、Angular）非常流行的今天，学习 jQuery 还有用吗？

jQuery 依然被用得很多，现在互联网公司的项目并不都是使用 Vue 或 React 等来开发的，还有相当一部分项目是采用传统方式来开发，而传统方式大多数情况下都会用到 jQuery。

在前端面试中，jQuery 依然是必备的一项技能。如果只学 Vue 或 React，实际上还是满足不了真正的前端开发工作。所以小伙伴们还是有必要认真地学一下 jQuery。

2.对于 jQuery 的学习，有什么推荐的吗？

> 给小伙伴们一个很有用的建议：在学习任何编程语言的过程中，一定要养成查阅官方文档的习惯，因为这是重要的参考资料，并且还能提高自己的英文水平。
>
> 其中，jQuery 官方文档地址如下：
>
> - jQuery API文档：[http://api.jquery.com](http://api.jquery.com/)；
> - jQuery UI文档：http://jqueryui.com/demos；
> - jQuery Mobile文档：http://jquerymobile.com/demos；
> - jQuery插件：[https://plugins.jquery.com](https://plugins.jquery.com/)。



## jQuery对象

**注**：jquery对象和dom对象

不能把jquery对象的方法用在原生js上。



**代码风格:**

```js
$(document).ready(function(){
    函数体；
})
```

- $()代表jquery对象。是jquery()的简写
- $(document).ready()，表示html文档加载完成后在执行js函数
- $("h3").html(),获取h3标记的内容，$("h3")相当于原生js中document.getElementByTagName("h3")

**注：jquery入口函数和原生window.onload()的区别**

1、jquery的入口函数可以写多个，并且不会覆盖；但是原生js的window.onload会发生覆盖

2、原生js会等到图片加载完在执行，jquery不会等到图片加载完后再执行



**jquery入口函数其他写法：**

（1）

````js
jQery(document).ready(function(){
    函数体；
})
````

（2）推荐：

````js
$((function(){
    函数体；
});
````

（3）

````js
jQery((function(){
    函数体；
});
````

**$()里面可以传的参数：**

1、传一个函数（入口函数）

2、接受一个字符串选择器（返回一个jquery对象）

3、接受一个代码片段（返回一个jquery对象，包含了创建的dom元素）

4、接收一个dom元素（会被包装成jquery对象）

![mark](http://qiniu.wind-zhou.com/blog/210106/bF4f2k7h46.png?imageslim)
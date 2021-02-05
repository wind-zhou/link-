# lesson-13  css兼容性

##补充：居中的总结

对文本和行内元素的水平居中一般采用`text-align:center`。当为单行时，垂直居中可以采用`line-height`

下面介绍几种对块进行居中的方法。

>参考链接：
>
> http://louiszhai.github.io/2016/03/12/css-center/

**一.使用margin**

**内容**

1.只能用于水平居中

2.必须指定元素的宽度

```css
.box1{
    width: 800px;
    height: 500px;
    border: 2px red solid;
}

.box2{
    width: 100px;
    height: 100px;
    background-color: #bfa;
    /* 将元素的左右外边距设置为auto，元素即可在其包含块中自动水平居中 */
    margin: 0 auto;
}
```

**二.使用绝对定位**

**1.1.必须要指定元素的宽度和高度**

```css
.box1{
    width: 800px;
    height: 500px;
    border: 2px red solid;

    position: relative;
}

.box2{
    width: 100px;
    height: 100px;
    background-color: #bfa;
    /* 通过绝对定位来设置元素的居中 */
    position: absolute;

    /* 四个偏移量都设置为0 */
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    margin: auto;
}
```

**1.2 定位拉回**

```css
	 .box1{
		     width: 500px;
		     height: 500px;
		     border: 2px red solid;
			 position: relative;
			 display: table-cell;
			 vertical-align: middle;
		 
		 }
		 
		 .box2{
		     width: 100px;
		     height: 100px;
		     background-color: #bfa;
			position: absolute;
			 left: 50%;
			 top: 50%;
			 margin-left:-50px ;
			 margin-top: -50px;
		 }
```

![mark](http://qiniu.wind-zhou.com/blog/201204/m35cCjgJ18.png?imageslim)



**三.使用表格（display:xxxx）**

**1.不需要指定元素的宽度高度（inline-block）**

```css
.box1{
    width: 800px;
    height: 500px;
    border: 2px red solid;
    /* 将父元素转换为单元格 */
    display: table-cell;
    vertical-align: middle;
}

.box2{
    width: 100px;
    height: 100px;
    background-color: #bfa;
}
```



**四.使用弹性盒flex**

**1.不需要设置元素的宽度和高度**

**2.会使所有的子元素都在父元素中居中**

```css
.box1{
    width: 800px;
    height: 500px;
    border: 2px red solid;
    display: flex;
    justify-content: center;/*水平居中*/
    align-items: center;/*垂直居中*/
}

.box2{
    width: 100px;
    height: 100px;
    background-color: #bfa;
}
```

##一、css兼容性

 主要知识：

- 产生兼容性原因
- 浏览器内核分类
- CSS hack
- 常见IE6BUG

###1.1  兼容性产生原因

**由于不同厂商的浏览器对CSS的支持解析不一样，导致不同浏览器环境呈现出不一致的页面效果。**



###1.2 常见的浏览器内核

Trident内核（IE）

Gecko内核（firefox）

webkit内核（safari内核，Chrome内核）

presto内核（opera 最新版Blink内核）



###1.3 **解决兼容性问题**

####**css reset**

- 通过重置css默认样式解决最基本的兼容性问题
  重置样式时有时不用`*`(全局选择器)，而是一个个列出来进行重置，因为*要匹配所有的标记，因此效率比较低
  设置时。重置样式的css代码要写在前面。

####**css hack**

**什么是css hack?**

就是针对不同的浏览器或浏览器的不同版本写相应的css code，叫做css hack。（就是重写一套）

**css hack的实现**

1. css属性前缀法  在属性前面加上浏览器的私有属性
   -moz-   （firefox）
   
   -ms-   （IE）
   
   -webkit-  （chrome和safari ）
   
      -o-  （opera）

   上面主要针对css3新增属性

2. 选择器前缀法
   根据选择器添加前缀（基本不用了）

3. IE条件注释法
   `<!--[if IE]>  这段文字在IE浏览器显示<！[endif]-->`

> 补充ie6 BUG
>
> 1、双边距问题
>
> 2、3px BUG
>
> 
>
> 解决低版本IE不支持h5新增标记问题
>
> 在 文档script中引入`html5 shiv.js   `（其实是引入了一个插件）



**css优先级**

行内式>内嵌式>链接式>导入式

id选择器>类别选择器>标记选择器

优先级算法：

- 行内选择符 1,0,0,0
- id选择符  0,1,0,0
- 类别选择符 0,0,1,0
- 元素选择符  0,0,0,1

优先级相同，采用就近原则

继承来的属性，优先级最低

！important 的优先级最高

## 浏览器的架构

![](http://qiniu.wind-zhou.com/blog/201125/C6G6Cg3gai.png?imageslim)





###重绘

当元素的一部分属性发生改变，如外观、背景、颜色等不会引起布局变化，浏览器会根据新属性重新绘制，使元素；呈现新的外观。(例如使用hover)

### 重排

  （回流reflow）：当渲染树中的一部分因为元素尺寸，布局，隐藏等改变而需要重新构建（回根节点重新渲染树）。称之为回流。(树的结构发生了改变)



**重排一定会引起重绘，但重绘不一定引起重排。**



触发重拍的条件：

- 页面渲染初始化
- 添加或删除可见的DOM元素
- 元素位置的改变或使用动画
- 浏览器尺寸发生变化（resize事件发生）
- 元素尺寸的改变（大小，边框，外边距等）

重排及其消耗资源。



重构：

- 将静态页面的大件构成称之为页面的重构。

- 浏览器重构页面是重排的过程。

## 兼容性：BFC

**在解释 BFC 是什么之前，需要先介绍 Box、Formatting Context的概念。**

###**Box: CSS布局的基本单位**

　　Box 是 CSS 布局的对象和基本单位， 直观点来说，就是一个页面是由很多个 Box 组成的。元素的类型和 display 属性，决定了这个 Box 的类型。 不同类型的 Box， 会参与不同的 Formatting Context（一个决定如何渲染文档的容器），因此Box内的元素会以不同的方式渲染。让我们看看有哪些盒子：

- **block-level box:display** 属性为 block, list-item, table 的元素，会生成 block-level box。并且参与 block fomatting context；
- **inline-level box:display** 属性为 inline, inline-block, inline-table 的元素，会生成 inline-level box。并且参与 inline formatting context；
- run-in box: css3 中才有， 这儿先不讲了。

###**Formatting context**

　　Formatting context 是 W3C CSS2.1 规范中的一个概念。**它是页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用**。最常见的 Formatting context 有 Block fomatting context (简称BFC)和 Inline formatting context (简称IFC)。

　　CSS2.1 中只有 `BFC `和 `IFC`, [CSS3](http://www.cnblogs.com/lhb25/category/146075.html) 中还增加了 `GFC `和 `FFC。`

### **什么是BFC**

　　BFC(Block formatting context)直译为"块级格式化上下文"。**它是一个独立的渲染区域**，只有Block-level box参与， 它规定了内部的Block-level Box如何布局，并且与这个区域外部毫不相干。

### **BFC布局规则**

1. 内部的Box会在垂直方向，一个接一个地放置。
2. Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠
3. 每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。
4. BFC的区域不会与float box重叠。  （**用来实现布局自适应**）
5. BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。
6. 计算BFC的高度时，浮动元素也参与计算（**用来解决父元素塌陷**）

### **如何生成BFC?**

1. 根元素
2. float属性不为none
3. position为absolute或fixed
4. display为inline-block, table-cell, table-caption, flex, inline-flex
5. overflow不为visible

注：**并不是所有的块级标记都有BFC渲染规则**

### **BFC在布局中的作用**

1. 防止margin重叠
2. 解决父元素塌陷
3. 自适应布局

- 防止margin重叠

  ```css
  <style>
       p {
           color :  #f55 ;
           background :  #fcc ;
           width :  200px ;
           line-height :  100px ;
           text-align : center ;
           margin :  100px ;
       }
  </style>
  <body>
       <p>Haha</p>
       <p>Hehe</p>
  </body>
  ```

  ![mark](http://qiniu.wind-zhou.com/blog/201204/349il4Ik74.png?imageslim)

  我们可以在p外面包裹一层容器，并触发该容器生成一个`BFC`。那么两个P便不属于同一个`BFC`，就不会发生margin重叠了。

  ![mark](http://qiniu.wind-zhou.com/blog/201204/k9HJHECK38.png?imageslim)

- 浮动相关问题（解决父元素塌陷）

  ```css
  <style>
  	     .par{
  	         border: 5px solid  #00FFFF;
  	         width: 300px;
  		 /*overflow :  hidden ;*/	 
  	     }
  	 
  	     .child {
  	         border: 1px solid #fcc;
  	         width:100px;
  	         height: 100px;
  	         float: left;
  	     }
  	</style>
  	
  -------------------------------------------------------------------------------------------------
  	<body>
  	     <div  class = "par" >
  	         <div  class = "child" ></div>
  	         <div  class = "child" ></div>
  	     </div>
  	</body>
  ```

![mark](http://qiniu.wind-zhou.com/blog/201204/jD490hm199.png?imageslim)

去掉注释后

![mark](http://qiniu.wind-zhou.com/blog/201204/5K8bCa2bl4.png?imageslim)

- 自适应布局
  
  **两列布局：一侧固定另一侧自适应**
  
  ```css
  <style>
  		.out{
  			width: 100%;
  			height: 500px;
  			border: #000000 2px solid;
  		}
  		.one{
  			width: 200px;
  			height: 250px;
  			background-color: #ccc;
  			height: 350px;
  		}
  		
  		.two{
             		 height: 350px;
  			height: 250px;
  			background-color: #00FF00;
  		}
  		
  	</style>
  ------------------------------------------------------------------------------------------
  	<body>
  	     <div class="out">
  	     	<div class="one"></div>
  		   <div class="two"></div>
  	     </div>	    
  	</body>
  ```
  
  ![mark](http://qiniu.wind-zhou.com/blog/201204/J5hJld9d7h.png?imageslim)
  
  这时one和two重叠，给two开启BFC后
  
  ![mark](http://qiniu.wind-zhou.com/blog/201204/kH8H2j03GI.png?imageslim)
  
  **三列布局：两端固定，中间自适应**
  
  左右两块各设置浮动，当左右各设置float，main不设置时，会出现遮盖现象
  
  ![mark](http://qiniu.wind-zhou.com/blog/201204/11GCFKBilB.png?imageslim)
  
  当给main设置`overflow：hidden；`后，实现了中间main的自适应。
  
  ![mark](http://qiniu.wind-zhou.com/blog/201204/bGbDaJ8C4L.gif)
  
  **注：做3例布局时，html写作顺序left-main-main。**
  
  

### 参考链接

[CSS的BFC详解](https://blog.csdn.net/shadow_zed/article/details/72811975)

 [CSS中的BFC详解](https://www.cnblogs.com/chen-cong/p/7862832.html)








































# lesson-2 选择器

## 简介

**选择器的概念：**

要使用css对HTML页面中的元素实现一对一，一对多或者多对一的控制，这就需要用到CSS选择器。

HTML页面中的元素就是通过CSS选择器进行控制的。

**选择器的类别：**

- 基本选择器
- 层次选择器
- 伪类选择器（过滤器）

## 基本选择器

###标记选择器

（1）选择器名和标记名相同

（2）**自动**应用到相同的标记

```html
<style type="text/css">
			p{
				color:#f00;
				font-size: 2.5rem;
			}
			h2{
				background-color: #0000FF;
				font-weight: normal;
			}
</style>
```

###类别选择器

标记选择器无法进行精准控制，所以有了第二种。

（1）类别名需要用户自己定义

（2）**手动**应用到标记里

总体分两步:

1. 定义类（前面有一个`.`）

```html
<style type="text/css">
			.one{
				color: chartreuse;
			}
		</style>
```

2. 引用类

```html
<p class="one"> hello world2</p>
```

**注：如果两个类的类名相同，在样式不冲突的情况下样式会叠加，样式冲突时会服从就近原则。**

也可以给**一个标记引用多个类，中间用空格分隔**，name样式会叠加，如果两个类发生样式冲突则服从就近原则。

```html
<p class="one two"> hello world2</p>
```

###ID选择器

（1）ID名自己定义

（2）手动应用到不同地方

（3）ID选择器和class选择器不同的是：**ID选择器只能用一次**

```css
#first{
		background-color:yellow;
	}
```

```html
<h2 id="first">标题2</h2>
```

### 三种选择器优先级问题

**ID选择器>类别选择器>标签选择器**

（按元素控制范围来分，控制的越精细优先级越高）

## 层次选择器

| 选择器                          |                                        | 举例         |                                        |      |
| ------------------------------- | -------------------------------------- | ------------ | -------------------------------------- | ---- |
| selector1` `selector2           | 包含选择器                             | div` `span   | 选择被div里包含的所有的span            | css1 |
| selector，selector2，sselector3 | 选择器分组（集合）为了减少重读的代码量 | \#two,#three |                                        | css1 |
| selector>selector2              | 子元素选择器（找儿子）                 | div>span     | 选择属于selector1元素的子元素selector2 | css2 |
| selector+selector2              | 下一个相邻的选择器（找同级选择器）     | div+span     | 选择**紧挨着**selector1后面的selector2 | css2 |
| selector1~selector2             | 接下来所有的统计指定元素               |              |                                        |      |

**‘+’选择器则表示某元素后相邻的兄弟元素，也就是紧挨着的，是单个的。而‘~’选择器则表示某元素后所有同级的指定元素，强调所有的。**

**1、包含选择器练习：**

```css
div span{
				color: aqua;
			}
```

```html
<div>
	<p>生活不止眼前的枸苟且
	<span >还有诗和远方的田野	</span>
	我奋不顾身的来到这世界</p>
</div>
<span>为了在那片海不够一切</span>
```

![mark](http://qiniu.wind-zhou.com/blog/201106/dlihKBF02g.png?imageslim)

**2、选择器分组练习：**

源码：

```css
 #two,#three{
				 color:white;
				 background-color: purple;
				
			 }
			 #two{
				  border: 2px #000000 solid ;
			 }	/*two选择器单独的样式*/	 
```

```html
		<p  id="two">uhfuihwfiorfoirwefoir</p>
		<p id="three">道具藕节解耦一北极鸥基本瞥见板配筋批号金额股票</p>
```

效果图：

![mark](http://qiniu.wind-zhou.com/blog/201106/J386kfj2AH.png?imageslim)

**3、子元素选择器练习（找儿子）：**

```css
div>span{
				color: aqua;
			}
```

```html
<div>
			<p>生活不止眼前的枸苟且
			<span >还有诗和远方的田野	</span>
			我奋不顾身的来到这世界</p>
			<span>这里会受影响！！！</span>
		</div>
		<span>为了在那片海不够一切</span>
```

![mark](http://qiniu.wind-zhou.com/blog/201106/hbB9FBFa5H.png?imageslim)

***易错点：***

当子元素选择器中的两个选择器是**类别选择器时**，**这里的相互父子关系仍然是按标记的父子关系来划分，类别选择器之间并没有所谓的继承关系。**

练习：

**正确写法**：

```css
	.four>.six{
				color: #00FFFF;
				border: #000000 2px solid ;
				
			}/*类选择器的嵌套*/
-------------------------------------------------------------------------------------------------------------------------------------------------

	<h1 class="four">
		<p class="six"> 
			老子天下第一
			<span >  好的，你是天下第一！</span>
		</p>
	</h1>

```

上面这种情况p里面的文字样式都会改变。

![mark](http://qiniu.wind-zhou.com/blog/201106/ee7GJ7A8li.png?imageslim)

**错误写法：**

```css
	.four>.six{
				color: #00FFFF;
				border: #000000 2px solid ;
				
			}/*类选择器的嵌套*/
-------------------------------------------------------------------------------------------------------------------------------------------------

	<h1 class="four">
		<p > 
			老子天下第一
			<span   class="six">好的，你是天下第一！</span>
		</p>
	</h1>
```

上面这种写法，由于在h1的子标记p里没有找到`class="six"`,因此样式不发生变化。

![mark](http://qiniu.wind-zhou.com/blog/201106/JdJ985A27f.png?imageslim)

**4、寻找的相邻选择器（找兄弟）：**

```css
div+span{
				color: aqua;
			}
----------------------------------------------------------------------------------------------------------------------------------------------
<div>
        <p>生活不止眼前的枸苟且
        <span >还有诗和远方的田野	</span>
        我奋不顾身的来到这世界</p>
        <span>这里会受影响！！！</span>
</div>
<span>为了在那片海不顾一切</span>
```

![mark](http://qiniu.wind-zhou.com/blog/201106/C2dgcAc0i6.png?imageslim)

```css
.four+.six{
				color: #00FFFF;
				border: #000000 2px solid ;
				
			}/*类选择器的嵌套*/
----------------------------------------------------------------------------------------------------------------------------------------------

<h1 class="four">
		<p>
			老子天下第一
			<span  > 好的，你是天下第一！</span>
		</p>
	</h1>
	<span  class="six"> hello</span>
```

![mark](http://qiniu.wind-zhou.com/blog/201106/7dkBkd42hg.png?imageslim)

```css
    div+span+span{
        color: aqua;
    }
--------------------------------------------------------------------------------------------------------------------------------------------------
		<div>
			<p>生活不止眼前的枸苟且
			<span >还有诗和远方的田野	</span>
			我奋不顾身的来到这世界</p>
			<span>这里会受影响！！！</span>
		</div>
		<span>为了在那片海不顾一切</span>
		<span>这么喜欢，直接跳海吧！！！</span>
```

![mark](http://qiniu.wind-zhou.com/blog/201106/D3jCimJ7Dk.png?imageslim)

## 全局声明（特殊的一个选择器）

全局声明符号`*`

会匹配所有的标记（**一般用来做初始化**--重置样式）。

因为HTML标签有些会自带一些样式，例如h标记，因此可能会用到初始化，方便后期调整。也为了解决css的兼容性（因为不同的标记可能会在不同的浏览器显示不同）。

```css
*{
	color:#0f0;
}
```

> **关于样式的继承：...**
>
> 有的样式可以继承，有的不能继承（例如边框），大部分的文字样式都是可以继承的。

优先级的权重算法。




# lesson-7 伪类和伪元素

#伪类选择器

简介

过滤器

## 结构伪类选择器

###**（1）通过父子关系查找**

| 选择器              | 描述                                                         | 版本 |
| ------------------- | ------------------------------------------------------------ | ---- |
| :root               | 选择匹配文档的**根元素**（指的是html）                       |      |
| E:empty             | 匹配没有任何子元素的元素E（如果没有加E,则会匹配所有的空标记。） | css3 |
| E:first-child       | 匹配父元素的第一个子元素（名为e的第一个儿子）<br />**两个条件（1）儿子名为E（2）还得是大儿子** | css3 |
| E:last-child        |                                                              | css3 |
| E:nth-child(n)      | 这里n可以除了设置数字还可以设置even和odd  或表达式的写法     | css3 |
| E:nth-last-child(n) | 倒数....                                                     | css3 |
| E:only-child        | 匹配只有一个子元素的E                                        | css3 |

####练习

- [x] :root  

  ```html
  		<style type="text/css">
  			:root{
  					color: #00FFFF;
  				}
  		</style>
  ---------------------------------------------------------------------------------------------------------------------------------------
  	<body>
  		
  		<div>
  			<p>hello 这是29</p>
  			<p>hello 这是74</p>
  			<p>hello 这是73</p>
  			<p>hello 这是30</p>
  		</div>
  		<div>
  			<span>
  				hello 这里是span！
  			</span>
  		</div>
  		
  ```

  ![mark](http://qiniu.wind-zhou.com/blog/201115/d034ILjCh0.png?imageslim)

- [x] E:empty

  ```html
  		<style type="text/css">
  				
  				p:empty,span:empty{
  					display: block;
  					width: 100px;
  					height: 30px;
  					background-color: #0000FF;
  				}
  ---------------------------------------------------------------------------------------------------------------------------------------
  	<body>
  		
  		<div>
  			<p>hello 这是29</p>
  			<p></p>
  			<p>hello 这是74</p>
  			<p></p>
  			<p>hello 这是73</p>
  			<span >
  				
  			</span>
  			<span ></span>
  			
  			
  			<p>hello 这是30 </p>
  		</div>
  		<div>
  			<span> 
  				hello 这里是span！
  			</span>
  			<span ></span>
  		</div>
  ```

![mark](http://qiniu.wind-zhou.com/blog/201115/EDA89dEGHh.png?imageslim)

**注：匹配时必须是空，连空格都不能有。**

- [x] E:first-child

```css
		<style type="text/css">
	
				p:first-child{
					background-color: #0000FF;
				}
			
		</style>
------------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		
		<div>
			<h1>这是标题</h1>
			<p>29</p>   
			<p>74</p>	
			<p>73</p>
			<p>30 </p>
		</div>
		<div>
			
			<p>99</p>      /*这个会被渲染*/
			<span> 
				hello 这是span
			</span>
			<p>194</p>
			<div >
				<p>100</p>   /*这个会被渲染*/
				<p></p>
			</div>
		</div>
```

![mark](http://qiniu.wind-zhou.com/blog/201115/Bf98CIAacD.png?imageslim)

>**该选择器平匹配的标签有两个条件（1）儿子名为E（2）还得是大儿子**
>
>这里找大儿子和几层嵌套没关系。

- [x] E:nth-child(n)

这个和上面同理，唯一不同的是这个是找第n个儿子

**他也有两个两个条件：（1）标记名字为P   (2)排行老二**

这里的n也可以写成表达式的方式。

例:

```css
	<style type="text/css">			
	p:nth-child(2n+1){
					background-color: #FF0000;
				}
			
		</style>
	</head>
----------------------------------------------------------------------------------------------------------------------------------------------
		
		<div>
			<h1>这是标题</h1>
			<p>29</p>
			<p>74</p>	
			<p>73</p>
			<p>30 </p>
		</div>
		<div>
			
			<p>99</p>
			<p>55</p>
			<span> 
				hello 这是span
			</span>
			<p>194</p>
			<div >
				<p>100</p>
				<p>222</p>
				<p>444</p>
			</div>
		</div>
		
```



![mark](http://qiniu.wind-zhou.com/blog/201115/4deK36ibme.png?imageslim)

**上图中n设置为2n+1,因此排行为奇数的p标记都被选中。这也也可以设置为odd（奇数）或even（偶数）。**

- [x] E:only-child

匹配只有一个子元素的E

```css
		<style type="text/css">
				p:only-child{
					background-color: #00FFFF;
				}
			
		</style>
------------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		
		<div>
			<h1>这是标题</h1>
			<p>29</p>				/*这个不会被渲染*/
		</div>
		<div>

			<span> 
				hello 这是span
			</span>
			<div >
				<h1>标题二</h1>
				<h2>标题2</h2>
				
			</div>
			<div >
				<p>100</p> 			/*这个会被渲染*/
			</div>
		</div>
```

![mark](http://qiniu.wind-zhou.com/blog/201115/edKfCD0icJ.png?imageslim)



该选择器匹配的标记**也要满足两个条件：（1）标签名字为E（2）该标记是独生子元素**



###**（2）通过兄弟关系查找**

| 选择器                 | 描述                                                         |      |
| ---------------------- | ------------------------------------------------------------ | ---- |
| E:first-of-type        | 同类型中第一个匹配到的元素E                                  | css3 |
| E:only-of-type         | 匹配同类型的唯一一个同级兄弟E                                | css3 |
| E:nth-of-type(n)       | **同级中第n个匹配到的元素E(从第一个E开始数，并且只按E计数)** | css3 |
| E:nth--last-of-type(n) | 倒着找                                                       | css3 |

#### 练习

- [x] E:first-of-type

```css
		<style type="text/css">
			p:first-of-type{
				background-color:#00FF00 ;		
			}
		</style>
------------------------------------------------------------------------------------------------------------------------------------
	<body>
		
		<div>
			<h1>这是标题</h1>
			<p>29</p>
		</div>
		<div>

			<span> 
				hello 这是span
			</span>
			<div >
				<h1>标题二</h1>
				<h2>标题2</h2>
				<p>200</p>
				<p>300</p>
				
			</div>
			<div >
				<p>100</p>
			</div>
		</div>
</body>
```



![mark](http://qiniu.wind-zhou.com/blog/201115/BKe5HaKcci.png?imageslim)



该选择器匹配的标记**也要满足两个条件：（1）标签名字为E（2）该标记在同级中第一次被匹配到**

- [x] E:only-of-type

将改成

```css
	p:only-of-type{
				
				background-color:#00FF00 ;
				
				
			}
```



![mark](http://qiniu.wind-zhou.com/blog/201115/B9EJbDaC9e.png?imageslim)

这个选取器的选择条件比行一个更苛刻了一些，他不光要求名字为E,还要求同级中该元素唯一(该元素的父元素只嵌套了一个E)。

- [x] E:nth-of-type(n)

  此选择器和第一个用法相同。

  ```css
  		<style type="text/css">
  
  			p:nth-of-type(2){
  				
  				background-color:#00FF00 ;
  							}			
  		</style>
  -----------------------------------------------------------------------------------------------------------------------------------------
  	<body>
  		
  		<div>
  			<h1>这是标题</h1>
  			<p>29</p>
  			<p>390</p>
  		</div>
  		<div>
  
  			<span> 
  				hello 这是span
  			</span>
  			<div >
  				<h1>标题二</h1>
  				<h2>标题2</h2>
  				<p>200</p>
  				<p>300</p>
  				
  			</div>
  			<div >
  				<p>100</p>
  				
  			</div>
  ```

  ![mark](http://qiniu.wind-zhou.com/blog/201115/5aHG4aJ1AL.png?imageslim)







## 状态伪类选择器

| 选择器      | 描述                                       |      |
| ----------- | ------------------------------------------ | ---- |
| E:link      | 超链接访问前样式                           |      |
| E:visited   | 超链接访问后样式                           |      |
| **E:hover** | **划入时的样式（不只适用于超链接，常用）** |      |
| E:active    | 激活时的样式                               |      |
| E:focus     | 设置元素成为焦点时的样式（**常用于表单**） |      |
| E:checked   | 匹配表单中处于选中元素的元素E              |      |
| E:enabled   | 匹配表单中可用状态元素                     |      |
| E:disabled  | 匹配表单中禁用状态元素                     |      |

# 伪元素选择器

**生成假标记，但在代码里看不到。**

**并没有标记。起到了标记的效果。**

| E:first-letter | 设置第一个字符的样式                                         |      |
| -------------- | ------------------------------------------------------------ | ---- |
| E:first-line   | 设置第一行字符的样式（不管第一行有多少字）                   |      |
| E:before       | **内置一个content属性**，用于在前面添加内容<br />行内式（也可以放个图片） |      |
| E:after        | 往后添加，用法同上                                           |      |

###练习

- [x] E:first-letter和E:first-line

```css
		<style type="text/css">
		p{
				width: 600px;
				margin: 0 auto;
			}
	
			p::first-line{
				color:#FF0000;
			}
		
			p::first-letter{
				background-color: #00FFFF;
			} 
	
		</style>
-------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		
		<p>
			巩固跟扩大本来的既有优势中日韩+东盟+新澳中日韩低端产业要转移，高端要市场，产业资本要出路。东盟要承接
制造业，要经济增长，他们有人口红利。新澳想卖更多的资源，想要挣更多的钱。最大最强的制造+最大的消费市场+最大的产业资
本+最重要的原材料市场+最优质的人口红利超级联合，朋友们!RCEP15国，经济活跃，经济往来密集，多数国家文化相近。强强联
合，在这寒冷的经济周期里面，一定会走出不同的路。注：2019年，中国—东盟贸易额达到6415亿美元，增长9.2%，快于中国对外
贸易平均增速，在中国前三大贸易伙伴（欧盟、东盟、美国）中增速最快2019年，中日贸易总额3150.0亿美元，较上年下降3.9%。其
中，我对日出口1432.3亿美元，下降2.6%；我自日进口1717.6亿美元，下降4.9%。2019年，中韩双边贸易2845.4亿美元，比上年下
降9.2%。其中，我对韩出口1109.7亿美元，比上年增长2%；自韩进口1735.7亿美元，比上年下降15.2%。2019年中澳双边贸易额为
1589.7亿美元，增长10.9%。其中，澳大利亚对中国出口1039.0亿美元，增长18.3%，占澳大利亚出口总额的38.2%，提高4.0个百分
点；澳大利亚自中国进口550.7亿美元，下降0.8%，占澳大利亚进口总额的25.8%，提高1.4个百分点。澳大利亚与中国的贸易顺差488
.3亿美元，增长51.1%。中国继续保持为澳第一大贸易伙伴、第一大出口目的地和第一大进口来源地。2019年，新西兰商品和服务出口
总额中，有23%出口至中国，进口总额中，有16%来自中国。2019年，中新两国商品和服务贸易额（双边贸易额）达334亿纽币，其中
出口201亿纽币，进口133亿纽币。自2017年以来，中国一直是新西兰最大的贸易伙伴。中日韩2019GDP21.087万亿美元，美国21.43
万亿美元
		</p>
```

![mark](http://qiniu.wind-zhou.com/blog/201115/13l6h0k6kd.png?imageslim)



- [x] E:before和E:after

在文章前后设置一个小三角

```css
<style type="text/css">
		p{
				width: 600px;
				margin: 0 auto;
			}
		p::before,p::after{
				 content: "";
				 border: #00FFFF 1px solid;
				 display: inline-block;
			
				border: 5px transparent solid;
				border-left-color:  #000000 ; 
		}
	</style>
```



![mark](http://qiniu.wind-zhou.com/blog/201115/l9b79d8a4k.png?imageslim)



> 注：
>
> **css2中是一个冒号，css3中是两个冒号，用于区分伪类选择器和伪元素选择器。**
>
> 关于三角图标，设置时先要设置`content:"";`,然后在设置边框。
>
> 这里直接还需将其设置成` display: inline-block;`,否则呈现的三角图标不完整，不知道是什么情况。
>
> 并且若将E:first-letter和E:first-line和E:before与E:after一起设置则不会显示，**原因是？**





#属性选择器



**属性选择器可以根据元素的属性及属性值来选择元素。**

| 选择器            | 描述                                 | 版本 |
| ----------------- | ------------------------------------ | ---- |
| E[attr]           | 选取属性中的E元素                    | css2 |
| E[attr=“value”]   | 选择属性值为value的元素E             | css2 |
| E[attr^=“value”]  | 选取属性的值为value开始的E元素       | css3 |
| E[attr$=“value”]  | 选取属性的值为value结束的E元素       | css3 |
| E[attr*=“value”]  | 选取属性的值含有value的E元素         | css3 |
| E[attr~=“value”]  | 选取多个属性值中包含的value值得E元素 | css2 |
| E[attr\|=“value”] | 选取指定属性具有指定值开始的E元素    | css3 |

例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>黑马前端--属性选择器</title>
	<style>
         a[title] {       /* 属性选择器用[]表示 要挨着 */
         	color: red;
         }
         input[type=text]
         {
         	color: red;
         }
	</style>
</head>
<body>
	<a href="#" title="baidu">百度</a>
	<a href="#" title="新浪">新浪</a>
	<a href="#">搜狐</a>
	<a href="#">网易</a>
	<a href="#">土豆</a>
    <hr />  <br />
	<input type="text" value="文本框">
	<input type="text" value="文本框">
	<input type="submit" value="提交">
	<input type="submit">
	<input type="submit">
	<input type="text">
	<input type="reset">
	<input type="reset">
	<input type="reset">
</body>
</html>

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190519232757223.JPG)

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>黑马前端--属性选择器</title>
	<style>

	    /* ^= 表示font开头 */
        div[class^=font] {
        	color: green;
        }

        /* $=表示结束位置 */
        div[class$=footer] {
        	color: blue;
        }
       /*  *=表示在任意位置都可以 */
        div[class*=tao]{
        	color: red;
        }


	</style>
</head>
<body>
	<div class="font12">属性选择器</div>
	<div class="font12">属性选择器</div>
	<div class="font24">属性选择器</div>
	<div class="font24">属性选择器</div>
	<div class="24font">属性选择器123</div>
	<div class="sub-footer">属性选择器-footer</div>
	<div class="jd-footer">属性选择器-footer</div>
	<div class="news-tao-nav">属性选择器-tao</div>
	<div class="news-tao-header">属性选择器-tao</div>
	<div class="tao-header">属性选择器-tao</div>
</body>
</html>

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190519233647632.JPG)





>
>
>如何理解伪类选择器和伪元素选择器？
>
>
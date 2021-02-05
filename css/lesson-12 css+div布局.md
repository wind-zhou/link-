# lesson-12 css+div布局

##简介

主要内容：

- div与span标记

- 盒子模型

- 元素的定位

- 元素定位实例

**之前是靠表格进行布局**，现在主要使用**div+span**进行布局。

网页中的元素都有自己的位置，从而实现网页的布局。

定位使用的主要属性:**float、position、z-index**。

## float

### 一、相邻元素的浮动

**CSS的Float（浮动），会使元素向左或向右移动，其周围的元素也会重新排列。Float（浮动），往往是用于图像，但它在布局时一样非常有用。**

float：`none`|`left`|`right`  默认为none

####(1)只给某个**块级元素**设置浮动

设置：	`float: left;`  

宽度变成内容的宽**(前提是没有设置宽高)**，且居左显示。



**实验：**

设置浮动前：

![mark](http://qiniu.wind-zhou.com/blog/201122/ebfd332f8B.png?imageslim)

设置浮动后：

![mark](http://qiniu.wind-zhou.com/blog/201122/jlh2K5Jl9B.png?imageslim)



源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.one{			
				height: 50px;
				background: #00FFFF;
				float: left;    /*设置浮动*/
			}
	
		</style>
	</head>
	
	<body>
	
		<div class="one">
			hello world!
		</div>
	</body>
</html>
```



浮动还有一个副作用：**脱离文档流**。

>**什么是文档流？**

>简单说就是**元素按照其在HTML中的位置顺序决定排布的过程**。并且这种过程遵循标准的描述（块级元素 占一行，行内并行排列）。
>
>html中有三种流 ：
>
>- #### 常规流：又包含三种类型:块级元素的**块级格式**、行内元素的**行内格式**以及两种元素的**相对定位**方式。
>
>- #### 浮动（float）
>
>- #### 绝对定位（position:absolute/position:fixed）

>**脱离文档流**只有两种情况，float和绝对定位。
>
>参考链接:
>
> [一篇文章了解HTML文档流(normal flow)](https://segmentfault.com/a/1190000012425858)
>
>[HTML 文档流和文本流的理解](http://www.mamicode.com/info-detail-2338885.html)



####(2)前面元素浮动，后面元素不浮动

两个相邻的跨级元素，前面元素设置float，会导宽变为内容的宽，且前面的元素脱离文档流，不再**占据**原来的位置。

<u>会导致后面的元素上移</u>，同时后面的元素如果有内容，**不会被遮盖**，会向后移动并显示出来。



**实验：**

源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.one{
			
			
				height: 50px;
				background: #00FFFF;
				float: left;
				border: #990000 1px solid;
			}
			
			.two{
				height: 30px;
				background: #0000FF;
				border: #FF0000 1px solid;
			}
	
		</style>
	</head>
	
	<body>
	
		<div class="one">
			hello world!
		</div>
		
		<div class="two">
			你好！
		</div>
	</body>
</html>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201122/AhhfAC4Fi4.png?imageslim)

#### (3)若后面元素浮动，前面元素不浮动

​	***对前面元素无影响。***

#### (4)前后都设置浮动

**两个元素后水平排列**



![mark](http://qiniu.wind-zhou.com/blog/201122/h4A3cDdHEH.png?imageslim)



> **注：这时不是覆盖**

### 二、嵌套元素的浮动

#### （1）子元素浮动，父元素不浮动

**子元素浮动会造成父元素的塌陷。**(前提是父元素没有自己的内容)

**实验：**

源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.one{
				border: #990000 1px solid;
			}
			.two{
			
				height: 30px;
				background: #0000FF;
				border: #FF0000 1px solid;
				float: left;
			}
	
		</style>
	</head>
	
	<body>
	
		<div class="one">
			
			<div class="two">
				你好！
			</div>
		</div>
	</body>
</html>
```

**效果：**

![mark](http://qiniu.wind-zhou.com/blog/201122/gHc2fk49mK.png?imageslim)



**解决父元素塌陷问题：**

一般有一下几种方法：

- [x] （1）强行给父元素设置一个高（不怎么用）
- [x] （2）开启父元素BFC----（给父元素添加`overflow：hidden；`）
- [x] （3）在父元素里设置一个空的div用来清除浮动，同时撑起父元素高度
- [x] （4）使用伪元素选择器after（其实和第二种本质一样）

>**解决高度塌陷的问题 – 清除浮动**
>
>**高度塌陷：**高度塌陷是指当容器内包含浮动元素，容器并未像如同这些元素不浮动般的自动扩展延伸。在文档流中，父元素的高度默认是被子元素撑开的， 也就是子元素多高，父元素就多高。但是当为子元素设置浮动以后，子元素会完全脱离文档流，此时将会导致子元素无法撑起父元素的高度，导致父元素的高度塌陷。由于父元素的高度塌陷了，则父元素下的所有元素都会向上移动，这样将会导致页面布局混乱。 **所以在开发中一定要避免出现高度塌陷的问题, 我们可以将父元素的高度写死，以避免塌陷的问题出现， 但是一旦高度写死，父元素的高度将不能自动适应子元素的高度，所以这种方案是不推荐使用的。**
>
>**解决方案一：**根据W3C的标准，在页面中元素都有一个隐含的属性叫做Block Formatting Context ， 简称BFC，该属性可以设置打开或者关闭，默认是关闭的。当开启元素的BFC以后，元素将会具有如下的特性：
>
>i.父元素的垂直外边距不会和子元素重叠
>
>ii.开启BFC的元素不会被浮动元素所覆盖
>
>iii.开启BFC的元素可以包含浮动的子元素 
>
>**如何开启元素的BFC ？**
>
>i.设置元素浮动 ，使用这种方式开启，虽然可以撑开父元素，但是会导致父元素的宽度丢失 而且使用这种方式也会导致下边的元素上移，不能解决问题 。
>
>ii.设置元素绝对定位。
>
>iii.设置元素为inline-block ，可以解决问题，但是会导致宽度丢失，不推荐使用这种方式 。
>
>iv.将元素的overflow设置为一个非visible的值。
>
>推荐方式：**将overflow设置为hidden**是副作用最小的开启BFC的方式。 但是在IE6及以下的浏览器中并不支持BFC，所以使用这种方式不能兼容IE6。在IE6中虽然没有BFC，但是具有另一个隐含的属性叫做hasLayout，该属性的作用和BFC类似，所在IE6浏览器可以通过开hasLayout来解决该问题 。开启方式很多，我们直接使用一种副作用最小的： 直接将元素的zoom设置为1即可 。zoom表示放大的意思，后边跟着一个数值，写几就将元素放大几倍。zoom:1表示不放大元素，但是通过该样式可以开启hasLayout。zoom这个样式，只在IE中支持，其他浏览器都不支持。
>
>```css
>    <body>        
>      <div class="box1">
>            <div class="box2"></div>
>       </div>        
>       <div class="box3"></div>        
>   </body>
>-------------------------------------------------------------------------
> .box1{
>      border: 10px red solid;
>      zoom:1;
>      overflow: hidden;              
>   }
>            
> .box2{
>      width: 100px;
>      height: 100px;
>      background-color: blue;
>      float: left;            
>    }
>            
> .box3{
>      height: 100px;
>      background-color: yellow;
> }
>```
>
>**解决方案二：**可以直接在高度塌陷的父元素的最后，添加一个空白的div，由于这个div并没有浮动，所以他是可以撑开父元素的高度的，然后在对其进行清除浮动，这样可以通过这个空白的div来撑开父元素的高度， 基本没有副作用 。使用这种方式虽然可以解决问题，但是会在页面中添加多余的结构。
>
>```css
>.box1{
>     border: 1px solid red;
>   }
>.box2{
>     width: 100px;
>     height: 100px;
>     background-color: blue;
>     float: left;
>    }
>.clear{
>     clear:both; 
>}
>-----------------------------------------------------------------------------------------------------------------
><body>
>     <div class="box1">
>       <div class="box2"></div>
>       <div class="clear"></div>
>     </div>
></body>
>```
>
>**解决方案三：**可以通过after伪类向元素的最后添加一个空白的块元素，然后对其清除浮动，这样做和添加一个div的原理一样，可以达到一个相同的效果，而且不会在页面中添加多余的div，这是我们最推荐使用的方式，几乎没有副作用。 在IE6中不支持after伪类, 所以在IE6中还需要使用hasLayout来处理。
>
>```css
>  .box1{
>       border: 1px solid red;
>       }    
> 
>  .box2{
>        width: 100px;
>        height: 100px;
>        background-color: blue;         
>        float: left;
>         }
>           
>   .clearfix:after{
>        /*添加一个内容*/
>         content: "";
>        /*转换为一个块元素*/
>         display: block;
>        /*清除两侧的浮动*/
>         clear: both;
>        /*设为不可见*/
>         visibility: hidden;
>         height:0;
>         }
>         
>    .clearfix{
>          zoom:1;
>         }
>---------------------------------------------------------------------------------------------------------
><body>
>    <div class="box1">
>        <div class="box2"></div>
>    </div>
></body>
>```
>
>

#### （2）父元素浮动，子元素没浮动

​	**则父子都脱离文档流。**

**实验：**

源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}
			.one{
				border: #990000 1px solid;
				float: left;
			}
			
			.two{
				height: 30px;
				background: #0000FF;
				border: #FF0000 1px solid;	
			}
	
		</style>
	</head>
	
	<body>
	
		<div class="one">
			hello world！
			<div class="two">
				你好！
			</div>
		</div>
		
	</body>
</html>
```



效果：

![mark](http://qiniu.wind-zhou.com/blog/201122/kfiC89BEEG.png?imageslim)

>简单理解：
>
>因为父元素脱离了文档流，所以html解释时会先把此处整个隔过去，连带着子元素也被动的脱离了文档流
>
>父元素脱离文档流导致父元素的宽变成了父元素内容的宽，这时子元素的宽也就变成了此时父元素的宽。
>
>**注：``脱离文档流`` 不等于`` 元素的宽变为内容的宽``**

### 三、清除浮动



 清除浮动可两大类方法

- 兄弟元素设置clear:both
- 父元素生成BFC（IE8+） 或haslayout(IE6/IE7)



<font size="5px" color="green"><b>**网页布局**时如果前面元素设置了浮动，可能会对后面的元素产生影响。一般有两种方法：</b></font>

1、**后面元素也设置浮动**，并调整width，使其挤到该在的位置

2**、使用清除浮动属性clear：**`left`|`both`|`right`

**实验：**

(1)通过设置width硬挤下去

源码:

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			*{
				margin: 0;
				padding: 0;
			}

			.container{
				
				width: 1000px;
				height: 800px;
				background-color: #00FF00;
			}
			
			.one{
				width: 300px;
				background-color: #0000FF;
				float: left;
			}
			
			.two{
				background-color: #90BCFF;
				width:701px;
				height: 300px;
				float: left;
			}
		
		</style>
	</head>	
	<body>			
		<div class="container">			
				<div class="one">
					你好！
				</div>
				
				<div class="two">
					
				</div>			
		</div>					
	</body>
</html>
```

![mark](http://qiniu.wind-zhou.com/blog/201123/A39I4H16h0.gif)

（2）通过clear属性调整

**clear属性规定元素的哪一侧不允许有其他浮动元素**。

在下方div中设置`clear：left：`

设置前后的效果图：

![mark](http://qiniu.wind-zhou.com/blog/201123/FL0g5mH0Jg.png?imageslim)





使用clear处理嵌套时，子元素浮动而导致的父元素塌陷问题

一般有三种方法：

（1）开启父元素BFC

（2）在父元素里设置一个空的div用来清除浮动，同时撑起父元素高度

（3）使用伪元素选择器after（其实和第二种本质一样）

###四、练习

使用float进行页面布局

源码:

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			body{
				margin: 0;
				padding: 0;
			}
		
			.one{
				width: 100%;
				height: 100px;
				background: #f00;
			}
					
			.two,.four{
				width: 20%;
				height: 300px;
				background: #00FF00;
				float: left;
			}
			
			.three{
				width: 60%;
				height: 300px;
				background-color: #0000FF;
				float: left;
			}
			
		
			.five{
				width: 100%;
				height: 100px;
				background-color: #000000;
				clear: left;  /*这里清除浮动，否则div-5会跑到上面去，并被覆盖*/
			}
			
			
		</style>
	</head>
	<body>
		<div class="one">
		</div>

		<div class="two">
		</div>
        
		<div class="three">
		</div>
		
		<div class="four">
		</div>
		
		<div class="five">
		</div>
	</body>
</html>

```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201129/BfCiIBD4II.png?imageslim)



### 五、参考链接

 [CSS深入——深入理解之float浮动](https://www.cnblogs.com/webfuns/articles/8516466.html)

[深入理解css浮动](https://www.cnblogs.com/starof/p/4608962.html)

[CSS深入理解之float浮动](https://blog.csdn.net/MySunshine07/article/details/82155505)

 [【前端Talkking】CSS系列——CSS深入理解之float浮动](https://segmentfault.com/a/1190000014554601)

 [CSS之浮动布局（float，浮动原理，清除/闭合浮动方法）](https://www.cnblogs.com/Ry-yuan/p/6816290.html)

## position

**用来指定块元素相对于父块的位置和相对于自己的位置**

position：`static（默认）`|`absolute`|`relative|fixed`

**先看下各个属性值的定义：**

1、static（静态定位）：默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）。

2、relative（相对定位）：生成相对定位的元素，通过top,bottom,left,right的设置相对于其正常（原先本身）位置进行定位。可通过z-index进行层次分级。　　

3、absolute（绝对定位）：生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。可通过z-index进行层次分级。

4、fixed（固定定位）：生成绝对定位的元素，相对于浏览器窗口进行定位。元素的位置通过 "left", "top", "right" 以及 "bottom" 属性进行规定。可通过z-index进行层次分级。

用的时候写两个就够了（横+纵）。

### absolute绝对定位

####1、相邻元素的定位

（1）当一个元素绝对定位，**他的宽会变成内容的宽**(包裹特性)，并且也会脱离文档流。

（2）当前面元素设置了绝对定位，后面的元素会上去，**并进行遮盖，内容也不会错开**。

（3）当后面的元素设置了绝对定位，对上面元素不影响。

（4）前后元素都设置绝对定位，则两者都脱离文档流，后面的会对前面的内容进行遮盖。

实验：

①

```css
	
div{
    background-color: #009EE5;
    border: #000000 1px solid;
    /* position: absolute; */
}
---------------------------------------------------------------------------------------------------------		
	<body>
			<div >
				hello!
			</div>	
	</body>
```



![mark](http://qiniu.wind-zhou.com/blog/201130/iFkmJAbKgf.png?imageslim)

②

```css
.one{
					width: 300px;
					height: 200px;
					background-color: #009EE5;
					position: absolute;
			}
			
			.two{
				border: #000000 1px solid;
			}
-----------------------------------------------------------------------------------------
			<div class="one">	</div>
			<div class="two">
				一句好的广告语，能强烈的激发人的感情，产生心理认同感。
				对于广告人来说，无论走到哪里，最敏感的就是广告语。
				一句广告语，可能只有短短几个字或一两句话，却是一个品牌的精华所在。
			</div>
```

![mark](http://qiniu.wind-zhou.com/blog/201130/efl4I94FEC.png?imageslim)

③

④

```html
<style type="text/css">
			#one{
				width: 300px;
				height: 300px;
				background-color: #0000FF;
				position: absolute;
			}
			#two{
				width: 100px;
				height: 100px;
				background:#00FF00;
				position: absolute;
			}
		</style>
-----------------------------------------------------------------------------------------------------------
	<body>
			<div id="one">
				
			</div>
			<div id="two">
				
			</div>
	</body>
```



![mark](http://qiniu.wind-zhou.com/blog/201201/0jc52e33h2.png?imageslim)



####2、嵌套元素的定位

如果父元素和子元素都设置绝对定位，则他们各自脱离文档流。父元素的宽变成了内容的宽（子元素撑起来）

```css
<style type="text/css">
			#one{
			
				height: 300px;
				background-color: #0000FF;
				/* position: absolute; */
			}
			#two{
				
				height: 100px;
			 	background:#00FF00;
				margin: 0 auto;
				position: absolute;
			}
		</style>
-------------------------------------------------------------------------------------------------------------------
	<body>
			<div id="one">
				<div id="two">
					kkkkkdjkjfjdio
				</div>
			</div>
		
	</body>
```

![mark](http://qiniu.wind-zhou.com/blog/201201/b2IC6J63JB.png?imageslim)

**绝对定位是相对于离他最近的那个设置了定位的祖先元素。如果没有设置定位的祖先元素，则相对于body。**



### relative相对定位

相对定位只是相对该元素本身（**当前位置**）且**不会脱离文档流**





> float可以和relative混用，float不能喝absolute混用;
>
> float可以和margin搭配使用。
>
>  相关链接： [关于对同一个盒子同时设置相对定位和浮动或者绝对定位和浮动的问题](https://blog.csdn.net/qq545698514/article/details/53606478)



分情况讨论

1、 只有一个元素，进行相对定位

这是并没有脱离文档流，因此下面元素没有上去

设置了相对定位的元素层次比较高，会遮盖住其他，如果两个元素都设置了相对定位，则后设置相对定位的层次较高。

### fixed 固定定位

相对于浏览器窗口进行定位， 他不随着滚动条的滚动而移动，固定在浏览器窗口某个位置。

（常用于做固定的广告、导航条）

**也会导致脱离文档流。**

### z-index 空间位置

用来调整定位时重叠快的上下位置。



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		
		<style type="text/css">
			
			body{
				margin: 0;
				padding: 0;
			}
		.one,.two,.three{
			width: 200px;
			height: 300px;
			position: absolute;
		}
		
		.one{
			background-color: #00FF00;
			left: 30px;
			top: 30px;
			z-index: 4;
		}
		
		.two{
			background-color: #0000FF;
			left: 50px;
			top: 50px;
			z-index: 3;
		}
		
		.three{
			background-color: #00FFFF;
			left: 70px;
			top: 70px;
			z-index: 2;
		}
		</style>
	</head>
	<body>
		
		<div class="one">
			hello world!
		</div>
		
		<div class="two">
			你好！
			
		</div>
		
		<div class="three">
			今天小雪！
		</div>
	</body>
</html>
```





<img src="http://qiniu.wind-zhou.com/blog/201122/d7LA29DfCG.png?imageslim" alt="mark" style="zoom:50%;" />







## 固定布局

### 固定浮动布局

- 不随窗口的变化为变化

- 主要使用浮动进行布局

- 缩放窗口不会影响网页布局

- 使用`margin：0 auto；`方式进行居中

  >margin:0 auto;进行居中有条件的
  >
  >1. width要小于屏幕
  >2. **不能拖文档流**

### 固定定位布局

- 不随窗口的变化为变化
- 主要是用`position：absolute；`进行定位
- 缩放窗口不会影响网页布局
- 采用`position：absolute；`拉回方式进行居中

定位拉回



box-sizeing  设置宽高的范围

边框-圆角

语法规则：

border-radius

做圆：（1）盒子是正方形（2）border-redius设置值大于边长的一半



border-redius：20px 50px；  

border-redius：20px 30px 50px ；左上 对角 右下

border-redius：20px 30px 40px 50px； 左上 右上 右下 坐下



边界图片：

border-image  用来添给边框添加背景图片



border-image-source：url（）-=

border-image-slice：number；（最少一个值，最多四个值）



背景透明

opaticy  这个会控制整个标记的不透明度。



## inline-block布局

**css之display:inline-block布局**

**1.解释一下display的几个常用的属性值，inline ， block， inline-block**

- inline（行内元素）:
  1. 使元素变成行内元素，拥有行内元素的特性，即可以与其他行内元素共享一行，不会独占一行. 
  2. 不能更改元素的height，width的值，大小由内容撑开. 
  3. 可以使用padding上下左右都有效，margin只有left和right产生边距效果，但是top和bottom就不行.
- block（块级元素）:
  1. 使元素变成块级元素，独占一行，在不设置自己的宽度的情况下，块级元素会默认填满父级元素的宽度. 
  2. *能够改变元素的height，width的值.* 
  3. **可以设置padding，margin的各个属性值，top，left，bottom，right都能够产生边距效果.**
-  inline-block（融合行内于块级）:
  1. 结合了inline与block的一些特点，结合了上述inline的第1个特点和block的第2,3个特点.
  2. 用通俗的话讲，就是不独占一行的块级元素。如图:

图一:
![img](https://img-blog.csdnimg.cn/img_convert/b65da41e21949087955e6e55d23fdb72.png)
图二：
![img](https://img-blog.csdnimg.cn/img_convert/d0c56a0a4c3ef1e4470f21ab0fc9305d.png)

两个图可以看出，display：inline-block后块级元素能够在同一行显示，有人这说不就像浮动一样吗。没错，display：inline-block的效果几乎和浮动一样，但也有不同，接下来讲一下inline-block和浮动的比较。

 

**2.inline-block布局 vs 浮动布局**

  **a.不同之处：**对元素设置display：inline-block ，元素不会脱离文本流，而float就会使得元素脱离文本流，且还有父元素高度坍塌的效果

  **b.相同之处：**能在某程度上达到一样的效果

　　我们先来看看这两种布局：
图一：display：inline-block
![img](https://img-blog.csdnimg.cn/img_convert/4f1294a50aa00199f32258e6c2ff9ac4.png)
图二：对两个孩子使用float：left，我在上一篇浮动布局讲过，这是父元素会高度坍塌，所以要闭合浮动，对box使用overflow：hidden，效果如下：
![img](https://img-blog.csdnimg.cn/img_convert/70a125c5ff7e29abd3e4927b8f87ccb3.png)

\>>乍一看两个都能做到几乎相同的效果，（仔细看看display：inline-block中有间隙问题，这个留到下面再讲）

　　**c.浮动布局不太好的地方：**参差不齐的现象，我们看一个效果：
图三：
![img](https://img-blog.csdnimg.cn/img_convert/ddd4c5abcd812415582599761dfa0570.png)
图四：
![img](https://img-blog.csdnimg.cn/img_convert/35f5f8b50e078a8f36dd33c227164000.png)
\>>从图3,4可以看出浮动的局限性在于，若要元素排满一行，换行后还要整齐排列，就要子元素的高度一致才行，不然就会出现图三的效果，而inline-block就不会。

 

**3.inline-block存在的小问题：**

　　**a**.上面可以看到用了display:inline-block后，存在间隙问题，间隙为4像素，这个问题产生的原因是换行引起的，因为我们写标签时通常会在标签结束符后顺手打个回车，而回车会产生回车符，回车符相当于空白符，通常情况下，多个连续的空白符会合并成一个空白符，而产生“空白间隙”的真正原因就是这个让我们并不怎么注意的空白符。

 

　　**b.**去除空隙的方法：
　　1.对父元素添加，{font-size:0}，即将字体大小设为0，那么那个空白符也变成0px，从而消除空隙
　　现在这种方法已经可以兼容各种浏览器，以前chrome浏览器是不兼容的
图一：
![img](https://img-blog.csdnimg.cn/img_convert/b6da26893ff8ad1dd4dd7a2018781074.png)

 

　　**c.**浏览器兼容性：ie6/7是不兼容 display：inline-block的所以要额外处理一下：
　　在ie6/7下：
　　对于行内元素直接使用{dislplay:inline-block;}
　　对于块级元素：需添加{display:inline;zoom:1;}

 

**4.总结:**

　　display:inline-block的布局方式和浮动的布局方式，究竟使用哪个，我觉得应该根据实际情况来决定的：
　　a.对于横向排列东西来说，我更倾向与使用inline-block来布局，因为这样清晰，也不用再像浮动那样清除浮动，害怕布局混乱等等。
　　b.对于浮动布局就用于需要文字环绕的时候，毕竟这才是浮动真正的用武之地，水平排列的是就交给inline-block了。

5.**将div内所有组件至于同一行的方法**

   目前可行的方法有三个：

​    ①.``<div style="display:inline-block">组件1</div> `` `<div style="display:inline-block">组件2</div>`

​    ②.``<div style="float:left">组件1</div>``  `<div style="float:left">组件2</div>`

​    这两种方法区别在哪前四条已经解释清楚，用②会将两个组件重叠，还需要给其中一个组件添加margin。这里还有第三种方法

​    ③. `<div style="position:absolute">组件1</div>`   `<div style="position:absolute;margin-left:xxxx">组件2</div> `

​    通过将两个组件进行绝对定位来保持在同一行，但这样也会有重叠现象，所以还是用①最好

>
>
>参考链接：https://www.cnblogs.com/jiangzilong/p/6145157.html
>
>







































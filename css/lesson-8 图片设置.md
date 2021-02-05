# lesson-8 图片设置

## 图片样式

HTML中图片的属性包括border、width、height、src、alt、title、align七种。

在css中，width、height、border可以在css设置样式。

**实验证明src、title、alt、align不能写在css中。**

### 图片边框

HTML中img的border只能设置粗细，而不能设置颜色等样式，但在css中可以。

例：

```css
	<style>
			div{
				height: 500px;
				border: 1px #000000 solid;
				/* text-align: center; */
				/* background-color: rgba(	0,0,0,0.5); */
				
			}
			
			
			img{
				width: 200px;
				height: 200px;
				border: 2px #00FF00 dashed;
		/* 		display: block;
				margin: 0 auto */;
				
			
				
			}
			
		</style>
--------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		<div><img src="../edge.png"   title="这是张图片" alt="加载失败"/></div>
	</body>
```

![mark](http://qiniu.wind-zhou.com/blog/201115/LIjIL29DCI.png?imageslim)



**图片的3pxBug**

原因：

因为img在a中垂直对齐方式也就是vertical-align默认值为baseline，所以img最垂直对齐时是按照a的基线对齐而不是底线

![mark](http://qiniu.wind-zhou.com/blog/201209/CKjlbAh7C3.png?imageslim)

图片在块级标签内有个“图片3px”的bug，解决方案就是把图片设置为块级。（其实是开启了bfc---后面会讲）

>注：3px的bug我在div套img时并没有发现，很奇怪。
>
>不过在列表的td中套img确实有这样的问题。
>
>解决方案有多个
>
>- vertical-align:bottom;（实践证明设置成top|bottom|middle都好使）
>
>- display：block；（**最常用**）
>
>- ...
>
>- # [css关于a标签嵌套img问题与基线问题](https://www.cnblogs.com/yaliu/articles/4484395.html)



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
		table{
			height: 400px;
			width: 400px;
			border-collapse: collapse;
			margin: 0 auto;
			border: #000000 1px solid;
			
		}
		td{
			width: 200px;
			height: 200px;
			border: #000000 1px solid;
		}
			img{
				width: 200px;
				height: 200px;
			/* 	display: block; */
				
				
			}
			
		</style>
	</head>
	<body>
		<table >
			
			<tr>
				<td><img src="../edge.png"   title="这是张图片" alt="加载失败"/></td>
				<td>2</td>
			</tr>
			
			<tr>
				<td>3</td>
				<td>4</td>
			</tr>
		</table>
	</body>
</html>
```

![mark](http://qiniu.wind-zhou.com/blog/201115/iICE068hbF.png?imageslim)



解决方案是将图片设置成块级。上面去掉注释后，3px消失。

![mark](http://qiniu.wind-zhou.com/blog/201115/edg59jJl89.png?imageslim)

设置前：



## 图片对齐

**横向水平对齐**：不能对图直接使用text-align，而是给他的父元素设置text-align；也可以将图片设置成块级，然后用

`margin：0 auto；`

**垂直居中**：在父元素中使用vertical-align。

## 背景颜色

基本语法：

**background-color：  ；**（支持16进制，rgb和英文单词。）



```css
<style type="text/css">
			div{
				width: 300px;
				height: 200px;
                border: #000000 1px solid;
                background-color: #f00 ；
                
		}
                </style>
--------------------------------------------------------------------------------------------------------
	<body>
		<div >
			
		</div>
</body>
```

![mark](http://qiniu.wind-zhou.com/blog/201115/iD0gFLig8d.png?imageslim)



## 背景渐变色的设置

- 标准语法(包含两个参数,第一个参数可以是**角度或者英文方向**,第二个是渐变起始,可以**多个颜色值**!)

> 1. gradient : ([方向或者角度] , 起始值颜色)
> 2. firefox/chrome/ms/opera 四者的写法已经标准化,较前一些版本需要带前缀
> 3. firefox(-moz-)/chrome(-webkit-)/microsoft(-ms)/opera(-o-) [四种前缀对应四种解析引擎,我那样写只是曾经的代表浏览器,…比如现在opera都跑去用google的blink引擎]

### **渐变角度(deg是degree的缩写,角度的意思)**

> - 自下而上: to top = 0deg || 360deg
> - 自上而下: top bottom = 180deg || -180deg
> - 自右到左: to left = -90deg || 270deg
> - 自左到右: to right = 90deg || -270deg
> - 右下角到左上角: to top left = 315deg || -45deg
> - 左下角到右上角: to top right = -315deg || 45deg
> - 右上角到左下角: to bottom left = 225deg || -135deg
> - 左上角到右下角:to bootom right = 135deg || -225deg
>
> **温馨提示: 建议用角度比较标准化,英文方向的safari有些解析后和其他浏览器好像不一样**

###线性渐变：

语法规则：

**Background-image：linear-gradient（方向，颜色1，颜色2，颜色3...）**

现将背景转换成图片，在进行 设置渐变。

![mark](http://qiniu.wind-zhou.com/blog/210112/kBFa0B7Dgb.png?imageslim)

![mark](http://qiniu.wind-zhou.com/blog/210112/JH8Iae0mf6.png?imageslim)

练习：

```css
<style type="text/css">
			div{
				width: 300px;
				height: 200px;
				border: #000000 1px solid;
				margin: 0 auto;
				
				background-image:linear-gradient( to left top,#f00 ,#0f0,#00f) ;
			}
	
		</style>
-----------------------------------------------------------------------------------------------------------
	<body>
		<div >
			
		</div>
		
	</body>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201115/BmiIjgl2A8.png?imageslim)



### 径向渐变

**Background-image：radial-gradient（颜色1，颜色2，颜色3）**

练习：

```html
		<style type="text/css">
			div{
				width: 300px;
				height: 200px;
				border: #000000 1px solid;
				margin: 0 auto;
				
				background-image:radial-gradient( #f00 ,#0f0,#00f) ;
			}
	
		</style>
-------------------------------------------------------------------------------------
	<body>
		<div >
			
		</div>
		
	</body>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201115/359E9kJBjb.png?imageslim)

## 背景图片

基本语法：

**backdground-image:url(图片路径)；**

设置背景图片有一个大小的问题：

1. 当图片过大时，父元素中只显示图片的一部分
2. 当图片过小时，图片会重复来填充满父元素

###**关于图片重复：**

设置图片重复，有四个值：

background-repeat：**repeat（默认）**|**repeat-y（垂直重复）**|**repeat-x（水平重复）**|**no-repeat（不重复）**；

练习：

**默认重复**

```css
div{
				width: 300px;
				height: 400px;
				border: #000000 1px solid;
				margin: 0 auto;
				
				background-image:url(../edge.png) ;
			}
	
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201115/IJ43dh1glg.png?imageslim)



**水平重复**

```css
	div{
				width: 300px;
				height: 400px;
				border: #000000 1px solid;
				margin: 0 auto;
				
				background-image:url(../edge.png) ;
				background-repeat: repeat-x;
			}
	
```

![mark](http://qiniu.wind-zhou.com/blog/201115/Lhj0EcKBdH.png?imageslim)

**垂直重复**

```css
	div{
				width: 300px;
				height: 400px;
				border: #000000 1px solid;
				margin: 0 auto;
				
				background-image:url(../edge.png) ;
				background-repeat: repeat-y;
			}
```



![mark](http://qiniu.wind-zhou.com/blog/201115/ecd0607309.png?imageslim)



> **水平和垂直方向的重复常用来设置渐变。**
>
> 一般用ps先设计好渐变的图片，然后截取很小的一块（1px即可），然后进行水平重复或垂直重复用来实现图片的优化(可以使网页的体积变小)。



###**背景图片的位置**

基本语法：

**background-position:  ；**

有九个位置可以进行粗略的设置。

也可以通过x-y轴的像素进行精确的控制。如`background-position：20px 50px；`

也可以使用百分比的方式设置

默认是在**左上角.**



**固定背景图片位置：**

background-attachment：fixed；

相当于浏览器的位置固定住，就是说滑动滚动条时，图片的位置相对浏览器位置不变。



练习：

 **设置图片位置：**

```css
	div{
				width: 300px;
				height: 400px;
				border: #000000 1px solid;
				margin: 0 auto;
				background-repeat: no-repeat;
				background-image:url(../edge.png) ;
				background-position: center center;
			}
```

![mark](http://qiniu.wind-zhou.com/blog/201115/g535g1K5ig.png?imageslim)

**设置图片固定：**

```css
		div{
				width: 400px;
				height: 500px;
				border: #000000 1px solid;
				background-image: url(../edge.png);
				background-repeat:no-repeat;
			}
```

若想让图片在整个网站滑动式都固定位置（类似广告），可以将其设置在body中。



###**背景图样式的合并**

backgroung-color:#f00;   设置背景颜色

background-image：url();  引入图片

background-repeat：norepeat;   设置重复

background-attachment：fixed;   固定位置

background-position:10px 20px;  设置位置



**上面五个参数可以合在一起写**

`background:#f00 url（）norepeat fixed 5px 10px;`



**css3中也可以直接设置背景图大小**

基本语法

**background-size：；**

背景图也可以设置多张图片。

background-image：url(),url();

**background-size:** 100px 40px,60px 100px;

background-repeat:no-repeat,no-repeat;

background-position：0 0,20px 50px；`

练习：

```css
		div{
			
				margin: 0 auto;
				
				width: 400px;
				height: 500px;
				border: #000000 1px solid;
				background-image: url(../edge.png),url(../../selfpic2.jpg);
				background-repeat:no-repeat,no-repeat;
				background-size: 100px 40px,60px 100px;
				background-position: 20px 50px,300px 100px;
			}
```

![mark](http://qiniu.wind-zhou.com/blog/201115/EhB6CdbI73.png?imageslim)




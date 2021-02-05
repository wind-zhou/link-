# lesson-4 用css设置文字样式

HTML使用font，css中已不再使用font。

##一、字体

font-familay：字体名称1,字体名称2...

设置多个字体是为了增加兼容性（总有一款适合你）。

**字体可以被继承。**

注意：制作网页时，一些特殊字体会被制作成图片，防止用户电脑没有安装这个字体，显示出现错误。

## 二、文字大小

font-size

**网页中默认文字都是16px**。

单位说明：

绝对大小：in（英寸），cm，mm，pt（印刷点数），pc（1pc=12pt）

相对大小：px（像素），%，em（倍数）

px是相对于于设备的尺寸和分辨率有关。

%是相对于父元素的大小来进行设定。

em**相对于父元素font-size**的值来设定 。

## 三、颜色

color：支持字母和16进制和rgba（）的写法。

注：rgba（0,255,0,1）最后一个参数是指透明度。

>**文字的这几个样式都会继承**

## 四、文字粗细

font-weight：`lighter`|`normal`|`bold`|`100-900九级粗细`

900=bold    normal=400   lighter=100

## 五、倾斜

font-style：`italic`|`oblique`|`normal`    斜体|倾斜|正常

italic和oblique的区别：斜体是在原字体基础上强制拉斜，二倾斜是在设计时就设计了单独一版字体。

## 六、阴影

可以增加文字的立体感。



**text-shadow：10px 5px 5px #ccc；**

/* x偏移量 | y偏移量 | 阴影模糊半径 | 阴影颜色 */



说明：

- 第一个参数表示阴影的水平位置（必写）
- 第二个参数设置阴影的垂直位置（必写）
- 第三个参数设置阴影的模糊程度
- 第四个参数设置阴影颜色

**补充：box-shadow可以设置盒子的影子。**



>```js
>div {
>    width: 150px;
>    height: 150px;
>    background-color: #fff;
>    
>    box-shadow: 120px 80px 40px 20px #0ff;
>    /* 顺序为: offset-x, offset-y, blur-size, spread-size, color */
>    /* blur-size 和 spread-size 是可选的 (默认为 0) */
>}
>```
>
>![mark](http://qiniu.wind-zhou.com/blog/210130/Ied1B9AAGf.png?imageslim)

参考链接：

[CSS3 box-shadow 效果大全](https://www.html.cn/archives/9360/)

 [box-shadow](https://developer.mozilla.org/zh-CN/docs/web/css/box-shadow)

## 七、下划线、顶划线、删除线

text-decoration：`underline`|`overline`|`line-through`|`blink(浏览器不支持)`|`none`

none是专门为\<a>设计的，但是设置时要直接在a中设置（**因为a不能继承color和下划线样式**）

## 八、英文字母大小写

text-transform：`capitalize`|`uppercase`|`lowercase`

​                           首字母大写|全部大写|全部小写

**浏览器识别英文字母是根据空格。**

## 九、强制文本换行

word-warp：`normal（默认）`|`break-word`

默认下**单词和url在断点处换行**，使用该属性可以进行强制换行（会把长单词掰断，进行换行）。

源码：

```html
<head>
<style>
			div{
				width: 200px;
				height: 200px;
				border: 1px #f00 solid;
				/*word-wrap: break-word;*/
			}
		</style>
	</head>
	<body>
		<div>
			jijijijfoiuwhfi jcnoiwhgipvjpwjrpwhgpbvjpowrghporpborhp
		</div>
      </body>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201112/Kdj1HFBIie.png?imageslim)

去掉注释后：

![mark](http://qiniu.wind-zhou.com/blog/201112/25AFIcCH3m.png?imageslim)

##十、文本溢出

text-overflow：`clip`|`ellipsis`

说明：

- clip修建文本，超出部分隐藏
- ellipsis 用**省略号**表示被修剪文本

**注：两个使用时都需要搭配`overflow:hidden|auto`进行使用;**

>**overflow的两个参数：hidden和auto。**
>
>hidden是指超出隐藏，auto是指超出时出现滚动条。
>
>![mark](http://qiniu.wind-zhou.com/blog/201112/dfA6fhA57B.png?imageslim)



最常用的组合是`text-overflow:ellipsis`和`overflow:hidden;`,实现了超出部分隐藏和末尾省略号功能。

例子：

```html
<style>
			div{
				width: 200px;
				height: 200px;
				border: 1px #f00 solid;
				text-overflow: ellipsis;
				overflow: hidden;
				
			}
		</style>
-------------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		<div>
			jijijijfoiuwhfi jcnoiwhgipvjpwjrpwhgpbvjpowrghporpborhp
		</div>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201112/C01b01a6mg.png?imageslim)





>个人观点：
>
>text-flow=clip这个参数貌似是个废物，单独无法使用，和overflow=hidden才能出现超出被裁切的效果，但是直接使用overflow=hidden也能实现这个效果。
>
>text-flow=ellipsis和overflow:hidden搭配最常用，他和overflow:auto搭配也没什么用处，会在出现省略号的同时也会出现滚动条。
>
>![mark](http://qiniu.wind-zhou.com/blog/201112/fgAL85FbhF.png?imageslim)



##十一、段落对齐方式

###11.1、水平对齐方式

####11.1.1、对文本的水平对齐

text-align

水平对齐方式：text-align：`left`|`right`|`center`|`justify(两端对齐)`

大部分浏览器对justify支持不完善。



>注：
>
>- text-align的使用对象是**块级元素**里的**文本**。
>- 水平对齐方式是相当于自己来说，常应用于块级元素，例如p，但对于行内元素（例如span），此标记失效。
>
>- **text-align只能设置文本对齐方式，不能设置块的对齐方式。**



#### 11.1.2、对行内元素的水平对齐

​	**对行内元素设置水平对齐方式，一般在外部套一个块级标记。（也可以把行内转换成块级，但是不推荐使用）**

原理就是把行内元素作为块级内部的text，整体对其进行居中。

```html
		<style>
			span{
					border: 1px #FF0000 solid;
				}
				div{
					
					height: 200px;
					width: 400px;
					text-align: center;
					border: 1px #000000 solid;	
				}
		</style>
-------------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		<div>
			<span >
				hello world.今天你吃了吗？
			</span>
		</div>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201112/fm8m215bbh.png?imageslim)



#### 11.1.3、对块级元素的水平对齐方式

这时候是**块级套块级**的情况。

对内部的块设置`margin:0 auto`

```html
<style>
			
		
		
		.one{
			width: 400px;
			height: 400px;
			border: 1px #f00 solid;
		}
			.one div{
			
				
				width: 300px;
				height: 200px;
				border: 1px #0000FF solid;
				margin: 0 auto;      /*对此块设置水平对齐*/
				text-align: center;   /*对文字设置水平对齐*/
				line-height: 200px;  /*对文字设置垂直对齐*/
				
			}
		</style>
--------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		
			<div class="one">
				<div>
					hello 我的宝贝！
				</div>
		</div>
	</body>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201112/ibDfBE3bei.png?imageslim)

### 11.2、垂直对齐方式

####11.2.1、对文字垂直对齐

分两种情况：1、单行文本垂直对齐2、多行文本垂对齐

>1、直接在块的css中设置line-height=块的height
>
>2、把块变成单元格`display：table-cell`，再设置垂直对齐`vertical-align:middle`

#### 11.2.2、对行内元素的垂直对齐

和上面对文字操作一样。

#### 11.2.3、对块级元素的垂直对齐

**块级嵌套块级。**

> 同上面一样。
>
> 把**外层**的div设置成`display：table-cell`，并在**外层div**设置`vertical-align:middle`

```html
<style>
.one{
			display: table-cell;
			vertical-align: middle;
			width: 400px;
			height: 400px;
			border: 1px #f00 solid;
		}
			.one div{
				width: 300px;
				height: 200px;
				border: 1px #0000FF solid;
				margin: 0 auto;
				text-align: center;
				line-height: 200px;	
			}
		</style>
------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		
			<div class="one">
				<div>
					hello 我的宝贝！
				</div>
		</div>
```

效果;

![mark](http://qiniu.wind-zhou.com/blog/201112/1hbjfKDgAc.png?imageslim)

遇到问题

```html
		<style>
			
		.one{
			display: table-cell;
			vertical-align: middle;
			width: 400px;
			height: 400px;
			border: 1px #f00 solid;
			
		}
			.one div{
			
				display: table-cell;
				width: 300px;
				height: 200px;
				border: 1px #0000FF solid;
				margin: 0 auto;
				text-align: center;
				vertical-align: middle;	
			}
		</style>
------------------------------------------------------------------------------------------------------------------------------------
	<body>
		
			<div class="one">
				<div>
					hello 我的宝贝！回复我我我痕迹热尔汇聚IE润喉片房间玩爆破尔黑白配 
				</div>
		</div>
	</body>
```

![mark](http://qiniu.wind-zhou.com/blog/201112/68bijBL6ag.png?imageslim)

上面无法水平居中。

## 十三、行间距和字间距

####13.1、行间距

**行间距**：line-height  ，两行文字基线的距离。（给文字加上下划线就是基线，一般不用设置，大概在22左右，设计时一般不会超过文字的三分之二）

也可以用来作垂直居中，但要求内容不超过一行。   **常用来做按钮。**

可以在css中将line-height设置为父元素色高度。

>## css行高（line-height）及文本垂直居中原理
>
>## 一、行高的定义
>
>标准定义：两行文字基线之间的距离。
>
>那么什么是基线？
>
>基线是在英文字母中用到的一个概念，我们刚学英语的时使用的那个英语本子每行有四条线。在 CSS 中，每一行文字也可以看成一个“行盒子”，而每一个行盒子都有4 条线：顶线、 中线、基线和底线。关于行盒子的具体内容，看下图：
>
>![mark](http://qiniu.wind-zhou.com/blog/201112/Amg5GD8cBe.png?imageslim)
>
>![mark](http://qiniu.wind-zhou.com/blog/201112/Im0C9mAilG.png?imageslim)
>
>如图，每一行文字，可看成由上间距、文本内容、下间距构成，根据行高的标准定义，行高等于两条基线之间的距离，即第一行的3-4+上下间距+第二行的1-2+2-3，因为css中每一行的上间距和下间距肯定是相等的，所以代换一下，行高就等于它本身的上间距+下间距+文本高度。因此，我们也可以把行高记为，行高就是一行的高度，这一行的高度中包含了上下两个间距和文本内容本身.
>
>
>
>## 二、行高的应用
>
>因为我们刚才说了，**css中的每一行的上下间距相等，**那么，文本内容在每一行中都是居中的。利用这个原理，我们就可以搞事情了,相信你也猜到了，没错，就是垂直居中。不信，我们看代码：
>
>```css
>div{
>            line-height:50px;
>            border: 1px solid silver;
>            text-align:center;
>        }
>---------------------------------------------------------------------------------------------------------------------------------------------
> <div>123</div>
>```
>
>效果图：
>
>![mark](http://qiniu.wind-zhou.com/blog/201112/dLK8c43GKK.png?imageslim)
>
>**注意注意！：**之前我们都以为，设置文本的垂直居中是把height值和line-height值设置为一样，才能够垂直居中。其实，在这里，我们看到了，这种说法其实并不准确，我们不用设置height值，同样可以垂直居中。**原因是line-height本身就可以代表一行的高度，会自己撑开盒子**，而设置盒子的height值反而多次一举了，反而给自己找不痛快，相当于设置line-height,其实就是设置了height了，以后我们也没必要在css中多写一行height值和line-height一样了.

#### 13.2、字间距

**字间距：**letter-spacing  设置字与字的距离。值可以设置为绝对值和性对值，一般为1-2个像素。（用的很少）

## css3字体

**用来自定义字体**

语法规则：

```css
@font-face{
    font-family:name;
    src:url(字体路径)；
        font-weight：normal|bold
}

然后在选择器之设置
font-family=“上面设置的名字”
```

>寻找字体可以去阿里矢量图库。
>
>
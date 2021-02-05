# lesson-3 盒子模型

## 块级与行内

div和span区别

行内标记和快级标记区别：

- 块级元素
  1. 总是从新的一行开始
  2. **宽度，高度可以控制**
  3. 宽度缺省的容器宽度为100%（默认充满浏览器）
  4. 块级元素可以嵌套块级元素，也可以嵌套行内标记
- 行内元素
  1. 和其他（行内）元素在一行
  2. **高度、宽度**、**上下外边距**不可控（根据内容决定宽高）
  3. 宽高为其他文字或图片宽高
  4. 行内只能套行内，不能套块级

>**补充：块级元素与行内元素和空标记汇总**
>
>块级标记：address 、center、h1-h6、blockquote，p，pre，div，article，section，aside，header，footer，nav，ul，ol，dl，li，**table？**，form，farmeset
>
>行内标记：font，i，u，del，sup，sub，b，span，a，input，textarea，**select**?，label,caption
>
>单标记：br，hr，img，input，link，meta

## 块级元素与行内元素的转换

**display**

`display：block`|`inline`|`inline-block`|`table-cell`|`none`

- `block`:把行内转换成块级
- `inline`：把块级转换成行内
- `inline-block`用于行内元素，想给行内元素设置大小，却又不想单独占一行
- `table-cell`：把标记转换成表格-单元格模式（为了给其设置垂直居中）
- `none`：用于隐藏标记（例如导航的二级导航的隐藏）

### <font color="#f00">练习</font>

(1) display:`block`

```css
a{
				background-color: #00FFFF;
				/*display:block;*/
			}
----------------------------------------------------------------------------------------------------------------------------------------
	<a href="">超链接</a>123456
```

此时：

![mark](http://qiniu.wind-zhou.com/blog/201108/AgdF2GcmBJ.png?imageslim)

去掉注释后：

```css
css
a{
				background-color: #00FFFF;
				display:block;
			}
----------------------------------------------------------------------------------------------------------------------------------------
	<a href="">超链接</a>123456
```

![mark](http://qiniu.wind-zhou.com/blog/201108/J26IfGhIf6.png?imageslim)

（2）display：`inline`

```css
div{
					background-color: #00FFFF;
					/*display: inline;*/
				}
--------------------------------------------------------------------------------------------------------------------------------------
		<div class="two">
			hello 周正！
		</div>你好呀！
```

此时：

![mark](http://qiniu.wind-zhou.com/blog/201108/ehJ10d7iJc.png?imageslim)

去掉注释后：

![mark](http://qiniu.wind-zhou.com/blog/201108/H2Gk3Kd23i.png?imageslim)

（3）display：`inline-block`

```css
    span{
        width: 300px;
        height: 30px;
        background-color: #00FFFF;
        border: #000000 2px solid;
        /*display: inline-block;*/

    }
-----------------------------------------------------------------------------------------------------------------------------------------
		<span>
			世界以痛吻我，却要我报之以歌。
		</span>天空没有鸟的痕迹，而我已经飞过。
```

![mark](http://qiniu.wind-zhou.com/blog/201108/DB7ibgfd54.png?imageslim)

去掉注释后：

![mark](http://qiniu.wind-zhou.com/blog/201108/K4jLFl7Efm.png?imageslim)



（4）display：`table-cell`

  (5) display:`none`

 ```css
	a{
					background-color: #00FFFF;
					/*display: none;*/
				}
---------------------------------------------------------------------------------------------------------------------------------------
<a href=""> 超链接</a>123456
 ```

此时：

![mark](http://qiniu.wind-zhou.com/blog/201108/6c18kHElA6.png?imageslim)

去掉注释后：

![mark](http://qiniu.wind-zhou.com/blog/201108/K91DacHhl9.png?imageslim)

## 盒子模型

**什么是盒子模型？**

**所有页面的元素都可以看成一个盒子，占据着一定的空间**。一般占据的空间比单纯内容要大。

![mark](http://qiniu.wind-zhou.com/blog/201108/6eFLa34Ik4.png?imageslim)

**content+padding+border+margin**

###content

**css中的width和height控制的是content的宽高。**

### border

border的三个主要属性

- color：颜色
- width：边框的粗细
- style：主要选值：dotted（点虚线），dashed（线段虚线），solid（实线），double（双边框）

**两种写法**：

（1）分开设置

```css
border-width: 10px;
border-style: double;
border-color: #FF0000;
```

（2）放在一起设置

```css
border:#FF0000 10px double;
```

#### <font color="#f00">练习</font>

**设置盒子的边框的大小、颜色和样式。**

![mark](http://qiniu.wind-zhou.com/blog/201108/lJkj8726CB.png?imageslim)

**也可以单独设置某一条边框。**

![mark](http://qiniu.wind-zhou.com/blog/201108/f43cm55ekc.png?imageslim)

**可以实现一个三角图标的效果。**

```css
div{
				width: 0px;
				height: 0px;
				border:10px solid transparent;
				border-right-color: #000000;
			}
```

![mark](http://qiniu.wind-zhou.com/blog/201108/FL7lAkmj7I.png?imageslim)

### padding

**控制content和border的距离。**

关于padding值得四种设置方法：

1. `padding:10px`一个值是上下左右
2. `padding:10px 20px`上下，左右
3. `padding:10px 20px 30px` 上，左右，下
4. `padding:10px 20px 30px 40px`上，右，下，左（顺时针 ）

**注：div标记如果不设置默认没有padding值**。

![mark](http://qiniu.wind-zhou.com/blog/201108/KL03jLJ7ba.png?imageslim)

![mark](http://qiniu.wind-zhou.com/blog/201108/h42D33LbeG.png?imageslim)

列表有默认的`padding-left：40px`和值。

![mark](http://qiniu.wind-zhou.com/blog/201108/5fje2k5eAg.png?imageslim)

### margin

**元素和元素间的距离。**

body的margin值默认为8px。因此div显示的内容不能紧贴着浏览器边缘，可以手动去掉。

![mark](http://qiniu.wind-zhou.com/blog/201108/iLJg9G4g5e.png?imageslim)

**两个块级元素上下之间的距离是上边盒子的margin-bottom和下面盒子的margin-top谁大取谁。**

>注：两个块级元素上下之间的距离=**两个块级元素border之间的距离**，由于两个盒子各有一个margin，但这里的距离不是margin-bottom和margin-top叠加，而是取最大值。

![mark](http://qiniu.wind-zhou.com/blog/201109/IDKhLhFE0l.png?imageslim)

**行内标记不能设置宽高**，但能设置padding，但内容不动，因此当padding过大可能会导致边框越出浏览器。

行内元素设置不了上下的margin值，只有左右的margin-left和margin-right。

![mark](http://qiniu.wind-zhou.com/blog/201110/h1j6f1j7mD.png?imageslim)

**行内元素左右之间的距离是`margin-right`+`margin-left`。**

>这里**左右两边的距离是相叠加**，而不是和上下一样去最大值。

一个盒子实际的宽=`content`+`padding-left`+`padding-right`+`border-left`+`border-right`+`margin-left`+`margin-right`

高度同理。       高=`content`+`padding-top`+`padding-bottom`+`border-top`+`border-bottom`+`margin-left`+`margin-right`



**在低版本的ie浏览器(ie8及其以下)中是非标准的盒子模型。**

区别：

标准盒子模型的width（height）指的是content的大小。

非标准盒子模型中css设置的width（height）指的是content+padding+border的大小。

>**就是说按标准盒子模型设计的网页按非标准模型打开会造成内容的压缩。**
>
>压缩只压缩内容，padding和border会保持原样！

### CSS中子元素margin-top对父元素产生作用的问题

#### 问题

在实际开发中遇到一个问题，子元素`div.yellow`想通过`margin-top`留白时，会把父元素`div.green`也拉下来。
问题图片如下：
![mark](http://qiniu.wind-zhou.com/blog/201207/L0mE3e6hAd.png?imageslim)
问题代码如下：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body style="margin: 0;">
    <style>
        .top {
            height: 5px;
            background: red;
        }
        
        .father {
            width: 300px;
            height: 300px;
            background: green;
        }
        
        .son {
            width: 150px;
            height: 150px;
            background: yellow;
            margin-top: 50px;
        }
    </style>
    <div class="top"></div>
    <div class="father">
        <div class="son"></div>
    </div>
</body>

</html>
```

#### 分析

**原因：margin合并。**

可以从上面问题看到子元素`son`加了`margin-top`为`50px`，此时父元素也跟随着下来了`50px`，然而这并不是我想要的结果，那为什么会造成这个原因呢？

那我们来了解下盒模型规范：

> In this specification, the expression collapsing margins means that adjoining margins (no non-empty content, padding or border areas or clearance separate them) of two or more boxes (which may be next to one another or nested) combine to form a single margin.
> 所有毗邻的两个或更多盒元素的`margin`将会合并为一个`margin`共享之。毗邻的定义为：同级或者嵌套的盒元素，并且它们之间没有`非空内容`、`Padding`或`Border`分隔。

再说了白点就是：父元素的第一个子元素的上边距`margin-top`如果碰不到有效的`border`或者`padding`就会不断一层一层的找自己 “领导”(父元素，祖先元素)的麻烦。只要给领导设置个有效的`border`或者`padding`就可以有效的管制这个目无领导的`margin`防止它越级，假传圣旨，把自己的`margin`当领导的`margin`执行。 对于垂直外边距合并的解决方案上面已经解释了，为父元素例子中的middle元素增加一个border-top或者padding-top即可解决这个问题。

#### 解决方法

那如何解决这个问题呢，w3.org给出了思路：

1. 一个浮动的盒与任何其它盒之间的margin不会合并（甚至一个浮动盒与它的流内子级之间也不会）
2. 建立了新的块格式化上下文的元素（例如，浮动盒与’overflow’不为’visible’的元素）的margin不会与它们的流内子级合并
3. 绝对定位的盒的margin不会合并（甚至与它们的流内子级也不会）
4. 内联盒的margin不会合并（甚至与它们的流内子级也不会）
5. 一个流内块级元素的bottom margin总会与它的下一个流内块级兄弟的top margin合并，除非兄弟有空隙
6. 一个流内块级元素的top margin会与它的第一个流内块级子级的top margin合并，如果该元素没有top border，没有top padding并且该子级没有空隙
7. 一个’height’为’auto’并且’min-height’为0的流内块级盒的bottom margin会与它的最后一个流内块级子级的bottom margin合并，如果该盒没有bottom padding并且没有bottom border并且子级的bottom margin不与有空隙的top margin合并
8. 盒自身的margin也会合并，如果’min-height’属性为0，并且既没有top或者bottom border也没有top或者bottom padding，并且其’height’为0或者’auto’，并且不含行盒，并且其所有流内子级的margin（如果有的话）都合并了

简单的来讲，就是：

1. 都用`float`来定位（有条件要求，适用范围较广）
2. 为父元素添加`overflow`不为`visiable`的属性 （适用范围极广，推荐使用）
3. 为元素添加`border`（一般不用）
4. 使用绝对定位（适用范围较窄）
5. 父元素增加`padding-top`属性（改变尺寸，不建议使用）



### 补充  css3的box-size

**css3中可以使用box-size自动的控制width代表的宽度**。

（打破了标准盒子模型和非标准盒子模型的界限）

有三个值

- content-box（默认） 
- border-box
- padding-box

box-sizing属性是CSS3中引入的，有人解释为它可以指定用width属性与height属性分别指定的宽度值与高度值是否包含元素内部的补白区域，以及边框的宽度与高度。这句话有点绕，**我理解为它是一种容器高宽的计算方法**，具体是怎样的一种计算方法，和传统的计算方法又有什么区别，通过下面的例子我们可以很直观的了解到。

如图1-1所示，两个div均统一设置属性，然后针对第二个div设置了其box-sizing属性，并赋值为border-box。具体代码：

```css
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title></title>
    <style type="text/css">
        div{
            width: 50px;
            height: 50px;
            margin: 10px;
            padding: 10px;
            border: 10px solid #888;
        }
        #bs{
            box-sizing: border-box;
        }
    </style>
</head>
<body>
<div></div>
<div id="bs"></div>
</body>
</html>
```

![mark](http://qiniu.wind-zhou.com/blog/201207/iLk7Cjbbam.png?imageslim)



从图1-1中可以看出两者大小的区别非常明显，我们可以借助谷歌浏览器来查看两者是如何计算的。图1-2是传统的计算方法，也就是上面第一个div的大小。

![mark](http://qiniu.wind-zhou.com/blog/201207/ek43j4f0dE.png?imageslim)

​    从图1-1中可以看出实际div的宽度为50+10*2+10*2=90px。因为我们给div指定的高宽是指的内容区的高宽，也就是图1-1中最里面的那个区域。

![mark](http://qiniu.wind-zhou.com/blog/201207/hc4L8c936i.png?imageslim)

​    图1-3是第二个div的实际计算大小，这里div的实际宽度为10+10\*2+10*2=50px，这么一计算，我们就很明白了，原来**在设置了box-sizing为border-box后，容器的高宽就是实际容器的高宽，而不是单纯指的是内容区的大小。也可以理解为，这时候的高宽计算方式把padding和border大小也算进来了。**

![mark](http://qiniu.wind-zhou.com/blog/201207/ABKhJgkfJe.png?imageslim)




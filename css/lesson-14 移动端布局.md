# lesson-14 移动端布局

媒体查询和移动端布局

<img src="http://qiniu.wind-zhou.com/blog/201122/d7LA29DfCG.png?imageslim" alt="mark" style="zoom:50%;" />

## 媒体查询

之前的布局是PC端使用固定式布局，移动端使用自适应（百分比布局---容易变形），现在使用响应式布局（可以自动获取屏幕大小）。

**什么是响应式布局?**

响应式布局是一种弹性的栅格布局，不同的尺寸下弹性适应。里面的各个模块可以在不同尺寸实现不同的布局。

（做出的网页可以在PC端，移动端，也可以在客户端查看）



**页面会根据屏幕的分辨率自适应以及自动缩放图片，并且向下兼容，移动优先。**

第一种：link的方式：

```html
1 <link rel="stylesheet" media="screen and (max-width:600px)" href="./css/blue.css">
2     <link rel="stylesheet" media="screen and (min-width:900px)" href="./css/red.css">
3     <link rel="stylesheet" media="screen and (min-width:1200px)" href="./css/yellow.css">
```

第二种：css的方式：

```html
    <style>
        @media screen and (max-width:600px) {
            body {
                background-color: blue;
            }
        }

        @media screen and (min-width:900px) {
            body {
                background-color: red;
            }
        }

        @media screen and (min-width:1200px) {
            body {
                background-color: yellow;
            }
        }
    </style>
```

 [媒体查询的两种方式](https://www.cnblogs.com/yangguoe/p/8260945.html)

##viewpoint理论

### 基本概念

屏幕尺寸：手机对角线的长度（英寸）

屏幕的分辨率：屏幕横纵方向上的物理像素点数

屏幕密度（ppi）：每英寸上的物理像素数（掌握手机ppi的计算方式）

视口尺寸：代表横纵上的**css像素个数**

### 4个像素

![](http://qiniu.wind-zhou.com/blog/210202/aBfd1FGiH0.png?imageslim)

- 物理像素

  分辨率：屏幕呈像的最小单位 

- css像素

  web开发的最小单位

  一个css像最终一定会转成物理像素进呈现

  **注：1css像素并不等于1个物理像素**

  那么，一个css像素到底占据多少个物理像素与什么有关？---**屏幕的特性**和用户的缩放行为

- 设备独立像素

  是手机提供的 css像素和物理像素的接口

  >**设备独立像素其实是设备自己的属性**，手机出厂时由于分辨率和dpr确定
  >
  >>DPR:像素比--即**物理像素点的个数**和设备独立像素的比值
  >>
  >>
  >>
  >>![mark](http://qiniu.wind-zhou.com/blog/210202/5dHIa29151.png?imageslim)
  >>
  >>上面那这张图可以看到iphone6的DPR=2，是因为iphone6的分辨比率为750px， 设备独立像素由图可知为 375，因此DPR为 2.
  >
  >
  >
  >计算公式：**设备独立像素=分辨率/dpr**
  >
  >这个东西称之为接口我认为很合适，他是面向开发者设计的，告诉开发者你要是设计移动端的网页，我的手机上横向可以放多少个**css像素点**。

- 位图像素

  图片的宽高，在网页设计时有一个准则：**要想让图片完美显示，需要一个位图像素占据一个物理像素。**

### 三个视口理论

#### （1）布局视口

**作用：决定网页的布局。**

其实这个视口顾名思义就是网页在布局时的视口，**单位是css像素**。

可以把这个视口看做存放网页的容器，里面布局摆放各种css盒子。

主要分为电脑端和移动端：

【1】电脑端

​	电脑端其实并不很常提及这个东西，其实就是电脑屏幕上当前可以显示的css像素点数

​	注：这里之所以说当前是因为**电脑端的布局视口是会发生变化的**，但用户放大屏幕时，布局视口会变小。

> 这个也好理解，用户放大是放大的DPR，也就是一个css像素将占据更多的物理像素，但是屏幕的物理分辨率不会变，因此可用于布局的css像素点数会变小，即布局视口会变小。

【2】移动端

其实这个概念就是为移动端设计的 。**移动端布局视口大小不会变化。（因为布局视口变化不然导致重绘重排，手机承担不起这样的消耗）**

那他有什么用呢？

这就说来话长了：在移动端进行开发时，需要解决的问题就是**如何让数以亿计的网页可以在移动端完美的显示（所谓完美就是指不会出现 水平的滚动条；铺满屏幕）**

**如果没有布局视口会怎样呢？**

​	如果早些年前，手机的分辨率比较小，横向的像素点数少，那么网页必回出现水平滚行动条。

​	现在手机屏幕的跟变绿已经足够大了，其实是可以放下了，但是会出现留白。

所以这时候我们可以看出，布局视口的作用其实是做了个100%的铺满效果。

>我认为布局视口的本质是根据不同终端的分辨率，动态的改变DPR。
>
>之前我们讨论的来那两种情况，其实都有一个前提，就是DPR=1，即一个css像素占据 一个物理像素。
>
>但当有了布局视口后，一般布局视口的大小是固定的（或980或1024），但分辨率不同的终端却不一样，此时DPR也不一样。



布局视口**一句话概括就是**：在写手机端的页面时，一个手机屏幕横向可以放下多少个 css像素点。

**至于为什么布局视口设置980或1024呢？**

​	是因为一般的网页的宽度为这样，

**那么为什么要按照pc端网页的大小设计布局视口呢？**

​	是因为我们要在移动端完美显示：没有滚动条或留白（铺满）



![mark](http://qiniu.wind-zhou.com/blog/210202/EdIAdll0lE.png?imageslim)

以iphone为例，当电脑端的页面超过980px时，如果放在iphone上显示会出现滚动条。





下面用几个例子来验证布局视口的存在

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <!-- <meta name="viewport" content="width=device-width, initial-scale=1.0"> -->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        .test {
            width: 490px;
            height: 200px;
            background: pink;
        }
    </style>
</head>

<body>
    <div class="test"> </div>
</body>

</html>
```



![mark](http://qiniu.wind-zhou.com/blog/210202/e3mI7fJ9md.png?imageslim)

![mark](http://qiniu.wind-zhou.com/blog/210202/CcKe2EbBE4.png?imageslim)

注意，

<1> 上面代码中`<meta name="viewport" content="width=device-width, initial-scale=1.0">  `被注释掉了。

​		关于这行的作用后面会说。

<2>这时的DPR我们可以算一下为：（414*3）/980，注意这里的DPR并不是上面标注的3。（这里他不起作用，但这里的不起作用指的是他在开发中不起作用，但他仍然是手机的固有属性。）

#### （2）视觉视口

视觉视口顾宁思议就是可以看到的css像素点个数。

用户的缩放行为会影响到视觉视口的大小。

- 用户放大时，视觉视口变小
- 用户缩小时，视觉视口变大

道理就是方放大是增加了css像素的大小。

#### （3)理想视口

关于理想视口解释前，我们再次扩展下前面对完美适配的解释：

**所谓的完美适配指的是**：

首先不需要用户缩放和横向滚动条就能正常的查看网站的所有内容；

第二，显示的文字的大小是合适，比如一段14px大小的文字，不会因为在一个高密度像素的屏幕里显示得太小而无法看清，理想的情况是这段14px的文字无论是在何种密度屏幕，何种分辨率下，显示出来的大小都是差不多的

我们可以看到理想的视口有两种要求，一个是显示要求，另一个是大小要求。布局视口着力解决 第一个问题，但是第二个个问题却没有解决，所以这时理想视口应运而生。

要想解决第二个问题，其实也很简单，就是直接放大css像素的大小就行了呗，根据其那面我们得知，增大css的大小等同增大DPR，之前我们看到在只用布局视口时DPR一般都小于1，所以看上去字很小。

之前按照布局视口都是按980px布局的，这就导致屏幕上挤了太多的css像素，因此可以使用meta标签``<meta name="viewport" content="width=device-width, initial-scale=1.0`,对布局视口进行粗暴的调整。

这句话的作用的使布局视口的宽度等于设备的宽度（独立设备像素的值）。

**这时的DPR其实就等于设备上标注的DPR的值，一般为2，3。**



一言以蔽之就是：理想视口就是当 **布局视口=视觉视口=独立设备像素**时 的视口。

**注：**一般使用理想视口的网页都是专门为移动端设计的，移动端网页的内容相对PC端要少很多。



#### 用js获取三种视口

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <!-- <meta name="viewport" content="width=device-width, initial-scale=1.0"> -->
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        .test {
            width: 1800px;
            height: 200px;
            background: pink;
        }
    </style>
</head>

<body>
    <!-- <div class="test">

    </div> -->
</body>

<script>
    var layOut = document.documentElement.clientWidth
    var visual = window.innerWidth;
    var ideal = screen.width;
    console.log("布局视口宽度为：", layOut)
    console.log("视觉视口宽度为：", visual)
    console.log("理想视口宽度为：", ideal)
</script>

</html>
```

**移动端：**

![mark](http://qiniu.wind-zhou.com/blog/210202/FjJKBA8Kl4.png?imageslim)

**pc端：**

![mark](http://qiniu.wind-zhou.com/blog/210202/CBDeDKmIh1.png?imageslim)

缩小屏幕时

![mark](http://qiniu.wind-zhou.com/blog/210202/I9kBdGkf3k.png?imageslim)

这里的理想视口，其实是screen对象的width属性指的是屏幕的宽度。

这里的1280px其实是因为，这是我的笔记本150%显示，我的电脑分辨率为1920 px，1280*1.5=1920.

由此也可见电脑的放大显示其实还是增大了DPR,增大了css像素。



###**利用meta标签对viewport进行控制**

 移动设备默认的viewport是layout viewport，也就是那个比屏幕要宽的viewport，但在进行移动设备网站的开发时，我们需要的是ideal viewport。那么怎么才能得到ideal viewport呢？这就该轮到meta标签出场了。

我们在开发移动设备的网站时，最常见的的一个动作就是把下面这个东西复制到我们的head标签中：

```HTML
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
```

这个name为viewport的meta标签到底有哪些东西呢，又都有什么作用呢？

meta viewport 标签首先是由苹果公司在其safari浏览器中引入的，目的就是解决移动设备的viewport问题。后来安卓以及各大浏览器厂商也都纷纷效仿，引入对meta viewport的支持，事实也证明这个东西还是非常有用的。

在苹果的规范中，meta viewport 有6个属性(暂且把content中的那些东西称为一个个属性和值)，如下：

| width         | 设置***layout viewport*** 的宽度，为一个正整数，或字符串"width-device" |
| ------------- | ------------------------------------------------------------ |
| initial-scale | 设置页面的初始缩放值，为一个数字，可以带小数                 |
| minimum-scale | 允许用户的最小缩放值，为一个数字，可以带小数                 |
| maximum-scale | 允许用户的最大缩放值，为一个数字，可以带小数                 |
| height        | 设置***layout viewport*** 的高度，这个属性对我们并不重要，很少使用 |
| user-scalable | 是否允许用户进行缩放，值为"no"或"yes", no 代表不允许，yes代表允许 |

这些属性可以同时使用，也可以单独使用或混合使用，多个属性同时使用时用逗号隔开就行了。

此外，在安卓中还支持 target-densitydpi 这个私有属性，它表示目标设备的密度等级，作用是决定css中的1px代表多少物理像素

| target-densitydpi | 值可以为一个数值或 high-dpi 、 medium-dpi、 low-dpi、 device-dpi 这几个字符串中的一个 |
| ----------------- | ------------------------------------------------------------ |
|                   |                                                              |

特别说明的是，当 target-densitydpi=device-dpi 时， css中的1px会等于物理像素中的1px。

因为这个属性只有安卓支持，并且安卓已经决定要废弃~~target-densitydpi~~ 这个属性了，所以这个属性我们要避免进行使用 。















![mark](http://qiniu.wind-zhou.com/blog/210201/lGeaH0FDLh.png?imageslim)

![mark](http://qiniu.wind-zhou.com/blog/210202/Bl9hIB7AiI.png?imageslim)

![mark](http://qiniu.wind-zhou.com/blog/210202/5BIb1cd1D6.png?imageslim)



适配

### 3个意外

#### 太大的元素

**问题描述：**当使用width=device-width来设置理想视口时，如果内容超过了l理想的宽度会出现如下的问题。



```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        .test {
            width: 375px;
            height: 200px;
            background: pink;
        }
    </style>
</head>

<body>
    <div class="test">jirowhgnirwngihpniewhefhcipvbwprighpovnpowrhgppnvpnefrpnbpotnjpirw </div>
</body>

</html>
```

![mark](http://qiniu.wind-zhou.com/blog/210202/i7gha4jak2.png?imageslim)



上面本该在内容超出后出现滚动条，但却没有出现，而且div的相对大小也出现了混乱。

**解决方法：**加上`initial-scale=1.0`

![mark](http://qiniu.wind-zhou.com/blog/210202/gIkadE800G.gif)

问题解决。

#### width和initial-scale冲突

**谁大听谁的**

注：initial-scale是相对于ideal视口进行放缩的，值值大于1则理想视口比原来小，反之正相反。

#### 等比问题

没有及时meta控制viewport时：

​	是等比。（值一个div相对屏幕的相对比例），页面太小，用户体验不好

有viewport ：

​	不等比。

举例：加入一个width=490px的div，没有viewport时，在布局视口为980的手机中，永远都占据1/2大小，所以等比。

但加了viewport后，在设置一个width=490px的div，这时不同的手机理想视口不一样（一般为375,414等），所以所占比例也不再一样。



**解决方案**：进行适配，就是动态的根据不同终端的理想视口大小去调整盒子的大小，以保证在所有的终端所占比例一样。

![mark](http://qiniu.wind-zhou.com/blog/210202/50EHjbeigj.png?imageslim)



rem适配原理：改变了一个元素在屏幕上占据的css个数

有点：内有破坏完美视口

缺点：px值到rem转换复杂



<iframe src="//player.bilibili.com/player.html?aid=59646061&bvid=BV1Kt41137Jr&cid=103901593&page=15" scrolling="" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

![mark](http://qiniu.wind-zhou.com/blog/210202/Dm91EH9Eke.png?imageslim)



![mark](http://qiniu.wind-zhou.com/blog/210202/IlmmcDF3J7.png?imageslim)



viewport适配原理：改变的是DPR（css像素与物理像素的比例），因为这时将所有的终端的布局视口都做了统一调整，

做这样调整的目的是使布局视口与设计图的大小一致，因为这样在省去了px向rem转换的麻烦。

缺点：不是完美视口

有点：简单，，所量即所得



100%适配：





>参考链接：
>
>[移动前端开发之viewport的深入理解](https://www.cnblogs.com/2050/p/3877280.html)
>
>[前端 HTML5 项目实战视频教程全集（62P）| 24 小时从入门到精通](https://www.bilibili.com/video/BV1Kt41137Jr?p=12&spm_id_from=pageDriver)



Hbuilder 设置

运行-浏览器运行-设置web服务器-内置web服务器-设置ip地址

打开调试的网页-将上方url输入到手机浏览器



```html
<meta name="">
```



css3的媒体查询 media query

什么是媒体查询？

通过不同的媒体类型和条件定义的样式规则。媒介查询让css可以更精确作用于不同媒介类型（不同类型手机）和同一媒介类型的不同条件（同一手机不同型号）。

（相当于多写几套css样式，然后根据屏幕大小的分辨率不同去切换css样式）

语法：

```
@media [only] mediatype and |not(media feature){
    css-code
}
```

说明：

- mediatype 取值

  - input
  - screen
  - speech
  - all

  only可选

- and|not  逻辑运算条件

- media feature 表示媒体查询功能
  几个常用的值：width，min-width，max-width

注：媒介查询时的顺序问题

要实现屏幕大于800时显示红色；600-800呈现绿色

```html
<style type="text/css">
	
			
			@media screen  and (min-width:600px){
				div{
					width:600px;
					margin: 0 auto;
					height: 50px;
					background-color: #00FF00;
				}
			}
			
			@media screen  and (min-width:800px){
				div{
					width:600px;
					margin: 0 auto;
					height: 50px;
					background-color: #f00;
				}
			}
		</style>
--------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		<div></div>
	</body>
```

媒介查询的方式不仅可以写在css代码中，还可以在引用css文件时写入，使用link标记

`<link rel="stylesheet" type="text/css" href="a.css" media="screen and (min-width:320px)"/>`



**数学原理：**

![mark](http://qiniu.wind-zhou.com/blog/201129/03AlfhFbAE.png?imageslim)



响应式开发原理

利用rem和css3的media only screen and (min-width:100px)进行设置



- rem

>**实现自适应的根本原理还是将绝对关系转换成了相对关系（比例关系）**
>
>那么是怎么转换的呢？
>
>要进行转换成相对关系，一定要有一个绝对的参照标准，例如1024屏幕里测量的div宽高为500*400，此时我们将参照标准设为`font-size：100px`（**这个标准自己设置，以好算为主，一般设为100px**，**但要注意要保证最后最小的参照标准不能小于12px**）,则div的宽高变为5rem\*4rem。这时他们的宽高的相对长度，以及宽高相对于屏幕的相对长度就固定了下来。此时屏幕内的相对关系转换完毕。
>
>注：这里其实有两对相对关系需要转换，（1）各个div自己宽高的相对关系（2）各个div宽高相对此时屏幕的相对关系。
>
>**其实在各个不同的屏幕之间也存在一个标度尺之间的相对关系。**
>
>接下来我们只需**按照不同屏幕的相对关系设置不同屏幕参照标准的参数**，则各个屏幕内的布局就设置完毕。
>
>
>
>`使用rem的原理其实是给每种分辨率的屏幕设置了了一个参照刻度尺，不同的屏幕之间的刻度尺的也呈相对关系。`



## 弹性盒子布局（flex box）

网页布局（layout）

传统布局：position+float

FLEX布局是什么？

任何一个容器都能指定一个flex布局

采用flex布局的元素称为flex容器，他的所有容器成员叫做项目（使用时必须父子嵌套）



任何一个容器都可以指定FLEX `display：flex；`

行内元素也可以使用 `display:inline-flex`



```css
<style type="text/css">
  
				  .con{
					  border: 2px #000000 solid;
					  display: flex;  /*设置弹性盒子*/
				  }
				  
				  .con>div{
					  background-color: #009EE5;
					  border: #00FF00 solid 1px;
				  }
			</style>
----------------------------------------------------------------------------------------------------------------------------------------------
	<body>
	
		<div class="con">
			<div>hello world</div>
			<div>hello world</div>
			<div>hello world</div>
			<div>hello world</div>
		</div>
	</body>
```

给容器设置display：flex；后，**项目会水平排列，大小变成内容的大小。**

**容器的属性：**

1. flex-direction 决定主轴的方向

   - row 默认数轴为水平 起点在左端

   - row-reverse  主轴水平，起点在右端
   - column  主轴垂直 起点在上
   - column-reverse

2. flex-warp  定义如果一条轴排不下，如何换行

   - nowrap 默认不换行
   - wrap 允许换行
   - wrap-reverse

3. flex-flow  前面两个的简写

4. justify-content 定义项目在主轴上的对齐方式

   - flex-start 默认值  左对齐
   - flex-end 右对齐
   - center 居中
   - **space-between 两段对齐，项目**
   - **都相等**  常用
   - space-around

5. align-items  属性定义项目在交叉轴（垂直）如何对齐

   - flex-start  垂直居上
   - flex-end
   - center  垂直居中 
   - baseline
   - stretch  如果未设置项目的高，将会撑满容器的高



**项目属性**

1. order 属性     定义排列的顺序，数值越小，越靠前  值也可以是负数

2. flex-grow :\<number> 定义项目的放大比例 默认为0     

   如果所有的项目都设为1，则所有项目**平分**剩余空间      （平分水平空间 ，可以用此实现自适应）      
   1. flex-shrink  定义项目的缩小比例，默认为1，空间不足时，项目将缩小
     

4. flex-basis  **定义分配剩余空间之前，项目占主轴的空间**（放大之前项目的宽度）。浏览器会根据这个属性计算主轴是否有空余空间，默认auto

5. flex属性还是flex-grow，flex-shrink，flex-basis简写默认 0 1 auto。

   auto 相当于（1 1 auto ）1相当于（1 1 0%） none（0 0 auto）

6. align-self 允许单个项目和其他项目可不一样的对齐方式，可覆盖align-items属性，默认为auto，表**示继承父元素的align-items属性，**如果没有父元素，等同于stretch

   align-self：auto|flex-start|flex-end|center|baseline|stretch
   
6. 

**轮播图补充**

之前使用\<marquee>标记

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
			<img src="img/behind.jpg"  usemap="#YCY">
			<map name="YCY" >
				<area  shape="rect" coords="0,0,200,200" href ="https://wwww.baidu.com" alt="" />
			</map>
	</body>
</html>

```



## css 布局的几种方式

[前言](https://blog.csdn.net/zhang6223284/article/details/81909600#前言)

- [1 table 布局](https://blog.csdn.net/zhang6223284/article/details/81909600#1-table-布局)
- 2 flex 布局
  - [2.1 盒模型](https://blog.csdn.net/zhang6223284/article/details/81909600#21-盒模型)
  - [2.2 display / poistion](https://blog.csdn.net/zhang6223284/article/details/81909600#22-display-poistion)
  - [2.3 flexbox 布局](https://blog.csdn.net/zhang6223284/article/details/81909600#23-flexbox-布局)
- 3 float 布局
  - [3.1 高度塌陷](https://blog.csdn.net/zhang6223284/article/details/81909600#31-高度塌陷)
  - [3.2 两栏布局](https://blog.csdn.net/zhang6223284/article/details/81909600#32-两栏布局)
  - [3.3 三栏布局](https://blog.csdn.net/zhang6223284/article/details/81909600#33-三栏布局)
- 4 响应式布局
  - [4.1 meta 标签](https://blog.csdn.net/zhang6223284/article/details/81909600#41-meta-标签)
  - [4.2 使用 rem](https://blog.csdn.net/zhang6223284/article/details/81909600#42-使用-rem)
  - [4.3 media query](https://blog.csdn.net/zhang6223284/article/details/81909600#43-media-query)
- [5 总结](https://blog.csdn.net/zhang6223284/article/details/81909600#5-总结)



## 理解流式布局和响应式布局

###流式布局：

流式布局在CSS2时代就有，主要是靠百分比进行排版，可以在不同分辨率下显示相同的版式。

流式布局：**网页中主要的划分区域的尺寸使用百分数**（搭配min-*、max-*属性使用），例如，设置网页主体的宽度为80%，min-width为960px。图片也作类似处理（width:100%, max-width一般设定为图片本身的尺寸，防止被拉伸而失真）。

这种布局方式在Web前端开发的早期历史上，用来应对不同尺寸的PC屏幕（那是屏幕尺寸的差异不会太大），在当今的移动端开发也是常用布局方式，但缺点明显：宽度使用百分比定义，但是高度和文字大小等大都是用px来固定，所以在大屏幕的手机下显示效果会变成有些页面元素宽度被拉的很长，但是高度、文字大小还是和原来一样（即，这些东西无法变得“流式”），显示非常不协调。



### 响应式布局：

响应式布局的关键技术是CSS3中的媒体查询，监测设备屏幕大小，通过css媒体查询来有针对性的更改页面的布局，可以监测屏幕方向(移动设备)，设备类型等等，核心在于感知。在不同屏幕下可以显示不同版式。响应式是用于解决不用设备之间不用分辨率之间的兼容问题(一般是指PC，平板，手机等设备之间较大的分辨率差异)

响应式设计的目标是确保一个页面在所有终端上（各种尺寸的PC、手机、手表、冰箱的Web浏览器等等）都能显示出令人满意的效果，

嗯，因为是css3时代才有的新技术，那坑爹的IE6、7、8铁定不支持了，所以，记得使用媒体查询的时候要用js做一下小小的兼容哦！

对于IE6/IE7/IE8浏览器，我们使用JavaScript，根据用户显示器的分辨率，为其动态创建一个CSS 文件，在头部head标签中嵌入如下的code：

```html
<script>
if (!window.screenX) {
    //IE6~8
    var oStyle = document.createElement("link");
    oStyle.rel = "stylesheet";
    oStyle.type = "text/css";
    if (screen.width > 1024) {
        oStyle.href = "widthScreen.css";	
    } else {
        oStyle.href = "normalScreen.css";	
    }
    document.getElementsByTagName("head")[0].appendChild(oStyle);
}
</script>
```

对CSS编写者而言，在实现上不拘泥于具体手法，但通常是糅合了流式布局+弹性布局，再搭配媒体查询技术使用。

>文章链接：
>
>[理解流式布局和响应式布局](https://blog.csdn.net/lhjuejiang/article/details/80643981?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)

## 固定布局、流体布局、响应式布局

### 一、什么是响应式布局

- 响应式布局就是一个网站能够兼容多个终端——而不是为每个终端做一个特定的版本。这个概念是为解决移动互联网浏览而诞生的。
- 响应式布局可以为不同终端的用户提供更加舒适的界面和更好的用户体验。

### 二、响应式布局的优点和缺点有哪些呢

**(1) 优点**

1. 面对不同分辨率设备灵活性强
2. 能够快捷解决多设备显示适应问题

**(2) 缺点**

1. 不能完全兼容所有浏览器，代码累赘，会出现隐藏无用的元素,加载时间加长
2. 一定程度上改变了网站原有的布局结构，会出现用户混淆的情况。

### 三、实现原理

原理：简单点说响应式布局它是通过CSS中Media Query（媒介查询）@media功能，来判断我们的终端设备宽度在多少像素内，然后就执行与之对应的CSS样式。

### 四、用示例来实践一下

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>响应式布局</title>
    <style>
    body {
            background-color: #ccc;
        }
        @media screen and (max-width: 1000px) {
            body {
                background-color: red;
            }
        }
        @media screen and (max-width: 800px) {
            body {
                background-color:green;
            }
        }
        @media screen and (max-width: 600px) {
            body {
                background-color: skyblue;
            }
        }
        @media screen and (max-width: 400px) {
            body {
                background-color: yellow;
            }
        }
    </style>
</head>
<body>
    这就是简单的响应式布局示例
</body>
</html>

```

- 看完我写的示例，你可以试着敲一下在浏览器里运行，然后缩小浏览器窗口，你就会发现网页的颜色会随着你的浏览器窗口宽度变化而变色，这就是css的媒体查询功能，根据浏览器视口宽度的不同来加载不同的css样式。
- 值得注意的是：在手机设备上，我们要禁止用户来缩放屏幕。不禁止的话，可能在显示上会造成错位，以及显示的不是手机网站的样式。所以，我们要通过代码来禁止用户在手机端上缩放屏幕，已达到正常的手机网站效果。
    禁止代码如下：

```html
<meta name=“viewport” content=“width=device-width; initial-scale=1.0”>
1
```

（注意的是在页面的头部之间加上上面这句。meta viewport这个属性是在移动设备上设置原始大小显示和是否缩放的声明。）

**参数设置∶**
    width – viewport的宽度
    height – viewport的高度
    initial-scale – 初始的缩放比例
    minimum-scale – 允许用户缩放到的最小比例
    maximum-scale – 允许用户缩放到的最大比例
    user-scalable – 用户是否可以手动缩放

### 五、注意事项

响应式布局一定要注意以下两点：

- 一 是图片，在移动设备上，要做一些特定适合的小图片来匹配，如果单纯使用压缩的图片会失真，影响用户体验；
- 二 是在头部加入如下代码，目的是声明在移动设备上设置原始大小显示和是否缩放

```html
 <meta name=“viewport” content=“width=device-width; initial-scale=1.0”>

```

最后说一下通过媒体查询来加载不同的css，这是响应式布局的核心，媒体查询的方法当然也有很多，如果有兴趣深入了解，大家也可以自行百度一下。

>文章链接：
>
>[固定布局、流体布局、响应式布局](https://blog.csdn.net/weixin_42554191/article/details/104043142)



## 流式布局与固定布局

常见的面试题会让你聊一聊流式布局与响应式布局，我还没遇到过直接问他俩区别的面试官，都是根据我的项目（里面有用到流式布局＋响应式布局）。

围绕这两点感觉网上大部分博客都长得差不多，那我就用自己粗浅的理解说一下由此展开的一点问题吧。

说起流式布局首先就要提到的是老掉牙的固定布局：**浏览器大小不影响内部元素大小。**

这不就是各大银行和国企的PO网站嘛 = = 无论屏幕多大网页都显示相同宽度。

在知乎上看到：在移动端开发中其实也可以采用固定布局（有两种方法）
[点击打开链接](https://www.zhihu.com/question/21679928)

由此引入一个知识点`viewport`

用于移动端，用来设置页面的大小和缩放比例，没有为手机设计的网站，通常会使用桌面的宽度来渲染（通常是960px，980px），然后再改变字体的大小和对内容的缩放来使内容适应屏幕。然后你就要使劲拖拽页面难过 so bad

但如果设置一个简单的meta标签就可以解决这个烦人的问题：

```html
<meta name="viewport" content="width=device-width; initial-scale=1.0; user-scalable=no;">

```

width=device-width：宽度等于当前设备宽（但会导致iphone、ipad横竖屏不分）

initial-scale=1.0：初始缩放值为1（会导致IE横竖屏不分）

这两条是为了互补，所以总是同时出现。

user-scalable=no：不允许客户手动缩放（不必须）

所以才会有这两种解决办法：

①在viewport meta标签上设置width=320（因为肾5的width是320），页面的各个元素也采用px作为单位。通过用JS动态修改标签的initial-scale使得页面等比缩放，从而刚好占满整个屏幕。

②设在viewport meta标签上设置content"width=640（手机宽度都是小于640的）,user-scalable=no，页面的各个元素也采用px作为单位。由于640px超出了手机宽度，浏览器会自动缩小页面至刚好全屏。

**接下来聊一聊流体布局**

一个页面原本
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200119172635112.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjU1NDE5MQ==,size_16,color_FFFFFF,t_70)
如果我们拽浏览器减小窗口宽度，固体布局时会是这种效果
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200119172654680.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjU1NDE5MQ==,size_16,color_FFFFFF,t_70)
但流体布局，看出来有很大的不同了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200119172733945.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjU1NDE5MQ==,size_16,color_FFFFFF,t_70)
元素宽度并不是固定的，而是按照分辨率宽度进行调整，但是整体布局没有发生改变。

固定宽度布局使用的是像素，但是流体布局宽度使用的是百分比，但由于高度和文字大小神马还是使用的px所以会造成一旦两个分辨率差的有点大效果就差强人意。毕竟里面的文字是不会随着你窗口的减小跟着变小的（不然你让移动端用户眼要瞎死嘛）。这也是早期屏幕分辨率相差不大时最爱用的（有人能告知一下那是啥时代吗？）

**插一波弹性布局**：包裹文字的元素的尺寸采用em、rem做单位，而页面的划分区域还是百分数或px做单位。

**在此处回顾下em和rem的区别**：em是根据自己的font-size×em尺寸得到最终的像素值；rem指的根em，他统一随着html的font-size而不是元素本身的font-size，搭配媒体查询或js，动态改变html的font-size即可改变所有（而且咱们计算起来很容易）。

在此提到的媒体查询可以引出我们今天的重头：响应式布局

CSS3中的媒体查询，可以在不同分辨率下对元素重新设置样式（不只是尺寸），在不同屏幕下可以显示不同版式。

@media screen and (min-width:480px) 手机

@media screen and (min-width:768px) 平板

@media screen and (min-width:992px) 桌面显示器

@media screen and (min-width: 1200px){ 选择器{ 属性：值; } } 大于1200px时

这四个值是常用的，注意先后顺序，小的在前大的在后。

## 经典的几种历流式布局

**前言**:今天总结一下经典的流式布局的几种实现方法,方便以后查看.

**流式布局**，也叫百分比布局，是移动端开发中经常使用的布局方式之一。

**流式布局的特征**：

- 宽度自适应，高度写死，并不是百分百还原设计图。
- 图标都是固定死大小的，包括字体等也是固定死的。并不是所有的东西都是自适应的。
- 一些大的图片，设置宽度为百分比自适应即可，随着屏幕大小进行变化,对于小图标或者文本等, 一般都是定死宽高大小。

**经典的流式布局结构**:

1. 左侧固定，右侧自适应
2. 右侧固定，左侧自适应
3. 两侧固定，中间自适应（圣杯布局，双飞翼布局）
4. 等分布局

###左侧固定右侧自适应的三种实现方法:

**1.利用bfc块级格式化上下文, 实现左侧固定右侧自适应**
(1) 让左边的盒子 float: left;
(2) 让右边的盒子 overflow: hidden;

具体css代码

```html
<style>
    * {
      margin: 0;
      padding: 0;
    }
    .father {
      height: 400px;
      background-color: pink;
    }
    .left {
      height: 300px;
      width: 200px;
      background-color: orange;
      float: left;
    }
    .right {
      height: 350px;
      background-color: blue;
      /* 触发了bfc的盒子, 不与浮动的元素重叠 */
      overflow: hidden;
    }
  </style>

```

html结构

```html
<div class="father">
    <div class="left"></div>
    <div class="right"></div>
</div>

```

**2.利用定位实现左侧固定右侧自适应**

(1) 给父盒子设置padding-left 值

(2) 给左侧子盒子设置width = padding-left ,并定位到父盒子的padding-left上.

(3) 右侧盒子自适应

具体css代码

```html
<style>
    * {
      margin: 0;
      padding: 0;
    }
    .father {
      height: 400px;
      background-color: pink;
      position: relative;
      padding-left: 200px;
    }
    .left {
      height: 300px;
      width: 200px;
      background-color: orange;
      position: absolute;
      left: 0;
      top: 0;
    }
    .right {
      height: 350px;
      background-color: blue;
    }
  </style>

```

html结构

```html
<div class="father">
    <div class="left"></div>
    <div class="right"></div>
</div>

```

**3.利用flex布局 实现左侧固定右侧自适应**

(1) 给父盒子设置display:flex ;

(2) 左侧盒子设置固定宽高 ,右侧盒子设置flex:1 ;

具体css代码

```html
<style>
    * {
      margin: 0;
      padding: 0;
    }
    .father {
      height: 400px;
      background-color: pink;
      display: flex;
    }
    .left {
      height: 300px;
      width: 200px;
      background-color: orange;
    }
    .right {
      flex: 1;
      height: 350px;
      background-color: blue;
    }
  </style>

```

html结构

```html
<div class="father">
    <div class="left"></div>
    <div class="right"></div>
</div>
```














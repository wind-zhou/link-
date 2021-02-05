

# lesson-10 css变形

- 2D 变形
- 3D变形

##2D变形(Transform属性)

**Transform属性**

css3新增transform属性，可**用于元素的变形**，实现元素的**旋转，缩放，移动，倾斜**等变形效果。

> 由于不同浏览器有不同版本内核，因此css在不同版本浏览器中存在兼容器问题，一些属性在不同浏览器上显示需要调用相应的私有属性。现在的transform已经不需要调用私有属性了。

基本语法：

transform：`none`|`transform-functions;`

###**rotate()旋转**

rotate(角度) ：通过指定的角度参数对原元素指定一个[2D rotation](http://www.w3.org/TR/SVG/coords.html#RotationDefined)（2D 旋转），**需先有transform-origin属性的定义**。transform-origin定义的是旋转的基点，其中angle是指旋转角度，如果设**置的值为正数表示顺时针旋转**，如果设置的值为负数，则表示逆时针旋转。

如：transform:rotate(30deg)；

```html
		<style type="text/css">
			.out{
				width: 300px;
				height: 300px;
				border: #000000 1px solid;
				margin: 200px auto;
		
				
			}
			
			.in{
				width: 300px;
				height: 300px;
				background-color: #00FF00;
				
			}
			
			.in:hover{
				transform: rotate(30deg);
			}
			
		</style>
----------------------------------------------------------------------------------------------------------------------------------------------
	<body>
		
		
		<div class="out">
			<div class="in">
				
			</div>
		</div>
	</body>
```



![mark](http://qiniu.wind-zhou.com/blog/201117/gmmHFa6Ija.gif)

改成transform:rotate(-30deg)；

![mark](http://qiniu.wind-zhou.com/blog/201117/cJbg041i7G.gif)



###**scale()缩放**

语法规则：`transform：scale(x,y);  `

中心缩放，里面的内容也会变化

注意：默认值是1，它的值放大是比1大，缩小比1小。

1、scale(x,y) 定义 2D 缩放转换，改变元素的宽度和高度。

**如：transform:scale(2,1.5);**

![mark](http://qiniu.wind-zhou.com/blog/201117/D5ckAkcGJD.png?imageslim)

2、scaleX(n) 定义 2D 缩放转换，改变元素的宽度。

**如：transform:scaleX(2):**

![mark](http://qiniu.wind-zhou.com/blog/201117/0iBhfa0ji0.png?imageslim)

3、scaleY(n)  定义 2D 缩放转换，改变元素的高度。

**如：transform:scaleY(2):**

![mark](http://qiniu.wind-zhou.com/blog/201117/m2JB3Hk2Bk.png?imageslim)

###**translate()移动**

基本语法：`transform：translate（dx dy）；`  

dx表示水平方向上,dy表示垂直方向上

1、translate(x,y)   定义 2D 转换，沿着 X 和 Y 轴移动元素。

**如：translate : translate(100px,20px);**

![mark](http://qiniu.wind-zhou.com/blog/201117/dK5Ida3b2h.png?imageslim)

2、translateX(n)   定义 2D 转换，沿着 X 轴移动元素。

**如：transform:translateX(100px);**

![mark](http://qiniu.wind-zhou.com/blog/201117/5g1EGJfDc5.png?imageslim)

3、translateY(n)   定义 2D 转换，沿着 Y 轴移动元素。

 **如：transform:translateY(20px);**

![mark](http://qiniu.wind-zhou.com/blog/201117/9hcGl17FEd.png?imageslim)



###**skew()倾斜**

语法规则：`skew（angleX，angleY）；`

说明：参数为**沿着x轴和y轴的旋转角度**，单位是deg。

1、transform:skew(30deg);

注：这时上下两条边不动，水平发生倾斜，想x轴正方向倾斜30deg，如果为-30deg，则项左倾斜30deg。

![mark](http://qiniu.wind-zhou.com/blog/201117/3g9fAdm2DD.png?imageslim)

2、transform:skewY(30deg);

这时左右边不动，垂直发生倾斜，向下倾斜了30deg，反之向上。

![mark](http://qiniu.wind-zhou.com/blog/201117/jC9gbBKAkI.gif)

3、transform:skew(30deg,40deg);

![mark](http://qiniu.wind-zhou.com/blog/201117/0KK8dH58dG.gif)

###**transform-origin  设置中心**

**上面中变形默认都是沿着中心点转的。**

设置中心：

transform-origin：x y；

中心点也可以设置为负数。

![mark](http://qiniu.wind-zhou.com/blog/201117/IHE3J3JBH4.png?imageslim)



实验：

![mark](http://qiniu.wind-zhou.com/blog/201119/B167GA34El.gif)

## 3D变形

| 属性                | 描述                                 |
| ------------------- | ------------------------------------ |
| transform-origin    | 允许你改变被转换元素的位置。         |
| transform-style     | 规定被嵌套元素如何在 3D 空间中显示。 |
| perspective         | 规定 3D 元素的透视效果。             |
| perspective-origin  | 规定 3D 元素的底部位置。             |
| backface-visibility | 定义元素在不面对屏幕时是否可见。     |

主要是 **旋转、缩放、移动**（每一个有两种写法）

###**旋转**

rotate3d（x,y,z,a）

x可以是0-1之间的数值，表示旋转轴x坐标方向的矢量（表示是否沿x轴旋转）

y、z同上  a表示旋转角度

也可以分写：rotateX（x-deg） rotateY(y-deg)  rotateZ(z-deg)

###**缩放**

scale3d（sx ,sy ,sz）   或scaleX(x)  scaleY(y)  scaleZ(z)

###**移动**

translate3d(tx,ty,tz)    或translateX（x）   translateY（y）   translateZ（z）

3d转换中的translateX（x） 和 translateY（y）用法相同。

**但 translateZ 必须添加透视 才能看到效果。**

perspective：100px；  近大远小。



![mark](http://qiniu.wind-zhou.com/blog/201119/DiKK2Ab0Kg.gif)



###3D转换属性

#### 1、transform-style

- [x] 呈现三维效果

transform-style：`flat`|`preserve-3d`

用于**指定嵌套元素**在三维空间中的呈现。

**注：transform-style只能加在父元素中。**且只对子元素生效，**不能继承**。

**验证试验：**

源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
						
			.out{	
				border: #FF0000 1px solid;
				width: 300px;
				height: 400px;
			
				transform-style: preserve-3d;
			  
				background-color: #0000FF;
				transform: rotateY(0deg);
				margin: 200px auto;				
			}
			
			.in{
				width: 300px;
				height: 400px;
				margin-top:30px;
				margin-left: 30px;
				border:  #00FF00 1px solid;
				background-color: #00FF00;
				transform: rotateX(0deg);			
			}
		
		</style>
	</head>
	<body>
			<div class="out">
					<div class="in">
						
					</div>
			</div>
	</body>
</html>
```

(1)当父元素.out中设置了	`transform-style: preserve-3d;`

![mark](http://qiniu.wind-zhou.com/blog/201119/DB9lBFGjLI.gif)



这时青色矩形会透过蓝色区域，呈现3d效果。

（2）当注释掉	`transform-style: preserve-3d;`后

![mark](http://qiniu.wind-zhou.com/blog/201119/6eb4ecHAb6.gif)

这时由于没有的3d的概念，青色区域旋转过程中只会在蓝色区域上面。（没有深度，所以透不过去）。



####2、 perspective

- [x] 增加透视规则

perspective：`number`|`none`规定3D元素的透视效果(近大远小)。

> 具体多大多小，可以进行调节，调节过程中的变化规律见下面详解。

**只能加在父元素。**且不可继承。

perspective属性初体验：



（1）不在父元素中设置perspective时，此时旋转子元素如下

![mark](http://qiniu.wind-zhou.com/blog/201119/d6C3fbmJc0.gif)



（2）当在父元素中设置了perspective，再次旋转子元素。

![mark](http://qiniu.wind-zhou.com/blog/201119/3Al45eBA15.gif)



> ### perspective详解：
>
> `perspective` 属性指定了**观察者与z=0平面**的距离，使具有**三维位置变换的元素产生透视效果**。z>0的三维元素比正常大，而z<0时则比正常小，大小程度由该属性的值决定。（**近大远小**）
>
> - **a)** perspective属性设置镜头到元素平面的距离。所有元素都是放置在z=0的平面上。比如perspective(300px)表示，镜头距离元素表面的位置是300像素。
> - **b)** perspective-origin属性规定了镜头在平面上的位置。默认是放在元素的中心。
>
> 
>
> 贴个链接：这篇文章贼叼！
>
> # [css3系列之详解perspective](https://www.cnblogs.com/yanggeng/p/11285856.html)



 下面用一个正方体（或者说骰子）向大家演示视角不同视角（perspective 以及 ）的差别。

 镜头距离z=0平面的不同距离的效果。

 ![img](https://img-blog.csdn.net/20161028151337443?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

​    

​     镜头在z坐标固定时，x和y坐标（perspective-origin）变化时的差别。

​    ![img](https://img-blog.csdn.net/20161028151430178?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)



####3、 perspective-orgin

- [x] 改变观察角度

  perspective-orgin：x-axis  y-axis  默认值为50%  
  
  perspective-origin**属性必须定义父元素上**

**总结：perspective的意义在于设置远近点大小的比例（操作的的是Z轴），让它产生3D感，perspective-orign设置眼睛在x-y平面观察的位置。**

## 实战---用css3实现立方体

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			
			body{
			    /*想看到整个立方的近大远小效果, 就给ul的父元素添加透视*/
			    perspective: 500px;
			    
			}
			
			.container{
					width: 200px;
					height: 200px;
					margin: 200px auto;	
					transform-style: preserve-3d;
					/* perspective: 500px; */
					 position: relative;
					/*使立方体先转过一个角度，方便观察效果*/
					transform: rotateX(30deg)  rotateY(45deg);
			}
			
			img{
				
				width: 200px;
				height: 200px;
				
			}
			
			.out{
				width: 200px;
				height: 200px;
				position: absolute;
			}
			
			.front{
				transform:translateZ(100px);
			}
			
			.behind{
				transform: rotateY(180deg) translateZ(100px);
			}
			
			.top{
				transform: rotateX(90deg) translateZ(100px);

			}
			
			.bottom{
				transform: rotateX(-90deg) translateZ(100px);
			}
			
			.left{
				transform: rotateY(90deg) translateZ(100px);
				
			}
			
			.right{
				transform: rotateY(-90deg) translateZ(100px);
			}
		
		</style>
	</head>
	
	<body>
	
		<div class="container">
			<div class="out front"> <img src="http://qiniu.wind-zhou.com/blog/201119/Kf09iaIG5D.jpg?imageslim"></div>
			<div class="out behind"> <img src="http://qiniu.wind-zhou.com/blog/201119/khAL65f6gG.jpg?imageslim"></div>
			<div class="out top"> <img src="http://qiniu.wind-zhou.com/blog/201119/J1ldjge2DK.jpg?imageslim"></div>
			<div class="out bottom"> <img src="http://qiniu.wind-zhou.com/blog/201119/m0kJEj3274.jpg?imageslim"> </div>
			<div class="out left"> <img src="http://qiniu.wind-zhou.com/blog/201119/1LaikAeA4F.jpg?imageslim"></div>
			<div class="out right"> <img src="http://qiniu.wind-zhou.com/blog/201119/8LcCgil72e.jpg?imageslim"></div>
			
		</div>
		
	</body>
</html>

```

效果图：

![mark](http://qiniu.wind-zhou.com/blog/201119/cFF8Ic5e8L.gif)



遇到的问题：

- 当`perspective：500px；`放在。container里时，呈现的立方体为梯形，但写在body里后，就正常了。

- 还有这里	`transform-style: preserve-3d;`去掉与否的变化及原因。

>再粘个链接：这个链接的博主的探究过程和我一致。但并没有给出我想要的解释。
>
>https://www.jianshu.com/p/fd81da55291f






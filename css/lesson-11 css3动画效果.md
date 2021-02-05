# lesson-11 css3动画效果

主要有两种1、过渡动画2、帧动画

## 过渡动画

**transition属性**

说明：css3过渡是元素从一种样式逐渐改变为另一种样式的效果,**基本上与状态伪类的hover搭配使用**。

![mark](http://qiniu.wind-zhou.com/blog/201119/JjAg20lC3L.png?imageslim)

| 属性                                                         | 描述                                           | CSS  |
| :----------------------------------------------------------- | :--------------------------------------------- | :--- |
| [transition](https://www.runoob.com/cssref/css3-pr-transition.html) | 简写属性，用于在一个属性中设置四个过渡属性。   | 3    |
| [transition-property](https://www.runoob.com/cssref/css3-pr-transition-property.html) | 规定应用过渡的 CSS 属性的名称。**默认值：all** | 3    |
| [transition-duration](https://www.runoob.com/cssref/css3-pr-transition-duration.html) | 定义过渡效果花费的时间。默认是 0。             | 3    |
| [transition-timing-function](https://www.runoob.com/cssref/css3-pr-transition-timing-function.html) | 规定过渡效果的时间曲线。默认是 "ease"。        | 3    |
| [transition-delay](https://www.runoob.com/cssref/css3-pr-transition-delay.html) | 规定过渡效果何时开始。默认是 0。               | 3    |

- [x] 1、transition-property  规定应用过渡的css3属性

  >​	主要能实现过渡效果的是大小为数值的元素，例如width、height、颜色

- [x] 2、transition-duration  设置过渡的时间  默认为0  单位s

- [x] 3、transition-timing-function  设置过渡效果的时间曲线  默认ease

  |          值           |                             描述                             |
  | :-------------------: | :----------------------------------------------------------: |
  |        linear         |            规定以**相同速度**开始至结束的过渡效果            |
  |         ease          |      规定**慢速开始，然后变快，然后慢速**结束的过渡效果      |
  |        ease-in        |                 规定以**慢速开始**的过渡效果                 |
  |       ease-out        |                 规定以**慢速结束**的过渡效果                 |
  |      ease-in-out      |                规定以慢速开始和结束的过渡效果                |
  | cubic-bezier(n,n,n,n) | 在 cubic-bezier 函数中定义自己的值。可能的值是 0 至 1 之间的数值。 |

- [x] 4、transition-delay  延迟执行时间  （主要用来制作动画队列的效果，例如先变宽，再变高）



**练习：实现一个过渡效果**

要求：

1、 对宽高和背景颜色进行过度

2、过渡时间分别为1s,3s,2s

3、过度顺序：先宽过度、再高过度、最后颜色过度

4、速度为匀速		

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			
			div{
				width: 50px;
				height: 50px;
				background: #00FF00;
				transition-property: width,height,background-color;
				transition-duration: 1s,3s,2s;
				transition-timing-function: linear;
				transition-delay:0s,1s,4s ;
			}
			
			div:hover{
				width:300px ;
				height: 300px;
				background-color: #E2393C;
			}
		
		</style>
	</head>
	
	<body>
	
		<div >
			
		</div>
	</body>
</html>
```
![mark](http://qiniu.wind-zhou.com/blog/201119/LdBLc5FCm5.gif)



**上面几个效果也可以写在一起**

直接写在transition中 ，**顺序就按上面写**。

语法：`transition: property duration timing-function delay,property duration timing-function delay;`

**可以省略,会自动配置为默认值**

```css
transition:width 1s linear 0s, height 3s linear 1s, background-color 2s linear 4s;
```



##帧动画（animation）

**原理：**



**开发者只需要定义关键的几帧，然后其他借助css的过渡实现。**

1. 定义关键帧
2. 在指定部位谁用animation属性引入关键帧

关键帧动画

**当只有两帧时：**

@keyframes规则  

```css
@keyframes name{

	from{css样式}

	to{css样式}

}
```

**当有多帧时：**

语法规则：

```css
@keyframes name{
	0% {css样式}
        25% {css样式}   
        50% {css样式}
        75% {css样式}
        100% {css样式}
}
```

**上面百分号代表时间**。



### animation属性

| 属性                                                         | 描述                                                         | CSS  |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :--- |
| [@keyframes](https://www.runoob.com/cssref/css3-pr-animation-keyframes.html) | 规定动画。                                                   | 3    |
| [animation](https://www.runoob.com/cssref/css3-pr-animation.html) | 所有动画属性的简写属性。                                     | 3    |
| [animation-name](https://www.runoob.com/cssref/css3-pr-animation-name.html) | 规定 @keyframes 动画的名称。                                 | 3    |
| [animation-duration](https://www.runoob.com/cssref/css3-pr-animation-duration.html) | 规定动画完成一个周期所花费的秒或毫秒。默认是 0。             | 3    |
| [animation-timing-function](https://www.runoob.com/cssref/css3-pr-animation-timing-function.html) | 规定动画的速度曲线。默认是 "ease"。                          | 3    |
| [animation-fill-mode](https://www.runoob.com/cssref/css3-pr-animation-fill-mode.html) | 规定当动画不播放时（当动画完成时，或当动画有一个延迟未开始播放时），要应用到元素的样式。 | 3    |
| [animation-delay](https://www.runoob.com/cssref/css3-pr-animation-delay.html) | 规定动画何时开始。默认是 0。                                 | 3    |
| [animation-iteration-count](https://www.runoob.com/cssref/css3-pr-animation-iteration-count.html) | c规定动画被播放的次数。默认是 1。                            | 3    |
| [animation-direction](https://www.runoob.com/cssref/css3-pr-animation-direction.html) | 规定动画是否在下一周期逆向地播放。默认是 "normal"。          | 3    |
| [animation-play-state](https://www.runoob.com/cssref/css3-pr-animation-play-state.html) | 规定动画是否正在运行或暂停。默认是 "running"。               | 3    |

![mark](http://qiniu.wind-zhou.com/blog/201120/dihJdAcDfc.png?imageslim)



**练习1：**

```html
<!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>css3逐帧动画</title>
        <style>
			
			.out{
				
				width: 500px;
				height: 500px;
				border: #000000 1px solid;
				margin: 200px auto;
				
			}
			
			
			.in{
				
					width: 100px;
					height: 100px;
					background-color: #00FFFF;
					
					/*animation-name:test ;
					animation-duration: 4s;
					animation-iteration-count: infinite;
					animation-timing-function: linear;
      			          animation-delay:0s;
					animation-direction: alternate;*/
                			/*上面是分开写，下面是简写*/
               			 animation: test 4s linear  0s infinite alternate;
				}
				
				
				img{
					width: 100px;
					height: 100px;
					border: #FF0000 1px solid;
				}
   
   
      	@keyframes test{
			
				0%{
					margin-top: 0px;
					margin-left: 0px;
					transform: rotateZ(0deg);
					
				}
				
				25%{
					margin-top: 0px;
					margin-left: 400px;
					background-color: #00FF00;
					transform: rotateZ(180deg);
					
			}
			
			50%{
				margin-top:400px  ;
				margin-left:400px ;
				background-color: #FC0400;
				transform: rotateZ(360deg);
			}
			
			75%{
				margin-top: 400px;
				margin-left: 0px;
				background-color: #FF0000;
				transform: rotateZ(0deg);
			}
			
			100%{
				margin-top: 0px;
				margin-left: 0px;
				
			}
		}
		
		
		
		.in:hover{
			animation-play-state: paused;
		}
  
        </style>
    </head>
    <body>
		
		<div class="out">
			<div class="in"><img src="../../img/bottom.jpg"></div>
		</div>
        
    </body>
```

![mark](http://qiniu.wind-zhou.com/blog/201120/F5hI5dDbdK.gif)



**练习2：**

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			
			body{
				background-image:linear-gradient( to left top,#f00 ,#00f) ;
				perspective:1000px;
			}
			
			.container{	
				width:300px ;
				height: 300px;
				margin: 200px auto;
				transform-style: preserve-3d;
				/*设置帧动画*/
				animation: first_ani 4s linear 0s infinite normal;
			}
			
			.face{
				
				width: 300px;
				height: 300px;
				color: white;
				font-weight: bold;
				font-size: 30px;
				line-height: 300px;
				text-align: center;
				position: absolute;	
			}
			
		
			
			.top{
				background-color: rgba(0,255,0,0.6);
				transform:rotateX(90deg) translateZ(150px) ;
				
			}
			
			.bottom{
				background-color: rgba(222,2,0,0.6);
				transform: rotateX(-90deg) translateZ(150px);
			}
			
			.left{
				background-color: rgba(100,100,100,0.6);
				transform: rotateY(90deg) translateZ(150px);
			}
			.right{
				background-color: rgba(1,205,0,0.6);
				transform: rotateY(-90deg) translateZ(150px);
			}
			.front{
				background-color: rgba(0,25,250,0.6);
				transform: translateZ(150px);
			}
			.behind{
				background-color: rgba(90,150,10,0.6);
				transform: rotateX(180deg) translateZ(150px);
			}
			
			
			@keyframes first_ani{
			from{
				transform: rotateX(0deg) rotateY(0deg)  rotateZ(0deg);
			}
			to{
				transform: rotateX(360deg) rotateY(360deg)  rotateZ(360deg);
			}
				}
		</style>
	</head>
	<body>
		
		<div class="container">
	
			<div class="face front">前面</div>
			<div class="face behind">后面</div>
			<div class="face top">上面</div>
			<div class="face bottom">下面</div>
			<div class="face left">左面</div>
			<div class="face right">右面</div>
		</div>
	</body>
</html>

```



![mark](http://qiniu.wind-zhou.com/blog/201120/8e9B3cJ0cK.gif)









 
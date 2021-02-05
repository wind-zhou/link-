# lesson-5 超链接

##几种超链接特效设置

1. 去除超链接下划线
   text-decoration：none；
2. 动态超链接
   要使用伪类选择器来创建动态超链接
   - a:link    鼠标点击前的样式，
   - a:visited  点击之后的超链接样式
   - **a:hover   鼠标滑到超链接上时的样式**
   - a:active   点击超链接时的样式

书写顺序：a:link--->a:visited--->a:hover--->a:active否则样式显示可能会出现错误。

##实战：做个按钮

**实战练习：**

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		
		<style>
			
			a:link,a:visited{

				font-weight: bold;
				text-decoration: none;
				background-color: #00FFFF;
				border-right: #0000FF 3px  solid;
				border-bottom: #0000FF 3px  solid;
				border-top: #000 3px  solid;
				border-left: #000 3px  solid;
				padding-right: 30px;
				padding-left: 30px;
				
			}
		
			a:hover{
				background-color: #00FF00;
				border-right: #000 3px  double;
				border-bottom: #000 3px  double;
				border-top: #FF0000 3px  solid;
				border-left: #FF0000 3px  solid;
				padding-right: 40px;
				padding-left: 20px;
				
			}
			
		</style>
	</head>
	<body>
		
		<a href="https://www.baidu.com">我的首页</a>
		
		<a href="https://www.baidu.com">个人中心</a>
		
		<a href="https://www.baidu.com">联系我们</a>
		
	</body>
</html>

```

![mark](http://qiniu.wind-zhou.com/blog/201113/fKI9aciJ3A.png?imageslim)

总结：

- 设计时按钮常常**通过划入前后边框颜色的变化来呈现一种点击的效果。**

- 上面按钮在点击时按钮文字会有些许移动，这通过设置padding来实现。

  >注意：为了保证点击划入时按钮的大小不发生变化，需要令前后的上下（左右）padding值之和相等。
  >
  >但由于行内标记设置padding值，但内容不动，所以呈现的效果是边框的位置发生了移动，这是设置一下
  >
  >`float：left；`即可。
  >
  >当然本例中没有设置上下的padding，因此没有这种情况。**（貌似是上下的padding影响，左右的padding不影响，不知道什么情况）**
  >



**鼠标特效：**

cursor属性是什么：指鼠标指针放在**一个元素边界范围内时所呈现的光标形状**，它包括问号，小手等形状。****

例如：鼠标划上去时变成小手

```css
div{
    cursor:pointer;
}
```



cursor页可以设置不同的形状：

| 值          | 描述                                                         |
| :---------- | :----------------------------------------------------------- |
| *url*       | 需使用的自定义光标的 URL。注释：请在此列表的末端始终定义一种普通的光标，以防没有由 URL 定义的可用光标。 |
| default     | 默认光标（通常是一个箭头）                                   |
| auto        | 默认。浏览器设置的光标。                                     |
| crosshair   | 光标呈现为十字线。                                           |
| **pointer** | 光标呈现为指示链接的指针（一只手） **用的最多**              |
| move        | 此光标指示某对象可被移动。                                   |
| e-resize    | 此光标指示矩形框的边缘可被向右（东）移动。                   |
| ne-resize   | 此光标指示矩形框的边缘可被向上及向右移动（北/东）。          |
| nw-resize   | 此光标指示矩形框的边缘可被向上及向左移动（北/西）。          |
| n-resize    | 此光标指示矩形框的边缘可被向上（北）移动。                   |
| se-resize   | 此光标指示矩形框的边缘可被向下及向右移动（南/东）。          |
| sw-resize   | 此光标指示矩形框的边缘可被向下及向左移动（南/西）。          |
| s-resize    | 此光标指示矩形框的边缘可被向下移动（南）。                   |
| w-resize    | 此光标指示矩形框的边缘可被向左移动（西）。                   |
| text        | 此光标指示文本。                                             |
| wait        | 此光标指示程序正忙（通常是一只表或沙漏）。                   |
| help        | 此光标指示可用的帮助（通常是一个问号或一个气球）。           |




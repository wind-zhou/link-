# lesson -10 框架

## 简介

**将浏览器分隔成多个小窗口，每个小窗口可以显示不同的网页。**（类似手机的分屏和一些论坛邮箱等，邮箱就是典型的厂字型结构，可以实现不同页面的任意切换。）

## 基本结构

### 基本语法

框架主要分为**框架**和**框架集**两部分，分别用frame和frameset标记。

**框架使用时没有body。，不能放在body里**

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<frameset>
		<frame />
		<frame />
	</frameset>
</html>
```





##框架的设置

**包括：**

- 水平分割（rows）
- 垂直分割(cols)
- 嵌套分割

### 水平分割

基本语法：

```html
<frameset rows="高度1,高度2,...,*">
   	 <frame src="url"> 
	<frame src="url">
   		...
</frameset>
```

**例：**

源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<frameset rows="100,200,*">
		<frame />
		<frame />
		<frame />
	</frameset>
</html>
```

效果图：

<img src="http://qiniu.wind-zhou.com/blog/201105/JbD53Ci89f.png?imageslim" alt="mark" style="zoom: 33%;" />

**注：rows的数值设置可以有两种方式**

1. 数值方式
2. 百分比方式

### 垂直分割

基本语法：

```html
<frameset cols="宽度1,宽度2,...,*">
   	 <frame src="url"> 
	<frame src="url">
   		...
</frameset>
```

所有用法和水平分割相同。

### 嵌套分割

利用框架的嵌套可以实现网页的布局，例如常见的厂字型结构。

直接上代码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<frameset rows="30%,*">
		<frame />
		<frameset cols="50%,*">
			<frame />
			<frame />
		</frameset>
	</frameset>
</html>
```

效果图：

![mark](http://qiniu.wind-zhou.com/blog/201105/33lFF7Icdh.png?imageslim)

### 窗口的边框

frameset里可利用border来控制边框。

**就是控制框架集中的分割线粗细，写在哪个frameset中控制哪条分割线。**

基本语法：

`<frameset border="">`

源码：

```html
<frameset rows="30%,*" >
		<frame />
		<frameset cols="50%,*" border="2">
			<frame />
			<frame />
		</frameset>
	</frameset>
```

效果图：

![mark](http://qiniu.wind-zhou.com/blog/201105/EeLgGabE8I.png?imageslim)

## 子窗口的设置

### 指定子窗口显示网页

基本语法：

```html
<frame src="url">
```

**例：**

源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<frameset rows="30%,*" >
		<frame  src="https://www.sogou.com/"/>
		<frameset cols="50%,*" border="2">
			<frame src="https://www.baidu.com/"/>
			<frame src="https://www.360.com/"/>
		</frameset>
	</frameset>
</html>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201105/82367A1j61.png?imageslim)

>注：这里的frame的url可以指向任何资源，图片，文本，音频，视频等。

### 空中子窗口的滚动条

scrolling来控制串口是否设置滚动条。

基本语法：

```html
<frame scrolling="yes|no|auto">
```

例：

源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<frameset rows="30%,*" >
		<frame  src="https://www.sogou.com/" scrolling="on"/>
		<frameset cols="50%,*" border="2" >
			<frame src="test-2.html" / scrolling="yes">
			<frame src="https://www.baidu.com/" scrolling="auto"/>
			
		</frameset>
	</frameset>
</html>
```

效果图

![mark](http://qiniu.wind-zhou.com/blog/201105/049188b8JA.png?imageslim)

### 调整窗口的大小

默认为分割后可以自由控制窗口大小，在frame标记内设置noresize后便可将其固定。

**例：**

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<frameset rows="30%,*" >
		<frame  src="https://www.sogou.com/" scrolling="no"/>
		<frameset cols="50%,*" border="2" >
			<frame src="selfpic.jpg"/ scrolling="yes" noresize="noresize">
			<frame src="https://www.baidu.com/" scrolling="auto"/>
			
		</frameset>
	</frameset>
</html>

```

效果图：

![mark](http://qiniu.wind-zhou.com/blog/201105/i46EF5HK4L.png?imageslim)

>注：上面代码中noresize写在了嵌套的框架集中的一个frame中，所以此时他的两个边框都不能移动，若只写成下面这样
>
>```html
><!DOCTYPE html>
><html>
>	<head>
>		<meta charset="utf-8">
>		<title></title>
>	</head>
>	<frameset rows="30%,*" >
>		<frame  src="https://www.sogou.com/" scrolling="no" noresize="noresize"/>
>		<frameset cols="50%,*" border="2" >
>			<frame src="selfpic.jpg"/ scrolling="yes" >
>			<frame src="https://www.baidu.com/" scrolling="auto"/>
>			
>		</frameset>
>	</frameset>
></html>
>注意这次noresize的位置。
>```
>
>![mark](http://qiniu.wind-zhou.com/blog/201105/Ee5gjAGG67.png?imageslim)

**重点：**如何在框架中实现在一个子窗口点击链接，在另一个窗口显示页面。

大概可以分为两步

1. 在要显示链接的子窗口的frame中通过`name=“设置的名称”`打一个锚点
2. 在需要点击的链接处a标记内加上`target="设置的名称"`

实战练习：

main文件源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<frameset rows="300,*" border="2">
		<frame src="https://www.baidu.com" />
		<frameset cols="500,*">
			<frame  src="111/test2.html" />
			<frame  name="hello" />
		</frameset>
	</frameset>
</html>
```

其中test2.html 源码：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<a href="https://www.baidu.com" target="hello"> 点我跳转百度</a>
	</body>
</html>
```

此时界面：

![mark](http://qiniu.wind-zhou.com/blog/201105/kKD3bJiba8.png?imageslim)

点击后：

![mark](http://qiniu.wind-zhou.com/blog/201105/CfEADGgg7f.png?imageslim)

## 浮动框架

小窗口浮动在大窗口上。

基本语法：

```html
<iframe src="url">
    
</iframe>
```

说明：iframe可以写在body中。

**主要作用：跨域传值。（在不同网站之间进行传输数据）**

**主要属性：**

![mark](http://qiniu.wind-zhou.com/blog/201105/9K618m97b7.png?imageslim)

练习：

源码：

```html
<iframe src="https://www.baidu.com" width="300px" height="200px" scrolling="auto"></iframe>
```

![mark](http://qiniu.wind-zhou.com/blog/201105/hh4kJH8G3K.png?imageslim)


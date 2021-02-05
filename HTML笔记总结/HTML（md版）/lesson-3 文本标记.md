# lesson-3 文本标记

## **文字内容**

### **添加文字**

直接在body标签里写即可。

### **标题字**

语法：

```html
<h1 align="left|right|center">标题文字</h1>
```

一共有六级，**默认全部加粗**。最小标题字号尾12px，向上依次增加2px。

align用来水平对齐方式（默认为left）。还有一个justify两端对齐，现在已经不用了。

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<h1>一级标题</h1>
		<h2>二级标题</h2>
		<h3>三级标题</h3>
		<h4>四级标题</h4>
		<h5>五级标题</h5>
	</body>
</html>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201106/heJgIC1HI0.png?imageslim)

标签有**块级标记**（自己占一行）和**行内标记**（有空位就会在同一行显示）。

h标签属于块标记。

###**空格**

注：两个空格的宽度为一个汉字。

**几个重要特殊字符：**

![mark](http://qiniu.wind-zhou.com/blog/201106/ch83KC4EHI.png?imageslim)

###**注释**

语法：

```html
<!--注释内容-->
```

##**文字样式**

用\<font>标记。可以设置字体字号和颜色。

基本语法：

```html
<font face="" size="" color="">...</font> 
- face 字体 
- size 大小 1-7 默认为3 --- 16像素（不是按像素来度量）
- color 颜色 支持单词和16进制的写法
```

**标记嵌套规则**：块级标记可以嵌套行内标记也可以嵌套块级标记，而行内标记只能嵌套行内标记不能嵌

套块级标记（其实是为了之后引入css时容易控制）。

eg：\<h>标记可以嵌套\<font>标记，但\<font>不能嵌套\<h>标记。

**就近原则**：嵌套时如果发生样式冲突，谁离得近谁生效。

## **文字修饰**

这组都是行内样式，且没有属性。

- 加粗

  语法：

  ```html
  <b>...</b> 或<strong>...</strong> (
  
  属于语义化标记，h5新增的) 什么事语义化？
  
  有助于提升网站对访客的易用性。 
  有助于设备对html的读取，对搜索引擎的友好的，可以让其更容易去识别到页面里的内容。
  ```

- 倾斜

  语法：

  ```html
  <i>...</i> 
  或<em>...</em>(语义化的标记)
  ```

- 下划线(underline)

  ```html
  <u>...</u>
  ```

- 删除线

  ```html
  <del>...</del>
  ```

- 上标、下标

  ```html
  <sup> ...</sup> 上标 
  <sub> ...</sub> 下标
  ```

- 地址（块级标记）

  ```html
  <address>...</address> (里面是斜体)
  ```

## **总结**

![mark](http://qiniu.wind-zhou.com/blog/201106/fDcka3a9FD.png?imageslim)




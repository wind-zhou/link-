# lesson-5列表

## 无序列表

**基本语法**

```html
<ul type=" ">
    <li>项目名称</li>
    <li>项目名称</li>
    <li>项目名称</li>
    ......
</ul>
```

注：这是个基本结构，必须嵌套使用。

**ul里面只能套li。**但li里面可以嵌套别的内容。**\<ul>和\<li>都是块级标记。**

**type属性说明**：

```html
disc------实心圆（默认）
circle------空心圆
square---小方块
```

**type属性也可以单独控制某一个\<li>**

## 有序列表

有序列表使用和无序列表使用基本相同。

**基本语法**

```html
<ol type=" " start=" ">
    <li>项目名称</li>
    <li>项目名称</li>
    <li>项目名称</li>
    ......
</ol>
```

### ol里有两个属性 type和start。

**type属性说明**：

>**type可选的值：**
>
>1   指定为阿拉伯数字
>a   指定为小写字母
>A   指定为大写字母
>i    指定为小写罗马数字
>I    指定为大写罗马数字

**start属性**：

可以修改计数的初始值。

### li里有两个属性type和value

**type：**

li里面也可以使用type，可以**改变当前这一行列表的标头计数格式**。

**value：**

可以独立控制值这一行的编号，但**会改变默认的排列**，使后面的编号从此value值依次顺承。

联系：

```html
<ol type="A" start="24"> 
    <li type="1" value="3">手机</li>
    <li>电脑</li>
    <li>电视</li>
    <li>冰箱</li>
</ol>
```

![mark](http://qiniu.wind-zhou.com/blog/201107/hdFbFic27E.png?imageslim)

###关于列表的嵌套

**li里可以嵌套其他内容。也可以嵌套列表（每次嵌套灰缩进40px）。**

举例：

```html
<ul type="square">
					<li>huawei
						<ul>
							<li>mate</li>
							<li>p</li>
							<li>honor</li>

						</ul>
					</li>
					<li>xiaomi</li>
					<li>oppo</li>
					<li>vivo</li>
				</ul>
```

![mark](http://qiniu.wind-zhou.com/blog/201107/ldCkj1J10K.png?imageslim)

## 定义列表

**基本语法**

```html
	<dl>
		<dt>手机品牌</dt>
		<dd>华为</dd>
		<dd>小米</dd>
		<dd>oppo</dd>
        
		<dt>电脑</dt>
		<dd>华为</dd>
		<dd>联想</dd>
		<dd>华硕</dd>	
	</dl>
```

列表里没有前面编码，**适用于一些不需要有编码的列表**

**类似于二级列表嵌套**
**会缩进两个半字符**
**即使没有\<dt>也会缩进**






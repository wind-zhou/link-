# lesson-8  表格

## 表格标记

表格现在在网站中大概两个作用：**罗列数据**和**网页布局**。

表格由三对标记构成：\<table>、\<tr>(行)、\<td>（行里的单元格）,逐级嵌套。

基本语法：

```html
<table >
	<tr>
		<td>1</td>
		<td>2</td>
		<td>3</td>
	</tr>
	<tr>
		<td>4</td>
		<td>5</td>
		<td>6</td>
	</tr>
	<tr>
		<td>7</td>
		<td>8</td>
		<td>9</td>
	</tr>
</table>
```

属性说明：

### **table表的属性**

| 属性        | 值                                                           |
| ----------- | ------------------------------------------------------------ |
| border      | 边框（默认为0）                                              |
| bordercolor | 设置边框颜色（**如果不设置，边框会有暗边和亮边**）           |
| width       | 宽度（单位是px或%）                                          |
| height      | 高度（注：高度一般不用百分数，因为百分比<br />填充是填充的父元素块，这里是body，但body<br />的高度由内容填充决定，因此会产生不确定性。） |
| bgcolor     | 设置单元格背景颜色                                           |
| background  | 设置表格背景图片（注：图片大小仅用HTML无法设置<br />1. 如果图片比表格大：会按表格大小截取相应大小部分<br />2. 如果图片比表格小：图片会重复，以达到表格大小<br />注：如果此时还设置了**bgcolor，则颜色会被覆盖在下方**） |
| cellspacing | 设置单元格距离（一般设为0）                                  |
| cellpadding | 设置单元格内边距（内容和边框的距离，默认的为0）              |
| align       | 设置表格水平对齐方式                                         |

### **设置行的属性**

| 属性    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| align   | （left\|center\|right）设施表格里内容**水平对齐方式**（默认为left） |
| valign  | （top\|bottom\|middle）设施表格里内容**垂直对齐方式**（默认为middle） |
| bgcolor | 控制一行的颜色                                               |
| height  | 一行的高度（设置宽没意义）                                   |

### **设置列的属性**

| 属性       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| align      | 设施表格里内容**水平对齐方式**                               |
| valign     | 设施表格里内容**垂直对齐方式**                               |
| bgcolor    | 设置单元格背景色                                             |
| background | 给某一个单元格设置图片背景                                   |
| width      | 设置单元格宽，并会改变这一行所有单元格宽度。<br />如果同一列的两个单元格width设置了不同的值，<br />则具体宽度会按最宽的一致，高度也是同理。 |
|            | 同上                                                         |
| rowspan    | 单元格跨行（就是合并单元格）                                 |
| colspan    | 单元格跨列                                                   |

**示例：**

```html
<table border="1" bordercolor="red" width="600" height="300" bgcolor="#00ff09" cellspacing="0" cellpadding="10" align="center">
	<tr >
		<td colspan="2">1</td>
		<!-- <td>2</td> 因为要跨列合并，所以这一个单元格要删除-->
		<td>3</td>
	</tr>
	<tr>
		<td rowspan="2">4 </td>
		<td>5</td>
		<td>6</td>
	</tr>
	<tr>
             <!-- <td>7</td>   因为要跨行合并，所以这一个单元格要删除-->
		<td>8</td>
		<td>9</td>
	</tr>

</table>
```

**效果：**

开始时：

![开始](http://qiniu.wind-zhou.com/blog/201030/95LakdkaG7.png?imageslim)

处理后：

![mark](http://qiniu.wind-zhou.com/blog/201030/8EfkbmDadC.png?imageslim)

**注： 进行跨行合并时，只能从上往下跨，进行跨列合并时，只能从左往右跨。**

###补充

># html 表格单元格的宽度和高度的设置方法
>
>做网页的时候，经常会碰到表格宽度对不齐的问题。详细地看了html中表格标签table的高度和宽度设置的细节，现总结如下：
>
>​    1、**table中的width和height设置及其作用**：table中设置的height其实是设置个<font color="red">最小值</font>，也就是当表格中的内容或者行高总值超过这个设置值时，会自动延长表格的height值，当表格中的内容或者行高没有达到这个值时，会自动扩大到这个值。table中设置的width值一般为表格宽度的最大值，不能改变，即使内部的内容宽度超过也不能改变。（**这个内部内容如果是图片的话是可以改变表格宽度的**。）
>
>   2、**tr标签中width和height设置及其作用**：<font color="red">tr标签里面的width设置不起任何作用</font>，因为从第一点可以看出，表格的width是不能改变的，tr标签当然就不起作用了。所以在tr中只有讨论height设置的可能了，tr中的height设置和几个tr之间的设置有关。**当几个tr都设置了height的具体数值时，各个tr的height按照设置的值的比例来分配总的height值，注意这里说的是总的height值。**当几个tr都没有设置height具体值时，平均分配总的height值。当有的tr设置了具体的数值，有的没有设置具体的数值为默认时，**先保证各个tr的基本需要，剩下的再满足设置了具体值的tr，之后再全部给没有设置具体值的tr**。最后一种情况还要考虑总的宽度不够tr总的设置值的情况，不够的话要满足tr的基本需要，这里会自动延长表格的height的。然后再考虑设置了heightr的tr，最后考虑没有设置height的tr。
>
>>简单总结：当某个tr的height的高度较小时，剩余几个tr平分table的高度，但当某个tr（设其为x）高度增加时，会挤压其他tr的height，其他单元格平分剩下的height，但当继续压缩，到达一个临界值，就是达到了某个有内容的tr的最小高度，由于有内容撑着，这时他的height不会被继续压缩，此后就是能压缩谁就压缩谁（没内容填充的倒霉鬼肯定首当其冲），当x的height继续增加达到table的总height时，之后x若再增大则会扩展table的height以满足需要求。
>
>   3、**td标签中width和height设置及其作用**：td标签里面的width和height都是起作用的。先看td的width吧，某一个td的width是和所处的一列每个td的width都相关的，取其中最大的width作为这一列中每个td的width，这点是让我们最混淆的地方，一定要从全局把握某个td的width，不能从这一个的width设置就断言它的宽度就是多少，这样是不准确的。当我们把每一列的宽度都弄清楚之后，事情就好办了。这时候各个td之间的宽度分配按照第二条中各 tr的height分配规律，有一点不同的是全部是默认的情况下，各td的width不是平均分配，而是根据各自的实际内容按比例分配。再看看td的height设置吧，这个相对简单一点了，不过各个td的height要看这个td所在的行的最大高度来确定这一行的每个td的height，然后各个行的高度情况和tr中的height分配原则是一样的。还有一点要注意，就是td的height和tr的height之间的关系。首先肯定是根据内容的需 要，在这个基础上，再根据设置的值来确定，哪个设置的值大就按照哪个，如果一个设置了值一个没有设置值，那么按照设置值的算。



>1,使用传统的方法
>
>
>```html
><table width="400"> 
><tr> 
><td width="100"></td> 
><td width="100"></td> 
><td width="100"></td> 
><td width="100"></td> 
></tr> 
><table> 
>```
>
>2,使用css
>
>
>```css
><style>
>.td{width:100px;}
></style>
><table width="400"> 
><tr> 
><td class="td"></td> 
><td class="td"></td> 
><td class="td"></td> 
><td class="td"></td> 
></tr> 
><table>
>```
>
>以上两种方法可能出现的问题就是,如果内容超过设定,如图片宽度大于100,会自然撑开,自动调节表格宽度
>
>3,用css
>
>```css
><style>
>.td{width:100px;overflow:hidden}
></style>
><table width="400"> 
><tr> 
><td class="td"></td> 
><td class="td"></td> 
><td class="td"></td> 
><td class="td"></td> 
></tr> 
><table>
>```
>
>用这种方法,可以把超过的部分隐藏掉,如果需要严格控制的话,可以采用这种方法,如果把overflow的属性值设置成scroll或者auto的话,可以采用这种方法,如果把overflow的属性值设置成scroll或者auto的话,可以在超过的时候使用滚动条调节....
>
>转载自：[html 表格单元格的宽度和高度的设置方法](https://www.jb51.net/web/630671.html)
>
># html中table表格td中英文不换行问题
>
>在html中给table设置一个，当某个td中的字符串是英文并且相当长时它不会换行会将其他列的内容挤出去，无法正常显示，我们需要添加
>
>```css
>table{
>
>word-break:break-all; 
>word-wrap:break-word
>
>}
>```
>
>
>
>## 语法
>
>```html
>word-break: normal|break-all|keep-all;
>```
>
>| 值        | 描述                           |
>| :-------- | :----------------------------- |
>| normal    | 使用浏览器默认的换行规则。     |
>| break-all | 允许在单词内换行。             |
>| keep-all  | 只能在半角空格或连字符处换行。 |
>
>英文则会自动换
>
>## [css中word-break、word-wrap和white-space的区别](https://www.cnblogs.com/bydzhangxiaowei/p/10444840.html)
>
>**white-space**主要用来设置CJK文本是否不折行，实际中主要用white-space:nowrap来让文本不折行。
>
>**word-wrap**主要用来设置非CJK文本是否折行（因为CJK文本会自动折行），如果空间足够，不会对单词内部进行截断
>
>**word-break**同样主要用来设置非CJK文本是否折行，但是会对单词内部进行截断





## 表格标题

作用：对表格进行简单说明。

基本语法：

```html
<caption> 标题</caption>
```

## 表格表头

表格的第一行（或第一列）用于替换td，里面的文字默认的样式是：水平居中；垂直居中；加粗。

## 其他元素

- `<thead></thead>`
- `<tbody></tbody>`
- `<tfoot></tfoot>`

## 表格嵌套

在td里嵌套新的table。

用表格做布局时可能会用到嵌套。

**注：表格嵌套越多结构越复杂，会拖慢网页加载速度，并且对网页后期维护不友好。**

>浏览器读取html时，从一个标记开始，但读内容时并不会对标记里的内容进行渲染，只有等读完整个标记时才会显示，因此多层表格嵌套会拖慢加载速度。
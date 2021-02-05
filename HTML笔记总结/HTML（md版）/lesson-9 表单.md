#lesson-9 表单

##简介

 **用于给用户填写信息，从而使网页具有交互功能。**

里面主要有三张标记：input，select，textarea

**基本语法：**

```html
<form name="" action=" " method="">
    <input>
    <select>
       ...
    </select>
    <textarea>....</textarea>
</form>
```

## form 表单属性

`<form name="" action=" " method="">`

- name 表单名称，用于服务器接收数据时识别表单。（必写）

- action 指里面写的是url链接，就是表单提交的地址（该属性如果被省略，则默认为当前页面地址）

- method 用于指定表单向服务器提交数据的方式。有Get和post两种方法。

  >GET和POST方法的区别：
  >
  >- 使用GET方法是，数据浏览器会将各个值添加到action属性指定的url后面。通过地址栏传值，数据会用？连接，多个值之间用&连接。
  >
  >  **但是GET传值有两个缺点：**
  >
  >  1. 地址栏允许输入url长度有限（最大2048个字符）
  >  2. 明文传输，不安全
  >
  >- post方式
  >
  >  post通过HTTP的post机制，将表单内容放到http的报文body里提交给action。
  >
  >  **post传输数据量较大，一般默认不受限制。**

## input

**单标记，行内标记，放在form里使用。**

- type

  1. **text 单行文本输入框**
     `<input name="" type="text"  name=" value="">`
     - 搭配**size**来控制对话框的长度（但是不太准确，页不常用）
     - 搭配**maxlength**来限定文本框最大长度
     
     - 搭配**value**可以设置默认值
     
  2. **password 用来输入密码**（用法与text一样，不过输入框内内容不可见）
  
  3. checkbox 复选框**
     `<input name="" type="checkbox" value="">说明文字`
     - checked 用于指定默认被选中
  
  **问题：checkbox中的值必须设置成一样的吗？  **
  
  ***一般都会设置成一样。***

5. **radio   单选框**
   `  <input type="radio" name="sex" value="man"  />男`  
   ` <input type="radio" name="sex" value="woman"  />女`  
    注：要实现单选，name要设置成一样。也可加配合checked实现默认选择。

6. **file 文档选择输入框**

```html
 <form action=" " method="post" enctype="multipart/form-data">
     <input type="file" name="file" > 
</form>
注：如果上传文件，method应改为post,后面的编码方式enctype页要设置一下
```

>补充：enctype中几个参数的含义：
>
>[post使用form-data和x-www-form-urlencoded的本质区别](https://blog.csdn.net/u013827143/article/details/86222486?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.compare)
>
>># Form enctype参数说明
>>
>>在Form元素的语法中，**EncType表明提交数据的格式** 用 Enctype 属性指定将数据回发到服务器时浏览器使用的编码类型。 下边是说明： application/x-www-form-urlencoded： 窗体数据被编码为名称/值对。这是标准的编码格式。 multipart/form-data： 窗体数据被编码为一条消息，页上的每个控件对应消息中的一个部分。 text/plain： 窗体数据以纯文本形式进行编码，其中不含任何控件或格式字符。  补充 form的enctype属性为编码方式，常用有两种：application/x-www-form-urlencoded和multipart/form-data，默认为application/x-www-form-urlencoded。 当action为get时候，浏览器用x-www-form-urlencoded的编码方式把form数据转换成一个字串（name1=value1&name2=value2...），然后把这个字串append到url后面，用?分割，加载这个新的url。 当action为post时候，浏览器把form数据封装到http body中，然后发送到server。 如果没有type=file的控件，用默认的application/x-www-form-urlencoded就可以了。 但是如果有type=file的话，就要用到multipart/form-data了。浏览器会把整个表单以控件为单位分割，并为每个部分加上Content-Disposition(form-data或者file),Content-Type(默认为text/plain),name(控件name)等信息，并加上分割符(boundary)。
>
>问题：get和urlencode，**get和form-data？ （不能这么搭配），**post和urlencode，post和form-data

  6. **hidden(隐藏域)**

`<input type="hidden" value="123456" name="zhouzheng">` 
  用于向后台传输一些必要的数据，但是不需要用户知道和修改（例如购物时商品的id）

  7. **submit（提交按钮）**
     `<input type="submit"  value="注册">"`
     这里name可以不写
  
  8. **img 图片按钮**
     `<input src="url" type="image">`
  
  9. **reset 重置按钮**
  
     `<input type="reset" value="重置">`

## 练习

**源码：**



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>hello HTML</title>
	</head>
            <body>
                <form name="login" action=" check/login.go" method="post" enctype="multipart/form-data">
                    <label>用户名：</label><input type="text" maxlength="3" name="zhou" value="admin" /><br />
                    <label>密码：</label><input type="password" name="pwd" maxlength="6" />	  <br />
                    <label>课程</label>
                    <input type="checkbox"  name="html" value="html">HTML
                    <input type="checkbox"  name="css" value="css">CSS
                    <input type="checkbox"  name="JavaScript" value="js" checked="checked">JavaScript<br/>
                    <label>性别：</label>
                    <input type="radio" name="sex" value="man" checked="checked" />男
                    <input type="radio" name="sex" value="woman"  />女<br/>
                    <label>头像</label>
                    <input type="file" name="file"/><br />
                    <input type="image" src="../selfpic.jpg"><br />
                    <input type="submit" value="注册" ><br />
                    <input type="reset" value="重置">
                </form>
       </body>
</html>

```



**效果图：**

![mark](http://qiniu.wind-zhou.com/blog/201101/7lhKk4aJK1.png?imageslim)

## textarea

和input同级，但属于**多行文本输入框**。

**行内，双标记。**

```html
<textarea  name="" rows="" cols="" color=""></textarea>

-- rows 指定最多显示几行，超出会出现滚动条
-- wrap 是否换行
```

注：**textarea也可以设置默认值，但不用value属性，直接写在两个标记中间即可。**

尽在html中文本框大小可以拖动，后面可以用css控制住。

## select

兼具块级元素（可以设置宽高）和行内元素（不单独一行）的特点

**下拉列表框**

基本语法：

```html
<form>
    <select name="city"  size="">
        	<option value="" selected>   值     //可以写成单标记，也可以搞成双标记
                <option value="" >值
    </select>
</form>
```

option是下拉列表的选择项。

selected代表该项默认被选中。

```html
城市：<select name="city" size="1">
                <option value="beijing">北京</option>
                <option value="tianjin " selected="selected">天津</option>
                <option value="qinhuangdao">秦皇岛</option>
	   </select><br />
```

## readonly与disabled

readonly--只读

disabled--禁用

**两者异同：**

- 两者使用后用于都有无法对内容进行操作
- readonly中的数据可以被提交到服务器，但disabled的内容无法被上传。

## HTML5新增的内容

### H5表单元素

#### label标签

># label标签介绍
>
>label标签为input元素定义标注(标记)，它不会向用户呈现任何特殊效果，和span标签类似。但label标签和span标签最大的区别就是它为鼠标用户改进了可用性，**可以关联特定的表单控件**。
>
>label标签和特定表单控件关联之后，如果用户在 label 元素内点击文本，就会触发关联的表单控件。就是说，**当用户选择该label标签时，浏览器就会自动将焦点转到和label标签相关的表单控件上**
>
># 主要使用场景
>
>**label标签常用于与checkbox或radio关联**，以实现点击文字也能选中/取消checkbox或radio。如下图，点击文字和点击前面的单选框效果相同，**即加大了控件的可点击区域较大**，因为点击标签或控件都将激活控件，这对于复选框和单选框特别有用。
>
>详细介绍请参考：
>
>https://blog.csdn.net/gnail_oug/article/details/72852150

**使用方法 有两种：**

1. 直接将整个包裹起来
   `<label><input name="sex" type="radio" value="woman"  checked="checked"/>女</label>`
2. 用label包裹单选框的后面内容，在用id将他们联系起来。
   `<input name="sex" type="radio" value="man"  id="one"/><label for="one">男</label>`

####button

按钮

```html
<button type="button|submit|reset">
    "按钮上的文字"
</button>
```

**注：默认为submit**，button是一个普通的按钮，后期用于实现控制，可控性更强。

#### optgroup

```html
女朋友：<select name="girlfriend">
						<option disabled selected="selected">--请选择你的女朋友--</option>
						<optgroup label="china">
							<option value="LYF">刘亦菲</option>
							<option value="DYRB">迪丽热巴</option>
							<option value="YCY">杨超越</option>
						</optgroup>
						
						<optgroup label="overseas">
							<option value="LISA">LISA</option>
							<option value="JENIE">jeenie</option>
							<option value="rose">rose</option>
    					</optgroup>
					</select>
					<br />
```

**用于select里，用于给select里的标记分组。**

####  datalist

作用：用于搜索时，搜索框弹出相近词条便于用户搜索。

**搭配input使用。**

在生产中（例如百度搜索），datalist里的option选项是由后台程序自动生成呢。（后台程序会根据input里提交的信息去后台db进行索引，然后导出相应数据用于生成option。）

```html
<input type="text" name="search"  list="curriculum"/>
        <datalist id="curriculum">
            <option value="html教程"></option>
            <option value="html从入门到精通"></option>
            <option value="三个月精通js"></option>
            <option value="剑指offor"></option>
            <option value="js课程"></option>
        </datalist>
```

**给文本框提供预选择项。**

### H5表单属性

（现在用的不是很多，先了解下即可）

这几个属性**用在提交按钮上**，用于替换form里面的相应属性。

| 属性           | 作用                                                         |
| -------------- | ------------------------------------------------------------ |
| formaction     | formaction=“url”该属性会覆盖form中的action属性               |
| formenctype    | formenctype=“multipart/form-data”该属性会覆盖form中的enctype属性 |
| formmethod     | formmethod=“post\|get”该属性会覆盖form中的method属性         |
| formnovalidate | 该属性与type=“submit”一起使用，用于覆盖form中的novalidate，关闭H5的表单验证功能 |
| formtarget     | formtarget=“_self\|\_blank”该属性会覆盖form里的target属性    |

autocomplete =“off|on”**默认为on**。设置是否让浏览器记录之前输入的值，**加载form里所有的input都会记录，也可以单独给某个input加。**

novalidate **关掉表单的自动验证功能**。写在form里。但是现在在开发中经常关掉，自己用js来写验证。因为在不同的浏览器中有不同部分的错误反馈，不利于控制。

#### input标记新增属性

input标记新增属性

| autofocus       | 自动获得焦点                                                 |
| --------------- | ------------------------------------------------------------ |
| **placeholder** | 提供可描述的 输入字符预期值提示信息。**写在input标签里。**<br />`<input  type="text" name="search" placeholder="请输入内容"/>` |
| **required**    | 用于**验证表单项是否为空**，加该属性代表不能为空<br />       |
| form            | 用于将form表单外部的input和某个form关联，一起提交（在开发时可能会有input放在外面的场景）。<br />`<input type="text" name="content" form="hello"/>`(需要在要关联的表单内打上id) |
| multiple        | 允许用户输入多个值，例如邮箱里写多个邮箱地址（中间用“，”隔开）；同时上传多个文件等 |
| pattern         | 使用方法pattern="正则表达式"                                 |

### H5新增的input类型

| color          | 用于选取颜色                                                 |
| -------------- | ------------------------------------------------------------ |
| data           | 用户点击时会弹出一个日期选择框   **（用最多）*****年月日***  |
| datatime       | 允许用户选择一个时间和日期（**utc时间**，**大部分PC浏览器不支持**） |
| datatime-local | 允许用户选择一个时间和日期（不包含时区）。(**获取本地时间**  chrome支持，firefox不支持) <br />***年月日时分*** |
| month          | 允许用户选择一个年份和月份   **年月**                        |
| time           | 允许选择一个时间   ***周***                                  |
| week           | 选择年和第几周                                               |
| **email**      | 用于输入email地址，**提交表但时会验证**（填的不是邮箱格式则无法通过） |
| tel            | 定义一个号码输入框。与普通文本框一样，**没有自动验证**（需要自己 验证） |
| number         | 用于输入数字，**可以设置最大最小属性**（min和max）           |

| range  | 显示一个滑块，进行选择（用于不太精确的地方）属性<br />:min,max,value（当前的值）,step(步长，默认为1) |
| ------ | ------------------------------------------------------------ |
| search | 搜索域，与text显示一样（**唯一区别就是进行了语义化**）       |
| url    | 输入url地址，提交表单时会验证（**必须是绝对路径**）          |

**这一组在IE中都不支持。**

###练习

源码：

```html
                        日期：<input  type="date" name="date"/><br />
                        日期时间：<input  type="datetime-local" name="datetime"/><br />
                        年月：<input  type="month" name="dmonth"/><br />
                        时间：<input  type="time" name="time"/><br />
                        周：<input  type="week" name="week"/><br />

                        邮箱：<input type="email"  name="name" autofocus="autofocus" required multiple ><br />
                        手机号：<input type="tel"  name="tel" ><br />
                        数字：<input type="number"  name="num" min="100" max="1000"><br />
                        range：<input type="range"  name="num" min="10" max="100" step="2" value="20"><br />
                        search：<input type="search"  name="search"><br />
                        url：<input type="url"  name="url"><br />
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201103/ijcDHL4D02.png?imageslim)




# jQuery选择器

##jquery选择器

#### 基本选择器

#### 层次关系选择器

##### 过滤选择器

相当于css里的伪类选择器

- 基本过滤器（自身筛选 ）
- 子元素过滤器（找儿子）
- 内容过滤器（用的比较少）
- 可见性过滤器
- 属性选择器
- 表单选择器（不常用）

###一、什么是jQuery选择器
jQuery选择器继承了CSS与Path语言的部分语法，允许通过标签名、属性名或内容对DOM元素进行快速、准确的选择，而不必担心浏览器的兼容性，通过jQuery选择器对页面元素的精准定位，才能完成元素属性和行为的处理。

###二、jQuery选择器的优势

-  代码更简单；
-  支持CSS1到CSS3选择器；
-  完善的机制处理

###三、jQuery选择器

jQuery选择器分类示意图：
![jQuery选择器分类示意图](https://img-blog.csdnimg.cn/20190221233918488.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzY3NTQ0Nw==,size_16,color_FFFFFF,t_70)

#### 1.基本选择器

jQuery选择器中使用最多的选择器，它由元素id、class、元素名、多个元素符组成。
功能表如下：
![基本选择器](https://img-blog.csdnimg.cn/20190221234300822.jpg)
例1：CSS样式：`<button id="btn" class="btn1">按钮</button>`
使用如下：

```js
console.log($("#btn"));
console.log($(".btn1"));
console.log($("*"));
console.log($("button"));
console.log($("#btn,.btn1,button"));

```

####2.层次选择器
通过DOM元素间的层次关系来获取元素，主要层次关系包括**父子、后代、相邻、兄弟**关系。
功能表如下：
![层次选择器](https://img-blog.csdnimg.cn/2019022123470728.jpg)

![说明](https://img-blog.csdnimg.cn/20190221234841572.jpg)
例2：CSS样式如下：

```html
<ul>
    <li>1</li>
    <li>2
        <ol>
            <li>11</li>
            <li>22</li>
            <li>33</li>
        </ol>
    </li>
    <li class="li3">3</li>
    <p>0000</p>
    <li>4</li>
</ul>

```

使用如下：

```js
console.log($("ul li"));
console.log($("ul>li"));
console.log($(".li3+"));
console.log($(".li3~li"));

```

#### 3.过滤选择器

##### （1）简单过滤选择器

过滤选择器是**根据某类过滤规则进行元素的匹配**，书写时都**以(:)开头**；简单过滤是使用最广泛的一种。
功能表如下：
![简单过滤选择器](https://img-blog.csdnimg.cn/20190222202920465.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzY3NTQ0Nw==,size_16,color_FFFFFF,t_70)
例3：CSS样式如下：

```css
<ul>
    <li>1</li>
    <li>2
        <ol>
            <li>11</li>
            <li>22</li>
            <li>33</li>
        </ol>
    </li>
    <li class="li3">3</li>
    <p>0000</p>
    <li>4</li>
</ul>
```

使用如下：

```js
console.log($("ul>li:first"));
console.log($("ul>li:last"));
console.log($("ul>li:even"));
console.log($("ul>li:odd"));
console.log($("ul>li:gt(1)"));
console.log($("ul>li:lt(1)"));
console.log($("ul>li:eq(1)"));
console.log($("ul>li:not(.li3)"));
```

##### （2）内容过滤选择器

根据元素中的**文字内容**或所包含的**子元素特征**“位。
功能表如下：
![内容过滤选择器](https://img-blog.csdnimg.cn/2019022220352632.jpg)
例4：CSS样式如下：

```css
<ul>
    <li>1</li>
    <li>2
        <ol>
            <li>11</li>
            <li>22</li>
            <li>33</li>
        </ol>
    </li>
    <li class="li3">3</li>
    <p>0000</p>
    <li>4</li>
</ul>
<div><span>40</span></div>
<span></span>
```

使用如下：

```js
console.log($("li:contains(2)"));
console.log($("span:empty"));
console.log($("span:parent"));
console.log($("div:has(span)"));
```

##### （3）可见性过滤选择器

根据元素**是否可见**的特征来获取元素
功能表如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190222210111582.jpg)
例5：CSS样式如下：

```css
<input type="button" class="btninput" value="按钮1" >
<input type="button" class="btninput" value="按钮2" >

<input type="text" style="visibility:hidden" class="btninput">
    <input type="text" style="opacity: 0;" class="btninput">
```

使用如下：

```js
console.log($(".btninput:hidden"));
console.log($(".btninput:visible"));
```

注：实验证明，通过`opacity:0`和`visibility:hidden`隐藏的仍会被视为可见。

#####（4）属性过滤选择器

属性过滤选择器根据元素的某个属性获取元素，如ID号或匹配属性值的内容，并以"[“号开始，以”]"号结束。
功能表如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190222210740990.jpg)
例6：CSS样式：`<button id="btn" class="btn1">按钮</button>`
使用如下：

```css
console.log($("button[id][class]"));
console.log($("button[id='btn'][class='btn1']"));
```

#####（5）子元素过滤选择器
获取所有父元素中指定的某个元素
功能表如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190222211255428.jpg)
例7：CSS样式如下：

```css
<ul>
    <li>1</li>
    <li>2
        <ol>
            <li>11</li>
            <li>22</li>
            <li>33</li>
        </ol>
    </li>
    <li class="li3">3</li>
    <p>0000</p>
    <li>4</li>
</ul>
<div><span>40</span></div>
```

使用如下：

```js
console.log($("ul>li:nth-child(2)"));
console.log($("ul>li:first-child"));
console.log($("ul>li:last-child"));
console.log($("div>span:only-child"));
```

#####（6）表单对象属性过滤选择器
对**所选择的表单元素**进行过滤，例如选择被选中的下拉框，多选框等元素
功能表如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190222215619165.jpg)
例7：CSS样式如下：

```css
<input type="checkbox" checked>
<input type="checkbox">
<input type="radio">男
<input type="radio">女
<input type="text">
<select id="sel">
    <option>宝鸡</option>
    <option selected>西安</option>
</select>
```

使用如下：

```js
console.log($("input[type='checkbox']:checked"));
console.log($("input[type='radio']"));
console.log($("input[type='text']"));
console.log($("input:text"));
console.log($(":input"));
console.log($(":button"));
$("#sel").change(function(){
    console.log($("#sel>option:seleted"));
```

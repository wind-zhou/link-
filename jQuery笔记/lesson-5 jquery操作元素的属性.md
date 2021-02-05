# lesson-5

# jquery操作元素的属性

原生js操作操作节点属性的方法：

- getAttribute()
- setAttribute()
- removeAttribute()

- className
- style

##元素属性处理

###attr() 

作用：获取或设置指定属性 **（相当于getAttribute()和setAttribute()结合）**

### removeAttr()

作用：删除指定属性



**练习**：实现点击切换样式：

仅使用attr

```js
    <style>
        .one {
            width: 100px;
            height: 100px;
            background-color: aqua;
        }
        
        .two {
            width: 100px;
            height: 100px;
            background-color: #f00;
        }
    </style>
-----------------------------------------------------------------------------------------------------------------

<body>
    <div class="one"></div>
</body>
<script>
    $(function() {
        $("div").click(function() {
            if ($(this).attr("class") == "one") {
                $(this).attr("class", "two");
            } else {
                $(this).attr("class", "one")
            }
        })
    })
</script>
```



## class属性处理

class也是元素的属性，因此可以直接用attr()方法来对其设置、删除等。

除此之外也有几个单独操作class的方法。



**addClass()**：追加class，不会覆盖。attr设置会覆盖。

**removeClass()** ：删除指定class  如果没写参数，则删除所有的class

**toggleClass()** ：切换某个指定的class。 **内部会自动判断**有无，如果有就删掉，没有就加上。

**hasClass()**  ：判断是否包含某个class，有返回true，没有返回false。



**练习**：

**示例1**

使用addClass()和removeClass()重构点击样式切换

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="../jquery-3.5.1.min.js"></script>
    <style>
        .one {
            width: 100px;
            height: 100px;
            background: #f00;
        }
        
        .two {
            width: 100px;
            height: 100px;
            background: #0f0;
        }
    </style>
</head>

<body>
    <div class="one">
        hello world!
    </div>

</body>
<script>
    $(function() {
        $("div").click(function() {
            if ($(this).attr("class") == "one") {
                $(this).addClass("two")  
            } else {
                $(this).removeClass("two")//去除类two，直接使用attr设置也可以。
            }
        })
    })
</script>

</html>
```

注：这里第一次判断为切换样式，直接使用addClass()叠加了一个类（two），之前使用attr时是直接更改class值，这里可以叠加实现样式切换，因为css结构中two在one后面。

**示例2**

使用toggleClass()对代码进行简化

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="../jquery-3.5.1.min.js"></script>
    <style>
        .one {
            width: 100px;
            height: 100px;
            background: #f00;
        }
        
        .two {
            width: 100px;
            height: 100px;
            background: #0f0;
        }
    </style>
</head>

<body>
    <div class="one">
        hello world!
    </div>

</body>
<script>
    $(function() {
        $("div").click(function() {
           $(this).toggleClass("two ");//这里做了优化，因为toggleClass进行了自动判断（内部相当于removeClass()和addClass()的结合）
        })
    })
</script>

</html>
```

#jquery获取或设置元素的内容

**jquery中操作元素内容的方法有三个：html()、text()、val()。**分别对标原生js中的innerHTML、innerText、value



**html()**：获取或设置元素的内部html代码，包括文本和html标记。

**text()**：只可以读取和设置元素的文本内容。

**val()：**获取或设置表单元素的value值，（例如input）。



注：上面三个方法都有设置和获取两种功能，获取时不写参数，设置时，将内容作为参数即可。

表单选项的checked和selected属性。

使用val()方法设置checked和selected的默认值。例：`$("input:checkedbox").val("[html]")`



**示例：简单的表单验证**

**![mark](http://qiniu.wind-zhou.com/blog/210111/C62CFcf56F.png?imageslim)**

# jquery 操作css

## css基本处理

**jquery操作css通过css()方法**。（原生js操作css通过class，style。）



css()方法：**获取或设置指定的css样式**.

###读取

几点注意：

- css()方法，**行内和style里设置的样式都可以获取到**，而原生js的style方式只能获取行内。

- **获取每次只能获取一个值**。

- 不允许获取**合并和简写**的属性，例如background、border等，获取时必须细化，例如

  `$("p").css("backgroundColor")`,遇到连字符写成驼峰的形式。

**示例：**

**获取p的背景颜色值**

```js
    <style>
        .one {
            width: 100px;
            height: 100px;
            background-color: #f00;
        }
        
        .two {
            width: 100px;
            height: 100px;
            background-color: #0f0;
        }
    </style>
----------------------------------------------------------------------------------------------------------------------------

<body>
    <p class="two"> </p>
    <p class="one"></p>

</body>
<script>
    $(function() {
        var color = $("p").css("backgroundColor")
        console.log(color)  
    })
</script>
```

输出：![mark](http://qiniu.wind-zhou.com/blog/210111/jjG64i8dD6.png?imageslim)



**注：只获取了第一个匹配到的值**

### 设置

css()方法设置时可以同时设置多个样式，**写成json串的形式**。设置的样式也会变为行内式。

**注**：css()在设置时支持合并和简写的形式。

例如：

`$("p").css("background-color"," #f00")`//设置简写

`$("p").css({"border":"1px solid #f00","color":"black"})`  //同时设置多个值

示例：

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="../jquery-3.5.1.min.js"></script>
    <style>
        .one {
            width: 100px;
            height: 100px;
            background-color: #f00;
            text-align: center;
            line-height: 100px;
        }
        
        .two {
            width: 100px;
            height: 100px;
            background-color: #0f0;
            text-align: center;
            line-height: 100px;
        }
    </style>
</head>

<body>
    <p class="two">周正 </p>
    <p class="one"> 你好</p>

</body>
<script>
    $(function() {
        var color = $("p").css({
            "border": "2px solid black",
            "color": "black",
        })
        console.log(color)
    })
</script>

</html>
```

![mark](http://qiniu.wind-zhou.com/blog/210111/EiLcJh5B1l.png?imageslim)

## css尺寸处理

关于宽高的操作，jquery有比css("width")更简洁的方法。单位px

**共有三组方法：**

- [width()](https://www.runoob.com/jquery/css-width.html) - 设置或返回元素的宽度
- [height()](https://www.runoob.com/jquery/css-height.html) - 设置或返回元素的高度
- [innerHeight()](https://www.runoob.com/jquery/html-innerheight.html) - 返回元素的高度（包含 padding）
- [innerWidth()](https://www.runoob.com/jquery/html-innerheight.html) - 返回元素的宽度（包含 padding）
- [outerWidth()](https://www.runoob.com/jquery/html-outerwidth.html) - 返回元素的宽度（包含 padding 和 border）
- [outerHeight()](https://www.runoob.com/jquery/html-outerheight.html) - 返回元素的高度（包含 padding 和 border）

**语法:**

返回宽度：

`$(selector).width()`

设置宽度：

`$(selector).width(value)`

### height()和width()

width() 方法设置或返回被选元素的宽度。

当该方法用于**返回**宽度时， 则返回第一个匹配元素的宽度。

当该方法用于**设置**宽度时，则设置所有匹配元素的宽度。

如下面的图像所示，该方法不包含 padding、border 或 margin。

![mark](http://qiniu.wind-zhou.com/blog/210111/5A3lB7aljJ.png?imageslim)

**注：使用**``height()``和``width()``处理 ，**获取的直接是数值，不带单位**（直接用css()获取有单位）



### innerWidth()和innerHeight()

innerWidth() 方法返回第一个匹配元素的内部宽度。

如下面的图像所示，该方法包含 padding，但不包含 border 和 margin。

![mark](http://qiniu.wind-zhou.com/blog/210111/5e2L6IgF0i.png?imageslim)





### outWidth()和outHeight()

outerHeight() 方法返回第一个匹配元素的外部高度。

如下面的图像所示，该方法包含 padding 和 border。

**提示：****如需包含 margin，请使用 outerHeight(true)。**

![mark](http://qiniu.wind-zhou.com/blog/210111/J996hdk74J.png?imageslim)



## css位置处理

![mark](http://qiniu.wind-zhou.com/blog/210112/EIBk6fD30d.png?imageslim)



### offset

用的不是很多

通过设置相对定位实现位置移动

### scrollTop()和scrollLeft()

jquery控制**滚动条**只有这一种

![mark](http://qiniu.wind-zhou.com/blog/210112/62e9mblgLG.png?imageslim)












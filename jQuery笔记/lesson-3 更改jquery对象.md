# lesson-3 更改jquery对象(筛选)

**更改对象操作：**

在许多情况下，jquery代码所做的事情变成了：**生成**jquery对象A，**操作**对jquery象A；**更改**为jquery对象B，操作jquery对象B；更改为jqueryC，操作jquery对象C......；如果对象之间存在某种关系，我们就可以通过关系来更改对象。

**jquery的链式操作：**

链式操作概述：生成一个jquery对象后，既要对它进行一次或多次的普通操作，同时还要对它进行更改操作。于是有必要把生成jquery对象储存在一个变量中，满足多次调用的需要。

jquery执行普通操作后会返回对象本身。（注：更改对象操作不是。）



## 更改为后代元素集合

### children()

**作用：是用来选择子元素的**

- children("选择器");

  选择子元素中，所有**匹配选择器的直接子元素**

- children();

  选择父元素的**所有直接子元素**

### find()

**作用：是用来选择后代元素的**

- find("选择器");

  选择后代元素中，**所有匹配选择器的后代元素**

- find();

  不选择原先元素任何后代元素// 写不写都一样，什么都选不中

### contents()

**作用：选择匹配元素文本块（节点）和子节点**

**注：**包括空文本节点

## 更改为祖先元素集合

### parent()（常用）

**作用：选择父元素**

　　parent("选择器")； //选择父元素中，所有匹配选择器的元素

　　parent(); //选择所有父元素

### parents()（常用）

**作用：选择祖先元素**

　　parents("选择器");选择祖先元素中，所有匹配选择器的元素

　　parents();//选择所有祖先元素

<a href="#parents"> 练习</a>

### parentsUntil()

**作用：祖先元素**

　　parentUntil("选择器")；//**选择祖先元素，直到找到匹配选择器的元素，但不包括匹配元素**

　　parentUntil();//选择所有祖先元素

<a href="#parentsUntil">练习</a>

### offsetParent()

作用：**选择最近的祖先定位元素**，**且该元素的css属性display不能为none**；

所谓定位元素是指其css属性的position取值为relitive、absolute、fixed。

如果祖先元素中没有合适的元素，**则会选择\<html>根元素。**

<a href="#offsetParent">练习</a>

### closest("选择器")（不常用）

**作用**：选择器本身和其他祖先元素所有匹配选择器的元素。

也即是说，先看看原先的元素是否匹配，否则会一层一层地向上找到最先匹配祖先元素。



## 更改为兄弟元素

###next()和prev()

- next("选择器")，**在原先元素后面的第一个兄弟元素中，选择匹配选择器的元素**。

​		next()或next("*"),会选取原先元素后面的第一个兄弟。（带参数与不带参数）

- prev("选择器")，**在原先元素前面的第一个兄弟元素中，选择匹配选择器的元素**。

  prev()或prev("*"),会选取原先元素前面的第一个兄弟。

<a href="#next">练习</a>

### nextAll()、prevAll()和siblings()

**也是找兄弟，只是不局限下一个了，而是有一个算一个。**

- nextAll("选择器")，**在原先元素后面的兄弟元素中，选取匹配选择器的元素。**

  nextAll()或nextAll("*"),会选取原先元素后面的所有兄弟。*

  **（向下找）**

- *- prevAll("选择器")，在原先元素前面的兄弟元素中，选取匹配选择器的元素*。

  *prevAll()或prevAll("*"),会选取原先元素前面的所有兄弟。

  **（向前找）**

- siblings(“选择器”)，在原先元素所有兄弟元素中，选取匹配选择器的元素。

  siblings()或siblings(“*”)，会选取原先元素所有兄弟。

  **（双向找）**

<a href="siblings">练习</a>

## 更改为更多元素的集合(扩展)

### add()

add("选择器")方法，**在原先元素的基础上添加选取匹配选择器的元素**；

说明：$("选择器1").add("选择器2")选取的元素等同于$("选择器1"，"选择器2")；相当于群组选择器；//给祖先元素用。

<a href="#add">练习</a>

### andSelf()

**在更改对象后使用**，将**原对象**添加到进来形成集合。

> （我愿称之为吃水不忘挖井人）

## 更改为部分元素集合（收缩）

### eq()、first()、last()

- eq(index) 选择元素中索引值为index的元素，索引从0开始，逆向从-1开始。

  **这个可以用来遍历。**

- first() 选第一个 相当于eq(0)

- last()  选最后一个 相当于eq(-1)

<a href="#eq">练习</a>

### slice(start,[end])

**方法**：筛选索引从start到（end-1）的元素

### filter("选择器")

**作用：**选择匹配选择器的元素

### not("选择器")

**作用：**选择不匹配选择器的元素

### has("选择器")

**作用**：选择匹配选择器的后代元素





## 还原为之前的jquery对象

### end()

执行更改后，当前的对象会发生改变，如果还需要操作原对象，可以使用end()方法；

如果需要后退多次，还可以连续调用，直至返回一个空集。

<a href="#end">练习</a>

## 侧导航

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="../jquery/jquery.min.js "></script>
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
            box-sizing: border-box;
        }
        
        ul {
            list-style-type: none;
        }
        
        .main {
            width: 200px;
            border: 1px solid;
        }
        
        .main>h3 {
            background-color: aqua;
        }
        
        .main li {
            text-align: center;
            border-bottom: 1px solid #000;
            background-color: blueviolet;
        }
        
        .main ul {
            display: none;
        }
        
        .show {
            display: block !important;
        }
        
        .hidden {
            display: none !important;
        }
    </style>
</head>

<body>

    <div id="con">
        <div class="main">
            <h3>游戏</h3>
            <ul>
                <li>王者荣耀</li>
                <li>和平精英</li>
                <li>滑雪大冒险</li>
            </ul>
        </div>

        <div class="main">
            <h3>体育</h3>
            <ul>
                <li>篮球</li>
                <li>排球</li>
                <li>玻璃球</li>
            </ul>
        </div>
        <div class="main">
            <h3>旅游</h3>
            <ul>
                <li>秦皇岛</li>
                <li>青岛</li>
                <li>海南岛</li>
            </ul>
        </div>
        <div class="main">
            <h3>音乐</h3>
            <ul>
                <li>邓紫棋</li>
                <li>张韶涵</li>
                <li>张靓颖</li>
            </ul>
        </div>


    </div>

</body>
<script>
    //原生js实现
    //点击时其他隐藏，只显示点击的部分

    // var divList = document.getElementsByClassName("main");
    // for (var i = 0; i < divList.length; i++) {

    //     divList[i].children[0].onclick = function() { //遍历main。找到每个h3，逐个绑定事件
    //         if (this.nextElementSibling.className == "") { //判断h3是否第一次被点击，如果是，则显示
    //             console.log("本个h3第一次被点击")
    //                 //1、遍历所有的ul，清空样式
    //             for (var j = 0; j < divList.length; j++) {
    //                 divList[j].children[1].className = "";
    //             }

    //             this.nextElementSibling.className = "show";
    //         } else { //判断h3是否第二次被点击，如果是，则再次消失
    //             console.log("本个h3第n次被点击")
    //             this.nextElementSibling.className = "";
    //         }
    //     }
    // }

    //jquery实现
    $(
        function() {
            $("h3").click(function() {
                $(this).next().show().parent().siblings().children("ul").hide();
            })
        }
    )
</script>

</html>
```



## 练习

### 更改为后代元素

#### children

(1)带参数

```js
<body>
    <ul class="one">
        <li class="first">1-1</li>
        <li id="second">1-2</li>
        <li class="first">1-3</li>
    </ul>
</body>

<script>
    $(function() {
        var $liNode = $(".one").children(".first");
        $liNode.css("background", "#0f0");
        console.log($liNode)
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/cHikm0mfI0.png?imageslim)

（2）不带参数 --选择所有

![mark](http://qiniu.wind-zhou.com/blog/210107/1Ccl2laKil.png?imageslim)



####contents()

```js
<body>
    <ul class="one">
        <li class="first">1-1</li>
        <li id="second">1-2</li>
        <li class="first">1-3</li>
    </ul>
</body>

<script>
    $(function() {
        var $liNode = $(".one").contents();
        $liNode.css("background", "#0f0");
        console.log($liNode)
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/Hli16chK3F.png?imageslim)

### 更改为祖先元素

#### parent()

(1)带参数

```js
<body>
    <ul class="one">
        <li class="first">1-1</li>
        <li id="second">1-2</li>
        <li class="first">1-3</li>
    </ul>
    <ul class="two">
        <li class="first">1-1</li>
        <li id="second">1-2</li>
        <li class="first">1-3</li>
    </ul>
</body>

<script>
    $(function() {
        var $liNode = $(".first").parent(".one");
        $liNode.css("background", "#0f0");
        console.log($liNode)
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/k9141G0KC3.png?imageslim)

(2）不带参数---选择所有

```js
<body>
    <ul class="one">
        <li class="first">1-1</li>
        <li id="second">1-2</li>
        <li class="first">1-3</li>
    </ul>
    <ul class="two">
        <li class="first">1-1</li>
        <li id="second">1-2</li>
        <li class="first">1-3</li>
    </ul>
</body>

<script>
    $(function() {
        var $liNode = $(".first").parent();
        $liNode.css("background", "#0f0");
        console.log($liNode)
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210107/2C4a77a31c.png?imageslim)

#### parents()

**找祖先**

<a name="parents"></a>

(1)不带参数

**找所有祖先**

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1.min.js"></script>
</head>

<body>
    <div class="conatiner">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li class="first">1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li class="first">1-3</li>
        </ul>
    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".first").parents();
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>

</html>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/39dKa4ikFJ.png?imageslim)

（2）带参数

**找指定祖先**

```js
<body>
    <div class="conatiner">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li class="first">1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li class="first">1-3</li>
        </ul>
    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".first").parents("body");
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210107/l1F9JHdcJ2.png?imageslim)

#### parentsUntil()

<a name="parentsUntil"></a>

(1)带参数  

**有截止位置**

```js
<body>
    <div class="conatiner">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li class="first">1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li class="first">1-3</li>
        </ul>
    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".first").parentsUntil("body");
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/g6C5mjfEIE.png?imageslim)

(2)不带参数

**找所有的祖先元素，和parents()效果相同。**

不再演示。

#### offsetParent()

**找最近设置了定位的祖先元素**

<a name="offsetParent"></a>

```js
    <style>
        .container {
            position: relative;
        }
    </style>
-------------------------------------------------------------------------------------------------------------------------------
<body>
    <div class="container">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li class="first">1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li class="first">1-3</li>
        </ul>
    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".first").offsetParent();
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/8HaB7fa375.png?imageslim)

### 更改为兄弟元素

#### next()

<a name="next"></a>

**找下一个兄弟**

(1)不带参数

*找所有的下一个兄弟。*

```js
<body>
    <div class="container">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>
    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".first").next();
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/8ahlFIHjjl.png?imageslim)

(2)带参数

又加了个限制条件进行筛选

```js
<body>
    <div class="container">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>
    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".first").next(".second");
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210107/mCEI9jAjcI.png?imageslim)

prev()同理，这里不再演示。

#### siblings()

<a name="siblings"></a>

**找兄弟。**

注：这里nextAll()和prevAll()不再演示，只练习siblings()

```js
<body>
    <div class="container">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".two").siblings();
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/k4maCa422B.png?imageslim)

前后两个兄弟都被找到，当然也可以加参数再次进行筛选。

### 更改为更多元素集合

<a href="add"></a>

#### add()

**扩展选择器集合**

```js
<body>
    <div class="container">
        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".two").add("#second");
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210107/2bm735e7jb.png?imageslim)

#### andSelf()

把老东家（原对象）也加进来。

```js

<body>
    <div class="container">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

    </div>
</body>

<script>
    $(function() {
        var $liNode = $(".two").next().andSelf();
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>

```

![mark](http://qiniu.wind-zhou.com/blog/210107/9F24bcKjBF.png?imageslim)

### 更改为部分元素集合

<a  name="eq"></a>

#### eq()

```js
<body>
    <div class="container">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

    </div>
</body>

<script>
    $(function() {
        var $liNode = $("ul").eq(1);
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210107/hD536CAJA6.png?imageslim)



#### slice()

```js

<body>
    <div class="container">
        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="four">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>


    </div>
</body>

<script>
    $(function() {
        var $liNode = $("ul").slice(1, 3);
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210107/aEH4dmD81f.png?imageslim)

#### filter()

```js
    <div class="container">
        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>


    </div>
</body>

<script>
    $(function() {
        var $liNode = $("ul").filter(".three");
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210107/gGDHFf1g93.png?imageslim)

#### has()

```js
<body>
    <div class="container">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li id="five">1-3</li>
        </ul>

    </div>
</body>

<script>
    $(function() {
        var $liNode = $("ul").has("#five");
        $liNode.css("border", " 1px solid #0f0");
        console.log($liNode)
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210107/AmHdIGfKHL.png?imageslim)

因为只有ul.three有id=five的儿子，因此被选了出来。

### 还原jquery对象

#### end()

<a name="end"></a>

```js
<body>
    <div class="container">


        <ul class="one">
            <li class="first">1-1</li>
            <li id="second">1-2</li>
            <li>1-3</li>
        </ul>
        <ul class="two">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li>1-3</li>
        </ul>

        <ul class="three">
            <li class="first">1-1</li>
            <li class="second">1-2</li>
            <li id="five">1-3</li>
        </ul>

    </div>
</body>

<script>
    $(function() {
        $(".container").children(".two").css("border", " 1px solid #0f0").end().children(".three").css("background", "#0f0");
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210107/BHL72ILGhl.png?imageslim)
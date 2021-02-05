# lesson-4 操作对象(节点)

## 创建节点

dom 节点创建的过程（创建节点<元素、属性、文本等>、添加节点的属性、加入到文档中）

**创建节点，直接 $(selector)即可，相当于DOM中的document.createElement(selector)**

jQuery创建元素节点的方法：

**创建元素节点:**

```js
$("<div></div>")；
```

**创建文本节点：**

```js
$("<div>直接将文本的内容添加进去</div>")；
```

**创建属性节点：**

```js
var div = $("<div class='right'><div class='aaron'>动态创建DIV元素节点</div></div>")
```

此时节点创建完成。下面开始对接点进行操作。

## 移动（插入）节点

在动态创建HTML元素节点后，还需将节点**插入到文档中**才有用。

根据元素的插入位置不同，插入方法分为**内部插入**和**外部插入**，如下表：

|                   类型                   |      方法      |                       描述                       |
| :--------------------------------------: | :------------: | :----------------------------------------------: |
|  **内部插入**<br />（插入后作为子元素）  |    append()    | 向每个匹配的**元素内部末尾**追加由参数指定的内容 |
|                                          |   appendTo()   |        把所有匹配的元素追加到指定的元素中        |
|                                          |   prepend()    |         向每个匹配的**元素内部前**置内容         |
|                                          |  prependTo()   |        把所有匹配的元素前置到指定的元素中        |
| **外部插入**<br />（插入后作为兄弟元素） |    after()     |           在每个匹配的元素之后插入内容           |
|                                          |    before()    |           在每个匹配的元素之前插入内容           |
|                                          | insertAfter()  |       把所有匹配的元素插入到指定的元素后面       |
|                                          | insertBefore() |       把所有匹配的元素插入到指定的元素后面       |

###append()和appendTo()

append() :向每个匹配的**元素内部末尾**追加由参数指定的内容

appendTo(): 把所有匹配的元素追加到指定的元素中

**注：append()和appendTo()方法颠倒过来**

### prepend()和prependTo()

prepend() ：向每个匹配的**元素内部前**置内容

prependTo()：把所有匹配的元素**前置**到指定的元素中

###after()和insertAfter()

after() 在匹配的**元素后**添加元素 

insertAfter() 将匹配元素添加到指定元素后面

### before()和insertBefore()

before()： 在每个匹配的**元素之前**插入内容

insertBefore() ：把所有匹配的元素插入到指定的元素后面

## 复制节点

### clone()

**clone()内的参数有两个：true和false**

true：在复制时连同事件绑定事件的也一起复制

false：不复制绑定的事件

## 替换元素

### replaceAll(selector)

replaceAll(selector)：使用指定的元素，替换掉所有匹配selector的元素



移动页面所有的元素来替换当前选定的元素 （找到10个，就把10个全搬过来）

你有3，我有3，咱们一替换就变了9个

###replaceWith(content)

replaceAll()  前面吧后面的换了，**和前面反过来**  自己测试

## 包裹节点

​	**不是很常用**

### wrap()

**复制节点的所有元素来包裹当前选定的元素**。

给某节点添加父节点（给他找个爹）

### unwrap()

 删除父元素（把他爸杀了）

## 删除和清空元素

jQuery中删除节点的方法:
　　remove(): **移除所有匹配的元素.**
　　empty(): 删除匹配的元素集合中所有内容,包括子节点.注意,**元素本身没有被删除**.

关于remove()方法,有几点需要说明一下:
　　1.remove()方法的**返回值**:
　　remove()方法会返回被删除节点的jQuery对象.可以把这个对象插入到其他的地方.
　　所以也可以用这种方法来移动节点

###remove()

###detach()  (可以保留当前元素事件)

###empty()  清空元素

## 练习

### 插入节点

#### append()和appendTo()

- appendTo()

  **操作对象是被插入的节点**

```js
<body>
    <button id="btn">点击向container中添加节点</button>
    <h1 id="name">周正</h1>
    <div class="container">
        <h1>hello world!</h1>
    </div>

</body>
<script>
    $(function() {
        $("#btn").click(function() {
            var hNode = $("<h2>这个世界很美好！</h2>"); //创建节点
            hNode.appendTo(".container");  //添加节点到...
        })
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210110/hhb1bd3CIF.png?imageslim)



注：插入节点时也可以插入已经存在的节点（**移动节点**）

上面jquery代码稍加改动即可：

```js
<script>
    $(function() {
        $("#btn").click(function() {
            $("#name").appendTo(".container");  //改动的部分
        })
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210110/JhdJ9Ehhd7.gif)

- append()

  **操作对象是要被插入节点的节点。**

html结构同上。

```js
<script>
    $(function() {
        $("#btn").click(function() {
            $(".container").append($("#name")).append($("<input type=\"num\" value=\"10\">"));
            //第二个append中直接写"<input type=\"num\" value=\"10\">"也行
        })
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210110/4fDg96cH1H.gif)



#### prepend()和prependTo()

- prepend()

```js
<body>
    <button id="btn">点击向container中添加节点</button>
    <h1 id="name">周正</h1>
    <div class="container">
        <h1>hello world!</h1>
    </div>
</body>

<script>
    $(function() {
        $("#btn").click(function() {
            $(".container").prepend($("#name")).prepend("<input type=\"num\" value=\"10\">");
        })
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210110/GelK1hc1l6.png?imageslim)



prependTo()和appendTo()使用方法一样，这里不做演示。

#### after()和insertAfter()

- after

**在该元素后面添加节点**

```js

<body>
    <button id="btn">点击向container中添加节点</button>
    <h1 id="name">周正</h1>
    <div class="container" style="border:1px solid #f00">
        <h1>hello world!</h1>
    </div>

</body>
<script>
    $(function() {
        $("#btn").click(function() {
            $(".container").after($("#name")).prepend("<input type=\"num\" value=\"10\">");
        })
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210111/FjJibjAlA9.gif)

- insertAfter()

```js
<body>
    <button id="btn">点击向container中添加节点</button>
    <h1 id="name">周正</h1>
    <div class="container" style="border:1px solid #f00">
        <h1>hello world!</h1>
    </div>

</body>
<script>
    $(function() {
        $("#btn").click(function() {
            // $(".container").after($("#name")).prepend("<input type=\"num\" value=\"10\">");

            $("#name").insertAfter($(".container")); // $("#name").insertAfter(".container");也可以
        })
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210111/0lDh9HJcj3.png?imageslim)



#### bofore()和insertBefore()

- bofore()

**在本元素前面添加节点**

```js
<body>
    <button id="btn">点击向container中添加节点</button>
    <h1 id="name">周正</h1>
    <div class="container" style="border:1px solid #f00">
        <h1>hello world!</h1>
    </div>

</body>
<script>
    $(function() {
        $("#btn").click(function() {
            $(".container").before("<input type=\"num\" value=\"10\">");
        })
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210111/BC7ma52gJK.png?imageslim)

- insertBefore()

```js
<script>
    $(function() {
        $("#btn").click(function() {
            $("<input type=\"num\" value=\"10\">").insertBefore(".container");
        })
    })
</script>
```

效果和前面一样。

### 复制节点

#### clone()

```js
<body>
    <button id="btn">点击向container中添加节点</button>
    <h1 id="name">周正</h1>
    <div class="container" style="border:1px solid #f00">
        <h1>hello world!</h1>
    </div>

</body>
<script>
    $(function() {
        $("#btn").click(function() {

            var node = $("#name").clone();
            console.log(node)
        })
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210111/bkl3j19kcj.png?imageslim)





### 替换节点

#### replaceWith()和replaceAll()

- replaceWith()

```js
<body>
    <button id="btn">点击向container中添加节点</button>
    <ul>
        <li class="source">1</li>
        <li class="source">2</li>
        <li class="source">3</li>
    </ul>

    <ul class="one">
        <li>我</li>
        <li>是</li>
        <li>你</li>
        <li>爹</li>
    </ul>

</body>
<script>
    $(function() {
        $("#btn").click(function() {

            $(".source").replaceWith($(".one").children())
        })
    })
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210111/7G7Dk1FceK.png?imageslim)



#### replaceAll()

```js
<script>
    $(function() {
        $("#btn").click(function() {

            $(".one").children().replaceAll(".source")
        })
    })
</script>
```

效果和上面例子一样。

### 包裹元素

#### wrap()

**给节点套个父节点**

```js
<body>
    <button id="btn">点击触发</button>
    <h1>hello world</h1>
    <div class="three" style="border:1px solid #ff0000">

    </div>
</body>
<script>
    $(function() {
        $("#btn").click(function() {
            $("h1").wrap("<p></P>")
        })
    })
</script>

```



![mark](http://qiniu.wind-zhou.com/blog/210111/FamII0D6Gc.png?imageslim)



#### unwrap()

删除父元素（触发一次，删除一层父元素）

````js
<body>
    <button id="btn">点击触发</button>


    <div>
        <div>
            <div>
                <h1>hello world</h1>
            </div>
        </div>
    </div>

    <div class="three" style="border:1px solid #ff0000">

    </div>
</body>
<script>
    $(function() {
        $("#btn").click(function() {
            $("h1").unwrap()
        })
    })
</script>
````

效果不再演示。

### 删除元素

#### remove()和detach

remove和detach删除节点连同本身也删除掉，并且会将删除的部分返回。**（有返回值）**

因为有返回值，所以我们可以将返回的部分移动到其他地方。

**remove和detach的区别：**

remove的返回部分会失去之前这些节点上的事件

detach的返回部分会保留之前绑定的事件

**注：但是，现在测试证明remove和detach都会保留返回部分绑定的事件，可能是现在的jquery版本已不再区分。**



```js
<body>
    <button id="btn">点击向container中添加节点</button>
    <ul class="two">
        <li class="source">1</li>
        <li class="source">2</li>
        <li class="source">3</li>
    </ul>

    <ul class="one">
        <li>我</li>
        <li>是</li>
        <li>你</li>
        <li>爹</li>
    </ul>


    <div class="three" style="border:1px solid #ff0000">

    </div>
</body>
<script>
    $(function() {
        $("#btn").click(function() {
            var testNode = $(".two").detach();  //换成remove效果一样
            testNode.appendTo(".three");
        })
    })



    var liList = document.getElementsByClassName("source");
    for (var i = 0; i < liList.length; i++) {
        liList[i].onclick = function() {
            this.style.background = "#f00";
        }
    }
</script>
```



![mark](http://qiniu.wind-zhou.com/blog/210111/Ed0CD5HDbg.gif)

#### empty

清空内容，包括文本内容，子节点等，**没有返回值**。

**注：节点本身并不会被删除。**

```js
<body>
    <button id="btn">点击向container中添加节点</button>
    <ul class="two">
        <li class="source">1</li>
        <li class="source">2</li>
        <li class="source">3</li>
    </ul>

    <ul class="one">
        <li>我</li>
        <li>是</li>
        <li>你</li>
        <li>爹</li>
    </ul>


    <div class="three" style="border:1px solid #ff0000">

    </div>
</body>
<script>
    $(function() {
        $("#btn").click(function() {
            $(".two").empty();
        })
    })



    var liList = document.getElementsByClassName("source");
    for (var i = 0; i < liList.length; i++) {
        liList[i].onclick = function() {
            this.style.background = "#f00";
        }
    }
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210111/dmKHlACf7E.png?imageslim)




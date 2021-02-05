# lesson-6 jquery动画效果

![mark](http://qiniu.wind-zhou.com/blog/210120/HKfaC9aeGK.png?imageslim)

## 隐藏显示

### hide()

**作用**：动态改变当前元素的**高度、宽度、不同明度**等，最终隐藏当前元素，此时实现隐藏式由于**display修改为none**。

**语法**： hide(动画运行时间)； 

```js
$(selector).hide(speed,callback)
```

speed：里面可选参数：slow（0.6秒）；normal(0.4秒)；fast（0.2秒）,

| 参数       | 描述                                                         |
| :--------- | :----------------------------------------------------------- |
| *speed*    | 可选。规定元素从可见到隐藏的速度。默认为 "0"。<br /><br />可能的值：<br /><br />- 毫秒 （比如 1500）<br />- "slow"<br />- "normal"<br />- "fast"<br /><br />在设置速度的情况下，元素从可见到隐藏的过程中，会逐渐地改变其**高度**、**宽度**、**外边距**、**内边距**和**透明度**。 |
| *callback* | 可选。<br /><br />hide **函数执行完之后，要执行的函数**。<br /><br />如需学习更多有关 callback 的内容，请访问我们的 jQuery Callback 这一章。除非设置了 speed 参数，否则不能设置该参数。 |



**test：**

点击隐藏

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>hide测试</title>
    <script src="../jquery-3.5.1/jquery-3.5.1.min.js">
    </script>
    <style>
        .con {
            width: 100px;
            height: 100px;
            margin: 0 auto;
        }
        
        .one {
            background: red;
        }
        
        .two {
            background: green;
        }
        
        .three {
            background: yellow;
        }
        
        .four {
            background: blue;
        }
    </style>
</head>

<body>
    <button id="btn"> 点击隐藏</button>

    <div class="one con"></div>

    <div class="two con"> </div>

    <div class="three con"></div>

    <div class="four con"></div>



</body>

<script>
    $(function() {

        $("#btn").click(function() {
            $(".one").hide("slow");
            $(".two").hide();
            $(".three").hide("fast");
            $(".four").hide(2000);
        })
    })
</script>

</html>
```



![mark](http://qiniu.wind-zhou.com/blog/210120/CbiaKeD9dB.gif)



分析：上面对hide里不用的speed参数进行了测试。右侧可见几个参数连续变化，知道最后最后消失，最终display变为none。

让我们抓取一帧看一下里面的内容。

![mark](http://qiniu.wind-zhou.com/blog/210120/FEF20e8jEK.png?imageslim)



变化的内容分别为**width、height、margin、padding、opacity**五个值。



### show()

**show的语法和hide完全相同。**只不过作用用来显示，显示后最终display恢复为none意外的值。



**示例1：**

点击隐藏，2s后自自动显示



```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>hide测试</title>
    <script src="../jquery-3.5.1/jquery-3.5.1.min.js">
    </script>
    <style>
        .con {
            width: 100px;
            height: 100px;
            margin: 0 auto;
        }
        
        .four {
            background: blue;
        }
    </style>
</head>

<body>
    <button id="btn"> 点击隐藏</button>

    <div class="four con"></div>

</body>

<script>
    $(function() {
        $("#btn").click(function() {
            $(".four").hide(2000, function() {
                setTimeout(function() {
                    $(".four").show(2000)
                }, 1000)
            });
        })
    })
</script>

</html>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/210120/LHdBDf4H41.gif)

**示例2：**

点击实现隐藏显示

![mark](http://qiniu.wind-zhou.com/blog/210120/Fb3j80jmE4.png?imageslim)



### toggle()

作用：会动态改变**width、height、margin、padding、opacity**五个值，并切换元素的可见状态。

即：若元素可见则切换为隐藏，隐藏则切换为可见。

 toggle() 方法是hide() 和 show() 方法的结合。

**示例：**

点击实现显示隐藏（使用toggle方法）

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>hide测试</title>
    <script src="../jquery-3.5.1/jquery-3.5.1.min.js">
    </script>
    <style>
        .con {
            width: 100px;
            height: 100px;
            margin: 0 auto;
        }
        
        .four {
            background: blue;
        }
    </style>
</head>

<body>
    <button id="btn"> 点击隐藏</button>

    <div class="four con"></div>

</body>

<script>
    $(function() {

        $("#btn").click(function() {
            $(".four").toggle(1000);
        })
    })
</script>

</html>
```



![mark](http://qiniu.wind-zhou.com/blog/210120/ka5ig1k7if.gif)





## 淡入淡出

### fadeOut()

**作用**：动态改变的当前元素的不透明度（**其他的不变**），最终隐藏。此时css属性修改为none。



**语法**：同hide和show相同

```js
$(selector).fadeOut(speed,callback)
```

speed：里面可选参数：slow（0.6秒）；normal(0.4秒)；fast（0.2秒）,

| 参数       | 描述                                                         |
| :--------- | :----------------------------------------------------------- |
| *speed*    | 可选。规定元素从可见到隐藏的速度。默认为 "0"。<br /><br />可能的值：<br /><br />- 毫秒 （比如 1500）<br />- "slow"<br />- "normal"<br />- "fast"<br /><br />在设置速度的情况下，元素从可见到隐藏的过程中，会逐渐地改变**透明度**。 |
| *callback* | 可选。<br /><br /> 函数执行完之后，要执行的函数。<br /><br />如需学习更多有关 callback 的内容，请访问我们的 jQuery Callback 这一章。除非设置了 speed 参数，否则不能设置该参数。 |

### fadeIn()

淡入效果。使用同上。

### fadeToggle()

动态切换，使用同toggle相同。

### fadeTo()

作用：**将当前元素调整至指定的透明度。**

语法：

```js
$(selector).fadeTo(speed,不透明度)

不透明度在0-1之间。
```



**示例1：**

点击实现淡入淡出

```js
<script>
    $(function() {

        $("#btn").click(function() {
            $(".four").fadeToggle(2000)
        })
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210120/B1e7ec2LbK.gif)



**示例2：**

使用fadeTo实现遮罩层效果

```JS
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>hide测试</title>
    <script src="../jquery-3.5.1/jquery-3.5.1.min.js">
    </script>
    <style>
        .con {
            width: 100px;
            height: 100px;
            margin: 0 auto;
        }
        
        .four {
            background: blue;
            position: relative;
        }
        
        .overlap {
            width: 100%;
            height: 100%;
            position: absolute;
            left: 0;
            top: 0;
            background: black;
            opacity: 0;
        }
    </style>
</head>

<body>
    <button id="btn"> 点击隐藏</button>

    <div class="four con">
        <div class="overlap"></div>
    </div>


</body>

<script>
    $(function() {

        $(".overlap").mouseover(function() {
            $(this).fadeTo(0, 0.4)
        })

        $(".overlap").mouseout(function() {
            $(this).fadeTo(0, 0)
        })
    })
</script>

</html>
```



![mark](http://qiniu.wind-zhou.com/blog/210120/e6BmHa3fk7.gif)



## 划入划出

![mark](http://qiniu.wind-zhou.com/blog/210122/j00eB1Dk1I.png?imageslim)

### slideUp()

作用：动态改变当前元素的**高度**（其他不变），最终隐藏当前元素。此时display修改为none。

语法：语法与hide()、show()相同。

### slideDown()

作用：动态改变当前元素的**高度**（其他不变），最终隐藏当前元素。此时css属性修改为block。

语法：语法与hide()、show()相同。



**示例1：**

点击隐藏和显示



```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .one {
            width: 200px;
            height: 200px;
            background: red;
            margin: 0 auto;
        }
    </style>
</head>

<body>
    <button id="hide"> 点击隐藏</button>

    <button id="show"> 点击显示</button>

    <div class="one">

    </div>

</body>

<script>
    $(function() {
        $("#hide").click(function() {
            $(".one").slideUp(2000)
        })

        $("#show").click(function() {
            $(".one").slideDown(2000)
        })
    })
</script>

</html>
```

![mark](http://qiniu.wind-zhou.com/blog/210122/C94HDG59A3.gif)

### slideToggle()

作用：动态改变当前元素的高度（其他不变），最终**切换可见状态**。

![mark](http://qiniu.wind-zhou.com/blog/210122/iLF8EHG11l.gif)



**示例2：**

使用slideUp、slideDown实现二级菜单。

（1）还用mouseover和mouseout触发事件

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        .one {
            width: 600px;
            /* display: flex; */
            margin: 0 auto;
        }
        
        ul {
            list-style-type: none;
        }
        
        .item {
            width: 200px;
            background: green;
            text-align: center;
            float: left;
        }
        
        .item>ul {
            display: none;
            background: yellow;
        }
    </style>
</head>

<body>

    <ul class="one">
        <li class="item">
            手机
            <ul>
                <li>华为</li>
                <li>小米</li>
                <li>oppo</li>
                <li>vivo</li>
            </ul>
        </li>

        <li class="item">
            电脑
            <ul>
                <li>惠普</li>
                <li>华硕</li>
                <li>联想</li>
                <li>华为</li>
            </ul>
        </li>

        <li class="item">
            明星
            <ul>
                <li>空尼奇瓦</li>
                <li>马尔扎哈</li>
                <li>迪丽热巴</li>
                <li>古力娜扎</li>
            </ul>
        </li>
    </ul>

</body>

<script>
    $(function() {
        var x = 1;
        var y = 1;
        $(".item").mouseover(function() {
            $(this).children("ul").slideDown("slow")
            console.log("触发了" + x + "次slideUp");
            x++;
        }).mouseout(function() {
            $(this).children("ul").slideUp("slow")
            console.log("触发了" + y + "次slideDown");
            y++;
        })

    })
</script>

</html>
```

**效果：**

![mark](http://qiniu.wind-zhou.com/blog/210124/5LHkh9keBB.gif)

**分析：**

上面的演示可知，使用mouseover和mouseout触发事件会有一个bug，就是划入子菜单的时候会出现来回弹跳的现象。

**原因**：事件冒泡带来的重复触发。 

当鼠标从导航条划入子菜单时，由于子元素上没有绑定事件，因此会向外冒泡，冒到绑定了slideup的li上，造成重复的触发mouseover，mouseout同理，当鼠标划出“手机”时，会触发一次mouseout（这是关键），当每次划过子菜单里的每一个li时，又会再次重复触发mouseout，因此会造成反复弹跳的现象。

**解决方案**：使用mouseenter和mouseleave来绑定事件



>注：这里的冒泡带来的bug我想了好长时间，后来明白了，第一行的导航栏“手机”“电脑”,本身就是绑定了事件的li的子元素，我之前把他们理解成了li本身，所以当时感觉从”手机“移动到下面的区域是从父元素进入子元素，这就产生了错误。
>
>理解正确时候，就可以理解为什么从“手机”进入下方后不会触发slidedown。

（2）使用mouseenter和mouseleave来绑定事件

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        * {
            padding: 0;
            margin: 0;
        }
        
        .one {
            width: 600px;
            /* display: flex; */
            margin: 0 auto;
        }
        
        ul {
            list-style-type: none;
        }
        
        .item {
            width: 200px;
            background: green;
            text-align: center;
            float: left;
        }
        
        .item>ul {
            display: none;
            background: yellow;
        }
    </style>
</head>

<body>

    <ul class="one">
        <li class="item">
            手机
            <ul>
                <li>华为</li>
                <li>小米</li>
                <li>oppo</li>
                <li>vivo</li>
            </ul>
        </li>

        <li class="item">
            电脑
            <ul>
                <li>惠普</li>
                <li>华硕</li>
                <li>联想</li>
                <li>华为</li>
            </ul>
        </li>

        <li class="item">
            明星
            <ul>
                <li>空尼奇瓦</li>
                <li>马尔扎哈</li>
                <li>迪丽热巴</li>
                <li>古力娜扎</li>
            </ul>
        </li>
    </ul>

</body>

<script>
    $(function() {
        var x = 1;
        var y = 1;
        $(".item").mouseenter(function() {
            $(this).children("ul").slideDown(3000)
            console.log("触发了" + x + "次slideUp");
            x++;
        }).mouseleave(function() {
            $(this).children("ul").slideUp(3000)
            console.log("触发了" + y + "次slideDown");
            y++;
        })
    })
</script>

</html>
```

效果：

![mark](http://qiniu.wind-zhou.com/blog/210124/44FC3II6JD.gif)



**注：**第一种方法和核心问题是划不到子区域上，其实带来这种问题的主要是mouseout的问题，因此只需要把mouseout改为mouseleave即可，mouseover不需要改动。

**实验证明，同时改动mouseover和mouseout和只改动mouse都会在某时触发反复弹跳的问题。**

># [mouseover和mouseenter的区别](https://www.cnblogs.com/psxiao/p/11543333.html)
>
>mouseover：当鼠标移入元素或其子元素都会触发事件，所以有一个重复触发，冒泡过程。对应的移除事件是mouseout
>
>mouseenter:当鼠标移除元素本身（不包含元素的子元素）会触发事件，也就是不会冒泡，对应的移除事件是mouseleave
>
>**mouseover和mouseenter的异同体现在两个方面：**
>
>1. 是否支持冒泡
>
>​     2.事件的触发时机
>
>先看一张图，对这两件事有一个简单直观的感受。
>
>![img](https://img2018.cnblogs.com/blog/1670358/201909/1670358-20190918160838058-597135305.png)
>
> 
>
> mouseenter事件的情况：
>
> 当鼠标从元素的边界之外移入元素的边界之内时，事件被触发。而鼠标本身在元素边界内时，要触发该事件，必须先将鼠标移出元素边界外，再次移入才能触发。
>
>也就是说：mouseover支持事件冒泡，而mouseenter不支持事件冒泡
>
> 
>
>由于mouseenter不支持事件冒泡，导致在一个元素的子元素上进入或离开的时候会触发其mouseover和mouseout事件，但不会触发mouseenter和mouseleave事件。
>
>**如何模拟mouseenter事件**
>
> 
>
>可见mouseover事件因其具有冒泡的性质，在子元素内移动的时候，频繁被触发，如果我们不希望如此，可以使用mouseenter事件代替之，但是早期只有ie浏览器支持该事件，虽然现在大多数高级浏览器都支持了mouseenter事件，但是难免会有些兼容问题，所以如果可以自己手动模拟，那就太好了。
>
># [mouseout和mouseleave的区别](https://www.cnblogs.com/coconutGirl/p/9435330.html)
>
>mouseleave事件是各元素各自触发，不是由子元素冒泡而来，而mouseout是由子元素冒泡而来。也就是：
>
>mouseleave是当**鼠标指针离开了目标元素以及目标元素的所有子元素以后才会触发**。如下例就是如果第二个div的高度比第三个有文本内容的div高，离开文本后鼠标还在第二个div范围内，只会触发有文本内容的div的mouseleave事件。
>
>而mouseout是只要鼠标指针离开了目标元素或者目标元素的所有子元素中的任何一个就会被触发，即使鼠标指针还在目标元素内。也就是离开子元素后，mouseout事件会冒泡到父元素上。直到取消了冒泡或者到达了最外层根元素，才会停止冒泡。

## 自定义动画 animate

![mark](http://qiniu.wind-zhou.com/blog/210124/m8h5efm8D6.png?imageslim)





**作用**：可以动态的改变当前元素的各种css属性。

该方法通过CSS样式将元素从一个状态改变为另一个状态。CSS属性值是逐渐改变的，这样就可以创建动画效果。

**语法1：**

```js
$(selector).animate({styles},speed,easing,callback)
```

| 参数       | 描述                                                         |
| :--------- | :----------------------------------------------------------- |
| *styles*   | 必需。规定产生动画效果的一个或多个 CSS 属性/值。<br /><br />**注意：** 当与 animate() 方法一起使用时，该属性名称必须是**驼峰写法**：<br /><br /> 您必须使用 paddingLeft 代替 padding-left，marginRight 代替 margin-right，依此类推。<br /><br />可以应用动画的属性：<br />![mark](http://qiniu.wind-zhou.com/blog/210124/AKk72Id6Gk.png?imageslim)<br /><br />![mark](http://qiniu.wind-zhou.com/blog/210124/igEC6Dd35F.png?imageslim) |
| *speed*    | 可选。<br /><br />规定动画的速度。可能的值：<br /><br />- 毫秒<br />- "slow"<br />- "fast" |
| *easing*   | 可选。<br /><br />规定在动画的不同点中元素的速度。<br /><br />默认值是 "swing"。<br /><br />可能的值：<br /><br />- "**swing**" - 在开头/结尾移动慢，在中间移动快<br /><br />- "**linear**" - 匀速移动<br /><br />**提示：**扩展插件中提供更多可用的 easing 函数。 |
| *callback* | 可选。<br /><br />animate 函数执行完之后，要执行的函数。<br /><br /> 如需学习更多有关 callback 的内容，请访问我们的 [jQuery Callback](https://www.runoob.com/jquery/jquery-callback.html) 这一章。 |

注：**只有数字值可创建动画**（比如 "margin:30px"）。字符串值无法创建动画（比如 "background-color:red"）。



**语法2：**

![mark](http://qiniu.wind-zhou.com/blog/210124/4degeJ8HiC.png?imageslim)



**示例1**：

使用animate实现中心放大效果

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .container {
            width: 200px;
            height: 300px;
            position: absolute;
            top: 200px;
            left: 400px;
            background: red;
        }
    </style>
</head>

<body>
    <button> 点击中心放大</button>

    <div class="container">


    </div>
</body>

<script>
    $(function() {
        $("button").click(function() {
            $(".container").animate({
                "width": "400px",
                "height": "500px",
                "left": "300px",
                "top": "100px",
            }, 1000)
        })
    })
</script>

</html>
```

![mark](http://qiniu.wind-zhou.com/blog/210124/Klf1G05m9m.gif)

**示例2：**

使用增量形式实现

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .container {
            width: 200px;
            height: 300px;
            position: absolute;
            top: 200px;
            left: 400px;
            background: red;
        }
    </style>
</head>

<body>
    <button> 点击中心放大</button>

    <div class="container">


    </div>
</body>

<script>
    $(function() {
        $("button").click(function() {
            $(".container").animate({
                "width": "+=200px",
                "height": "+=200px",
                "left": "-=100px",
                "top": "-=100px",
            }, 1000)
        })
    })
</script>

</html>
```

**示例3：**

使用css3实现

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .container {
            width: 200px;
            height: 300px;
            position: absolute;
            top: 200px;
            left: 400px;
            background: red;
            transition: all 1s;
        }
        
        .after {
            width: 300px;
            height: 400px;
            top: 150px;
            left: 350px;
        }
    </style>
</head>

<body>
    <button id="btn"> 点击中心放大</button>

    <div class="container">


    </div>
</body>

<script>
    document.getElementById("btn").onclick = function() {
        document.getElementsByClassName("container")[0].className = "container after"
    }
</script>

</html>
```



**示例4：**

变换之后通过callback函数改变颜色

```js
<script>
    $(function() {
        $("button").click(function() {
            $(".container").animate({
                "width": "+=200px",
                "height": "+=200px",
                "left": "-=100px",
                "top": "-=100px",
            }, 1000, function() {
                $(".container").css("backgroundColor", "green")
            })
        })
    })
</script>
```

![mark](http://qiniu.wind-zhou.com/blog/210124/1bLgaElLm5.gif)



**示例5：**

类似横幅拉出的效果

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .container {
            width: 300px;
            height: 300px;
            margin: 0 auto;
            border: 1px solid violet;
        }
        
        .move {
            width: 0px;
            height: 50px;
            background: red;
            float: right;
            white-space: nowrap;
            overflow: hidden;
            text-align: center;
        }
    </style>
</head>

<body>
    <button id="switch"> 开始</button>

    <div class="container">
        <div class="move">
            生活不止眼前的苟且，还有诗和远方！
        </div>

    </div>

    <button id="btn">停止</button>
</body>

<script>
    $(function() {
        $("#switch").click(function() {
            $(".move").animate({
                "width": "300px"
            }, 3000)
        })
    })
</script>

</html>
```



![mark](http://qiniu.wind-zhou.com/blog/210124/6biALdg1Ha.gif)





**示例6：**

实现增加时，从右往左增加

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .container {
            width: 300px;
            height: 300px;
            margin: 0 auto;
            border: 1px solid violet;
            position: relative;
        }
        
        .move {
            width: 150px;
            height: 50px;
            background: red;
            position: absolute;
            top: 125px;
            right: 125px;
        }
    </style>
</head>

<body>
    <button id="switch"> 开始</button>

    <div class="container">
        <div class="move">

        </div>

    </div>

    <button id="btn">停止</button>
</body>

<script>
    $(function() {
        $("#switch").click(function() {
            $(".move")
                .animate({
                    "width": "-=100px"
                }, 2000)
                .animate({
                    "width": "150px",
                    "right": "125px"
                }, 1000)
        })
    })
</script>

</html>
```



![mark](http://qiniu.wind-zhou.com/blog/210124/FH8BGmIdHl.gif)



默认都是沿x轴和y轴的正方向进行延伸。

![mark](http://qiniu.wind-zhou.com/blog/210124/JdJGbcglL7.png?imageslim)



这里只要将右侧卡死，则其不得不向左变化。使用`float：right`



**简单总结：**

| 动画方法               |                 改变的参数                  |
| :--------------------- | :-----------------------------------------: |
| hide()和show()         | **width、height、margin、padding、opacity** |
| fadeOut和fadeIn()      |                 **opacity**                 |
| slideUp()和slideDown() |                 **height**                  |
| animate()              |       **改变各种css属性（数值化的）**       |



## 动画队列

![mark](http://qiniu.wind-zhou.com/blog/210124/KBkHfa8Im3.png?imageslim)



**示例1：**

div先增加长度，再增加宽度，最后变颜色，然后再退回去。

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .container {
            width: 100px;
            height: 50px;
            margin: 0 auto;
            background: red;
        }
    </style>
</head>

<body>
    <button> 点击中心放大</button>

    <div class="container">


    </div>
</body>

<script>
    $(function() {
        $("button").click(function() {
            $(".container")
                .animate({
                    "width": "200px",
                }, 1000)
                .animate({
                    "height": "100px"
                }, 1000, function() {
                    $(".container").css("backgroundColor", "green")
                })
                .animate({
                    "height": "50px"
                }, 1000)
                .animate({
                    "width": "100px",
                }, 1000)

        })
    })
</script>

</html>
```



![mark](http://qiniu.wind-zhou.com/blog/210124/8672eCKfi5.gif)

**注：**上面动画中可以看到宽度增加时，是中心放大，这是因为css中设置了``margin：0 auto；``,这还真是意外收获。



**示例2：**

使用动画队列实现小方块的四角移动

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .container {
            width: 300px;
            height: 300px;
            margin: 0 auto;
            border: 1px solid violet;
            position: relative;
        }
        
        .move {
            position: absolute;
            left: 0;
            top: 0;
            width: 50px;
            height: 50px;
            background: red;
        }
    </style>
</head>

<body>
    <button> 点击中心放大</button>

    <div class="container">
        <div class="move">

        </div>
    </div>
</body>

<script>
    $(function() {
        $("button").click(function() {

            startMove();

            function startMove() {
                $(".move")
                    .animate({
                        "left": "250px"
                    }, 1000)
                    .animate({
                        "top": "250px"
                    }, 1000)
                    .animate({
                        "left": "0px"
                    }, 1000)
                    .animate({
                        "top": "0px"
                    }, 1000, startMove)
            }

        })
    })
</script>

</html>
```



![mark](http://qiniu.wind-zhou.com/blog/210124/i10CGk3lJl.gif)



**注**:这里实现一直运动是因为在一个周期结束后，在最后一个animate的callback函数又再次调用了这个函数（递归调用）



## 延迟动画队列 delay()

**作用**：delay() 方法对队列中的下一项的执行设置延迟。

**语法**：

```js
$(selector).delay()
```

delay()里参数可以是slow，fast，normal和毫秒。

**示例1：**

对上面例子进行改动，在第四部之前暂停2s

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1/jquery-3.5.1.min.js"></script>
    <style>
        .container {
            width: 300px;
            height: 300px;
            margin: 0 auto;
            border: 1px solid violet;
            position: relative;
        }
        
        .move {
            position: absolute;
            left: 0;
            top: 0;
            width: 50px;
            height: 50px;
            background: red;
        }
    </style>
</head>

<body>
    <button> 点击中心放大</button>

    <div class="container">
        <div class="move">

        </div>
    </div>
</body>

<script>
    $(function() {
        $("button").click(function() {

            startMove();

            function startMove() {
                $(".move")
                    .animate({
                        "left": "250px"
                    }, 1000)
                    .animate({
                        "top": "250px"
                    }, 1000)
                    .animate({
                        "left": "0px"
                    }, 1000)
                    .delay(2000)
                    .animate({
                        "top": "0px"
                    }, 1000, startMove)
            }
        })
    })
</script>

</html>
```

![mark](http://qiniu.wind-zhou.com/blog/210124/1c8Ce4KJaH.gif)



## 终止动画队列

![mark](http://qiniu.wind-zhou.com/blog/210124/ge04CH43BL.png?imageslim)



### 语法

```js
$(selector).stop(stopAll,goToEnd);
```

可选的 stopAll 参数规定是否应该清除动画队列。**默认是 false**，即仅停止活动的动画，允许任何排入队列的动画向后执行。

可选的 goToEnd 参数规定是否立即完成当前动画。**默认是 false**。

因此，默认地，stop() 会清除在被选元素上指定的当前动画。

下面的例子演示 stop() 方法，不带参数：

**示例1：**



```js
<!DOCTYPE html>
<html>
<head>
<script src="/jquery/jquery-1.11.1.min.js"></script>
<script> 
$(document).ready(function(){
  $("#flip").click(function(){
    $("#panel").slideDown(5000);
  });
  $("#stop").click(function(){
    $("#panel").stop();
  });
});
</script>
 
<style type="text/css"> 
#panel,#flip
{
padding:5px;
text-align:center;
background-color:#e5eecc;
border:solid 1px #c3c3c3;
}
#panel
{
padding:50px;
display:none;
}
</style>
</head>

<body>
 
<button id="stop">停止滑动</button>
<div id="flip">点击这里，向下滑动面板</div>
<div id="panel">Hello world!</div>

</body>
</html>

```

![mark](http://qiniu.wind-zhou.com/blog/210124/C2ICbbD8mC.gif)



注：这里只所以停止后又可以接上，是因为slidedown可以疾苦当前的位置。



**温馨提示：**

　　jQuery中的动画有show()、hide()、fadeIn()、fadeOut()、slideDown()、slideUp()、animate()等等。stop()方法对上述的动画都适用。

## 回调函数

jquery动画函数里面可以跟一个回调函数，表示动画结束后执行的代码

前面已经使用过。



**练习：**

使用animate简单实现一个轮播图

```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="./jquery-3.5.1.min.js"></script>
    <style>
        .show {
            width: 400px;
            height: 400px;
            border: 1px solid red;
            margin: 0 auto;
            overflow: hidden;
        }
        
        .img {
            width: 1600px;
            height: 400px;
            position: relative;
        }
        
        .img img {
            width: 400px;
            height: 400px;
            float: left;
        }
    </style>
</head>

<body>

    <div class="container">
        <div class="show">
            <div class="img">
                <img src="../js案例汇总/img/city.jpg" alt="">
                <img src="../js案例汇总/img/city2.jpg" alt="">
                <img src="../js案例汇总/img/city4.jpg" alt="">
                <img src="../js案例汇总/img/city3.jpg" alt="">
            </div>
        </div>

    </div>

</body>
<script>
    $(function() {
        function lbt() {
            var x = $(".img").css("left")

            if (parseInt(x) >= -800) {
                $(".img").animate({
                    "left": "-=400px"
                }, 500)
            } else {
                $(".img").animate({
                    "left": "0px"
                }, 500)
            }
        }

        setInterval(lbt, 2000)

    })
</script>

</html>
```






































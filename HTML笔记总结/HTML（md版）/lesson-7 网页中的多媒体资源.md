# lesson-7 网页中的多媒体资源

## 图片\<img>

**基本语法**：

```html
<img src="url" border="" width="" height="" align="" alt="" title="">
```

注：图片标记首先是一个单标记（空标记），但兼具行内标记和块级标记的特点。

**src和href的区别**：src是引入（拿过来），而href引用（过去）。

> 行内标记设置不了宽高。

| src    | 引入的源地址                                                 |
| ------ | ------------------------------------------------------------ |
| border | 设置边框的粗细（边框颜色无法改变）                           |
| width  | 设置宽度**（如果仅设置一项，那么图片会按原比例变化，<br />两个都不设置则按原大小输出）** |
| height | 设置高度（设置方式有百分比（父元素宽度的百分比）和像素单位两种设置方法） |
| align  | 设置对齐方式                                                 |
| title  | 鼠标划入时的提示信息                                         |
| alt    | 图片加载失败时的提示信息                                     |

**几点注意：**

- 虽然设置宽高时可以设置一个，但为了以后网页的维护，**需要把两个值都进行设置**（为了更换图片是不影响显示效果）
- 图片中使用align属性会导致img**脱离文档流**。**因此设置水平对齐可用center或用h（p也可以）标记处理。**

## 背景音乐

```html
<bgsound  src="url" loop="-1"> 
```

只有IE支持,且没有控件。

**不好意思，这个标记已被废弃！**

## Vedio视频

以前网页里插入视频是用 flash格式，但想播放视频浏览器必须有flash的插件。

>Flash扩展知识。
>

语法格式:

```html
<video src="url"></video>
```

**属性说明：**

| 属性     | 值       |                                                              |
| -------- | -------- | ------------------------------------------------------------ |
| controls | controls | 视频控制控件，比如播放按钮<br />经常会加一句话：“您当前浏览器不支持此视频，请升级你的浏览器” |
| autoplay | autoplay | 自动播放                                                     |
| height   | pixels   | 设置视频播放器的大小（但画面大小不变）                       |
| loop     | loop     | 循环播放                                                     |
| preload  | preload  | 预加载（视频预先缓存）                                       |
| src      | url      |                                                              |
| width    | pixels   | 设置视频播放器的高                                           |

为了是浏览器可以播放多种格式的视频，**可以再video里嵌套source标记**（前提是准备了多种格式的文件）。

>**如何嵌套source标记？**
>
>```js
>    <video width="602px" height="345px" controls="controls"> 
>
>        <source src="public/video/test.mp4" type="video/mp4"></source> 
>        
>        <source src="public/video/test.ogg" type="video/ogg"></source> 
>        
>        your browser does not support the video tag 
>        
>        </video>
>```
>
>
>
>

## Audio

```html
<audio src="url"></audio>
```

**audio标记和vedio的使用一模一样！**

>音频的格式，以及各个浏览器的支持。
>

## Canvas画布

***HTML5中最重要的也是功能最强大的！！！***

>如何理解Canvas画布？
>
>可以看做ps中的背景画布。

**Canvas作用**：

- 绘制图像
- 渲染文字
- 制作动画
- 制作游戏

canvas标记的**默认尺寸**是300*150px。

基本语法：

```html
<canvas width=""  height=""></canvas>
```

**说明**：canvas内容是通过canvas众多接口，由JS绘制。
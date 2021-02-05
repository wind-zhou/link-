# lesson-9表格与表单

## 控制表格

合并边框

基本语法：

`border-collapse：separate（分开）|collapse（合并）`

设置给table。这里设置边框合并和HTML中使用`cellpadding=“0”`不一样。HTML中设置使他们的边框挨在了一起，宽度加倍，而这里是直接合并，宽度只有一个边框的宽度。



**跨行跨列合并没有css，还是直接在属性里设置。**

设置表格隔行变色。

`tr:nth-child(odd){
				background-color: #A7995A;
			}`

设置划入变色

`	tr:hover{
				background-color:#00FFFF ;
			}`

练习

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			table{
				height: 500px;
				width: 400px;
				border-collapse: collapse;
				margin: 0 auto;
				border: #000000 1px solid;
				text-align: center;
			}
			td{
				border: #000000 1px solid;
			}
			tr:nth-child(odd){
				background-color: #A7995A;
			}
			tr:hover{
				background-color:#00FFFF ;
			}
		
		</style>
	</head>
	<body>
		<table >
			<tr>
				<td>1</td>
				<td>2</td>
				<td>3</td>
				<td>4</td>
			</tr>
			<tr>
				<td>1</td>
				<td>2</td>
				<td>3</td>
				<td>4</td>
			</tr>
			<tr>
				<td>1</td>
				<td>2</td>
				<td>3</td>
				<td>4</td>
			</tr>
			<tr>
				<td>1</td>
				<td>2</td>
				<td>3</td>
				<td>4</td>
			</tr>
			<tr>
				<td>1</td>
				<td>2</td>
				<td>3</td>
				<td>4</td>
			</tr>
		</table>
		
	</body>
</html>

```

效果：

![mark](http://qiniu.wind-zhou.com/blog/201115/1l8kd67meg.png?imageslim)

>注意：
>
>**要想使表格显示边框，不能只在table里设置边框，那只会设置表格外部的轮廓，要想使单元格显示边框应在td里单独设置边框。**



## 表单设置

**input输入框里的文字样式不能继承，需要单独设置。**

设置文本框内的光标右移，可以设置padding-left



单选按钮（复选按钮）只能设置大小（宽高），其他的边框颜色等设置不了，可以自己画一个假的把原按钮按住，再用js进行连接。



textarea的边框大小默认可以设置，但可以通过设置resize：none；禁止用户自己重置尺寸。





##练习

**写一个电子表单：**

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style type="text/css">
			
			*{
				margin: 0;
				padding: 0;
				
			}
			
			#header{
					height: 33px;
					background-color: #f7f7f7;
					font-size: 12px;
					color: #000000;
					padding-left: 16px;
					padding-top: 11px;
				
				}
			
			.con{
				display: inline-block;
			/* 	width: 80px; */
				text-align: right;
				font-size: 14px;
				width:150px;
				height: 14px;
				/* border:  #FF0000 1px dashed ; */   /*测试线*/
				margin-left: 131px;
				margin-right: 19px;
				color: #9c9c9c;
			}
			body{
				background-color: #f2f2f2;
			}
			form{
				background-color: #fff;
				width: 988px;
				height: 782px;
				border: #dddddd 1px solid;
				margin:32px auto 95px;  
			}
			
			p{
				/* border: #000000 1px solid; */   /*测试线*/
				
				margin:31px 0 ;
			}
			
			.inputSet{
				width: 268px;
				height: 34px;
				border: 1px #cbcbcb soild;
				outline:none;
				
				
				}
		
				span{  /*设置*的颜色*/
					color: #fc0400;
					
				}
				
				
				.address1{      /*设置公司所在地*/
					
						width:71px ;
						height: 32px;
						border: 1px #cccccc solid;
						margin-right:10px ;
					}
					
					.checkbox1{  /*设置复选框的间距*/
						/* border: #000000 1px solid; */
						margin-right: 15px;
						color: #323232;
						
					}
					.numberOfCompant{/*设置企业人数的select*/
					
						width: 89px;
						height:32px;
						outline: none;
						border: 1px #cccccc solid;

					}
					select[name=major]{  /*设置公司行业的select*/
						width: 311px;
						height: 32px;
						border: 1px #cccccc solid;
						
					}
					select[name=xingzhi]{  /*设置公司行业的select*/
						width: 145px;
						height: 32px;
						border: 1px #cccccc solid;
						
					}
					input[name=verification]{  /*设置公司行业的select*/
						width:130px;
						height: 32px;
						border: 1px #cccccc solid;
						outline: none;
						margin-right: 26px;
					}
					
					img{
						/* display: inline-block; */
						
						border: #000000 1px solid;
						margin-bottom: 3px;
						margin-right: 26px;
						vertical-align: bottom;  /*这里属实看不懂*/
					}
					
					a{
						color: #0000FF;
						text-decoration: none;
					}
					
					font{
						color: #323232;
					}
					.agreement{
						padding-left: 304px;
						}
						
						input[type=submit]{
							display: block;
							width: 270px;
							height: 36px;
							background-color:#e2393c ;
							border: 1px solid transparent;
							color: white;
							font-weight: bold;
							font-size: 15px;
							margin: 0 auto;
						
						}
				
		</style>
	</head>
	<body>
		<form action="#"  method="post">
			
			<div id="header">
				公司信息
			</div>
			<p>
				<label class="con  "><span>*</span>公司名称:</label>
				<input type="text" name="companyName" class="inputSet" />
			</p>
			<p>
				<label class="con "><span>*</span>公司所在地:</label>
		
			<select name="city1" class="address1">
				<option value="HZ">请选择</option>
				<option value="JS">江苏</option>
			</select>
			
			<select name="city2"  class="address1">
				<option value="HZ">请选择</option>
				<option value="JS">江苏</option>
			</select>
			
			<select name="city3"  class="address1">
				<option value="HZ">请选择</option>
				<option value="JS">江苏</option>
			</select>
		</p>
		
		<p>
			<label class="con "><span>*</span>公司地址:</label>
			<input type="text" name="address" class="inputSet" />
		</p>
		<p>
			<label class="con "><span>*</span>购买类型和用途</label>
			
				
			
			<label class="checkbox1"><input type="checkbox" name="content2"  />IT设备</label>
			<label class="checkbox1"><input type="checkbox" name="content2"  />数码通讯</label>
			<label class="checkbox1"><input type="checkbox" name="content3"  />办公用品耗时</label>
			<label class="checkbox1"><input type="checkbox" name="content4"  />大家电</label>
			<label class="checkbox1"><input type="checkbox" name="content5"  />项目合作-政府采购</label>
			<label class="checkbox1"><input type="checkbox" name="content6"  />礼品</label><br><br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
			&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
		
			<label class="checkbox1"><input type="checkbox" name="content7"  />商旅(机票/酒店)</label>
			
		</p>
		<p>
			<label class="con">负责销售:</label>
			<input type="text" name="sell" class="inputSet" />
		</p>
		<p>
			<label class="con">企业人数:</label>
			<select name="number" class="numberOfCompant">
				<option value="a" selected="selected">50-99</option>
				<option value="b">0-50</option>
			</select>
		</p>
		
		<p>
			<label class="con ">公司行业:</label>
			<select name="major">
				<option value="c" selected>计算机软件</option>
				<option value="d" >设计</option>
			</select>
		</p>
		<p>
			<label class="con">公司性质:</label>
			<select name="xingzhi" size="1">
				<option value="e" selected="selected" disabled="disabled">请选择</option>
				<option value="f">传销</option>
			</select>
		</p>
		<p >
			<label class="con "><span>*</span>验证码:</label>
			<input type="text" name="verification" />  
			<img src="../Verification.png" >
			<span >
				<font>看不清？</font><a href="#">换一张</a>
			</span>
		</p>          
		<p class="agreement">                 
			<label>
				<input type="checkbox" name="www" checked="checked" value="yes" />我已阅读并同意<a href="#">《京东用户注册协议》</a>
			</label>
		</p>
			<p>
				<input type="submit"  value="立即注册"/>
			</p>
		</form>
	</body>
</html>
```

![mark](http://qiniu.wind-zhou.com/blog/201117/d978aamh8j.png?imageslim)
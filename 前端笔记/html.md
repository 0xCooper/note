- **<!DOCTYPE html>** 声明为 HTML5 文档
- **<html>** 元素是 HTML 页面的根元素
- **<head>** 元素包含了文档的元（meta）数据，如 <meta charset="utf-8"> 定义网页编码格式为 **utf-8**。
- **<title>** 元素描述了文档的标题
- **<body>** 元素包含了可见的页面内容
- **<h1>** 元素定义一个大标题
- **<p>** 元素定义一个段落

<!-- 这是一个注释 -->

```bash
<h1 align="left|center|right|justify"> 
一号标题</h1>
align用来标识其标题文字的对齐方式

--------特殊符号代码--------
&nbsp来添加空格
&lt    <
&amp   &
&gt	   >
&times x(乘号)
&divide  除号
&quot  双引号
&cope  版权
&reg   注册商标
--------------------------
<code></code>计算机代码
<font color="" size="" face="黑体">


设置图像对其方式
<img src="URL" align="value">
top,middle,bottom,left,center,right


滚动文字
marquee
<marquee width="" height="" bgcolor="" dirction="up|down|left|right" behavior="scroll|slide|alternate"
hspace=""
vspace=""
scrollamount=""
scrolldelay=""
onMouseOver="this.stop()"
onMouseOver="this.start()"
> </marquee>

scroll  循环往复滚动
slide   滚动一次，然后停止
alternate  来回交替滚动
<marquee scrollamount="滚动速度" scrolldelay="延迟时间"
>   滚动内容 <marquee>


<img src="" hspace="水平间距" vspace="垂直间距"   >


<p align="center"><a href="">
<img border="0" src="">
</a>
</p>


文本输入框
<p>
<input type="text" size="60" name=" "  >
<input tytpe="button" name="baidu"  value="百度一下">
</p>

<ol>有序列表
	<li>cooffee</li>
	<li>tea</li>
	<li>milk</li>
</ol>

<ul>无序列表
	<li>dada</li>
	<li>momo</li>
</ul>


<style type=text/css"">
	img{width:100px;height:100px;border:2px  #cc0066 ridge }
ul{list-style-type:none;}
li{float:left;}
</style>

```



## 替换文本属性（Alt）

alt 属性用来为图像定义一串预备的可替换的文本。替换文本属性的值是用户定义的。

```
<img src="boat.gif" alt="Big Boat">
```

在浏览器无法载入图像时，替换文本属性告诉读者她们失去的信息。此时，浏览器将显示这个替代性的文本而不是图像。为页面上的图像都加上替换文本属性是个好习惯，这样有助于更好的显示信息，并且对于那些使用纯文本浏览器的人来说是非常有用的


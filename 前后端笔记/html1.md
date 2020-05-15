```
html标准样式
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>页面标题</title>
</head>
<body>
</body>
</html>
```

```
添加链接
<img src=""  width=""  height=""/>
<a href=""></a>
```

```
属性
class  为html元素定义一个类名  class=""  内部可以引入多个属性
id    第一元素的唯一一个id
style   规定行内样式
title
align   align="center"  对齐方式
```

```
规范
<br> 进行换行
```

```
表格制作
1.table 标签
<table  width="500" border="1"  align="center"  cellpspacing="0"  cellpadding="0" >
<caption></caption>           定义表格元素标题
<th></th>用于表头
2.表的结构
<tr>  <!--tr用于一行-->
		<td></td>
</tr>
3.合并单元格
<td colspan="2"> </td>         此时的单元格是占两个横着的位置
<td rowspan="2"> </td>         此时的单元格是占两个竖着的位置
4.表单
<input/>  单标签 
	4.1 input 属性
		type  name value内部值 size checked 
		<input type ="text"/>输入框
		<input type="radio"  name="" />单选框
还有checkbox 多选  button submit reset 普通按钮
5.label标签，用于绑定
属性 for
<lable for="pwd">用户名：<input type="text" >
				 密码：<input type="text" id=pwd>
</lable>
6.textarea控件 双标签
<textarea cos=""  rows="" >	</tectarea>
7.下拉菜单
<select  name=""  id="">
<option vlues="">   选择年份</option>
<option vlues="">  1991</option>
<option vlues="">   1992 </option>
</select>
8.表单域
<form action="demo.php" method="get/post"   >action把表单的内容送到服务器 post提交不会显示在url   
</form>


```

  

```html
html与css的关系

案例1. 实现改变形态
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Html和CSS的关系</title>
        <style type="text/css">
        h1{
            font-size:12px;
            color:#930;
            text-align:left;
        }
        </style>
    </head>
    <body>
        <h1>Hello World!</h1>
    </body>
</html>
案例2.  实现局部变色
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>CSS样式的优势</title>
    <style type="text/css">
    span {
        color: blue;
    }
    </style>
</head>
<body>
    <p>慕课网，<span>超酷的互联网</span>、IT技术免费学习平台，创新的网络一站式学习、实践体验；<span>服务及时贴心</span>，内容专业、<span>有趣易学</span>。专注服务互联网工程师快速成为技术高手！</p>
</body>
</html>
```



```
插入视频
<body>
	<iframe height=498 width=510 src='http://player.youku.com/embed/XMzIzNTc0MTAwMA==' frameborder=0 'allowfullscreen'></iframe>
</body>
```



```
<base>标签  单标签
		可以通过 href 与target设置全局属性 在head 里面设置
	`	把<base>标签放在head的第一个元素和head中的元素也可以应用
class属性
	定义上style中的类别，然后在body中引用
	target属性 可以控制标签是否在新的页面打开
	类选择器的使用在<style type="text/css">中 如h1.s(s即为类名)
```

```

```

```html
<!--实现点击显性-->
<!DOCTYPE HTML>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=gb2312">
<title>宽度和高度</title>
<style type="text/css">
li{
    border-bottom:1px dotted #ccc;
    width:200px;height:30px;
}
li{ text-shadow: 0 0 80px #000; 
    color: rgba(255,255,255,0);
    transition: text-shadow 1s, color 1s;
}
li:hover{
    text-shadow: 0 0 1px #000; 
    color:#000;
    transition: text-shadow 1s, color 1s;
}
</style>
</head>
<body>
<ul>
    <li>别让不会说话害了你</li>
    <li>二十七八岁就应该有的见识</li>
    <li>别让不好意思害了你</li>
</ul>
<p>碰下上面的那一团个试试=w=</p>
</body>
</html>
```




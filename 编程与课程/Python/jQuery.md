jQuery 语法是通过选取 HTML 元素，并对选取的元素执行某些操作。

基础语法： **$(\*selector\*).\*action\*()**

 jQuery 函数位于一个 document ready 函数中：

```

$(document).ready(function(){
 
   // 开始写 jQuery 代码...
 
});

```

jQuery 中所有选择器都以美元符号开头：$()。



```
<script>
$(document).ready(function(){
  $("button").click(function(){
    $("p").hide();
  });
});
</script>
</head>

<body>
<h2>这是一个标题</h2>
<p>这是一个段落。</p>
<p>这是另一个段落。</p>
<button>点我</button>
</body>
</html>
```

##  #id 选择器

jQuery #id 选择器通过 HTML 元素的 id 属性选取指定的元素。

页面中元素的 id 应该是唯一的，所以您要在页面中选取唯一的元素需要通过 #id 选择器。

通过 id 选取元素语法如下：

$("#test")

```
<script>
$(document).ready(function(){
  $("#button1").click(function(){
    $("#test").hide();
  });
});
</script>
```

##  .class 选择器

jQuery 类选择器可以通过指定的 class 查找元素。

语法如下：

$(".test")

```

$(document).ready(function(){
  $("button").click(function(){
    $(".test").hide();
  });
});

```





```
<script>
$(document).ready(function(){
  $("#btn1").click(function(){
    $("p").append(" <b>追加文本</b>。");
  });

  $("#btn2").click(function(){
    $("ol").append("<li>追加列表项</li>");
  });
});
</script>
```

#### 开头添加

```
$(document).ready(function(){
	$("#btn1").click(function(){
		$("p").prepend("<b>在开头追加文本</b>。 ");
	});
	$("#btn2").click(function(){
		$("ol").prepend("<li>在开头添加列表项</li>");
	});
});
```

#### 获取输入框的值

```
txt=$("input").val();
```

```
<script>
$(document).ready(function(){
	$("button").click(function(){
		txt=$("input").val();
		$.post("demo_ajax_gethint.php",{suggest:txt},function(result){
			$("span").html(result);
		});
	});
});
</script>
</head>
<body>
<button> 点击</button>
<p>在以下输入框中输入名字:</p>
第一个名称:
<input type="text" />
<p>匹配项: <span></span></p>
<p>该实例的PHP代码 (<a href="demo_ajax_gethint.txt" target="_blank">demo_ajax_gethint</a>) </p>

</body>
</html>
```

获取当前点击的id

```
<script>
$(document).ready(function(){
  $("button").click(function(){
  	var id=$(this).attr('id')
    alert($("#runoob").attr("href"));
  });
});
</script>
```



```
<script>
$(document).ready(function(){
  $("button").click(function(){
    alert($("#runoob").attr("href"));
  });
});
</script>
```



点击按钮 按钮发起git或post然后执行然后返回当前页面

#### 暂停执行

```
1、3秒钟后提示警告框，只执行一次
setTimeout(function(){
alert("ok");
},3000);
2、每隔三秒钟提示警告框，反复执行
setInterval(function(){
alert("ok");
},3000);
```


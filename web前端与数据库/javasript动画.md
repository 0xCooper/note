```
1.最简单的欢迎
<button type="button" onclick="alert('欢迎')" ></button>
```

```
改变html内容
x=document.getElementById("demo");  //查找元素
x.innerHTML="Hello JavaScript";    //改变内容
```

```
改变样式
function myFunction()
{
	x=document.getElementById("demo") // 找到元素
	x.style.color="#ff0000";          // 改变样式
}
```

```
script实现切换多张图片

<script>
		var i = 1;
		function nextImg(){
			i++;
			var next = document.getElementById("nImg");
			next.src = "img/pic"+i+".jpg";
			if(i==3){
				i=0;
			} 
		}
</script>
```


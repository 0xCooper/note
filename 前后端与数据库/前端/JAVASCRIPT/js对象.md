```js
var person = {
    firstName:"John",
    lastName:"Doe",
    age:50,
    eyeColor:"blue",
    id:123
};
```

```js
var person = {
    firstName: "John",
    lastName : "Doe",
    id : 5566,
     a : function() 
	{
       return this.firstName + " " + this.lastName;
    }
};
```

对象输入函数

```js
document.getElementById("demo1").innerHTML = "不加括号输出函数表达式："  + person.a;
document.getElementById("demo2").innerHTML = "加括号输出函数执行结果："  +  person.a();
```

执行js时会输出文本在 id的位置

```js
<p id="demox"></p>
```


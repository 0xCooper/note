```vue
var vm = new Vue({
  // 选项
})

<div id="app">
  <p>{{ message }}</p>
</div>

<script>
new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue.js!'
  }
})
</script>
```

```vue




<script type="text/javascript">
		var vm = new Vue({
			el: '#vue_det',
			data: {
				site: "菜鸟教程",
				url: "www.runoob.com",
				alexa: "10000"
			},
			methods: {
				details: function() {
					return  this.site + " - 学的不仅，更是梦想！";
				}
			}
		})
	</script>
```

if语句

```vue
<div id="app">
    <p v-if="seen">现在你看到我了</p>
    <template v-if="ok">
      <h1>菜鸟教程</h1>
    </template>
</div>
    
<script>
new Vue({
  el: '#app',
  data: {
    seen: true,
    ok: false
  }
})
</script>
```

点击按钮调用函数

```vue
<div id="app">
   <!-- `greet` 是在下面定义的方法名 -->
  <button v-on:click="greet">Greet</button>
</div>

<script>
var app = new Vue({
  el: '#app',
  data: {
    name: 'Vue.js'
  },
  // 在 `methods` 对象中定义方法
  methods: {
    greet: function (event) {
      // `this` 在方法里指当前 Vue 实例
      
      // `event` 是原生 DOM 事件
	  if (event) {
		  alert(event.target.tagName)
	  }
    }
  }
})
```



想实现功能 






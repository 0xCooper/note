`view-sources`查看源代码
`get  post` 传值
`robots.txt协议`
`index.php的备份文件名``index.php.bak`
`cookie`F12打开调试器，然后查看消息头与返回的响应可能存在
不能按下的按钮，利用post进行传值或者删除不能按下的属性
一直输不对的密码框

```
浏览器工具f12的用法
https://blog.csdn.net/m0_37724356/article/details/79884006

浏览器开发者工具的使用imooc上的·视频
https://www.imooc.com/learn/759


cookie的基础知识
https://www.cnblogs.com/huchong/p/8481779.html



在f12中的application可以看到cookie的

查看cookie的值

1.在浏览器的地址栏中输入 JavaScript：alert（doucument.cookie）(不区分大小写)就会弹出你当前网页登录的cookie信息

由于浏览器会将JavaScript屏蔽，建议复制以下的文本然后再讲1去除。
1javascript:alert(document.cookie) 

2.按下F12进入开发者模式 console 在命令行中在输入刚刚的JavaScript：alert（document。cookie）

cookie的组成
（1） name/value 设置cookie的名称及对应的值
（2） expires属性：设置cookie的生存期，有两种储存类型的cookie:
会话性与持久性
（3）path属性：定义了web站点上可以访问该cookie的目录//问题：如果不能访问该cookie，客户端岂不是就不能访问，就必须要就行再登录？
（4）Domain属性：指定了可以访问该cookie的web站点或域
（5）secure属性：指定是否使用HTTPS安全协议发送cookie，使用HTTPS安全协议，可以更有效的保护cookie不会被窃取
（6）HTTPonly 属性：用于防止客户端脚本通过document。cookie属性访问cookie
有助于保护cookie不被跨站脚本攻击窃取与篡改，（但是，HTTPOnly的应用仍存在局限性，一些浏览器可以阻止客户端脚本对Cookie的读操作，但允许写操作；此外大多数浏览器仍允许通过XMLHTTP对象读取HTTP响应中的Set-Cookie头 ）后面这段不是很懂


安全威胁


cookie捕获

恶意cookies
会话置顶




//详细见百度百科
https://baike.baidu.com/item/cookie/1119?fr=aladdin
```


参考教程

```
https://blog.csdn.net/kclax/article/details/91353595
```



#### xss(跨站脚本攻击)

漏洞发生在服务端，攻击是在浏览器


分为四部 

1.攻击者将恶意代码注入到服务器
2.用户在没有防备的情况下访问了服务器
3.服务器将含有恶意代码的网页响应给客户端
4.在客户端浏览器中触发恶意js代码

```
WAMP集成环境包  php +mysql +apache
```

常用测试脚本

```
<script>alert("1")</script>
<svg><h1/a="'>
<img/src=1 onerror=alert(1)>
```

流量劫持,实现恶意跳转

```
<script>window.location.href="http://www.baidu.com";</script>
```


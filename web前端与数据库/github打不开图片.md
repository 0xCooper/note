# [github图片打不开解决方案](https://www.cnblogs.com/geektcp/p/12417206.html)



github界面的图片打不开的原因是域名污染

修改windows下的host文件

C:\Windows\System32\drivers\etc\hosts

或者linux下host文件

/etc/hosts

添加如下一行：

```
[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

199.232.28.133 raw.githubusercontent.com
199.232.68.133 gist.githubusercontent.com
199.232.28.133 cloud.githubusercontent.com
199.232.28.133 camo.githubusercontent.com
199.232.28.133 avatars0.githubusercontent.com
199.232.68.133 avatars1.githubusercontent.com
199.232.28.133 avatars2.githubusercontent.com
199.232.68.133 avatars3.githubusercontent.com
199.232.68.133 avatars4.githubusercontent.com
199.232.68.133 avatars5.githubusercontent.com
199.232.68.133 avatars6.githubusercontent.com
199.232.68.133 avatars7.githubusercontent.com
199.232.68.133 avatars8.githubusercontent.com

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 
```

大功告成，重启浏览器，打开github。。。
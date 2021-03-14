##  安装 酷Q on Dockers

1.下载 酷Q Docker 镜像：

```
docker pull coolq/wine-coolq
```

2.创建一个文件夹，用来存放 酷Q 数据：

```
mkdir /root/coolq-data
```

3.运行 酷Q：

```
docker run --name=coolq -d -p 8080:9000 -v /root/coolq-data:/home/user/coolq -e VNC_PASSWD=12345678 -e COOLQ_ACCOUNT=10000 coolq/wine-coolq
```

这个命令里有几个参数，可以自定义：

| **参数含义** | **参数示例**     |
| ------------ | ---------------- |
| 远程监听端口 | 8080             |
| 数据存放位置 | /root/coolq-data |
| 远程访问密码 | 12345678         |
| 机器人帐号   | 123456           |

至此，你的 酷Q 就成功安装了，可以直接访问 你的IP:8080 打开 VNC 操作 酷Q 了。

库区社区账号

| -酷q社区账号 | -密码    |
| ------------ | -------- |
| myc20200502  | qwer1234 |



修改密码应该可以通过passwd命令来修改密码



添加功能

服务器状态
在线运行代码

加群提醒

百度
消息转发

![](https://imgc.cqp.me/forum/201908/24/164539t76w88zmcc8btvtm.png)



![](https://www.baidu.com/img/dong_f6764cd1911fae7d460b25e31c7e342c.gif)


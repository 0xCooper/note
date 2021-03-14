```cmd
for /l %i in (1,1,254) do ping -n 1  -w 30 192.168.9.%i >>d:\pinglog.txt
//平通整个网段
@for /l %i in (1,1,255) do @ping -n 1 -w 40 192.168.1.%i & if errorlevel 1 (echo 192.168.1.%i>>na.txt) else (echo 192.168.1.%i>>act.txt)
```

```
1. ping 命令
测试网络联接状况以及信息包发送和接收状况。但是不能够测试端口。
语法：ping IP地址或主机名 [-t] [-a] [-n count] [-l size]
参数含义：
-t 不停地向目标主机发送数据；
-a 以IP地址格式来显示目标主机的网络地址；
-n count 指定要Ping多少次，具体次数由count来指定；
-l size 指定发送到目标主机的数据包的大小。
Sample: ping 192.168.0.1 -t (不停的测试192.168.0.1，按ctrl+c停止)
Sample: for /L %%a in (0,1,255) do ping 192.168.0.%%a -n 1 >> tmp.txt (ping一下所有的局域网电脑)
```


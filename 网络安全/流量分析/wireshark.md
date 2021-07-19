**linux上用命令行进行抓包**

```bash
[root@bass Desktop]# tcpdump -i eth0 -w dump.pcap
-i #是指定要抓取的网卡
-w #指定结果保存的位置
```

## 1.wireshark过滤

```

```

### **协议过滤**

- **TCP：**只显示TCP协议的数据流
- **HTTP：**只显示HTTP协议的数据流
- **ICMP：**只显示ICMP协议的数据流
- **ARP：**只显示ARP协议的数据流
- **DNS：**显示DNS协议的数据流

### **IP过滤**

- **ip.addr = 192.168.116.138**，只显示ip为192.168.116.138有关的数据流
- **ip.src = 192.168.116.138**，只显示源IP地址为192.168.116.138的数据流
- **ip.dst = 192.168.116.138**，只显示目标IP地址为192.168.116.138的数据流

### **端口过滤**

- **tcp.port == 80**，只显示80端口TCP数据流
- **udp.prot == 67**，只显示67端口UDP数据流
- **tcp.srcport == 80**, 只显示源地址的80端口数据流
- **tcp.dstport == 80，**只显示目的地址80端口数据流

### **过滤HTTP协议**

- **http.request.method=="GET"**，显示get请求
- **http.request.method=="POST"** ，显示POST请求
- **http.request.url contains admin** ，显示url中包含admin的 请求
- **http.request.code==404**，显示状态码为404

### **连接符**

and，or

如tcp.port == 80 and ip.addr = 192.168.116.138

筛选http Get传参与Post传参包

```
http.request.method==GET
http.request.method==POST
```

查找字符串

```
http contains "POST" #在http头中查找http头
```

https流量交互过程



找地址

```
http.request.uri == “path”或 http.request.uri contains “path”
```


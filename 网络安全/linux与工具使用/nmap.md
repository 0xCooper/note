##### nmap的扫描类型

nmap -sP:以ping的方式进行扫描

```
nmap -sP 192.168.1.0/24
```



```
适合局域网内扫描ip存在
```

nmap -sS TCP syn扫描

##### 扫描选项

-v:显示扫描过程
-sV 版本探测

-O:识别远程操作系统
-p:指定端口 80 ，443，3389

```
nmap -sP IP/24(网段) -oG nmap.txt
将扫描结果保存在文件中
nmap -iL ip.txt 扫描文本中的ip
```

```
nmap -traceroute 101.200.46.43
```

```
nmap -O 101.200.46.43 探测操作系统

```


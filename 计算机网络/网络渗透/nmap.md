##### nmap的扫描类型

nmap -sP:以ping的方式进行扫描

```
适合局域网内扫描ip存在
```

nmap -sS TCP syn扫描

##### 扫描选项

-v:显示扫描过程
-O:识别远程操作系统
-p:指定端口 80 ，443，3389

```
nmap -sP IP/24(网段) -oG nmap.txt
将扫描结果保存在文件中
```


1.查看操作系统版本

```
输入"uname -a ",可显示电脑以及操作系统的相关信息。 

cat /proc/version 说明正在运行的内核版本

cat /etc/issue  说明发行商版本

lsb_release -a (适用于所有的linux，包括Redhat、SuSE、Debian等发行版，但是在debian下要安装lsb)
```

2.查看硬件信息

```
cat /proc/cpuinfo 
lscpu
cat /proc/meminfo #查看内存信息

```

```
lsof - list open files, UNIX一切皆文件
lsof -p PID
```


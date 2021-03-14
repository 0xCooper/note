```
osts所在文件夹：

    Windows 系统hosts位于 C:\Windows\System32\drivers\etc\hosts
    Android（安卓）系统hosts位于 /etc/hosts
    Mac（苹果电脑）系统hosts位于 /etc/hosts
    iPhone（iOS）系统hosts位于 /etc/hosts
    Linux系统hosts位于 /etc/hosts
    绝大多数Unix系统都是在 /etc/hosts





#
Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost
如果你怀疑你的hosts文件 被病毒 木马修改，可复制以上内容修复hosts 文件。
值得一提的是#后都是注释，所以清空hosts文件对系统正常运行并没有什么影响。 

```

```
host文件作用
1、加快域名解析
对于要经常访问的网站，我们可以通过在Hosts中配置域名和IP的映射关系，提高域名解析速度。由于有了映射关系，当我们输入域名计算机就能很快解析出IP，而不用请求网络上的DNS服务器。
2、方便局域网用户
在很多单位的局域网中，会有服务器提供给用户使用。但由于局域网中一般很少架设DNS服务器，访问这些服务器时，要输入难记的IP地址。这对不少人来说相当麻烦。可以分别给这些服务器取个容易记住的名字，然后在Hosts中建立IP映射，这样以后访问的时候，只要输入这个服务器的名字就行了。
3、屏蔽网站（域名重定向）
有很多网站不经过用户同意就将各种各样的插件安装到你的计算机中，其中有些说不定就是木马或病毒。对于这些网站我们可以利用Hosts把该网站的域名映射到错误的IP或本地计算机的IP，这样就不用访问了。在WINDOWS系统中，约定 127.0.0.1 为本地计算机的IP地址, 0.0.0.0是错误的IP地址。
如果，我们在Hosts中，写入以下内容：
127.0.0.1要屏蔽的网站A的域名
0.0.0.0要屏蔽的网站B的域名
这样，计算机解析域名A和 B时，就解析到本机IP或错误的IP，达到了屏蔽网站A 和B的目的。
4、顺利连接系统
对于Lotus的服务器和一些数据库服务器，在访问时如果直接输入IP地址那是不能访问的，只能输入服务器名才能访问。那么我们配置好Hosts文件，这样输入服务器名就能顺利连接了。
5.虚拟域名
很多时候，网站建设者需要把”软环境“搭建好，再进行上传调试。但类似于邮件服务，则需要使用域名来辅助调试，这时就可以将本地 IP 地址与一个”虚拟域名“做地址指向，就可以达到要求的效果，且无需花费。如：
　　127.0.0.1 网站域名
　　之后在浏览器地址栏中输入对应的网站域名即可。
```

本机hosts文件信息
翻译

```
*35；版权所有（c）1993-2009 Microsoft Corp.

IT35；

这是Microsoft TCP/IP for Windows使用的示例主机文件。

IT35；

此文件包含IP地址到主机名的映射。每个

*35；输入应保持在单独的行上。IP地址应该

*35；放在第一列，后跟相应的主机名。

IP地址和主机名应至少用一个分隔

空间.35；

IT35；

此外，可以在个人身上插入注释（如这些注释）

*35行或在机器名之后，用35；符号表示。

IT35；

例如：

IT35；

*35；102.54.94.97 rhino.acme.com 35；源服务器

.3538.25.63.10 x.acme.com.35；x客户端主机



本地主机名解析在DNS本身中处理。

；127.0.0.1本地主机

：1本地主机
```


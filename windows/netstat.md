命令中各选项的含义如下：
-a 显示所有socket，包括正在监听的。
　　-c 每隔1秒就重新显示一遍，直到用户中断它。
　　-i 显示所有网络接口的信息，格式“netstat -i”。
　　-n 以网络IP地址代替名称，显示出网络连接情形。
　　-r显示核心路由表，格式同“route -e”。
　　-t 显示TCP协议的连接情况
　　-u 显示UDP协议的连接情况。
　　-v 显示正在进行的工作。
　　-p 显示建立相关连接的程序名和PID。
　　-b 显示在创建每个连接或侦听端口时涉及的可执行程序。
　　-e 显示以太网统计。此选项可以与 -s 选项结合使用。
　　-f 显示外部地址的完全限定域名(FQDN)。
　　-o显示与与网络计时器相关的信息。
-s 显示每个协议的统计。
　　-x 显示 NetworkDirect 连接、侦听器和共享端点。
　　-y 显示所有连接的 TCP 连接模板。无法与其他选项结合使用。
　　interval 重新显示选定的统计，各个显示间暂停的 间隔秒数。按 CTRL+C 停止重新显示统计。如果省略，则 netstat 将打印当前的配置信息一次。
列标题
Name接口的名字
Mtu 接口的最大传输单位
Net/Dest 接口所在的网络
Address 接口的IP地址
Ipkts 接收到的数据包数目
Ierrs 接收到时已损坏的数据包数目
Opkts 发送的数据包数目
Oeers 发送时已损坏的数据包数目
Collisions 由这个接口所记录的网络冲突数目
常用选项
netstat -a
——本选项显示一个所有的有效连接信息列表，包括已建立的连接（ESTABLISHED），也包括监听连接请求（LISTENING）的那些连接。
netstat -b
该参数可显示在创建网络连接和侦听端口时所涉及的可执行程序。
netstat -s
——本选项能够按照各个协议分别显示其统计数据。如果你的应用程序（如Web浏览器）运行速度比较慢，或者不能显示Web页之类的数据，那么你就可以用本选项来查看一下所显示的信息。你需要仔细查看统计数据的各行，找到出错的关键字，进而确定问题所在。
netstat -e
——本选项用于显示关于以太网的统计数据，它列出的项目包括传送数据报的总字节数、错误数、删除数，包括发送和接收量（如发送和接收的字节数、数据包数 [1]  ），或有广播的数量。可以用来统计一些基本的网络流量。
netstat -r
——本选项可以显示关于路由表的信息，类似于后面所讲使用routeprint命令时看到的信息。除了显示有效路由外，还显示当前有效的连接。
netstat -n
——显示所有已建立的有效连接。
netstat -p
——显示协议名查看某协议使用情况
常见状态
编辑
即连接状态。在原模式中没有状态，在用户数据报协议中也经常没有状态，于是状态列可以空出来。若有状态，通常取值为：
LISTEN
侦听来自远方的TCP端口的连接请求
SYN-SENT
在发送连接请求后等待匹配的连接请求
SYN-RECEIVED
在收到和发送一个连接请求后等待对方对连接请求的确认
ESTABLISHED
代表一个打开的连接
FIN-WAIT-1
等待远程TCP连接中断请求，或先前的连接中断请求的确认
FIN-WAIT-2
从远程TCP等待连接中断请求
CLOSE-WAIT
等待从本地用户发来的连接中断请求
CLOSING
等待远程TCP对连接中断的确认
LAST-ACK
等待原来的发向远程TCP的连接中断请求的确认
TIME-WAIT
等待足够的时间以确保远程TCP接收到连接中断请求的确认
CLOSED
没有任何连接状态
命令示例
编辑
该命令（Winxp下）的一般格式为 ：
C:\>netstat /?
显示协议统计信息和当前 TCP/IP网络连接。
NETSTAT [-a] [-b] [-e] [-n] [-o] [-p proto] [-r] [-s] [-v]
-a 显示所有连接和监听端口。
-b 显示包含于创建每个连接或监听端口的可执行组件。在某些情况下已知可执行组件
拥有多个独立组件，并且在这些情况下包含于创建连接或监听端口的组件序列被显示。
这种情况下，可执行组件名在底部的 [] 中，顶部是其调用的组件，等等，直到 TCP/IP
部分。注意此选项可能需要很长时间，如果没有足够权限可能失败。
-e 显示以太网统计信息。此选项可以与 -s选项组合使用
-n 以数字形式显示地址和端口号。 此选项可以与 -a选项组合使用
-o 显示与每个连接相关的所属进程 ID。
-p proto 显示 proto 指定的协议的连接；proto 可以是
下列协议之一: TCP、UDP、TCPv6 或 UDPv6。
如果与 -s 选项一起使用以显示按协议统计信息，proto 可以是下列协议之一:
IP、IPv6、ICMP、ICMPv6、TCP、TCPv6、UDP 或 UDPv6。
-r 显示路由表。
-s 显示按协议统计信息。默认地，显示 IP、
IPv6、ICMP、ICMPv6、TCP、TCPv6、UDP 和 UDPv6 的统计信息；
-p 选项用于指定默认情况的子集。
-v 与 -b 选项一起使用时将显示包含于为所有可执行组件创建连接或监听端口的组件
interval 重新显示选定统计信息，每次显示之间
暂停时间间隔(以秒计)。按 CTRL+C 停止重新
显示统计信息。如果省略，netstat 显示当前
配置信息(只显示一次)
该命令（Win2000下）的一般格式为 ：
C:\>netstat /?
Displays protocol statistics and current TCP/IP network connections.
NETSTAT [-a] [-e] [-n] [-s] [-p proto] [-r]
-a Displays all connections and listening ports.
-e Displays Ethernet statistics. This may be combined with the -s
option.
-n Displays addresses and port numbers in numerical form.
-p proto Shows connections for the protocol specified by proto; proto
may be TCP or UDP. If used with the -s option to display
per-protocol statistics, proto may be TCP, UDP, or IP.
-r Displays the routing table.
-s Displays per-protocol statistics. By default, statistics are
shown for TCP, UDP and IP; the -p option may be used to specify
a subset of the default.
interval Redisplays selected statistics, pausing interval seconds
between each display. Press CTRL+C to stop redisplaying
statistics. If omitted, netstat will print the current
configuration information once
微软公司故意将这个功能强大的命令隐藏起来是因为它对于普通用户来说有些复杂。我们已经知道：Netstat它可以用来获得你的系统网络连接的信息（使用的端口，在使用的协议等 ），收到和发出的数据，被连接的远程系统的端口，Netstat在内存中读取所有的网络信息。
实录
用实例详细的解释一下各个参数的使用：
C:\>netstat -a
Active Connections
Proto Local Address Foreign Address State
TCP Eagle:ftp Eagle:0 LISTENING
TCP Eagle:telnet Eagle:0 LISTENING
TCP Eagle:smtp Eagle:0 LISTENING
TCP Eagle:http Eagle:0 LISTENING
TCP Eagle:epmap Eagle:0 LISTENING
TCP Eagle:https Eagle:0 LISTENING
TCP Eagle:microsoft-ds Eagle:0 LISTENING
TCP Eagle:1030 Eagle:0 LISTENING
TCP Eagle:6059 Eagle:0 LISTENING
TCP Eagle:8001 Eagle:0 LISTENING
TCP Eagle:8005 Eagle:0 LISTENING
TCP Eagle:8065 Eagle:0 LISTENING
TCP Eagle:microsoft-ds localhost:1031 ESTABLISHED
TCP Eagle:1031 localhost:microsoft-ds ESTABLISHED
TCP Eagle:1040 Eagle:0 LISTENING
TCP Eagle:netbios-ssn Eagle:0 LISTENING
TCP Eagle:1213 218.85.139.65:9002 CLOSE_WAIT
TCP Eagle:2416 219.133.63.142:https CLOSE_WAIT
TCP Eagle:2443 219.133.63.142:https CLOSE_WAIT
TCP Eagle:2907 192.168.1.101:2774 CLOSE_WAIT
TCP Eagle:2916 192.168.1.101:telnet ESTABLISHED
TCP Eagle:2927 219.137.227.10:4899 TIME_WAIT
TCP Eagle:2928 219.137.227.10:4899 TIME_WAIT
TCP Eagle:2929 219.137.227.10:4899 ESTABLISHED
TCP Eagle:3455 218.85.139.65:9002 ESTABLISHED
TCP Eagle:netbios-ssn Eagle:0 LISTENING
UDP Eagle:microsoft-ds *:*
UDP Eagle:1046 *:*
UDP Eagle:1050 *:*
UDP Eagle:1073 *:*
UDP Eagle:1938 *:*
UDP Eagle:2314 *:*
UDP Eagle:2399 *:*
UDP Eagle:2413 *:*
UDP Eagle:2904 *:*
UDP Eagle:2908 *:*
UDP Eagle:3456 *:*
UDP Eagle:4000 *:*
UDP Eagle:4001 *:*
UDP Eagle:6000 *:*
UDP Eagle:6001 *:*
UDP Eagle:6002 *:*
UDP Eagle:6003 *:*
UDP Eagle:6004 *:*
UDP Eagle:6005 *:*
UDP Eagle:6006 *:*
UDP Eagle:6007 *:*
UDP Eagle:6008 *:*
UDP Eagle:6009 *:*
UDP Eagle:6010 *:*
UDP Eagle:6011 *:*
UDP Eagle:1045 *:*
UDP Eagle:1051 *:*
UDP Eagle:netbios-ns *:*
UDP Eagle:netbios-dgm *:*
UDP Eagle:netbios-ns *:*
UDP Eagle:netbios-dgm *:*
详细信息
我们拿其中一行来解释吧：
Proto Local Address Foreign Address State
TCP Eagle:2929 219.137.227.10:4899 ESTABLISHED
协议（Proto）：TCP，指是传输控制协议。
本地机器名（Local Address）：Eagle，俗称计算机名，安装系统时设置的，可以在“我的电脑”属性中修改，本地打开并用于连接的端口：2929）
远程机器名（Foreign Address）：219.137.227.10
远程端口：4899
状态：ESTABLISHED
状态列表
LISTEN ：在监听状态中。
ESTABLISHED：已建立联机的联机情况。
-a 参数常用于获得你的本地系统开放的端口，用它您可以自己检查你的系统上有没有被安装木马
如果您Netstat你自己的话，发现下面的信息：
Port 12345(TCP) Netbus
Port 31337(UDP) Back Orifice
相关
继续我们的探讨，使用-n参数。（Netstat -n)
Netstat -n基本上是-a参数的数字形式：
C:\>netstat -n
Active Connections
Proto Local Address Foreign Address State
TCP 127.0.0.1:445 127.0.0.1:1031 ESTABLISHED
TCP 127.0.0.1:1031 127.0.0.1:445 ESTABLISHED
TCP 192.168.1.180:1213 218.85.139.65:9002 CLOSE_WAIT
TCP 192.168.1.180:2416 219.133.63.142:443 CLOSE_WAIT
TCP 192.168.1.180:2443 219.133.63.142:443 CLOSE_WAIT
TCP 192.168.1.180:2907 192.168.1.101:2774 CLOSE_WAIT
TCP 192.168.1.180:2916 192.168.1.101:23 ESTABLISHED
TCP 192.168.1.180:2929 219.137.227.10:4899 ESTABLISHED
TCP 192.168.1.180:3048 192.168.1.1:8004 SYN_SENT
TCP 192.168.1.180:3455 218.85.139.65:9002 ESTABLISHED
-a 和 －n 是最常用的两个，据我不完全测试得出以下结果：
1. -n 显示用数字化主机名，即IP地址，而不是compute_name【eagle】
2. -n 只显示TCP连接
得到IP等于得到一切，它是最容易使机器受到攻击的东西，所以隐藏自己IP，获得别人的IP对hacker来说非常重要.
-a 和 -n 是最常用的命令，如果要显示一些协议的更详细信息，就要用-p这个参数了，它其实是-a 和 -n的一个变种，我们来看一个实例，你就明白了：【netstat -p @@@ 其中@@@为TCP或者UDP】
C:\>netstat -ptcp
Active Connections
Proto Local Address Foreign Address State
TCP Eagle:microsoft-ds localhost:1031 ESTABLISHED
TCP Eagle:1031 localhost:microsoft-ds ESTABLISHED
TCP Eagle:1213 218.85.139.65:9002 CLOSE_WAIT
TCP Eagle:2416 219.133.63.142:https CLOSE_WAIT
TCP Eagle:2443 219.133.63.142:https CLOSE_WAIT
TCP Eagle:2907 192.168.1.101:2774 CLOSE_WAIT
TCP Eagle:2916 192.168.1.101:telnet ESTABLISHED
TCP Eagle:2929 219.137.227.10:4899 ESTABLISHED
TCP Eagle:3455 218.85.139.65:9002 ESTABLISHED
继续我们的参数讲解 -e
含义：本选项用于显示关于以太网的统计数据。它列出的项目包括传送的数据报的总字节数、错误数、删除数、数据报的数量和广播的数量。这些统计数据既有发送的数据报数量，也有接收的数据报数量。这个选项可以用来统计一些基本的网络流量。
C:\>netstat -e
Interface Statistics
Received Sent
Bytes ????????? ????????
Unicast packets ?????? ??????
Non-unicast packets 886526 2386
Discards 0 0
Errors 0 0
Unknown protocols 4449
若接收错和发送错接近为零或全为零，网络的接口无问题。但当这两个字段有100个以上的出错分组时就可以认为是高出错率了。高的发送错表示本地网络饱和或在主机与网络之间有不良的物理连接; 高的接收错表示整体网络饱和、本地主机过载或物理连接有问题，可以用Ping命令统计误码率，进一步确定故障的程度。netstat -e 和ping结合使用能解决一大部分网络故障。
接下来我们开始讲解两个比较复杂的参数 -r 和 -s 。
-r是用来显示路由表信息，我们来看例子：
C:\>netstat -r
Route Table（路由表）
Interface List（网络接口列表）
0x1 ........................... MS TCP Loopback interface
0x10003 ...00 0c f1 02 76 81 ...... Intel(R) PRO/Wireless LAN 2100 3B Mini PCI
dapter
0x10004 ...00 02 3f 00 05 cb ...... Realtek RTL8139/810x Family Fast Ethernet
Active Routes:（动态路由）
Network Destination Netmask Gateway Interface Metric
0.0.0.0 0.0.0.0 192.168.1.254 192.168.1.181 30
0.0.0.0 0.0.0.0 192.168.1.254 192.168.1.180 20
127.0.0.0 255.0.0.0 127.0.0.1 127.0.0.1 1
192.168.1.0 255.255.255.0 192.168.1.180 192.168.1.180 20
192.168.1.0 255.255.255.0 192.168.1.181 192.168.1.181 30
192.168.1.180 255.255.255.255 127.0.0.1 127.0.0.1 20
192.168.1.181 255.255.255.255 127.0.0.1 127.0.0.1 30
192.168.1.255 255.255.255.255 192.168.1.180 192.168.1.180 20
192.168.1.255 255.255.255.255 192.168.1.181 192.168.1.181 30
224.0.0.0 240.0.0.0 192.168.1.180 192.168.1.180 20
224.0.0.0 240.0.0.0 192.168.1.181 192.168.1.181 30
255.255.255.255 255.255.255.255 192.168.1.180 192.168.1.180 1
255.255.255.255 255.255.255.255 192.168.1.181 192.168.1.181 1
Default Gateway: 192.168.1.254（默认网关）
===========================================================================
补充
Persistent Routes:（静态路由）
None
C:\>
-s 参数的作用前面有详细的说明，来看例子
C:\>netstat -s
IPv4 Statistics （IP统计结果）
Packets Received = 369492（接收包数）
Received Header Errors = 0（接收头错误数）
Received Address Errors = 2（接收地址错误数）
Datagrams Forwarded = 0（数据报递送数）
Unknown Protocols Received = 0（未知协议接收数）
Received Packets Discarded = 4203（接收后丢弃的包数）
Received Packets Delivered = 3 6 5 2 8 7（接收后转交的包数）
Output Requests = 3 69066（请求数）
Routing Discards = 0（路由丢弃数 ）
Discarded Output Packets = 2172（包丢弃数）
Output Packet No Route = 0（不路由的请求包）
Reassembly Required = 0（重组的请求数）
Reassembly Successful = 0（重组成功数）
Reassembly Failures = 0（重组失败数）
Datagrams Successfully Fragmented = 0（分片成功的数据报数）
Datagrams Failing Fragmentation = 0（分片失败的数据报数）
Fragments Created = 0（分片建立数）
ICMPv4 Statistics （ICMP统计结果）包括Received和Sent两种状态
Received Sent
Messages 285 784（消息数）
Errors 0 0（错误数）
Destination Unreachable 53 548（无法到达主机数目）
Time Exceeded 0 0（超时数目）
Parameter Problems 0 0（参数错误）
Source Quenches 0 0（源夭折数）
Redirects 0 0（重定向数）
Echos 25 211（回应数）
Echo Replies 207 25（回复回应数）
Timestamps 0 0（时间戳数）
Timestamp Replies 0 0（时间戳回复数）
Address Masks 0 0（地址掩码数）
Address Mask Replies 0 0（地址掩码回复数）
TCP Statistics for IPv4（TCP统计结果）
Active Opens = 5217（主动打开数）
Passive Opens = 80（被动打开数）
Failed Connection Attempts = 2944（连接失败尝试数）
Reset Connections = 529（复位连接数）
Current Connections = 9（当前连接数目）
Segments Received = 350143（当前已接收的报文数）
Segments Sent = 347561（当前已发送的报文数）
Segments Retransmitted = 6108（被重传的报文数目）
UDP Statistics for IPv4（UDP统计结果）
Datagrams Received = 14309（接收的数据包）
No Ports = 1360（无端口数）
Receive Errors = 0（接收错误数）
Datagrams Sent = 14524（数据包发送数）
-----------------------------------------------------
netstat -abnov ，显示的该进程发起的程序进程或者文件列表。此命令常用来判断是否有可疑进程，之后进行相关操作。
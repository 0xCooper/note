双Tab，用于补全

Ctrl+T，建立新页

Ctrl+W，关闭标签页

Ctrl+Tab，切换标签页

Alt+F4，关闭所有标签页

Ctrl+1，切换到第一个页签，Ctrl+2同理

Alt + enter，切换到全屏状态

在cmder->config->aliases，打开aliases。

并将:

```
l=ls --show-control-chars 
la=ls -aF --show-control-chars 
ll=ls -alF --show-control-chars 
ls=ls --show-control-chars -F
```

添加至文件末尾，用于增强命令并添加颜色区分。

```css
Tab       自动路径补全
Ctrl+T    建立新页签
Ctrl+W    关闭页签
Ctrl+Tab  切换页签
Alt+F4    关闭所有页签
Alt+Shift+1 开启cmd.exe
Alt+Shift+2 开启powershell.exe
Alt+Shift+3 开启powershell.exe (系统管理员权限)
Ctrl+1      快速切换到第1个页签
Ctrl+n      快速切换到第n个页签( n值无上限)
Alt + enter 切换到全屏状态
Ctr+r       历史命令搜索
Tab         自动路径补全
Ctrl+T      建立新页签
Ctrl+W      关闭页签
Ctrl+Tab    切换页签
Alt+F4      关闭所有页签
Alt+Shift+1 开启cmd.exe
Alt+Shift+2 开启powershell.exe
Alt+Shift+3 开启powershell.exe (系统管理员权限)
Ctrl+1      快速切换到第1个页签
Ctrl+n      快速切换到第n个页签( n值无上限)
Alt + enter 切换到全屏状态
Ctr+r       历史命令搜索
Win+Alt+P   开启工具选项视窗
```

```
五、关于中文乱码问题：

将下面的4行命令添加到cmder/config/aliases文件末尾,如果还是不行参考前面字体设置，将前面提到的字体设置里面的Monospace的复选框不选中。还有就是养成良好的编码习惯文件命名最好不要有中文。

l=ls --show-control-chars 
la=ls -aF --show-control-chars 
ll=ls -alF --show-control-chars 
ls=ls --show-control-chars -F


```

```

```

之前在网找了好多方法，可是都解决不了，很多人在在Environment里添加set LANG=zh_CN.UTF-8来解决中文乱码的问题，可是我用这个方法并没有成功，可能是环境的原因吧，我的系统是win10的。<br>最后找到解决办法：<br>Settings-&gt;Startup-&gt;Environment 添加<br>set LANG=zh_CN.UTF-8
set LC_ALL=zh_CN.utf8
![img](https://images2018.cnblogs.com/blog/763945/201804/763945-20180404153700272-1516801389.png)

```
cmder默认的命令提示符是 λ ，如果想改成常见的 $ ,具体操作如下：<br>打开cmder安装目录下的<strong>\vendor\clink.lua</strong>文件找到<code>lambda = "λ"</code>和<code>lambda = "("..env..") λ"</code>把λ替换成$<br>然后重启cmder即可，但powerShell需要另行设置<br>打开cmder安装目录下的<strong>\vendor\profile.ps1</strong>文件找到<code>λ &lt;PostPrompt&gt; &lt;repl input&gt;</code>和<code>λ &lt;PostPrompt&gt; |</code>和<strong><em>Microsoft.PowerShell.UtilityWrite-Host "`nλ " -NoNewLine -ForegroundColor "DarkGray"</em></strong>把λ替换成$ ,然后重启cmder即可

```

```
自定义aliasessssss
原文地址：https://www.cnblogs.com/ziyoublog/p/10416684.html。

```


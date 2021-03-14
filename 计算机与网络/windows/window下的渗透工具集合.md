https://pentestbox.org/zh/#download

- 2017-02-04
- [安全](https://www.webshell.cc/anquan)
- 暂无评论
- 747次阅读

#### 0x01介绍

PentestBox：[渗透](https://www.webshell.cc/tag/shentou)测试盒子 顾名思义，这是一个[渗透](https://www.webshell.cc/tag/shentou)工具包，但是不同于绝大多数国内xx工具包的是，这里集成的大都是[Linux](https://www.webshell.cc/tag/linux)下的工具,Kali [Linux](https://www.webshell.cc/tag/linux)上面的常用的很多工具这里面也都集成了。

PentestBox官网：https://[pentestbox](https://www.webshell.cc/tag/pentestbox).org/zh/

官方的介绍如下：

PentestBox是一款Windows平台下预配置的便携式开源[渗透](https://www.webshell.cc/tag/shentou)测试环境

为什么又有一个[渗透](https://www.webshell.cc/tag/shentou)测试环境？

PentestBox不同于运行在虚拟机或者双启动环境的Linux渗透测试发行版。

它打包了所有的[安全](https://www.webshell.cc/tag/security)工具，并且可以在Windows系统中原生地运行，有效地降低了对虚拟机或者双启动环境的需求。

我们发现超过50%的渗透测试发行版是运行在Windows系统下的虚拟机程序中，这激发我们创造了它。

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/6a992d5529f459a44fee58c733255e86.png)](https://www.webshell.cc/wp-content/uploads/2017/02/6a992d5529f459a44fee58c733255e86.png)

 

#### 0x02下载

官网上自带的下载速度还是蛮快的，这里我下载的是 附带 metasploit版本的PentestBox

```
PentestBox： https://sourceforge.net/projects/pentestbox/files/PentestBox-v2.2.exe/download

种子：https://pentestbox.org/PentestBox-v2.2.torrent

安装有 Metasploit 的 PentestBox：https://sourceforge.net/projects/pentestbox/files/PentestBox-with-Metasploit-v2.2.exe/download

种子：https://pentestbox.org/PentestBox-with-Metasploit-v2.2.torrent
```

 

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/fd456406745d816a45cae554c788e754.png)](https://www.webshell.cc/wp-content/uploads/2017/02/fd456406745d816a45cae554c788e754.png)

 

#### 0x03安装

官网 提示：按照带有metasploit 的版本的时候得关闭windows自带的防火墙,因为metasploit生成的攻击载荷 对于 windows的安全来说 是个威胁。

防火墙的关闭：

Windows7直接在控制面板里面 关闭防火墙即可：

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/10b9a0e0aa92e62ca9b611ad12105cda.png)](https://www.webshell.cc/wp-content/uploads/2017/02/10b9a0e0aa92e62ca9b611ad12105cda.png) [![img](https://www.webshell.cc/wp-content/uploads/2017/02/120f1ba86ba516d67d66ecb915b50ce4.png)](https://www.webshell.cc/wp-content/uploads/2017/02/120f1ba86ba516d67d66ecb915b50ce4.png)

Windows 10的话，除了关闭上述的防火墙 还得关闭 Windows Defender

在windows 自带的 设置-更新和安全-Windows Defender 中关闭。

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/36e5371ad91c9d2d09e9d7c0e76055db.png)](https://www.webshell.cc/wp-content/uploads/2017/02/36e5371ad91c9d2d09e9d7c0e76055db.png)

注意 如果没有关闭防火墙的话，PentestBox安装的过程中释放的文件 会直接被 防火墙 悄悄的干掉，如果这样的话 就非常的尴尬了，所以 为了方便，建议开始的时候直接关闭防火墙。

直接运行 文件 选择安装的文件位置路径，即可安装，安装其实就是文件的释放，最后整个文件夹大小为4.55GB左右

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/19ad89bc3e3c9d7ef68b89523eff1987.png)](https://www.webshell.cc/wp-content/uploads/2017/02/19ad89bc3e3c9d7ef68b89523eff1987.png)

所以我们可以直接 把PentestBox安装在移动硬盘或者 U盘中，这样就打造了移动渗透工具的平台了，在任意的windows系统上运行，这就比Kali 的Live U盘要方便许多

 

#### 0x04基本文件结构

PentestBox共5个文件夹,2个库文件，一个bat批处理和一个exe启动程序。

bat和exe都可以启动PentestBox

base文件夹：[![img](https://www.webshell.cc/wp-content/uploads/2017/02/593616de15330c0fb2d55e55410bf994.png)](https://www.webshell.cc/wp-content/uploads/2017/02/593616de15330c0fb2d55e55410bf994.png)里面放了一些工具需要用到的环境变量文件，如：python 、jdk等

bin文件夹：[![img](https://www.webshell.cc/wp-content/uploads/2017/02/593616de15330c0fb2d55e55410bf994.png)](https://www.webshell.cc/wp-content/uploads/2017/02/593616de15330c0fb2d55e55410bf994.png)里面的工具基本上足够满足日常的渗透测试要求了

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/9a09b4dfda82e3e665e31092d1c3ec8d.png)](https://www.webshell.cc/wp-content/uploads/2017/02/9a09b4dfda82e3e665e31092d1c3ec8d.png)

 

#### 0x05 基本操作

5.1.软件安装：

终端下输入：toolsmanager

打开工具管理器，在这里可以 安装/升级/卸载 软件

首先，它会从GitHub的信息库自动更新，然后会显示菜单。如果没有互联网连接，脚本会等待一段时间，然后显示菜单。如下图：

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/3ac340832f29c11538fbe2d6f75e8bcc.png)](https://www.webshell.cc/wp-content/uploads/2017/02/3ac340832f29c11538fbe2d6f75e8bcc.png)

可以通过选择编号进入相关的模块。例如，如果我选择了Web应用程序类别，然后按10，它会显示：

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/2567a5ec9705eb7ac2c984033e06189d.png)](https://www.webshell.cc/wp-content/uploads/2017/02/2567a5ec9705eb7ac2c984033e06189d.png)

在这里面 我们就可以安装 这里面列出的工具。
 现在，如果你想安装imagejs
 然后键入install imagejs
 它会安装它。安装后，重启 PentestBox，你所安装的工具会生效。
 可以用toolsmanager安装的软件列表，具体见这里 modules.[pentestbox](https://www.webshell.cc/tag/pentestbox).com

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/42d297c97acd11aa077241a9f3b566bc.png)](https://www.webshell.cc/wp-content/uploads/2017/02/42d297c97acd11aa077241a9f3b566bc.png)

5.2.软件更新：

1.安装软件就酱紫了，如果要更新的话，这里直接输入编号 11

Update all installed Modules 这里就开始更新已经安装的工具了：

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/e80a1ba5ddefbb3f13045ed0c9ec69eb.png)](https://www.webshell.cc/wp-content/uploads/2017/02/e80a1ba5ddefbb3f13045ed0c9ec69eb.png)

2.PentestBox是一个开源项目，让在PentestBox使用的所有文件都存在于它的Github上库。
 终端下输入：update 从它的Github上库，如果有任何更改，然后显示菜单将先进行自我更新。如果没有互联网连接，脚本会等待一段时间，然后显示菜单。

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/adc38f65ff29b40c468874a25bfc4585.png)](https://www.webshell.cc/wp-content/uploads/2017/02/adc38f65ff29b40c468874a25bfc4585.png)

5.3.软件卸载：

在toolsmanager 的软件目录里面 我们现在想卸载已经安装过的软件的话，直接键入uninstall + 软件名

假如这里我们想卸载 xssless，然后键入uninstall xssless，这样就会卸载 xssless

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/fe98497efedbe156ecc4b953aea77e07.png)](https://www.webshell.cc/wp-content/uploads/2017/02/fe98497efedbe156ecc4b953aea77e07.png)

 

#### 0x06 键盘快捷键

```
CTRL + T ：要打开新的标签页
CTRL + C ：要关闭脚本/程序运行。
CTRL + w ：这将关闭当前活动的控制台。
ALT +Enter ：Pentestbox 会去全屏。
```

#### 0x07安装后的调试

因为是国外开源项目的原因，有些配置不符合我们国内的本土风情，举个例子：

1.PentestBox 面封装的atom 编辑器是无法输入汉语的，而且插件也会出现一些问题，比如minimap等得重新配置

解决方法：将自己原来的atom安装的文

里件夹替换PentestBox里面的atom即可

C:UsersCTFAppDataLocalatomapp-1.12.6 (‘CTF’是我自己电脑的用户名)

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/3e10f8c809242d3a0f94c18e7addb866.png)](https://www.webshell.cc/wp-content/uploads/2017/02/3e10f8c809242d3a0f94c18e7addb866.png)

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/3a2c8049477c279af5ec16dbc92db4cd.png)](https://www.webshell.cc/wp-content/uploads/2017/02/3a2c8049477c279af5ec16dbc92db4cd.png)

\2. PentestBox封装Burpsuite的是Free版本的，功能上自然比不上 国内的专业破解版的Burpsuite

解决方法:把专业版破解版的burpsuite替换进去，并重命名 即可。

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/afaff8193505e29230b76f8c8dd78170.png)](https://www.webshell.cc/wp-content/uploads/2017/02/afaff8193505e29230b76f8c8dd78170.png)

 

#### 0x08 添加自己的工具

很多情况下自己的工具 toolsmanager或默认PentestBox未安装。可以按照下面的指南 来手动添加自己的工具：

需要做两件事情，

1.下载/克隆工具文件，

2.设置别名

别名是基本上是需要PentestBox控制台通过，例如终端命令的SqlMap是一个别名访问sqlmap。

8.1.基于Python的工具

首先复制文件到 C:/PentestBox/bin/customtools/下
 添加一个别名:编辑customaliases文件 位于/PentestBox/bin/customtools/文件夹下。



[![img](https://www.webshell.cc/wp-content/uploads/2017/02/5ed3341e31fc13fb3bb013723b9c14be.png)](https://www.webshell.cc/wp-content/uploads/2017/02/5ed3341e31fc13fb3bb013723b9c14be.png)

例如，如果你需要添加一个别名hello的工具，那么它的别名是 hello=python "%[pentestbox](https://www.webshell.cc/tag/pentestbox)_ROOT%bincustomtoolsHello.py" $*
 上述行添加到customaliases并保存文件 复制到文件夹下：

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/203ad5ffa1d7c650ad681fdff3965cd2.png)](https://www.webshell.cc/wp-content/uploads/2017/02/203ad5ffa1d7c650ad681fdff3965cd2.png)

然后编辑 customaliases文件

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/1dc49e4cc0046e1ecaafced131abd295.png)](https://www.webshell.cc/wp-content/uploads/2017/02/1dc49e4cc0046e1ecaafced131abd295.png)

重启你的 PentestBox ，即可生效

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/098f6bcd4621d373cade4e832627b4f6.png)](https://www.webshell.cc/wp-content/uploads/2017/02/098f6bcd4621d373cade4e832627b4f6.png)

8.2.基于exe的工具

1.下载/克隆工具文件。
 2.设置别名 方法同上， 只是别名这里 设置的格式为：tool="%pentestbox_ROOT%bincustomtoolstool.exe" $*
 举例：我们添加个金典的 小葵解密工具

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/098f6bcd4621d373cade4e832627b4f6.png)](https://www.webshell.cc/wp-content/uploads/2017/02/098f6bcd4621d373cade4e832627b4f6.png)

编辑 customaliases文件

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/06c552c92675b148656f379ccecdc906.png)](https://www.webshell.cc/wp-content/uploads/2017/02/06c552c92675b148656f379ccecdc906.png)

效果如下：

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/c5ae8ab2b8826aeb795356cb0a726911.png)](https://www.webshell.cc/wp-content/uploads/2017/02/c5ae8ab2b8826aeb795356cb0a726911.png)

8.3.基于Ruby的工具和Java的工具

语法格式：

Java ：tool=start javaw -jar "%pentestbox_ROOT%bincustomtoolstool.jar" $*

Ruby : wpscan=ruby "%pentestbox_ROOT%bincustomtoolswpscanwpscan.rb" $*

在PentestBox 中添加自己的Java 和 Ruby工具，方法的原理是一样的，只是在编辑 customaliases文件 的时候，语法格式有点区别，Java 和 Ruby 的工具格式 参考上面的格式。

#### 0x09 通过网络共享PentestBox

考虑你想要在你的办公室，实验室等使用多台计算机上PentestBox喜欢而不是在每个计算机上安装PentestBox的环境中，你可以只安装一台计算机上，共享该文件夹作为一个驱动器上的其他计算机在同一个网络。

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/85e47ac07ac9d6416168a97e33fa969a.png)](https://www.webshell.cc/wp-content/uploads/2017/02/85e47ac07ac9d6416168a97e33fa969a.png)

更改读取权限读/写，并单击共享。

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/8ddf878039b70767c4a5bcf4f0c4f65e.png)](https://www.webshell.cc/wp-content/uploads/2017/02/8ddf878039b70767c4a5bcf4f0c4f65e.png)

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/fac989447cad2edbc89fbcba70003b36.png)](https://www.webshell.cc/wp-content/uploads/2017/02/fac989447cad2edbc89fbcba70003b36.png)

现在在局域网的其他电脑上的的 资源管理器 中的 网络 可以看到共享的文件夹

[![img](https://www.webshell.cc/wp-content/uploads/2017/02/ec6ef230f1828039ee794566b9c58adc.png)](https://www.webshell.cc/wp-content/uploads/2017/02/ec6ef230f1828039ee794566b9c58adc.png) [![img](https://www.webshell.cc/wp-content/uploads/2017/02/1d665b9b1467944c128a5575119d1cfd.png)](https://www.webshell.cc/wp-content/uploads/2017/02/1d665b9b1467944c128a5575119d1cfd.png)

最后，你可以像你所使用的电脑上安装使用PentestBox。
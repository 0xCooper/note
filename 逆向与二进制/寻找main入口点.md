## 一丶识别各个程序的入口点

入门知识,识别各个应用程序的入口点

(举例识别VC 编译器生成,以及VS编译生成的Debug版本以及Release版本)

## 1.识别VC6.0 Debug版本

1.1 首先,新建一个VC debug版本的程序,然后F5运行,可以看到栈回溯窗口

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNDEyNDA0NC0xNTU0MzY4Nzk0LnBuZw?x-oss-process=image/format,png)

1.2 而后通过栈回溯窗口,点击mainCRTStarup,查看main函数之前会调用什么API

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNDIzODY2OS0zNTIyMzc5ODgucG5n?x-oss-process=image/format,png)

确定之后,OD打开查看.

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNDYzMDMwOS0xNTQ4NDQ3MDEyLnBuZw?x-oss-process=image/format,png)

可以看到调用API的位置,但是怎么确定那个是入口点,我们知道, VC中的main函数是3个参数,那么我们只需要找到

三个push 然后一个Call的位置,则可以确定,(确定也是要你F7跟进去,看看代码是不是main函数的代码,或者参数传参是什么)

1.3确定main入口点

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNTAwODcxNi0xNTgyNjEzMzA1LnBuZw?x-oss-process=image/format,png)

在上图可以看到,三个push,然后一个Call,那么我们跟进去查看,因为是Debug版本,所以已经提示出来参数是什么了

所以直接可以确定了.

1.4 F7跟进去查看.

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNTE0NzI0Ny0xNjc1Nzk5ODE1LnBuZw?x-oss-process=image/format,png)

可以直接确定使我们的入口点

IDA查看一次

步骤和前边一样,先看入口点特征,Debug版本特征是调用API GetVersion

所以IDA中查看.

1.查看文本视图

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNTQyNjE2OS0xNjE3NTAxOTAyLnBuZw?x-oss-process=image/format,png)

2.展开文本视图

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNTQ0NjcwMC0xMzE5NjYxOTM2LnBuZw?x-oss-process=image/format,png)

这里提示你要CTRL + 加号 展开

展开查看

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNTUzMjA1OS03MjQ5ODkyMTgucG5n?x-oss-process=image/format,png)

 

3.根据特征,读取代码,确定main位置

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNTYwNjg3Mi01NDM5NDg3NTEucG5n?x-oss-process=image/format,png)

因为是Debug所以有符号显示 下面直接看Release版本

## 2.查看VC6.0 Release版本

首先,特征是一样的,都是调用GetVersion

那么现在直接OD打开去分析.(当然IDA也可以,都是工具)

1.一样,先找特征

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNTk0OTA3NS0yMjcyNDQ0ODIucG5n?x-oss-process=image/format,png)

2.找到之后,因为我们写的是main,所以判断是main,只要找到三个push一个Call即可

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAwNTkyNzcxNi0zNzIzOTcxOS5wbmc?x-oss-process=image/format,png)

已经找到了 F7 跟进去查看.

3.确认是不是.

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMDExNTI5NC0xMzExODQwMjE5LnBuZw?x-oss-process=image/format,png)

可以看出,因为是Release版本,所以都给优化没了.确实使我们写的代码

 

## 3.查看VS系列 Debug版本(没个版本不一样,所以先看下特征这里是 VS 2015)

1.栈回溯,确定入口点特征

首先第一步,还是编写一段代码

然后通过栈回溯,查看入口的特征.

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMTcyNTUyOC0xMTA4MjE0NzkzLnBuZw?x-oss-process=image/format,png)

那么我觉着,这个是入口点的特征,而在tmainCRTStartup里面调用的wmain

那么此时OD打开的时候可以分析遇到的第二个call,然后在第二个call里面跟进去.

通过栈回溯,可以看到会调用这种API,而下方的截图则会调用wmain,所以OD打开,不断的跟,也是三个push 一个Call

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMTU1Njg3Mi02MjEzNjc0OTcucG5n?x-oss-process=image/format,png)

2.OD分析

因为是Debug版本,有跳转表,也可以看到符号信息,所以直接跳转过来

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMTk0NzgwOS04NzcyMjU1ODIucG5n?x-oss-process=image/format,png)

跳转过来之后(看下图)

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMjAxOTkxOS0yMTkxNzgwNjMucG5n?x-oss-process=image/format,png)

可以看到确实是两个Call,也就是我们上面分析的,然后进入第二个Call

3.确定入口点位置

F7跟进去,查找三个push 一个Call

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMjIyMzM0MS0xMjMwMzY5MzcwLnBuZw?x-oss-process=image/format,png)

找到了,我们跟进去查看,看看是否是入口点,

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMjI1MjA3NS0xMTQzODAwNTYucG5n?x-oss-process=image/format,png)

跟进去之后发现又有一层跳转表,没关系,F8 走过去

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMjMyNzM0MS04MDU3NjYzNTAucG5n?x-oss-process=image/format,png)

跟过来之后则会发现确实使我们入口点写的代码了

##  

## 4. VS系列,查看Release版本

Release版本是一样的,直接IDA打开查看(换着工具看)

1.进去IDA,打开入口点,CTRL + 加号展开

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMjgzNjk4MS0yMTIxMzM4ODgyLnBuZw?x-oss-process=image/format,png)

CTRL + 加号展开不做演示,同上面分析一样.

查看反汇编

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMjk1ODMyNS0xNTg2ODkxODQwLnBuZw?x-oss-process=image/format,png)

发现IDA直接跟过来的就是这个,那么此时好办了,我们知道main在它的下面,那么直接寻找三个push 一个Call即可.

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMzA0ODgyNS0xMzk0NDA3MTAzLnBuZw?x-oss-process=image/format,png)

 

找到了,双击_main确认一下.

![img](http://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWFnZXMyMDE3LmNuYmxvZ3MuY29tL2Jsb2cvMTE5NzM2NC8yMDE3MTEvMTE5NzM2NC0yMDE3MTEwNzAxMzExMjQ1MC0xNjEzNjQ3ODk4LnBuZw?x-oss-process=image/format,png)

我们刚才写的代码已经出来了


这几种常见的设备通信技术，都可用于上网，但区别还是很大

问题：蓝牙与wifi与zigbee等区别

协议结构图

![img](https://img-blog.csdn.net/20170120115703614?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvbGlkaXlhMDA3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

第一层：physicallayer（物理层）

　　信道带宽提供2M，提供三个广播信道1M。

第二层：link layer（链路层）

　　执行一些基带协议，底层的数据包管理协议。

第三层：\\host controller interface （主机控制接口层

　　提供主机与控制层 的通讯方式，以及命令格式，重用蓝牙标准，比如一些串口，USB等等。

第四层：L2CAP（逻辑链路于适配器协议层）

　　为它上层提供数据业务，提供端到端的逻辑数据通信。

第五层：security managerSM）安全管理层

　　层与层之间会有通信，它是建立数据交换安全方面的数据知识。

第六层：attribute protocol\\ATT）通用接入层

　　定义了一些通用接口，供应用层和底层之间的调用，比如你要调底层的硬件模块的东西，就需要这个层的底层的驱动模块去实现它的一些功能，所以它会同时封装一些API的函数设置。

\\第七层：\\generic attribute profile\\（\\\\GATT\\\\）（属性协议层）\\\

　　允许设备以属性的形式向外设备暴露它的一些数据，就像广播者与观察者之间，它一直在广播自己的属性，数据出去。观察者观察到了它以后就可以把它的属性提取出来。

\\第八层：\\generic access profile\\（\\\\GAP\\\\）通用属性剖面\\\

　　具体属性协
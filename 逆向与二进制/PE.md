#### 导出表

导出表的结构体

前四个字节是地址，后四个字节是大小

![1604495848393](../img/1604495848393.png)







#### 扩大节

![1604481939060](../img/1604481939060.png)









#### PE头



![](https://gitee.com/muyinchuan/images/raw/master/img/20201025123931.png)



![](https://gitee.com/muyinchuan/images/raw/master/img/20201025170708.png)

文件属性

![](https://gitee.com/muyinchuan/images/raw/master/img/20201025171131.png)





#### 扩展PE头

![](https://gitee.com/muyinchuan/images/raw/master/img/20201029170846.png)



![](https://gitee.com/muyinchuan/images/raw/master/img/20201029170959.png)









1.可执行文件
![1599736710063](../img/1599736710063.png)

![1599738605021](../img/1599738605021.png)

#### dos_header结构体（共64字节）

![1599739359943](../img/1599739359943.png)

最后四个字节就是pe头的位置

与pe头的中间位置就是这个DOS块，可以随便改

#### PE文件头

![1599740307105](../img/1599740307105.png)

![1599740673300](../img/1599740673300.png)

标准pe头占20个字节

![1599742219540](../img/1599742219540.png)

之后是224个字节的扩展PE头

![1599989587425](../img/1599989587425.png)

大于200就是400，文件对齐便于数据处理

#### 节表

一个节表是40个字节

size of rawdata 文件中对齐的大小

```
1、Name	8个字节 一般情况下是以"\0"结尾的ASCII吗字符串来标识的名称，内容可以自定义.									
										
注意：该名称并不遵守必须以"\0"结尾的规律，如果不是以"\0"结尾，系统会截取8个字节的长度进行处理.										
										
2、Misc  双字 是该节在没有对齐前的真实尺寸,该值可以不准确。										
										
3、VirtualAddress 节区在内存中的偏移地址。加上ImageBase才是在内存中的真正地址.										
										
4、SizeOfRawData  节在文件中对齐后的尺寸.										
										
5、PointerToRawData 节区在文件中的偏移.										
										
6、PointerToRelocations 在obj文件中使用 对exe无意义										
										
7、PointerToLinenumbers 行号表的位置 调试的时候使用										
										
8、NumberOfRelocations 在obj文件中使用  对exe无意义										
										
9、NumberOfLinenumbers 行号表中行号的数量 调试的时候使用										
										
10、Characteristics 节的属性	
```

![1599742715082](../img/1599742715082.png)



![1599743028403](../img/1599743028403.png)

4个节表后面就是编译器插入的一些东西

![1599743573480](../img/1599743573480.png)

按照文件对齐分配空间

内存对齐

#### 新增节的步骤

![1604156488313](../img/1604156488313.png)

#### shellcode

![1604408265937](../img/1604408265937.png)

#### 合并节
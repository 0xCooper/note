在学习操纵系统，汇编，逆向的过程中都提及了内存分配，就算如此本人对进程的内存分布还是疑惑



#### 疑问

> C语言的头文件加载进去会在一个什么位置   就像找main入口一样
>
> pe镜像占了多大的位置
>
> 如何去取得系统区的

1.首先大致的内存图是这样的

![](https://gitee.com/muyinchuan/images/raw/master/img/20201025124615.png)

![](https://gitee.com/muyinchuan/images/raw/master/img/20201025153434.png)

思考：如何找到这几个段

![](https://gitee.com/muyinchuan/images/raw/master/img/20201025154337.png)


需要记住的头文件

```
<unistd.h> Unix Standard的缩写包含对操作系统的调用
<fcntl.h> 文件描述符相关
<signal.h> 信号相关
<pthread.h>线程
<sys/ipc.h>进程间通信

```

```
size_t 无符号整型 是sizeof的返回值
```

#### gcc去除未用到的函数

> 在一个源文件中，里面有很多函数，但是main函数没有全部调用，未使用的函数也会被编译，也会被“打包”到最后的可执行文件中，要去除掉不要的函数，方法如下：
>
> 1.执行gcc -function-sections <name.c>。其中-function-sections的意思是，将不同函数编译到不同的section上面。如果没有这个选项，所有的函数都会编译到一个section上面，于是函数就不能被“剥离”
>
> 2.执行ld --gc-sections <object>。表示把不要的函数section去掉。
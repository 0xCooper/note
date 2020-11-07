![](https://gitee.com/muyinchuan/images/raw/master/img/20201009143416.png)



##### gcc

```
gcc a.c b.c d.c -o hello  ##多文件连编辑
```



```
-o：指定生成的输出文件；
-E：仅执行编译预处理；
-S：将C代码转换为汇编代码；
-wall：显示警告信息；
-c：仅执行编译操作，不进行连接操作。

-E
预编译后停下来，生成后缀为 .i 的预编译文件。
-c
编译后停下来，生成后缀为 .o 的目标文件。
-S
汇编后停下来，生成后缀为 .s 的汇编源文件。
```



##### makefile

```
最基本的makefile


1:hello:hello.c
2:	gcc hello.c -o hello
```


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
生成-o文件
gcc -c hello.c -o hello.o
```



##### makefile

命名 makefile Makefile

一个规则
两个函数
三个自动变量

```makefile
最基本的makefile


hello:hello.c
# 目标：依赖
	gcc hello.c -o hello
#前面有一个tab的缩进  wq就是最简单的makefile1
#使用make就出来了


 #如果是两步
hello:hello.o
	gcc hello.c -o hello
hello.o:hello.c
	gcc -c hello.c -o hello.o

#直接 make
a.out:hello.c add.c sub.c div1.c
	gcc hello.c add.c sub.c div.c -o a.out 
	
```

#### 两个函数

$(wildcard *.c)  $(patsubst %.c ,%.o,$(src))

```
1.src = $(wildcard *.c)
找到当前目录下的所有1后缀为.c的文件，赋值给src
2.obj = $(patsubst %.c ,%.o,$(src))
把src变量里所有后缀为.c替换为.o
将参数3中 包含参数1的部署，替换为参数2
make clean -n  #模拟执行


$@:在规则的命令表示目标 
$<:在规则的命令中表示第一个依赖条件
$^:在该规则的命名表示所有依赖条件
```

```
clean
1.src = $(wildcard *.c)
2.obj = $(patsubst %.c ,%.o,$(src))
ALL:a.out

add.o:add.c 
	gcc -c add.c -o add.o


clean:
	-rm -rf $(obj)  a.out
# “-” 删除不存在文件不报错
```

makefile 方便扩展



```
src = $(wildcard *.c)
obj = $(patsubst %.c ,%.o,$(src))//生成一个.o的文件列表
ALL:a.out
a.out: $(obj) //所有o生成一个a.out
	gcc $^ -o $@
%.o:%.c           //每一个c生成一个o
	gcc -c $< -o $@    
//$(obj):%.o:%.c
//gcc -c $< -o $@    静态模式规则
clean:
	-rm -rf $(obj) a.out
```


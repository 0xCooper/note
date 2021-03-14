数组的长度确定，一定是常量

#### int 类型数组

![](https://gitee.com/muyinchuan/images/raw/master/img/20201024171719.png)

![](https://gitee.com/muyinchuan/images/raw/master/img/20201024171547.png)

#### char类型数组

![](https://gitee.com/muyinchuan/images/raw/master/img/20201024173048.png)

12个字节处理是对齐长度，数组本身只有10个字节

#### short类型

![](https://gitee.com/muyinchuan/images/raw/master/img/20201024173001.png)

缓存区溢出

![](https://gitee.com/muyinchuan/images/raw/master/img/20201024173734.png)

```c
#include<stdio.h>
#include<stdlib.h>
void HelloWord()
{	
	printf("Hello World");
	
	getchar();
}	
void Fun()
{
	int arr[5] = {1,2,3,4,5};
	arr[6] = (int)Helloword;
}	
int main(){
Fun();
return 0;
}

```

缓存区溢出的原理就是ebp+4的ret地址被修改了





#### 多维数组

##### 一维数组的汇编代码

![](https://gitee.com/muyinchuan/images/raw/master/img/20201024180615.png)

##### 二维的汇编代码

![](https://gitee.com/muyinchuan/images/raw/master/img/20201024180732.png)

```
结论：多维数组在计算机存储里没有区别
```

#### 数组的参数传递

![](https://gitee.com/muyinchuan/images/raw/master/img/20201025151615.png)

结论

```
数组作为参数传递时，传的是参数的首地址
```

观察可以得出arr[i]与*（p+i）是等价的

![](https://gitee.com/muyinchuan/images/raw/master/img/20201025152115.png)
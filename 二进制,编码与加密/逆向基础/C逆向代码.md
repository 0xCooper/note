```cpp
c语言中写汇编
#include "stdafx.h"


int _declspec(naked) fun(){

	_asm{
	mov eax,0xf
	ret
	}
}

int main(int argc, char* argv[])
{
	int a;
	
	printf("Hello World!\n");	
	a = fun();
	printf("%d\n",a);
	return 0;
}


```

w

#### c语言



#### 查看不懂节区的位置

```
#include<stdio.h>
#include<stdlib.h>
 
int  a;
int  b=1;
 
main()
{
    int  n = 0;
    char *p1 = NULL;
    char *p2 = NULL;
    const int s = 10;
    p1 = (char*)malloc(200);
    p2 = "hello";
 
    printf("main  %p\n",main);
    printf("未初始化 a   %p\n",&a);
    printf("初始化   b   %p\n",&b);
    printf("局部变量 n   %p\n",&n);
    printf("动态内存 p1  %p\n",p1);
    printf("常量     s   %p\n",&s);
    printf("常字符串 p2  %p\n",p2);
 
    while(1)
    {}
}
1
```

#### 缓存区溢出

##### 1

```
#include<stdio.h>
fun();
void fun(){
int i;
int a[]={0,1,2,3,4,5,6,7,8,9};
for( i=0;i<=10;i++)
	{
	a[i]=0;
	printf("hello world!");


	}
}
int main(){
fun();
return 0;
}
```

##### 2

```
基于缓冲区溢出的HelloWorld
			
void HelloWord()		
{			
	printf("Hello World");
			
	getchar();	
}			
void Fun()		
{			
	int arr[5] = {1,2,3,4,5};
			
	arr[6] = (int)HelloWord;
			
}			
```










自动关机小程序

![1599736268650](../img/1599736268650.png)

![1599736282073](../img/1599736282073.png)

![1599736309575](../img/1599736309575.png)

![1599736453578](../img/1599736453578.png)















![1599786207132](../img/1599786207132.png)





![1599786216925](../img/1599786216925.png)




次方运算

#### 常用对数

```c
double log10(double x)
     double x, ret;
   x = 10000;
  
   /* 计算 log10(10000) */
   ret = log10(x);
   printf("log10(%lf) = %lf\n", x, ret);
```

与自然对数

```c
double pow(double x, double y) //c语言
在#include <math.h>头文件中
自然对数
double log(double x)

 double x, ret;
   x = 2.7;

   /* 计算 log(2.7) */
   ret = log(x);
   printf("log(%lf) = %lf", x, ret);
```

#### 平方根

```c
double sqrt(double x)
   printf("%lf 的平方根是 %lf\n", 4.0, sqrt(4.0) );
   printf("%lf 的平方根是 %lf\n", 5.0, sqrt(5.0) );
```

#### 绝对值

```c
double fabs(double x)

  int a, b;
   a = 1234;
   b = -344;
  
   printf("%d 的绝对值是 %lf\n", a, fabs(a));
   printf("%d 的绝对值是 %lf\n", b, fabs(b));
```


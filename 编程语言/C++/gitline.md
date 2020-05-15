cin.getline(s,n)

在C++中本质上有两种getline函数：

第一种：在头文件<istream>中，是iostream类的成员函数。

第二种：在头文件<string>中，是普通函数。

```
#include<iostream>
#include<string>
using namespace std;

int main()
{
    string name;
    string city;
    cout <<"please input your name ";
    gitline(cin,city);
    cout <<"input your city you live in";
    getline (cin,city);
    cout <<"hello,"<<name <<endl;
    cout <<"you live in "<<city <<endl;
    return 0;
        
}
```

```cpp

#include<iostream>
#include<string>
using namespace std;
 
int main(){
	string line;
	getline(cin,line,'?');//这里的问号为输入语句的终止符
	cout<<line;
	return 0;
}

//在这个如果不输入？？这个语句不会结束
```

```
getline(cin,string)//可能只读取string变量
```

![1587583871637](../img/1587583871637.png)

```
上图的1后用了delim(终止符 回车)就发审b的问题
```

![1587584087170](../img/1587584087170.png)

```
#include<iostream>
#include<string>
using namespace std;
int main()
{

	char a;
	string b;
        cin.get(a);
    getline(cin,b);
        cout<<a<<"<-a"<<endl;
    cout<<b<<"<-b"<<endl;



return 0;
}//这个程序先输入输入两次
```

 ***cin.getline()***函数也是 C++ 函数，它接受的参数是一个 C风格字符串（也就是一个字符数组），和一个最大长度

```cpp
#include <iostream>
using namespace std;

char str[20];
cin.getline(str, 20);
```


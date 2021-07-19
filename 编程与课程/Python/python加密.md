```
pip install pycryptodome
pip install hashlib
#hashlib 提供常见的消息摘要 md5 或者 base64
```



#### md5使用方法

```
import hashlib
# 待加密信息
str = '这是一个测试'
# 创建md5对象
hl = hashlib.md5()
# 此处必须声明encode
# 若写法为hl.update(str)  报错为： Unicode-objects must be encoded before hashing
hl.update(str.encode(encoding='utf-8'))

print('MD5加密前为 ：' + str)
print('MD5加密后为 ：' + hl.hexdigest())
```


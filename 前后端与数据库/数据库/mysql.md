```
mysql> set password for root@localhost = password('123');


ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'password('123')' at line 1
```



原因：数据库版本较新，发生了改变
旧版：

```
UPDATE USER SET PASSWORD = PASSWORD('新密码') WHERE USER = '用户名';
```



新版：

```
alter user '用户名'@'主机名' identified by '新密码';


```

旧版2：

```
SET PASSWORD FOR '用户名'@'主机名' = PASSWORD('新密码');
```



新版2：

```
SET PASSWORD FOR '用户名'@'主机名' = '新密码';
```


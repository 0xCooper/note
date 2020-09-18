启动mysql

```bash
systemctl start mysql
systemctl status mysql #查看服务器mysql运行状态
systemctl status mssql-server#查看一下这个sql-server的运行状态，发现这个sqlserver仍在运行

```

为了连接mysql下载了navicat preminum 15

```sql
grant all privileges on *.* to 'root'@'%' identified by 'bpikwCPslPhG' with grant option;
```

参数说明如下。

- `*.*`参数，第一个“*”为数据库占位符，如果填“*”则代表所有数据库。第二个“*”为数据库对象占位符，如果填“*”则代表数据库中所有对象。
- `'root'@'%'`参数，root为授权登录的数据库账户，“%”为IP地址占位符。假如要限制只能在1.1.1.1登录，则需要把“%”改成1.1.1.1。如果填“%”则代表允许任何IP地址登录。
- `'123456'`参数，该参数为数据库密码。

```bash
mysql -uroot -p[$密码字符串$]
mysql -uroot -pbpikwCPslPhG
```

执行如下SQL语句，刷新权限。

```mysql
flush privileges;
quit#一气呵成  退出  完成 
```



创建了一个数据库与用户

```bash
#账户 admin 密码 admin 对admin具有绝对的权限
#数据库 admin
```


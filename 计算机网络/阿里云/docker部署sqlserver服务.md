[参考教程](https://www.cnblogs.com/hulizhong/p/11271739.html)

官方教程使用docker运行sql server容器镜像

<https://docs.microsoft.com/zh-cn/sql/linux/quickstart-install-connect-docker?view=sql-server-2017&pivots=cs1-bash>

1.从 Microsoft 容器注册表中拉取 SQL Server 2017 Linux 容器映像。

Bash

```bash
sudo docker pull mcr.microsoft.com/mssql/server:2017-latest
```

2. 查看镜像并允许此镜像  运行

```bash
docker images
sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyPassWord123"  -p 1433:1433 --name sql1  -d mcr.microsoft.com/mssql/server:2017-latest
```

然后查看是否允许成功

```
sudo docker ps -a
```

然后这里我们就配置了SQL Server，接下来我们实际进入容器内操作。

```bash
sudo docker exec -it sql1 "bash"

/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "MyPassWord123"
```





出现问题 docker容器出现exit



```
先修改端口试试

中间
```


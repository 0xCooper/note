环境准备

### 安装nodejs

```
curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash -
yum -y install nodejs
```

### 使用npm安装pm2

```
npm install pm2 -g
```

### 安装mysql

```shell
wget http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm
rpm -ivh mysql-community-release-el7-5.noarch.rpm
yum install mysql-community-server -y
```

### 启动mysql服务

```
service mysqld restart
```

设置mysqlroot账户密码

```
/usr/bin/mysqladmin -u root password 'qUgCQvyk4Firekylin'
```

安装ngnix

centos上使用yum安装nginx

```
yum install nginx -y
```

在服务器上下载安装包

```
wget https://firekylin.org/release/latest.tar.gz
```

### 解压安装包

```
tar zvxf latest.tar.gz
```

### 安装程序依赖

```
cd firekylin
npm install
```

### 复制项目下的 `pm2_default.json` 文件生成新文件 `pm2.json`





```
cp pm2_default.json pm2.json
```

### 修改 pm2.json 文件中的 cwd 配置值为项目的当前路径 `/root/firekylin`：

```
{
  "apps": [{
    "name": "firekylin",
    "script": "www/production.js",
    "cwd": "/root/firekylin",
    "exec_mode": "fork",
    "max_memory_restart": "1G",
    "autorestart": true,
    "node_args": [],
    "args": [],
    "env": {

    }
  }]
}
```

### 然后通过以下命令启动项目

```
pm2 startOrReload pm2.json
```

Firekylin 已经启动成功，使用浏览器直接访问 <http://139.199.221.141:8360/> 即可看到 Firekylin 的配置界面。





## 配置信息

通过访问 <http://139.199.221.141:8360/> 配置信息，配置过程输入参数如截图所示，其中数据库信息中的`帐号`字段设置为 `root`，`密码`字段设置为 `qUgCQvyk4Firekylin`，`数据库名`字段设置为 `firekylin`，`主机`字段设置为 `127.0.0.1`，其他字段使用默认值；后台管理帐号中的`帐号`字段使用默认值 `admin`，`密码`字段设置为 `qUgCQvyk4Admin`：

![img](https://mc.qcloudimg.com/static/img/2b6b8757d891a5c67581f64b0c75cc42/1.png)

配置完成后可以通过后台管理帐号设置的`帐号`和`密码`登录博客管理后台，其值分别为 `admin` 和 `qUgCQvyk4Admin`，截图如下所示：

![img](https://mc.qcloudimg.com/static/img/d5b5b0b892c165eb6d80e8a699d22657/1.png)
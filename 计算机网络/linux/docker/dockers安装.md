### centos7 下的 docker的安装

1.查看centos linux的内核版本(必须高于3.10)

```bash
uname -r 
```

2.安装docker

```bash
yum install docker
```

3.启动docker 后台服务

```bash
service docker start
```

## 使用脚本安装 Docker

1、使用 `sudo` 或 `root` 权限登录 Centos。

2、确保 yum 包更新到最新。

```bash
$ sudo yum update
```

3、执行 Docker 安装脚本。

```bash
$ curl -fsSL https://get.docker.com/ | sh
```

执行这个脚本会添加 `docker.repo` 源并安装 Docker。

4、启动 Docker 进程。

```bash
$ sudo service docker start
```

5、验证 `docker` 是否安装成功并在容器中执行一个测试的镜像。

```bash
$ sudo docker run hello-world
```

到此，docker 在 CentOS 系统的安装完成。


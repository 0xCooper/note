```shell
docker启动命令,docker重启命令,docker关闭命令

启动        systemctl start docker
守护进程重启   sudo systemctl daemon-reload
重启docker服务   systemctl restart  docker
重启docker服务  sudo service docker restart
关闭docker service docker stop 
关闭docker systemctl stop docker
```



```
docker ps 当前正在运行的容器名称  参数 -a 查看所有容器  -n 10查看最近10创建的镜像
docker images 列出当前储存在机器中的镜像
docker pull xxx 下载镜像
docker 参数 ：-d后台运行   -p xxxx:xxxx端口映射  （前面是主机端口，后面是虚拟端口）
docker info   ##查看docker容器信息
```

```shell
docker start #启动一个已经停止的容器
docker stop <ID>  #停止一个已容器
docker restart <ID>  #重启一个容器
docker rm -f <ID> # 删除容器
docker attach <ID> #进入某个容器（使用exit推出后容器也会跟着推出）
 docker exec -ti <ID> #启动一个伪终端以交互式的方式进入某个容器（使用exit退出后容器不停止运行）
  docker port mymysql#列出指定端口的映射
```

```
docker中载入ubuntu镜像
docker pull ubuntu
$ docker run -it ubuntu /bin/bash  ——以命令行模式进入
exit 推出ubuntu
```



```shell
运行·web应用

docker pull training/webapp#载入镜像
docker run -d -P taining/webapp python app.py# -P将容器内部使用的端口映射到我们使用的主机上 （随机映射到主机空闲的端口）
docker ps #查看我们运行的容器 可以查到端口容器的映射
docker logs [ID或者名字]#可以查看容器内部的便准输出
docker top [名字] #可以查看容器内部运行的 进程


```

```shell
#Docker的安装  centOS安装方法
uname -a #查看内核版本，确认其版本在3.1以上
#yum update #更新yum包  建议不更新
yum install -y yum-utils device-mapper-persistent-data lvm2
#安装需要的软件包
 yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
 #设置yum的源
 
 yum list docker-ce --showduplicates | sort -r
#查看所有仓库中所有docker版本，并选择特定版本安装
yum install docker-ce-版本号

#上述两部也可以直接运行一步  yum install docker  
systemctl start docker  #启动docker
 
 systemctl enable docker
Created symlink from /etc/systemd/system/multiuser.target.wants/docker.service to /usr/lib/systemd/system/docker.service.#加入开机启动项

docker version #用于验证docker是否安装成功
#client和service两部分表示docker安装启动都成功了
```

```shell
##查看docker容器版本
docker version
##查看docker容器信息
docker info
##查看docker容器帮助
docker --help

##列出本地images
docker images
##含中间映像层
docker images -a
##只显示镜像ID
docker images -q
##含中间映像层
docker images -qa  
```

2.2、镜像搜索

```shell
##搜索仓库MySQL镜像
docker search mysql

## --filter=stars=600：只显示 starts>=600 的镜像

docker search --filter=stars=600 mysql

## --no-trunc 显示镜像完整 DESCRIPTION 描述

docker search --no-trunc mysql

## --automated ：只列出 AUTOMATED=OK 的镜像

docker search  --automated mysql
```

```shell
##下载Redis官方最新镜像，相当于：docker pull redis:latest
docker pull redis
##下载仓库所有Redis镜像
docker pull -a redis
##下载私人仓库镜像
docker pull bitnami/redis
```
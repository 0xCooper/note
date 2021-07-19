```bash
docker commit -a "author" -m "information"  <ID>  name#-a是作者  将容器打包成镜像

```



```shell
docker启动命令,docker重启命令,docker关闭命令

启动        systemctl start docker
守护进程重启   sudo systemctl daemon-reload
重启docker服务   systemctl restart  docker
重启docker服务  sudo service docker restart
关闭docker service docker stop 
关闭docker systemctl stop docker
```

```bash
docker save [ID] > /home/unbuntu-save-time.tar #导出镜像
docker load   <  /home/myubuntu-save-time.tar #加载导入镜像
 docker tag IMAGEID(镜像id) REPOSITORY:TAG（仓库：标签）#命名
 docker tag <ID>  ubuntu:latest 
```

```
docker run -d -p 80:80 -p 22:22 #多个端口映射
```



```bash
docker ps 当前正在运行的容器名称  参数 -a 查看所有容器  -n 10查看最近10创建的镜像
docker images 列出当前储存在机器中的镜像
docker pull xxx 下载镜像
docker 参数 ：-d后台运行   -p xxxx:xxxx端口映射  （前面是主机端口，后面是虚拟端口）
docker info   ##查看docker容器信息
```

```
容器内部的文件复制出来

docker cp  /    /   【id】
```



```bash
容器变成镜像
docker commit -m "提交的信息" -a <ID> NWENAME
```

```shell
docker start #启动一个已经停止的容器
docker stop <ID>  #停止一个已容器
docker restart <ID>  #重启一个容器
docker rm -f <ID> # 删除容器
docker rmi <ID>  #删除镜像
docker attach <ID> #进入某个容器（使用exit推出后容器也会跟着推出）
 docker exec -ti <ID> /bin/bash#启动一个伪终端以交互式的方式进入某个容器（使用exit退出后容器不停止运行）
  docker port mymysql#列出指定端口的映射
```

```
docker中载入ubuntu镜像
docker pull ubuntu
$ docker run -it ubuntu /bin/bash  ——以命令行模式进入
exit 推出ubuntu
```

```bash
dokerhub仓库管理
docker login   #用户登录
docker logout #用户退出
docker push username/unbuntu  #上传镜像
```

#### 查看大小

```
docker system df -v
#查看单个容器大小
```


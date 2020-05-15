```shell
#Docker 官方提供的一键安装脚本，两行命令：
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

```shell
#docker 启动所有容器
docker start $(docker ps -a | awk '{ print $1}' | tail -n +2)
```

```shell
systemctl start docker   #通过systemctl启动服务
```







docker中    关闭所有的容器命令

```dart
docker stop $(docker ps -a | awk '{ print $1}' | tail -n +2)
```

docker中 删除所有的容器命令

```dart
docker rm $(docker ps -a | awk '{ print $1}' | tail -n +2)
```

docker中    删除所有的镜像

```dart
docker rmi $(docker images | awk '{print $3}' |tail -n +2)
```


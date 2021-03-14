##               [sqli-labs 环境搭建（docker）](https://www.cnblogs.com/blogs-1024/p/11128999.html)          

 

```
             步骤：1.运行：docker info     //查看docker信息，确认docker正常

​                        2.搜索sqli-labs：docker search sqli-labs

​                        3.建立镜像：docker pull acgpiano/sqli-labs

​                        4.查看存在的镜像：docker images

​                        5.运行存在的镜像：docker run -dt --name sqli -p 80:80 --rm acgpiano/sqli-labs 

​                                                     //参数解释：-dt  后台运行； --name  命名；-p 80:80  将后面的docker容器端口映射到前面的主机端口。--rm 用于删除数据 这样方便web测试

​                         进入运行中的docker容器：docker exec -it ID号 /bin/bash
```



# 各种linux版本的docker安装

详细docker教程见菜鸟教程

https://www.runoob.com/docker/docker-tutorial.html

# CentOS Docker 安装

Docker 支持以下的 64 位 CentOS 版本：

- CentOS 7 
-  CentOS 8
- 更高版本...

该 centos-extras 库必须启用。默认情况下，此仓库是启用的，但是如果已禁用它，则需要[重新启用它](https://wiki.centos.org/AdditionalResources/Repositories)。

建议使用 overlay2 存储驱动程序。

------

## 卸载旧版本

较旧的 Docker 版本称为 docker 或 docker-engine 。如果已安装这些程序，请卸载它们以及相关的依赖项。

 $ **sudo** **yum remove** docker \
                   docker-client \
                   docker-client-latest \
                   docker-common \
                   docker-latest \
                   docker-latest-logrotate \
                   docker-logrotate \
                   docker-engine

------

## 安装 Docker Engine-Community

### 使用 Docker 仓库进行安装

在新主机上首次安装 Docker Engine-Community 之前，需要设置 Docker 仓库。之后，您可以从仓库安装和更新 Docker。

 **设置仓库**

安装所需的软件包。yum-utils 提供了 yum-config-manager  ，并且 device mapper 存储驱动程序需要 device-mapper-persistent-data 和 lvm2。

 $ **sudo** **yum install** -y yum-utils \
   device-mapper-persistent-data \
   lvm2


使用以下命令来设置稳定的仓库。

 $ **sudo** yum-config-manager \
     --add-repo \
     https:**//**download.docker.com**/**linux**/**centos**/**docker-ce.repo


### 安装 Docker Engine-Community

安装最新版本的 Docker Engine-Community 和 containerd，或者转到下一步安装特定版本：

```
$ sudo yum install docker-ce docker-ce-cli containerd.io
```

如果提示您接受 GPG 密钥，请选是。

> **有多个 Docker 仓库吗？**
>
> 如果启用了多个 Docker 仓库，则在未在 yum install 或 yum update 命令中指定版本的情况下，进行的安装或更新将始终安装最高版本，这可能不适合您的稳定性需求。

Docker 安装完默认未启动。并且已经创建好 docker 用户组，但该用户组下没有用户。

**要安装特定版本的 Docker Engine-Community，请在存储库中列出可用版本，然后选择并安装：**

1、列出并排序您存储库中可用的版本。此示例按版本号（从高到低）对结果进行排序。

 $ **yum list** docker-ce --showduplicates **|** **sort** -r

 docker-ce.x86_64  3:18.09.1-3.el7                     docker-ce-stable
 docker-ce.x86_64  3:18.09.0-3.el7                     docker-ce-stable
 docker-ce.x86_64  18.06.1.ce-3.el7                    docker-ce-stable
 docker-ce.x86_64  18.06.0.ce-3.el7                    docker-ce-stable


2、通过其完整的软件包名称安装特定版本，该软件包名称是软件包名称（docker-ce）加上版本字符串（第二列），从第一个冒号（:）一直到第一个连字符，并用连字符（-）分隔。例如：docker-ce-18.09.1。

```
$ sudo yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io
```

启动 Docker。

```
$ sudo systemctl start docker
```

通过运行 hello-world 映像来验证是否正确安装了 Docker Engine-Community 。

```
$ sudo docker run hello-world
```

# Debian Docker 安装

Docker 支持以下的 Debian 版本：

- Buster 10 
- Stretch 9 (stable) / Raspbian Stretch

Docker Engine-Community 在 x86_64（或 amd64 ）armhf，和 arm64 体系结构上受支持。

------

## 卸载旧版本

Docker 的旧版本被称为 docker，docker.io 或 docker-engine，如果已安装，请卸载它们：

```
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

------

## 安装 Docker Engine-Community

### 使用 Docker 仓库进行安装

在新主机上首次安装 Docker Engine-Community 之前，需要设置 Docker 仓库。之后，您可以从仓库安装和更新 Docker。

Raspbian 用户不能使用此方法！

对于 Raspbian，尚不支持使用仓库进行安装。您必须改为使用 shell 脚本方式。

### 设置仓库

更新 apt 包索引。

```
$ sudo apt-get update
```

安装 apt 依赖包，用于通过 HTTPS 来获取仓库。

 $ **sudo** **apt-get install** \
     apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common


添加 Docker 的官方 GPG 密钥：

```
$ curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```

9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88 通过搜索指纹的后8个字符，验证您现在是否拥有带有指纹的密钥。

 $ **sudo** **apt-key** fingerprint 0EBFCD88

 pub   4096R**/**0EBFCD88 2017-02-22
       Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
 uid                  Docker Release **(**CE deb**)** **<**docker**@**docker.com**>**
 sub   4096R**/**F273FCD8 2017-02-22
 使用以下指令设置稳定版仓库
 $ **sudo** add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/debian **\**    $(lsb_release -cs) **\**    stable"


### 安装 Docker Engine-Community

更新 apt 包索引：

```
$ sudo apt-get update
```

安装最新版本的 Docker Engine-Community 和 containerd ，或者转到下一步安装特定版本：

```
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

要安装特定版本的 Docker Engine-Community，请在仓库中列出可用版本，然后选择一种安装。列出您的仓库中可用的版本：

 $ **apt-cache** madison docker-ce

   docker-ce **|** 5:18.09.1~3-0~debian-stretch **|** https:**//**download.docker.com**/**linux**/**debian stretch**/**stable amd64 Packages
   docker-ce **|** 5:18.09.0~3-0~debian-stretch **|** https:**//**download.docker.com**/**linux**/**debian stretch**/**stable amd64 Packages
   docker-ce **|** 18.06.1~ce~3-0~debian        **|** https:**//**download.docker.com**/**linux**/**debian stretch**/**stable amd64 Packages
   docker-ce **|** 18.06.0~ce~3-0~debian        **|** https:**//**download.docker.com**/**linux**/**debian stretch**/**stable amd64 Packages
   ...


使用第二列中的版本字符串安装特定版本，例如 5:18.09.1~3-0~debian-stretch 。

```
$ sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```

测试 Docker 是否安装成功，输入以下指令，打印出以下信息则安装成功：

$ sudo docker run hello-world



Unable to find image 'hello-world:latest' locally

latest: Pulling from library/hello-world

1b930d010525: Pull complete
                                                                        
                                                          Digest: 
sha256:c3b4ada4687bbaa170745b3e4dd8ac3f194ca95b2d0518b417fb47e5879d9b5f

Status: Downloaded newer image for hello-world:latest





Hello from Docker!

This message shows that your installation appears to be working correctly.





To generate this message, Docker took the following steps:

 1. The Docker client contacted the Docker daemon.

 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.

    (amd64)

 3. The Docker daemon created a new container from that image which runs the

    executable that produces the output you are currently reading.

 4. The Docker daemon streamed that output to the Docker client, which sent it

    to your terminal.





To try something more ambitious, you can run an Ubuntu container with:

 $ docker run -it ubuntu bash





Share images, automate workflows, and more with a free Docker ID:

 https://hub.docker.com/





For more examples and ideas, visit:

 https://docs.docker.com/get-started/

----



# **Ubuntu 16.04 安装 Docker**

1.选择国内的云服务商，这里选择阿里云为例

```
curl -sSL http://acs-public-mirror.oss-cn-hangzhou.aliyuncs.com/docker-engine/internet | sh -
```

2.安装所需要的包

```
sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual
```

3.添加使用 HTTPS 传输的软件包以及 CA 证书

```
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates
```

4.添加GPG密钥

```
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
```

5.添加软件源

```
echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" | sudo tee /etc/apt/sources.list.d/docker.list
```

6.添加成功后更新软件包缓存

```
sudo apt-get update
```

7.安装docker

```
sudo apt-get install docker-engine
```

8.启动 docker

```
sudo systemctl enable docker
sudo systemctl start docker
```
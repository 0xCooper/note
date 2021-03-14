

### 介绍

---

CCAA 是服务器离线下载解决⽅案包，组件包含了Aria2 提供离线下载，ccaa_web⽀撑AriaNg运⾏， 

AriaNg为Aria2 提供WEB界⾯以及Filemanager提供⽂件管理

#### 主要功能

* ⽀持HTTP/HTTPS/FTP/BT/磁⼒链 接等离线下载，断点续传等！
* 文件管理，视频在线播放！

```shell
#国内服务器
bash <(curl -Lsk https://raw.githubusercontent.com/helloxz/ccaa/master/ccaa.sh) cdn
#海外
bash <(curl -Lsk https://raw.githubusercontent.com/helloxz/ccaa/master/ccaa.sh)
```

### Docker安装

```shell
docker run --name="ccaa" -d -p 6080:6080 -p 6081:6081 -p 6800:6800 -p 51413:51413 \
    -v /data/ccaaDown:/root/ccaa \
    -e PASS="xiaoz.me" \
    helloz/ccaa \
    sh -c "dccaa pass && dccaa start"
```

- 第一个`/data/ccaaDown`为本地目录，CCAA下载后的内容会保存在此目录，请根据自身情况设置
- `xiaoz.me`为Aria2密钥，运行的时候请修改为自己的密码
- 文件管理默认用户名为`ccaa`，密码为`admin`，登录后可在后台修改

### 常用命令

- ccaa:进入CCAA操作界面

- ccaa status:查看CCAA运行状态

- ccaa stop:停止CCAA

- ccaa start:启动CCAA

- ccaa restart:重启CCAA

- ccaa -v:查看CCAA版本（2.0开始支持）

  ### 安装详细步骤

  1.这个地方输入 1 

```
Linux + File Browser + Aria2 + AriaNg一键安装脚本(CCAA)
1) 安装CCAA
2) 卸载CCAA
3) 更新bt-tracker
q) 退出！
```

​	2.默认下载路径 可以直接回车

```shell
设置下载路径（请填写绝对地址，默认/data/ccaaDown）:    /root/CCAA
```

​	3.按要求随便就可以

```
Aria2 RPC 密钥:(字母或数字组合，不要含有特殊字符):	 md5qwe    
```

​	4.成功

```shell
-------------------------------------------------------------
大功告成，请访问: http://ip:6080/
File Browser 用户名:ccaa
File Browser 密码:admin
Aria2 RPC 密钥: md5qwe
帮助文档: https://dwz.ovh/ccaa （必看）
-------------------------------------------------------------
```

常见问题
打不开

* 可能是服务器的端口没有打开 

  ```shell
  #主要有以下端口
  -p 6080 -p 6081-p 6800 -p 51413 6998
  ```

  

建议：

这里笔者不建议直接下载
建议通过dockers下载，可以避免很多问题！
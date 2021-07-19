#### 0.避免拒绝弱密码

#### 1.ssh安全

ssh端口可设置在其他端口

#### 2查看安全日志

```bash
tail -30 /var/log/secure
/var/log/cron	与定时任务相关的日志信息
```

```bash
cat /etc/issue	登陆信息显示数据
```

linux安全问题

#### 3.防止任意用户得su具有root权限

#### 4.恶意文件扫描

```
grep '<?php $post[eval[]]'
```


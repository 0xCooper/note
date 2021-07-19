dd命令十分的神奇和好用



dd命令可以用来备份系统,可以复制加密磁盘，可以做起动器



dd命令做usb启动盘十分方便,只须:

```
sudo dd if=xxx.iso of=/dev/u盘 bs=1M
#上面的u盘写sdb,sdc,写自己的设备名
```

将光盘做成iso:

```
用dd做iso
dd if=/dev/cdrom of=/tmp/aaa.iso
```



dd备份恢复系统:

1、备份

```
用liveCD开机，
\# dd if=/dev/sda1 of=sda1.img.bak bs=4M（然后把disk1.bak这个备份文件cp到安全的地方）
```

2、还原

```
用liveCD开机，
# dd if=sda1.img.bak of=/dev/sda1
\# e2fsck -f /dev/sda1
\# resize2fs /dev/sda1
\# e2fsck -f /dev/sda1
```



**注意：**

​    不要直接在计算机上用本地磁盘启动系统后执行dd命令生成本地磁盘的镜像。而应该使用livecd启动计算机。

​    因此计算机运行时会对系统盘产生大量写操作。 直接对运行中的系统盘生成的镜像，在恢复到其他硬盘上时，很可能会无法启动！

**dd用来彻底擦除数据**

```
#擦除数据
dd if=/dev/zero of=/dev/sda conv=notrunc
```

**销毁磁盘数据**

```
dd if=/dev/urandom of=/dev/hda1
#干了坏事不想被抓，就赶紧销毁
注意:利用随机的数据填充硬盘,在某些必要的场合可以用来销毁数据。
```







思考：

备份文件系统

```
dd if=/dev/sda2 of=./sda2.bak
#之后提前分出大小相当的区sdb2
dd if=./sda2.bak of=/dev/sdb2
```







```
1.备份/dev/hdb全盘数据,并利用gzip工具进行压缩,保存到指定路径
dd if=/dev/hdb | gzip > /root/image.gz
2.将压缩的备份文件恢复到指定盘
gzip -dc /root/image.gz | dd of=/dev/hdb
```

```
1.备份磁盘开始的512个字节大小的MBR信息到指定文件
dd if=/dev/hda of=/root/image count=1 bs=512
count=1指仅拷贝一个块;bs=512指块大小为512个字节。
恢复:dd if=/root/image of=/dev/hda
```

参数

```
参数

1. if=文件名:输入文件名,缺省为标准输入。即指定源文件。< if=input file >
2. of=文件名:输出文件名,缺省为标准输出。即指定目的文件。< of=output file >
3. ibs=bytes:一次读入bytes个字节,即指定一个块大小为bytes个字节。
obs=bytes:一次输出bytes个字节,即指定一个块大小为bytes个字节。
bs=bytes:同时设置读入/输出的块大小为bytes个字节。

4. cbs=bytes:一次转换bytes个字节,即指定转换缓冲区大小。
5. skip=blocks:从输入文件开头跳过blocks个块后再开始复制。
6. seek=blocks:从输出文件开头跳过blocks个块后再开始复制。
注意:通常只用当输出文件是磁盘或磁带时才有效,即备份到磁盘或磁带时才有效。
7. count=blocks:仅拷贝blocks个块,块大小等于ibs指定的字节数。
8. conv=conversion:用指定的参数转换文件。
```





远程备份

```
利用netcat和dd做远程备份
在源主机上执行此命令备份/dev/hda：
dd if=/dev/hda bs=16065b | netcat < targethost-IP > 1234
在目的主机上执行此命令来接收数据并写入/dev/hdc：
netcat -l -p 1234 | dd of=/dev/hdc bs=16065b
以下两条指令是目的主机指令的变化分别采用bzip2 gzip对数据进行压缩，并将备份文件保存在当
前目录 ：
netcat -l -p 1234 | bzip2 > partition.img
netcat -l -p 1234 | gzip > partition.img
```


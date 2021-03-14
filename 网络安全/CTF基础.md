```
ctf工具网站
http://www.ctftools.com/down/
```


题目分类

```
web,PPC,crypto,pwn,REVERSE,STEGA,MISC
```

```
CRYPTO 密码学，加解密技术
pwn 攻破，取得权限，多为数据溢出类题目
ERVERSE 逆向工程，软件逆向破解技术
STEGA 隐写术
MISC 安全杂项 ，题目涉及流量分析，电子取证，数据分析
```

#### 获取Flag

##### linux中

```
&find / -name "flag.txt"
cat flag.txt
```











#### 敏感目录

```
robots.txt
.ssh
```

![image-20201215184922639](../img/image-20201215184922639.png)











### flag

```
	  对应密文
flag  ZmxhZ3  #Base64加密

```

### gif隐写术

```
convert 1.gif 02d%.png #分离图片
binwalk 2.gif  #分析文件
binwalk -e  2.gif  #分离图片
foremost -T 2.gif #foremost分离

```

![img](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1607237840379&di=f7dd6990aaf6a99b6d6ea1ad8954da50&imgtype=0&src=http%3A%2F%2Fwww.php3.cn%2Fupload%2Fckfinder%2Fimages%2F2013102402153121543.gif)



杂项
rar






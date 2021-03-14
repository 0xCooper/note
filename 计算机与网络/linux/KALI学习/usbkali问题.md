步骤
1.下载iso镜像  www.kali.org
2.用软件写入U盘

问题1.可能存在不能不能从bios界面中读取的问题
优盘启动kali找不到文件

1. ,下载工具Universal-USB-Installer、kali-linux镜像

   用到Universal-USB-Installer-1.9.3.1，低于1.9.3.1版本的，在选择系统类型的时候找不到kali linux，制作的系统安装盘在安装系统的时候容易出问题。

   kali-linux的下载页面，百度搜索吧，不许贴网址，自己根据需要下载版本

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=6ee03d93cc8065387beaa413a7dfa115/cf1b9d16fdfaaf510e2d39628a5494eef11f7a25.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=1)

2. 2

   2、制作U盘系统安装盘

   （1）打开Universal-USB-Installer，选择I agree。

   （2）选择系统类型为kali linux,选中kali linux的系统ISO文件，然后选中插入电脑的U盘盘符，点击”Create”就会制作好U盘系统安装盘。

   （3）刻录完成之后点击close即可完成刻录

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=a1205eb5cabf6c81f7372ce88c3fb1d7/d53f8794a4c27d1eefb981191dd5ad6edcc4384b.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=2)

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=3cec11263fdbb6fd255be5263925aba6/cefc1e178a82b90127a666ee758da9773812efe0.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=3)

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=836f90043f01213fcf334edc64e636f8/dc54564e9258d109bda10d6fd758ccbf6d814da8.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=4)

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=9f947730e11190ef01fb92dffe1a9df7/32fa828ba61ea8d3e7bed3d9910a304e241f584a.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=5)

3. 3

   3、开始kali  linux的安装，将U盘插入到要装系统的电脑，设置BIOS支持U盘启动，就会看到kali linux的安装界面。选择install,或者下面的一项（Graphical install-图形界面），建议新手选择这项然后进行安装。

   如果出现提示“not a COM32R image.Boot:"，这时候按一下”Tab“键后会出现命令选项，这是再输入Graphical install就可以了

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=66b945e41fd8bc3ec60806cab28aa6c8/7c1ed21b0ef41bd5a756182a57da81cb38db3de2.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=6)

   END

## 方法2/步骤

1. 

   如果按照上面的方法在电脑上启动的时候找不到U盘，可以尝试使用UltraISO来刻录Kali Linux镜像文件。步骤如下：

2. 

   1、打开UltraISO，点击文件-打开，打开Kali Linux镜像文件。

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=50d77790cc8065387beaa413a7dfa115/cf1b9d16fdfaaf51301a73618a5494eef11f7a77.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=7)

3. 

   2、点击启动--写入硬盘映像文件。

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=4d6c15f508f41bd5da53e8f461db81a0/0b55b319ebc4b74573db45c8c9fc1e178b8215a4.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=8)

4. 

   3、弹出写入镜像对话框，先格式化U盘，如果U盘已经格式化，则点击”写入“进行刻录操作，等待刻录完成。

   [![用U盘安装Kali linux系统](https://imgsa.baidu.com/exp/w=500/sign=374881ba0f23dd542173a768e108b3df/4610b912c8fcc3ce3fa634ed9445d688d53f208e.jpg)](http://jingyan.baidu.com/album/375c8e19c2a65b25f2a229b7.html?picindex=9)

5. 5

   4、刻录完成之后，操作步骤如方法1最后一步。

   END

## 注意事项

- U盘需要4G

  ```
  来源：百度经验
  
  ```


# 持久加密盘

```bash
#将镜像刻度到U盘
dd if=kali-linux-1.1.0-amd64.iso of=/dev/sdb bs=1M
```


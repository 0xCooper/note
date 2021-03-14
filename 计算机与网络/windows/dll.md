 须注册所有dll文件,才能解决内存不能为read等问题 
系统dll文件没有注册，可能引起各种各样不可知的问题，比如无法打开二级链接，经常出现“内存不能为read或written”等错误。如何一下把所有的dll文件重新注册一遍呢？ 

点击:开始-->运行,在运行框中输入cmd，在命令提示符下输入： 

```bash
for %1 in ([%windir%](https://www.baidu.com/s?wd=%25windir%25&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)\system32\*.dll) do regsvr32.exe /s %1   
```


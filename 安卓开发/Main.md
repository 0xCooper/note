#### XML

```xml
<?xml vsersion="1.0" encoding="utd-8"?>
<中国>
	<北京>
		<海定></海定>
	<北京>
<中国>
<!--这是注释-->
```

```
xml语法
文档声明
元素
属性
注释
CDATA
特殊字符           XML只能有一个跟标签
元素要求：不能以数字下划线开头  不能以xml开头
属性：   <person name="liufeng">
<!---->
```

```
<![CDATA][]>CDATA里的内容不会被解析
&lt   <
&gt   >
&quot "
&apos '
```

#### xml约束

约束文档定义了xml中允许出现的元素名称，属性及元素出现的顺序

###### DTD

```
1.引入文档
<?xml version="1.0"?>
<!DOCTYPE 书架 SYSYTEM "BOOK.did">
<书架>
</书架>
```



###### schema


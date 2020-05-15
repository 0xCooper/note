# Java环境变量配置

C:\Program Files\Java\jdk-13.0.1\

在 "系统变量" 中设置 3 项属性，JAVA_HOME、PATH、CLASSPATH(大小写无所谓),若已存在则点击"编辑"，不存在则点击"新建"。

-  变量名：**JAVA_HOME** 
-  变量值：**C:\Program Files (x86)\Java\jdk1.8.0_91**         // 要根据自己的实际路径配置

-  变量名：**CLASSPATH** 
-  变量值：**.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;**          //记得前面有个"."

- 变量名：**Path**
- 变量值：**%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;**

### 测试JDK是否安装成功

1、"开始"->"运行"，键入"cmd"；

2、键入命令: **java -version**、**java**、**javac** 几个命令，出现以下信息，说明环境变量配置成功；

 ![img](https://www.runoob.com/wp-content/uploads/2013/12/java-win9.png)
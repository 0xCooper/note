**选择了vim编辑器**

版本 2.221.0


Git工作流程  工作区->暂存区->仓库

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png)

Git工作区域    ： 新建修改代码

gitstatus ：当前文件状况
git add hello.php：  将hello.php文件上传到暂存区
git add test.php ： 同上

gitstatus ：查看状态
git commit -m 文件名 :提交描述，将文件从暂存区提交到仓库

gitstatus :查看状态结束

###### git初始化

1.设置用户名
git config --global user.name "Mu815"
2.设置用户邮箱
git config --global user.email "MYC2019410@163.com"
3.git config --list  :查看设置

注意：该设置在github主页显示了谁提交了该文件

###### 初始化一个新的Git仓库

1.创建文件夹  mkdir test
2.在文件内初始化git(创建仓库)  cd
3.git init  :创建了一个隐藏文件

添加文件

1.touch    创建文件
git add a.php  :添加到暂存区
git  sataus

###### 修改仓库文件

1.vi a1.php :用vi编辑器
2.重复上面操作

###### 删除仓库文件

1.rm -rf a1.php   ：删除本地文件
2.git rm a1.php
3.git commit -m "第一次删除仓库文件"

## Git远程仓库

如何将本地仓库同步到远程仓库
git push 

###### git克隆

git clone 【仓库地址】

###### 同步到远程仓库

git push

<!--如果git push 没有权限
vi .git/config
将[remote="origin"]
url = https ://github.com/用户名/仓库名.git
修改为
[remote ="origin"]
url =https://用户名：密码@github.com/用户名/仓库名.git-->


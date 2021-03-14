# win10无法使用内置管理员账户打开应用怎么办



Win10管理员账户Administrator默认关闭和隐藏，就是防止这个高权限账户被“滥用”影响系统安全。不过我们有时候也需要开启该账户，以便 完成一些特殊任务。但我们在登录Windows10管理员账户后却发现，所有Windows应用都无法运行，甚至有部分用户反映连开始菜单都无法打开（个 别现象），因为Win10的开始菜单也是Windows应用。【下方的“特别注意”需阅读】

[![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=cdb3485ecf3d70cf4cfaaa0dc8ddd1ba/7a899e510fb30f24f02af664ce95d143ad4b0320.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=1)



[![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=e7be07a4d643ad4ba62e46c0b2035a89/8ad4b31c8701a18bb95be84e992f07082838fe7b.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=2)



## 方法/步骤

1. 1

   ​     **视频参考：**

   

2. 2

   首先，按住键盘，Windows+R，Windows键就是有是个方块的图形按键，Alt旁边。按下之后，在里头输入：**secpol.msc**，如图所示：

   [![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=e7aff94bddb44aed594ebee4831d876a/3c6d55fbb2fb43160c95807b27a4462309f7d32d.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=3)

3. 3

   输入完毕，回车(确认)，来到“**本地安全策略编辑器**”如图所示，然后，按照图片上的，依次打开：**安全设置>本地策略>安全选项>用户帐户控制：用于内置管理员帐户的管理审批模式，**然后，双击它，将改为：**已启用，**点击应用，再点确定。如图所示：

   [![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=0ce7dae065d9f2d3201124ef99ec8a53/eaf81a4c510fd9f9a039b068222dd42a2834a481.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=4)

   [![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=acd4bcbcae773912c4268561c8188675/f603918fa0ec08fa0beae9a65eee3d6d54fbdacd.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=5)

4. 4

   确定完了，**一定要重启你的电脑**。重启完了，看看，是不是可以打开应用了。看，打开日历，正常。

   [![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=d1dce2c4e7fe9925cb0c695004a95ee4/c83d70cf3bc79f3d13291e31bda1cd11738b29e3.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=6)

   END

## 方法二（上面的失败）

1. 1

   也是一样，按住键盘，Windows+R，按下之后，在里头输入：**regedit**，回车，完了，打开注册表编辑器。

2. 2

   **在注册表编辑器中定位到以下位置（依次打开）：**

   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System

3. 3

   在右边找到**FilterAdministratorToken**，双击后将数值数据改为“1”后点击“确定”。

   [![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=bb559369b73533faf5b6932e98d2fdca/0ff41bd5ad6eddc4f357ae9c3fdbb6fd52663320.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=7)

4. 4

   **注意**：如果右边没有这个“FilterAdministratorToken”，则需要手动在右边空白处点击鼠标右键，新建 DWORD（32位）值，并更名为FilterAdministratorToken，将其数值数据改为1。

5. 5

   改完了之后，还要改另外一个，也是一样，依次找到：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System \UIPI**

6. 6

   我们看到，右边有个默认的项。将它的值改成1，如图所示：

   [![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=4c299ef3d262853592e0d221a0ee76f2/18d8bc3eb13533fa55f2772fafd3fd1f41345b6f.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=8)

7. 7

   两个改完了，**重启电脑**。即可。如果改了之后，仍然无解。那说明就是其他问题了。如下方的【特别注意】

   END

## 【特别注意】

1. 

   很多人，不知不觉随意去改系统的账户控制。也许是杀毒软件帮你改，也许是优化软件帮你改。将账户控制调低，或者关闭。但要注意：系统的账户控制初始是【默认】，不要去乱改。改了就影响了。

   

   **恢复方法：**控制面板—系统和安全—更改用户账户控制。把滑块调整至默认。完了确定即可。如下图所示：

   [![win10无法使用内置管理员账户打开应用怎么办](https://imgsa.baidu.com/exp/w=500/sign=f105c2ace7fe9925cb0c695004a85ee4/c83d70cf3bc79f3d33f03e59bda1cd11728b2942.jpg)](http://jingyan.baidu.com/album/455a9950a096a4a166277896.html?picindex=9)

   END

## 注意事项

- 本经验中的Win10为官方原版新装的，所有一切均为出厂默认状态。由于您的后期使用，如更改设置。那么可能与本经验Win10有不同之处，这一点需要特别强调。本经验将按照系统默认状态为准的。
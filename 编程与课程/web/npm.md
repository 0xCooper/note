### npm是nodejs的包管理器

```shell
npm -v #查看版本
```

```shell
sudo npm install npm -g #升级


```

```shell
#安装淘宝镜像
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

### npm安装nodejs模块

```shell
npm install <Module Name>
```

```shell
npm install express
#安装好之后，express 包就放在了工程目录下的 node_modules 目录中，因此在代码中只需要通过 require('express') 的方式就好，无需指定第三方包路径。

var express = require('express');
```

### 全局安装与本地安装

```
npm install express          # 本地安装
npm install express -g   # 全局安装
```

### 查看安装信息

你可以使用以下命令来查看所有全局安装的模块：

```
$ npm list -g

```

如果要查看某个模块的版本号，可以使用命令如下：

```
$ npm list grunt


projectName@projectVersion /path/to/project/folder
└── grunt@0.4.1
```

### 关于packages,json

package.json 位于模块的目录下，用于定义包的属性。

### Package.json 属性说明

- **name** - 包名。
- **version** - 包的版本号。
- **description** - 包的描述。
- **homepage** - 包的官网 url 。
- **author** - 包的作者姓名。
- **contributors** - 包的其他贡献者姓名。
- **dependencies** - 依赖包列表。如果依赖包没有安装，npm 会自动将依赖包安装在 node_module 目录下。
- **repository** - 包代码存放的地方的类型，可以是 git 或 svn，git 可在 Github 上。
- **main** - main 字段指定了程序的主入口文件，require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。
- **keywords** - 关键字

### 卸载模块

我们可以使用以下命令来卸载 Node.js 模块。

```
$ npm uninstall express
```



卸载后，你可以到 /node_modules/ 目录下查看包是否还存在，或者使用以下命令查看：

```
$ npm ls
```

### 更新模块

我们可以使用以下命令更新模块：

```
$ npm update express
```

### 创建模块

创建模块，package.json 文件是必不可少的。我们可以使用 NPM 生成 package.json 文件，生成的文件包含了基本的结果。
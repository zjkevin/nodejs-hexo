---
title: npm操作
tags:
  - nodejs
  - 默认
categories: nodejs
kind: nodejs
date: 2016-12-18 20:48:53
permalink: mpm
---

### 包安装
有了node.js服务端，我们跟使用python一样，要找一个包安装管理工具，NPM登场
```{bash}
$ npm -v
$ npm --version
```

### npm的升级
```{bash}
$ npm install npm -g
```

### 全局安装和本地安装
命令差别就是有没有-g
```{bash}
$ npm install npm [-g]
```
本地安装，安装包会放在npm运行的目录下的node_modules文件夹下，没有则创建该文件夹
全局安装，安装包会在/usr/local下或者node的安装目录,全局有效，哪里都可以引用

### 查看全局安装模块
```{bash}
$ npm ls -g
```

### 有来有去，怎么安装，就怎么卸载,加个un就可以
```{bash}
$ npm uninstall npm [-g]
```

### 更新模块
```{bash}
$ npm update <package>
```

### 搜索模块
```{bash}
$ npm search <package>
```

### 版本号
NPM使用语义版本号来管理代码
语义版本号分为X.Y.Z三位，分别代表主版本号、次版本号和补丁版本号 
1、如果只是修复bug，需要更新Z位。
2、如果是新增了功能，但是向下兼容，需要更新Y位。
3、如果有大变动，向下不兼容，需要更新X位。
版本号有了这个保证后，在申明第三方包依赖时，除了可依赖于一个固定版本号外，还可依赖于某个范围的版本号。例如"argv": "0.0.x"表示依赖于0.0.x系列的最新版argv。

### 安装指定版本号
```{bash}
npm install <package>:0.0.1 [-g]
npm install "lodash":"=3.8.0"
npm install "lodash":"3.8.0"
npm install lodash@3.8.0
npm install "lodash":">3.8.0"
npm install "lodash":"<3.8.0"
npm install "lodash":"<=3.8.0"
npm install "lodash":">=3.8.0"
```

### ^ (caret，插入符)和 ~ (tilde，波浪符)
3.1.1 含义和对比
用法举例
| 版本号写法        | 含义           | 中文解释  |
| ------------- |:-------------:| -----:|
| ^4.11.1 | Compatible with 4.11.1 4.11.1 <= version < 5.0.0 （ 4.x.x 且 >=4.11.1 ） | 主版本号不变 |
| ~4.11.1 | Reasonably close to 4.11.1 4.11.1 <= version < 4.12.0 （ 4.11.x 且 >=4.11.1 ）| 主版本号和次版本号都不变 |

使用 ^ 会更激进，因为它会获得“尽可能新的且能够保持兼容性的版本” 而使用 ~ 会更温和更保险，因为它会获得“尽可能靠近指定版本的升级版本”。 

例外场景 0.x.x 
任何规则都有例外。 0.x.x 版本意味着“Anything can change at any time.”。主版本号为 0 是为了做快速开发。在版本成型之前，开发者可以任意更改其代码，甚至做不兼容的变更而不受约束，然后通过修改次要版本，来控制版本；如果你的软件被用于正式环境，或已经有了稳定的 API 被使用者依赖，则将其升级到 1.0.0 版本或以上。
因此，针对 0.x.x ，指定其依赖版本号时会更趋于谨慎，而 ^ 的行为也变得和 ~ 一样了。例如 ^0.3.0 和 ~0.3.0 取值都是 0.3.0 <= version < 0.4.0 


### npm install xx [exclusive]
-S, --save: Package will appear in your dependencies.         发布产品依赖
-D, --save-dev: Package will appear in your devDependencies.  开发产品依赖，如单元测试等
-O, --save-optional: Package will appear in your optionalDependencies.  好随意的依赖，哈哈
---
title: node.js的安装
date: 2016-06-30 13:29:24
permalink: nodejs_install
tags:
- nodejs
- 技术平台
categories: 日志
---

### 简介
Node.js 就是运行在服务端的 JavaScript。Node.js 是一个基于Chrome JavaScript 运行时建立的一个平台。Node.js是一个事件驱动I/O服务端JavaScript环境，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。-_-! 性能到底怎么样不用是不知道的，这辈子汽车的V8引擎估计是用不上了，这个V8还是可以尝试一下。

根据你的系统平台去官网下载相应安装包[node.js官网](https://nodejs.org)

感觉linux下面第一个命令都要查看版本
```{bash}
$ node -v
$ node --version
```

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

创建模块 暂不介绍，因为还没打算实际项目引入node.js 本篇仅做基本了解，一切疑问查询官网或者npm help

[文档](./public/1.rar)
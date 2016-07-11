---
title: bootstrap细节
tags:
  - bootstrap
  - 默认
categories: bootstrap
kind: bootstrap
date: 2016-07-05 17:03:29
---


bootstrap-3.3.6 包结构
```{bash}
├─css
│      bootstrap-theme.css        
│      bootstrap-theme.css.map
│      bootstrap-theme.min.css
│      bootstrap-theme.min.css.map
│      bootstrap.css
│      bootstrap.css.map
│      bootstrap.min.css
│      bootstrap.min.css.map
│
├─fonts
│      glyphicons-halflings-regular.eot
│      glyphicons-halflings-regular.svg
│      glyphicons-halflings-regular.ttf
│      glyphicons-halflings-regular.woff
│      glyphicons-halflings-regular.woff2
│
└─js
        bootstrap.js
        bootstrap.min.js
        npm.js
```

#### bootstrap会引用到一些google字体，中国特色，网上有一些国内CDN，如 http://fonts.useso.com

写一个python 实现字体的自动离线下载，保存到本地，因为我们的系统很有可能运行在内网环境，某人说google字体只针对英文，那就能够让英文字体好看一点就尽量好看一下，^_~。
脚本思路：
输入:
http://fonts.googleapis.com/css?family=Roboto:400,100,300,500
1. 从我们的国内CDN列表中，选择一个可以访问的站点，将输入URL替换成如下
   http://fonts.useso.com/css?family=Roboto:400,100,300,500
2. 获取替换后URL所对应的CSS文件

3. 解析CSS文件中的字体url,逐一下载到本地，按照CDN默认的层级关系存放字体文件

4. 修改对应的CSS文件中字体url为本地，将该CSS文件存入本地

输出：
存入本地的CSS文件地址
css/family=Roboto-400_100_300_500.css
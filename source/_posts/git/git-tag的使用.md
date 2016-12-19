---
title: git_tag的使用
tags:
  - git
  - 开发工具
categories: 开发工具
kind: git
date: 2016-11-14 15:09:30
permalink: git_tag
---


#### 打标签

```{bash}
git tag -a v0.0.1 -m "0.0.1版本"
```

#### 推送标签到服务端
```{bash}
git push origin v0.0.1
```

#### 查看该标签信息

```{bash}
git show v0.0.1
```

#### 列出该分支上的所有tag

```{bash}
git tag
```


#### 切换到该tag
```{bash}
git checkout v0.0.1
```

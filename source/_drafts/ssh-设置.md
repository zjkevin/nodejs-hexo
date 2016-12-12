---
title: ssh_设置
kind: ssh
tags:
---

### 常用设置

#### 允许root远程登录

    /etc/ssh/sshd_config
    修改配置节：
    PermitRootLogin without-password ---> PermitRootLogin yes

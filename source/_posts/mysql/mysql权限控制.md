---
title: mysql权限控制
tags:
  - mysql
  - 默认
categories: mysql
kind: mysql
date: 2016-12-20 15:02:38
permalink: mysql_privileges
---

CREATE USER rbac IDENTIFIED BY 'rbacerHY123@#'; 

### 用户授权，很暴力的给了所有权限，数据库是DBA的活，细的权限交付生产环境让他们去折腾
```{bash}
grant all privileges on cmdb.* to 'cmdb'@'%' identified by 'cmdberHY123@#';
grant all privileges on cmdb.* to 'cmdb'@'localhost' identified by 'cmdberHY123@#';
grant all privileges on rbac.* to 'rbac'@'localhost' identified by 'rbacerHY123@#';
grant all privileges on rbac.* to 'rbac'@'%' identified by 'rbacerHY123@#';

flush privileges;


grant all privileges on cmdb1.* to 'cmdb'@'%' identified by 'cmdberHY123@#';
grant all privileges on cmdb1.* to 'cmdb'@'localhost' identified by 'cmdberHY123@#';
flush privileges;


grant all privileges on *.* to 'cmdb'@'%' identified by 'cmdberHY123@#';
```


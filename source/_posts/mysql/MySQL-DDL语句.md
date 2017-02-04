---
title: MySQL_DDL语句
tags:
  - mysql
  - 默认
categories: mysql
kind: mysql
date: 2017-01-22 11:06:39
permalink: mysql_ddl
---

### 建库语句
```sql
    CREATE DATABASE redmine DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
```
grant all privileges on redmine.* to 'redmine'@'%' identified by 'redmine';
grant all privileges on redmine.* to 'redmine'@'localhost' identified by 'redmine';
CREATE USER redmine IDENTIFIED BY 'redmine';
flush privileges;
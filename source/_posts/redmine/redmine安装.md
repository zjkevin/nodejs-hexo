---
title: redmine安装
tags:
  - redmine
  - 默认
categories: redmine
kind: redmine
date: 2016-12-22 14:37:47
permalink: redmine_install
---

之前的一台服务器上运行了几年的redmine，玩一把迁移,版本redmine-2.5.2

<!--more-->

### redmine迁移
```{bash}
cp redmine-2.5.2.tar.gz /var/www/
cd /var/www/
tar -xzvf redmine-2.5.2.tar.gz 
cd redmine-2.5.2
# 配置mysql数据库，将原来的库导入
vim database.yml

# gem源设置方法
gem sources -a https://gems.ruby-china.org/
gem sources -l
gem sources --remove https://ruby.taobao.org/


# 通过Gemfile文件安装
cd /var/www/redmine-2.5.2
bundle install --without development test rmagick

# 启动
ruby script/rails server webrick -e production
```

### 很久没用那个平台,admin密码忘记了
用ruby代码修改
```ruby
./rails console production

admin_user = User.find_by_login('admin')
admin_user.password = 'xxxxxx'
admin_user.save
```
### 启动之后发现附件页面报错

在redmine配置确定附件的地址，确认该地址的权限是否有问题，发现没有问题，最后发现是新的mysql的sql_mode和原先旧服务器上的设置不一样

修改mysql配置文件，my.cnf，跟旧服务器保持一致，mysql的sql_mode控制着数据库的行为，不一样的设置会有不一样的约束，很重要
```{bash}
vim /etc	/mysql/my.cnf
[mysqld]
sql_mode = ''
```

```sql
# 查看当前mysql服务器的引擎
show engines;
# 查看当前mysql的模式
show variables like 'sql_mode';
```

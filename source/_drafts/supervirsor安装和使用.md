---
title: supervirsor安装和使用
kind: 进程监控管理
tags:
---


#### 安装

Supervisor is known to work with Python 2.4 or later but will not work under any version of Python 3.

Python2.4以上，但是暂不支持Python3

python2 -m pip install supervisor
如果python2的pip没安装 请执行easy_install-2.7 pip安装

或者
下载压缩包安装
```{bash}
    wget <网址>supervisor-3.3.1.tar.gz
    tar -xzvf supervisor-3.3.1.tar.gz 
    cd supervisor-3.3.1
    python setup.py install
```

检查你的环境变量，supervisor的命令在 /usr/local/python2.7/bin/下，根据你系统的python安装情况自行匹配位置
确保/usr/local/python2.7/bin/ 加入PATH中，否则你只能cd到/usr/local/python2.7/bin/去操作
```{bash}    
    /etc/profile.d/
    vim supervirsor.sh
    加入一行 export PATH=/usr/local/python2.7/bin:$PATH 
```

### 创建配置文件
```{bash}
$ echo_supervisord_conf > /etc/supervisord.conf
$ mkdir -p /etc/supervisor/conf.d/
$ vim /etc/supervisord.conf
# 添加托管程序的配置文件目录
[include]
files = /etc/supervisor/conf.d/*.conf
```

### 开机自启动

#### systemd配置
```{bash}
vim /lib/systemd/system/supervisord.service
# 内容如下
[Unit]
Description=Supervisord
After=network.target

[Service]
Type=forking
ExecStart=/usr/bin/supervisord -c /etc/supervisor/supervisord.conf 
ExecStop=/usr/local/bin/supervisorctl shutdown 
ExecReload=/usr/local/bin/supervisorctl reload 
KillMode=process 
Restart=on-failure
RestartSec=42s

[Install]
WantedBy=multi-user.target
# 加入systemd
$ systemctl enable supervisord
# 验证
$ systemctl is-enabled supervisord
```

### supervisord web界面
```{bash}
[inet_http_server]         ; inet (TCP) server disabled by default
port=*:9001        ; (ip_address:port specifier, *:port for all iface)

[supervisorctl]
serverurl=unix:///tmp/supervisor.sock ; use a unix:// URL  for a unix socket
serverurl=http://127.0.0.1:9001 ; use an http:// url to specify an inet socket
```
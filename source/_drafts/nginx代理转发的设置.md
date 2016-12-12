---
title: nginx代理转发的设置
kind: nginx
tags:
---

### 需求 代理服务器分发，宕机能够自动剔除

#### 健康监测需要安装第三方组件

```shell

    server {
        listen 10001;
        #server_name  www.zhangjiesoft.com;
        #access_log  logs/host.access.log  main;
        location / {
            proxy_pass   http://rbac;
            proxy_set_header Host $host;
            proxy_set_header X-Forward-For $remote_addr;
            #proxy_set_header   X-Real-IP        $remote_addr;
            #proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
        }
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
        #location = /stats {
        #    healthcheck_status;
        #} 
    }

    upstream  rbac {
            server 127.0.0.1:11001;
            server 127.0.0.1:11002;
            #server 127.0.0.1:10003;
            #server 127.0.0.2:10001;
            #开启健康探测功能
            #healthcheck_enable;
            #health_check;
            #设置健康检测的时延
            #healthcheck_delay  1000;     
            #设置健康检测的超时时间
            #healthcheck_timeout  1000;
            #后方某台服务器有一次检测不到即视为宕掉
            #healthcheck_failcount  1
            #使用GET方法访问后方服务器站点下的.health来进行探测 
            #healthcheck_send  "GET /.health HTTP/1.0"     
    }

    server {
        listen       11001;
        #server_name  rbac;
        #access_log  logs/host.access.log  main;
        location / {
            #proxy_pass   http://127.0.0.1:11001;
            proxy_set_header Host $host;
            proxy_set_header X-Forward-For $remote_addr;
            #proxy_set_header   X-Real-IP        $remote_addr;
            #proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
            proxy_connect_timeout 1;
        }
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }    
    }

    server {
        listen       11002;
        #server_name  rbac;
        #access_log  logs/host.access.log  main;
        location / {
            #proxy_pass   http://127.0.0.1:11002;
            proxy_set_header Host $host;
            proxy_set_header X-Forward-For $remote_addr;
            proxy_connect_timeout 1;
            #proxy_set_header   X-Real-IP        $remote_addr;
            #proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
        }
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
    }


    #server {
    #    listen       8080;
    #    server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
    #    error_page   500 502 503 504  /50x.html;
    #    location = /50x.html {
    #        root   html;
    #    }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    #}
    #include /usr/local/nginx/vhosts/*;


    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}   
```

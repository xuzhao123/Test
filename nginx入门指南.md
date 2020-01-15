---
title: nginx入门指南
categories: nginx
---

## 安装

nginx安装步骤如下:
```bash
yum install -y gcc
yum install -y gcc-c++
yum install -y pcre pcre-devel
yum install -y zlib zlib-devel
yum install -y openssl openssl-devel
wget http://nginx.org/download/nginx-1.17.6.tar.gz
tar -zxvf nginx-1.17.6.tar.gz
cd  nginx-1.17.6
./configure
make make install
```
安装完毕

## 常用操作

### 查询nginx运行目录
```bash
ps -ef | grep nginx

root     18918 18656  0 23:14 pts/0    00:00:00 grep --color=auto nginx
root     24996     1  0  2019 ?        00:00:00 nginx: master process /usr/local/nginx/sbin/nginx
root     24997 24996  0  2019 ?        00:00:00 nginx: worker process
```

### 验证配置是否正确
```bash
nginx -t
```

### 停止nginx
```bash
nginx -s stop
nginx -s quit
```

### 重启nginx
```bash
nginx -s reload
```

### nginx配置https
```bash
# 1. 下载完证书文件，将证书文件保存到nginx安装目录
scp -r [本地证书文件目录] [账号]@[nginx服务器ip]:[服务器证书文件目录]
# 2. 修改nginx暗转目录 conf/nginx.conf，修改为如下
    # HTTPS server
    server {
        listen 443 ssl;   #SSL协议访问端口号为443。此处如未添加ssl，可能会造成Nginx无法启动。
        server_name localhost;  #将localhost修改为您证书绑定的域名，例如：www.example.com。
        root html;
        index index.html index.htm;
        ssl_certificate cert/domain name.pem;   #将domain name.pem替换成您证书的文件名。
        ssl_certificate_key cert/domain name.key;   #将domain name.key替换成您证书的密钥文件名。
        ssl_session_timeout 5m;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;  #使用此加密套件。
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;   #使用该协议进行配置。
        ssl_prefer_server_ciphers on;   
        location / {
        root html;   #站点目录。
        index index.html index.htm;   
        }
    }
# 3. 重启nginx
nginx -s reload
```
一般来讲，做完上述操作就已经开启了https。

同时也可以将http强行跳转到https
```bash
# 在nginx.conf中，加上rewrite记录
    server {
        listen       80;
        server_name  localhost;
        rewrite ^(.*)$ https://$host$1 permanent;    
    } 
```
另外可能会出现这样一句报错 [emerg] the "ssl" parameter requires ngx_http_ssl_module in /usr/local/nginx/conf/nginx.conf，提示是没有安装ssl模块导致，需要重新安装nginx。
```
# 进入nginx源码包
./configure --prefix=/usr/local/nginx --with-http_stub_status_module --with-http_ssl_module
make
# 备份原有nginx
cp /usr/local/nginx/sbin/nginx /usr/local/nginx/sbin/nginx.bak
# 关闭nginx运行，覆盖nginx
nginx -s stop
cp ./objs/nginx /usr/local/nginx/sbin/
# 启动
nginx
```






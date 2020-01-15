---
title: nginx安装指南
categories: nginx
---

# nginx入门指南

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

`查询nginx运行目录`
```bash
ps -ef | grep nginx

root     18918 18656  0 23:14 pts/0    00:00:00 grep --color=auto nginx
root     24996     1  0  2019 ?        00:00:00 nginx: master process /usr/local/nginx/sbin/nginx
root     24997 24996  0  2019 ?        00:00:00 nginx: worker process
```

`验证配置是否正确`
```bash
nginx -t
```

`停止nginx`
```bash
nginx -s stop
nginx -s quit
```

`重启nginx`
```bash
nginx -s reload
```


---
title: nginx安装指南2
categories: nginx
---

# nginx安装指南

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
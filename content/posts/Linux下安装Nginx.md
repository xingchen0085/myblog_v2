---
title: "Linux下安装Nginx"
date: 2017-12-18T14:34:07+08:00
draft: false
toc: true
---
## 介绍
Nginx("engine x")是一款是由俄罗斯的程序设计师Igor Sysoev所开发高性能的 Web和 反向代理 服务器，也是一个 IMAP/POP3/SMTP 代理服务器。在高连接并发的情况下，Nginx是Apache服务器不错的替代品。

## 环境
Nginx 安装
系统平台：CentOS release 6.8 (Final) 32位。


## 安装开始
一、安装编译工具及库文件

```bash
yum -y install make zlib zlib-devel gcc-c++ libtool  openssl openssl-devel
```

二、首先要安装 PCRE

PCRE 作用是让 Nginx 支持 Rewrite 功能。

1、下载 PCRE 安装包，下载地址： http://downloads.sourceforge.net/project/pcre/pcre/8.35/pcre-8.35.tar.gz 

[root@bogon server]# wget http://downloads.sourceforge.net/project/pcre/pcre/8.35/pcre-8.35.tar.gz
2、解压安装包:

```bash
[root@bogon server]# tar zxvf nginx-1.6.2.tar.gz
```
3、进入安装包目录

```bash
[root@bogon server]# cd nginx-1.6.2
```
4、编译安装 

```bash
[root@bogon nginx-1.6.2]# ./configure --prefix=/usr/local/server/nginx --with-http_stub_status_module --with-http_ssl_module --with-pcre=/usr/local/server/pcre-8.35
[root@bogon nginx-1.6.2]# make
[root@bogon nginx-1.6.2]# make install
```
5、查看pcre版本

```bash
[root@bogon nginx-1.6.2]# /usr/local/server/nginx/sbin/nginx -v
```
到此，nginx安装完成。

检查配置文件ngnix.conf的正确性命令：

```bash
[root@bogon conf]# /usr/local/server/nginx/sbin/nginx -t
```
启动 Nginx
Nginx 启动命令如下：

```bash
[root@bogon conf]# /usr/local/server/nginx/sbin/nginx
```
## Nginx 其他命令
以下包含了 Nginx 常用的几个命令：

```bash
/usr/local/server/nginx/sbin/nginx -s reload            # 重新载入配置文件
/usr/local/server/nginx/sbin/nginx -s reopen            # 重启 Nginx
/usr/local/server/nginx/sbin/nginx -s stop              # 停止 Nginx
```

###附加(保留用户IP到真实服务器)

说明：这是后期附加内容，需求是获取用户请求的IP地址。但是经过Nginx代理后的请求，执行getRemoteAddr()方法时，获取到的是本机IP，造成存储了本机的IP信息，而不是用户的IP。在查阅各种资料后，得出以下解决办法。

前往Nginx安装目录下/conf/路径，找到nginx.conf配置文件，在代理配置项添加以下内容。

```bash
#此处配置请求路径，这里为  ' / ',即根路径
location / {
			proxy_set_header Host $host;				#保留主机信息
			proxy_set_header X-Real-IP $remote_addr;	#保留IP信息
			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
			proxy_set_header Remote_Addr $http_true_client_ip;
			proxy_redirect off;
			proxy_pass   http://127.0.0.1:8091/;		#请求由谁处理？就在这里配置
        }
```

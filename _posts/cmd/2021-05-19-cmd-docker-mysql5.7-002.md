---
layout: post
title:  "docker安装mysql5.7"
author: GEJT
image: assets/images/avatar.jpg
category: docker常用命令
tags: [docker常用命令]
dateTime: "2020年5月19日"
excerpt: docker安装mysql5.7
permalink: /cmd-docker/002
typora-root-url: ..\..\
typora-copy-images-to: ..\..\img
---
### 拉取mysql5.7镜像

```
//拉取镜像
docker pull mysql:5.7
//查看本地镜像
docker images
```

### 创建并运行容器，指定数据目录

```
//创建运行mysql容器
docker run --name mysql-test -p 3306:3306 -v /mysql/datadir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -d mysql:5.7
//查看运行中的容器
docker ps
//查看所有容器
docker ps -a
```

#### 查看生成的数据库文件

```
//查看生成的数据库文件
cd /mysql/datadir
ll
总用量 188484
-rw-r-----. 1 polkitd input       56 5月  19 10:05 auto.cnf
-rw-------. 1 polkitd input     1680 5月  19 10:05 ca-key.pem
-rw-r--r--. 1 polkitd input     1112 5月  19 10:05 ca.pem
-rw-r--r--. 1 polkitd input     1112 5月  19 10:05 client-cert.pem
-rw-------. 1 polkitd input     1676 5月  19 10:05 client-key.pem
-rw-r-----. 1 polkitd input      668 5月  19 10:06 ib_buffer_pool
-rw-r-----. 1 polkitd input 79691776 5月  19 10:07 ibdata1
-rw-r-----. 1 polkitd input 50331648 5月  19 10:07 ib_logfile0
-rw-r-----. 1 polkitd input 50331648 5月  19 10:05 ib_logfile1
-rw-r-----. 1 polkitd input 12582912 5月  19 10:07 ibtmp1
drwxr-x---. 2 polkitd input     4096 5月  19 10:05 mysql
drwxr-x---. 2 polkitd input     8192 5月  19 10:05 performance_schema
-rw-------. 1 polkitd input     1680 5月  19 10:05 private_key.pem
-rw-r--r--. 1 polkitd input      452 5月  19 10:05 public_key.pem
-rw-r--r--. 1 polkitd input     1112 5月  19 10:05 server-cert.pem
-rw-------. 1 polkitd input     1680 5月  19 10:05 server-key.pem
drwxr-x---. 2 polkitd input     8192 5月  19 10:05 sys
```

#### 停止容器，删除容器和镜像

```
//停止运行容器
docker stop mysql-test
//启动运行容器
docker start mysql-test
//删除容器
docker rm mysql-test
//强制删除容器
docker rm -f mysql-test
//删除镜像
docker rmi mysql:5.7
```



### 创建并运行容器，指定配置文件

```
docker run --name mysql-test1 -p 3306:3306 -v /mysql/custom:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=root -d mysql:5.7
```

> mysql实例会从/etc/mysql/my.cnf和/etc/mysql/conf.d/config-file.cnf合并使用配置，也就是说你的/my/custom目录下可以包含这两种文件

### 创建并运行容器，指定初始化数据脚本

```
docker run --name mysql-test2 -p 3306:3306 -v /mysql/init:/docker-entrypoint-initdb.d -e MYSQL_ROOT_PASSWORD=root -d mysql:5.7
```

> 容器启动后mysql实例会从/docker-entrypoint-initdb.d目录下查找.sh、.sql和.sql.gz结尾的文件并执行


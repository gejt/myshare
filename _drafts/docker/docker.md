---
layout: post
title:  "docker"
author: GEJT
image: assets/images/avatar.jpg
category: docker
tags: [docker]
dateTime: "2020年5月19日"
excerpt: docker常用命令，centos7安装docker,docker安装mysql5.7
permalink: /cmd-docker/000
typora-root-url: ..\..\
typora-copy-images-to: ..\..\img

---

## centos7安装docker

### 安装yum-utils

```
sudo yum install -y yum-utils
```

### 设置docker下载respository

```
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo

```

### 安装docker-ce,并验证安装

```
sudo yum install docker-ce docker-ce-cli containerd.io
//启动docker
systemctl start docker
docker -v
//停止docker
systemctl stop docker
```

### 设置阿里云镜像加速

```
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://xxx.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker

```

> 注意：阿里云镜像加速可以注册阿里云自行获取

### 其他命令

```
//设置开机启动
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
//禁用开机启动
sudo systemctl disable docker.service
sudo systemctl disable containerd.service
```

## docker安装mysql5.7

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
//停止运行容器docker stop mysql-test//启动运行容器docker start mysql-test//删除容器docker rm mysql-test//强制删除容器docker rm -f mysql-test//删除镜像docker rmi mysql:5.7
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

> 容器启动后mysql实例会从/docker-entrypoint-initdb.d目录下查找.sh 、.sql和.sql.gz结尾的文件并执行

## docker安装最新版tomcat

### 拉取最新tomcat镜像

```
docker pull tomcat
```
### 启动tomcat并映射80端口
```
docker run -p 80:8080 --name tomcat8080 -d tomcat
```
### 浏览器访问
![image-20210528095406959](/img/image-20210528095406959.png)

**注：** 这里是访问正常了，因为tomcat下没有manager-ui

### docker-tomcat容器的内部结构

```
[root@VM-8-10-centos webapps]# docker exec -it tomcat8080 /bin/bash
root@b59da814ae38:/usr/local/tomcat# pwd
/usr/local/tomcat
root@cf86d45b9d09:/usr/local/tomcat# ls
BUILDING.txt  CONTRIBUTING.md  LICENSE	NOTICE	README.md  RELEASE-NOTES  RUNNING.txt  bin  conf  lib  logs  native-jni-lib  temp  webapps  webapps.dist  work
```

### 强制删除tomcat容器

```
[root@VM-8-10-centos webapps]# docker rm -f tomcat8080
tomcat8080
[root@VM-8-10-centos webapps]# 
[root@VM-8-10-centos webapps]# 
[root@VM-8-10-centos webapps]# docker ps
CONTAINER ID   IMAGE       COMMAND                  CREATED      STATUS      PORTS                                                  NAMES
70ec2c069e02   mysql:5.7   "docker-entrypoint.s…"   2 days ago   Up 2 days   0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql-test

```

### 启动容器并映射本地磁盘目录

#### 创建index.html

```
mkdir -p /tomcat/webapps/ROOT
cd /tomcat/webapps/ROOT
vi index.html
```

#### index.html

```
helloWorld!!!
```

#### 启动容器并映射本地磁盘目录

```
docker run -p 80:8080 -v /tomcat/webapps:/usr/local/tomcat/webapps  --name tomcat8080 -d tomcat
```

运行效果

![image-20210528100327576](/img/image-20210528100327576.png)

同理，你也可以把log和conf目录映射到本地磁盘。****


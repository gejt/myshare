---

layout: post
title:  "kubernetes"
author: GEJT
image: assets/images/avatar.jpg
category: docker
tags: [docker,k8s]
dateTime: "2021年5月16日"
excerpt: docker编排工具kubernetes
permalink: /docker/000
typora-root-url: ..\..\
typora-copy-images-to: ..\..\img

---

## docker基础

### 容器化技术简介

#### 物理机时代

![image-20210516165547409](/img/image-20210516165547409.png)

#### 虚拟化技术

![image-20210516165921301](/img/image-20210516165921301.png)

#### 容器时代

![image-20210516170012476](/img/image-20210516170012476.png)

##### 容器化解决的问题

![image-20210516170152791](/img/image-20210516170152791.png)

![image-20210516170330163](/img/image-20210516170330163.png)

##### 容器化技术应用场景

![image-20210516170438516](/img/image-20210516170438516.png)

![image-20210516170524102](/img/image-20210516170524102.png)

### 初识docker

#### docker介绍

![image-20210516170726101](/img/image-20210516170726101.png)

#### 标准化应用打包

![image-20210516170330163](/img/image-20210516170330163.png)

#### docker的发展

![image-20210516170940613](/img/image-20210516170940613.png)

### Contos7环境安转docker

### VmWare安转Cenos7

### Windows环境安转docker

### 阿里云docker镜像加速

### Docker基本概念

#### Docker是一个容器化平台

![image-20210516173516828](/img/image-20210516173516828.png)

#### Docker体系结构

![image-20210516173946066](/img/image-20210516173946066.png)

#### 容器与镜像

![image-20210516174431468](/img/image-20210516174431468.png)

#### Docker执行流程

![image-20210516174842803](/img/image-20210516174842803.png)

### Docker常用命令

- docker pull 镜像名<:tags> - 从远程仓库抽取镜像
- docker images - 查看本地镜像
- docker run 镜像名<:tags> - 创建容器，启动应用
- docker ps - 查看正在运行中的镜像
- docker rm <-f> 容器id - 删除容器
- docker rmi <-f> 镜像名<:tags> - 删除镜像

### Docker快速部署tomcat运行

```
docker pull tomcat
docker images
docker run tomcat -p 8000:8080 --name tomcat8080 -d
netstat -tu|pn
docker ps 
docker stop tomcat8080
docker rm tomcat8080
docker rmi tomcat:lastest
```

#### Docker容器与宿主机通信

![image-20210516180603231](/img/image-20210516180603231.png)

#### 了解容器内部结构

![image-20210516181330360](/img/image-20210516181330360.png)

#### 在容器中执行命令

![image-20210516214723867](/img/image-20210516214723867.png)

```
docker exec -it tomcat8080 /bin/bash
ls
cat /proc/version
java -version
exit
```

存放位置

/var/lib/docker

### 容器的声明周期

![image-20210516215216105](/img/image-20210516215216105.png)

```
docker create tomcat --name mytomcat
docker ps 
docker ps -a 
docker start mytomcat
docker pause mytomcat
docker unpause mytomcat
docmer stop mytomcat
```

### Dockerfile构建镜像

#### Dockerfile镜像描述文件

![image-20210516215950077](/img/image-20210516215950077.png)

#### Dockerfile自动部署tomcat应用

![image-20210516220032604](/img/image-20210516220032604.png)

Dockerfile无扩展名

```
FROM tomcat:lastest
MAINTAINER gejt.com
#切换工作目录，不存在自动创建
WORKDIR /var/local/tomcat/webapps
ADD docker-web ./docker-web
```

```
docker build -t gejt.com/mywebapp:1.0 .
docker run -d gejt.com/mywebapp:1.0 -p 8081:8080
```

#### 镜像分层（layer）概念

![image-20210516220950458](/img/image-20210516220950458.png)

#### mywebapp执行过程

![image-20210516221051709](/img/image-20210516221051709.png)


### Dockerfile基础命令

#### FROM 基于基准镜像

![image-20210516221603417](/img/image-20210516221603417.png)

#### LABEL&MAINTAINER  -设置说明信息

![image-20210516221709423](/img/image-20210516221709423.png)

#### WORKDIR - 设置工作目录

![image-20210516221842755](/img/image-20210516221842755.png)

#### ADD&COPY - 复制文件

![image-20210516221928323](/img/image-20210516221928323.png)

#### ENV - 设置环境常量

![image-20210516222027228](/img/image-20210516222027228.png)



### Dockerfile执行指令

#### RUN & CMD & ENTRYPOINT

![image-20210516222200768](/img/image-20210516222200768.png)



#### 不同的执行时机

![image-20210516222247062](/img/image-20210516222247062.png)

##### RUN - 构建是运行

![image-20210516222315865](/img/image-20210516222315865.png)



###### shell运行方式

![image-20210516222431645](/img/image-20210516222431645.png)

###### exec运行方式

![image-20210516222459788](/img/image-20210516222459788.png)

##### ENTRYPOINT执行命令

![image-20210516222554036](/img/image-20210516222554036.png)

##### CMD执行命令

![image-20210516222616948](/img/image-20210516222616948.png)

### 容器间利用Link进行单向通信

![image-20210517084359156](/img/image-20210517084359156.png)

```
docker run -d --name web tomcat
docker run -d --name database -it centos /bin/bash
#查看元数据 查看ip地址
docker inspect database
docker exec -it web /bin/bash
docker run -d --name web --link database tomcat
# 在tomcat中ping database 可以ping通
```

### Bridge网桥进行双向通信

![image-20210517085147705](/img/image-20210517085147705.png)

```
docker run -d --name web tomcat
docker run -d --name database -it centos /bin/bash
docker network ls
docker create -d bridge my-bridge
docker network ps
docker network connect my-birdge web
docker network connect my-birdge database
```

#### 网桥实现原理

![image-20210517085738839](/img/image-20210517085738839.png)

### Volume容器间共享数据

#### 容器间数据共享

![image-20210517085922604](/img/image-20210517085922604.png)

![image-20210517085955784](/img/image-20210517085955784.png)

#### 通过设置-v挂在宿主机目录

![image-20210517090112136](/img/image-20210517090112136.png)

#### 通过--volumes-form共享容器内挂载点

![image-20210517090211452](/img/image-20210517090211452.png)

```
docker run --name t1 -d -p 8000:8080 -v /user/webapps:/user/local/tomcat/webapps
docker run --name t2 -d -p 8001:8080 -v /user/webapps:/user/local/tomcat/webapps
docker create --name webpage -v /user/webapps:/user/local/tomcat/webapps tomcat /bin/true
docker run -p 8003:8080 --volumes-from webpage --name t3 -d tomcat
docker run -p 8004:8080 --volumes-from webpage --name t4 -d tomcat
```



### Docker Compose(容器编排工具)

![image-20210517091214153](/img/image-20210517091214153.png)

#### 容器编排工具

![image-20210517091115124](/img/image-20210517091115124.png)

![image-20210517091245499](/img/image-20210517091245499.png)

#### 安装Docker Compose

```
docker compose -version
mkdir wordpress
cd wordpress
vi docker-pompose.yml

docker-compse up -d

```



## k8s

### 容器编排与kubernetes（k8s）

![image-20210516112118811](/img/image-20210516112118811.png)

nginx、tomcat 、mysql、redis等服务的安装部署,设备数量上去以后变得很麻烦,充分利用资源，真的需要这么多资源，每一次都要人工去做吗？支持集群的容器编排工具来完成自动化的编排和部署。

### 容器编排工具

#### docker compose

单机容器编排

#### docker swarm

集群容器编排工具

#### kubernetes

google提供的集群容器编排工具

k8s:k和s中有8个英文字母

经过大量实验，大量宿主机验证的

##### kubernetes特性

![image-20210516112805198](/img/image-20210516112805198.png)

### kubernetes的基本概念

![image-20210516113028018](/img/image-20210516113028018.png)

三台宿主机集群

#### master

主节点

创建容器，自动部署，自动发布

单独部署到一台独立物理机

#### Pod

![image-20210516113353941](/img/image-20210516113353941.png)

##### pause

网络和数据卷

![image-20210516113616008](/img/image-20210516113616008.png)

#### Lable

说明性标签，相当于每一个pod的别名，主节点才能找到对应的pod来进行操作。

#### Replaction Controller(复制控制器)

创建副本

实时监控

控制pod服务的数量

### 三个基础应用

![image-20210516114104534](/img/image-20210516114104534.png)

### kubernetes集群部署

#### 国内安装k8s的四种途径

![image-20210516114259869](/img/image-20210516114259869.png)

k8s 1.14

#### 环境准备

![image-20210516114457976](/img/image-20210516114457976.png)

![image-20210516114540187](/img/image-20210516114540187.png)

![image-20210516114608554](/img/image-20210516114608554.png)

![image-20210516114701411](/img/image-20210516114701411.png)

#### 安装kubeadm快速部署工具

![image-20210516114913005](/img/image-20210516114913005.png)

#### 利用kubeadm构建集群

### 重新启动服务

#### kubeadm/kubelet\kubectl区别

![image-20210516120550943](/img/image-20210516120550943.png)

#### 启动节点命令

##### 启动节点的k8s服务

systemctrl start kubelet

##### 设置开机启动

systemctl enable kubelet

### 启用WebUIDashboard

### Dashboard部署Tomcat集群

### Deployment脚本部署Tomcat集群

#### Deployment(部署)

![image-20210516122028945](/img/image-20210516122028945.png)

![image-20210516122138232](/img/image-20210516122138232.png)

![image-20210516122151436](/img/image-20210516122151436.png)

### 基于NFS协议实现集群文件共享

![image-20210516124906746](/img/image-20210516124906746.png)

#### 集群文件共享

![image-20210516124957709](/img/image-20210516124957709.png)

#### 部署配置挂载点



### 利用Rinetd对外提供Service负载均衡支持

![image-20210516131450201](/img/image-20210516131450201.png)

### 更新集群配置与资源限定

#### k8s部署调整命令

![image-20210516132115900](/img/image-20210516132115900.png)

#### 资源限定

![image-20210516132157423](/img/image-20210516132157423.png)
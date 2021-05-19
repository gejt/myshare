---
layout: post
title:  "centos7安装docker"
author: GEJT
image: assets/images/avatar.jpg
category: docker常用命令
tags: [docker常用命令]
dateTime: "2020年5月19日"
excerpt: centos7安装docker
permalink: /cmd-docker/001
typora-root-url: ..\..\
typora-copy-images-to: ..\..\img
---

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


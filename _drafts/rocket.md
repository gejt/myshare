---
layout: post
title:  RocketMq
author: GEJT
image: assets/images/avatar.jpg
category: RocketMq
tags: [RocketMq]
dateTime: "2021年4月26日"
excerpt: 在windows环境下安装rocketMq,并验证发送和接收消息。
permalink: /rocket/00
directory: [官方网站,下载地址,解压安装,启动NameServer,启动Broker,验证发送消息,验证接收消息,关闭服务,总结]
typora-root-url: ..\..\
typora-copy-images-to: ..\..\img
---

### 官方网站

本文参照RocketMq[官方网站](https://rocketmq.apache.org/)进行实验，用户可以进入官网自行查看。windows下的安装和实验都参照了官方的[快速启动](https://rocketmq.apache.org/docs/quick-start/),如果写的不清楚的可自行翻阅快速启动，另外，linux下的安装部署也可以参考快速启动。

### 下载地址

本文使用RocketMq4.8.0版本，可点击[下载](https://www.apache.org/dyn/closer.cgi?path=rocketmq/4.8.0/rocketmq-all-4.8.0-bin-release.zip),如果下载地址失效，请浏览官方快速启动找到对应的下载链接。

### 解压安装

#### 解压

安装文件下载好是zip格式[rocketmq-all-4.8.0-bin-release.zip](https://www.apache.org/dyn/closer.cgi?path=rocketmq/4.8.0/rocketmq-all-4.8.0-bin-release.zip)，我的解压后的目录如下：
```
D:\develop\rocketmq-all-4.8.0-bin-release
```

![image-20210331234411220](/img/image-20210331234411220.png)

其中/bin目录下放了我们常用的启动和关停命令，如`mqnamesrv.cmd`,`mqbroker.cmd`等。/lib目录下放了RockketMq运行时用到的lib库文件。

#### 设置环境变量

我用的是win10笔记本，环境变量配置过程如下：

在【此电脑】点击右键，点击【属性】打开控制面板主页，并按照如下图片所示的步骤依次添加环境变量。

![image-20210401000423581](/img/image-20210401000423581.png)

![image-20210401000603524](/img/image-20210401000603524.png)

![image-20210401000801641](/img/image-20210401000801641.png)

![image-20210401000911542](/img/image-20210401000911542.png)

![image-20210401000949275](/img/image-20210401000949275.png)

```
ROCKETMQ_HOME="D:\develop\rocketmq-all-4.8.0-bin-release"
NAMESRV_ADDR="localhost:9876"
```

我的win10配置好环境变量后重启才能生效，我记得有时候只要重新打开cmd就能生效，原因不知。如果你知道原因请私信告诉我，谢谢。

### 启动NameServer

win+R 输入cmd,启动命令行，cd 到D:\develop\rocketmq-all-4.8.0-bin-release目录下，执行命令启动name server

```
.\bin\mqnamesrv.cmd
```

![image-20210401002638215](/img/image-20210401002638215.png)

### 启动Broker

win+R 输入cmd,启动命令行，cd 到D:\develop\rocketmq-all-4.8.0-bin-release目录下，执行命令启动name server

```
.\bin\mqbroker.cmd -n localhost:9876 autoCreateTopicEnable=true
```

![image-20210401002737210](/img/image-20210401002737210.png)

### 验证发送消息

win+R 输入cmd,启动命令行，cd 到D:\develop\rocketmq-all-4.8.0-bin-release目录下，使用tools工具发送消息。

```
.\bin\tools.cmd  org.apache.rocketmq.example.quickstart.Producer
```

![image-20210401003002152](/img/image-20210401003002152.png)

![image-20210401003054489](/img/image-20210401003054489.png)

### 验证接收消息

win+R 输入cmd,启动命令行，cd 到D:\develop\rocketmq-all-4.8.0-bin-release目录下，使用tools工具接收消息。

```
.\bin\tools.cmd  org.apache.rocketmq.example.quickstart.Consumer
```

![image-20210401003203320](/img/image-20210401003203320.png)

### 关闭服务

我们关闭相应的命令窗口就关掉了就关掉了对应的服务。

### 总结

Name Server相当rocket的注册中心，所以要先启动Name Server服务，Broker启动、消息的发布订阅,都会注册到Name Server,从Name Server中获取Broker的路由，发布消息到Broker以及从Broker消费消息。

![image-20210401003736521](/img/image-20210401003736521.png)


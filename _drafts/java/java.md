---
layout: post
title:  "Java"
author: GEJT
image: assets/images/avatar.jpg
category: Java基础
tags: [Java]
dateTime: "2021年4月28日"
excerpt: Java
permalink: /java/00
typora-root-url: ..\..\
typora-copy-images-to: ..\..\img

---

## 安装JDK

系统：windows10

JDK版本：1.8

### JDK 下载

到oracle官方网站下载jdk1.8 windows64版本 
[下载地址](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

### JDK 安装

安装JDK,我的安装目录结构如下
![JDK目录结构](/img/java/jdk-path.png)

### 配置环境变量

我的电脑->属性->高级系统设置-环境变量

添加JAVA_HOME环境变量，如下图

![JAVA_HOME环境变量](/img/java/jdk-env-java-home.png)

找到path环境变量增加新的值，如下图

![JAVA_HOME环境变量](/img/java/jdk-env-path.png)

### 验证JDK安装是否正确

打开cmd命令行，输入 java命令，显示如下：

![JAVA_HOME环境变量](/img/java/jdk-cmd-java.png)

输入 javac命令，显示如下：

![JAVA_HOME环境变量](/img/java/jdk-cmd-javac.png)

### 恭喜你，JDK安装成功



## IDEA开发helloWord

### 安装IDEA开发工具

百度网盘下载[IDEA](https://pan.baidu.com/s/1DlJqix524msUbgQdQb48hw)，提取码：1o3k；解压并安装IDEA。

### IDEA 基础配置

打开IDEA->Configure->Structure for New Project

Platform Setting->SDKS 设置已安装好的JDK,如下图
![Platform SDKS](/img/java/idea-platform-sdks.png)

Project Setting->Project  设置 默认的JDK和级别，如下图

![Platform SDKS](/img/java/idea-project-sdks.png)

### 新建项目，编写HelloWorld程序

Create New Project -> Maven（[Maven配置](https://www.cnblogs.com/zhangchengzi/p/9865100.html)） 如下图

![Platform SDKS](/img/java/idea-create-project-maven.png)

点击[NEXT] 输入GroupId 和ArtifactId 如下图

![Platform SDKS](/img/java/idea-create-project-maven1.png)

点击[NEXT],点击【FIHISH】,创建项目成功 如下图

![Platform SDKS](/img/java/idea-create-project-maven2.png)
![Platform SDKS](/img/java/idea-create-project-maven3.png)

### 新建class  HelloWorld.java ,编写代码并运行程序 如下图

![Platform SDKS](/img/java/idea-create-project-maven-run.png)

### 恭喜你，成功的运行了一个Java程序。

## JAVA基础语法

### 数据类型

### 基础语法

### 预算符

## Java执行流程控制

### 条件语句

if条件语句

ifelse条件语句

ifelseif多分支语句

swich多分支语句

### 循环语句

while循环语句

dowile循环语句

for循环语句

### 跳转语句

break跳转语句

continue跳转语句

## 面向对象编程

### 类也是一种对象

### 对象的创建

### 属性和方法

构造方法

方法重载

方法重写

### 初始化

类的初始化

成员初始化

构造器初始化

初始化顺序

数组初始化

### 对象的销毁

对象的作用域

### this和super

## 访问控制权限

### 集成

### 多态

### 组合

### 代理

### 向上转型

### static

### final

## 接口和抽象类

### 接口

### 抽象类

## 异常

### 认识异常

### 什么是Throwalbe

### 常见的异常

### 与Exception有关的Java关键字

throws和throw

try、finally、catch

### 什么是Error

## 内部类

### 创建内部类

## 集合

## I/O

## 泛型

## 反射

## 枚举

## 注解
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

![image-20210430094221267](/img/image-20210430094221267.png)

![image-20210430094254046](/img/image-20210430094254046.png)

### 基础语法

![image-20210430094320985](/img/image-20210430094320985.png)

### 运算符

![image-20210430094345444](/img/image-20210430094345444.png)

![image-20210430094420158](/img/image-20210430094420158.png)

![image-20210430094450101](/img/image-20210430094450101.png)

![image-20210430094539524](/img/image-20210430094539524.png)

![image-20210430094606899](/img/image-20210430094606899.png)

![image-20210430094630015](/img/image-20210430094630015.png)

## Java执行流程控制

### 条件语句

if条件语句

![image-20210506091233090](/img/image-20210506091233090.png)

ifelse条件语句

![image-20210506091257231](/img/image-20210506091257231.png)

ifelseif多分支语句

![image-20210506091335335](/img/image-20210506091335335.png)

swich多分支语句

![image-20210506091419344](/img/image-20210506091419344.png)

### 循环语句

while循环语句

![image-20210506091437520](/img/image-20210506091437520.png)

dowile循环语句

![image-20210506091456454](/img/image-20210506091456454.png)

for循环语句

![image-20210506091515127](/img/image-20210506091515127.png)

for-each语句

![image-20210506091613539](/img/image-20210506091613539.png)

### 跳转语句

![image-20210506091644222](/img/image-20210506091644222.png)

break跳转语句

![image-20210506091708705](/img/image-20210506091708705.png)

![image-20210506091729431](/img/image-20210506091729431.png)

continue跳转语句

![image-20210506091751591](/img/image-20210506091751591.png)

## 面向对象编程

![image-20210506091901370](/img/image-20210506091901370.png)

### 类也是一种对象

![image-20210506091924555](/img/image-20210506091924555.png)

![image-20210506092134686](/img/image-20210506092134686.png)

### 对象的创建

![image-20210506092326220](/img/image-20210506092326220.png)

### 属性和方法

![image-20210506092444001](/img/image-20210506092444001.png)

![image-20210506092529010](/img/image-20210506092529010.png)

构造方法

![image-20210506092632338](/img/image-20210506092632338.png)

![image-20210506092702911](/img/image-20210506092702911.png)

![image-20210506092818011](/img/image-20210506092818011.png)

![image-20210506092920771](/img/image-20210506092920771.png)

方法重载

![image-20210506092948442](/img/image-20210506092948442.png)

![image-20210506093044755](/img/image-20210506093044755.png)

方法重写

![image-20210506093159287](/img/image-20210506093159287.png)

### 初始化

类的初始化

![image-20210506093331869](/img/image-20210506093331869.png)

成员初始化

![image-20210506093434578](/img/image-20210506093434578.png)

构造器初始化

![image-20210506093523773](/img/image-20210506093523773.png)

初始化顺序

![image-20210506093604458](/img/image-20210506093604458.png)

![image-20210506093644582](/img/image-20210506093644582.png)

![image-20210506093728151](/img/image-20210506093728151.png)

数组初始化

![image-20210506093818170](/img/image-20210506093818170.png)

可变参数列表

![image-20210506093939036](/img/image-20210506093939036.png)

### 对象的销毁

![image-20210506094034689](/img/image-20210506094034689.png)

对象的作用域

![image-20210506094100006](/img/image-20210506094100006.png)

### this和super

![image-20210506094315782](/img/image-20210506094315782.png)

![image-20210506094353696](/img/image-20210506094353696.png)

![image-20210506094503337](/img/image-20210506094503337.png)

![image-20210506094546156](/img/image-20210506094546156.png)

![image-20210506094614411](/img/image-20210506094614411.png)

![image-20210506094638395](/img/image-20210506094638395.png)

## 访问控制权限

![image-20210507092640859](/img/image-20210507092640859.png)

### 继承

![image-20210507092811668](/img/image-20210507092811668.png)

![image-20210507092843975](/img/image-20210507092843975.png)

![image-20210507092920438](/img/image-20210507092920438.png)

### 多态

![image-20210507092951905](/img/image-20210507092951905.png)

![image-20210507093034452](/img/image-20210507093034452.png)

### 组合

![image-20210507093128857](/img/image-20210507093128857.png)

![image-20210507093224758](/img/image-20210507093224758.png)

### 代理

![image-20210507093306197](/img/image-20210507093306197.png)

### 向上转型

![image-20210507093410989](/img/image-20210507093410989.png)

### static

![image-20210507093537790](/img/image-20210507093537790.png)

### final

![image-20210507093620552](/img/image-20210507093620552.png)

## 接口和抽象类

### 接口

![image-20210507093751824](/img/image-20210507093751824.png)



### 抽象类

![image-20210507094005330](/img/image-20210507094005330.png)

![image-20210507094026947](/img/image-20210507094026947.png)

## 异常

![image-20210507094136355](/img/image-20210507094136355.png)

### 认识异常

![image-20210507094311997](/img/image-20210507094311997.png)

### 什么是Throwalbe

![image-20210507094434820](/img/image-20210507094434820.png)

![image-20210507094523822](/img/image-20210507094523822.png)

### 常见的异常

![image-20210507094715148](/img/image-20210507094715148.png)

![image-20210507094831687](/img/image-20210507094831687.png)

### 与Exception有关的Java关键字

![image-20210507094910953](/img/image-20210507094910953.png)

throws和throw

![image-20210507095017160](/img/image-20210507095017160.png)

try、finally、catch

![image-20210507095042409](/img/image-20210507095042409.png)

![image-20210507095112783](/img/image-20210507095112783.png)

### 什么是Error

![image-20210507095209862](/img/image-20210507095209862.png)

![image-20210507095234568](/img/image-20210507095234568.png)

![image-20210507095334846](/img/image-20210507095334846.png)

## 内部类

![image-20210508092947404](/img/image-20210508092947404.png)

![image-20210508093042819](/img/image-20210508093042819.png)

### 创建内部类

![image-20210508093237107](/img/image-20210508093237107.png)

## 集合

![image-20210508093328544](/img/image-20210508093328544.png)

![image-20210508093554149](/img/image-20210508093554149.png)

### Iterable接口

![image-20210508093839512](/img/image-20210508093839512.png)

![image-20210508094002379](/img/image-20210508094002379.png)

![image-20210508094023079](/img/image-20210508094023079.png)

### 顶层接口

![image-20210508094211016](/img/image-20210508094211016.png)

#### ArrayList

![image-20210508095553007](/img/image-20210508095553007.png)

#### Vector

![image-20210508095608607](/img/image-20210508095608607.png)

#### LinkedList类

![image-20210508095626460](/img/image-20210508095626460.png)

#### Stack

![image-20210508095645183](/img/image-20210508095645183.png)

#### HashSet

![image-20210508095711363](/img/image-20210508095711363.png)

#### TreeSet

![image-20210508095733184](/img/image-20210508095733184.png)

#### LinkedHashSet类

![image-20210508095753254](/img/image-20210508095753254.png)

![image-20210508095819068](/img/image-20210508095819068.png)

![image-20210508095842133](/img/image-20210508095842133.png)

#### PriorityQueue

![image-20210508095859188](/img/image-20210508095859188.png)

#### HashMap

![image-20210508095912112](/img/image-20210508095912112.png)

#### TreeMap类

![image-20210508095926509](/img/image-20210508095926509.png)

#### LinkedHashMap类

![image-20210508095948269](/img/image-20210508095948269.png)

#### HashTable类

![image-20210508100009035](/img/image-20210508100009035.png)

#### IdentityHashMap类

![image-20210508100024390](/img/image-20210508100024390.png)

#### WeekHashMap类

![image-20210508100040993](/img/image-20210508100040993.png)

### Collections类

![image-20210508095016544](/img/image-20210508095016544.png)

![image-20210508095051166](/img/image-20210508095051166.png)

![image-20210508095115814](/img/image-20210508095115814.png)

### 集合实现类特征图

![image-20210508095249741](/img/image-20210508095249741.png)



## 泛型

![image-20210509164615299](/img/image-20210509164615299.png)

![image-20210509164816421](/img/image-20210509164816421.png)

### 泛型的使用

泛型的使用有多种方式，下面我们就来一起讨论下。

#### 用泛型表示类

![image-20210509164952893](/img/image-20210509164952893.png)

#### 用泛型表示接口

![image-20210509165036347](/img/image-20210509165036347.png)

#### 泛型方法

![image-20210509165102540](/img/image-20210509165102540.png)

#### 泛型通配符

![image-20210509165307098](/img/image-20210509165307098.png)

##### 上界通配符

![image-20210509165350277](/img/image-20210509165350277.png)

##### 下界通配符

![image-20210509165405691](/img/image-20210509165405691.png)

## 反射

![image-20210509165556976](/img/image-20210509165556976.png)

![image-20210509165647146](/img/image-20210509165647146.png)

![image-20210509165901455](/img/image-20210509165901455.png)

![image-20210509165929774](/img/image-20210509165929774.png)

![image-20210509170023279](/img/image-20210509170023279.png)

![image-20210509170207856](/img/image-20210509170207856.png)

![image-20210509170238239](/img/image-20210509170238239.png)

![image-20210509170512653](/img/image-20210509170512653.png)

### Class类

![image-20210509170719754](/img/image-20210509170719754.png)

![image-20210509171847403](/img/image-20210509171847403.png)

![image-20210509171926466](/img/image-20210509171926466.png)

![image-20210509171957478](/img/image-20210509171957478.png)

![image-20210509172035178](/img/image-20210509172035178.png)

![image-20210509172106130](/img/image-20210509172106130.png)

![image-20210509172134979](/img/image-20210509172134979.png)

### Field类

![image-20210509172221449](/img/image-20210509172221449.png)

![image-20210509172238622](/img/image-20210509172238622.png)

![image-20210509172255648](/img/image-20210509172255648.png)

### Method类

![image-20210509172348215](/img/image-20210509172348215.png)

### ClassLoader类

![image-20210509172448836](/img/image-20210509172448836.png)

## 枚举

![image-20210509175310782](/img/image-20210509175310782.png)

### 枚举特性

![image-20210509175439239](/img/image-20210509175439239.png)

![image-20210509175514766](/img/image-20210509175514766.png)

![image-20210509175536867](/img/image-20210509175536867.png)

![image-20210509175600727](/img/image-20210509175600727.png)

### 枚举和普通类一样

![image-20210509175712515](/img/image-20210509175712515.png)

![image-20210509175742448](/img/image-20210509175742448.png)

![image-20210509175843683](/img/image-20210509175843683.png)

### 枚举的神秘之处

![image-20210509175933329](/img/image-20210509175933329.png)

![image-20210509180013976](/img/image-20210509180013976.png)

### 枚举类

![image-20210509180057269](/img/image-20210509180057269.png)

![image-20210509180201780](/img/image-20210509180201780.png)

## I/O

![image-20210509180313205](/img/image-20210509180313205.png)

![image-20210509180346871](/img/image-20210509180346871.png)

### File类

![image-20210509180521680](/img/image-20210509180521680.png)

![image-20210509180553249](/img/image-20210509180553249.png)

![image-20210509180619888](/img/image-20210509180619888.png)

![image-20210509180702063](/img/image-20210509180702063.png)

![image-20210509180723638](/img/image-20210509180723638.png)

### 基础IO类和相关方法

![image-20210509180857800](/img/image-20210509180857800.png)

#### InputStream

![image-20210509180946015](/img/image-20210509180946015.png)

#### OutputStream

![image-20210509181028419](/img/image-20210509181028419.png)

#### Reader类

![image-20210509181132142](/img/image-20210509181132142.png)

![image-20210509181148729](/img/image-20210509181148729.png)

#### Writer类

![image-20210509181215459](/img/image-20210509181215459.png)

### InputStream及其子类

![image-20210509181354251](/img/image-20210509181354251.png)

### OutputStream及其子类

![image-20210509181438817](/img/image-20210509181438817.png)

### Reader及其子类

![image-20210509181517045](/img/image-20210509181517045.png)

### Writer及其子类

![image-20210509181556950](/img/image-20210509181556950.png)

## 注解

![image-20210509211319586](/img/image-20210509211319586.png)

![image-20210509211517056](/img/image-20210509211517056.png)

> 注意：注解是不支持继承的。

## 关于null的几种处理方式

![image-20210509211801581](/img/image-20210509211801581.png)

### 大小写 敏感

![image-20210509211845582](/img/image-20210509211845582.png)

![image-20210509211903955](/img/image-20210509211903955.png)

### null是任何引用类型的初始值

![image-20210509212018769](/img/image-20210509212018769.png)

### null是一种特殊的值

![image-20210509212105440](/img/image-20210509212105440.png)

![image-20210509212242282](/img/image-20210509212242282.png)

### 使用null-safe方法

![image-20210509212351944](/img/image-20210509212351944.png)

### null判断

![image-20210509212527820](/img/image-20210509212527820.png)

![image-20210509212544741](/img/image-20210509212544741.png)
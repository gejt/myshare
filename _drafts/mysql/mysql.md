---
layout: post
title:  "mysql"
author: GEJT
image: assets/images/avatar.jpg
category: mysql基础
tags: [mysql]
dateTime: "2021年5月11日"
excerpt: mysql
permalink: /mysql/00
typora-root-url: ..\..\
typora-copy-images-to: ..\..\img

---

## MySQL简介

![mysql](/img/mysql.jpg)

### 什么是Mysql?

MySQL是一个关系型数据库管理系统，由瑞典MySQL AB 公司开发，属于 Oracle 旗下产品。MySQL 是最流行的关系型数据库管理系统之一，在 WEB 应用方面，MySQL是最好的 RDBMS (Relational Database Management System，关系数据库管理系统) 应用软件之一。
MySQL是一种关系型数据库管理系统，关系数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。
MySQL所使用的 SQL 语言是用于访问数据库的最常用标准化语言。MySQL 软件采用了双授权政策，分为社区版和商业版，由于其体积小、速度快、总体拥有成本低，尤其是开放源码这一特点，一般中小型网站的开发都选择 MySQL 作为网站数据库。

![img](/img/908fa0ec08fa513d1273a4a63d6d55fbb3fbd9e9)

### 应用环境

与其他的大型数据库例如 Oracle、DB2、SQL Server等相比，MySQL [1]  自有它的不足之处，但是这丝毫也没有减少它受欢迎的程度。对于一般的个人使用者和中小型企业来说，MySQL提供的功能已经绰绰有余，而且由于 MySQL是开放源码软件，因此可以大大降低总体拥有成本。
Linux作为操作系统，Apache 或Nginx作为 Web 服务器，MySQL 作为数据库，PHP/Perl/Python作为服务器端脚本解释器。由于这四个软件都是免费或开放源码软件（FLOSS)，因此使用这种方式不用花一分钱（除开人工成本）就可以建立起一个稳定、免费的网站系统，被业界称为“LAMP“或“LNMP”组合。

### 系统特性

1. [2]  MySQL使用 C和 C++编写，并使用了多种编译器进行测试，保证了源代码的可移植性。

2. 支持 AIX、FreeBSD、HP-UX、Linux、Mac OS、NovellNetware、OpenBSD、OS/2 Wrap、Solaris、Windows等多种操作系统。

3. 为多种编程语言提供了 API。这些编程语言包括 C、C++、Python、Java、Perl、PHP、Eiffel、Ruby,.NET和 Tcl 等。

4. 支持多线程，充分利用 CPU 资源。

5. 优化的 SQL查询算法，有效地提高查询速度。

6. 既能够作为一个单独的应用程序应用在客户端服务器网络环境中，也能够作为一个库而嵌入到其他的软件中。

7. 提供多语言支持，常见的编码如中文的 GB 2312、BIG5，日文的 Shift_JIS等都可以用作数据表名和数据列名。

8. 提供 TCP/IP、ODBC 和 JDBC等多种数据库连接途径。
9. 提供用于管理、检查、优化数据库操作的管理工具。

10. 支持大型的数据库。可以处理拥有上千万条记录的大型数据库。

11. 支持多种存储引擎。

12. MySQL 是开源的，所以你不需要支付额外的费用。

13. MySQL 使用标准的 SQL数据语言形式。

14. MySQL 对 PHP 有很好的支持，PHP是比较流行的 Web 开发语言。

15. MySQL是可以定制的，采用了 GPL协议，你可以修改源码来开发自己的 MySQL 系统。

16. 在线 DDL/更改功能，数据架构支持动态应用程序和开发人员灵活性（5.6新增）

17. 复制全局事务标识，可支持自我修复式集群（5.6新增）

18. 复制无崩溃从机，可提高可用性（5.6新增）

19. 复制多线程从机，可提高性能（5.6新增）

20. 3倍更快的性能（5.7 [3]  新增）

21. 新的优化器（5.7新增）

22. 原生JSON支持（5.7新增）

23. 多源复制（5.7新增）

24. GIS的空间扩展 [4]  （5.7新增）

### 存储引擎

#### MyISAM

MySQL 5.0 之前的默认数据库引擎，最为常用。拥有较高的插入，查询速度，但不支持事务

#### InnoDB

事务型数据库的首选引擎，支持ACID事务，支持行级锁定, MySQL 5.5 起成为默认数据库引擎

#### BDB

源 自 Berkeley DB，事务型数据库的另一种选择，支持Commit 和Rollback 等其他事务特性

#### Memory

所有数据置于内存的存储引擎，拥有极高的插入，更新和查询效率。但是会占用和数据量成正比的内存空间。并且其内容会在 MySQL 重新启动时丢失

#### Merge

将一定数量的 MyISAM 表联合而成一个整体，在超大规模数据存储时很有用

#### Archive

非常适合存储大量的独立的，作为历史记录的数据。因为它们不经常被读取。Archive 拥有高效的插入速度，但其对查询的支持相对较差

#### Federated

将不同的 MySQL 服务器联合起来，逻辑上组成一个完整的数据库。非常适合分布式应用

#### Cluster/NDB

高冗余的存储引擎，用多台数据机器联合提供服务以提高整体性能和安全性。适合数据量大，安全和性能要求高的应用

#### CSV

逻辑上由逗号分割数据的存储引擎。它会在数据库子目录里为每个数据表创建一个 .csv 文件。这是一种普通文本文件，每个数据行占用一个文本行。CSV 存储引擎不支持索引。

#### BlackHole

黑洞引擎，写入的任何数据都会消失，一般用于记录 binlog 做复制的中继

#### EXAMPLE

存储引擎是一个不做任何事情的存根引擎。它的目的是作为 MySQL 源代码中的一个例子，用来演示如何开始编写一个新存储引擎。同样，它的主要兴趣是对开发者。EXAMPLE 存储引擎不支持编索引。

> 另外，MySQL 的存储引擎接口定义良好。有兴趣的开发者可以通过阅读文档编写自己的存储引擎   。

### 应用架构

#### 单点（Single）

单点适合小规模应用

#### 主从复制（Replication）

主从复制适合中小规模应用

![img](/img/a1ec08fa513d26976c0ac02555fbb2fb4216d8e9)

#### 集群（Cluster）

集群适合大规模应用

![img](/img/f603918fa0ec08fa62d9dbdf59ee3d6d54fbdae9)

### 安装Mysql

#### Windows 上安装 MySQL

1.进入官网找到自己所需的安装包：https://dev.mysql.com/  ，路径：DOWNLOAD-->MYSQL Community Edition(GRL)-->MYSQL on Windows (Installer & Tool)

或直接点击 https://dev.mysql.com/downloads/windows/installer/ 查看最新版本。

![img](/img/1202941-20170722225513168-99169810.png)

![img](/img/1202941-20170722225525340-1635922988.png)

![img](/img/1571831313-3095-20170722225535090-1925937407.png)

2.找到所需的安装包,

![img](/img/1571831313-8105-20170722225609184-438065502.png)

3.点击download。这里选择的是安装版（mysql -install-community）

![img](/img/1571831313-8141-1-20170722225738356-88388521.png)

4.选择不登陆下载。

![img](/img/1571831313-7844-20170722225950840-2044210671.png)

5.双击运行下载好的mysql-installer-community-5.7.19.0.msi，程序运行需要一些时间，请等待一下。

![img](/img/1571831314-6138-20170722230026215-1797155710.png)

6.运行成功之后，进入欢迎的界面.选择我同意协议，不然无法进行下一步。

![img](/img/1571831314-1312-20170722230046043-978659071.png)

7. 进入类型选择页面，本人需要mysql云服务就选择了developer default（7.1是默认安装的步骤），如果只想安装mysql server的就选择custom模式（7.2步骤是选择自己需要的服务器类型，所选择的用于做一些数据分析）

- 
- developer default（开发者默认）：安装mysql开发所需的所有产品
- server only（服务器）：只安装mysql服务器产品
- client only（客户端）：只安装没有服务器的mysql客户端产品
- full（完全）：安装所有包含的mysql产品和功能
- custom（手动）：手动选择系统上应安装的产品

![img](/img/1571831314-6490-20170722230201246-220989429.png)

7.1开发者默认模式检测以下程序会安装不成功，点击下一步进入下一个安装流程—>跳到第八步。

check requirements：以下产品的请求失败，安装程序将自动尝试解决其中一些问题。标记为手动的要求无法自动解决。单击这些项目以尝试手动恢复。

![img](/img/1571831314-6339-20170722230232793-1759462371.png)

检测到不可安装的程序说明：

Visual Studio：是一款代码编辑工具（可编写C#、Visual Basic、C++、TypeScript、F# ），如果你安装的话就安装要求去安装Visual Studio version：2012.2013.2015.2017其中一个版本

Connector/pyton 3.4：电脑有python3.6了就没选择3.4版本的。如果你没安装有python可按要求去安装一些内容。

7.2选择mysql server（服务） 5.7.19 x64

选择mysql workbench(mysql 的工作薄) 6.3.9 x64

选择mysql notiyier(通知) 1.1.7 x86(因为这里只有一个选择所以选择了86)点击下一步进入下一个安装流程—>跳到第九步。

![img](/img/1571831314-7923-20170722230314340-1501335191.png)

8.当我们点击下一步的时候安装程序出现了提示：（一个或者移动产品要求没有得到满足，那些符合要求的产品将不会安装/升级。你想要继续吗），这里我选择的是：YES

![img](/img/1571831315-4997-1-20170722230439528-92431868.png)

9.在安装所选界面能看到我们接下来所需要安装的程序，点击execute

![img](/img/1571831315-6544-20170722230506262-176699446.png)

10安装程序进度界面，安装需要一些时间。点击dide tails能看到安装日志

![img](/img/1571831315-4350-20170722230524700-2060141633.png)

11.程序安装完成之后，点击next

![img](/img/1571831315-5686-20170722230808200-494027333.png)

12.在product configutration（产品配置）页面能看到需要配置的程序，点击next（页面英语介绍：现在我们将逐一介绍以下产品的配置向导。您可以随时取消，如果您希望离开此向导，而不必配置所有产品）

![img](/img/1571831316-1727-20170722230838934-1132653366.png)

13.先配置mysql server的类型以及网络：type and networking（类型和网络），这里有两种mysql server类型，选择第一种类型点击next。

有两种类型简单介绍

- 1.standalone mysql server/classic mysql replication：独立的mysql服务器/经典的mysql复制。

  choose this option if you want to run the mysql server either standalone with the opportunity to later configure classic mysql replication：选择这个选项，如果你想运行mysql服务器是独立的，有机会以后配置经典的mysql复制

- 2.innodb cluster sandbox thst setup(for testing only)：

innodb集群沙箱thst设置（仅用于测试）

![img](/img/1571831316-4284-20170722230918575-127114164.png)

14.设置服务器配置类型以及连接端口：继续next

Config Type:选择Development Machine，用于小型以及学习所用足够了。

Port number：输入3306，也可以输入其他最好是3306-3309之间。

![img](/img/1571831316-1042-20170722231058356-1269244144.png)

15.配置root的密码（该密码要记住），系统提示这密码虚弱

![img](/img/1571831317-1713-20170722231209903-956653442.png)

16.添加其他管理员，点击add user 输入账号密码点击ok（如果添加的管理员只允许在本地登录就将host改成local），回到界面之后点击next

![img](/img/1571831317-3908-20170722231228387-1590560639.png)

17.配置mysql在windows系统中的名字，是否选择开机启动mysql服务，其它的没进行修改，点击"Next"。

![img](/img/1571831317-1586-20170722231608825-2099636815.png)

18.配置插件和扩展页面没进行修改直接下一步：

![img](/img/1571831317-4097-20170722231638887-180558399.png)

19.Mysql server :apply configuration（应用配置页面），选择execute进行安装配置

![img](/img/1571831318-8984-20170722231654278-649027984.png)

20.mysql server应用配置的log，选择finish

![img](/img/1571831318-9740-20170722231714809-1553936235.png)

21.安装程序又回到了product configutration（产品配置）页面，此时我们看到mysql server安装成功的显示，继续下一步：

![img](/img/1571831318-2164-20170722231738825-1692782858.png)

22.配置mysql router：勾选configure mysql route for innoDB cluster之后输入密码。（如果不想输入密码可直接点击点一下）点击下一步

![img](/img/1571831318-2952-20170722231755762-1299837152.png)

23.Mysql router :apply configuration（应用配置页面）点击execute,

![img](/img/1571831319-7917-20170722231811528-357673493.png)

24.安装完成之后点击选择finish

![img](/img/1571831319-7786-20170722231826746-634086390.png)

25.检测root密码

![img](/img/1571831319-2072-20170722231844528-1242732523.png)

26.安装一些server，老规矩点击execute，完成之后点击finish

![img](/img/1571831319-9386-20170722231902950-256599456.png)

27.程序回到产品配置页面。继续下一步：

28.安装程序完成界面。

![img](/img/1571831319-1406-20170722231933637-179722774.png)

29. 双击运行之前下载的安装包，能看到我们所安装的产品。

![img](/img/1571831320-7960-20170722232012418-1876643408.png)

30.配置mysql环境变量

上面安装的是时候我们看到mysql默认安装路径是：C:\Program Files\MySQL\MySQL Server 5.7

我的电脑右键—>属性à高级系统设置à环境变量à新建MYSQL_HOME,将安装目录输入：

![img](/img/1571831320-7374-41-20170722232031684-1843508.png)

找到path编辑：输入%MYSQL_HOME%\bin

![img](/img/1571831320-5015-20170722232044090-1304683536.png)

打开cmd输入mysql –u root –p

输入root的密码

![img](/img/1571831320-6727-20170722232055731-2127042770.png)

> 原文链接：https://www.cnblogs.com/xiaodingdong/p/7223245.html

#### Linux/UNIX 上安装 MySQL

Linux平台上推荐使用RPM包来安装Mysql,MySQL AB提供了以下RPM包的下载地址：

- **MySQL** - MySQL服务器。你需要该选项，除非你只想连接运行在另一台机器上的MySQL服务器。
- **MySQL-client** - MySQL 客户端程序，用于连接并操作Mysql服务器。
- **MySQL-devel** - 库和包含文件，如果你想要编译其它MySQL客户端，例如Perl模块，则需要安装该RPM包。
- **MySQL-shared** - 该软件包包含某些语言和应用程序需要动态装载的共享库(libmysqlclient.so*)，使用MySQL。
- **MySQL-bench** - MySQL数据库服务器的基准和性能测试工具。

安装前，我们可以检测系统是否自带安装 MySQL:

```
rpm -qa | grep mysql
```

如果你系统有安装，那可以选择进行卸载:

```
rpm -e mysql　　// 普通删除模式
rpm -e --nodeps mysql　　// 强力删除模式，如果使用上面命令删除时，提示有依赖的其它文件，则用该命令可以对其进行强力删除
```

**安装 MySQL：**

接下来我们在 Centos7 系统下使用 yum 命令安装 MySQL，需要注意的是 CentOS 7 版本中 MySQL数据库已从默认的程序列表中移除，所以在安装前我们需要先去官网下载 Yum 资源包，下载地址为：https://dev.mysql.com/downloads/repo/yum/

![img](/img/repo-name-small.png)

```
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
rpm -ivh mysql-community-release-el7-5.noarch.rpm
yum update
yum install mysql-server
```

权限设置：

```
chown mysql:mysql -R /var/lib/mysql
```

初始化 MySQL：

```
mysqld --initialize
```

启动 MySQL：

```
systemctl start mysqld
```

查看 MySQL 运行状态：

```
systemctl status mysqld
```

**注意：**如果我们是第一次启动 mysql 服务，mysql 服务器首先会进行初始化的配置。

> 此外,你也可以使用 MariaDB 代替，MariaDB 数据库管理系统是 MySQL 的一个分支，主要由开源社区在维护，采用 GPL 授权许可。开发这个分支的原因之一是：甲骨文公司收购了 MySQL 后，有将 MySQL 闭源的潜在风险，因此社区采用分支的方式来避开这个风险。
>
> MariaDB的目的是完全兼容MySQL，包括API和命令行，使之能轻松成为MySQL的代替品。
>
> ```
> yum install mariadb-server mariadb 
> ```
>
> mariadb数据库的相关命令是：
>
> ```
> systemctl start mariadb  #启动MariaDB
> systemctl stop mariadb  #停止MariaDB
> systemctl restart mariadb  #重启MariaDB
> systemctl enable mariadb  #设置开机启动
> ```

------

##### 验证 MySQL 安装

在成功安装 MySQL 后，一些基础表会表初始化，在服务器启动后，你可以通过简单的测试来验证 MySQL 是否工作正常。

使用 mysqladmin 工具来获取服务器状态：

使用 mysqladmin 命令来检查服务器的版本, 在 linux 上该二进制文件位于 /usr/bin 目录，在 Windows 上该二进制文件位于C:\mysql\bin 。

```
[root@host]# mysqladmin --version
```

linux上该命令将输出以下结果，该结果基于你的系统信息：

```
mysqladmin  Ver 8.23 Distrib 5.0.9-0, for redhat-linux-gnu on i386
```

如果以上命令执行后未输出任何信息，说明你的Mysql未安装成功。

------

##### 使用 MySQL Client(Mysql客户端) 执行简单的SQL命令

你可以在 MySQL Client(Mysql客户端) 使用 mysql 命令连接到 MySQL 服务器上，默认情况下 MySQL 服务器的登录密码为空，所以本实例不需要输入密码。

命令如下：

```
[root@host]# mysql
```

以上命令执行后会输出 mysql>提示符，这说明你已经成功连接到Mysql服务器上，你可以在 mysql> 提示符执行SQL命令：

```
mysql> SHOW DATABASES;
+----------+
| Database |
+----------+
| mysql    |
| test     |
+----------+
2 rows in set (0.13 sec)
```

------

##### Mysql安装后需要做的

Mysql安装成功后，默认的root用户密码为空，你可以使用以下命令来创建root用户的密码：

```
[root@host]# mysqladmin -u root password "new_password";
```

现在你可以通过以下命令来连接到Mysql服务器：

```
[root@host]# mysql -u root -p
Enter password:*******
```

**注意：**在输入密码时，密码是不会显示了，你正确输入即可。


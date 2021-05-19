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

与其他的大型数据库例如 Oracle、DB2、SQL Server等相比，MySQL 自有它的不足之处，但是这丝毫也没有减少它受欢迎的程度。对于一般的个人使用者和中小型企业来说，MySQL提供的功能已经绰绰有余，而且由于 MySQL是开放源码软件，因此可以大大降低总体拥有成本。
Linux作为操作系统，Apache 或Nginx作为 Web 服务器，MySQL 作为数据库，PHP/Perl/Python作为服务器端脚本解释器。由于这四个软件都是免费或开放源码软件（FLOSS)，因此使用这种方式不用花一分钱（除开人工成本）就可以建立起一个稳定、免费的网站系统，被业界称为“LAMP“或“LNMP”组合。

### 系统特性

1. MySQL使用 C和 C++编写，并使用了多种编译器进行测试，保证了源代码的可移植性。

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

## 安装Mysql

### Windows 上安装 MySQL

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

参考资料：

https://www.cnblogs.com/xiaodingdong/p/7223245.html

### Linux/UNIX 上安装 MySQL

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

#### 验证 MySQL 安装

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

#### 使用 MySQL Client(Mysql客户端) 执行简单的SQL命令

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

#### Mysql安装后需要做的

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

参考资料：

https://www.runoob.com/mysql/mysql-install.html

### Docker 安装 MySQL

#### 1、查看可用的 MySQL 版本

访问 MySQL 镜像库地址：https://hub.docker.com/_/mysql?tab=tags 。

可以通过 Sort by 查看其他版本的 MySQL，默认是最新版本 **mysql:latest** 。

[![img](/img/docker-mysql1.png)](https://www.runoob.com/wp-content/uploads/2016/06/docker-mysql1.png)

你也可以在下拉列表中找到其他你想要的版本：

[![img](/img/docker-mysql2.png)](https://www.runoob.com/wp-content/uploads/2016/06/docker-mysql2.png)

此外，我们还可以用 **docker search mysql** 命令来查看可用版本：

```
$ docker search mysql
NAME                     DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
mysql                    MySQL is a widely used, open-source relati...   2529      [OK]       
mysql/mysql-server       Optimized MySQL Server Docker images. Crea...   161                  [OK]
centurylink/mysql        Image containing mysql. Optimized to be li...   45                   [OK]
sameersbn/mysql                                                          36                   [OK]
google/mysql             MySQL server for Google Compute Engine          16                   [OK]
appcontainers/mysql      Centos/Debian Based Customizable MySQL Con...   8                    [OK]
marvambass/mysql         MySQL Server based on Ubuntu 14.04              6                    [OK]
drupaldocker/mysql       MySQL for Drupal                                2                    [OK]
azukiapp/mysql           Docker image to run MySQL by Azuki - http:...   2                    [OK]
...
```

#### 2、拉取 MySQL 镜像

这里我们拉取官方的最新版本的镜像：

```
$ docker pull mysql:latest
```

[![img](/img/docker-mysql3.png)](https://www.runoob.com/wp-content/uploads/2016/06/docker-mysql3.png)

#### 3、查看本地镜像

使用以下命令来查看是否已安装了 mysql：

```
$ docker images
```

[![img](/img/docker-mysql6.png)](https://www.runoob.com/wp-content/uploads/2016/06/docker-mysql6.png)

在上图中可以看到我们已经安装了最新版本（latest）的 mysql 镜像。

#### 4、运行容器

安装完成后，我们可以使用以下命令来运行 mysql 容器：

```
$ docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql
```

参数说明：

- **-p 3306:3306** ：映射容器服务的 3306 端口到宿主机的 3306 端口，外部主机可以直接通过 **宿主机ip:3306** 访问到 MySQL 的服务。
- **MYSQL_ROOT_PASSWORD=123456**：设置 MySQL 服务 root 用户的密码。

[![img](/img/docker-mysql4.png)](https://www.runoob.com/wp-content/uploads/2016/06/docker-mysql4.png)

#### 5、安装成功

通过 **docker ps** 命令查看是否安装成功：

[![img](/img/docker-mysql5.png)](https://www.runoob.com/wp-content/uploads/2016/06/docker-mysql5.png)

本机可以通过 root 和密码 123456 访问 MySQL 服务。

[![img](/img/docker-mysql7.png)](https://www.runoob.com/wp-content/uploads/2016/06/docker-mysql7.png)

参考资料：

https://www.runoob.com/docker/docker-install-mysql.html

### Mysql设置远程访问权限

#### 方法一

添加远程用户admin密码为password 

GRANT ALL PRIVILEGES ON *.* TO admin@localhost IDENTIFIED BY \'password\' WITH GRANT OPTION GRANT ALL PRIVILEGES ON *.* TO admin@\"%\" IDENTIFIED BY \'password\' WITH GRANT OPTION
mysql教程添加远程用户或允许远程访问三种方法

用root用户登陆，然后：

grant all privileges on *.* to 创建的用户名 @"%" identified by "密码";

flush privileges;   * 刷新刚才的内容*

格式：grant 权限 on 数据库教程名.表名 to 用户@登录主机 identified by "用户密码";

            @ 后面是访问mysql的客户端ip地址（或是 主机名） % 代表任意的客户端，如果填写 localhost 为

本地访问（那此用户就不能远程访问该mysql数据库了）。

同时也可以为现有的用户设置是否具有远程访问权限。如下：

use mysql;

update db set host = '%' where user = '用户名'; （如果写成 host=localhost 那此用户就不具有远程访问权限）

flush privileges;

grant all privileges on *.* to 'myuser'@'%' identified by 'mypassword' with grant option;

#### 方法二

1．  使用grant语句添加：首先在数据库本机上用root用户

登录mysql（我是用远程控制linux服务器，相当于在服务器本机登录mysql了），然后输入：

mysql>grant all privileges on *.* to admin@localhost identified by 'something' with grant option;

添加一个用户admin并授权通过本地机（localhost)访问，密码"something"。

 mysql>grant all privileges on *.* to admin@"%" identified by 'something' with grant option;

添加一个用户admin并授权可从任何其它主机发起的访问（通配符％）。使用这一条语句即可。

2．使用insert语句：

mysql>insert into user values('%','admin',password('something'), 'y','y','y','y','y','y',

'y','y','y','y','y','y','y','y')

   用户信息可在mysql数据库中的users表中查看，这里不在介绍了就。数清y的个数哦。

   好了，使用admin帐号连接试试看，我是屡试屡成功哦，呵呵！

#### 方法三

添加远程用户admin密码为password 
grant all privileges on *.* to admin@localhost identified by 'password' with grant option 
grant all privileges on *.* to admin@"%" identified by 'password' with grant option

参考资料：

https://www.cnblogs.com/ashe666/p/11305466.html

## MySQL数据库存储引擎

数据库存储引擎：是数据库底层软件组织，数据库管理系统（DBMS）使用数据引擎进行创建、查询、更新和删除数据。不同的存储引擎提供不同的存储机制、索引技巧、锁定水平等功能，使用不同的存储引擎，还可以获得特定的功能。现在许多不同的数据库管理系统都支持多种不同的数据引擎。MySQL的核心就是插件式存储引擎。

### 查看存储引擎

我们可以用SHOW ENGINES; 来查询数据库的存储引擎。

 ![img](/img/20180115165622341)

MySQL给用户提供了许多不同的存储引擎。在MySQL中，不需要在整个服务器中使用同一种存储引擎，针对具体的要求，可以对每一个表使用不同的存储引擎。Support列的值表示某种引擎是否能使用：YES表示可以使用、NO表示不能使用、DEFAULT表示该引擎为当前默认的存储引擎。

我们也可以通过使用命令来查看数据库默认使用的引擎：SHOW VARIABLES LIKE 'storage_engine';

  ![img](/img/20180115165640973)

### MySQL常见的三种数据库存储引擎

#### lInnoDB存储引擎

InnoDB是事务型数据库的首选引擎，支持事务安全表（ACID），其它存储引擎都是非事务安全表，支持行锁定和外键，MySQL5.5以后默认使用InnoDB存储引擎。

##### InnoDB主要特性

为MySQL提供了具有提交、回滚和崩溃恢复能力的事务安全（ACID兼容）存储引擎。InnoDB锁定在行级并且也在 SELECT语句中提供一个类似Oracle的非锁定读。这些功能增加了多用户部署和性能。在SQL查询中，可以自由地将InnoDB类型的表和其他MySQL的表类型混合起来，甚至在同一个查询中也可以混合。

InnoDB表的自动增长列可以手工插入，但是插入的如果是空或0，则实际插入到则是自动增长后到值。可以通过"ALTER TABLE...AUTO_INCREMENT=n;"语句强制设置自动增长值的起始值，默认为1，但是该强制到默认值是保存在内存中，数据库重启后该值将会丢失。可以使用LAST_INSERT_ID()查询当前线程最后插入记录使用的值。如果一次插入多条记录，那么返回的是第一条记录使用的自动增长值。

对于InnoDB表，自动增长列必须是索引。如果是组合索引，也必须是组合索引的第一列，但是对于MyISAM表，自动增长列可以是组合索引的其他列，这样插入记录后，自动增长列是按照组合索引到前面几列排序后递增的。

MySQL支持外键的存储引擎只有InnoDB，在创建外键的时候，父表必须有对应的索引，子表在创建外键的时候也会自动创建对应的索引。在创建索引的时候，可以指定在删除、更新父表时，对子表进行的相应操作，包括restrict、cascade、set null和no action。其中restrict和no action相同，是指限制在子表有关联的情况下，父表不能更新；casecade表示父表在更新或删除时，更新或者删除子表对应的记录；set null 则表示父表在更新或者删除的时候，子表对应的字段被set null。

当某个表被其它表创建了外键参照，那么该表对应的索引或主键被禁止删除。

可以使用set foreign_key_checks=0;临时关闭外键约束，setforeign_key_checks=1;打开约束。

InnoDB存储引擎为在主内存中缓存数据和索引而维持它自己的缓冲池。InnoDB将它的表和索引在一个逻辑表空间中，表空间可以包含数个文件（或原始磁盘文件）。这与MyISAM表不同，比如在MyISAM表中每个表被存放在分离的文件中。InnoDB表可以是任何尺寸，即使在文件尺寸被限制为2GB的操作系统上。

InnoDB支持外键完整性约束，存储表中的数据时，每张表的存储都按主键顺序存放，如果没有显示在表定义时指定主键，InnoDB会为每一行生成一个6字节的ROWID，并以此作为主键。

使用 InnoDB存储引擎 MySQL将在数据目录下创建一个名为 ibdata1的10MB大小的自动扩展数据文件，以及两个名为 ib_logfile0和 ib_logfile1的5MB大小的日志文件

#### MyISAM存储引擎

MyISAM基于ISAM存储引擎，并对其进行扩展。它是在Web、数据仓储和其他应用环境下最常使用的存储引擎之一。MyISAM拥有较高的插入、查询速度，但不支持事务，不支持外键。

##### MyISAM主要特性

###### 支持大文件系统

被大文件系统和操作系统支持。

当把删除和更新及插入操作混合使用的时候，动态尺寸的行产生更少碎片。这要通过合并相邻被删除的块，若下一个块被删除，就扩展到下一块自动完成。

每个MyISAM表最大索引数是64，这可以通过重新编译来改变。每个索引最大的列数是16。

最大的键长度是1000字节，这也可以通过编译来改变，对于键长度超过250字节的情况，一个超过1024字节的键将被用上。

###### 支持全文索引

BLOB和TEXT列可以被索引。

NULL被允许在索引的列中，这个值占每个键的0~1个字节。

所有数字键值以高字节优先被存储以允许一个更高的索引压缩。

每个MyISAM类型的表都有一个AUTOINCREMENT的内部列，当INSERT和UPDATE操作的时候该列被更新，同时AUTOINCREMENT列将被刷新。所以说，MyISAM类型表的AUTOINCREMENT列更新比InnoDB类型的AUTOINCREMENT更快。

数据文件和索引文件可以放置在不同的目录，平均分配IO，获取更快的速度。要指定数据文件和索引文件的路径，需要在创建表的时候通过DATA DIRECTORY和INDEX DIRECTORY语句指定，文件路径需要使用绝对路径。

每个MyISAM表都有一个标志，服务器或myisamchk程序在检查MyISAM数据表时会对这个标志进行设置。MyISAM表还有一个标志用来表明该数据表在上次使用后是不是被正常的关闭了。如果服务器以为当机或崩溃，这个标志可以用来判断数据表是否需要检查和修复。如果想让这种检查自动进行，可以在启动服务器时使用--myisam-recover现象。这会让服务器在每次打开一个MyISAM数据表是自动检查数据表的标志并进行必要的修复处理。MyISAM类型的表可能会损坏，可以使用CHECK TABLE语句来检查MyISAM表的健康，并用REPAIR TABLE语句修复一个损坏到MyISAM表。

每个字符列可以有不同的字符集。

有VARCHAR的表可以固定或动态记录长度。

VARCHAR和CHAR列可以多达64KB。

使用MyISAM引擎创建数据库，将产生3个文件。文件的名字以表名字开始，扩展名之处文件类型：frm文件存储表定义、数据文件的扩展名为.MYD（MYData）、索引文件的扩展名时.MYI（MYIndex）。

##### MyISAM的表支持3种不同的存储格式

静态(固定长度)表，动态表，压缩表

 静态表是默认的存储格式。静态表中的字段都是非变长字段，这样每个记录都是固定长度的，这种存储方式的优点是存储非常迅速，容易缓存，出现故障容易恢复；缺点是占用的空间通常比动态表多。静态表在数据存储时会根据列定义的宽度定义补足空格，但是在访问的时候并不会得到这些空格，这些空格在返回给应用之前已经去掉。同时需要注意：在某些情况下可能需要返回字段后的空格，而使用这种格式时后面到空格会被自动处理掉。

动态表包含变长字段，记录不是固定长度的，这样存储的优点是占用空间较少，但是频繁到更新删除记录会产生碎片，需要定期执行OPTIMIZE TABLE语句或myisamchk -r命令来改善性能，并且出现故障的时候恢复相对比较困难。

压缩表由myisamchk工具创建，占据非常小的空间，因为每条记录都是被单独压缩的，所以只有非常小的访问开支。

#### MEMORY存储引擎

MEMORY存储引擎将表中的数据存储到内存中，为查询和引用其他表数据提供快速访问。

##### MEMORY主要特性

MEMORY表的每个表可以有多达32个索引，每个索引16列，以及500字节的最大键长度。

可以在一个MEMORY表中有非唯一键值。

MEMORY支持AUTO_INCREMENT列和对可包含NULL值的列的索引。

MEMORY表在所由客户端之间共享（就像其他任何非TEMPORARY表）。

MEMORY表内存被存储在内存中，内存是MEMORY表和服务器在查询处理时的空闲中，创建的内部表共享。

默认情况下，MEMORY数据表使用散列索引，利用这种索引进行“相等比较”非常快，但是对“范围比较”的速度就慢多了。因此，散列索引值适合使用在"="和"<=>"的操作符中，不适合使用在"<"或">"操作符中，也同样不适合用在order by字句里。如果确实要使用"<"或">"或betwen操作符，可以使用btree索引来加快速度。

存储在MEMORY数据表里的数据行使用的是固定长度的格式，因此加快处理速度，这意味着不能使用BLOB和TEXT这样的长度可变的数据类型。VARCHAR是一种长度可变的类型，但因为它在MySQL内部当作长度固定不变的CHAR类型，所以也可以使用。

create table tab_memoryengine=memory select id,name,age,addr from man order by id;

使用USING HASH/BTREE来指定特定到索引。

create index mem_hash using hashon tab_memory(city_id);

在启动MySQL服务的时候使用--init-file选项，把insert into...select或load data infile 这样的语句放入到这个文件中，就可以在服务启动时从持久稳固的数据源中装载表。

每个MEMORY表中放置到数据量的大小，受到max_heap_table_size系统变量的约束，这个系统变量的初始值是16M，同时在创建MEMORY表时可以使用MAX_ROWS子句来指定表中的最大行数。

每个MEMORY表实际对应一个磁盘文件，格式是.frm。MEMORY类型的表访问非常快，因为它到数据是放在内存中的，并且默认使用HASH索引，但是一旦服务器关闭，表中的数据就会丢失，但表还会继续存在。　服务器需要足够的内存来维持所在的在同一时间使用的MEMORY表，当不再需要MEMORY表的内容时，要释放被MEMORY表使用的内存，应该执行 DELETE FROM或 TRUNCATE TABLE，或者删除整个表（使用DROP TABLE）。

### 存储引擎的选择

在实际工作中，选择一个合适的存储引擎是一个比较复杂的问题。每种存储引擎都有自己的优缺点，不能笼统地说谁比谁好。

 

| 特性           | InnoDB | MyISAM | MEMORY |
| -------------- | ------ | ------ | ------ |
| 事务安全       | 支持   | 无     | 无     |
| 存储限制       | 64TB   | 有     | 有     |
| 空间使用       | 高     | 低     | 低     |
| 内存使用       | 高     | 低     | 高     |
| 插入数据的速度 | 低     | 高     | 高     |
| 对外键的支持   | 支持   | 无     | 无     |

InnoDB： 支持事务处理，支持外键，支持崩溃修复能力和并发控制。如果需要对事务的完整性要求比较高（比如银行），要求实现并发控制（比如售票），那选择InnoDB有很大的优势。如果需要频繁的更新、删除操作的数据库，也可以选择InnoDB，因为支持事务的提交（commit）和回滚（rollback）。

MyISAM： 插入数据快，空间和内存使用比较低。如果表主要是用于插入新记录和读出记录，那么选择MyISAM能实现处理高效率。如果应用的完整性、并发性要求比较低，也可以使用。

MEMORY： 所有的数据都在内存中，数据的处理速度快，但是安全性不高。如果需要很快的读写速度，对数据的安全性要求较低，可以选择MEMOEY。它对表的大小有要求，不能建立太大的表。所以，这类数据库只使用在相对较小的数据库表。

同一个数据库也可以使用多种存储引擎的表。如果一个表要求比较高的事务处理，可以选择InnoDB。这个数据库中可以将查询要求比较高的表选择MyISAM存储。如果该数据库需要一个用于查询的临时表，可以选择MEMORY存储引擎。

若要修改默认引擎，可以修改配置文件中的default-storage-engine。可以通过：show variables like 'default_storage_engine';查看当前数据库到默认引擎。命令：show engines和show variables like 'have%'可以列出当前数据库所支持到引擎。其中Value显示为disabled的记录表示数据库支持此引擎，而在数据库启动时被禁用。在MySQL5.1以后，INFORMATION_SCHEMA数据库中存在一个ENGINES的表，它提供的信息与show engines;语句完全一样，可以使用下面语句来查询哪些存储引擎支持事物处理：select engine from information_chema.engines where transactions ='yes';

可以通过engine关键字在创建或修改数据库时指定所使用到引擎。

在创建表的时候通过engine=...或type=...来指定所要使用的引擎。show table status from DBname来查看指定表的引擎。



参考资料

https://blog.csdn.net/qq_29168493/article/details/79066399
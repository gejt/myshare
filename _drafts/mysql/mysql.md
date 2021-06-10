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

# MySQL介绍

## MySQL简介

![mysql](/img/mysql.jpg)

### 什么是MySQL?

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

被大文件系统和操作系统支持。

当把删除和更新及插入操作混合使用的时候，动态尺寸的行产生更少碎片。这要通过合并相邻被删除的块，若下一个块被删除，就扩展到下一块自动完成。

每个MyISAM表最大索引数是64，这可以通过重新编译来改变。每个索引最大的列数是16。

最大的键长度是1000字节，这也可以通过编译来改变，对于键长度超过250字节的情况，一个超过1024字节的键将被用上。

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



## 安装MySQL

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

19.MySQL server :apply configuration（应用配置页面），选择execute进行安装配置

![img](/img/1571831318-8984-20170722231654278-649027984.png)

20.mysql server应用配置的log，选择finish

![img](/img/1571831318-9740-20170722231714809-1553936235.png)

21.安装程序又回到了product configutration（产品配置）页面，此时我们看到mysql server安装成功的显示，继续下一步：

![img](/img/1571831318-2164-20170722231738825-1692782858.png)

22.配置mysql router：勾选configure mysql route for innoDB cluster之后输入密码。（如果不想输入密码可直接点击点一下）点击下一步

![img](/img/1571831318-2952-20170722231755762-1299837152.png)

23.MySQL router :apply configuration（应用配置页面）点击execute,

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

Linux平台上推荐使用RPM包来安装MySQL,MySQL AB提供了以下RPM包的下载地址：

- **MySQL** - MySQL服务器。你需要该选项，除非你只想连接运行在另一台机器上的MySQL服务器。
- **MySQL-client** - MySQL 客户端程序，用于连接并操作MySQL服务器。
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

如果以上命令执行后未输出任何信息，说明你的MySQL未安装成功。

------

#### 使用 MySQL Client(MySQL客户端) 执行简单的SQL命令

你可以在 MySQL Client(MySQL客户端) 使用 mysql 命令连接到 MySQL 服务器上，默认情况下 MySQL 服务器的登录密码为空，所以本实例不需要输入密码。

命令如下：

```
[root@host]# mysql
```

以上命令执行后会输出 mysql>提示符，这说明你已经成功连接到MySQL服务器上，你可以在 mysql> 提示符执行SQL命令：

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

#### MySQL安装后需要做的

MySQL安装成功后，默认的root用户密码为空，你可以使用以下命令来创建root用户的密码：

```
[root@host]# mysqladmin -u root password "new_password";
```

现在你可以通过以下命令来连接到MySQL服务器：

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

### MySQL设置远程访问权限

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

# MySQL数据库

## 创建数据库

在 [MySQL](http://c.biancheng.net/mysql/) 中，可以使用 **CREATE DATABASE** 语句创建数据库，语法格式如下：

```
CREATE DATABASE [IF NOT EXISTS] <数据库名>
[[DEFAULT] CHARACTER SET <字符集名>] 
[[DEFAULT] COLLATE <校对规则名>];
```

`[ ]`中的内容是可选的。语法说明如下：

- <数据库名>：创建数据库的名称。MySQL 的数据存储区将以目录方式表示 MySQL 数据库，因此数据库名称必须符合操作系统的文件夹命名规则，不能以数字开头，尽量要有实际意义。注意在 MySQL 中不区分大小写。
- IF NOT EXISTS：在创建数据库之前进行判断，只有该数据库目前尚不存在时才能执行操作。此选项可以用来避免数据库已经存在而重复创建的错误。
- [DEFAULT] CHARACTER SET：指定数据库的字符集。指定字符集的目的是为了避免在数据库中存储的数据出现乱码的情况。如果在创建数据库时不指定字符集，那么就使用系统的默认字符集。
- [DEFAULT] COLLATE：指定字符集的默认校对规则。

> MySQL 的字符集（CHARACTER）和校对规则（COLLATION）是两个不同的概念。字符集是用来定义 MySQL 存储字符串的方式，校对规则定义了比较字符串的方式。后面我们会单独讲解 MySQL 的字符集和校对规则。

### 最简单的创建 MySQL 数据库的语句

在 MySQL 中创建一个名为 test_db 的数据库。在 MySQL 命令行客户端输入 SQL 语句`CREATE DATABASE test_db;`即可创建一个数据库，输入的 SQL 语句与执行结果如下。

```
mysql> CREATE DATABASE test_db;
Query OK, 1 row affected (0.12 sec);
```

“Query OK, 1 row affected (0.12 sec);”提示中，“Query OK”表示上面的命令执行成功，“1 row affected”表示操作只影响了数据库中一行的记录，“0.12 sec”则记录了操作执行的时间。

若再次输入`CREATE DATABASE test_db;`语句，则系统会给出错误提示信息，如下所示：

```
mysql> CREATE DATABASE test_db;
ERROR 1007 (HY000): Can't create database 'test_db'; database exists
```

提示不能创建“test_db”数据库，数据库已存在。MySQL 不允许在同一系统下创建两个相同名称的数据库。

可以加上`IF NOT EXISTS`从句，就可以避免类似错误，如下所示：

```
mysql> CREATE DATABASE IF NOT EXISTS test_db;
Query OK, 1 row affected (0.12 sec)
```

### 创建 MySQL 数据库时指定字符集和校对规则

使用 MySQL 命令行工具创建一个测试数据库，命名为 test_db_char，指定其默认字符集为 utf8，默认校对规则为 utf8_chinese_ci（简体中文，不区分大小写），输入的 SQL 语句与执行结果如下所示：

```
mysql> CREATE DATABASE IF NOT EXISTS test_db_char  DEFAULT CHARACTER SET utf8  DEFAULT COLLATE utf8_chinese_ci;
Query OK, 1 row affected (0.03 sec)
```

这时，可以使用`SHOW CREATE DATABASE`查看 test_db_char 数据库的定义声明，发现该数据库的指定字符集为 utf8，运行结果如下所示：

```
mysql> SHOW CREATE DATABASE test_db_char;
+--------------+-----------------------------------------------------+
| Database     | Create Database                                     |
+--------------+-----------------------------------------------------+
| test_db_char | CREATE DATABASE `test_db_char` /*!40100 DEFAULT CHARACTER SET utf8 */ |
+--------------+-----------------------------------------------------+
1 row in set (0.00 sec)
```

“1 row in set (0.00 sec)”表示集合中有 1 行信息，处理时间为 0.00秒。时间为 0.00 秒并不代表没有花费时间，而是时间非常短，小于 0.01 秒。

### MySQL查看或显示数据库

数据库可以看作是一个专门存储数据对象的容器，每一个数据库都有唯一的名称，并且数据库的名称都是有实际意义的，这样就可以清晰的看出每个数据库用来存放什么数据。在 [MySQL](http://c.biancheng.net/mysql/) 数据库中存在系统数据库和自定义数据库，系统数据库是在安装 MySQL 后系统自带的数据库，自定义数据库是由用户定义创建的数据库。

在 MySQL 中，可使用 **SHOW DATABASES** 语句来查看或显示当前用户权限范围以内的数据库。查看数据库的语法格式为：

```
SHOW DATABASES [LIKE '数据库名'];
```

语法说明如下：

- LIKE 从句是可选项，用于匹配指定的数据库名称。LIKE 从句可以部分匹配，也可以完全匹配。
- 数据库名由单引号`' '`包围。

#### 查看所有数据库

列出当前用户可查看的所有数据库：

```
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
6 row in set (0.22 sec)
```

可以发现，在上面的列表中有 6 个数据库，它们都是安装 MySQL 时系统自动创建的，其各自功能如下：

- information_schema：主要存储了系统中的一些数据库对象信息，比如用户表信息、列信息、权限信息、字符集信息和分区信息等。
- mysql：MySQL 的核心数据库，类似于 SQL Server 中的 master 表，主要负责存储数据库用户、用户访问权限等 MySQL 自己需要使用的控制和管理信息。常用的比如在 mysql 数据库的 user 表中修改 root 用户密码。
- performance_schema：主要用于收集数据库服务器性能参数。
- sakila：MySQL 提供的样例数据库，该数据库共有 16 张表，这些数据表都是比较常见的，在设计数据库时，可以参照这些样例数据表来快速完成所需的数据表。
- sys：MySQL 5.7 安装完成后会多一个 sys 数据库。sys 数据库主要提供了一些视图，数据都来自于 performation_schema，主要是让开发者和使用者更方便地查看性能问题。
- world：world 数据库是 MySQL 自动创建的数据库，该数据库中只包括 3 张数据表，分别保存城市，国家和国家使用的语言等内容。

#### 创建并查看数据库

先创建一个名为 test_db 的数据库：

mysql> CREATE DATABASE test_db;
Query OK, 1 row affected (0.12 sec)

再使用 SHOW DATABASES 语句显示权限范围内的所有数据库名，如下所示：

```
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| test_db            |
| world              |
+--------------------+
7 row in set (0.22 sec)
```

你看，刚才创建的数据库已经被显示出来了。

#### 使用 LIKE 从句

先创建三个数据库，名字分别为 test_db、db_test、db_test_db。

1) 使用 LIKE 从句，查看与 test_db 完全匹配的数据库：

```
mysql> SHOW DATABASES LIKE 'test_db';
+--------------------+
| Database (test_db) |
+--------------------+
| test_db            |
+--------------------+
1 row in set (0.03 sec)
```

2) 使用 LIKE 从句，查看名字中包含 test 的数据库：

```
mysql> SHOW DATABASES LIKE '%test%';
+--------------------+
| Database (%test%)  |
+--------------------+
| db_test            |
+--------------------+
| db_test_db         |
+--------------------+
| test_db            |
+--------------------+
3 row in set (0.03 sec)
```

3) 使用 LIKE 从句，查看名字以 db 开头的数据库：

```
mysql> SHOW DATABASES LIKE 'db%';
+----------------+
| Database (db%) |
+----------------+
| db_test        |
+----------------+
| db_test_db     |
+----------------+
2 row in set (0.03 sec)
```

4) 使用 LIKE 从句，查看名字以 db 结尾的数据库：

```
mysql> SHOW DATABASES LIKE '%db';
+----------------+
| Database (%db) |
+----------------+
| db_test_db     |
+----------------+
| test_db        |
+----------------+
2 row in set (0.03 sec)
```

参考资料：

http://c.biancheng.net/view/2413.html

http://c.biancheng.net/view/2419.html

## MySQL数据库字符集

MySQL支持多种字符集(character set)提供用户存储数据，同时允许用不同排序规则(collation)做比较。下面基于MySQL5.7介绍一下字符集相关变量的使用。

### 字符集、字符序的概念与联系

在数据的存储上，MySQL提供了不同的字符集支持。而在数据的对比操作上，则提供了不同的字符序支持。MySQL提供了不同级别的设置，包括server级、database级、table级、column级，可以提供非常精准的设置。

什么是字符集、字符序?简单的来说：

字符集(character set)：定义了字符以及字符的编码。

字符序(collation)：定义了字符的比较规则。

举个例子：

有四个字符：A、B、a、b，这四个字符的编码分别是A = 0, B = 1, a = 2, b = 3。这里的字符 + 编码就构成了字符集(character set)。

### MySQL支持的字符集、字符序

MySQL支持多种字符集 与 字符序。

一个字符集对应至少一种字符序(一般是1对多)。

两个不同的字符集不能有相同的字符序。

每个字符集都有默认的字符序。

#### 查看支持的字符集

可以通过以下方式查看MYSQL支持的字符集。

SHOW CHARACTER SET;

select * from information_schema.HARACTER_SETS;

![fb67ecfb60df63ab69fc2911fbcdf08f.png](/img/fb67ecfb60df63ab69fc2911fbcdf08f.png)

#### 查看支持的字符序

可以通过如下方式查看MYSQL支持的字符序。

SHOW COLLATION WHERECharset='utf8';

SELECT * FROM information_schema.COLLATIONS WHERE CHARACTER_SET_NAME="utf8";

![4d83522b27d1a11bb429e8cab50499bd.png](/img/4d83522b27d1a11bb429e8cab50499bd.png)

### 系统的字符集(character_set_system)

character_set_system为元数据的字符集，即所有的元数据都使用同一个字符集。试想如果元数据采用不同字符集，INFORMATION_SCHEMA中的相关信息在不同行之间就很难展示。同时该字符集要能够支持多种语言，方便不同语言人群使用自己的语言命名database、table、column。MySQL选择UTF-8作为元数据编码，用源码固定。

查看system字符集：

```
select @@global.character_set_system;
```

![638f0e8f46ac44fbff88037d0baefa50.png](/img/638f0e8f46ac44fbff88037d0baefa50.png)

因为很少设定，所以就不做指定介绍了。

### server的字符集、字符序(character_set_server/collation_server)

当create database没有指定charset/collation就会用character_set_server/collation_server，这两个变量可以动态设置，有session/global级别。

在源码中character_set_server/collation_server实际对应一个变量，因为一个collation对应着一个charset，所以源码中只记录CHARSET_INFO结构的collation_server即可。当修改character_set_server，会选择对应charset的默认collation。对于其他同时有charset和collation的变量，源码记录也都是记录collation。

character_set_server、collation_server分别对应server字符集、server字符序。

#### 查看server字符集、字符序

分别对应character_set_server、collation_server两个系统变量。

```
SET GLOBALSHOW_COMPATIBILITY_56=ON;

SHOW VARIABLES LIKE "character_set_server";

SHOW VARIABLES LIKE "collation_server";
```

![87e25a8e5b2bf572682bed540fe64d30.png](/img/87e25a8e5b2bf572682bed540fe64d30.png)

#### 启动服务时指定

可以在MySQL服务启动时，指定server字符集、字符序。如不指定，默认的字符序分别为latin1、latin1_swedish_ci

mysqld--character-set-server=latin1--collation-server=latin1_swedish_ci

#### 配置文件指定

除了在命令行参数里指定，也可以在配置文件里指定，如下所示。

```
[client]

default-character-set=utf8

[mysql]

default-character-set=utf8

[mysqld]

collation-server=utf8_unicode_ci

init-connect='SET NAMES utf8'

character-set-server=utf8
```

#### 运行时修改

例子：运行时修改(重启后会失效，如果想要重启后保持不变，需要写进配置文件里)

```
mysql>SETcharacter_set_server=utf8;
```

#### 编译时指定默认字符集、字符序

character_set_server、collation_server的默认值，可以在MySQL编译时，通过编译选项指定：

```
cmake .-DDEFAULT_CHARSET=latin1-DDEFAULT_COLLATION=latin1_german1_ci
```

#### 实例:通过设置session中不同的character_set_server使创建database的默认charset和collation不同。

```
set character_set_server='utf8';

create database d1;

select * from information_schema.schemata where SCHEMA_NAME='d1';

set character_set_server='latin1';

create database d2;

select * from SCHEMATA where SCHEMA_NAME='d2';
```

![7f5ee8ba60b754c89aead24c48604044.png](/img/7f5ee8ba60b754c89aead24c48604044.png)

### database的字符集、字符序(character_set_database/collation_database)

指定数据库级别的字符集、字符序。同一个MySQL服务下的数据库，可以分别指定不同的字符集/字符序。该变量值session级别表示当前database的charset/collation，在后面的源码版本中该变量可能修正为只读，不建议修改该值。其global级别变量后面也会移除。

#### 设置数据的字符集/字符序

可以在创建、修改数据库的时候，通过CHARACTER SET、COLLATE指定数据库的字符集、排序规则。

创建数据库：
```
CREATE DATABASE db_name

[[DEFAULT] CHARACTER SET charset_name]

[[DEFAULT] COLLATE collation_name]
```

修改数据库：

```

ALTER DATABASE db_name

[[DEFAULT] CHARACTER SET charset_name]

[[DEFAULT] COLLATE collation_name]
```

例子：创建数据库test_schema，字符集设置为utf8，此时默认的排序规则为utf8_general_ci。
```
CREATE DATABASE `test_schema` DEFAULT CHARACTER SET utf8;
```
#### 查看数据库的字符集/字符序

有3种方式可以查看数据库的字符集/字符序。

查看test_schema的字符集、排序规则。(需要切换默认数据库)：
```
mysql>use test_schema;

mysql>SELECT @@character_set_database, @@collation_database;
```

查看test_schema的字符集、数据库(不需要切换默认数据库)：
```

mysql>SELECT SCHEMA_NAME, DEFAULT_CHARACTER_SET_NAME, DEFAULT_COLLATION_NAME

FROM information_schema.SCHEMATA WHERE schema_name="test_schema";
```

查看创建数据库的语句，来查看字符集：
```

mysql>SHOW CREATE DATABASE test_schema;
```

### table的字符集、字符序

创建表、修改表的语法如下，可通过CHARACTER SET、COLLATE设置字符集、字符序。
```

CREATE TABLE tbl_name (column_list)

[[DEFAULT] CHARACTER SET charset_name]

[COLLATE collation_name]]
```
```

ALTER TABLE tbl_name

[[DEFAULT] CHARACTER SET charset_name]

[COLLATE collation_name]
```

#### 创建table并指定字符集/字符序

指定字符集为utf8，字符序则采用默认的。

```

CREATE TABLE `test_schema`.`test_table` (

`id` INT NOT NULL COMMENT '',

PRIMARY KEY (`id`) COMMENT '')

DEFAULT CHARACTER SET=utf8;
```

#### 查看table的字符集/字符序

同样，有3种方式可以查看table的字符集/字符序。

方式一：通过SHOW TABLE STATUS查看table状态，注意Collation为utf8_general_ci，对应的字符集为utf8。
```
SHOW TABLE STATUS FROM test_schema \G;
```


方式二：查看information_schema.TABLES的信息。
```

USE test_schema;

SELECT TABLE_COLLATION FROM information_schema.TABLES WHERE
```

方式三：通过SHOW CREATE TABLE确认。
```

SHOW CREATE TABLE test_table;
```

#### table字符集、字符序如何确定

假设CHARACTER SET、COLLATE的值分别是charset_name、collation_name。如果创建table时：

明确了charset_name、collation_name，则采用charset_name、collation_name。

只明确了charset_name，但collation_name未明确，则字符集采用charset_name，字符序采用charset_name对应的默认字符序。

只明确了collation_name，但charset_name未明确，则字符序采用collation_name，字符集采用collation_name关联的字符集。

charset_name、collation_name均未明确，则采用数据库的字符集、字符序设置。

### column的字符集、排序

类型为CHAR、VARCHAR、TEXT的列，可以指定字符集/字符序，语法如下：

```
col_name {CHAR | VARCHAR | TEXT} (col_length)

[CHARACTER SET charset_name]

[COLLATE collation_name]
```



#### 新增column并指定字符集/排序规则

例子如下：(创建table类似)

```
mysql>ALTER TABLE test_table ADD COLUMN char_column VARCHAR(25) CHARACTER SET utf8;
```



#### 查看column的字符集/字符序

```
mysql>SELECT CHARACTER_SET_NAME, COLLATION_NAME FROM information_schema.COLUMNS WHERETABLE_SCHEMA="test_schema"ANDTABLE_NAME="test_table"ANDCOLUMN_NAME="char_column";

+--------------------+-----------------+

| CHARACTER_SET_NAME | COLLATION_NAME |

+--------------------+-----------------+

| utf8 | utf8_general_ci |

+--------------------+-----------------+
1 row in set (0.00 sec)
```

#### column字符集/排序规则确定

假设CHARACTER SET、COLLATE的值分别是charset_name、collation_name：

如果charset_name、collation_name均明确，则字符集、字符序以charset_name、collation_name为准。

只明确了charset_name，collation_name未明确，则字符集为charset_name，字符序为charset_name的默认字符序。

只明确了collation_name，charset_name未明确，则字符序为collation_name，字符集为collation_name关联的字符集。

charset_name、collation_name均未明确，则以table的字符集、字符序为准。

参考资料：

https://blog.csdn.net/weixin_31002509/article/details/113121089

https://blog.csdn.net/haogexiaole/article/details/80739503

https://www.cnblogs.com/haore147/p/3618028.html

### MySQL 数据库字符集 utf8 和 utf8mb4 的区别

MySQL 的 utf8 实际上不是真正的 UTF-8。utf8 只支持每个字符最多三个字节，而真正的 UTF-8 是每个字符最多四个字节。

MySQL 一直没有修复这个 bug，他们在 2010 年发布了一个叫作 utf8mb4 的字符集，绕过了这个问题。当然，他们并没有对新的字符集广而告之（可能是因为这个 bug 让他们觉得很尴尬），以致于现在网络上仍然在建议开发者使用 utf8，但这些建议都是错误的。

简单概括如下：

（1）MySQL 的 utf8mb4 是真正的 UTF-8。

（2）MySQL 的 utf8 是一种专属的编码，它能够编码的 Unicode 字符并不多。

所有在使用 utf8 的 MySQL 和 MariaDB 用户都应该改用 utf8mb4，永远都不要再使用 utf8。

这里（https://mathiasbynens.be/notes/mysql-utf8mb4#utf8-to-utf8mb4）提供了一个指南用于将现有数据库的字符编码从 utf8 转成 utf8mb4。

参考资料：

https://www.cnblogs.com/wbxk/p/10785517.html

# MySQL数据库表结构

## MySQL中数据类型介绍

### MySQL的数据类型

主要包括以下五大类：

整数类型：BIT、BOOL、TINY INT、SMALL INT、MEDIUM INT、 INT、 BIG INT

浮点数类型：FLOAT、DOUBLE、DECIMAL

字符串类型：CHAR、VARCHAR、TINY TEXT、TEXT、MEDIUM TEXT、LONGTEXT、TINY BLOB、BLOB、MEDIUM BLOB、LONG BLOB

日期类型：Date、DateTime、TimeStamp、Time、Year

其他数据类型：BINARY、VARBINARY、ENUM、SET、Geometry、Point、MultiPoint、LineString、MultiLineString、Polygon、GeometryCollection等

 

#### 整型

| MySQL数据类型 | 含义（有符号）                       |
| ------------- | ------------------------------------ |
| tinyint(m)    | 1个字节 范围(-128~127)               |
| smallint(m)   | 2个字节 范围(-32768~32767)           |
| mediumint(m)  | 3个字节 范围(-8388608~8388607)       |
| int(m)        | 4个字节 范围(-2147483648~2147483647) |
| bigint(m)     | 8个字节 范围(+-9.22*10的18次方)      |

取值范围如果加了unsigned，则最大值翻倍，如tinyint unsigned的取值范围为(0~256)。

 int(m)里的m是表示SELECT查询结果集中的显示宽度，并不影响实际的取值范围，没有影响到显示的宽度，不知道这个m有什么用。

 

#### 浮点型(float和double)

| MySQL数据类型 | 含义                                             |
| ------------- | ------------------------------------------------ |
| float(m,d)    | 单精度浮点型  8位精度(4字节)   m总个数，d小数位  |
| double(m,d)   | 双精度浮点型  16位精度(8字节)   m总个数，d小数位 |

设一个字段定义为float(6,3)，如果插入一个数123.45678,实际数据库里存的是123.457，但总个数还以实际为准，即6位。整数部分最大是3位，如果插入数12.123456，存储的是12.1234，如果插入12.12，存储的是12.1200.

 

定点数

浮点型在数据库中存放的是近似值，而定点类型在数据库中存放的是精确值。 

decimal(m,d) 参数m<65 是总个数，d<30且 d<m 是小数位。

 

#### 字符串(char,varchar,_text)

| MySQL数据类型 | 含义                            |
| ------------- | ------------------------------- |
| char(n)       | 固定长度，最多255个字符         |
| varchar(n)    | 固定长度，最多65535个字符       |
| tinytext      | 可变长度，最多255个字符         |
| text          | 可变长度，最多65535个字符       |
| mediumtext    | 可变长度，最多2的24次方-1个字符 |
| longtext      | 可变长度，最多2的32次方-1个字符 |

##### char和varchar

1.char(n) 若存入字符数小于n，则以空格补于其后，查询之时再将空格去掉。所以char类型存储的字符串末尾不能有空格，varchar不限于此。 

2.char(n) 固定长度，char(4)不管是存入几个字符，都将占用4个字节，varchar是存入的实际字符数+1个字节（n<=255）或2个字节(n>255)，

所以varchar(4),存入3个字符将占用4个字节。 


3.char类型的字符串检索速度要比varchar类型的快。
varchar和text： 

1.varchar可指定n，text不能指定，内部存储varchar是存入的实际字符数+1个字节（n<=255）或2个字节(n>255)，text是实际字符数+2个字

节。 

##### text类型不能有默认值。 

3.varchar可直接创建索引，text创建索引要指定前多少个字符。varchar查询速度快于text,在都创建索引的情况下，text的索引似乎不起作用。

 

##### 二进制数据(_Blob)

1._BLOB和_text存储方式不同，_TEXT以文本方式存储，英文存储区分大小写，而_Blob是以二进制方式存储，不分大小写。

2._BLOB存储的数据只能整体读出。 

3._TEXT可以指定字符集，_BLO不用指定字符集。

 

#### 日期时间类型

| MySQL数据类型 | 含义                          |
| ------------- | ----------------------------- |
| date          | 日期 '2008-12-2'              |
| time          | 时间 '12:25:36'               |
| datetime      | 日期时间 '2008-12-2 22:06:44' |
| timestamp     | 自动存储记录修改时间          |

若定义一个字段为timestamp，这个字段里的时间数据会随其他字段修改的时候自动刷新，所以这个数据类型的字段可以存放这条记录最后被修改的时间。

 

### 数据类型的属性

 

| MySQL关键字        | 含义                     |
| ------------------ | ------------------------ |
| NULL               | 数据列可包含NULL值       |
| NOT NULL           | 数据列不允许包含NULL值   |
| DEFAULT            | 默认值                   |
| PRIMARY KEY        | 主键                     |
| AUTO_INCREMENT     | 自动递增，适用于整数类型 |
| UNSIGNED           | 无符号                   |
| CHARACTER SET name | 指定一个字符集           |

 

### MYSQL数据类型的长度和范围

各数据类型及字节长度一览表：

| 数据类型           | 字节长度 | 范围或用法                                                   |
| ------------------ | -------- | ------------------------------------------------------------ |
| Bit                | 1        | 无符号[0,255]，有符号[-128,127]，天缘博客备注：BIT和BOOL布尔型都占用1字节 |
| TinyInt            | 1        | 整数[0,255]                                                  |
| SmallInt           | 2        | 无符号[0,65535]，有符号[-32768,32767]                        |
| MediumInt          | 3        | 无符号[0,2^24-1]，有符号[-2^23,2^23-1]]                      |
| Int                | 4        | 无符号[0,2^32-1]，有符号[-2^31,2^31-1]                       |
| BigInt             | 8        | 无符号[0,2^64-1]，有符号[-2^63 ,2^63 -1]                     |
| Float(M,D)         | 4        | 单精度浮点数。天缘博客提醒这里的D是精度，如果D<=24则为默认的FLOAT，如果D>24则会自动被转换为DOUBLE型。 |
| Double(M,D)        | 8        | 双精度浮点。                                                 |
| Decimal(M,D)       | M+1或M+2 | 未打包的浮点数，用法类似于FLOAT和DOUBLE，天缘博客提醒您如果在ASP中使用到Decimal数据类型，直接从数据库读出来的Decimal可能需要先转换成Float或Double类型后再进行运算。 |
| Date               | 3        | 以YYYY-MM-DD的格式显示，比如：2009-07-19                     |
| Date Time          | 8        | 以YYYY-MM-DD HH:MM:SS的格式显示，比如：2009-07-19 11：22：30 |
| TimeStamp          | 4        | 以YYYY-MM-DD的格式显示，比如：2009-07-19                     |
| Time               | 3        | 以HH:MM:SS的格式显示。比如：11：22：30                       |
| Year               | 1        | 以YYYY的格式显示。比如：2009                                 |
| Char(M)            | M        | 定长字符串。                                                 |
| VarChar(M)         | M        | 变长字符串，要求M<=255                                       |
| Binary(M)          | M        | 类似Char的二进制存储，特点是插入定长不足补0                  |
| VarBinary(M)       | M        | 类似VarChar的变长二进制存储，特点是定长不补0                 |
| Tiny Text          | Max:255  | 大小写不敏感                                                 |
| Text               | Max:64K  | 大小写不敏感                                                 |
| Medium Text        | Max:16M  | 大小写不敏感                                                 |
| Long Text          | Max:4G   | 大小写不敏感                                                 |
| TinyBlob           | Max:255  | 大小写敏感                                                   |
| Blob               | Max:64K  | 大小写敏感                                                   |
| MediumBlob         | Max:16M  | 大小写敏感                                                   |
| LongBlob           | Max:4G   | 大小写敏感                                                   |
| Enum               | 1或2     | 最大可达65535个不同的枚举值                                  |
| Set                | 可达8    | 最大可达64个不同的值                                         |
| Geometry           |          |                                                              |
| Point              |          |                                                              |
| LineString         |          |                                                              |
| Polygon            |          |                                                              |
| MultiPoint         |          |                                                              |
| MultiLineString    |          |                                                              |
| MultiPolygon       |          |                                                              |
| GeometryCollection |          |                                                              |

### 使用建议

1、在指定数据类型的时候一般是采用从小原则，比如能用TINY INT的最好就不用INT，能用FLOAT类型的就不用DOUBLE类型，这样会对MYSQL在运行效率上提高很大，尤其是大数据量测试条件下。

2、不需要把数据表设计的太过复杂，功能模块上区分或许对于后期的维护更为方便，慎重出现大杂烩数据表

3、数据表和字段的起名字也是一门学问

4、设计数据表结构之前请先想象一下是你的房间，或许结果会更加合理、高效

5、数据库的最后设计结果一定是效率和可扩展性的折中，偏向任何一方都是欠妥的

 

### 选择数据类型的基本原则

前提：使用适合存储引擎。

选择原则：根据选定的存储引擎，确定如何选择合适的数据类型。

下面的选择方法按存储引擎分类：

- MyISAM 数据存储引擎和数据列：MyISAM数据表，最好使用固定长度(CHAR)的数据列代替可变长度(VARCHAR)的数据列。
- MEMORY存储引擎和数据列：MEMORY数据表目前都使用固定长度的数据行存储，因此无论使用CHAR或VARCHAR列都没有关系。两者都是作为CHAR类型处理的。
- InnoDB 存储引擎和数据列：建议使用 VARCHAR类型。


对于InnoDB数据表，内部的行存储格式没有区分固定长度和可变长度列（所有数据行都使用指向数据列值的头指针），因此在本质上，使用固定长度的CHAR列不一定比使用可变长度VARCHAR列简单。因而，主要的性能因素是数据行使用的存储总量。由于CHAR平均占用的空间多于VARCHAR，因 此使用VARCHAR来最小化需要处理的数据行的存储总量和磁盘I/O是比较好的。

下面说一下固定长度数据列与可变长度的数据列。

#### char与varchar

CHAR和VARCHAR类型类似，但它们保存和检索的方式不同。它们的最大长度和是否尾部空格被保留等方面也不同。在存储或检索过程中不进行大小写转换。

下面的表显示了将各种字符串值保存到CHAR(4)和VARCHAR(4)列后的结果，说明了CHAR和VARCHAR之间的差别：

| 值         | CHAR(4) | 存储需求 | VARCHAR(4) | 存储需求 |
| ---------- | ------- | -------- | ---------- | -------- |
| ''         | '  '    | 4个字节  | ''         | 1个字节  |
| 'ab'       | 'ab '   | 4个字节  | 'ab '      | 3个字节  |
| 'abcd'     | 'abcd'  | 4个字节  | 'abcd'     | 5个字节  |
| 'abcdefgh' | 'abcd'  | 4个字节  | 'abcd'     | 5个字节  |


请注意上表中最后一行的值只适用*不使用严格模式*时；如果MySQL运行在严格模式，超过列长度不的值*不\*保存**，并且会出现错误。

从CHAR(4)和VARCHAR(4)列检索的值并不总是相同，因为检索时从CHAR列删除了尾部的空格。通过下面的例子说明该差别：
mysql> CREATE TABLE vc (v VARCHAR(4), c CHAR(4));
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO vc VALUES ('ab ', 'ab ');
Query OK, 1 row affected (0.00 sec)

mysql> SELECT CONCAT(v, '+'), CONCAT(c, '+') FROM vc;
+----------------+----------------+
| CONCAT(v, '+') | CONCAT(c, '+') |
+----------------+----------------+
| ab +     | ab+      |
+----------------+----------------+
1 row in set (0.00 sec)

#### text和blob

在使用text和blob字段类型时要注意以下几点，以便更好的发挥数据库的性能。

①BLOB和TEXT值也会引起自己的一些问题，特别是执行了大量的删除或更新操作的时候。删除这种值会在数据表中留下很大的"空洞"，以后填入这些"空洞"的记录可能长度不同,为了提高性能,建议定期使用 OPTIMIZE TABLE 功能对这类表进行碎片整理.

②使用合成的（synthetic）索引。合成的索引列在某些时候是有用的。一种办法是根据其它的列的内容建立一个散列值，并把这个值存储在单独的数据列中。接下来你就可以通过检索散列值找到数据行了。但是，我们要注意这种技术只能用于精确匹配的查询（散列值对于类似<或>=等范围搜索操作符 是没有用处的）。我们可以使用MD5()函数生成散列值，也可以使用SHA1()或CRC32()，或者使用自己的应用程序逻辑来计算散列值。请记住数值型散列值可以很高效率地存储。同样，如果散列算法生成的字符串带有尾部空格，就不要把它们存储在CHAR或VARCHAR列中，它们会受到尾部空格去除的影响。

合成的散列索引对于那些BLOB或TEXT数据列特别有用。用散列标识符值查找的速度比搜索BLOB列本身的速度快很多。

③在不必要的时候避免检索大型的BLOB或TEXT值。例如，SELECT *查询就不是很好的想法，除非你能够确定作为约束条件的WHERE子句只会找到所需要的数据行。否则，你可能毫无目的地在网络上传输大量的值。这也是 BLOB或TEXT标识符信息存储在合成的索引列中对我们有所帮助的例子。你可以搜索索引列，决定那些需要的数据行，然后从合格的数据行中检索BLOB或 TEXT值。

④把BLOB或TEXT列分离到单独的表中。在某些环境中，如果把这些数据列移动到第二张数据表中，可以让你把原数据表中 的数据列转换为固定长度的数据行格式，那么它就是有意义的。这会减少主表中的碎片，使你得到固定长度数据行的性能优势。它还使你在主数据表上运行 SELECT *查询的时候不会通过网络传输大量的BLOB或TEXT值。

#### 浮点数与定点数

为了能够引起大家的重视，在介绍浮点数与定点数以前先让大家看一个例子：
mysql> CREATE TABLE test (c1 float(10,2),c2 decimal(10,2));
Query OK, 0 rows affected (0.29 sec)

mysql> insert into test values(131072.32,131072.32);
Query OK, 1 row affected (0.07 sec)

mysql> select * from test;
+-----------+-----------+
| c1    | c2    |
+-----------+-----------+
| 131072.31 | 131072.32 |
+-----------+-----------+
1 row in set (0.00 sec)

从上面的例子中我们看到c1列的值由131072.32变成了131072.31，这就是浮点数的不精确性造成的。

在mysql中float、double（或real）是浮点数，decimal（或numberic）是定点数。

浮点数相对于定点数的优点是在长度一定的情况下，浮点数能够表示更大的数据范围；它的缺点是会引起精度问题。在今后关于浮点数和定点数的应用中，大家要记住以下几点：

1. 浮点数存在误差问题；
2. 对货币等对精度敏感的数据，应该用定点数表示或存储；
3. 编程中，如果用到浮点数，要特别注意误差问题，并尽量避免做浮点数比较；
4. 要注意浮点数中一些特殊值的处理。

 

参考资料

https://www.cnblogs.com/-xlp/p/8617760.html

https://www.runoob.com/mysql/mysql-data-types.html



## MySQL创建表

### 建表语法

要在数据库中创建一个新表，可以使用MySQL `CREATE TABLE`语句。 `CREATE TABLE`语句是MySQL中最复杂的语句之一。

下面以简单的形式来说明`CREATE TABLE`语句的语法：

```sql
CREATE TABLE [IF NOT EXISTS] table_name(
        column_list
) engine=table_type;
```

我们来更详细地来查看其语法：

- 首先，指定要在`CREATE TABLE`子句之后创建的表的名称。表名在数据库中必须是唯一的。 `IF NOT EXISTS`是语句的可选部分，允许您检查正在创建的表是否已存在于数据库中。 如果是这种情况，MySQL将忽略整个语句，不会创建任何新的表。 强烈建议在每个`CREATE TABLE`语句中使用`IF NOT EXISTS`来防止创建已存在的新表而产生错误。
- 其次，在`column_list`部分指定表的列表。字段的列用逗号(`，`)分隔。我们将在下一节中向您展示如何更详细地列(字段)定义。
- 第三，需要为`engine`子句中的表指定存储引擎。可以使用任何存储引擎，如：*InnoDB*，*MyISAM*，*HEAP*，*EXAMPLE*，*CSV*，*ARCHIVE*，*MERGE*， *FEDERATED*或*NDBCLUSTER*。如果不明确声明存储引擎，MySQL将默认使用*InnoDB*。

> 注：InnoDB自*MySQL 5.5*之后成为默认存储引擎。 *InnoDB*表类型带来了诸如ACID事务，引用完整性和崩溃恢复等关系数据库管理系统的诸多好处。在以前的版本中，MySQL使用*MyISAM*作为默认存储引擎。

要在`CREATE TABLE`语句中为表定义列，请使用以下语法：

```sql
column_name data_type[size] [NOT NULL|NULL] [DEFAULT value] 
[AUTO_INCREMENT]
```

以上语法中最重要的组成部分是：

- `column_name`指定列的名称。每列具有特定数据类型和大小，例如：`VARCHAR(255)`。
- `NOT NULL`或`NULL`表示该列是否接受`NULL`值。
- `DEFAULT`值用于指定列的默认值。
- `AUTO_INCREMENT`指示每当将新行插入到表中时，列的值会自动增加。每个表都有一个且只有一个`AUTO_INCREMENT`列。

如果要将表的特定列设置为主键，则使用以下语法：

```sql
PRIMARY KEY (col1,col2,...)
```

### 建表语句示例

下面让我们练习一个例子，在示例数据库(testdb)中创建一个名为`tasks`的新表，如下所示：

可以使用`CREATE TABLE`语句创建这个`tasks`表，如下所示：

```sql
CREATE TABLE IF NOT EXISTS tasks (
  task_id INT(11) NOT NULL AUTO_INCREMENT,
  subject VARCHAR(45) DEFAULT NULL,
  start_date DATE DEFAULT NULL,
  end_date DATE DEFAULT NULL,
  description VARCHAR(200) DEFAULT NULL,
  PRIMARY KEY (task_id)
) ENGINE=InnoDB;
```



参考资料：

https://www.cnblogs.com/borter/p/12452689.html

https://www.runoob.com/mysql/mysql-create-tables.html



## MySQL修改数据表（ALTER TABLE语句）

为实现数据库中表规范化设计的目的，有时候需要对之前已经创建的表进行结构修改或者调整。

在 MySQL 中可以使用 **ALTER TABLE** 语句来改变原有表的结构，例如增加或删减列、创建或取消索引、更改原有列类型、重新命名列或表等。

### 基本语法

修改表指的是修改数据库中已经存在的数据表的结构。MySQL 使用 ALTER TABLE 语句修改表。常用的修改表的操作有修改表名、修改字段数据类型或字段名、增加和删除字段、修改字段的排列位置、更改表的存储引擎、删除表的外键约束等。

常用的语法格式如下：

ALTER TABLE <表名> [修改选项]

修改选项的语法格式如下：

{ ADD COLUMN <列名> <类型>
| CHANGE COLUMN <旧列名> <新列名> <新列类型>
| ALTER COLUMN <列名> { SET DEFAULT <默认值> | DROP DEFAULT }
| MODIFY COLUMN <列名> <类型>
| DROP COLUMN <列名>
| RENAME TO <新表名> }

### 添加字段

随着业务的变化，可能需要在已经存在的表中添加新的字段，一个完整的字段包括字段名、数据类型、完整性约束。添加字段的语法格式如下：

ALTER TABLE <表名> ADD <新字段名> <数据类型> [约束条件] [FIRST|AFTER 已存在的字段名]；

`新字段名`为需要添加的字段的名称；`FIRST` 为可选参数，其作用是将新添加的字段设置为表的第一个字段；`AFTER` 为可选参数，其作用是将新添加的字段添加到指定的`已存在的字段名`的后面。

【实例 1】使用 ALTER TABLE 修改表 tb_emp1 的结构，在表的第一列添加一个 int 类型的字段 col1，输入的 SQL 语句和运行结果如下所示。

```
mysql> ALTER TABLE tb_emp1
    -> ADD COLUMN col1 INT FIRST;
Query OK, 0 rows affected (0.94 sec)
Records: 0  Duplicates: 0  Warnings: 0
mysql> DESC tb_emp1;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| col1   | int(11)     | YES  |     | NULL    |       |
| id     | int(11)     | YES  |     | NULL    |       |
| name   | varchar(25) | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float       | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

> 提示：“FIRST 或 AFTER 已存在的字段名”用于指定新增字段在表中的位置，如果 SQL 语句中没有这两个参数，则默认将新添加的字段设置为数据表的最后列。

【实例 2】使用 ALTER TABLE 修改表 tb_emp1 的结构，在一列 name 后添加一个 int 类型的字段 col2，输入的 SQL 语句和运行结果如下所示。

```
mysql> ALTER TABLE tb_emp1
    -> ADD COLUMN col2 INT AFTER name;
Query OK, 0 rows affected (0.50 sec)
Records: 0  Duplicates: 0  Warnings: 0
mysql> DESC tb_emp1;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| col1   | int(11)     | YES  |     | NULL    |       |
| id     | int(11)     | YES  |     | NULL    |       |
| name   | varchar(25) | YES  |     | NULL    |       |
| col2   | int(11)     | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float        | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
6 rows in set (0.00 sec)
```

可以看到，表 tb_emp1 中增加了一个名称为 col2 的字段，其位置在指定的 name 字段后面，添加字段成功。

### 修改字段数据类型

修改字段的数据类型就是把字段的数据类型转换成另一种数据类型。在 MySQL 中修改字段数据类型的语法规则如下：

```
ALTER TABLE <表名> MODIFY <字段名> <数据类型>
```

其中，`表名`指要修改数据类型的字段所在表的名称，`字段名`指需要修改的字段，`数据类型`指修改后字段的新数据类型。

【实例 3】使用 ALTER TABLE 修改表 tb_emp1 的结构，将 name 字段的数据类型由 VARCHAR(22) 修改成 VARCHAR(30)，输入的 SQL 语句和运行结果如下所示。

```
mysql> ALTER TABLE tb_emp1
    -> MODIFY name VARCHAR(30);
Query OK, 0 rows affected (0.15 sec)
Records: 0  Duplicates: 0  Warnings: 0
mysql> DESC tb_emp1;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| col1   | int(11)     | YES  |     | NULL    |       |
| id     | int(11)     | YES  |     | NULL    |       |
| name   | varchar(30) | YES  |     | NULL    |       |
| col2   | int(11)     | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float        | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
6 rows in set (0.00 sec)
```

语句执行后，发现表 tb_emp1 中 name 字段的数据类型已经修改成 VARCHAR(30)，修改成功。

### 删除字段

删除字段是将数据表中的某个字段从表中移除，语法格式如下：

ALTER TABLE <表名> DROP <字段名>；

其中，`字段名`指需要从表中删除的字段的名称。

【实例 4】使用 ALTER TABLE 修改表 tb_emp1 的结构，删除 col2 字段，输入的 SQL 语句和运行结果如下所示。

```
mysql> ALTER TABLE tb_emp1
    -> DROP col2;
Query OK, 0 rows affected (0.53 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC tb_emp1;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| col1   | int(11)     | YES  |     | NULL    |       |
| id     | int(11)     | YES  |     | NULL    |       |
| name   | varchar(30) | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float        | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```

### 修改字段名称

MySQL 中修改表字段名的语法规则如下：

ALTER TABLE <表名> CHANGE <旧字段名> <新字段名> <新数据类型>；

其中，`旧字段名`指修改前的字段名；`新字段名`指修改后的字段名；`新数据类型`指修改后的数据类型，如果不需要修改字段的数据类型，可以将新数据类型设置成与原来一样，但数据类型不能为空。

【实例 5】使用 ALTER TABLE 修改表 tb_emp1 的结构，将 col1 字段名称改为 col3，同时将数据类型变为 CHAR(30)，输入的 SQL 语句和运行结果如下所示。

```
mysql> ALTER TABLE tb_emp1
    -> CHANGE col1 col3 CHAR(30);
Query OK, 0 rows affected (0.76 sec)
Records: 0  Duplicates: 0  Warnings: 0
mysql> DESC tb_emp1;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| col3   | char(30)    | YES  |     | NULL    |       |
| id     | int(11)     | YES  |     | NULL    |       |
| name   | varchar(30) | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float        | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
5 rows in set (0.01 sec)
```

CHANGE 也可以只修改数据类型，实现和 MODIFY 同样的效果，方法是将 SQL 语句中的“新字段名”和“旧字段名”设置为相同的名称，只改变“数据类型”。

> 提示：由于不同类型的数据在机器中的存储方式及长度并不相同，修改数据类型可能会影响数据表中已有的数据记录，因此，当数据表中已经有数据时，不要轻易修改数据类型。

### 修改表名

MySQL 通过 ALTER TABLE 语句来实现表名的修改，语法规则如下：

ALTER TABLE <旧表名> RENAME [TO] <新表名>；

其中，`TO` 为可选参数，使用与否均不影响结果。

【实例 6】使用 ALTER TABLE 将数据表 tb_emp1 改名为 tb_emp2，输入的 SQL 语句和运行结果如下所示。

```
mysql> ALTER TABLE tb_emp1
    -> RENAME TO tb_emp2;
mysql> SHOW TABLES;
+--------------------+
| Tables_in_test_db  |
+--------------------+
| tb_emp2            |
+--------------------+
1 rows in set (0.00 sec)
```

> 提示：用户可以在修改表名称时使用 DESC 命令查看修改后两个表的结构，修改表名并不修改表的结构，因此修改名称后的表和修改名称前的表的结构是相同的。

参考资料：

http://c.biancheng.net/view/2433.html

https://www.cnblogs.com/wwthuanyu/p/10069869.html

## MySQL 删除数据表

MySQL中删除数据表是非常容易操作的，但是你在进行删除表操作时要非常小心，因为执行删除命令后所有数据都会消失。

### 语法

以下为删除MySQL数据表的通用语法：

```
DROP TABLE table_name ;
```

### 实例

在mysql>命令提示窗口中删除数据表SQL语句为 **DROP TABLE** ：

以下实例删除了数据表runoob_tbl:

```
root@host# mysql -u root -p
Enter password:*******
mysql> use RUNOOB;
Database changed
mysql> DROP TABLE runoob_tbl
Query OK, 0 rows affected (0.8 sec)
mysql>
```

参考资料：

https://www.runoob.com/mysql/mysql-drop-tables.html



## MySQL主键（PRIMARY KEY）

主键（PRIMARY KEY）的完整称呼是“主键约束”，是 [MySQL](http://c.biancheng.net/mysql/) 中使用最为频繁的约束。一般情况下，为了便于 DBMS 更快的查找到表中的记录，都会在表中设置一个主键。

主键分为单字段主键和多字段联合主键，本节将分别讲解这两种主键约束的创建、修改和删除。

使用主键应注意以下几点：

- 每个表只能定义一个主键。
- 主键值必须唯一标识表中的每一行，且不能为 NULL，即表中不可能存在有相同主键值的两行数据。这是唯一性原则。
- 一个字段名只能在联合主键字段表中出现一次。
- 联合主键不能包含不必要的多余字段。当把联合主键的某一字段删除后，如果剩下的字段构成的主键仍然满足唯一性原则，那么这个联合主键是不正确的。这是最小化原则。

### 在创建表时设置主键约束

在创建数据表时设置主键约束，既可以为表中的一个字段设置主键，也可以为表中多个字段设置联合主键。但是不论使用哪种方法，在一个表中主键只能有一个。下面分别讲解设置单字段主键和多字段联合主键的方法。

#### 1）设置单字段主键

在 CREATE TABLE 语句中，通过 **PRIMARY KEY** 关键字来指定主键。

在定义字段的同时指定主键，语法格式如下：

<字段名> <数据类型> PRIMARY KEY [默认值]

例 1

在 test_db 数据库中创建 tb_emp3 数据表，其主键为 id，SQL 语句和运行结果如下。

```
mysql> CREATE TABLE tb_emp3
    -> (
    -> id INT(11) PRIMARY KEY,
    -> name VARCHAR(25),
    -> deptId INT(11),
    -> salary FLOAT
    -> );
Query OK, 0 rows affected (0.37 sec)
mysql> DESC tb_emp3;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int(11)     | NO   | PRI | NULL    |       |
| name   | varchar(25) | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float       | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.14 sec)
```


或者是在定义完所有字段之后指定主键，语法格式如下：

[CONSTRAINT <约束名>] PRIMARY KEY [字段名]

例 2

在 test_db 数据库中创建 tb_emp4 数据表，其主键为 id，SQL 语句和运行结果如下。

```
mysql> CREATE TABLE tb_emp4
    -> (
    -> id INT(11),
    -> name VARCHAR(25),
    -> deptId INT(11),
    -> salary FLOAT,
    -> PRIMARY KEY(id)
    -> );
Query OK, 0 rows affected (0.37 sec)
mysql> DESC tb_emp4;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int(11)     | NO   | PRI | NULL    |       |
| name   | varchar(25) | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float       | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.14 sec)
```

#### 2）在创建表时设置联合主键

所谓的联合主键，就是这个主键是由一张表中多个字段组成的。

比如，设置学生选课数据表时，使用学生编号做主键还是用课程编号做主键呢？如果用学生编号做主键，那么一个学生就只能选择一门课程。如果用课程编号做主键，那么一门课程只能有一个学生来选。显然，这两种情况都是不符合实际情况的。

实际上设计学生选课表，要限定的是一个学生只能选择同一课程一次。因此，学生编号和课程编号可以放在一起共同作为主键，这也就是联合主键了。

主键由多个字段联合组成，语法格式如下：

PRIMARY KEY [字段1，字段2，…,字段n]

注意：当主键是由多个字段组成时，不能直接在字段名后面声明主键约束。

例 3

创建数据表 tb_emp5，假设表中没有主键 id，为了唯一确定一个员工，可以把 name、deptId 联合起来作为主键，SQL 语句和运行结果如下。

```
mysql> CREATE TABLE tb_emp5
    -> (
    -> name VARCHAR(25),
    -> deptId INT(11),
    -> salary FLOAT,
    -> PRIMARY KEY(name,deptId)
    -> );
Query OK, 0 rows affected (0.37 sec)
mysql> DESC tb_emp5;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| name   | varchar(25) | NO   | PRI | NULL    |       |
| deptId | int(11)     | NO   | PRI | NULL    |       |
| salary | float       | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.14 sec)
```

### 在修改表时添加主键约束

主键约束不仅可以在创建表的同时创建，也可以在修改表时添加。但是需要注意的是，设置成主键约束的字段中不允许有空值。

在修改数据表时添加主键约束的语法格式如下：

ALTER TABLE <数据表名> ADD PRIMARY KEY(<字段名>);

查看 tb_emp2 数据表的表结构，SQL 语句和运行结果如下所示。

```
mysql> DESC tb_emp2;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int(11)     | NO   |     | NULL    |       |
| name   | varchar(30) | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float       | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.14 sec)
```

例 4

修改数据表 tb_emp2，将字段 id 设置为主键，SQL 语句和运行结果如下。

```
mysql> ALTER TABLE tb_emp2
    -> ADD PRIMARY KEY(id);
Query OK, 0 rows affected (0.94 sec)
Records: 0  Duplicates: 0  Warnings: 0
mysql> DESC tb_emp2;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int(11)     | NO   | PRI | NULL    |       |
| name   | varchar(30) | YES  |     | NULL    |       |
| deptId | int(11)     | YES  |     | NULL    |       |
| salary | float       | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (0.12 sec)
```

通常情况下，当在修改表时要设置表中某个字段的主键约束时，要确保设置成主键约束的字段中值不能够有重复的，并且要保证是非空的。否则，无法设置主键约束。

### 删除主键约束

当一个表中不需要主键约束时，就需要从表中将其删除。删除主键约束的方法要比创建主键约束容易的多。

删除主键约束的语法格式如下所示：

ALTER TABLE <数据表名> DROP PRIMARY KEY;

例 5

删除 tb_emp2 表中的主键约束，SQL 语句和运行结果如下。

```
mysql> ALTER TABLE tb_emp2
    -> DROP PRIMARY KEY;
Query OK, 0 rows affected (0.94 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

由于主键约束在一个表中只能有一个，因此不需要指定主键名就可以删除一个表中的主键约束。

参考资料：

http://c.biancheng.net/view/2440.html



## MySQL外键约束（FOREIGN KEY）

[MySQL](http://c.biancheng.net/mysql/) 外键约束（FOREIGN KEY）是表的一个特殊字段，经常与主键约束一起使用。对于两个具有关联关系的表而言，相关联字段中主键所在的表就是主表（父表），外键所在的表就是从表（子表）。

外键用来建立主表与从表的关联关系，为两个表的数据建立连接，约束两个表中数据的一致性和完整性。比如，一个水果摊，只有苹果、桃子、李子、西瓜等 4 种水果，那么，你来到水果摊要买水果就只能选择苹果、桃子、李子和西瓜，其它的水果都是不能购买的。

主表删除某条记录时，从表中与之对应的记录也必须有相应的改变。一个表可以有一个或多个外键，外键可以为空值，若不为空值，则每一个外键的值必须等于主表中主键的某个值。

定义外键时，需要遵守下列规则：

- 主表必须已经存在于数据库中，或者是当前正在创建的表。如果是后一种情况，则主表与从表是同一个表，这样的表称为自参照表，这种结构称为自参照完整性。
- 必须为主表定义主键。
- 主键不能包含空值，但允许在外键中出现空值。也就是说，只要外键的每个非空值出现在指定的主键中，这个外键的内容就是正确的。
- 在主表的表名后面指定列名或列名的组合。这个列或列的组合必须是主表的主键或候选键。
- 外键中列的数目必须和主表的主键中列的数目相同。
- 外键中列的数据类型必须和主表主键中对应列的数据类型相同。

### 在创建表时设置外键约束

在 CREATE TABLE 语句中，通过 **FOREIGN KEY** 关键字来指定外键，具体的语法格式如下：

[CONSTRAINT <外键名>] FOREIGN KEY 字段名 [，字段名2，…]
REFERENCES <主表名> 主键列1 [，主键列2，…]

例 1

为了展现表与表之间的外键关系，本例在 test_db 数据库中创建一个部门表 tb_dept1，表结构如下表所示。



| 字段名称 | 数据类型    | 备注     |
| -------- | ----------- | -------- |
| id       | INT(11)     | 部门编号 |
| name     | VARCHAR(22) | 部门名称 |
| location | VARCHAR(22) | 部门位置 |


创建 tb_dept1 的 SQL 语句和运行结果如下所示。

```
mysql> CREATE TABLE tb_dept1
    -> (
    -> id INT(11) PRIMARY KEY,
    -> name VARCHAR(22) NOT NULL,
    -> location VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.37 sec)
```

创建数据表 tb_emp6，并在表 tb_emp6 上创建外键约束，让它的键 deptId 作为外键关联到表 tb_dept1 的主键 id，SQL 语句和运行结果如下所示。

```
mysql> CREATE TABLE tb_emp6
    -> (
    -> id INT(11) PRIMARY KEY,
    -> name VARCHAR(25),
    -> deptId INT(11),
    -> salary FLOAT,
    -> CONSTRAINT fk_emp_dept1
    -> FOREIGN KEY(deptId) REFERENCES tb_dept1(id)
    -> );
Query OK, 0 rows affected (0.37 sec)

mysql> DESC tb_emp6;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| id     | int(11)     | NO   | PRI | NULL    |       |
| name   | varchar(25) | YES  |     | NULL    |       |
| deptId | int(11)     | YES  | MUL | NULL    |       |
| salary | float       | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
4 rows in set (1.33 sec)
```

以上语句执行成功之后，在表 tb_emp6 上添加了名称为 fk_emp_dept1 的外键约束，外键名称为 deptId，其依赖于表 tb_dept1 的主键 id。

> 注意：从表的外键关联的必须是主表的主键，且主键和外键的数据类型必须一致。例如，两者都是 INT 类型，或者都是 CHAR 类型。如果不满足这样的要求，在创建从表时，就会出现“ERROR 1005(HY000): Can't create table”错误。

### 在修改表时添加外键约束

外键约束也可以在修改表时添加，但是添加外键约束的前提是：从表中外键列中的数据必须与主表中主键列中的数据一致或者是没有数据。

在修改数据表时添加外键约束的语法格式如下：

ALTER TABLE <数据表名> ADD CONSTRAINT <外键名>
FOREIGN KEY(<列名>) REFERENCES <主表名> (<列名>);

例 2

修改数据表 tb_emp2，将字段 deptId 设置为外键，与数据表 tb_dept1 的主键 id 进行关联，SQL 语句和运行结果如下所示。

```
mysql> ALTER TABLE tb_emp2
    -> ADD CONSTRAINT fk_tb_dept1
    -> FOREIGN KEY(deptId)
    -> REFERENCES tb_dept1(id);
Query OK, 0 rows affected (1.38 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SHOW CREATE TABLE tb_emp2\G
*************************** 1. row ***************************
       Table: tb_emp2
Create Table: CREATE TABLE `tb_emp2` (
  `id` int(11) NOT NULL,
  `name` varchar(30) DEFAULT NULL,
  `deptId` int(11) DEFAULT NULL,
  `salary` float DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `fk_tb_dept1` (`deptId`),
  CONSTRAINT `fk_tb_dept1` FOREIGN KEY (`deptId`) REFERENCES `tb_dept1` (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=gb2312
1 row in set (0.12 sec)
```

注意：在为已经创建好的数据表添加外键约束时，要确保添加外键约束的列的值全部来源于主键列，并且外键列不能为空。

### 删除外键约束

当一个表中不需要外键约束时，就需要从表中将其删除。外键一旦删除，就会解除主表和从表间的关联关系。

删除外键约束的语法格式如下所示：

ALTER TABLE <表名> DROP FOREIGN KEY <外键约束名>;

例 3

删除数据表 tb_emp2 中的外键约束 fk_tb_dept1，SQL 语句和运行结果如下所示。

```
mysql> ALTER TABLE tb_emp2
    -> DROP FOREIGN KEY fk_tb_dept1;
Query OK, 0 rows affected (0.19 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SHOW CREATE TABLE tb_emp2\G
*************************** 1. row ***************************
       Table: tb_emp2
Create Table: CREATE TABLE `tb_emp2` (
  `id` int(11) NOT NULL,
  `name` varchar(30) DEFAULT NULL,
  `deptId` int(11) DEFAULT NULL,
  `salary` float DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `fk_tb_dept1` (`deptId`)
) ENGINE=InnoDB DEFAULT CHARSET=gb2312
1 row in set (0.00 sec)
```

可以看到，tb_emp2 中已经不存在 FOREIGN KEY，原有的名称为 fk_emp_dept 的外键约束删除成功。



参考资料：

http://c.biancheng.net/view/2441.html



## MySQL 索引

MySQL索引的建立对于MySQL的高效运行是很重要的，索引可以大大提高MySQL的检索速度。

打个比方，如果合理的设计且使用索引的MySQL是一辆兰博基尼的话，那么没有设计和使用索引的MySQL就是一个人力三轮车。

拿汉语字典的目录页（索引）打比方，我们可以按拼音、笔画、偏旁部首等排序的目录（索引）快速查找到需要的字。

索引分单列索引和组合索引。单列索引，即一个索引只包含单个列，一个表可以有多个单列索引，但这不是组合索引。组合索引，即一个索引包含多个列。

创建索引时，你需要确保该索引是应用在 SQL 查询语句的条件(一般作为 WHERE 子句的条件)。

实际上，索引也是一张表，该表保存了主键与索引字段，并指向实体表的记录。

上面都在说使用索引的好处，但过多的使用索引将会造成滥用。因此索引也会有它的缺点：虽然索引大大提高了查询速度，同时却会降低更新表的速度，如对表进行INSERT、UPDATE和DELETE。因为更新表时，MySQL不仅要保存数据，还要保存一下索引文件。

建立索引会占用磁盘空间的索引文件。

------

### 普通索引

#### 创建索引

这是最基本的索引，它没有任何限制。它有以下几种创建方式：

```
CREATE INDEX indexName ON table_name (column_name)
```

如果是CHAR，VARCHAR类型，length可以小于字段实际长度；如果是BLOB和TEXT类型，必须指定 length。

#### 修改表结构(添加索引)

```
ALTER table tableName ADD INDEX indexName(columnName)
```

#### 创建表的时候直接指定

```
CREATE TABLE mytable(  
 
ID INT NOT NULL,   
 
username VARCHAR(16) NOT NULL,  
 
INDEX [indexName] (username(length))  
 
);  
```

#### 删除索引的语法

```
DROP INDEX [indexName] ON mytable; 
```

------

### 唯一索引

它与前面的普通索引类似，不同的就是：索引列的值必须唯一，但允许有空值。如果是组合索引，则列值的组合必须唯一。它有以下几种创建方式：

#### 创建索引

```
CREATE UNIQUE INDEX indexName ON mytable(username(length)) 
```

#### 修改表结构

```
ALTER table mytable ADD UNIQUE [indexName] (username(length))
```

#### 创建表的时候直接指定

```
CREATE TABLE mytable(  
 
ID INT NOT NULL,   
 
username VARCHAR(16) NOT NULL,  
 
UNIQUE [indexName] (username(length))  
 
);  
```

------

### 使用ALTER 命令添加和删除索引

有四种方式来添加数据表的索引：

- ALTER TABLE tbl_name ADD PRIMARY KEY (column_list):该语句添加一个主键，这意味着索引值必须是唯一的，且不能为NULL。
- **ALTER TABLE tbl_name ADD UNIQUE index_name (column_list):** 这条语句创建索引的值必须是唯一的（除了NULL外，NULL可能会出现多次）。
- **ALTER TABLE tbl_name ADD INDEX index_name (column_list):** 添加普通索引，索引值可出现多次。
- **ALTER TABLE tbl_name ADD FULLTEXT index_name (column_list):**该语句指定了索引为 FULLTEXT ，用于全文索引。

以下实例为在表中添加索引。

```
mysql> ALTER TABLE testalter_tbl ADD INDEX (c);
```

你还可以在 ALTER 命令中使用 DROP 子句来删除索引。尝试以下实例删除索引:

```
mysql> ALTER TABLE testalter_tbl DROP INDEX c;
```

------

### 使用 ALTER 命令添加和删除主键

主键作用于列上（可以一个列或多个列联合主键），添加主键索引时，你需要确保该主键默认不为空（NOT NULL）。实例如下：

```
mysql> ALTER TABLE testalter_tbl MODIFY i INT NOT NULL;
mysql> ALTER TABLE testalter_tbl ADD PRIMARY KEY (i);
```

你也可以使用 ALTER 命令删除主键：

```
mysql> ALTER TABLE testalter_tbl DROP PRIMARY KEY;
```

删除主键时只需指定PRIMARY KEY，但在删除索引时，你必须知道索引名。

------

### 显示索引信息

你可以使用 SHOW INDEX 命令来列出表中的相关的索引信息。可以通过添加 \G 来格式化输出信息。

尝试以下实例:

```
mysql> SHOW INDEX FROM table_name; \G
........
```

参考资料：

https://www.runoob.com/mysql/mysql-index.html



## Mysq数据增删改查

### MySQL 插入数据

MySQL 表中使用 **INSERT INTO** SQL语句来插入数据。

你可以通过 mysql> 命令提示窗口中向数据表中插入数据，或者通过PHP脚本来插入数据。

#### 语法

以下为向MySQL数据表插入数据通用的 **INSERT INTO** SQL语法：

```
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
```

如果数据是字符型，必须使用单引号或者双引号，如："value"。

INSERT 插入多条数据

```
INSERT INTO table_name  (field1, field2,...fieldN)  VALUES  (valueA1,valueA2,...valueAN),(valueB1,valueB2,...valueBN),(valueC1,valueC2,...valueCN)......;
```

#### 实例

以下实例中我们将向 runoob_tbl 表插入三条数据:

```
root@host# mysql -u root -p password;
Enter password:*******
mysql> use RUNOOB;
Database changed
mysql> INSERT INTO runoob_tbl 
    -> (runoob_title, runoob_author, submission_date)
    -> VALUES
    -> ("学习 PHP", "菜鸟教程", NOW());
Query OK, 1 rows affected, 1 warnings (0.01 sec)
mysql> INSERT INTO runoob_tbl
    -> (runoob_title, runoob_author, submission_date)
    -> VALUES
    -> ("学习 MySQL", "菜鸟教程", NOW());
Query OK, 1 rows affected, 1 warnings (0.01 sec)
mysql> INSERT INTO runoob_tbl
    -> (runoob_title, runoob_author, submission_date)
    -> VALUES
    -> ("JAVA 教程", "RUNOOB.COM", '2016-05-06');
Query OK, 1 rows affected (0.00 sec)
mysql>
```

**注意：** 使用箭头标记 **->** 不是 SQL 语句的一部分，它仅仅表示一个新行，如果一条SQL语句太长，我们可以通过回车键来创建一个新行来编写 SQL 语句，SQL 语句的命令结束符为分号 **;**。

在以上实例中，我们并没有提供 runoob_id 的数据，因为该字段我们在创建表的时候已经设置它为 AUTO_INCREMENT(自动增加) 属性。 所以，该字段会自动递增而不需要我们去设置。实例中 NOW() 是一个 MySQL 函数，该函数返回日期和时间。

接下来我们可以通过以下语句查看数据表数据：

#### 读取数据表

select * from runoob_tbl;

输出结果：

![img](/img/71971E68-78B3-4964-AC4C-E75114D3B5B5.jpg)

**如果所有的列都要添加数据可以不规定列进行添加数据**

```
mysql> INSERT INTO runoob_tbl
    -> VALUES
    -> (0, "JAVA 教程", "RUNOOB.COM", '2016-05-06');
```

第一列如果没有设置主键自增（PRINARY KEY AUTO_INCREMENT）的话添加第一列数据比较容易错乱，要不断的查询表看数据。

如果添加过主键自增（PRINARY KEY AUTO_INCREMENT）第一列在增加数据的时候，可以写为0或者null，这样添加数据可以自增， 从而可以添加全部数据，而不用特意规定那几列添加数据。

参考资料：

https://www.runoob.com/mysql/mysql-insert-query.html

### MySQL UPDATE 更新

如果我们需要修改或更新 MySQL 中的数据，我们可以使用 SQL UPDATE 命令来操作。

#### 语法

以下是 UPDATE 命令修改 MySQL 数据表数据的通用 SQL 语法：

```
UPDATE table_name SET field1=new-value1, field2=new-value2
[WHERE Clause]
```

- 你可以同时更新一个或多个字段。
- 你可以在 WHERE 子句中指定任何条件。
- 你可以在一个单独表中同时更新数据。

当你需要更新数据表中指定行的数据时 WHERE 子句是非常有用的。

------

通过命令提示符更新数据

以下我们将在 SQL UPDATE 命令使用 WHERE 子句来更新 runoob_tbl 表中指定的数据：

#### 实例

以下实例将更新数据表中 runoob_id 为 3 的 runoob_title 字段值：

#### SQL UPDATE 语句：

```

mysql> UPDATE runoob_tbl SET runoob_title='学习 C++' WHERE runoob_id=3; Query OK, 1 rows affected (0.01 sec)  mysql> SELECT * from runoob_tbl WHERE runoob_id=3; 
+-----------+--------------+---------------+-----------------+ 
| runoob_id | runoob_title | runoob_author | submission_date 
| +-----------+--------------+---------------+-----------------+ 
| 3         | 学习 C++   | RUNOOB.COM    | 2016-05-06      
| +-----------+--------------+---------------+-----------------+ 
1 rows in set (0.01 sec)

从结果上看，runoob_id 为 3 的 runoob_title 已被修改。

```

参考资料

https://www.runoob.com/mysql/mysql-update-query.html

### MySQL DELETE 语句

你可以使用 SQL 的 DELETE FROM 命令来删除 MySQL 数据表中的记录。

你可以在 **mysql>** 命令提示符或 PHP 脚本中执行该命令。

#### 语法

以下是 SQL DELETE 语句从 MySQL 数据表中删除数据的通用语法：

```
DELETE FROM table_name [WHERE Clause]
```

- 如果没有指定 WHERE 子句，MySQL 表中的所有记录将被删除。
- 你可以在 WHERE 子句中指定任何条件
- 您可以在单个表中一次性删除记录。

当你想删除数据表中指定的记录时 WHERE 子句是非常有用的。

这里我们将在 SQL DELETE 命令中使用 WHERE 子句来删除 MySQL 数据表 runoob_tbl 所选的数据。

#### 实例

以下实例将删除 runoob_tbl 表中 runoob_id 为3 的记录：

#### DELETE 语句：

```
mysql> use RUNOOB; 
Database changed 
mysql> DELETE FROM runoob_tbl WHERE runoob_id=3; 
Query OK, 1 row affected (0.23 sec)
```



#### delete，drop，truncate 都有删除表的作用，区别如下

-  1、delete 和 truncate 仅仅删除表数据，drop 连表数据和表结构一起删除，打个比方，delete 是单杀，truncate 是团灭，drop 是把电脑摔了。
-  2、delete 是 DML 语句，操作完以后如果没有不想提交事务还可以回滚，truncate 和 drop 是 DDL 语句，操作完马上生效，不能回滚，打个比方，delete 是发微信说分手，后悔还可以撤回，truncate 和 drop 是直接扇耳光说滚，不能反悔。
-  3、执行的速度上，**drop>truncate>delete**，打个比方，drop 是神舟火箭，truncate 是和谐号动车，delete 是自行车。

参考资料：

https://www.runoob.com/mysql/mysql-delete-query.html

### MySQL 查询数据

MySQL 数据库使用SQL SELECT语句来查询数据。

你可以通过 mysql> 命令提示窗口中在数据库中查询数据，或者通过PHP脚本来查询数据。

#### 语法

以下为在MySQL数据库中查询数据通用的 SELECT 语法：

```
SELECT column_name,column_name
FROM table_name
[WHERE Clause]
[LIMIT N][ OFFSET M]
```

- 查询语句中你可以使用一个或者多个表，表之间使用逗号(,)分割，并使用WHERE语句来设定查询条件。
- SELECT 命令可以读取一条或者多条记录。
- 你可以使用星号（*）来代替其他字段，SELECT语句会返回表的所有字段数据
- 你可以使用 WHERE 语句来包含任何条件。
- 你可以使用 LIMIT 属性来设定返回的记录数。
- 你可以通过OFFSET指定SELECT语句开始查询的数据偏移量。默认情况下偏移量为0。

#### 实例

以下实例将返回数据表 runoob_tbl 的所有记录:

#### 读取数据表

select * from runoob_tbl;

输出结果：

![img](/img/DB742246-84F3-4447-BD43-6BAEADD7CA91.jpg)

参考资料：

https://www.runoob.com/mysql/mysql-select-query.html



# MySQL函数

## 什么是函数：

 

- 函数存储着一系列sql语句，调用函数就是一次性执行这些语句。所以函数可以降低语句重复。【但注意的是函数注重返回值，不注重执行过程，所以一些语句无法执行。所以函数并不是单纯的sql语句集合。】
- mysql函数有自己的自定义函数（已经定义好了的函数）。
- 这里主要介绍如何自定义函数。

 

**补充**

- 函数与存储过程的区别：函数只会返回一个值，不允许返回一个结果集。函数强调返回值，所以函数不允许返回多个值的情况，即使是查询语句。

  ```
  -- 不行的代码：Not allowed to return a result set from a function
  create function myf()returns int 
  begin
  select * from student;
  return 100;
  end;
  ```

## 函数的创建

### 语法

```
create function 函数名([参数列表]) returns 数据类型
begin
 sql语句;
 return 值;
end;
```

- 参数列表的格式是： 变量名 数据类型



### 示例

```
-- 最简单的仅有一条sql的函数
create function myselect2() returns int return 666;
select myselect2(); -- 调用函数

--
create function myselect3() returns int
begin 
    declare c int;
    select id from class where cname="python" into c;
    return c;
end;
select myselect3();
-- 带传参的函数
create function myselect5(name varchar(15)) returns int
begin 
    declare c int;
    select id from class where cname=name into c;
    return c;
end;
select myselect5("python");
```

 

 

**补充**

- 还可以有一些特别的选项，特别的选项写在return 之后，begin之前，如：

- comment:一个关于函数的描述
- 还有一些比如sql security等选项，有兴趣可以自行百度。这里不讲解，仅一提有此知识点。

 

## 函数的调用

 

- 直接使用函数名()就可以调用【**虽然这么说，但返回的是一个结果，sql中不使用select的话任何结果都无法显示出来（所以单纯调用会报错），】**

- 如果想要传入参数可以使用函数名(参数)

- 调用方式【下面调用的函数都是上面中创建的。】：

  复制代码

  ```
  -- 无参调用
  select myselect3();
  -- 传参调用
  select myselect5("python");
  select * from class where id=myselect5("python");
  ```

##  函数的查看

 

- 查看函数创建语句：show create function 函数名;
- 查看所有函数：show function status [like 'pattern'];

 

## 函数的修改

- 函数的修改只能修改一些如comment的选项，不能修改内部的sql语句和参数列表。
- alter function 函数名 选项；

 

##  函数的删除

- drop function 函数名;

参考资料

https://www.cnblogs.com/progor/p/8871480.html

## MySQL内置函数

可以对 MySQL 常用函数进行简单的分类，大概包括数值型函数、字符串型函数、日期时间函数、聚合函数等。

### MySQL 数值型函数

| 函数名称                                                     | 作 用                                                      |
| ------------------------------------------------------------ | ---------------------------------------------------------- |
| [ABS](http://c.biancheng.net/mysql/abc.html)                 | 求绝对值                                                   |
| [SQRT](http://c.biancheng.net/mysql/sqrt.html)               | 求二次方根                                                 |
| [MOD](http://c.biancheng.net/mysql/mod.html)                 | 求余数                                                     |
| [CEIL 和 CEILING](http://c.biancheng.net/mysql/ceil_celing.html) | 两个函数功能相同，都是返回不小于参数的最小整数，即向上取整 |
| [FLOOR](http://c.biancheng.net/mysql/floor.html)             | 向下取整，返回值转化为一个BIGINT                           |
| [RAND](http://c.biancheng.net/mysql/rand.html)               | 生成一个0~1之间的随机数，传入整数参数是，用来产生重复序列  |
| [ROUND](http://c.biancheng.net/mysql/round.html)             | 对所传参数进行四舍五入                                     |
| [SIGN](http://c.biancheng.net/mysql/sign.html)               | 返回参数的符号                                             |
| [POW 和 POWER](http://c.biancheng.net/mysql/pow_power.html)  | 两个函数的功能相同，都是所传参数的次方的结果值             |
| [SIN](http://c.biancheng.net/mysql/sin.html)                 | 求正弦值                                                   |
| [ASIN](http://c.biancheng.net/mysql/asin.html)               | 求反正弦值，与函数 SIN 互为反函数                          |
| [COS](http://c.biancheng.net/mysql/cos.html)                 | 求余弦值                                                   |
| [ACOS](http://c.biancheng.net/mysql/acos.html)               | 求反余弦值，与函数 COS 互为反函数                          |
| [TAN](http://c.biancheng.net/mysql/tan.html)                 | 求正切值                                                   |
| [ATAN](http://c.biancheng.net/mysql/atan.html)               | 求反正切值，与函数 TAN 互为反函数                          |
| [COT](http://c.biancheng.net/mysql/cot.html)                 | 求余切值                                                   |

### MySQL 字符串函数

| 函数名称                                                 | 作 用                                                        |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| [LENGTH](http://c.biancheng.net/mysql/length.html)       | 计算字符串长度函数，返回字符串的字节长度                     |
| [CONCAT](http://c.biancheng.net/mysql/concat.html)       | 合并字符串函数，返回结果为连接参数产生的字符串，参数可以使一个或多个 |
| [INSERT](http://c.biancheng.net/mysql/insert.html)       | 替换字符串函数                                               |
| [LOWER](http://c.biancheng.net/mysql/lower.html)         | 将字符串中的字母转换为小写                                   |
| [UPPER](http://c.biancheng.net/mysql/upper.html)         | 将字符串中的字母转换为大写                                   |
| [LEFT](http://c.biancheng.net/mysql/left.html)           | 从左侧字截取符串，返回字符串左边的若干个字符                 |
| [RIGHT](http://c.biancheng.net/mysql/right.html)         | 从右侧字截取符串，返回字符串右边的若干个字符                 |
| [TRIM](http://c.biancheng.net/mysql/trim.html)           | 删除字符串左右两侧的空格                                     |
| [REPLACE](http://c.biancheng.net/mysql/replace.html)     | 字符串替换函数，返回替换后的新字符串                         |
| [SUBSTRING](http://c.biancheng.net/mysql/substring.html) | 截取字符串，返回从指定位置开始的指定长度的字符换             |
| [REVERSE](http://c.biancheng.net/mysql/reverse.html)     | 字符串反转（逆序）函数，返回与原始字符串顺序相反的字符串     |

### MySQL 日期和时间函数

| 函数名称                                                     | 作 用                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [CURDATE 和 CURRENT_DATE](http://c.biancheng.net/mysql/curdate_current_date.html) | 两个函数作用相同，返回当前系统的日期值                       |
| [CURTIME 和 CURRENT_TIME](http://c.biancheng.net/mysql/curtime_current_time.html) | 两个函数作用相同，返回当前系统的时间值                       |
| [NOW 和 SYSDATE](http://c.biancheng.net/mysql/now_sysdate.html) | 两个函数作用相同，返回当前系统的日期和时间值                 |
| [UNIX_TIMESTAMP](http://c.biancheng.net/mysql/unix_timestamp.html) | 获取UNIX时间戳函数，返回一个以 UNIX 时间戳为基础的无符号整数 |
| [FROM_UNIXTIME](http://c.biancheng.net/mysql/from_unixtime.html) | 将 UNIX 时间戳转换为时间格式，与UNIX_TIMESTAMP互为反函数     |
| [MONTH](http://c.biancheng.net/mysql/month.html)             | 获取指定日期中的月份                                         |
| [MONTHNAME](http://c.biancheng.net/mysql/monthname.html)     | 获取指定日期中的月份英文名称                                 |
| [DAYNAME](http://c.biancheng.net/mysql/dayname.html)         | 获取指定曰期对应的星期几的英文名称                           |
| [DAYOFWEEK](http://c.biancheng.net/mysql/dayofweek.html)     | 获取指定日期对应的一周的索引位置值                           |
| [WEEK](http://c.biancheng.net/mysql/week.html)               | 获取指定日期是一年中的第几周，返回值的范围是否为 0〜52 或 1〜53 |
| [DAYOFYEAR](http://c.biancheng.net/mysql/dayofyear.html)     | 获取指定曰期是一年中的第几天，返回值范围是1~366              |
| [DAYOFMONTH](http://c.biancheng.net/mysql/dayofmonth.html)   | 获取指定日期是一个月中是第几天，返回值范围是1~31             |
| [YEAR](http://c.biancheng.net/mysql/year.html)               | 获取年份，返回值范围是 1970〜2069                            |
| [TIME_TO_SEC](http://c.biancheng.net/mysql/time_to_sec.html) | 将时间参数转换为秒数                                         |
| [SEC_TO_TIME](http://c.biancheng.net/mysql/sec_to_time.html) | 将秒数转换为时间，与TIME_TO_SEC 互为反函数                   |
| [DATE_ADD 和 ADDDATE](http://c.biancheng.net/mysql/date_add_adddate.html) | 两个函数功能相同，都是向日期添加指定的时间间隔               |
| [DATE_SUB 和 SUBDATE](http://c.biancheng.net/mysql/date_sub_subdate.html) | 两个函数功能相同，都是向日期减去指定的时间间隔               |
| [ADDTIME](http://c.biancheng.net/mysql/addtime.html)         | 时间加法运算，在原始时间上添加指定的时间                     |
| [SUBTIME](http://c.biancheng.net/mysql/subtime.html)         | 时间减法运算，在原始时间上减去指定的时间                     |
| [DATEDIFF](http://c.biancheng.net/mysql/datediff.html)       | 获取两个日期之间间隔，返回参数 1 减去参数 2 的值             |
| [DATE_FORMAT](http://c.biancheng.net/mysql/date_format.html) | 格式化指定的日期，根据参数返回指定格式的值                   |
| [WEEKDAY](http://c.biancheng.net/mysql/weekday.html)         | 获取指定日期在一周内的对应的工作日索引                       |

### MySQL 聚合函数

| 函数名称                                         | 作用                             |
| ------------------------------------------------ | -------------------------------- |
| [MAX](http://c.biancheng.net/mysql/max.html)     | 查询指定列的最大值               |
| [MIN](http://c.biancheng.net/mysql/min.html)     | 查询指定列的最小值               |
| [COUNT](http://c.biancheng.net/mysql/count.html) | 统计查询结果的行数               |
| [SUM](http://c.biancheng.net/mysql/sum.html)     | 求和，返回指定列的总和           |
| [AVG](http://c.biancheng.net/mysql/avg.html)     | 求平均值，返回指定列数据的平均值 |

### MySQL 流程控制函数

| 函数名称                                           | 作用           |
| -------------------------------------------------- | -------------- |
| [IF](http://c.biancheng.net/mysql/if.html)         | 判断，流程控制 |
| [IFNULL](http://c.biancheng.net/mysql/ifnull.html) | 判断是否为空   |
| [CASE](http://c.biancheng.net/mysql/case.html)     | 搜索语句       |

**1、IF(expr,v1,v2)函数**

　　如果表达式expr成立，返回结果v1；否则，返回结果v2。

```
SELECT IF(1 > 0,'正确','错误')    
->正确
```

　　**2、IFNULL(v1,v2)函数**

　　如果v1的值不为NULL，则返回v1，否则返回v2。

```
SELECT IFNULL(null,'Hello Word')
->Hello Word
```

　　**3、CASE**

　　**语法1：**

```
CASE 
　　WHEN e1
　　THEN v1
　　WHEN e2
　　THEN e2
　　...
　　ELSE vn
END
```

　　CASE表示函数开始，END表示函数结束。如果e1成立，则返回v1,如果e2成立，则返回v2，当全部不成立则返回vn，而当有一个成立之后，后面的就不执行了。

```
SELECT CASE 
　　WHEN 1 > 0
　　THEN '1 > 0'
　　WHEN 2 > 0
　　THEN '2 > 0'
　　ELSE '3 > 0'
　　END
->1 > 0
```

　　**语法2：**

```
CASE expr 
　　WHEN e1 THEN v1
　　WHEN e1 THEN v1
　　...
　　ELSE vn
END
```

　　如果表达式expr的值等于e1，返回v1；如果等于e2,则返回e2。否则返回vn。

```
SELECT CASE 1 
　　WHEN 1 THEN '我是1'
　　WHEN 2 THEN '我是2'
ELSE '你是谁'
```

###  MySQL系统信息函数

系统信息函数用来查询MySQL数据库的系统信息。

| 函数                                                         | 作用                                                     |
| ------------------------------------------------------------ | -------------------------------------------------------- |
| VERSION()                                                    | 返回数据库的版本号SELECT VERSION() ->5.0.67-community-nt |
| CONNECTION_ID()                                              | 返回服务器的连接数                                       |
| DATABASE()、SCHEMA                                           | 返回当前数据库名                                         |
| USER()、SYSTEM_USER()、SESSION_USER()、CURRENT_USER()、CURRENT_USER | 返回当前用户                                             |
| CHARSET(str)                                                 | 返回字符串str的字符集                                    |
| COLLATION(str)                                               | 返回字符串str的字符排列方式                              |
| LAST_INSERT_ID()                                             | 返回最近生成的AUTO_INCREMENT值                           |

### MySQL加密函数

加密函数是MySQL用来对数据进行加密的函数。

　　**1、PASSWORD(str)**

　　该函数可以对字符串str进行加密，一般情况下，PASSWORD(str)用于给用户的密码加密。

```
SELECT PASSWORD('123')
    ->*23AE809DDACAF96AF0FD78ED04B6A265E05AA257
```

　　**2、MD5**

　　MD5(str)函数可以对字符串str进行散列，可以用于一些普通的不需要解密的数据加密。

```
SELECT md5('123')
    ->202cb962ac59075b964b07152d234b70
```

　　**3、ENCODE(str,pswd_str)与DECODE(crypt_str,pswd_str)**

　　ENCODE函数可以使用加密密码pswd_str来加密字符串str，加密结果是二进制数，需要使用BLOB类型的字段保存。该函数与DECODE是一对，需要同样的密码才能够解密。

```
SELECT ENCODE('123','xxoo')
    ->;vx
SELECT DECODE(';vx','xxoo')
    ->123
```

### MySQL其他函数

**1、格式化函数FORMAT(x,n)**

　　FORMAT(x,n)函数可以将数字x进行格式化，将x保留到小数点后n位。

```
SELECT FORMAT(3.1415926,3)
    ->3.142
```

　　**2、不同进制的数字进行转换**

- ASCII(s) 返回字符串s的第一个字符的ASCII码；
- BIN（x） 返回x的二进制编码；
- HEX(x) 返回x的十六进制编码；
- OCT(x) 返回x的八进制编码；
- CONV(x,f1,f2) 返回f1进制数变成f2进制数；

　　**3、IP地址与数字相互转换的函数**

- INET_ATON(IP)函数可以将IP地址转换为数字表示；IP值需要加上引号；
- INET_NTOA(n)函数可以将数字n转换成IP形式。

```
SELECT INET_ATON('192.168.0.1')
    ->3232235521
SELECT INET_NTOA(3232235521)
    ->192.168.0.1
```

　　**4、加锁函数和解锁函数**

- GET_LOCK(name,time)函数定义一个名称为nam、持续时间长度为time秒的锁。如果锁定成功，则返回1；如果尝试超时，则返回0；如果遇到错误，返回NULL。
- RELEASE_LOCK(name)函数解除名称为name的锁。如果解锁成功，则返回1；如果尝试超时，返回0了如果解锁失败，返回NULL；
- IS_FREE_LOCK(name)函数判断是否已使用名为name的锁定。如果使用，返回0，否则，返回1；

 

```
SELECT GET_LOCK('MySQL',10)
    ->1    (持续10秒)
SELECT IS_FREE_LOCK('MySQL')
    ->1    
SELECT RELEASE_LOCK('MySQL')
    ->1
```

　　**5、重复执行指定操作的函数**

　　BENCHMARK(count.expr)函数将表达式expr重复执行count此，然后返回执行时间。该函数可以用来判断MySQL处理表达式的速度。

```
SELECT BENCHMARK(10000,NOW())
    ->0    返回系统时间1万
```

　　**6、改变字符集的函数**

　　CONVERT(s USING cs)函数将字符串s的字符集变成cs。

```
SELECT CHARSET('ABC')
    ->utf-8    

SELECT CHARSET(CONVERT('ABC' USING gbk))
    ->gbk
```

　　**7、转换数据类型**

- CAST(x AS type)
- CONVERT(x,type)

　　这两个函数只对BINARY、CHAR、DATE、DATETIME、TIME、SIGNED INTEGER、UNSIGNED INTEGER。

```
SELECT CAST('123' AS UNSIGNED INTEGER) + 1
    ->124

SELECT '123' + 1
    ->124 其实MySQL能默认转换

SELECT CAST(NOW() AS DATE)　　->2014-12-18
```

参考资料：

https://www.cnblogs.com/kissdodog/p/4168721.html

http://c.biancheng.net/mysql/function/

# MySQL视图

## 什么是视图

通俗的讲，视图就是一条SELECT语句执行后返回的结果集。所以我们在创建视图的时候，主要的工作就落在创建这条SQL查询语句上。

视图是一个**虚拟表**，是sql的查询结果，其内容由查询定义。同真实的表一样，视图包含一系列带有名称的列和行数据，在使用视图时动态生成。视图的数据变化会影响到基表，基表的数据变化也会影响到视图[insert update delete ] ; 创建视图需要create view 权限，并且对于查询涉及的列有select权限；使用create or replace 或者 alter修改视图，那么还需要改视图的drop权限。

## 视图的特性

视图是对若干张基本表的引用，一张虚表，查询语句执行的结果，不存储具体的数据（基本表数据发生了改变，视图也会跟着改变）；

可以跟基本表一样，进行增删改查操作(ps:增删改操作有条件限制)；

 　![img](https://img2018.cnblogs.com/blog/1215492/201903/1215492-20190306103335338-1776417010.png)

## 视图使用基本语法

### 创建视图

```
create view  视图名  as  select 字段名 from 表名;
```

### 修改视图

```
alter view 视图名 as select 语句;
alter view 视图名 as  select 视图;
```

### 显示视图创建情况

```
show create view 视图名;
```

### 查看视图

```
Show tables；
Show table status [ from db_name ] [ like ‘pattern’ ]；
SELECT * FROM information_schema.views where table_name = 'my_view';
```

### 删除视图

```
drop view 视图名[,视图名…];
```

### 重命名视图

```
Rename table 视图名 to 新视图名;
```

## 视图使用示例

### 参考表结构

```
-- ----------------------------

-- Table structure for `course`

-- ----------------------------

DROP TABLE IF EXISTS `course`;

CREATE TABLE `course` (

 `id` bigint(20) NOT NULL AUTO_INCREMENT,

 `name` varchar(200) NOT NULL,

 `description` varchar(500) NOT NULL,

 PRIMARY KEY (`id`)

) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;



-- ----------------------------

-- Records of course

-- ----------------------------

INSERT INTO `course` VALUES ('1', 'JAVA', 'JAVA课程');

INSERT INTO `course` VALUES ('2', 'C++', 'C++课程');

INSERT INTO `course` VALUES ('3', 'C语言', 'C语言课程');



-- ----------------------------

-- Table structure for `user`

-- ----------------------------

DROP TABLE IF EXISTS `user`;

CREATE TABLE `user` (

 `id` bigint(20) NOT NULL AUTO_INCREMENT,

 `account` varchar(255) NOT NULL,

 `name` varchar(255) NOT NULL,

 `address` varchar(255) DEFAULT NULL,

 `others` varchar(200) DEFAULT NULL,

 `others2` varchar(200) DEFAULT NULL,

 PRIMARY KEY (`id`)

) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8;



-- ----------------------------

-- Records of user

-- ----------------------------

INSERT INTO `user` VALUES ('1', 'user1', '小陈', '美国', '1', '1');

INSERT INTO `user` VALUES ('2', 'user2', '小张', '日本', '2', '2');

INSERT INTO `user` VALUES ('3', 'user3', '小王', '中国', '3', '3');



-- ----------------------------

-- Table structure for `user_course`

-- ----------------------------

DROP TABLE IF EXISTS `user_course`;

CREATE TABLE `user_course` (

 `id` bigint(20) NOT NULL AUTO_INCREMENT,

 `userid` bigint(20) NOT NULL,

 `courseid` bigint(20) NOT NULL,

 PRIMARY KEY (`id`)

) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8;



-- ----------------------------

-- Records of user_course

-- ----------------------------

INSERT INTO `user_course` VALUES ('1', '1', '2');

INSERT INTO `user_course` VALUES ('2', '1', '3');

INSERT INTO `user_course` VALUES ('3', '2', '1');

INSERT INTO `user_course` VALUES ('4', '2', '2');

INSERT INTO `user_course` VALUES ('5', '2', '3');

INSERT INTO `user_course` VALUES ('6', '3', '2');
```



### 查表原语句

```
SELECT
    `uc`.`id` AS `id`,
    `u`.`name` AS `username`,
    `c`.`name` AS `coursename`
FROM
    `user` `u`
LEFT JOIN `user_course` `uc` ON ((`u`.`id` = `uc`.`userid`))
LEFT JOIN `course` `c` ON ((`uc`.`courseid` = `c`.`id`))
WHERE
    u.`name` = '小张'
```

### 创建单表视图

```
DROP VIEW
IF EXISTS `view_user_keyinfo`;

CREATE ALGORITHM = UNDEFINED DEFINER = `root`@`localhost` SQL SECURITY DEFINER VIEW `view_user_keyinfo` AS SELECT
    `u`.`id` AS `id`,
    `u`.`account` AS `account`,
    `u`.`name` AS `username`
FROM
    `user` `u`;
			进行增删改操作如下，操作成功（注意user表中的其它字段要允许为空，否则操作失败）：
			INSERT INTO view_user_keyinfo (account, username)
VALUES
    ('test1', 'test1');
			DELETE
FROM
    view_user_keyinfo
WHERE
    username = 'test1';
			UPDATE view_user_keyinfo
SET username = 'updateuser'
WHERE
    id = 1
```

### 创建多表视图

```
DROP VIEW
IF EXISTS `view_user_course`;

CREATE ALGORITHM = UNDEFINED 
DEFINER = `root`@`localhost` 
SQL SECURITY DEFINER 
VIEW `view_user_course` AS (
    SELECT
        `uc`.`id` AS `id`,
        `u`.`name` AS `username`,
        `c`.`name` AS `coursename`
    FROM
        (
            (
                `user` `u`
                LEFT JOIN `user_course` `uc` ON ((`u`.`id` = `uc`.`userid`))
            )
            LEFT JOIN `course` `c` ON ((`uc`.`courseid` = `c`.`id`))
        )
);
			几点说明（MySQL中的视图在标准SQL的基础之上做了扩展）
				ALGORITHM=UNDEFINED：指定视图的处理算法；
				DEFINER=`root`@`localhost`：指定视图创建者；
				SQL SECURITY DEFINER：指定视图查询数据时的安全验证方式；
	从视图查询数据
		SELECT
    vuc.username,
    vuc.coursename
FROM
    view_user_course vuc
WHERE
     vuc.username = '小张'
```

### 视图增删改数据

#### 正确的示例

视图与表是一对一关系情况：如果没有其它约束（如视图中没有的字段，在基本表中是必填字段情况），是可以进行增删改数据操作

```
DROP VIEW
IF EXISTS `view_user_keyinfo`;

CREATE ALGORITHM = UNDEFINED DEFINER = `root`@`localhost` SQL SECURITY DEFINER VIEW `view_user_keyinfo` AS SELECT
    `u`.`id` AS `id`,
    `u`.`account` AS `account`,
    `u`.`name` AS `username`
FROM
    `user` `u`;
    
#进行增删改操作如下，操作成功（注意user表中的其它字段要允许为空，否则操作失败）：
				INSERT INTO view_user_keyinfo (account, username)
VALUES
    ('test1', 'test1');
    
DELETE
FROM
    view_user_keyinfo
WHERE
    username = 'test1';
				UPDATE view_user_keyinfo
SET username = 'updateuser'
WHERE
    id = 1
```

视图与表是一对多关系情况：如果只修改一张表的数据，且没有其它约束（如视图中没有的字段，在基本表中是必填字段情况），是可以进行改数据操作

```
update view_user_course set coursename='JAVA' where id=1;
update view_user_course set username='test2' where id=3;
```

#### 错误的示例

```
update view_user_course set username='test',coursename='JAVASCRIPT' where id=3
```

操作失败，提示错误信息如下：

```

[SQL] update view_user_course set username='test',coursename='JAVASCRIPT' where id=3

[Err] 1393 - Can not modify more than one base table through a join view 'demo.view_user_course'
```

因为不能在一张由多张关联表连接而成的视图上做同时修改两张表的操作；

#### 其他错误示例

```
delete from view_user_course where id=3;
insert into view_user_course(username, coursename) VALUES('2','3');
```

## 使用场景

- 权限控制的时候，不希望用户访问表中某些含敏感信息的列，比如salary...

- 关键信息来源于多个复杂关联表，可以创建视图提取我们需要的信息，简化操作；
- 大数据分表时可以用到

比如,表的行数超过200万行时,就会变慢,

可以把一张的表的数据拆成4张表来存放.

News表

Newsid, 1,2,3,4

News1,news2,news3,news4表

 

把一张表的数据分散到4张表里,分散的方法很多,

最常用可以用id取模来计算.

Id%4+1 = [1,2,3,4]

比如 $_GET['id'] = 17,

17%4 + 1 = 2, $tableName = 'news'.'2'

Select * from news2 where id = 17;

**还可以用视图, 把4张表形成一张视图**

Create view news as select from n1 union select from n2 union.........

参考资料

​	https://www.cnblogs.com/cshaptx4869/p/10481749.html
​	https://www.cnblogs.com/chenpi/p/5133648.html
​	http://c.biancheng.net/view/2584.html





# MySQL存储过程

## 什么是存储过程

SQL语句需要先编译然后执行，而存储过程（Stored Procedure）是一组为了完成特定功能的SQL语句集，经编译后存储在数据库中，用户通过指定存储过程的名字并给定参数（如果该存储过程带有参数）来调用执行它。

存储过程是可编程的函数，在数据库中创建并保存，可以由SQL语句和控制结构组成。当想要在不同的应用程序或平台上执行相同的函数，或者封装特定功能时，存储过程是非常有用的。数据库中的存储过程可以看做是对编程中面向对象方法的模拟，它允许控制数据的访问方式。

存储过程的优点：

(1).**增强SQL语言的功能和灵活性**：存储过程可以用控制语句编写，有很强的灵活性，可以完成复杂的判断和较复杂的运算。

(2).**标准组件式编程**：存储过程被创建后，可以在程序中被多次调用，而不必重新编写该存储过程的SQL语句。而且数据库专业人员可以随时对存储过程进行修改，对应用程序源代码毫无影响。

(3).**较快的执行速度**：如果某一操作包含大量的Transaction-SQL代码或分别被多次执行，那么存储过程要比批处理的执行速度快很多。因为存储过程是预编译的。在首次运行一个存储过程时查询，优化器对其进行分析优化，并且给出最终被存储在系统表中的执行计划。而批处理的Transaction-SQL语句在每次运行时都要进行编译和优化，速度相对要慢一些。

(4).减少网络流量：针对同一个数据库对象的操作（如查询、修改），如果这一操作所涉及的Transaction-SQL语句被组织进存储过程，那么当在客户计算机上调用该存储过程时，网络中传送的只是该调用语句，从而大大减少网络流量并降低了网络负载。

(5).作为一种安全机制来充分利用：通过对执行某一存储过程的权限进行限制，能够实现对相应的数据的访问权限的限制，避免了非授权用户对数据的访问，保证了数据的安全。

MySQL 5.0 版本开始支持存储过程。

存储过程（Stored Procedure）是一种在数据库中存储复杂程序，以便外部程序调用的一种数据库对象。

存储过程是为了完成特定功能的SQL语句集，经编译创建并保存在数据库中，用户可通过指定存储过程的名字并给定参数(需要时)来调用执行。

存储过程思想上很简单，就是数据库 SQL 语言层面的代码封装与重用。

### 优点

- 存储过程可封装，并隐藏复杂的商业逻辑。
- 存储过程可以回传值，并可以接受参数。
- 存储过程无法使用 SELECT 指令来运行，因为它是子程序，与查看表，数据表或用户定义函数不同。
- 存储过程可以用在数据检验，强制实行商业逻辑等。

### 缺点

- 存储过程，往往定制化于特定的数据库上，因为支持的编程语言不同。当切换到其他厂商的数据库系统时，需要重写原有的存储过程。
- 存储过程的性能调校与撰写，受限于各种数据库系统。



## 存储过程的创建和调用

存储过程就是具有名字的一段代码，用来完成一个特定的功能。
创建的存储过程保存在数据库的数据字典中。
MYSQL 存储过程中的关键语法
声明语句结束符，可以自定义:

```
DELIMITER $$
或
DELIMITER //
```

### 声明存储过程

```
CREATE PROCEDURE demo_in_parameter(IN p_in int)     
```

### 存储过程开始和结束符号

```
BEGIN .... END    
```

### 变量赋值

```
SET @p_in=1  
```

### 变量定义

```
DECLARE l_int int unsigned default 4000000; 
```

### 创建mysql存储过程、存储函数

```
create procedure 存储过程名(参数)
```

### 创建存储过程

​				

```
CREATE
    [DEFINER = { user | CURRENT_USER }]
　PROCEDURE sp_name ([proc_parameter[,...]])
    [characteristic ...] routine_body

proc_parameter:
    [ IN | OUT | INOUT ] param_name type

characteristic:
    COMMENT 'string'
  | LANGUAGE SQL
  | [NOT] DETERMINISTIC
  | { CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }
  | SQL SECURITY { DEFINER | INVOKER }

routine_body:
　　Valid SQL routine statement

[begin_label:] BEGIN
　　[statement_list]
　　　　……
END [end_label]
```

### 调用存储过程

```
call sp_name[(传参)];
```

### 存储过程体

存储过程体包含了在过程调用时必须执行的语句，例如：dml、ddl语句，if-then-else和while-do语句、声明变量的declare语句等
过程体格式：以begin开始，以end结束(可嵌套)

```
BEGIN
　　BEGIN
　　　　BEGIN
　　　　　　statements; 
　　　　END
　　END
END
```

**注意**：每个嵌套块及其中的每条语句，必须以分号结束，表示过程体结束的begin-end块(又叫做复合语句compound statement)，则不需要分号。
为语句块贴标签:

```
[begin_label:] BEGIN
　　[statement_list]
END [end_label]
```

例如：

```
label1: BEGIN
　　label2: BEGIN
　　　　label3: BEGIN
　　　　　　statements; 
　　　　END label3 ;
　　END label2;
END label1
```

标签有两个作用：

1. 增强代码的可读性
2. 在某些语句(例如:leave和iterate语句)，需要用到标签

### 实例

#### 创建数据库，备份数据表用于示例操作

```
mysql> create database db1;
mysql> use db1;    
mysql> create table PLAYERS as select * from TENNIS.PLAYERS;
mysql> create table MATCHES  as select * from TENNIS.MATCHES;
					mysql> select * from MATCHES;
+---------+--------+----------+-----+------+
| MATCHNO | TEAMNO | PLAYERNO | WON | LOST |
+---------+--------+----------+-----+------+
|       1 |      1 |        6 |   3 |    1 |
|       7 |      1 |       57 |   3 |    0 |
|       8 |      1 |        8 |   0 |    3 |
|       9 |      2 |       27 |   3 |    2 |
|      11 |      2 |      112 |   2 |    3 |
+---------+--------+----------+-----+------+
5 rows in set (0.00 sec)
```


#### 创建存储过程用于删除除给定球员参加的所有比赛

```
mysql> delimiter $$　　#将语句的结束符号从分号;临时改为两个$$(可以是自定义)
mysql> CREATE PROCEDURE delete_matches(IN p_playerno INTEGER)
​    -> BEGIN
​    -> 　　DELETE FROM MATCHES
​    ->    WHERE playerno = p_playerno;
​    -> END$$
Query OK, 0 rows affected (0.01 sec)

mysql> delimiter;　　#将语句的结束符号恢复为分号
```

#### 调用存储过程删除player_no是57的队员

```
mysql> call delete_matches(57);
Query OK, 1 row affected (0.03 sec)

mysql> select * from MATCHES;
+---------+--------+----------+-----+------+
| MATCHNO | TEAMNO | PLAYERNO | WON | LOST |
+---------+--------+----------+-----+------+
|       1 |      1 |        6 |   3 |    1 |
|       8 |      1 |        8 |   0 |    3 |
|       9 |      2 |       27 |   3 |    2 |
|      11 |      2 |      112 |   2 |    3 |
+---------+--------+----------+-----+------+
```

解析：默认情况下，存储过程和默认数据库相关联，如果想指定存储过程创建在某个特定的数据库下，那么在过程名前面加数据库名做前缀。 在定义过程时，使用 DELIMITER $$ 命令将语句的结束符号从分号 ; 临时改为两个 $$，使得过程体中使用的分号被直接传递到服务器，而不会被客户端（如mysql）解释。

## 存储过程的参数

MySQL存储过程的参数用在存储过程的定义，共有三种参数类型,IN,OUT,INOUT,形式如：

```
CREATE PROCEDURE 存储过程名([[IN |OUT |INOUT ] 参数名 数据类形...])
```

1. IN 输入参数：表示调用者向过程传入值（传入值可以是字面量或变量）

2. OUT 输出参数：表示过程向调用者传出值(可以返回多个值)（传出值只能是变量）

3. INOUT 输入输出参数：既表示调用者向过程传入值，又表示过程向调用者传出值（值只能是变量）


### 1、in 输入参数

```
mysql> delimiter $$
   mysql> create procedure in_param(in p_in int)
   ​    -> begin
   ​    -> 　　select p_in;
   ​    -> 　　set p_in=2;
   ​    ->    select P_in;
   ​    -> end$$
   mysql> delimiter ;

mysql> set @p_in=1;

mysql> call in_param(@p_in);
+------+
| p_in |
+------+
|    1 |
+------+

+------+
| P_in |
+------+
|    2 |
+------+

mysql> select @p_in;
+-------+
| @p_in |
+-------+
|     1 |
+-------+
```

以上可以看出，p_in 在存储过程中被修改，但并不影响 @p_in 的值，因为前者为局部变量、后者为全局变量。

### 2、out输出参数

```
mysql> delimiter //
mysql> create procedure out_param(out p_out int)
​    ->   begin
​    ->     select p_out;
​    ->     set p_out=2;
​    ->     select p_out;
​    ->   end
​    -> //
mysql> delimiter ;

mysql> set @p_out=1;

mysql> call out_param(@p_out);
+-------+
| p_out |
+-------+
|  NULL |
+-------+
　　#因为out是向调用者输出参数，不接收输入的参数，所以存储过程里的p_out为null
+-------+
| p_out |
+-------+
|     2 |
+-------+

mysql> select @p_out;
+--------+
| @p_out |
+--------+
|      2 |
+--------+
```

　　#调用了out_param存储过程，输出参数，改变了p_out变量的值

### 3、inout输入参数

```
mysql> delimiter $$
mysql> create procedure inout_param(inout p_inout int)
    ->   begin
    ->     select p_inout;
    ->     set p_inout=2;
    ->     select p_inout;
    ->   end
    -> $$
mysql> delimiter ;

mysql> set @p_inout=1;

mysql> call inout_param(@p_inout);
+---------+
| p_inout |
+---------+
|       1 |
+---------+

+---------+
| p_inout |
+---------+
|       2 |
+---------+

mysql> select @p_inout;
+----------+
| @p_inout |
+----------+
|        2 |
+----------+
#调用了inout_param存储过程，接受了输入的参数，也输出参数，改变了变量
```

**注意：**

1、如果过程没有参数，也必须在过程名后面写上小括号例：

```
CREATE PROCEDURE sp_name ([proc_parameter[,...]]) ……
```

2、确保参数的名字不等于列的名字，否则在过程体中，参数名被当做列名来处理

**建议：**

- 输入值使用in参数。
- 返回值使用out参数。-
- inout参数就尽量的少用。

## 存储过程中变量

### 变量定义

局部变量声明一定要放在存储过程体的开始

```
DECLAREvariable_name [,variable_name...] datatype [DEFAULT value];
```

其中，datatype 为 MySQL 的数据类型，如: int, float, date,varchar(length)
例如:

```
DECLARE l_int int unsigned default 4000000;  
DECLARE l_numeric number(8,2) DEFAULT 9.95;  
DECLARE l_date date DEFAULT '1999-12-31';  
DECLARE l_datetime datetime DEFAULT '1999-12-31 23:59:59';  
DECLARE l_varchar varchar(255) DEFAULT 'This will not be padded';
```

### 变量赋值

```
SET 变量名 = 表达式值 [,variable_name = expression ...]
```

### 用户变量

在MySQL客户端使用用户变量:

```
mysql > SELECT 'Hello World' into @x;  
mysql > SELECT @x;  
+-------------+  
|   @x        |  
+-------------+  
| Hello World |  
+-------------+  
mysql > SET @y='Goodbye Cruel World';  
mysql > SELECT @y;  
+---------------------+  
|     @y              |  
+---------------------+  
| Goodbye Cruel World |  
+---------------------+  

mysql > SET @z=1+2+3;  
mysql > SELECT @z;  
+------+  
| @z   |  
+------+  
|  6   |  
+------+
```

在存储过程中使用用户变量

```
mysql > CREATE PROCEDURE GreetWorld( ) SELECT CONCAT(@greeting,' World');  
mysql > SET @greeting='Hello';  
mysql > CALL GreetWorld( );  
+----------------------------+  
| CONCAT(@greeting,' World') |  
+----------------------------+  
|  Hello World               |  
+----------------------------+
```

在存储过程间传递全局范围的用户变量

```
mysql> CREATE PROCEDURE p1()   SET @last_procedure='p1';  
mysql> CREATE PROCEDURE p2() SELECT CONCAT('Last procedure was ',@last_procedure);  
mysql> CALL p1( );  
mysql> CALL p2( );  
+-----------------------------------------------+  
| CONCAT('Last procedure was ',@last_proc       |  
+-----------------------------------------------+  
| Last procedure was p1                         |  
 +-----------------------------------------------+
```

**注意:**

1、用户变量名一般以@开头
2、滥用用户变量会导致程序难以理解及管理

### 变量作用域

内部的变量在其作用域范围内享有更高的优先权，当执行到 end。变量时，内部变量消失，此时已经在其作用域外，变量不再可见了，应为在存储过程外再也不能找到这个申明的变量，但是你可以通过 out 参数或者将其值指派给会话变量来保存其值。

```
	mysql > DELIMITER //  
mysql > CREATE PROCEDURE proc3()  
     -> begin 
     -> declare x1 varchar(5) default 'outer';  
     -> begin 
     -> declare x1 varchar(5) default 'inner';  
      -> select x1;  
      -> end;  
       -> select x1;  
     -> end;  
     -> //  
mysql > DELIMITER ;
```



## 存储过程的注释

MySQL 存储过程可使用两种风格的注释

两个横杆--：该风格一般用于单行注释。

c 风格： 一般用于多行注释。
例如：

```
mysql > DELIMITER //  
mysql > CREATE PROCEDURE proc1 --name存储过程名  
     -> (IN parameter1 INTEGER)   
     -> BEGIN   
     -> DECLARE variable1 CHAR(10);   
     -> IF parameter1 = 17 THEN   
     -> SET variable1 = 'birds';   
     -> ELSE 
     -> SET variable1 = 'beasts';   
    -> END IF;   
    -> INSERT INTO table1 VALUES (variable1);  
    -> END   
    -> //  
mysql > DELIMITER ;
```

## MySQL存储过程的查询

我们像知道一个数据库下面有那些表，我们一般采用 showtables; 进行查看。那么我们要查看某个数据库下面的存储过程，是否也可以采用呢？答案是，我们可以查看某个数据库下面的存储过程，但是是另一钟方式。

我们可以用以下语句进行查询：

```
selectname from mysql.proc where db='数据库名';

或者

selectroutine_name from information_schema.routines where routine_schema='数据库名';

或者

showprocedure status where db='数据库名';
```

如果我们想知道，某个存储过程的详细，那我们又该怎么做呢？是不是也可以像操作表一样用describe 表名进行查看呢？

答案是：我们可以查看存储过程的详细，但是需要用另一种方法：

```
SHOWCREATE PROCEDURE 数据库.存储过程名;
```

## MySQL存储过程的修改

```
ALTER PROCEDURE
```

更改用 CREATE PROCEDURE 建立的预先指定的存储过程，其不会影响相关存储过程或存储功能。

## MySQL存储过程的删除

删除一个存储过程比较简单，和删除表一样：

```
DROP PROCEDURE
```

## MySQL存储过程的控制语句

### 条件语句

#### if-then-else 语句

```
mysql > DELIMITER //  
mysql > CREATE PROCEDURE proc2(IN parameter int)  
     -> begin 
     -> declare var int;  
     -> set var=parameter+1;  
     -> if var=0 then 
     -> insert into t values(17);  
     -> end if;  
     -> if parameter=0 then 
     -> update t set s1=s1+1;  
     -> else 
     -> update t set s1=s1+2;  
     -> end if;  
     -> end;  
     -> //  
mysql > DELIMITER ;
```

#### case语句

```
mysql > DELIMITER //  
mysql > CREATE PROCEDURE proc3 (in parameter int)  
     -> begin 
     -> declare var int;  
     -> set var=parameter+1;  
     -> case var  
     -> when 0 then   
     -> insert into t values(17);  
     -> when 1 then   
     -> insert into t values(18);  
     -> else   
     -> insert into t values(19);  
     -> end case;  
     -> end;  
     -> //  
mysql > DELIMITER ; 
case
    when var=0 then
        insert into t values(30);
    when var>0 then
    when var<0 then
    else
end case
```

### 循环语句

#### while ···· end while

```
while 条件 do
    --循环体
end while
```

```
mysql > DELIMITER //  
mysql > CREATE PROCEDURE proc4()  
     -> begin 
     -> declare var int;  
     -> set var=0;  
     -> while var<6 do  
     -> insert into t values(var);  
     -> set var=var+1;  
     -> end while;  
     -> end;  
     -> //  
mysql > DELIMITER ;
```

#### repeat···· end repeat

它在执行操作后检查结果，而 while 则是执行前进行检查。

```
repeat
    --循环体
until 循环条件  
end repeat;
```

​					

```
mysql > DELIMITER //  
mysql > CREATE PROCEDURE proc5 ()  
     -> begin   
     -> declare v int;  
     -> set v=0;  
     -> repeat  
     -> insert into t values(v);  
     -> set v=v+1;  
     -> until v>=5  
     -> end repeat;  
     -> end;  
     -> //  
mysql > DELIMITER ;
```

#### loop ·····endloop

loop 循环不需要初始条件，这点和 while 循环相似，同时和 repeat 循环一样不需要结束条件, leave 语句的意义是离开循环。
					

```
mysql > DELIMITER //  
mysql > CREATE PROCEDURE proc6 ()  
     -> begin 
     -> declare v int;  
     -> set v=0;  
     -> LOOP_LABLE:loop  
     -> insert into t values(v);  
     -> set v=v+1;  
     -> if v >=5 then 
     -> leave LOOP_LABLE;  
     -> end if;  
     -> end loop;  
     -> end;  
     -> //  
mysql > DELIMITER ;
```

#### LABLES 标号

标号可以用在 begin repeat while 或者 loop 语句前，语句标号只能在合法的语句前面使用。可以跳出循环，使运行指令达到复合语句的最后一步。

#### ITERATE迭代

ITERATE 通过引用复合语句的标号,来从新开始复合语句:

```
mysql > DELIMITER //  
mysql > CREATE PROCEDURE proc10 ()  
     -> begin 
     -> declare v int;  
     -> set v=0;  
     -> LOOP_LABLE:loop  
     -> if v=3 then   
     -> set v=v+1;  
     -> ITERATE LOOP_LABLE;  
     -> end if;  
     -> insert into t values(v);  
     -> set v=v+1;  
     -> if v>=5 then 
     -> leave LOOP_LABLE;  
     -> end if;  
     -> end loop;  
     -> end;  
     -> //  
mysql > DELIMITER ;
```

## MySQL存储过程的游标

### MySQL中使用fetch关键字来使用光标，语法形式

​			

```
Fetch cur_name intovar_name[,var_name…]; 
Cur_name表示光标的名称 
Var_name表示将光标中的select语句查询出来的信息存入该参数。Var_name必须在声明光标前就定义好。 
Fetch cur_employee intoemp_name,emp_age; 
```

### 使用范例

#### 将表test_cur1数据复制到test_cur2准备数据表和数据

```
CREATE TABLE `test_cur1` ( 
 `id` int(11) NOT NULL auto_increment, 
 `type` char(11) default NULL, 
 `order1` char(11) default NULL, 
 PRIMARY KEY (`id`) 
) 
INSERT INTO `test_cur1` VALUES (1, '145', 'd1'); 
INSERT INTO `test_cur1` VALUES (2, '134', '1d'); 
INSERT INTO `test_cur1` VALUES (3, '123', '1ad'); 
INSERT INTO `test_cur1` VALUES (4, '121', '1as'); 

CREATE TABLE `test_cur2` ( 
 `id` int(11) NOT NULL auto_increment, 
 `type` char(11) default NULL, 
 `order1` char(11) default NULL, 
 PRIMARY KEY (`id`) 
) 
```

#### 编写存储过程使用游标

```
create procedure get_cur () 
BEGIN
 DECLARE done INT DEFAULT 0; 
 DECLARE ID int(11); 
 DECLARE type char(11); 
 DECLARE order1 char(11); 
 DECLARE mycur CURSOR FOR SELECT * FROM test_cur1;//定义光标 
 DECLARE CONTINUE HANDLER FOR SQLSTATE '02000' SET done = 1; 
 //打开光标 
 OPEN mycur; 
 //开始循环 
 REPEAT 
 FETCH mycur INTO ID,type,order1;//取出光标的内容到临时变量 
 IF NOT done THEN
 INSERT INTO test_cur2 VALUES (ID,type,order1);//插入到另一张表 
 END IF; 
 UNTIL done END REPEAT;//当done=1时结束循环 
 //关闭光标 
 CLOSE mycur; 
END
```

#### 调用存储过程	

```
call get_cur()
```

参考资料

​		https://www.runoob.com/w3cnote/mysql-stored-procedure.html
​		https://www.cnblogs.com/mark-chan/p/5384139.html
​		https://www.jb51.net/article/70677.htm

# MySQL触发器

## 什么是触发器

​		触发器是与表有关的数据库对象，在满足定义条件时触发，并执行触发器中定义的语句集合。触发器的这种特性可以协助应用在数据库端确保数据的完整性。
​		举个例子，比如你现在有两个表【用户表】和【日志表】，当一个用户被创建的时候，就需要在日志表中插入创建的log日志，如果在不使用触发器的情况下，你需要编写程序语言逻辑才能实现，但是如果你定义了一个触发器，触发器的作用就是当你在用户表中插入一条数据的之后帮你在日志表中插入一条日志信息。当然触发器并不是只能进行插入操作，还能执行修改，删除。

## 创建触发器

### 语法规则

```
CREATE TRIGGER trigger_name trigger_time trigger_event ON tb_name FOR EACH ROW trigger_stmt
trigger_name：触发器的名称
tirgger_time：触发时机，为BEFORE或者AFTER
trigger_event：触发事件，为INSERT、DELETE或者UPDATE
tb_name：表示建立触发器的表明，就是在哪张表上建立触发器
trigger_stmt：触发器的程序体，可以是一条SQL语句或者是用BEGIN和END包含的多条语句
所以可以说MySQL创建以下六种触发器：
BEFORE INSERT,BEFORE DELETE,BEFORE UPDATE
AFTER INSERT,AFTER DELETE,AFTER UPDATE
				其中，触发器名参数指要创建的触发器的名字
				BEFORE和AFTER参数指定了触发执行的时间，在事件之前或是之后
				FOR EACH ROW表示任何一条记录上的操作满足触发事件都会触发该触发器
			创建有多个执行语句的触发器
				CREATE TRIGGER 触发器名 BEFORE|AFTER 触发事件
ON 表名 FOR EACH ROW
BEGIN
    执行语句列表
END
```

其中，BEGIN与END之间的执行语句列表参数表示需要执行的多个语句，不同语句用分号隔开
一般情况下，mysql默认是以 ; 作为结束执行语句，与触发器中需要的分行起冲突

为解决此问题可用DELIMITER，如：DELIMITER ||，可以将结束符号变成||

当触发器创建完成后，可以用DELIMITER ;来将结束符号变成;

```
mysql> DELIMITER ||
mysql> CREATE TRIGGER demo BEFORE DELETE
    -> ON users FOR EACH ROW
    -> BEGIN
    -> INSERT INTO logs VALUES(NOW());
    -> INSERT INTO logs VALUES(NOW());
    -> END
    -> ||
Query OK, 0 rows affected (0.06 sec)

mysql> DELIMITER ;
```

上面的语句中，开头将结束符号定义为||，中间定义一个触发器，一旦有满足条件的删除操作

就会执行BEGIN和END中的语句，接着使用||结束

最后使用DELIMITER ; 将结束符号还原

### 触发器事件类型trigger_event

#### INSERT型触发器

激活触发器条件

- INSERT
- LOAD DATA
- REPLACE

load data语句是将文件的内容插入到表中，相当于是insert语句，而replace语句在一般的情况下和insert差不多，但是如果表中存在primary 或者unique索引的时候，如果插入的数据和原来的primary key或者unique相同的时候，会删除原来的数据，然后增加一条新的数据，所以有的时候执行一条replace语句相当于执行了一条delete和insert语句。

#### UPDATE型触发器

激活触发器条件

- UPDATE

#### DELETE型触发器

激活触发器条件

- DELETE
- REPLACE

### NEW和OLD的使用

#### INSERT型触发器

NEW表示将要或者已经新增的数据

#### UPDATE型触发器

OLD表示将要或者已经删除的数据，NEW表示将要或者已经修改的数据

#### DELETE型触发器

OLD表示将要或者已经删除的数据
可以使用一下格式来使用相应的数据			

```
NEW.columnname：新增行的某列数据
OLD.columnname：删除行的某列数据
```

### 查看触发器

```
SHOW TRIGGERS
```

**注：SHOW TRIGGERS语句无法查询指定的触发器**

```
SELECT * FROM information_schema.triggers;
```

所有触发器信息都存储在information_schema数据库下的triggers表中 ,可以使用SELECT语句查询，如果触发器信息过多，最好通过TRIGGER_NAME字段指定查询。

### 删除触发器

```
DROP TRIGGER [IF EXISTS] [schema_name.]trigger_name
```

### 使用示例

#### 用户users表

```
CREATE TABLE `users` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) CHARACTER SET utf8mb4 DEFAULT NULL,
  `add_time` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `name` (`name`(250)) USING BTREE
) ENGINE=MyISAM AUTO_INCREMENT=1000001 DEFAULT CHARSET=latin1;
```

#### 日志logs表

```
CREATE TABLE `logs` (
  `Id` int(11) NOT NULL AUTO_INCREMENT,
  `log` varchar(255) DEFAULT NULL COMMENT '日志说明',
  PRIMARY KEY (`Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='日志表';
```

#### 需求

当在users中插入一条数据，就会在logs中生成一条日志信息。

#### 创建触发器

```
DELIMITER $
CREATE TRIGGER user_log AFTER INSERT ON users FOR EACH ROW
BEGIN
DECLARE s1 VARCHAR(40)character set utf8;
DECLARE s2 VARCHAR(20) character set utf8;#后面发现中文字符编码出现乱码，这里设置字符集
SET s2 = " is created";
SET s1 = CONCAT(NEW.name,s2);     #函数CONCAT可以将字符串连接
INSERT INTO logs(log) values(s1);
END $
DELIMITER ;
```

## 限制和注意事项

1. 触发程序不能调用将数据返回客户端的存储程序，也不能使用采用CALL语句的动态SQL语句，但是允许存储程序通过参数将数据返回触发程序，也就是存储过程或者函数通过OUT或者INOUT类型的参数将数据返回触发器是可以的，但是不能调用直接返回数据的过程。

2. 不能再触发器中使用以显示或隐式方式开始或结束事务的语句，如START TRANS-ACTION,COMMIT或ROLLBACK。
   		

注意事项：MySQL的触发器是按照BEFORE触发器、行操作、AFTER触发器的顺序执行的，其中任何一步发生错误都不会继续执行剩下的操作，如果对事务表进行的操作，如果出现错误，那么将会被回滚，如果是对非事务表进行操作，那么就无法回滚了，数据可能会出错。

参考资料
		https://www.cnblogs.com/geaozhang/p/6819648.html
		https://www.cnblogs.com/zh-1721342390/p/9602941.html

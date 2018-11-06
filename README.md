## MySQL

<br>

数据的存储方式
1) 人工管理阶段
2) 文件系统阶段
3) 数据库系统管理阶段

数据库技术构成
1) 数据库系统DBS
* 数据库管理系统DBMS（DataBaseManagementSystem）
* 数据库管理员DBA（DataBaseAdministrator）
2) SQL语言（结构化查询语言）
* DDL语句--数据库定义语言：CREATE、DROP、ALTER……
* DML语句--数据库操纵语言：INSERT、DELETE、UPDATE、SELECT……
* DCL语句--数据库控制语言：GRANT、REVOKE……
3) 数据访问技术
* ODBC PHP
* JDBC JAVA
4) 数据库管理系统软件
* ORACLE
* SQLServer
* DB2
* MySQL
5) DBA之路
ORACLE--DBA MySQL--DBA对于做DBA来说不论从事那个行业做的内容基本上不会有太多改变我们所关心是数据的安全性,稳定性,高效性需要我们有所改变的是去认识新同事适应新的环境

6) 数据库与我们的生活使用和数据库管理数据的优势
* 我们一直在使用数据库, 站点搜索资料, 登录用户名和密码(银行 邮箱) atm取钱
7) 数据库的具体应用
* 数据库系统就是一套对大量信息进行管理的高效方法而已
* 数据信息的来源: 科研数据, 商业账目记录, 学生信息, 销售业绩, 员工信息等等
* 能够缩短信息记录的录入时间
* 能够缩短信息记录的检索时间
* 灵活的信息检索顺序
* 灵活的输出格式
* 信息记录能够同时被多人使用: 有纸办公2个人不能共用一份资料复印
* 信息记录的远程访问和电子传输: 有纸办公只能在信息资料的存放地点使用

是不是所有的数据操作都要使用数据库？
> 不是, 比如: 商品采购清单列出要买的东西买一样划掉一样不用建数据库记录

<br>

## 介绍MySQL

MySQL是一个开源的小型的关系型数据库管理系统(RDBMS: Relational Database management System) 由瑞典MySQLAB公司开发目前属于ORACLE公司2008被SUN收购SUN2009被ORACLE收购 MySQL所使用的SQL语言是用于访问数据库的最常用标准化语言MySQL软件采用了双授权政策，它分为社区版和商业版，由于其体积小、速度快, 总体拥有成本低尤其是开放源码这一特点,一般中小型网站的开发都选择MySQL作为网站数据库由于其社区版的性能卓越，搭配PHP和Apache可组成良好的开发环境。

## 对MySQL未来看法

MySQL这些年发展的势头很猛,如火如荼基本已经成为互联网行业的标配,也成为各大公司的核心服务,但是这几年也有很多不和谐的因数让使用者们不安ORACLE收MySQL以后，对于MySQL的未来有可能会导致市场占有率下降,毕竟ORACLE是以盈利为目的公司，他总会想法设法在MySQL上找到盈利点或者减少对ORACLE数据库市场的影响。MySQL数据库以后到底会怎么样,被ORACLE抛弃被付费,但是也不用过分担心这个因为当前版本的mysql已经可以满足大部分的业务以后你也可以选择MySQL数据库的分支例如MariaDB, PerconaServer等其他使用innodb的存储引擎的数据库管理系统

## MySQL的主要分支版本有: perconaserver, MariaDB这两大分支

perconaserver是mysql早起的核心研发团队出来创业搞的分支版本,MariaDB是mysql创始人monty搞的一个分支一年前MariaDB开始在国内圈子里面产生一些影响大家还是以测试为主今年随着国外多个大型网站切换到MariaDB,RHEL7使用MariaDB替换原生的MySQL,大家对MariaDB的测试与学习越来越成熟,一些同行已经开始将自己公司的核心库往MariaDB上迁移,这也就意味着,MariaDB的时代已经拉开帷幕MariaDB相比官方的MySQL性能更好,bug更少,feature也更给力所以以前不太看好MariaDB的从业者你们应该好好考虑一下改变自己的观念了

关系型数据库: 将数据保存在不同的表中,而不是将所有数据放在一个大仓库内这样就增加了速度并提高了灵活性。


## 数据库的组织结构

1) 数据库: 用来存放信息的仓库, 构造简单, 遵守一定的规则存放数据
2) 管理系统：用来对数据进行插入, 检索, 修改, 删除等操作的软件
3) 客户端程序：用来连接管理系统
4) 管理员：使用客户端程序连接管理系统，操作数据库。

<br>

## MySQL的C/S结构
1) 支持并发访问: 由服务器提供安排处理sql的先后顺序客户端程序只是把请求发往服务器, 即使出现多个客户同时请求访问同一个数据表的情况也不会出现两个用户同时修改一条记录。
2) 不必在存放数据库的服务器上登录MySQL

<br>

## 什么是数据库(database)?
是一个以某种有组织的方式存储的数据集合保存有组织的数据的容器。

文件柜: 里面可以有一份文件，一组文件；是存放数据的物理位置。
映射到文件系统是一个目录。
什么是表(table)？
保存资料的结构化的文件，可以存储某种特定类型的数据。
文件：记录资料信息。
数据库中的表名唯一，但是不同的数据库中却可以使用同一个表名。
什么是模式(schema)？
描述数据库和表的布局和特性的信息，说明数据在表中如何存储。
文件柜里的文件如何排列以及文件的内容如何排列。
什么是列(colunm)？
表中的一个字段。所有的表都是由一个或多个列组成的，存储着表中的某一部分信息。
什么是数据类型(datatype)？
定义列可以存储的数据种类。
每个列都有相应的数据类型，它限制(或允许)该列存储什么样的数据。如防止在数值
列输入字符。
什么是行(row)？
表中的一个记录。
什么是表空间(Tablespace)？
InnoDB存储引擎才有表空间
数据库表空间：数据库的最大的逻辑单位，数据都是存储在表空间里的
数据文件：数据库存数数据的物理文件，在磁盘上能看到的
什么是SQL？
结构化查询语言StructuredQueryLanguage；是一种专门用来与数据库通信的语
言。
优点：
通用：几乎所有的DBMS(数据库管理系统)都支持sql。
简单：语句都是由描述性很强的英语单词组成的。




4、数据库管理系统的分类
1）关系型数据库
是建立在关系模型基础上的数据库
常见的关系型数据库：             
MySQL：开放源代码的
MariaDB：MySQL的替代品   
Oracle：闭源  甲骨文公司的
SQL Server：微软的 大学常见
DB2：IBM
Sybase：  Sybase公司
	Access： 微软的
2）非关系型数据库(NoSQL)
	与关系型数据库最明显的差别：不再使用SQL作为查询语言。
	常见的非关系型数据库：
	hadoop：分布式数据库   跟云结合
	主要用来处理大数据
	MongoDB：文件导向型数据库
	5、MySQL的结构
	C/S结构：客户端/服务器结构  客户端和服务器端都得安装软件

	6、mysql使用场景
	1）web网站系统
	2）日志记录系统
	3）数据仓库系统
	4）嵌入式系统


RDB对象：
库，表，索引，视图，用户，存储过程，存储函数，触发器，事件调度器

约束：230
域约束：数据类型约束
外键约束：引用完整性约束
主键约束：某字段能指示标志此字段所属的实体，并且不允许为空
唯一性约束： 每一行的某字段都不允许出现相同值，可以为空
一张表中可以有多个

<br>

| DML  |      数据操作语言    |
|------|---------------------|
|INSERT | 向数据库表中插入数据  |
|DELETE | 删除数据库表当中的数据 |
|SELECT | 查询数据库表当中的数据 |
|UPDATE | 更新数据库表当中的数据 |

<br>

| DDL  | 数据定义语言  |
|------|--------------|
|CREATE| 在数据库当中进行表创建 |
|DROP  | 在数据库当中将表删除 |
|ALTER | 在数据库当中为数据表添加一个字段 |

<br>

| DCL | 数据控制语言 |
|-----|-------------|
|GRANT| 为数据库当中的用户进行授权 |
|REVOKE| 删除数据库当中用户的权限 |


关系型数据
表示层 表
逻辑层 存储引擎
物理层 数据文件


MySQL：单线程多进程的

单进程：
守护线程

应用线程
10个用户
256M
1G
256M



关系运算
投影：只输出指定属性
选择：只输出符合条件的行
自然连接：具有相同名字的所有属性取值相同的行
笛卡儿积：
(a+b)*(c+d) = ac+ad+bc+bd

使用程序设计语言如何跟RDBMS交互
1) 嵌入式SQL: 与动态SQL类似，但其语言必须程序编译时完全确定下来ODBC
2) 动态SQL: 程序设计语言使用函数 (mysql_connect()) 或者方法与RDBMS服务器建立连接并进行交互通过建立连接向SQL服务器发送查询语句并将结果保存至变量中进行处理JDBC

使用cmake编译mysql-5.6 cmake 指定编译选项的方式不同于make， 实现方式对比如下：
```shell
./configure         cmake . 
./configure --help    cmake . -LAH  or  ccmake . 
```

指定安装文件的安装路径时常用的选项：
```shell
-DCMAKE_INSTALL_PREFIX=/usr/local/mysql
-DMYSQL_DATADIR=/data/mysql
-DSYSCONFDIR=/etc
```

默认编译的存储引擎包括： csv， myisam， myisamerg 若要安装其他存储引擎，可以使用类似如下编译选项：
```shell
-DWITH_INNOBASE_STORAGE_ENGINE = 1
-DWITH_ARCHIVE_STORAGE_ENGINE = 1
-DWITH_BLACKHOLE_STORAGE_ENGINE = 1
-DWITH_FEDERATED_STORAGE_ENGINE = 1
```

若要明确指定不编译某存储引擎，可以使用类似如下的选项
```shell
-DWITHOUT_<ENGINE>_STORAGE_ENGINE = 1
```
比如：
```shell
-DWITHOUT_EXAMPLE_STORAGE_ENGINE = 1
-DWITHOUT_FEDERATED_STORAGE_ENGINE = 1
-DWITHOUT_PARTITION_STORAGE_ENGINE = 1
```

如若要编译进其它功能，如ssl 等， 则可使用类似如下选项来实现编译时使用某库或不使用某库
```shell
-DWITH_TCP_PORT = 3306
-DMYSQL_UNIX_ADDR = /tmp/mysql.sock
-DENABLED_LOCAL_INFILE = 1
-DEXTRA_CHARSETS = all
-DDEFAULT_CHARSET = utf8
-DDEFAULT_COLLATION = utf8_general_ci
-DWITH_DEBUG = 0
-DENABLE_PROFILING = 1
```

### 编译安装cmake
```shell
[root@zhangyz ~]# tar zxvf cmake-2.8.12.tar.gz -C /usr/src
[root@zhangyz ~]# cd /usr/src/cmake.2.8.12
[root@zhangyz cmake.2.8.12]# ./bootstrap --prefix=/usr/local/cmake 
Curses libraries were not found. Curses GUI for CMake will not be built.
-- Looking for elf.h
-- Looking for elf.h - found
-- Looking for a Fortran compiler
-- Looking for a Fortran compiler - NOTFOUND
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found
-- Found Qt4: /usr/bin/qmake (found version "4.8.7") 
-- Performing Test QT4_WORKS
-- Performing Test QT4_WORKS - Success
-- Performing Test run_pic_test
-- Performing Test run_pic_test - Success
-- Configuring done
-- Generating done
-- Build files have been written to: /usr/src/cmake-2.8.12.2
[root@zhangyz cmake.2.8.12]# make 
[100%] Building C object Tests/CTestTestMemcheck/NoLogDummyChecker/CMakeFiles/pseudonl_purify.dir/ret0.c.o
Linking C executable purify
[100%] Built target pseudonl_purify
Scanning dependencies of target pseudonl_valgrind
[100%] Building C object Tests/CTestTestMemcheck/NoLogDummyChecker/CMakeFiles/pseudonl_valgrind.dir/ret0.c.o
Linking C executable valgrind
[100%] Built target pseudonl_valgrind
[root@zhangyz cmake.2.8.12]# make install
-- Installing: /usr/local/cmake/share/cmake-2.8/editors/vim/cmake-syntax.vim
-- Installing: /usr/local/cmake/share/cmake-2.8/editors/emacs/cmake-mode.el
-- Installing: /usr/local/cmake/share/cmake-2.8/completions/cmake
-- Installing: /usr/local/cmake/share/cmake-2.8/completions/cpack
-- Installing: /usr/local/cmake/share/cmake-2.8/completions/ctest
[root@zhangyz cmake.2.8.12]# /usr/local/cmake/bin/cmake . -LAH
[root@zhangyz cmake.2.8.12]# /usr/local/cmake/bin/cmake --version
cmake version 2.8.12.2

```

### 编译安装mysql
```shell
[root@zhangyz ~]# tar -xf mysql-5.6.16.tar.gz -C /usr/src
[root@zhangyz ~]# cd /usr/src/mysql-5.6.16/
[root@zhangyz mysql-5.6.16]# /usr/local/cmake/bin/cmake . -LAH 
[root@zhangyz mysql-5.6.16]# /usr/local/cmake/bin/cmake . -DCMAKE_INSTALL_PREFIX=/usr/local/mysql -DINSTALL_MYSQLDATADIR=/data/db/ -DMYSQL_DATADIR=/data/db/ -DSYSCONFDIR=/usr/local/mysql/etc -DWITH_INNOBASE_STORAGE_ENGINE=1 -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci -DMYSQL_TCP_PORT=5535 -DMYSQL_UNIX_ADDR=/usr/local/mysql/tmp/mysql.sock -DWITH_EXTRA_CHARSETS=all
-- Running cmake version 2.8.12.2
CMake Warning (dev) at CMakeLists.txt:187 (INCLUDE):
  Syntax Warning in cmake code at

    /usr/src/mysql-5.6.16/cmake/ssl.cmake:237:55

  Argument not separated from preceding token by whitespace.
This warning is for project developers.  Use -Wno-dev to suppress it.

-- MySQL 5.6.16
-- Packaging as: mysql-5.6.16-Linux-x86_64
-- HAVE_VISIBILITY_HIDDEN
-- HAVE_VISIBILITY_HIDDEN
-- HAVE_VISIBILITY_HIDDEN
-- Could NOT find Curses (missing:  CURSES_LIBRARY CURSES_INCLUDE_PATH) 
CMake Error at cmake/readline.cmake:85 (MESSAGE):
  Curses library not found.  Please install appropriate package,

      remove CMakeCache.txt and rerun cmake.On Debian/Ubuntu, package name is libncurses5-dev, on Redhat and derivates it is ncurses-devel.
Call Stack (most recent call first):
  cmake/readline.cmake:128 (FIND_CURSES)
  cmake/readline.cmake:202 (MYSQL_USE_BUNDLED_EDITLINE)
  CMakeLists.txt:410 (MYSQL_CHECK_EDITLINE)


-- Configuring incomplete, errors occurred!
See also "/usr/src/mysql-5.6.16/CMakeFiles/CMakeOutput.log".
See also "/usr/src/mysql-5.6.16/CMakeFiles/CMakeError.log".
```

以上的运行结果报了一个错误, 要先安装一个依赖包Curses然后在移除掉CMakeCache.txt文件在重新运行编译, 解决方法如下

```shell
[root@zhangyz mysql-5.6.16]# yum -y install ncurses-devel
[root@zhangyz mysql-5.6.16]# rm -rf CMakeCache.txt 
[root@zhangyz mysql-5.6.16]# /usr/local/cmake/bin/cmake . -DCMAKE_INSTALL_PREFIX=/usr/local/mysql -DINSTALL_MYSQLDATADIR=/data/db/ -DMYSQL_DATADIR=/data/db/ -DSYSCONFDIR=/usr/local/mysql/etc -DWITH_INNOBASE_STORAGE_ENGINE=1 -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci -DMYSQL_TCP_PORT=5535 -DMYSQL_UNIX_ADDR=/usr/local/mysql/tmp/mysql.sock -DWITH_EXTRA_CHARSETS=all
-- Looking for asprintf - found
-- Check size of pthread_t
-- Check size of pthread_t - done
-- Performing Test HAVE_PEERCRED
-- Performing Test HAVE_PEERCRED - Success
-- Library mysqlclient depends on OSLIBS -lpthread;m;dl
-- Googlemock was not found. gtest-based unit tests will be disabled. You can run cmake . -DENABLE_DOWNLOADS=1 to automatically download and build required components from source.
-- If you are inside a firewall, you may need to use an http proxy: export http_proxy=http://example.com:80
Warning: Bison executable not found in PATH
-- Library mysqlserver depends on OSLIBS -lpthread;m;crypt;dl
-- Configuring done
-- Generating done
-- Build files have been written to: /usr/src/mysql-5.6.16
[root@zhangyz mysql-5.6.16]# make
[root@zhangyz mysql-5.6.16]# make install 
```

安装完成之后进入mysql源码安装目录
```shell
[root@zhangyz mysql-5.6.16]# cd /usr/local/mysql
[root@zhangyz mysql]# mkdir tmp etc var log
[root@zhangyz mysql]# cp scripts/mysql_install_db ./bin 
```

创建一个mysql用户, 如果已经存在就不需要创建
```shell
[root@zhangyz mysql]# useradd -M -s /sbin/nologin mysql
```

修改权限
```shell
[root@zhangyz mysql]# chown root:mysql /usr/local/mysql/ -R
[root@zhangyz mysql]# chown mysql:mysql /data/db/ -R   
```

初始化mysql数据库
```shell
//如果要指定配置文件的位置，使用下面参数 --defaults-file=/usr/local/mysql/etc/my.cnf
[root@zhangyz mysql]# /usr/local/mysql/bin/mysql_install_db --basedir=/usr/local/mysql/ --datadir=/data/db --user=mysql
```

启动mysql
```shell
[root@zhangyz mysql]# /usr/local/mysql/bin/mysqld_safe --user=mysql &
```

打开mysql数据库
```shell
[root@zhangyz ~]# /usr/local/mysql/bin/mysql
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 26
Server version: 5.6.12 Source distribution

Copyright (c) 2000, 2014, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```

启动成功了, 接下来为mysql数据库设定一个密码
```shell
[root@zhangyz ~]# /usr/local/mysql/bin/mysqladmin -u root password redhat
[root@zhangyz ~]# /usr/local/mysql/bin/mysql -uroot -p'redhat'
Warning: Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 28
Server version: 5.6.16 Source distribution

Copyright (c) 2000, 2014, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```

查看mysql数据库的端口
```shell
[root@zhangyz ~]# netstat -tunlp | grep mysql 
tcp        0      0 :::5635                     :::*                        LISTEN      24815/mysqld    
```



#### MySQL目录结构

```shell
/usr/local/mysql5.5  —— 软件的安装目录
bin：存放的是服务器和客户端的程序(命令)
docs：文档           
lib：存放库文件         
README：简介  
sql-bench：benchmarks性能测试
COPYING：跟版权相关的
include：存放的头文件
man：man手册
scripts：脚本目录
support-files：模板文件
data：存放数据的目录，我们指定了/data/mysql，那么这个目录就不再使用了
INSTALL-BINARY ：mysql的安装文档
mysql-test：mysql测试相关的
share：共享路径及其他
/data/mysql  —— 数据存放路径
[root@s200 mysql]# ls
ibdata1  ：系统自己命名的数据文件    
mysql-bin.00000X ：二进制日志文件、主要用于备份恢复
mysql-bin.index：二进制日志索引文件                 
ib_logfile0和ib_logfile1：系统自己命名的日志文件         
s200.uplooking.com.err：错误日志文件
s200.uplooking.com.pid：pid文件
mysql ：以下三个都是数据库，mysql是必须存在的       
test
performance_schema
```


| 数据库引擎名字和表结构文件 | 描述 |
|------------------------|------|
| MyISAM |          |
| .frm   | 表结构    |
| .MYD   | 表数据    |
| .MYI   | 表索引    |

| 数据库引擎名字和表结构文件 | 描述 |
|------------------------|------|
| InnoDB | 所有表共享一个表空间文件 |
| .frm | 表结构 |
| .ibd | 表空间 (表数据和表索引) |

查看mysql服务器当前使用的是什么数据库引擎

```sql
mysql> show engines;
+--------------------+---------+----------------------------------------------------------------+--------------+------+------------+
| Engine             | Support | Comment                                                        | Transactions | XA   | Savepoints |
+--------------------+---------+----------------------------------------------------------------+--------------+------+------------+
| PERFORMANCE_SCHEMA | YES     | Performance Schema                                             | NO           | NO   | NO         |
| MRG_MYISAM         | YES     | Collection of identical MyISAM tables                          | NO           | NO   | NO         |
| MEMORY             | YES     | Hash based, stored in memory, useful for temporary tables      | NO           | NO   | NO         |
| BLACKHOLE          | YES     | /dev/null storage engine (anything you write to it disappears) | NO           | NO   | NO         |
| CSV                | YES     | CSV storage engine                                             | NO           | NO   | NO         |
| MyISAM             | YES     | MyISAM storage engine                                          | NO           | NO   | NO         |
| ARCHIVE            | YES     | Archive storage engine                                         | NO           | NO   | NO         |
| FEDERATED          | NO      | Federated MySQL storage engine                                 | NULL         | NULL | NULL       |
| InnoDB             | DEFAULT | Supports transactions, row-level locking, and foreign keys     | YES          | YES  | YES        |
+--------------------+---------+----------------------------------------------------------------+--------------+------+------------+
```

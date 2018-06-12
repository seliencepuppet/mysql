## MySQL

<br>

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

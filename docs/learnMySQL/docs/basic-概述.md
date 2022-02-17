# 数据库相关概念

| 名称      | 全称                               | 简称                                 |
| ------- | -------------------------------- | ---------------------------------- |
| 数据库     | 存储数据的仓库，数据是有组织的进行存储              | DataBase(DB)                       |
| 数据库管理系统 | 操纵和管理数据库的大型软件                    | Data Base Management System (DBMS) |
| SQL     | 操作关系型数据库的编程语言，定义了一套操作关系型数据库的统一标准 | Structured Query Language (SQL)    |

## 主流的关系型数据库管理系统

- Oracle

- MySQL

- Microsoft SQL Server

- PostgreSQL

- IBM DB2

- Microsoft Access

- SQLite

- MariaDB

- Microsoft Azure SQL Database

- Hive

## 小结

1. 数据库：数据存储的仓库

2. 数据库管理系统：操纵和管理数据库的大型软件

3. SQL：操作关系型数据库的编程语言，是一套标准

# MySQL安装与启动

[MySQL官网](https://www.mysql.com/)

[社区版下载页面]([MySQL :: MySQL Community Downloads](https://dev.mysql.com/downloads/))

[官方安装教程]([MySQL :: MySQL 8.0 Reference Manual :: 2 Installing and Upgrading MySQL](https://dev.mysql.com/doc/refman/8.0/en/installing.html))

## centos-stream8干净环境安装

1. 添加MySQL Yum 仓库
   
   从官网下载社区版安装包
   
   ```bash
   wget https://dev.mysql.com/get/mysql80-community-release-el8-3.noarch.rpm
   ```
   
   安装MySQL的rpm包
   
   ```bash
   $> sudo yum install mysql80-community-release-el8-{version-number}.noarch.rpm
   ```
   
   `/etc/yum.repos.d/{mysql-community.repo，mysql-community-source.repo}`
   上述安装操作的意义是：将MySQL的Yum仓库列表加入到系统的仓库列表中，并且下载GPGKEY来检查软件包的完整性
   
   可以使用下列命令检查MySQL Yum仓库是否被成功安装
   
   ```bash
   $> yum repolist enabled | grep "mysql.*-community.*"
   ```

2. 选择MySQL发行版本
   
   当使用MySQL Yum仓库时，默认安装MySQL8.0
   
   在Yum的不同子仓库中有不同系列版本的社区服务器
   
   并且其余版本默认禁用
   
   可以使用下列命令查看MySQL Yum仓库中所有的子版本
   
   ```bash
   $> yum repolist all | grep mysql
   ```
   
   如果要从最新的GA系列安装最新版本，则不需要额外配置，可以跳过此步骤
   
   如果需要选取其他版本，应当禁用当前默认子仓库，并且启用相应版本的子仓库
   
   ```bash
   $> sudo dnf config-manager --disable mysql57-community
   $> sudo dnf config-manager --enable mysql80-community
   ```
   
   除了使用上述命令外，还可以直接编辑`/etc/yum.repos.d/mysql-community.repo`配置文件
   
   找到相应条目，更改`enabled`选项即可
   
   ```vim
   [mysql57-community]
   name=MySQL 5.7 Community Server
   baseurl=http://repo.mysql.com/yum/mysql-5.7-community/el/6/$basearch/
   enabled=1
   gpgcheck=1
   gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql-2022
          file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
   ```
   
   使用下述命令检查启用禁用情况
   
   ```bash
   $> yum repolist enabled | grep mysql
   ```

3. 禁用EL8系统的默认MySQL模块
   
   基于EL8的系统包含默认启用的MySQL模块，除非禁用此模块，否则它会屏蔽MySQL仓库提供的包，要禁用默认模块并使得仓库包可见，可以使用下列命令禁用并检查
   
   ```bash
   $> sudo yum module disable mysql
   $> dnf module list |grep mysql
   ```

4. 安装MySQL
   
   使用下列命令安装MySQL服务端
   
   ```bash
   $> sudo yum install mysql-community-server
   ```

5. 启动MySQL服务端
   
      使用`systemctl`管理MySQL服务端即可
   
   ```bash
   $> systemctl start mysqld
   $> systemctl status mysqld
   ```
   
      使用docker运行centos镜像时如需启用`systemctl`可以使用`-d --privileged  /usr/sbin/init`参数启用`systemctl`功能
   
   ```bash
   docker run -d --privileged IMG /usr/sbin/init
   ```
   
      `/usr/sbin/init`：初始容器里的CENTOS，用于启动`dbus-daemon`。

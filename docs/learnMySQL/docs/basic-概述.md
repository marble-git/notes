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
   
   ```

2. 选择MySQL发行版本

3. 禁用EL8系统的默认MySQL模块

4. 安装MySQL

5. 启动MySQL服务端

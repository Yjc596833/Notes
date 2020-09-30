<!--
 * @Author: your name
 * @Date: 2020-09-30 16:52:54
 * @LastEditTime: 2020-09-30 17:12:49
 * @LastEditors: your name
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Mysql\MySQL Command Line 常用命令.md
-->
连接：mysql [-h127.0.0.1] [-P3306] -uroot -p    (端口要用大写P，与密码p加以区分）

查看mysql的数据库列表：show databases;

使用某个库：use [数据库名];

查看表列表：show tables;

查看数据库的创建sql：show create database [数据库名称];

查看表的创建sql：show create table [表名];

查看数据的字符集相关信息: show variables like '%char%';

查看当前登录的用户：select user(); 或 select current_user();

查看数据库系统配置的用户列表：SELECT * FROM mysql.user; （其中权限相关的信息也在这个表中，用户超期也在这个表中）

创建用户编辑用户、创建数据库建议用MySqlWorkBench工具，强大可视，避免错误。

创建用户：CREATE USER 'test'@'localhost' IDENTIFIED BY '123456';

root账户修改用户的密码的方式：udpate mysql.user set authentication_string=password('[你的密码]') where user='[需要修改的用户名]'；

有的老版本的mysql保存密码的字段为'password',修改密码是需要根据不同的字段名来调整sql是用authentication_string还是用password。

为用户授权：GRANT ALL PRIVILEGES ON db.* TO 'test'@'localhost';

修改用户信息后刷新用户权限：flush privileges;

创建数据库： create database [数据库名称] default character set utf8 collate utf8_general_ci;

查看用户的授权语句：show grants for [用户名];

移除某个授权：revoke [drop | 权限] on [数据库名称].* from [用户名称];

 删除某个数据库实例：DROP DATABASE [数据库名称];

查询一个用户有几个schemas（数据库实例）的访问权限：show grants for [用户名];  (会将赋权给用户访问的数据列出来）

查看mysql的权限关键字列表：show privilege;

查看某个schema（数据库实例）有哪些用户可以访问：select host,db,user from mysql.db;
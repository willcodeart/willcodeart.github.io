---
title: linux安装mysql
description: linux安装mysql
categories:
tags:
---



##### root用户登入Linux，使用yum 命令安装MySQL

```
sudo yum install mysql
sudo yum install mysql-server
sudo yum install mysql-devel
```

安装过程中，可能出现找不到mysql-server包，需做如下调整；

1.安装从网上下载文件的wget命令

```
[root@master ~]# yum -y install wget
```


2.下载mysql的repo源

```
[root@master ~]# wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm 
```

3.安装mysql-community-release-el7-5.noarch.rpm包

```
[root@master ~]# rpm -ivh mysql-community-release-el7-5.noarch.rpm
```


4.查看下

```
[root@master ~]# ls -1 /etc/yum.repos.d/mysql-community*
/etc/yum.repos.d/mysql-community.repo
/etc/yum.repos.d/mysql-community-source.repo
会获得两个mysql的yum repo源：/etc/yum.repos.d/mysql-community.repo，/etc/yum.repos.d/mysql-community-source.repo。
```

5.安装mysql

```
[root@master ~]# yum install mysql-server
```

##### 将/var/lib/mysql的用户群改成mysql，并赋予属主和属组权限

```
sudo chgrp -R mysql /var/lib/mysql
chmod -R 770 /var/lib/mysql
```

##### 启动mysql服务，设置登录mysql的用户、密码

```
sudo service mysqld start
/usr/bin/mysqladmin -u root password '你的密码'
mysqladmin -u root password 123456
```

##### 连接mysql

格式： mysql -h主机地址 -u用户名 -p用户密码
连接本机mysql，进入目录mysql\bin，再键入命令mysql -uroot -p， 回车后提示输入密码。
连接到远程主机上的MYSQL。假设远程主机的IP为：110.110.110.110，用户名为root,密码为abcd123。则键入以下命令：

```
mysql -h110.110.110.110 -uroot -pabcd123
```

##### 设置字符集

```
SHOW VARIABLES LIKE 'character_set_%';
set character_set_server=utf8;	
set character_set_database=utf8;
```

##### AWS服务器访问设置

1.如果使用aws服务器，进入aws控制台，找到运行实例的安全组，编辑入站安全组，添加规则。选择规则MYSQL/Aurora，端口设置为3306，保存。

2.登录数据库，执行以下代码
GRANT ALL PRIVILEGES ON *.* TO 'username'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
FLUSH PRIVILEGES;

第一行代码作用为创建用户username，设置密码为password，并且允许来自所有域名的访问，第二行代码为更新权限。
如果更改已有的用户允许远程访问可以修改mysql数据库下user表，将默认字段Host内容‘localhost’更改为‘%’。

```
GRANT ALL PRIVILEGES ON *.* TO 'hello'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
```

​	
# mysql-learning
### 第一章：MySQL介绍
* 操作系统中数据存放的载体：
  * Windows, Linux和MacOS都是基于文件(eg: AVI, DOC, JPG, TXT)的操作系统
* 什么是数据库系统Database Management System？
  * 数据库系统(DBMS)是指一个能为用户提供信息服务的系统。它实现了有组织地，动态地存储大量相关数据的功能，提供了数据处理和信息资源共享的便利手段。
* 什么是关系型数据库系统Relational Database Management System？
  * 关系型数据库系统(RDBMS)是指使用了关系模型的数据库系统
  * 关系模型中，数据是分类存放的，数据之间可以有联系
  * 关系型数据库是多线程的，例如秒杀系统，有100库存，使用关系型数据库很容易超卖，就因为是你多线程的，不好控制
* 什么是NoSQL数据库系统？
  * NoSQL数据库指的是数据分类存放，但是数据之间没有关联关系的数据库系统
  * Redis是一种常见的NoSQL数据库， 是单线程的
  * 常见的主流NoSQL数据库：Redis（使用内存保存数据的），MemCache（使用内存保存数据的）， MOngoDB（使用硬盘保存数据的，保存海量低价值的数据是很有价值的， eg：新闻， 消息， 朋友圈，回帖等）， Neo4J（使用硬盘保存数据的，适用于保存复杂的组织关系和人际关系）
  * NoSQL数据库的应用场景 eg： 秒杀库存， 登录信息， 消息通知， 新闻
* MySQL数据库
  * MySQL是应用最广泛，普及度最高的开源关系型数据库
  * mysql -uroot -p
  * show databases;
  * CREATE DATABASE name;
  * 增删改查 -> Insert, Delete, Update, Select
  * net stop mysql80
  * net start mysql80
  * MySQL默认端口号3306, 80端口是HTTP常用端口
* 重设root密码
  * 创建一个TXT文件，定义修改密码的SQL语句
  * ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
* MySQL配置文件
  * 注意区分mac版mysql与Windows版的mysql配置文件扩展名不同:
  * mac下: my.cnf
  * windows下: my.ini
  * 在my.ini文件中，我们可以设置各种MySQL的配置，例如字符集，端口号，目录地址等等
* 本章总结：
  * 掌握了windows平台上MySQL数据库的安装与管理，明白逻辑库，数据表与数据目录的对应关系
  * 懂得MySQL数据库的常用参数设置：端口号，字符集， IP绑定，连接数等等
  * 掌握MySQL数据库的用户管理，能创建用户并分配权限，设置远程登陆（%）
  * 对于MySQL数据库上的忘记密码的账户，能重置该账户的密码信息
  


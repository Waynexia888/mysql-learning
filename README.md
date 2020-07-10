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

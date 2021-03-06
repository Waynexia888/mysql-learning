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
### 第2章：数据库表的相关操作(DDL)
* 学习目标
  * 管理逻辑库和数据表 -> 创建，删除，修改逻辑库和数据表
  * 了解常用的数据类型和约束 -> 字符串，整数，浮点数，精确数字，日期，枚举。主键约束，非空约束，唯一约束，外键约束等
  * 掌握索引运行机制和使用原则 -> 排序为什么可以提高数据检索速度？ 怎么创建和删除索引？ 什么条件下使用索引？
* 什么是SQL语言？
  * SQL是用于访问和处理数据的标准的计算机语言
* SQL语言分类、
  * DML -> Data Manipulation Language:  添加，删除，修改， 查询
  * DCL -> Data Control Language: 用户，权限，事务
  * DDL -> Data Definition Language: 逻辑库， 数据表， 视图， 索引
* SQL语句注意事项
  * SQL语句不区分大小写， 但是字符串区分大小写
  * SELECT "HelloWorld";
  * SQL语句必须以分号结尾
  * SQL语句中的空白和换行没有限制，但是不能破坏语法
* SQL语句的注释
  * SQL语句的注释有两种，分别如下：
  * #这是一段注释文字
  * /* 这是另一段注释文字 */
* 创建逻辑库(属于DDL分类语句)
  * CREATE DATABASE name;   name -> 逻辑库名称
  * SHOW DATABASES;
  * DROP DATABASE name;
* 创建数据表
  * ![创建数据表](images/创建数据表.png)<br/>
* ![create table](images/create-table.png)<br/>
  * INT UNSIGNED 无符号的整数（即非负数）
  * PRIMARY KEY 主键
  * VARCHAR(20)  字符串，最大不能超过20个字符
  * NOT NULL 非空
  * DATE 日期
  * CHAR(1) 固定长度的字符，长度为1
  * 一个数据库中有很多逻辑空间，如果想在某个逻辑空间里添加表table，首先要USE test(使用test这个逻辑空间），然后CREATE TABLE 数据表(...)
  * INSERT INTO student VALUE(1, "李强", "男", "1995-05-15", "13312345678", NULL);  -> 插入一条数据
* ![table data](images/table-data.png)<br/>
* 数据表的其他操作
  * ![数据表的其他操作](images/数据表的其他操作.png)<br/>
  * DESC student -> 查看student这个表的结构详情信息
  * SHOW CREATE TABLE student -> 查看student这个表当初创建时候的sql语句
  * DROP TABLE student -> student这个数据表不想要了（注意这条语句的意思不是删除这个表的数据）
* 数据类型-数字
  * ![数据类型-数字](images/数据类型-数字.png)<br/>
  * FLOAT, DOUBLE有精度丢失的问题， 因此保存重要精准数据的时候（例如钱），使用DECIMAL类型
* 数据类型-字符串
  * ![数据类型-字符串](images/数据类型-字符串.png)<br/>
* 数据类型-日期
  * ![数据类型-日期](images/数据类型-日期.png)<br/>
* 修改表结构-添加字段
  * ![修改表结构-添加字段](images/修改表结构-添加字段.png)<br/>
  * ![修改表结构-添加字段1](images/修改表结构-添加字段1.png)<br/>
* 修改表结构-修改字段类型，约束，或者注释
  * ![修改字段类型，约束，或者注释](images/修改字段类型，约束，或者注释.png)<br/>
  * ![修改字段类型和约束1](images/修改字段类型和约束1.png)<br/>
* 修改表结构-修改字段名称
  * ![修改字段名称](images/修改字段名称.png)<br/>
  * ![修改字段名称1](images/修改字段名称1.png)<br/>
* 修改表结构-删除字段
  * ![删除字段](images/删除字段.png)<br/>
  * ![删除字段1](images/删除字段1.png)<br/>
* 数据库的范式
  * 构造数据库必须遵循一定的规则，这种规则就是范式
  * 目前关系数据库有6种范式，一般情况下，只满足第三范式即可
  * 第一范式：原子性
  * ![第一范式-原子性](images/第一范式-原子性.png)<br/>
  * 第二范式：唯一性（eg：流水号那一列可以看作是primary key主键列）
  * ![第二范式-唯一性](images/第二范式-唯一性.png)<br/>
  * 第三范式：关联性
  * ![第三范式-关联性1](images/第三范式-关联性1.png)<br/>
* 数据定义语言：字段约束
  * MySQL中的字段约束共有4种：
  * ![字段约束](images/字段约束.png)<br/>
* 主键约束
  * 主键约束要求字段的值在全表必须唯一，而且不能为NULL值
  * 建议主键一定要使用数字类型，因为数字的检索速度会非常快
  * ![主键约束](images/主键约束.png)<br/>
* 非空约束
  * ![非空约束](images/非空约束.png)<br/>
* 唯一约束
  * ![唯一约束](images/唯一约束.png)<br/>
* 练习
  * ![练习1](images/练习1.png)<br/>
  * ![练习2](images/练习2.png)<br/>
  * 注意： married BOOLEAN NOT NULL DEFAULT FALSE
  * 由于数据类型没有BOOLEAN，因此BOOLEAN 会自动转换成tinyint类型，DEFAULT FALSE代表0， TRUE代表1
* 外键约束
  * ![外键约束](images/外键约束.png)<br/>
  * 外键约束的定义是写在子表上的
  * ![外键约束-父表](images/外键约束-父表.png)<br/>
  * ![外键约束-子表](images/外键约束-子表.png)<br/>
* 外键约束的闭环问题
  * ![外键约束的闭环问题](images/外键约束的闭环问题.png)<br/>
  * `因此在创建数据表的时候，一般都是放弃创建外键约束的，因为要避免形成环状，形成循环依赖`
* 数据定义语言：索引 - 提升数据检索速度
  * 数据排序的好处 -> 一旦数据排序之后，查找的速度就会翻倍，现实世界跟程序世界都是如此
  * 如何创建索引？ -> 只要设置好索引，后台会对`字段`进行排序，生成二叉树
  * ![创建索引](images/创建索引.png)<br/>
  * ![创建索引1](images/创建索引1.png)<br/>
  * ![创建索引2](images/创建索引2.png)<br/>
  * 如何添加与删除索引
  * ![添加与删除索引](images/添加与删除索引.png)<br/>
  * ![添加与删除索引1](images/添加与删除索引1.png)<br/>
  * ![添加与删除索引2](images/添加与删除索引2.png)<br/>
  * 注意：primary key主键自带索引功能，自动对id进行索引
* 索引的使用原则
  * 数据量很大，而且经常被查询的数据表可以设置索引
  * （eg：日志表，记录了user日常）因为`不经常被查询`，不适合索引；`经常增删改的表`也不适合索引; `表记录太少（即写入太少）`也不适合索引
  * 索引只添加在经常被用作检索条件的字段上面
  * 不要在大字段上（很长的字段上）创建索引
  * 读取多于写入，例如淘宝app，大家都是看得多买的少，一定要货比三家后才会下订单，所以在淘宝系统上，查询远远超过写入，因此说让淘宝用户最快检索的商品是非常重要的，这就要使用索引
* 本章总结：
  * 掌握了逻辑库和数据表的管理
  * 了解MySQL常用数据类型
  * 掌握MySQL的字段约束
  * 掌握索引机制，懂得什么时候使用索引
### 第三章：数据库的基本查询(DML)
* 学习目标
  * 数据的简单查询（无条件查询记录，字段的计算和字段的别名）
  * 数据的高级查询（数据排序，分页，去除重复记录）
  * 数据的有条件查询（条件表达式：数学运算符，比较运算符，逻辑运算符，按位运算符）
* 数据操作语言：普通查询
  * 记录查询
  * ![记录查询](images/记录查询.png)<br/>
  * 使用列别名
  * ![使用列别名](images/使用列别名.png)<br/>
  * 查询语句的子句执行顺序：先执行FROM（选择数据来源），再执行SELECT（选择输出内容）
* 数据操作语言：数据分页
  * 数据分页
  * ![数据分页](images/数据分页.png)<br/>
  * 数据分页的简写用法
  * ![数据分页的简写用法](images/数据分页的简写用法.png)<br/>
* 数据操作语言：结果集排序
  * 结果集排序
  * ![结果集排序](images/结果集排序.png)<br/>
  * 排序关键字
  * ![排序关键字](images/排序关键字.png)<br/>
  * 排序字段内容相同的情况
  * ![排序字段内容相同的情况](images/排序字段内容相同的情况.png)<br/>
  * 多个排序字段
  * ![多个排序字段](images/多个排序字段.png)<br/>
  * 排序 + 分页
  * ![排序 + 分页](images/排序和分页.png)<br/>
* 数据操作语言：去除重复记录
  * 结果集中的重复记录
  * ![结果集中的重复记录](images/结果集中的重复记录.png)<br/>
  * 去除重复记录
  * ![去除重复记录](images/去除重复记录.png)<br/>
  * 去重注意事项
  * ![去重注意事项](images/去重注意事项.png)<br/>
* 数据操作语言：条件查询(一)
  * 条件查询
  * ![条件查询](images/条件查询.png)<br/>
  * 四类运算符
  * ![四类运算符](images/四类运算符.png)<br/>
  * 算数运算符
  * ![算数运算符](images/算数运算符.png)<br/>
  * ![算数运算符1](images/算数运算符1.png)<br/>
  * 比较运算符
  * ![比较运算符](images/比较运算符.png)<br/>
  * ![比较运算符1](images/比较运算符1.png)<br/>
  * ![比较运算符2](images/比较运算符2.png)<br/>
* 数据操作语言：条件查询(二)
  * 逻辑运算符
  * ![逻辑运算符](images/逻辑运算符.png)<br/>
  * ![逻辑运算符1](images/逻辑运算符1.png)<br/>
  * 按位运算符
  * ![按位运算符](images/按位运算符.png)<br/>
  * Where子句的注意事项
  * ![Where子句的注意事项](images/Where子句的注意事项.png)<br/>
  * 各种子句的执行顺序
  * ![各种子句的执行顺序](images/各种子句的执行顺序.png)<br/>
### 第四章：数据库的高级查询(DML)
* 学习目标
  * 数据统计分析（聚合函数，分组查询，HAVING子句）
  * 多表连接查询（内连接，外连接，以及多表查询的多种语法）
  * 子查询（单行子查询，多行子查询，WHERE子查询，FROM子查询，SELECT子查询）
* 聚合函数
  * ![聚合函数](images/聚合函数.png)<br/>
  * SUM函数
  * ![SUM函数](images/SUM函数.png)<br/>
  * MAX函数
  * ![MAX函数](images/MAX函数.png)<br/>
  * MIN函数
  * ![MIN函数](images/MIN函数.png)<br/>
  * AVG函数
  * ![AVG函数](images/AVG函数.png)<br/>
  * COUNT函数
  * ![COUNT函数](images/COUNT函数.png)<br/>
  * ![COUNT函数1](images/COUNT函数1.png)<br/>
* 分组查询
  * 为什么要分组？
  * ![为什么要分组](images/为什么要分组.png)<br/>
  * 逐级分组
  * ![逐级分组](images/逐级分组.png)<br/>
  * 对SELECT子句的要求
  * ![对SELECT子句的要求](images/对SELECT子句的要求.png)<br/>
  * 对分组结果集再次做汇总计算
  * ![对分组结果集再次做汇总计算](images/对分组结果集再次做汇总计算.png)<br/>
  * GROUP_CONCAT函数
  * ![GROUP_CONCAT函数](images/GROUP_CONCAT函数.png)<br/>
  * ![GROUP_CONCAT函数1](images/GROUP_CONCAT函数1.png)<br/>
  * 各种子句的执行顺序
  * ![各种子句的执行顺序1](images/各种子句的执行顺序1.png)<br/>
* HAVING子句
  * ![HAVING子句](images/HAVING子句.png)<br/>
  * ![HAVING子句1](images/HAVING子句1.png)<br/>
  * ![HAVING子句2](images/HAVING子句2.png)<br/>
  * ![HAVING子句3](images/HAVING子句3.png)<br/>

<img src="/assets/mysql.png" width="300" hegiht="100" align=center />


## 前言

MYSQL是最流行的关系型数据库管理系统。

## 目录

* [基本入门](#base)
  * [连接MYSQL](#connect)
  * [数据库操作](#operationDatabase)
    * [查看](#showDataBase)
    * [选择](#selectDataBase)
    * [创建](#createDataBase)
    * [删除](#dropDataBase)
  * [mysql数据类型](#datatype)
  * [数据表操作](#operationTables)
    * [创建数据表](#createTable)
    * [删除数据表](#dropTable)
  * [数据操作](#operationData)
    * [插入数据](#insertData)
    * [查询数据](#selectData)
    * [更新数据](#updateData)
    * [删除数据](#deleteData)
    * [like查询](#likeData)
    * [union](#union)
    * [order by](#orderBy)

<hr/> 
<a name="base"></a>
## 基本入门

<a name="connect"></a>
#### 连接MYSQL

我们先连接mysql服务器：

```json
mysql -u root -p
Enter password: *****
```

<a name="operationDatabase"></a>
#### 数据库操作

<a name="showDataBase"></a>
* 查看数据库

```json
mysql> show databases;

+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| test               |
+--------------------+
4 rows in set (0.00 sec)
```

<a name="selectDataBase"></a>
* 选择数据库

```json
mysql> use mysql;

Database changed
```

<a name="createDataBase"></a>
* 创建数据库

```json
mysql> create database test;

Query OK, 1 row affected (0.00 sec)
```

<a name="dropDataBase"></a>
* 删除数据库

```json
mysql> drop database test;

Query OK, 0 rows affected (0.00 sec)
```

<a name="datatype"></a>
#### MYSQL 数据类型

MySql支持多种类型，大致可以分为三类： 数值、日期/时间和字符串类型。

<a name="operationTables"></a>
#### 数据表操作

<a name="createTable"></a>
* 创建数据表

```json
mysql> CREATE TABLE IF NOT EXISTS `runoob_tbl`(
   `runoob_id` INT UNSIGNED AUTO_INCREMENT,
   `runoob_title` VARCHAR(100) NOT NULL,
   `runoob_author` VARCHAR(40) NOT NULL,
   `submission_date` DATE,
   PRIMARY KEY ( `runoob_id` )
)ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

<a name="dropTable"></a>
* 删除数据表

```json
mysql> DROP TABLE runoob_tbl;
```

<a name="operationData"></a>
#### 数据操作

<a name="insertData"></a>
* 插入数据

```json
insert into arms (name, img_src, type_id, descript, remarks) values ('碎 片手雷', 'www', 8, '手雷手雷', '哈哈，炸死你');

Query OK, 1 row affected (0.00 sec)
```

<a name="selectData"></a>
* 查询数据

```json
select * from arms where id = 1;
```

<a name="updateData"></a>
* 更新数据

```json
update arms set name = '手雷1' where id = 30;
```

<a name="deleteData"></a>
* 删除数据

```json
delete from arms where id = 30;
```

<a name="likeData"></a>
* like查询
  * `%a`  // 以A结尾的数据
  * `a%`  // 以a开始的数据
  * `%a%` // 包含a的数据
  * `_a_` // 三位且中间字母是a的数据
  * `_a`  // 两位且结尾字母是a的数据
  * `a_`  // 两位且开头字母是a的数据

```json
select * from arms where img_src like '%5200%';
```

<a name="union"></a>
* union: 用于连接两个或者两个以上的数据表

```json
SELECT country FROM Websites
UNION
SELECT country FROM apps
ORDER BY country;
```

<a name="orderBy"></a>
* order by

```json
select * from arms order by id asc limit 0, 20;
```


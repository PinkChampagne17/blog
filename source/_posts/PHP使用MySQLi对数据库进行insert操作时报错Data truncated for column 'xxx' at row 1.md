---
title: PHP使用MySQLi对数据库进行insert操作时报错Data truncated for column 'xxx' at row 1
date: 2020-07-11 20:29:00
categories: 
- PHP
---

PHP在MySQLi使用SQL语句`INSET INTO student (sid, name, age, sex, uid) values (123, '123', '123', '男', 1)`对数据库进行操作时出现了"Data truncated for column 'xxx' at row 1"的错误信息。

## 问题原因与解决方法

这里以面向对象方法为例。

在数据库表创建时使用了`default charset=utf8`，但创建mysqli对象后没有使用`set_charset()`方法并填入参数`"utf-8"`，并且因为这条SQL语句中包含了中文字符，所以出现了报错。

```SQL
--数据库创建表时使用了default charset=utf8
CREATE TABLE user (
   id int auto_increment primary key,
   uname varchar(20) not null,
   pwd varchar(20) not null
)default charset=utf8;
```

```PHP
    $conn = new mysqli("localhost", "root", "", "student_management", 3306);

    // 在创建mysqli对象后设置charset为utf-8
    $conn->set_charset("utf8");
```

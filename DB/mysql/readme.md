## 数据库概述

### 1. 什么是数据库管理系统 
> 数据库管理系统（DataBase Management System，DBMS）：指一种操作和管理数据库的大型软件，用于建立、使用和维护数据库，对数据库进行统一管理和控制，以保证数据库的安全性和完整性。用户通过数据库管理系统访问数据库中表内的数据。
> 
常见的数据库管理系统 

- MYSQL：开源免费的数据库，小型的数据库.已经被Oracle收购了.MySQL6.x版本也开始收费。
- Oracle：收费的大型数据库，Oracle公司的产品。Oracle收购SUN公司，收购MYSQL。
- DB2：IBM公司的数据库产品,收费的。常应用在银行系统中
- SQLServer：MicroSoft 公司收费的中型的数据库。C#、.net等语言常使用
- SQLite: 嵌入式的小型数据库，应用在手机端

### 2. SQL语句

> 数据库是不认识JAVA语言的，但是我们同样要与数据库交互，这时需要使用到数据库认识的语言SQL语句，它是数据库的代码。 
结构化查询语言(Structured Query Language)简称SQL，是一种数据库查询和程序设计语言，用于存取数据以及查询、更新和管理关系数据库系统。 
创建数据库、创建数据表、向数据表中添加一条条数据信息均需要使用SQL语句

SQL分类
 
- 数据定义语言：简称DDL(Data Definition Language)，用来定义数据库对象：数据库，表，列等。关键字：create，alter，drop等
- 数据操作语言：简称DML(Data Manipulation Language)，用来对数据库中表的记录进行更新。关键字：insert，delete，update等
- 数据控制语言：简称DCL(Data Control Language)，用来定义数据库的访问权限和安全级别，及创建用户
- 数据查询语言：简称DQL(Data Query Language)，用来查询数据库中表的记录。关键字：select，from，where等

SQL通用语法

- SQL语句可以单行或多行书写，以分号结尾
- 可使用空格和缩进来增强语句的可读性
- MySQL数据库的SQL语句不区分大小写，建议使用大写，例如：SELECT * FROM user
- 同样可以使用/**/的方式完成注释
  
MySQL中常用的数据类型如下:

|类型|	描述|
|---- |----|
|int|	整型|
|double	|浮点型|
|varchar|字符串类型|
|date	|日期类型,格式为yyyy-MM-dd,只有年月日,没有时分秒|

详细的数据类型

> MySQL支持多种类型，大致可以分为三类：数值、日期/时间和字符串(字符)类型

`数值类型`

MySQL支持所有标准SQL数值数据类型。 
这些类型包括严格数值数据类型(INTEGER、SMALLINT、DECIMAL和NUMERIC)，以及近似数值数据类型(FLOAT、REAL和DOUBLE PRECISION)。 
关键字INT是INTEGER的同义词，关键字DEC是DECIMAL的同义词。 
BIT数据类型保存位字段值，并且支持MyISAM、MEMORY、InnoDB和BDB表。 
作为SQL标准的扩展，MySQL也支持整数类型TINYINT、MEDIUMINT和BIGINT。下面的表显示了需要的每个整数类型的存储和范围。

|类型	|大小	|范围（有符号）	|范围（无符号）|	用途|
|----|----|----|----|----|
|TINYINT	|1 字节	|(-128，127)	|(0，255)	|小整数值|
|SMALLINT	|2 字节	|(-32 768，32 767)|	(0，65 535)	|大整数值|
|MEDIUMINT	|3 字节	|(-8 388 608，8 388 607)|(0，16 777 215)|大整数值|
|INT或INTEGER	|4 字节	|(-2 147 483 648，2 147 483 647)|(0，4 294 967 295)	|大整数值|
|BIGINT	|8 字节	|(-9 233 372 036 854 775 808，9 223 372 036 854 775 807)	|(0，18 446 744 073 709 551 615)	|极大整数值|
|FLOAT|	4 字节	|(-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38)	|0，(1.175 494 351 E-38，3.402 823 466 E+38)	|单精度浮点数值|
|DOUBLE	|8 字节	|(-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308)	0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308)|	双精度浮点数值|
|DECIMAL|	对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2	|依赖于M和D的值	|依赖于M和D的值	|小数值|

`日期和时间类型`

表示时间值的日期和时间类型为DATETIME、DATE、TIMESTAMP、TIME和YEAR。 
每个时间类型有一个有效值范围和一个”零”值，当指定不合法的MySQL不能表示的值时使用”零”值。 
TIMESTAMP类型有专有的自动更新特性，将在后面描述。

|类型	|大小 (字节)	|范围	|格式|	用途|
|----|----|----|----|----|
|DATE	|3	|1000-01-01/9999-12-31|	YYYY-MM-DD	|日期值|
|TIME|	3	|‘-838:59:59’/’838:59:59’	|HH:MM:SS	|时间值或持续时间|
|YEAR	|1	|1901/2155	|YYYY|	年份值|
|DATETIME|	8	|1000-01-01 00:00:00/9999-12-31 23:59:59	|YYYY-MM-DD HH:MM:SS	|混合日期和时间值|
|TIMESTAMP	|4	|1970-01-01 00:00:00/2038结束时间是第 2147483647 秒，北京时间 2038-1-19 11:14:07，格林尼治时间 2038年1月19日 凌晨 03:14:07|YYYYMMDD HHMMSS	|混合日期和时间值，时间戳|

`字符串类型`

字符串类型指CHAR、VARCHAR、BINARY、VARBINARY、BLOB、TEXT、ENUM和SET。该节描述了这些类型如何工作以及如何在查询中使用这些类型。

|类型	|大小	|用途|
|----|----|----|
|CHAR|0-255字节	|定长字符串|
|VARCHAR|0-65535 字节	|变长字符串|
|TINYBLOB	|0-255字节|	不超过 255 个字符的二进制字符串|
|TINYTEXT	|0-255字节	|短文本字符串|
|BLOB|	0-65 535字节	|二进制形式的长文本数据|
|TEXT	|0-65 535字节|	长文本数据|
|MEDIUMBLOB	|0-16 777 215字节	|二进制形式的中等长度文本数据|
|MEDIUMTEXT	|0-16 777 215字节|	中等长度文本数据|
|LONGBLOB	|0-4 294 967 295字节|	二进制形式的极大文本数据|
|LONGTEXT	|0-4 294 967 295字节|	极大文本数据|

CHAR和VARCHAR类型类似，但它们保存和检索的方式不同。它们的最大长度和是否尾部空格被保留等方面也不同。在存储或检索过程中不进行大小写转换。 
BINARY和VARBINARY类类似于CHAR和VARCHAR，不同的是它们包含二进制字符串而不要非二进制字符串。也就是说，它们包含字节字符串而不是字符字符串。这说明它们没有字符集，并且排序和比较基于列值字节的数值值。 
BLOB是一个二进制大对象，可以容纳可变数量的数据。有4种BLOB类型：TINYBLOB、BLOB、MEDIUMBLOB和LONGBLOB。它们只是可容纳值的最大长度不同。 
有4种TEXT类型：TINYTEXT、TEXT、MEDIUMTEXT和LONGTEXT。这些对应4种BLOB类型，有相同的最大长度和存储需求。



### mysql数据库操作

#### 创建数据库
```
create database 数据库名;
create database if not exists 数据库名; -- 如果不存在则创建
```

#### 查看数据库
查看MySQL服务器中的所有数据库:
```
show databases;
```

查看某个数据库的定义信息
```
show create database 数据库名;
```
删除数据库
```
drop database 数据库名称;
```
切换数据库
```
use 数据库名;
```
#### 表结构相关语句

##### 创建表
格式:
```
create table 表名(
   字段名 类型(长度) 约束,
   字段名 类型(长度) 约束
);
```
例如:
```
CREATE TABLE sort (
  sid INT, #分类ID 
  sname VARCHAR(100) #分类名称
);
CREATE TABLE sort (
  sid INT, #分类ID 
  sname VARCHAR(100) #分类名称
)CHARSET=utf8;
```
> 主键约束 
主键是用于标识当前记录的字段。它的特点是非空，唯一。在开发中一般情况下主键是 不具备任何含义，只是用于标识当前记录

格式: 
1. 在创建表时创建主键,在字段后面加上 primary key
```
CREATE TABLE 表名(
    id int primary key,
    ....
);
```
2. 在创建表时创建主键,在表创建的最后来指定主键
```
CREATE TABLE 表名(
    id int,
    ....,
    primary key(id)
);
```
删除主键:
```
alter table 表名 drop primary key;
```
主键自增长(只适用于MySQL)

> 一般主键是自增长的字段,不需要指定,实现添加自增长语句,主键字段后加auto_increment,例如:
```
CREATE TABLE sort (
  sid INT PRIMARY KEY auto_increment, #分类ID 
  sname VARCHAR(100) #分类名称
);
```
##### 查看表
查看数据库中所有的表
```
show tables;
```
查看表结构
```
desc 表名;
```
查看建表语句
```
show create table 表名;
```
删除表
格式:
```
drop table 表名;
```
修改表结构

删除列:
```
alter TABLE 表名 DROP 列名;
```
修改表名:
```
RENAME TABLE 表名 TO 新表名;
```
修改表的字符集
```
alter TABLE 表名 CHARACTER SET 字符集
```
修改列名
```
alter TABLE 表名 CHANGE 列名 新列名 列类型;
```
添加列
```
alter table 表名 add 列名 列类型;
```
### DML操作

首先先知道查询表中所有数据的语句:
```
SELECT * FROM 表名;
```
> DML是对表中的数据进行增、删、改的操作。不要与DDL混淆了,包含:
INSERT: 插入
UPDATE: 更新
DELETE: 删除

> 小知识:
在mysql中,字符串类型和日期类型都要用单引号括起来: ‘tom’ ‘2015-09-04’ 
空值：null


3.2.1 插入操作: INSERT:

语法:
```
INSERT INTO 表名（列名1，列名2 ...）VALUES(列值1，列值2...);
```
注意:

列名与与列值的类型、个数、顺序要一一对应
可以把列名当做java中的形参，把列值当做实参
值不要超出列定义的长度
如果插入空值，请使用null
插入的日期和字符一样，都使用引号括起来

3.2.2 修改操作: UPDATE

语法:
```
UPDATE 表名 SET 列名1=列值1，列名2=列值2... WHERE 列名=值
```

删除操作

语法
```
DELETE FROM 表名 [WHERE 列名=值]
```

### DQL 操作

DQL数据查询语言 （重要） 
数据库执行DQL语句不会对数据进行改变，而是让数据库发送结果集给客户端。 
查询返回的结果集是一张 虚拟表。

语法
```
 SELECT 列名 FROM表名 
[WHERE -> GROUP BY -> HAVING -> ORDER BY]
```

> SELECT selection_list /要查询的列名称/  
FROM table_list /要查询的表名称/  
WHERE condition /行条件/  
GROUP BY grouping_columns /对结果分组/  
HAVING condition /分组后的行条件/  
ORDER BY sorting_columns /对结果分组/  
LIMIT offset_start, row_count /结果限定/


### 1. 基础查询

1.1 查询所有列
```
SELECT * FROM stu;
```
1.2 查询指定列
```
SELECT sid, sname, age FROM stu;
```
### 2. 条件查询

2.1 条件查询介绍

> 条件查询就是在查询时给出WHERE子句，在WHERE子句中可以使用如下运算符及关键字:
=、!=、<>、<、<=、>、>=；
BETWEEN…AND；
IN(set)；
IS NULL； IS NOT NULL
AND；
OR；
NOT；

2.2 查询性别为女,并且年龄为50的学生信息
```
SELECT * FROM stu
WHERE gender='female' AND age<50;
```

2.3 查询学号为S_1001，或者姓名为liSi的记录
```
SELECT * FROM stu
WHERE sid ='S_1001' OR sname='liSi';
```

2.4 查询学号为S_1001，S_1002，S_1003的记录
```
SELECT * FROM stu 
WHERE sid IN ('S_1001','S_1002','S_1003');
```
2.5 查询学号不是S_1001，S_1002，S_1003的记录
```
SELECT * FROM tab_student 
WHERE s_number NOT IN ('S_1001','S_1002','S_1003');
```

2.6 查询年龄为null的记录
```
SELECT * FROM stu
WHERE age IS NULL;
```

2.7 查询年龄在20-40之间学生的记录
```
SELECT * 
FROM stu
WHERE age>=20 AND age<=40;
```
或者
```
SELECT * 
FROM stu 
WHERE age BETWEEN 20 AND 40;
```

2.8 查询性别非男的学生记录
```
SELECT * 
FROM stu
WHERE gender!='male';
```
或
```
SELECT * 
FROM stu
WHERE gender<>'male';
```
或
```
SELECT * 
FROM stu
WHERE NOT gender='male';
```


2.9 查询姓名不为null的学生记录
```
SELECT * 
FROM stu
WHERE sname IS NOT NULL;
```
或
```
SELECT * 
FROM stu
WHERE NOT sname IS NULL;
```
### 3 模糊查询

> 前面介绍的所有操作符都是针对已知值进行过滤的,不管是匹配一个还是多个值,测试大于还是小于已知值,或者检查摸个范围的值,共同点是过滤中使用的值都是已知的.但是,这种过滤方法并不是任何时候都好用,例如当想查询中包含a字母的学生时就需要使用模糊查询了。     
模糊查询需要使用关键字LIKE 
在使用like关键字时,通常和通配符配合使用
通配符: 用来匹配一部分的特殊字符     
_ : 匹配任意一个字符   
% : 任意0~n个字符   

3.1 查询姓名由5个字母构成的学生记录
```
SELECT * 
FROM stu
WHERE sname LIKE '_____'
-- 模糊查询必须使用LIKE关键字。其中 “_”匹配任意一个字母，5个“_”表示5个任意字母
```

3.2 查询姓名由5个字母构成，并且第5个字母为“i”的学生记录
```
SELECT * 
FROM stu
WHERE sname LIKE '____i';
```
3.3 查询姓名以“z”开头的学生记录
```
SELECT * 
FROM stu
WHERE sname LIKE 'z%';
-- 其中“%”匹配0~n个任何字母。
```
3.4 查询姓名中第二个字母是i的学生记录
```
SELECT * 
FROM stu
WHERE sname LIKE '_i%';
```
3.5 查询姓名中包含“a”字母的学生记录
```
SELECT * 
FROM stu
WHERE sname LIKE '%a%';
```
### 4. 字段控制查询

4.1 去除重复记录

>去除重复记录（两行或两行以上记录中系列的上的数据都相同），例如emp表中sal字段就存在相同的记录。当只查询emp表的sal字段时，那么会出现重复记录，那么想去除重复记录，需要使用DISTINCT
```
SELECT DISTINCT sal FROM emp;
```

数据是没有重复的

4.2 查看雇员的月薪和佣金之和

因为sal和comm两列的类型都是数值类型，所以可以做加运算。如果sal或comm中有一个字段不是数值类型，那么会出错
```
SELECT *,sal+comm FROM emp;
```

而comm列有很多记录的值为NULL，因为任何东西与NULL相加结果还是NULL，所以结算结果可能会出现NULL。下面使用了把NULL转换成数值0的函数IFNULL:
```
SELECT *,sal+IFNULL(comm,0) FROM emp;
```


4.3 给列添加别名

在上面查询中出现列名为sal+IFNULL(comm,0)，这很不美观，现在我们给这一列给出一个别名，为total：
```
SELECT *, sal+IFNULL(comm,0) AS total FROM emp;
```


给列起别名时，是可以省略AS关键字的：
```
SELECT *,sal+IFNULL(comm,0)  total FROM emp;
```

### 5. 排序

排序使用 order by 列名 asc/desc 作为语法 
默认是asc(升序) 可以指定 desc 降序

5.1 查询所有学生记录，按年龄升序排序
```
SELECT *
FROM stu
ORDER BY age ASC;
```
或者
```
SELECT *
FROM stu
ORDER BY age;
```


5.2 查询所有学生记录，按年龄降序排序
```
SELECT *
FROM stu
ORDER BY age DESC;
```

5.3 查询所有雇员，按月薪降序排序，如果月薪相同时，按编号升序排序
```
SELECT * FROM emp
ORDER BY sal DESC,empno ASC;
```

### 6. 聚合函数

聚合函数是用来做纵向运算的函数

> COUNT()：统计指定列不为NULL的记录行数；  
MAX()：计算指定列的最大值，如果指定列是字符串类型，那么使用字符串排序运算；   
MIN()：计算指定列的最小值，如果指定列是字符串类型，那么使用字符串排序运算；   
SUM()：计算指定列的数值和，如果指定列类型不是数值类型，那么计算结果为0；   
AVG()：计算指定列的平均值，如果指定列类型不是数值类型，那么计算结果为0；   

6.1 COUNT

>当需要纵向统计时使用COUNT(),COUNT小括号中可以放入指定列名,和* 如果是* 则代表查询的是结果集的行数,如果是列名,则是指定列的行数

查询emp表中记录数
```
SELECT COUNT(*) AS cnt FROM emp;
```


查询emp表中有佣金的人数
```
SELECT COUNT(comm) cnt FROM emp;
```


注意，因为count()函数中给出的是comm列，那么只统计comm列非NULL的行数
查询emp表中月薪大于2500的人数
```
SELECT COUNT(*) AS '人数' FROM emp
WHERE sal > 2500;
```


统计月薪与佣金之和大于2500元的人数
```
SELECT COUNT(*) AS cnt FROM emp WHERE sal+IFNULL(comm,0) > 2500;
```


查询有佣金的人数，有领导的人数
```
SELECT COUNT(comm), COUNT(mgr) FROM emp;
```


6.2 SUM和AVG

当需要纵向求和时使用sum()函数。当需要求平均值时使用avg()函数

查询所有雇员的月薪和
```
SELECT SUM(sal) FROM emp;
```


查询所有雇员月薪和，以及所有雇员佣金和
```
SELECT SUM(sal), SUM(comm) FROM emp;
```


查询所有雇员月薪+佣金和
```
SELECT SUM(sal+IFNULL(comm,0)) FROM emp;
```


统计所有员工的平均工资
```
SELECT AVG(sal) FROM emp;
```


6.3 MAX 和 MIN

MAX和MIN 是用来查询最大值和最小值的

查询员工的最高工资和最低工资:
```
SELECT MAX(sal), MIN(sal) FROM emp;
```


### 7. 分组查询

当需要分组查询时需要使用GROUP BY子句，例如查询每个部门的工资和，这说明要使用部门来分组

>注意: 
凡是和聚合函数同时出现的列名，一定要写在group by 之后 
分组时候是无法体现单个数据的 
group by 一般会合聚合函数配合使用,单独使用的时候意义不大

7.1 分组查询

查询每个部门编号和每个部门的工资和:
```
SELECT deptno, SUM(sal)
FROM emp
GROUP BY deptno;
```


查询每个部门的部门编号以及每个部门的人数
```
SELECT deptno,COUNT(*)
FROM emp
GROUP BY deptno;
```


查询每个部门的编号以及每个部门工资大于1500的人数:
```
SELECT deptno,COUNT(*)
FROM emp
WHERE sal>1500
GROUP BY deptno;
```


7.2 HAVING字句

查询工资总和大于9000的部门编号以及工资总和:
```
SELECT deptno, SUM(sal)
FROM emp
GROUP BY deptno
HAVING SUM(sal) > 9000;
```

having和where的区别 
>1. having是在分组后对数据进行过滤,而where是在分组前对数据进行过滤 
>2. having后面可以使用聚合函数(统计函数),where后面不可以使用聚合函数

WHERE是对分组前记录的条件，如果某行记录没有满足WHERE子句的条件，那么这行记录不会参加分组；而HAVING是对分组后数据的约束


统计出各个部门的各个岗位中,平均工资>1000的信息
```
SELECT
  job,
  deptno,
  avg(sal)
FROM emp
GROUP BY job, deptno
HAVING avg(sal) > 1000;
```


### 8. LIMIT

LIMIT用来限定查询结果的起始行，以及总行数。

查询5行记录，起始行从0开始
```
SELECT * FROM emp LIMIT 0, 5;
```


查询语句的书写顺序:
```
select – from- where- group by- having- order by-limit
查询语句的执行顺序:

from - where -group by - having - select - order by-limit

```
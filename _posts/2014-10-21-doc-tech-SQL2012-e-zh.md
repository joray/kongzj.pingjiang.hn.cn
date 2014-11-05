---
layout: post
category : 技术
title: SQL2012 学习
tagline: ""
tags : [SQL2012, SQL]
---
{% include JB/setup %}


####SQL常用命令1:
1.SELECT

2.INSERT

3.UPDATE

4.DELETE


##相关示例

SELECT 列名称 FROM 表名称

	SELECT * FROM Datebase.Tables;     //  SELECT 列 FROM 数据库.表;
	SELECT * FROM Sales.Customer;

SELECT DISTINCT 列名称 FROM 表名称
SELECT 列名称 FROM 表名称 WHERE 列 运算符 值


AND 和 OR 运算符

SELECT * FROM Persons WHERE FirstName='Thomas' AND LastName='Carter'
SELECT Company, OrderNumber FROM Orders ORDER BY Company

INSERT INTO 语句
INSERT INTO 表名称 VALUES (值1, 值2,....)

INSERT INTO Persons VALUES ('Gates', 'Bill', 'Xuanwumen 10', 'Beijing')

UPDATE 表名称 SET 列名称 = 新值 WHERE 列名称 = 某值
UPDATE Person SET FirstName = 'Fred' WHERE LastName = 'Wilson' 

DELETE FROM 表名称 WHERE 列名称 = 值
DELETE FROM Person WHERE LastName = 'Wilson' 


####SQL常用命令2:

1.CREATE

2.DROP




####SQL语法1:

1.FROM 

2.ORDER BY

3.GROUP BY


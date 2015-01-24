---
layout: post
category : 技术
title: 远程 唤醒
tagline: ""
tags : [远程, 唤醒]
---
{% include JB/setup %}











a.

端口映射>虚拟服务器>转发规则>添加一新条目>
端口为7777,7777也可以是其它端口号,只要不和其它的冲突,IP地址为需要唤醒电脑网卡所使用的IP地址.比如
192.168.1.8,协议为UDP,并使之处于“生效”状态。 这一步使得当路由器收到发到它7端口的数据都会转发到192.168.1.8这台电脑上。 


b.

IP与MAC绑定>IP与MAC绑定>静态ARP绑定设置>添加一新条目>
MAC地址为网卡(被唤电脑上的)MAC.如00-0B-2F-XX-XX-XX,IP为上一步设置的IP192.168.1.8,当路由器收到从internet发来的MagicPacket包时,由于设了端口映射就需要将其转发到192.168.1.8上。但由于电脑是处理关机状态,ARP无法通过广播找到192.168.1.8这台电脑,Magic包将
被路由器丢弃,因此进行静态的IP-MAC绑定,使数据包可以直接发往MAC为00-0B-2F-XX-XX-XX的网卡上。 此时,从理论上来说,通过internet的远程唤醒就可以成功了。但还有一些工作需要补充,以便更
好地工作。 

c.

静态地址分配,为了确保该电脑在启动后可以获得192.168.1.8这个IP,需要在DHCP服务器中设置一个静态地址分配,即MAC 00-0B-2F-XX-XX-XX 静态分配192.168.1.8永不过期。 

d.

在路由器上使用动态DDNS功能,花生壳,这样可以用一个域名来访问而不用查看经常改变的公网IP,ADSL拨号上网的IP是经常变的。同时,允许路由器可以进行无端WEB管理,以方便当我们在任何地方都可以检查路由器的状态。






















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


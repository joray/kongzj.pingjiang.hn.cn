---
layout: post
category : 技术
title: apache php 运行环境
tagline: ""
tags : [apache, php]
---
{% include JB/setup %}


###在WINXP:
1. IIS6/TS/ISAP/VC9
2. IIS6/NTS/FastCGI/VC9
3. Apache/NTS/FastCGI/VC9
4. Apache/TS/Apache module/VC6

###在WIN7下：
1. IIS7/NTS/FastCGI/VC9
2. Apache/TS/FastCGI/VC9



###相关配置
Windows Apache 及 PHP 运行环境

	httpd-2.4.10-win32.zip => http://www.apachelounge.com/download/
	php-5.5.17-Win32-VC9-x86.zip (VC9 x86 Thread Safe ) => http://windows.php.net/download/
	mysql-5.6.16-win32.msi => http://www.mysql.com/downloads/mysql/


1、先决条件：
第一次你必须安装32位 ( Windows 7+ 以上)  Visual C++ 2010 Redistributable Package.
如果没有安装，请正载: http://www.microsoft.com/download/en/details.aspx?id=8328

执行程序vcredist_x86.exe


2、安装 Apache 2.4 
解压缩文件Apache Zip 至 c:\apache24 (注意：不是c:\apache24\Apache24)
解压缩至新的文件夹，你将需要调整设置的选项，请不要这样，除非你知道该怎么设置这些选项 changba.comu54984936


注意：Apache.org上的版本为VC6，下载VC9/VC10/VC11的请在http://www.apachelounge.com/下载

3、install Apache as a server(安装Apache为一个windows的一个服务)
	command line:

	c:\windows>cd c:\apache24\bin
	c:\apache24\bin>
	
	httpd.exe -k install -n "Apache2.4"   or     	httpd.exe -k install
	httpd.exe -k uninstall -n "Apache2.4"   or     	httpd.exe -k uninstall
	
	/********* httpd.conf ******/
	
	ServerRoot "c:/Apache24"
	
	Listen 192.168.1.100:80
	
	ServerName 192.168.1.100:80
	
	DocumentRoot "d:/webservice/app"
	
	<Directory "d:/webservice/app">  
	</Directory>	
	<Directory />
		Options FollowSymLinks
		AllowOverride All
		Order deny,allow
		allow from all
	</Directory>
	
	<IfModule dir_module>
	DirectoryIndex index.html index.php
	</IfModule>
	
	
	Include conf/extra/httpd-vhosts.conf
	
	
	#php 5.4
	LoadFile "C:/php/php5ts.dll"
	LoadModule php5_module "c:/php/php5apache2_4.dll"
	AddType application/x-httpd-php .php .phtml
	PHPIniDir "C:/php"


4、执行程序ApacheMonitor.exe：
	C:\Apache24\bin\ApacheMonitor.exe

5、ApacheMonitor.exe程序创建快捷方式，放到开始菜单的启动文件夹开机即可以监视Apache运行

6、D:\webservice\app 文件目录为网站根目录

7、编辑：C:\WINDOWS\system32\drivers\etc\hosts
	加入一行：
	127.0.0.1       www.example.com
	
8、编辑：C:\Apache24\conf\extra\httpd-vhosts.conf
	加上一个虚拟网站：





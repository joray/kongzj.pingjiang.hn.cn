---
layout: post
category : 技术
title: apache php 运行环境
tagline: ""
tags : [apache, php]
---
{% include JB/setup %}


### 在WINXP:

	a IIS6/TS/ISAP/VC9
	b IIS6/NTS/FastCGI/VC9
	c Apache/NTS/FastCGI/VC9
	d Apache/TS/Apache module/VC6

### 在WIN7下：

	a IIS7/NTS/FastCGI/VC9
	b Apache/TS/FastCGI/VC9



### 相关配置
Windows Apache 及 PHP 运行环境

	php5
	
	httpd-2.4.10-win32.zip => http://www.apachelounge.com/download/
	php-5.5.17-Win32-VC9-x86.zip (VC9 x86 Thread Safe ) => http://windows.php.net/download/
	mysql-5.6.16-win32.msi => http://www.mysql.com/downloads/mysql/
	
	
	php7
	
	httpd-2.4.33-win32-VC15.zip
	Apache 2.4.33 Win32
	https://www.apachelounge.com/download/VC15/binaries/httpd-2.4.33-Win32-VC15.zip
	
	php-7.2.4-Win32-VC15-x86.zip
	VC15 x86 Thread Safe (2018-Mar-28 20:47:44)
	https://windows.php.net/downloads/releases/php-7.2.4-Win32-VC15-x86.zip
	
	https://dev.mysql.com/get/Downloads/MySQLInstaller/mysql-installer-community-8.0.11.0.msi


1、先决条件：
第一次你必须安装32位 ( Windows 7+ 以上)  Visual C++ 2010 Redistributable Package.
如果没有安装，请正载: http://www.microsoft.com/download/en/details.aspx?id=8328
执行程序vcredist_x86.exe

php7 vc15 
请安装：https://aka.ms/vs/15/release/VC_redist.x64.exe https://aka.ms/vs/15/release/VC_redist.x86.exe

2、安装 Apache 2.4 
解压缩文件Apache Zip 至 c:\apache24 (注意：不是c:\apache24\Apache24)
解压缩至新的文件夹，你将需要调整设置的选项，请不要这样，除非你知道该怎么设置这些选项 changba.comu54984936


注意：Apache.org上的版本为VC6，下载VC9/VC10/VC11的请在http://www.apachelounge.com/下载

3、install Apache as a server(安装Apache为一个windows的一个服务)

	command line:

	c:\windows>cd c:\apache24\bin
	c:\apache24\bin>
	
	httpd.exe -k install -n "Apache2.4" 
	httpd.exe -k uninstall -n "Apache2.4" 
	
	/********* httpd.conf ******/
	
	ServerRoot "c:/Apache24"
	
	Listen 192.168.0.6:80
	
	ServerName 192.168.0.6:80
	
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
	#LoadFile "C:/php/php5ts.dll"
	#LoadModule php5_module "c:/php/php5apache2_4.dll"
	#AddType application/x-httpd-php .php .phtml
	#PHPIniDir "C:/php"
	
	#php 7.2
	LoadFile "C:/php/php7ts.dll"
	LoadModule php7_module "c:/php/php7apache2_4.dll"
	AddType application/x-httpd-php .php .phtml
	PHPIniDir "C:/php"

4、PHP设置：

	; On windows:
	extension_dir = "ext"


5、执行程序ApacheMonitor.exe：

	C:\Apache24\bin\ApacheMonitor.exe

6、ApacheMonitor.exe程序创建快捷方式，放到开始菜单的启动文件夹开机即可以监视Apache运行

7、D:\webservice\app 文件目录为网站根目录

8、编辑：
	
	C:\WINDOWS\system32\drivers\etc\hosts

	加入一行：
	127.0.0.1       www.example.com
	
9、编辑：
	
	C:\Apache24\conf\extra\httpd-vhosts.conf
	加上一个虚拟网站：

**** 常见问题

	/*******PHP.INI*******/
	
	; On windows:
	extension_dir = "ext"

	导入数据超时，设置以下两个值
	max_execution_time = 3000
	max_input_time = 3600

	memory_limit = 512M
	upload_max_filesize = 200M
	max_file_uploads = 200
	
	extension=php_bz2.dll
	extension=php_curl.dll
	extension=php_fileinfo.dll
	extension=php_gd2.dll
	extension=php_gettext.dll
	;extension=php_gmp.dll
	extension=php_intl.dll
	extension=php_imap.dll
	extension=php_interbase.dll
	;extension=php_ldap.dll
	extension=php_mbstring.dll
	extension=php_exif.dll      ; Must be after mbstring as it depends on it
	extension=php_mysql.dll
	extension=php_mysqli.dll
	;extension=php_oci8.dll      ; Use with Oracle 10gR2 Instant Client
	;extension=php_oci8_11g.dll  ; Use with Oracle 11gR2 Instant Client
	;extension=php_openssl.dll
	;extension=php_pdo_firebird.dll
	extension=php_pdo_mysql.dll
	;extension=php_pdo_oci.dll
	extension=php_pdo_odbc.dll
	extension=php_pdo_pgsql.dll
	extension=php_pdo_sqlite.dll
	extension=php_pgsql.dll
	;extension=php_pspell.dll
	;extension=php_shmop.dll


---
layout: post
category : name
title: name
tagline: ""
tags : [name]
---
{% include JB/setup %}




***

	优想
	华悦
	爱悦
	正华
	飞越
	安瑞
	
	
	
	网络科技有限公司
	计算机科技有限公司
	计算机技术有限公司
	信息技术有限公司
	电脑科技有限公司
	科技有限公司
	
	
	长沙优想信息科技有限公司
	
	湖南景瑞信息科技有限公司	
	湖南恒萃信息科技有限公司	

	湖南华悦计算机有限公司
	湖南华悦信息科技有限公司
	湖南安瑞信息科技有限公司


***

	sudo apt install php
	sudo apt install postgresql
	ALTER USER postgres with encrypted password 'pwdpwd';

***

	sudo apt-get install mysql-server 
	sudo apt-get install mysql-client
	sudo apt-get install libmysqlclient-dev

***

	sudo systemctl restart nginx
	sudo restart nginx
	sudo gedit /etc/nginx/sites-available/imreser
	sudo ln -s /etc/nginx/sites-available/imreser /etc/nginx/sites-enabled
	sudo mkdir /var/www/imreser.com
	
***

	********sudo gedit /etc/nginx/sites-available/imreser

	server {
		listen 8080;
		listen [::]:8080;
	
		server_name imreser.com www.imreser.com;
	
		root /var/www/imreser.com;
		index index.html index.php;
	
		location / {
			try_files $uri $uri/ =404 index.php;
		}
	
		# pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
		#
		location ~ \.php$ {
			include snippets/fastcgi-php.conf;
		
		#	# With php7.0-cgi alone:
		#	fastcgi_pass 127.0.0.1:9000;
		#	# With php7.0-fpm:
			fastcgi_pass unix:/run/php/php7.0-fpm.sock;
		}
	
		# deny access to .htaccess files, if Apache's document root
		# concurs with nginx's one
		#
		location ~ /\.ht {
			deny all;
		}
	}

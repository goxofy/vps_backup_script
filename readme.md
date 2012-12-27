介绍：

一个自用的vps备份脚本，能够将你的web数据和数据库数据打包并发送到设定好的ftp服务器上，并且能发送一份副本到你的邮箱里。



使用方法：

首先在vps上安装Email发送组件，

	 sudo apt-get install sendmail mutt  #mutt为发送邮件支持附件功能


用编辑器打开，修改顶部参数

	#!/bin/bash
	#你要修改的地方从这里开始
	MYSQL_USER=root                             #mysql用户名
	MYSQL_PASS=123456                      #mysql密码
	MAIL_TO=×××@×××.com                 #数据库发送到的邮箱
	FTP_USER=***                             #ftp用户名
	FTP_PASS=123456                         #ftp密码
	FTP_IP=*******                         #ftp地址
	FTP_backup=backup                          #ftp上存放备份文件的目录,这个要自己得ftp上面建的
	WEB_DATA=/home/www                          #要备份的网站数据
	#你要修改的地方从这里结束  
	
给脚本加上可执行权限

	chmod +x /root/AutoBak.sh
	
cron添加自动运行

	crontab -e
	00 00 * * * /root/AutoBak.sh

其中00 00为时间分/小时，可自行修改，例如：30 12 ***，就是每天12.30运行这个脚本。
title: Mac中MySQL的安装、配置、删除
date: 2014-11-17 00:29:59
tags: [java ,服务器]
categories: 技术
---
#1.如何删除MySQL
``` bash
首先可以在System Preferences中的Other里MySQL设置，停止其服务，然后参照以下手工删除命令行。

apple$ sudo rm /usr/local/mysql
apple$ sudo rm -rf /usr/local/mysql*
apple$ sudo rm -rf /Library/StartupItems/MySQLCOM
apple$ sudo rm -rf /Library/PreferencePanes/My*
apple$ sudo rm -rf /Library/Receipts/mysql*
apple$ sudo rm -rf /Library/Receipts/MySQL*
apple$ sudo rm -rf /var/db/receipts/com.mysql.*

编辑/etc/hostconfig，删除其中的MYSQLCOM=-YES-这行
``` 
#2.下载Img镜像安装
http://www.mysql.com/downloads/ 
#3.下载安装MySQL Workbench(GUI Tool)

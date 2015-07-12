title: Mac下配置tomcat
date: 2014-11-09 23:53:13
tags: [java ,服务器]
categories: 技术
---
到 apache官方主页 下载 Mac 版本的完整 .gz文件包。解压拷贝到 /Library目录下。

注：如果系统是OS X 10.10系统会存在不能使用新版jdk的情况，https://jdk8.java.net/download.html， 在此下载兼容版本

1。Mac中 Finder打开 Library的方法
新建 Finder窗口   按下 shift +Command+G  输入  /Library  进入  该隐藏目录。
ps:这个快捷键非常的有用，一定要记住！

2。修改目录权限
选中 文件夹   Command＋I 打开 简介， 修改文件权限    命令     sudo chmod 755 /Library/Tomcat （给个777 权限 也无所谓）

安装Tomcat：
在Apache网站下载最新的Tomcat二进制编码包：（注意别下载了Windows的安装包）http://tomcat.apache.org/ （mac下是.gz）
下载完后，解压，并将文件夹命名为Tomcat
将重命名的文件夹移动到根目录/Library中（别处也可），安装过程便完成了
执行/Library/Tomcat/bin下的startup.sh，然后打开http://localhost:8080 查看是否Tomcat已经启动，若要停止服务器就运行同目录下的shutdown.sh
如果遇到诸如无法找到目录以及文件地问题，一般是因为文件权限造成地问题，可以如此解决：
sudo chmod 755 /Library/Tomcat/bin/*.sh
sudo chmod 755 /Library/Tomcat/bin/*.bat
遇见”JAVA_HOME not defined”JAVA路径未定义错误，在终端中执行以下命令：

sudo setenv JAVA_HOME /Library/Java/Home
配置Tomcat启动脚本：
使用文本编辑器添加以下代码：
``` bash
#!/bin/bash
case $1 in
start)
sh /Library/Tomcat/bin/startup.sh
;;
stop)
sh /Library/Tomcat/bin/shutdown.sh
;;
restart)
sh /Library/Tomcat/bin/shutdown.sh
sh /Library/Tomcat/bin/startup.sh
;;
*)
echo “Usage: start|stop|restart”
;;
esac
exit 0
``` 
将文件保存为tomcat，小写并不带后缀。赋予文件执行权限：
chmod 777 tomcat
。将这个文件放置到终端包含的路径中，例如/usr/bin，而后便可以在终端中简单地输入tomcat start和tomcat stop启用tomcat了。
快捷命令如下：
1）tomcat start 
2)  tomcat stop
3)  tomcat restart 
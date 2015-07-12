title: Mac上安装Rails
date: 2015-02-08 06:03:51
categories: 技术
tags:
---
##环境
Xcode(苹果开发IDE，需要其中的command line工具)
ruby(开发语言环境) 
Homebrew(包管理环境，安装你需要但苹果不需要的东西)
RVM(ruby版本管理，可以让你在不同的ruby版本下切换)
rails(开发框架)
步骤
首先将Xocde安装上
##安装ruby

1. ruby -v

##安装homebrew

> ruby -e "$(curl -fsSL
> https://raw.github.com/mxcl/homebrew/go/install)"

安装完后，检查版本

1. brew -v

##安装rvm

>  \curl -L https://get.rvm.io | bash -s stable

安装完成后，检查版本

> rvm -v

多个ruby版本切换

> rvm install 1.9.3
> rvm use 1.9.3
> rvm --default 1.9.3

##安装Rails

> sudo gem install rails -V

因为国内万恶的墙的问题，原本应该很顺畅的这一步，在国内就会突然恰到某个包的下载，然后就一直不动了。解决方法是，使用淘宝的镜像安装(业界良心)

> gem sources --remove https://rubygems.org/ 
gem sources -a http://ruby.taobao.org/ 
gem sources -l

用这个安装完成，便可查看rails版本

> rails -v

创建一个测试工程，检查环境是否安好

> rails new hello --skip-bundle


加上—skip-bundle还是墙的原因，然后我们要在新建的项目中，手动的为它安装bundle。
新建项目之后再安装bundle,进入到项目中，打开Gemfile,修改第一行：source ‘https://rubygems.org‘修改为：source ’http://ruby.taobao.org’

> gem install bundle


使用cd命令进入hello文件夹，尝试启动rails的server服务，看是否正常。

> rails server

如果报错：

> Could not find gem 'sdoc (>= 0) ruby' in the gems available on this
> machine.
> 
> 
> Run `bundle install` to install missing gems.


继续使用命令

> bundle install



至此，继续使用rails server命令，如果看到
=> Booting WEBrick
=> Rails 4.0.1 application starting in development on http://0.0.0.0:3000
=> Run `rails server -h` for more startup options
=> Ctrl-C to shutdown server
[2013-12-01 01:09:34] INFO  WEBrick 1.3.1
[2013-12-01 01:09:34] INFO  ruby 2.0.0 (2013-06-27) [universal.x86_64-darwin13]
[2013-12-01 01:09:34] INFO  WEBrick::HTTPServer#start: pid=1130 port=3000
说明启动成功，至此，已安装好rails的环境，步数较多，需要耐心，如果出现权限问题的提示，就在相应的命令前加sudo，来提高权限即可。



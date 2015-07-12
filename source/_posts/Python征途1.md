title: Python征途1
date: 2015-01-15 18:02:35
tags: [技术]
categories: 技术
---
首先我使用的是Mac本，使用的工具是[TextMate](http://macromates.com/)，一般Mac OS会自带Python，但是版本很低，建议[升级](http://jingyan.baidu.com/article/14bd256e39b63dbb6d261289.html)，升级不一定要拆卸老版本的Python，可以只改Path路径就可以。
2.x和3.x的Python还是有差别，
比如2.x版本语法 print ‘hello world’，更新后运行就告诉我语法错误，
3.x应该为 print(‘hello world’)
<br>
如果你是一名apple开发者，千万不要删除2.7版本，因为Xcode需要它的支持。
。
开始练习
打开你的终端，输入python，然后看见一些版本信息，也可以看到下面出现了可以输入python代码的提示，好把，输入 print('hello world'),回车。
可以看到输出的"hello world"

再新建一个文本一helloworld.py，输入print('hello world')，保存。在终端输入python (路径)/helloworld.py,可以看到终端运行了这个脚本。
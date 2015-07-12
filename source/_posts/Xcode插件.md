title: Xcode插件
date: 2015-01-11 16:07:24
tags: [Xcode ,ios]
categories: Xcode
---
##检查NSColor/UIColor实例
<img src="/Xcode/XcodeAdditionImages/8369_140506094312_1.png" height="200" width="200">
单从RGB的值分辨颜色很不容易，所以面对一个NSColor或者UIColor值，我们直到创建并运行代码才知道它是什么颜色。不过可以使用[ColorSense](https://github.com/omz/ColorSense-for-Xcode) for Xcode。

##本地化
<img src="/Xcode/XcodeAdditionImages/8369_140506094658_1.png" height="200" width="200">
<img src="/Xcode/XcodeAdditionImages/8369_140506094713_1.png" height="200" width="200">
[Lin](https://github.com/questbeat/Lin-Xcode5)是一款开源的智能的xcode5插件 可在代码中添加本地化编辑器，用图形化管理项目的本地化。

Xcode的插件架构是基于一些特定于Xcode私有框架，包括DVTKit和IDEKit。在Xcode的应用程序包中运行[class-dump](http://stevenygard.com/projects/class-dump/)可得到一个完整的[列表](https://github.com/luisobo/Xcode5-RuntimeHeaders)。

##Xcode快速跳转到项目沙盒
<img src="/Xcode/XcodeAdditionImages/gotosandbox.png" height="200" width="200">




[ZLGotoSandboxPlugin-Xcode](https://github.com/MakeZL/ZLGotoSandboxPlugin)
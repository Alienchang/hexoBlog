title: UIApplication详解
date: 2015-01-09 12:04:19
tags:
categories: 技术
---
##UIApplication详解
``` bash
[UIApplication sharedApplication]<br>
``` 
 &emsp;&emsp;UIApplication，顾名思义，代表的是整个应用做的事，因此每个程序只能有一个，系统使用的是单例模式，就是上面的[UIApplication sharedApplication]来得到一个实例。这个单例实例是在系统启动时由main函数里面的UIApplicationMain方法生成，就是每个程序里都有的AppDelegate，它实现了UIApplicationDelegate的Protocol，也就是AppDelegate的一个实例。每次通过[UIApplication sharedApplication]调用的就是它。UIApplication在程序里的角色：它保存一个UIWindow对象序列，用来快速恢复views。它还有很多作用，不过我也不大清楚了。<br>下面来看看我们能用它来干什么：

一、远程提醒，就是push notification注册；<br>
二、可以连接到UIUndoManager；<br>
三、检查能否打开某个URL，并且打开URL；这个功能可以配合应用的自定义URL功能，来检测是否安装了某个应用。比如检测是否安装了淘宝的应用，可以用下面的代码：
``` bash
NSURL *url = [NSURL URLWithString[NSString stringWithFormat:@"taobao://item.taobao.com/item.htm?id=12688928896"]];  
// 判断当前系统是否有安装淘宝客户端  
if ([[UIApplication sharedApplication] canOpenURL:url]) {  
   // 如果已经安装淘宝客户端，就使用客户端打开链接  
     [[UIApplication sharedApplication] openURL:url];  
}  
``` 

四、注册Local Notification；<br>
五、在后台运行以及从后台转为前台时的操作；<br>六、防止屏幕睡眠：
``` bash
[[UIApplication sharedApplication].idleTimerDisabled=YES; 
``` 
七、手动调整status bar的位置和状态，如设置为竖屏、横屏等；<br>
八、设置badge number，就是图标右上角的数字；<br>
九、每当应用联网时，在状态栏上会显示联网小菊花。UIApplication可以设置是否出现。<br>
十。。。还有一些应用，不过那些更不常用，而且我也看不太懂。就写到这里吧。





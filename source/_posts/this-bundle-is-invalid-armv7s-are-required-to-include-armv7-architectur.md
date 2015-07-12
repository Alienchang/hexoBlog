title: 'this bundle is invalid. armv7s are required to include armv7 architectur'
date: 2015-02-10 20:00:50
tags: [Xcode ,ios]
categories: Xcode
---
##Apps that include an arm64 architecture are required to include an armv7


----------


![此处输入图片的描述][1]
遇到上面的报错：首先编译的时候，把真机拔掉就可以了~
如果还不行的话：Build Active Architecture Only 里面的Release 设置为NO就好了~

还可以找到项目配置的架构Architecture部分，将“Build Active Architecture Only”里的Release设置为No（如果不是no的话，当你开着模拟器或者插着手机的时候，就只编译当前的cpu架构的版本），如图所示：




[1]: http://img.blog.csdn.net/20150113181035212?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvamltamFycnk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center
title: xcode5国际化配置
date: 2014-09-23 18:00:08
tags:
categories: 技术
---

国际化分为三种

1.icon国际化，程序图标名的国际化（微信，weChat）。

2.程序内文字的变化。

###一、icon国际化
<img src="/img/xcode5internationalization/1.png" style="width: 400px;"/>
<img src="/img/xcode5internationalization/2.png" style="width: 400px;"/>
<img src="/img/xcode5internationalization/3.png" style="width: 400px;"/>
<img src="/img/xcode5internationalization/4.png" style="width: 400px;"/>


在InfoPlish.strings(english)文件中加入：
CFBundleDisplayName ="Program";  

同理在InfoPlish.strings(chinese)文件中加入：
CFBundleDisplayName ="应用程序";  

在TestLocationTests-Info.plist文件中的
Bundle display name = CFBundleDisplayName 完成了中英文的icon模块的国际化。

###二、程序国际化
（1）类似“本地化应用程序名称”第一步，点击“new file”然后在弹出窗口左侧选择IOS的resource项，在右侧就可以看到“String File”的图标。创建这个文件，命名为“Localizable”（一定是这个文件名否则后面调用会有一些区别）就生成一个Localizable.strings文件；

（2）类似“本地化应用程序名称”第二第三步，在Localizable.strings(english)文件中加入：
``` bash
"welcome"="Click on the screen to continue...";
```

 同理在Localizable.strings(chinese)文件中加入：
``` bash
"welcome"="点击屏幕继续...";
```
（3）在代码中使用NSLocalizedString(<#key#>, <#comment#>)来读取本地化字符串，代码如下：

``` bash
CCLabelTTF *label = [CCLabelTTF labelWithString:NSLocalizedString(@"welcome", nil) fontName:@"Marker Felt" fontSize:18];  
CGSize size = [[CCDirector sharedDirector] winSize];  
label.position =  ccp( size.width /2 , size.height/2+30 );  
[self addChild: label];
```

注意：如果你的strings文件名字不是Localizable而是自定义的话，如wang.strings，那么你就得使用NSLocalizedStringFromTable()来读取本地化字符串：
``` bash
NSLocalizedStringFromTable(@"welcome",@"wang", nil)
```

###三、程序内图片的变化

这里又分两种方法，第一种和本地化字符串方法类似，把中英文图片的名字分别存到中英文对应的strings文件，然后通过NSLocalizedString)来获取图片名称，如：

Localizable.strings(english)文件中加入：
``` bash
"BtnCancel"="BtnCancelEn.png";
```
Localizable.strings(chinese)文件中加入：
``` bash
"BtnCancel"="BtnCancelCn.png";
```
然后在代码中使用NSLocalizedString)来获取图片名称：
``` bash
CCSprite *btnCancel = [CCSprite spriteWithSpriteFrameName:NSLocalizedString(@"BtnCancel", nil)];  
btnCancel.position=ccp(s.width/2,s.height/2-40);  
[self addChild:btnCancel z:2 tag:104];
```
第二种就比较正规化了：点中你要本地化的图片，如“icon.png”，然后XCode-> View-> Utilities -> File Inspector，在Localization中点“+”添加chinese （zh－Hans）；在图片左边就会出现一个倒三角，点开就会出现（english）和（chinese）的2张图，并且在项目文件夹中会出现en.lproj文件和zh-Hans.lproj文件；en.lproj文件存放的是英文版图片，zh-Hans.lproj存放的是中文版图片，中英文图片名字一样，我们在文件夹中直接替换图片就可以了，最后使用时直接使用正常名字就行了，如：“icon.png”

最后收集一些资料；


1. 取得 iPhone 支持的所有语言设置
NSUserDefaults *defaults = [ NSUserDefaults standardUserDefaults ];

NSArray *languages = [defaults objectForKey : @"AppleLanguages" ];

NSLog ( @"%@" , languages);

2.获取当前使用的语言版本，并比较

NSString *currentLanguage = [[NSLocale preferredLanguages] objectAtIndex:0];

        if([currentLanguage isEqualToString:@"en"]) {

     // English

        }
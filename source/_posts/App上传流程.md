title: App上传流程
date: 2014-04-05 11:11:59
categories: 技术
tags: [ios]
tags:
---
###一. 网页上的操作（填写应用信息）：
1. 登录https://itunesconnect.apple.com/，Manage Your Apps——Add New App

2. 点击页面上的链接注册新Bundle ID。ID建议用com.domainname.appname的形式。ID名称不能改，其他信息是可以随时修改的。注册完ID之后回来刷新页面，选择新注册的ID。

3. 填写App名称。这是显示在苹果商店里的名称，和App安装之后显示在手机屏幕上的名字可以不一样，但应该相似。注意名称里不要堆积过多的关键词！星盘大师第一次就因为这个原因被拒了！

4. SKU Number设成跟Bundle ID一样就可以。下一步。

5. 设定available的日期。一般设置的日期比上传的晚两三周，因为审核需要时间。

6. 选择地区、价格等等。默认是所有地区，一般不用改。下一步。

7. 设定版本号，据说最好1.0起，不要显得还在测试的样子。

8. 版权，写成“2014 XingYan”这种形式（不含引号）就可以。

9. 下面各项根据自己情况填写即可。必须把必填的项都填完才能保存，不让填一半中途保存，不过，在保存之后提交之前所有东西都可以随时修改，所以不用担心。下一步。

10. 是否用了加密。一般选no，如果选yes需要提供一些额外证明。

11. 是否用了第三方的东西，如果用了是否合法。都选yes。

12. 广告。目前我们没广告，选no。下一步。

###二. 新建发布证书
1. 登录https://developer.apple.com/account/ios/profile/profileList.action，点加号+

2. 选择Distribution，App Store，下一步。

3. 选择刚才新建的Bundle ID。一路继续。

###三. Xcode里的操作（上传软件包）：
上传有很多种办法，但最后管用的还是以下这种：
1. Xcode菜单：Product——Archive（必须选真实的设备，否则菜单是灰色的）

2. 成功之后会出现Organizer（菜单：Window——Organizer）

3. 选择相应的archive，点上方右侧的按钮Validate，检测App是否有问题。

4. 通过检测后，点Distribute。会出现几个选项，其中第二个选项Save for Enterprise or Ad Hoc Deployment可生成IPA文件，方便备份保存（过程中可选择用什么证书签名）。要上传苹果商店的话选第一个选项Submit to the iOS App Store，然后按照提示一步步操作即可。

如果出现上传失败，是网络原因，多试几次即可。
如果出现证书问题，注意工程设置里的Bundle ID设的是否一致，另可参考这篇文章：
http://stackoverflow.com/questions/10215530/no-identities-were-available-administrator-request


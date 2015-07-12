layout: mytext
title: des加密
date: 2015-01-11 21:18:52
tags:
---
最近做了两个项目一个是外包（北美的一个教育软件），还有就是我们的创业项目。这两个项目中在数据传输方面我们都用了des加密，感觉很好用就记下了。

##加密方式
客户端每次登录时会向服务器发送一个唯一token，服务器根据当前session返回给客户端一个字符串，再由客户端根据key和session合成一个des加密解密的一个key。在这登录以后与服务器的所有网络请求都需要发送给服务器这个key，因为服务器知道这个唯一的token和那个session串，所以他可以根据这个key解密你发送的已经加密的网络数据。

##平台差异性
不同平台的加密可能会出现一些差异
第一个项目是php，android（java），iOS平台组合
<br>iOS端<a href="/downLoadData/DES/NSString+DES.zip" style="font-size: 14px; text-decoration: underline;"><strong><span style="font-size: 14px;">下载</span></strong></a>




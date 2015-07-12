title: 适配iOSUINavigationBar遮挡TableView问题
categories: 技术
date: 2014-07-04 12:58:54
tags: [小知识 ,ios]
---
if([[[UIDevice currentDevice]systemVersion]floatValue]>=7.0)
    {
        self.edgesForExtendedLayout = UIRectEdgeNone;
        self.automaticallyAdjustsScrollViewInsets = NO;
    }

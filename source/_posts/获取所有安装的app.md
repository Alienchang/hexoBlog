title: 获取所有安装的app
date: 2014-10-31 00:02:20
tags: [小知识 ,ios]
---
``` bash
#include <objc/runtime.h>
Class LSApplicationWorkspace_class = objc_getClass("LSApplicationWorkspace");
NSObject* workspace = [LSApplicationWorkspace_class performSelector:@selector(defaultWorkspace)];
NSLog(@"apps: %@", [workspace performSelector:@selector(allApplications)]);
``` 
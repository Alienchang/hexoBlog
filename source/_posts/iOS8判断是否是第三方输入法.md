title: iOS8判断是否是第三方输入法
date: 2015-07-10 14:28:52
tags:
---
if ([NSStringFromClass([[textField textInputMode] class])  isEqualToString:@"UIKeyboardExtensionInputMode"]) {
    NBLog(@"是他大爷的第三方输入法");
}


//UIKeyboardExtensionInputMode是控制台下po出来的，私有的

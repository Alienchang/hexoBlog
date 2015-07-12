title: 解决UIGesture和tableViewCell点击事件的冲突
date: 2015-01-15 17:10:37
tags: [小知识 ,ios ,技术]
categories: 技术
---
当你给一个controller的view加了手势之后发现tableViewCell不回接收到响应，因为响应被view拦截
``` bash
#pragma mark - UIGestureRecognizerDelegate
- (BOOL)gestureRecognizer:(UIGestureRecognizer *)gestureRecognizer shouldReceiveTouch:(UITouch *)touch
{
    // 输出点击的view的类名
    NSLog(@"%@", NSStringFromClass([touch.view class]));

    // 若为UITableViewCellContentView（即点击了tableViewCell），则不截获Touch事件
    if ([NSStringFromClass([touch.view class]) isEqualToString:@"UITableViewCellContentView"]) {
        return NO;
    }
    return  YES;
}
``` 
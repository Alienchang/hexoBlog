title: iOS小技巧
date: 2015-02-07 19:27:58
categories: 技术
tags:
---

1. 在tableViewCell中获取当前cell所在的indexPath？
``` bash
- (UITableView*)tableView {
    if (tableView == nil) {
        tableView = (UITableView*)self.superview;
    while (tableView && ![tableView isKindOfClass:[UITableView class]]) {
        tableView = (UITableView*)tableView.superview;
    }
}
    return tableView;
}


NSIndexPath *p = [self.tableView indexPathForCell:self];
```
2. 想做现在还不能做
``` bash
善用 // TODO: xxxxxx
```

3. 想在两个网络请求后再callback?
```dispatch_group_t serviceGroup = dispatch_group_create();
dispatch_group_enter(serviceGroup);
[Network fetchSuccess:{
    dispatch_group_leave(serviceGroup);
} error:{
    dispatch_group_leave(serviceGroup);
}];

dispatch_group_enter(serviceGroup);
[Network fetchSuccess:{
    dispatch_group_leave(serviceGroup);
} error:{
    dispatch_group_leave(serviceGroup);
}];

dispatch_group_notify(serviceGroup,dispatch_get_main_queue(),^{
    // Assess any errors
    NSError *overallError = nil;
    successBlock();
    // Now call the final completion block
});

```

4. 计算文字所占大小
``` bash
NSDictionary * tdic = [NSDictionary dictionaryWithObjectsAndKeys:[AppSkin fontOfBoldTinySize],NSFontAttributeName,nil];

CGSize actualsize =[string boundingRectWithSize:size options:NSStringDrawingUsesLineFragmentOrigin  attributes:tdic context:nil].size;
```
5. 实时监听textField的字符变化，当你想用UITextField实现SearchBar的功能时，你会发现系统没有给出与SearchBar相似的delegate，这时我们可以用通知来实现这个功能
``` bash
//注册对应的通知：
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(textFieldChanged:) name:UITextFieldTextDidChangeNotification object:textField];

//实现textFieldChanged函数
- (void)textFieldChanged:(id)sender
{
NSNotification *notification = (NSNotification *)sender;
UITextField *textField = notification.object;
}

//记得在dealloc中删除掉通知。
- (void)dealloc
{
[[NSNotificationCenter defaultCenter] removeObserver:self name:UITextFieldTextDidChangeNotification object:nil];
}
```
6. iOS8判断是否是第三方输入法
``` bash
if ([NSStringFromClass([[textField textInputMode] class]) isEqualToString:@"UIKeyboardExtensionInputMode"]) {
NBLog(@"是他大爷的第三方输入法");
}
//UIKeyboardExtensionInputMode是控制台下po出来的，私有的
```
7. 给一个controller的view加了手势之后发现tableViewCell不回接收到响应，因为响应被view拦截
```
pragma mark - UIGestureRecognizerDelegate
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




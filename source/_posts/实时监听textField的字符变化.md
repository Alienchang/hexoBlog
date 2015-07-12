title: 实时监听textField的字符变化
date: 2015-01-15 17:14:47
tags: [小知识 ,ios ,技术]
categories: 技术
---
当你想用UITextField实现SearchBar的功能时，你会发现系统没有给出与SearchBar相似的delegate，这时我们可以用通知来实现这个功能
1，注册对应的通知：
``` bash
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(textFieldChanged:) name:UITextFieldTextDidChangeNotification object:textField];
``` 
2，实现textFieldChanged函数
``` bash
- (void)textFieldChanged:(id)sender
{
    NSNotification *notification = (NSNotification *)sender;
    UITextField *textField = notification.object;
}
``` 
3，记得在dealloc中删除掉通知。
``` bash
- (void)dealloc
{
    [[NSNotificationCenter defaultCenter] removeObserver:self name:UITextFieldTextDidChangeNotification object:nil];
}
``` 

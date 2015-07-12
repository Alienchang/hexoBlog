title: UITextField自定义
date: 2014-08-13 09:22:44
categories: 技术
tags: [小知识 ,ios ,技术]
---
``` bash
//重置textField编辑时输入框的rect
- (CGRect)editingRectForBounds:(CGRect)bounds
{
    return  CGRectMake(3, 0, bounds.size.width - 3, bounds.size.height);
}
```

``` bash
- (CGRect)textRectForBounds:(CGRect)bounds
{
return CGRectInset(bounds, 3, 0);
}
```

``` bash
- (CGRect)borderRectForBounds:(CGRect)bounds
{
return  CGRectMake(3, 0,bounds.size.width - 3, bounds.size.height);
}
```

``` bash
- (CGRect)placeholderRectForBounds:(CGRect)bounds
{
return  CGRectMake(3, 0,bounds.size.width - 3, bounds.size.height);
}
```
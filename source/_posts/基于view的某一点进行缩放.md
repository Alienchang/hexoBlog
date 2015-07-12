title: 基于view的某一点进行缩放
date: 2014-07-21 11:05:31
categories: 技术
tags: [小知识 ,ios ,技术]
---
朋友问的，顺便就记下来吧

``` bash
- (void)viewDidLoad
{
    [super viewDidLoad];
    
    UIView \*view = [[UIView alloc] initWithImage:[UIImage imageNamed:@"5A46917B4B71720582F6A0F77F2653FC.jpg"]];
    [view       setUserInteractionEnabled:YES];
    [view       setFrame:CGRectMake(100, 100, 100, 100)];

    UITapGestureRecognizer \*tapGestureRecognizer = [[UITapGestureRecognizer alloc] initWithTarget:self action:@selector(tapAction:)];

    [view.layer setAnchorPoint:CGPointMake(0, 0)];     //关键就在于这句话，这个point是以view的坐标为准

    [view       addGestureRecognizer:tapGestureRecognizer];
    [view       setBackgroundColor:[UIColor redColor]];
    
    [self.view addSubview:view];
}
- (void)tapAction:(UITapGestureRecognizer \*)sender
{
    UIView \*view = sender.view;
    if (!_isScaled) {
        _isScaled = YES;
        [view setTransform:CGAffineTransformMakeScale(0.5, 0.5)];
    }else{
        _isScaled = NO;
        [view setTransform:CGAffineTransformMakeScale(1, 1)];
    }
    
}
```
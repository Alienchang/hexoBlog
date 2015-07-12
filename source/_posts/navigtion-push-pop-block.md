title: 'navigtion push pop block'
date: 2015-06-30 11:53:18
tags: [ios ,小知识]
categories: blog
---
```base
#import "MyNavigationController.h"

@interface MyNavigationController ()

@property (nonatomic, copy) void (^completion)(void);

@end

@implementation MyNavigationController

- (void)viewDidLoad
{
[super viewDidLoad];
// Do any additional setup after loading the view.
self.delegate = self;
}

- (void)dealloc
{
    self.delegate = nil;
}

- (void)didReceiveMemoryWarning
{
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}

- (void)pushViewController:(UIViewController *)viewController animated:(BOOL)animated completion:(void (^)(void))completion
{
    self.completion = completion;
    [self pushViewController:viewController animated:animated];
}

- (UIViewController *)popViewControllerAnimated:(BOOL)animated completion:(void (^)(void))completion
{
    self.completion = completion;
    return [self popViewControllerAnimated:animated];
}

- (NSArray *)popToViewController:(UIViewController *)viewController animated:(BOOL)animated completion:(void (^)(void))completion
{
    self.completion = completion;
    return [self popToViewController:viewController animated:animated];
}

- (NSArray *)popToRootViewControllerAnimated:(BOOL)animated completion:(void (^)(void))completion
{
    self.completion = completion;
    return [self popToRootViewControllerAnimated:animated];
}

#pragma mark - UINavigationControllerDelegate Methods

- (void)navigationController:(UINavigationController *)navigationController didShowViewController:(UIViewController *)viewController animated:(BOOL)animated
{
    if (self.completion)
    {
        self.completion();
    }
}

@end
```